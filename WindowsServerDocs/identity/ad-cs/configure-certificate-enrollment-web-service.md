---
layout: Conceptual
title: Configure the Certificate Enrollment Web Service role service | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-cs/configure-certificate-enrollment-web-service
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how to configure the Certificate Enrollment Web Service role service to enable secure certificate enrollment over HTTPS.
author: robinharwood
ms.topic: how-to
ms.author: roharwoo
ms.date: 2025-03-27T00:00:00.0000000Z
locale: en-us
document_id: bbb9c257-37e5-6dc3-3ec9-b681a22c587d
document_version_independent_id: bbb9c257-37e5-6dc3-3ec9-b681a22c587d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-cs/configure-certificate-enrollment-web-service.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-cs/configure-certificate-enrollment-web-service
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-cs/configure-certificate-enrollment-web-service.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: af853223-8ed5-3a6e-8a77-d473f4314a30
---

# Configure the Certificate Enrollment Web Service role service | Microsoft Learn

The Certificate Enrollment Web Service is an Active Directory Certificate Services (AD CS) role service that enables users and computers to enroll for and renew certificates even when the computer isn't a member of a domain or if a domain-joined computer isn't connected to the domain.

Together with the Certificate Enrollment Policy Web Service, this enables policy-based automatic certificate enrollment for users and computers.

This article describes how to configure the Certificate Enrollment Web Service.

## Prerequisites

- The Certificate Enrollment Web Service role is installed. A couple notes about installation:

    - The administrator who performs the installation must be a member of the Enterprise Admins group.
    - The administrator who installs the Certificate Enrollment Web Service must have Request Certificates permissions on the target certification authority (CA).
    - The computer on which the Certificate Enrollment Web Service will be installed must be a member of the domain.
- An enterprise certification authority (CA) on a computer running Windows Server.
- Client computers must be running at least Windows 10 or Windows Server 2016.
- A Server Authentication certificate installed for HTTPS.

Note

The Web Server (IIS) role service with the Microsoft .NET Framework are automatically added during the Certificate Enrollment Web Service installation, if they aren't already installed.

## Certificate Enrollment Web Service configuration

After the Certificate Enrollment Web Service is installed, it must be configured. The following sections describe how to complete configuration.

### Configure the CA role service

If the CA role service is installed on the local computer, then the local computer is automatically selected as the CA. However, the Certificate Enrollment Web Service and CA role service can't be installed at the same time.

Important

If you intend to install both the Certificate Enrollment Web Service and CA role service, complete the CA role service installation first.

The following prerequisites apply to configuring the CA for the Certificate Enrollment Web Service:

- The Certificate Enrollment Web Service can be configured to work with an enterprise CA on the same or on a different computer.
- The Certificate Enrollment Web Service can't be configured to work with a standalone CA—an enterprise CA is required.

Configuration tips:

- If you want to avoid having to trust the Certificate Enrollment Web Service account for delegation, and you need to process only certificate renewal requests, enable renewal-only mode by selecting **Configure the Certificate Enrollment Web Service for renewal-only mode**.
- If you want the Certificate Enrollment Web Service to process new certificate enrollment requests and certificate renewals, don't select **Configure the Certificate Enrollment Web Service for renewal-only mode.**
- Ensure the Certificate Enrollment Web Service account is trusted for delegation.
- You can install multiple instances of the Certificate Enrollment Web Service on a single computer. However, you can only install one instance by using Server Manager. To install a second instance, you must use the Windows PowerShell cmdlet [Install-AdcsEnrollmentWebService](/en-us/powershell/module/adcsdeployment/install-adcsenrollmentwebservice).

Note

