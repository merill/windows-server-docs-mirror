---
layout: Conceptual
title: Configure Network Device Enrollment Service to use a domain user account for Active Directory Certificate Services | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/create-domain-user-account-ndes-service-account
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how to configure a service account for the Network Device Enrollment Service (NDES) as a role service with certificates based on Simple Certificate Enrollment Protocol (SCEP)
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2023-04-03T00:00:00.0000000Z
locale: en-us
document_id: 6ea9a684-ba48-86db-2df4-1a5cf765d0ce
document_version_independent_id: 6ea9a684-ba48-86db-2df4-1a5cf765d0ce
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/create-domain-user-account-ndes-service-account.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/create-domain-user-account-ndes-service-account
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/create-domain-user-account-ndes-service-account.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: e95636cc-47a2-89a0-ad55-734ca8d0e33b
---

# Configure Network Device Enrollment Service to use a domain user account for Active Directory Certificate Services | Microsoft Learn

It's recommended that you configure NDES to specify a user account, which requires extra steps. If you select the built-in application pool identity, no other configuration is required.

In this article, learn how to configure Network Device Enrollment Service (NDES) to run as a specified service account.

The NDES allows routers and other network devices to obtain certificates based on the Simple Certificate Enrollment Protocol (SCEP) without using domain credentials.

SCEP was developed to support the secure, scalable issuance of certificates to network devices by using existing certification authorities (CAs). The protocol supports CA and registration authority public key distribution, enrollment, and certificate revocation queries.

For more information about NDES and how it works with certificates based using the Simple Certificate Enrollment Protocol, see [What is Network Device Enrollment Service for Active Directory Certificate Services?](network-device-enrollment-service-overview).

## Prerequisites

After installing the NDES role service for Active Directory Certificate Services (AD CS), verify that you meet the following prerequisites:

- Be a domain user account.
- Be a member of the local *IIS\_IUSRS* group.
- Have Request permissions on the configured Certificate Authority (CA).
- Have Read and Enroll permissions on the NDES certificate template, which is configured automatically.
- If you're using a CNAME or load balanced network name, configure a service principle name (SPN) in Active Directory Domain Services.

## Create a domain user account to act as the NDES service account

You next need to create a domain user account as the NDES service account.

1. Sign in to the domain controller or administrative computer with Active Directory Domain Services Remote Server Administration Tools installed. Open **Active Directory Users and Computers** by using an account that has permissions to add users to the domain.
2. In the console tree, expand the structure until you see the container where you want to create the user account. For example, some organizations have a Services OU or similar account. Right-click the container, select **New**, and then select **User**.
3. In the **New Object - User** text boxes, enter appropriate names for all the fields so that it's clear that you're creating a user account. Be sure to follow your organization's policy for creating a service account, if such a policy exists. As an example, you could enter the following, and then select **Next**.

    - **First name**: *Ndes*
    - **Last name**: *Service*
    - **User logon name**: *NdesService*
4. Ensure that you set a complex password for the account and confirm the password. Configure the password options to correspond to your organization's security policies regarding service accounts. If the password is configured to expire, you should have a process in place to ensure that you reset the password at the required intervals.
5. Select **Next**, and then select **Finished**.

Tip

- You can also use the [New-ADUser](/en-us/powershell/module/activedirectory/new-aduser) Windows PowerShell command to add a domain user account.
- Depending upon your Active Directory Domain Service (AD DS) configuration, you may be able to implement a Managed Service Account or Group Managed Service Account for NDES. For more information about Managed Service Accounts, see [Managed Service Accounts](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd378925%28v=ws.10%29). For more information about Group Managed Service Accounts, see [Group Managed Service Accounts Overview](/en-us/windows-server/security/group-managed-service-accounts/group-managed-service-accounts-overview).

## Add the NDES service account to the local *IIS\_IUSRS* group

After you successfully created a domain user account as the NDES service account, you must add this NDES service account to the local *IIS\_IUSRS* group.

1. On the server that is hosting the NDES service, open **Computer Management** (*compmgmt.msc*).
2. In the Computer Management console tree, under **System Tools**, expand **Local User and Groups**. Select **Groups**.
3. In the details pane, select *IIS\_IUSRS*.
4. In the **General** tab, select **Add**.
5. In the **Select Users, Computers, Service Accounts, or Groups** text box, type the user sign-in name for the account that you configured to be the service account.
6. Select **Check Names**, select **OK** twice, and then close **Computer Management**.

Tip

