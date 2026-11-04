---
layout: Conceptual
title: Manually Configure a Service Account for a Federation Server Farm | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/manually-configure-a-service-account-for-a-federation-server-farm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Manually Configure a Service Account for a Federation Server Farm'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: dde1639a-439a-a95e-028f-62fbbee058ec
document_version_independent_id: 357a5c2e-c4f8-d618-1740-5235d9a26a2a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Manually-Configure-a-Service-Account-for-a-Federation-Server-Farm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/manually-configure-a-service-account-for-a-federation-server-farm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Manually-Configure-a-Service-Account-for-a-Federation-Server-Farm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c9fa18ad-b0ad-ca85-b75d-089717795a86
---

# Manually Configure a Service Account for a Federation Server Farm | Microsoft Learn

If you intend to configure a federation server farm environment in Active Directory Federation Services (AD FS), you must create and configure a dedicated service account in Active Directory Domain Services (AD DS) where the farm will reside. You then configure each federation server in the farm to use this account. You must complete the following tasks in your organization when you want to allow client computers on the corporate network to authenticate to any of the federation servers in an AD FS farm using Windows Integrated Authentication.

Important

As of AD FS 3.0 (Windows Server 2012 R2), AD FS supports the use of a [Group Managed Service Account](../../ad-ds/manage/group-managed-service-accounts/group-managed-service-accounts/group-managed-service-accounts-overview) (gMSA) as the service account. This is the recommended option, as it removes the need for managing the service account password over time. This document covers the alternate case of using a traditional service account, such as in domains still running a Windows Server 2008 R2 or earlier domain functional level (DFL).

Note

You have to perform the tasks in this procedure only one time for the entire federation server farm. Later, when you create a federation server by using the AD FS Federation Server Configuration Wizard, you must specify this same account on the **Service Account** wizard page on each federation server in the farm.

#### Create a dedicated service account

1. Create a dedicated user/service account in the Active Directory forest that is located in the identity provider organization. This account is necessary for the Kerberos authentication protocol to work in a farm scenario and to allow pass-through authentication on each of the federation servers. Use this account only for the purposes of the federation server farm.
2. Edit the user account properties, and select the **Password never expires** check box. This action ensures that this service account's function is not interrupted as a result of domain password change requirements.

    Note

    Using the Network Service account for this dedicated account will result in random failures when access is attempted through Windows Integrated Authentication, as a result of Kerberos tickets not validating from one server to another.

#### To set the SPN of the service account

1. Because the application pool identity for the AD FS AppPool is running as a domain user/service account, you must configure the Service Principal Name (SPN) for that account in the domain with the Setspn.exe command-line tool. Setspn.exe is installed by default on computers running Windows Server 2008 . Run the following command on a computer that is joined to the same domain where the user/service account resides:

    ```
    setspn -a host/<server name> <service account>
    ```

    For example, in a scenario in which all federation servers are clustered under the Domain Name System (DNS) host name fs.fabrikam.com and the service account name that is assigned to the AD FS AppPool is named adfs2farm, type the command as follows, and then press ENTER:

    ```
    setspn -a host/fs.fabrikam.com adfs2farm
    ```

    It is necessary to complete this task only once for this account.
2. After the AD FS AppPool identity is changed to the service account, set the access control lists (ACLs) on the SQL Server database to allow Read access to this new account so that the AD FS AppPool can read the policy data.