If the certification authority that the Certificate Enrollment Web Service will be using has spaces in the name, such as Margies Travel Issuing CA, instead of Margies-Travel-Issuing-CA, then extra configuration steps are required after installation of the service. The extra steps required are documented in [Implementing Certificate Enrollment Web Services in Windows Server that uses an Issuing CA with spaces in the name](https://social.technet.microsoft.com/wiki/contents/articles/15668.implementing-certificate-enrollment-web-services-in-windows-server-2012-that-uses-an-issuing-ca-with-spaces-in-the-name.aspx).

### Set the authentication type for Certificate Enrollment Web Service

Clients communicating with the Certificate Enrollment Web Service must use one of the following authentication types:

- Windows integrated authentication
- Client certificate authentication
- User name and password authentication

See [Certificate Enrollment Web Service Guidance](/en-us/archive/technet-wiki/7734.certificate-enrollment-web-services-in-active-directory-certificate-services#authentication-method-considerations) for detailed descriptions of each authentication type.

### Allow key-based renewal for Certificate Enrollment Web Service

Key-based renewal mode is a feature that allows an existing valid certificate to be used to authenticate a certificate renewal request. This enables computers that aren't connected directly to the internal network the ability to automatically renewal an existing certificate.

For more information, see [Configure Certificate Enrollment Web Service for certificate key-based renewal on a custom port](/en-us/windows-server/identity/ad-cs/certificate-enrollment-certificate-key-based-renewal).

### Configure a service account

During Certificate Enrollment Web Service configuration, you can specify one of the following types of accounts as the service account:

- User account that acts as the service account (recommended)
- Built-in application pool identity of the Internet Information Services (IIS) installation on the local computer

Using a specific user account as the service account is the recommended configuration. However, there are more steps required to configure a user account as a service account. The user account that is to be configured as a service account must be:

- A domain account in the domain in which the Certificate Enrollment Web Services computer is a member.
- A member of the local IIS\_IUSRS group on which the Certificate Enrollment Web Service is installed.
- Configured with a service principal name (SPN), if Kerberos authentication is selected or delegation required because the Certificate Enrollment Web Service is hosted on a different computer than the one running the CA role service.
- Trusted for delegation for the host service and the Remote Procedure Call system service (RPCSS), if Certificate Enrollment Web Service is installed on a different computer than the CA, and if new certificates are to be issued by the Certificate Enrollment Web Service.

#### Create a domain user account to act as the service account

1. Sign in to the domain controller or administrative computer with Active Directory Domain Services Remote Server Administration Tools installed. Open **Active Directory Users and Computers** by using an account that has permissions to add users to the domain.
2. In the console tree, locate the container where you want to create the user account. For example, some organizations have a Services OU or similar account. Right-select the container, select **New**, and then select **User**.
3. In the **New Object - User** text boxes, enter appropriate names for all the fields so that it's clear that you're creating a user account. Be sure to follow your organization's policy for creating a service account, if such a policy exists. As an example, you could enter the following, and then select **Next**.

    1. **First name**: **CES**
    2. **Last name**: **Service**
    3. **User logon name**: **CES**
4. Set a complex password for the account and confirm the password. Configure the password options to correspond to your organization's security policies regarding service accounts.
5. Select **Next**, and then select **Finished**.

Tip

You can also use the [Windows PowerShell cmdlet New-ADUser](/en-us/powershell/module/activedirectory/new-aduser) to add a domain user account.

#### Add the service account to the local IIS\_IUSERS group

1. On the server that is hosting Certificate Enrollment Web Service, open **Computer Management** (compmgmt.msc).
2. In the Computer Management console tree, under **System Tools**, expand **Local User and Groups**, and then select **Groups**.
3. In the details pane, double-click **IIS\_IUSRS**.
4. On the **General** tab, select **Add**.
5. In the **Select Users, Computers, Service Accounts, or Groups** text box, type the user sign-in name for the account that you configured to be the service account.
6. Select **Check Names**, select **OK** twice, and then close **Computer Management**.

Tip

You can also type `net localgroup IIS_IUSRS <domain>\<username> /Add</` to add the service account for the Certificate Enrollment Web Service to the local IIS\_IUSRS group. The command prompt or Windows PowerShell must be run as an administrator. See [Add a member to a local group](https://technet.microsoft.com/library/cc739265.aspx) for more information.

#### Set a service principal name for the service account

1. Ensure that you're using an account that's a member of the Domain Admins group. Open Windows PowerShell or a Command Prompt window as an administrator.
2. Use the following command syntax to register the server principal name (SPN) for the service account: `setspn -s http/<computername> <domainname>\<accountname>`. For example, to register a service account with the sign-in name CES in the cpandl.com domain for a computer named CES1, you'd run the following command: `setspn -s http/CES1.cpandl.com cpandl\CES`.

#### Configure the Certificate Enrollment Web Service user account for constrained delegation

1. Sign in to the domain controller or administrative computer with Active Directory Domain Services Remote Server Administration Tools installed. Open **Active Directory Users and Computers** by using an account that has permissions to add users to the domain.
2. In the console tree, expand the structure until you see the container that holds the user account. Select that container.
3. In the details pane, right-select the user account that is the service account for the Certificate Enrollment Web Service, and then select **Properties**.
4. On the **Delegation** tab, select **Trust this user for delegation to specified services only**.

    Note

    The **Delegation** tab is only available in the user account properties after you've created an SPN for the user account.
5. Ensure that **Use Kerberos only** is selected (if the authentication type was set to Windows integrated authentication during installation) or **Use any authentication protocol** (if the authentication type was set to Client certificate authentication during installation), and then select **Add**.
6. In the **Add Services** dialog box, select **Users or Computers**.
7. In the **Select Users or Computers** dialog box, type the name of the computer that is hosting the CA. Select **Check Names**, and then select **OK**.
8. In the **Add Services** dialog box, press the Ctrl key, and then select both of the following services:

    - **HOST**
    - **rpcss**

    Select **OK** twice.
9. Close Active Directory Users and Computers.

If you specified the default application pool instead of a user account to act as the service account for Certificate Enrollment Web Service, you must trust the computer account on which the Certificate Enrollment Web Service is installed for delegation.

Important

You need to perform the following procedure only if you selected **Use the built-in application pool identity** when you specified the service account for the Certificate Enrollment Web Service.

#### Configure the Certificate Enrollment Web Service computer account for constrained delegation

1. Sign in to the domain controller or administrative computer with Active Directory Domain Services Remote Server Administration Tools installed. Open **Active Directory Users and Computers** by using an account that has permissions to add users to the domain.
2. In the console tree, expand the structure until you see the container that holds the computer account that's hosting the Certificate Enrollment Web Service. Select that container.
3. In the details pane, right-click the computer account that is hosting the Certificate Enrollment Web Service, and then click **Properties**.
4. On the **Delegation** tab, select **Trust this computer for delegation to the specified services only**.
5. Ensure that **Use Kerberos only** is selected, and then select **Add**.
6. In the **Add Services** dialog box, select **Users or Computers**.
7. In the **Select Users or Computers** dialog box, type the name of the computer that's hosting the Certificate Enrollment Web Service. Select **Check Names**, and then select **OK**.
8. In the **Add Services** dialog box, press the Ctrl key, and then select both of the following services:

    - **HOST**
    - **rpcss**

    Select **OK** twice.
9. Close Active Directory Users and Computers.

## Select a server certificate

The Certificate Enrollment Web Service and the Certificate Enrollment Policy Web Service must use Secure Sockets Layer (SSL) for communication with clients (by using HTTPS). Each service must have a valid certificate that has an enhanced key usage (EKU) policy of Server Authentication in the local computer certificate store.

Note

If you haven't yet provided an SSL certificate to the server that is hosting the Certificate Enrollment Web Service, you can do so by following the instructions in [Configure SSL/TLS on a Web site in the domain with an Enterprise CA](https://social.technet.microsoft.com/wiki/contents/articles/12485.configure-ssltls-on-a-web-site-in-the-domain-with-an-enterprise-ca.aspx).

## Complete configuration

If you enabled renewal-only mode, you need to complete the following extra configuration steps.

- Update CA permissions
- Set the CA policy module flag

### Update CA permissions

1. On the CA, sign in as a CA administrator.
2. Open the Certification Authority console.
3. Right-select the CA, and then select **Properties**.
4. On the **Security** tab, select **Add**.
5. In the **Select Users, Computers, Service Accounts, or Groups** dialog box, type the name of service account for the Certificate Enrollment Service. Select **Check Names**, and then select **OK**.

    Note

    If you assigned the built-in application pool as the service account, enter the computer account name that's hosting the Certificate Enrollment Web Service.
6. In the **CA Properties** dialog box, under **Group or user names**, select the service account name for the Certificate Enrollment Web Service. Ensure that the **Allow** check box is selected for **Read** permission. Clear the **Allow** check box for **Request Certificates** permission (which is selected by default), and then select **OK**.
7. Close the Certification Authority console.

#### Set the CA policy module flag

1. On the CA, sign in as a CA administrator.
2. Open a Command Prompt window or Windows PowerShell as an administrator.
3. Run `certutil | findstr "Config"` and note the output of the CA Configuration.
4. Run `certutil -config "<CAConfig>" -setreg policy\EditFlags +EDITF_ENABLERENEWONBEHALFOF`, where `<CAConfig\>` is the actual CA Config information that was returned in the previous step.
5. Restart the CA service. To do so from a command prompt, run `net stop certsvc && net start certsvc`. To restart from Windows PowerShell, run `restart-service certsvc`.