You can also use `net localgroup IIS_IUSRS <domain>\<username> /Add` to add the NDES service account to the local *IIS\_IUSRS* group. The command prompt or Windows PowerShell must be run as Administrator. For more information, see the[Add-LocalGroupMember](/en-us/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember)] PowerShell command.

## Set up request permission on the CA

NDES service accounts need to request permission on the CA that is to be used by NDES.

1. On the CA that is to be used by NDES, open the CA console with an account that has Manage CA permissions.
2. Open the Certification Authority console. Right-click the CA, and then select **Properties**.
3. On the **Security** tab, you can see the accounts that have Request Certificates permissions. By default the group **Authenticated Users** has this permission. The service account that you created is a member of **Authenticated Users** when it's in use. You don't need to grant more permissions, if **Authenticated Users** has the Request Certificates permission. However, if that isn't the case, you should grant the NDES service account Request Certificates permission on the CA. To do so:

    - Select **Add**.
    - In the **Select Users, Computers, Service Accounts, or Groups** text box, type the name of the NDES service account, and select **Check Names**, and then select **OK**.
    - Ensure that NDES service account is selected. Ensure that the **Allow** check box that corresponds to **Request Certificates** is selected. Select **OK**.

## Verify whether it's necessary to set a service principal name for NDES

You need to configure a service principal name (SPN) in Active Directory if you're using a load balancer or virtual name. In this section, learn how to determine whether it's necessary to set an SPN in Active Directory.

- If you're using a single NDES server and its actual hostname (most common scenario), the account doesn't need an SPN registered. The computer account's default SPNs for HOST/computerFQDN cover this case. If you're using all other defaults (particularly around IIS kernel-mode authentication), you can skip ahead to the next section of this article.
- If you're using a custom A record as a hostname, or load balancing with a Virtual IP, an SPN needs to be registered against the NDES service account (SCEPSvc). To register an SPN against the NDES service account:

    1. Use the Setspn command syntax of: `Setspn -s HTTP/<computerfqdn> <domainname\accountname>` when entering your commands. For example, your domain is `Fabrikam.com`, your NDES CNAME is `NDESFARM`, and you're using a service account named `SCEPSvc`. In the example, you would run the following commands.

        - `Setspn -s HTTP/NDESFARM.fabrikam.com fabrikam\SCEPSvc`
        - `Setspn -s HTTP/NDESFARM fabrikam\SCEPSvc`
    2. Then disable IIS Kernel-mode Authentication for the site.

## Set up the NDES role service

After installation completes, you need to do a few steps to finish configuring the NDES computer.

If NDES is installed on a CA, you don't have the opportunity to select a CA because the local CA is used.

When you install NDES on a computer that isn't a CA, you must select the target CA. You can select the CA using the CA name or by the computer name.

To select the CA:

1. Open AD CS Configuration from Server Manager.
2. Select on **CA for NDES**
3. Select **CA name** or **Computer name**, and then select **Select**.
4. The option you choose determines the type of dialog box that is presented next:

    - If you clicked **CA name**, you're presented with the **Select Certification Authority** dialog box, which has a list of CAs from which you can choose.

        or
    - If you clicked **Computer name**, you see the **Select Computer** dialog box where you can set the **Locations** and enter the computer name that you want to specify as the CA.

You're now ready to complete setup of the NDES role service. The remaining steps are verifying the Registration Authority information and setting up cryptography.

1. Registration Authority (RA) information that you provide is used to construct the signing certificate that is issued to the service. In Server Manager. Select RA information.
2. Check all fields and confirm that the RA information is correct (or is set to the defaults).

NDES uses two certificates and their keys to enable device enrollment. Organizations can use different Cryptographic Service Providers (CSPs) to store these keys, or change the length of the keys that is used by the service. Only Cryptographic Application Programming Interface (CryptoAPI) Service Providers are supported for the RA keys—Cryptography API; Next Generation (CNG) providers aren't supported.

1. To configure the cryptography, in Server Manager, select Cryptography for NDES.
2. Enter the values for Signature Key Provider and/or Encryption Key Provider and decide on key length values.
3. Continue through the wizard to complete the installation of NDES.

Now that you've configured the role service, you can learn detailed information about NDES configuration and operation see [Network Device Enrollment Service (NDES) in Active Directory Certificate Services (AD CS)](/en-us/archive/technet-wiki/9063.active-directory-certificate-services-ad-cs-network-device-enrollment-service-ndes).

Tip

If you make configuration changes for NDES or to the certificate templates that are used by NDES, you must stop and restart NDES, IIS and the CA service.