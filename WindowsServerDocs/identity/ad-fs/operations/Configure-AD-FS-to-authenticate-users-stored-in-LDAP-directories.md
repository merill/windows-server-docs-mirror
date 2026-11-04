---
layout: Conceptual
title: Configure AD FS to authenticate users stored in LDAP directories | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/configure-ad-fs-to-authenticate-users-stored-in-ldap-directories
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configure AD FS to authenticate users stored in LDAP directories in Windows Server 2016 or later'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: de1b1289-7d19-42f9-3414-5430f7216a56
document_version_independent_id: b650a7fa-e79e-425b-7239-6332bb22a3db
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Configure-AD-FS-to-authenticate-users-stored-in-LDAP-directories.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/configure-ad-fs-to-authenticate-users-stored-in-ldap-directories
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Configure-AD-FS-to-authenticate-users-stored-in-LDAP-directories.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: adcf9e77-a465-89fe-a804-dca26d013a36
---

# Configure AD FS to authenticate users stored in LDAP directories | Microsoft Learn

The following topic describes the configuration required to enable your AD FS infrastructure to authenticate users whose identities are stored in Lightweight Directory Access Protocol (LDAP) v3-compliant directories.

In many organizations, identity management solutions consist of a combination of Active Directory, AD LDS, or third-party LDAP directories. With the addition of AD FS support for authenticating users stored in LDAP v3-compliant directories, you can benefit from the entire enterprise-grade AD FS feature set regardless of where your user identities are stored. AD FS supports any LDAP v3-compliant directory.

Note

Some of the AD FS features include single sign-on (SSO), device authentication, flexible conditional access policies, support for work-from-anywhere through the integration with the Web Application Proxy, and seamless federation with Microsoft Entra which in turn enables you and your users to utilize the cloud, including Office 365 and other SaaS applications. For more information, see [Active Directory Federation Services Overview](../ad-fs-overview).

In order for AD FS to authenticate users from an LDAP directory, you must connect this LDAP directory to your AD FS farm by creating a **local claims provider trust**. A local claims provider trust is a trust object that represents an LDAP directory in your AD FS farm. A local claims provider trust object consists of a variety of identifiers, names, and rules that identify this LDAP directory to the local federation service.

You can support multiple LDAP directories, each with its own configuration, within the same AD FS farm by adding multiple **local claims provider trusts**. In addition, AD DS forests that are not trusted by the forest that AD FS lives in can also be modeled as local claims provider trusts. You can create local claims provider trusts by using Windows PowerShell.

LDAP directories (local claims provider trusts) can co-exist with AD directories (claims provider trusts) on the same AD FS server, within the same AD FS farm, therefore, a single instance of AD FS is capable of authenticating and authorizing access for users that are stored in both AD and non-AD directories.

Only forms-based authentication is supported for authenticating users from LDAP directories. Certificate-based and Integrated Windows authentication are not supported for authenticating users in LDAP directories.

All passive authorization protocols that are supported by AD FS, including SAML, WS-Federation, and OAuth are also supported for identities that are stored in LDAP directories.

The WS-Trust active authorization protocol is also supported for identities that are stored in LDAP directories.

## Configure AD FS to authenticate users stored in an LDAP directory

To configure your AD FS farm to authenticate users from an LDAP directory, you can complete the following steps:

1. First, configure a connection to your LDAP directory using the **New-AdfsLdapServerConnection** cmdlet:

    ```
    $DirectoryCred = Get-Credential
    $vendorDirectory = New-AdfsLdapServerConnection -HostName dirserver -Port 50000 -SslMode None -AuthenticationMethod Basic -Credential $DirectoryCred
    ```

    Note

    It is recommended that you create a new connection object for each LDAP server you want to connect to. AD FS can connect to multiple replica LDAP servers and automatically fail over in case a specific LDAP server is down. For such a case, you can create one AdfsLdapServerConnection for each of these replica LDAP servers and then add the array of connection objects using the -**LdapServerConnection** parameter of the **Add-AdfsLocalClaimsProviderTrust** cmdlet.

    **NOTE:** Your attempt to use Get-Credential and type in a DN and password to be used to bind to an LDAP instance might result in a failure because of the user interface requirement for specific input formats, for example, domain\username or user@domain.tld. You can instead use the ConvertTo-SecureString cmdlet as follows (the example below assumes uid=admin,ou=system as the DN of the credentials to be used to bind to the LDAP instance):

    ```
    $ldapuser = ConvertTo-SecureString -string "uid=admin,ou=system" -asplaintext -force
    $DirectoryCred = Get-Credential -username $ldapuser -Message "Enter the credentials to bind to the LDAP instance:"
    ```

    Then enter the password for the uid=admin and complete the rest of the steps.
2. Next, you can perform the optional step of mapping LDAP attributes to the existing AD FS claims using the **New-AdfsLdapAttributeToClaimMapping** cmdlet. In the example below, you map givenName, Surname, and CommonName LDAP attributes to the AD FS claims:

    ```
    #Map given name claim
    $GivenName = New-AdfsLdapAttributeToClaimMapping -LdapAttribute givenName -ClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname"
    # Map surname claim
    $Surname = New-AdfsLdapAttributeToClaimMapping -LdapAttribute sn -ClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname"
    # Map common name claim
    $CommonName = New-AdfsLdapAttributeToClaimMapping -LdapAttribute cn -ClaimType "http://schemas.xmlsoap.org/claims/CommonName"
    ```

    This mapping is done in order to make attributes from the LDAP store available as claims in AD FS in order to create conditional access control rules in AD FS. It also enables AD FS to work with custom schemas in LDAP stores by providing an easy way to map LDAP attributes to claims.
3. Finally, you must register the LDAP store with AD FS as a local claims provider trust using the **Add-AdfsLocalClaimsProviderTrust** cmdlet:

    ```
    Add-AdfsLocalClaimsProviderTrust -Name "Vendors" -Identifier "urn:vendors" -Type Ldap
    
    # Connection info
    -LdapServerConnection $vendorDirectory
    
    # How to locate user objects in directory
    -UserObjectClass inetOrgPerson -UserContainer "CN=VendorsContainer,CN=VendorsPartition" -LdapAuthenticationMethod Basic
    
    # Claims for authenticated users
    -AnchorClaimLdapAttribute mail -AnchorClaimType "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/upn" -LdapAttributeToClaimMapping @($GivenName, $Surname, $CommonName)
    
    # General claims provider properties
    -AcceptanceTransformRules "c:[Type != ''] => issue(claim=c);" -Enabled $true
    
    # Optional - supply user name suffix if you want to use Ws-Trust
    -OrganizationalAccountSuffix "vendors.contoso.com"
    ```

    In the example above, you are creating a local claims provider trust called "Vendors". You are specifying connection information for AD FS to connect to the LDAP directory this local claims provider trust represents by assigning `$vendorDirectory` to the `-LdapServerConnection` parameter. Note that in step one, you've assigned `$vendorDirectory` a connection string to be used when connecting to your specific LDAP directory. Finally, you are specifying that the `$GivenName`, `$Surname`, and `$CommonName` LDAP attributes (which you mapped to the AD FS claims) are to be used for conditional access control, including multi-factor authentication policies and issuance authorization rules, as well as for issuance via claims in AD FS-issued security tokens. In order to use active protocols like Ws-Trust with AD FS, you must specify the OrganizationalAccountSuffix parameter, which enables AD FS to disambiguate between local claims provider trusts when servicing an active authorization request.