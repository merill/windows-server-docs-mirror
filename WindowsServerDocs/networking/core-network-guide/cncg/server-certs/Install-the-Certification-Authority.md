---
layout: Conceptual
title: Install the Certification Authority on Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/cncg/server-certs/install-the-certification-authority
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to install Active Directory Certificate Services so that you can enroll a server certificate to servers.
ms.topic: install-set-up-deploy
author: robinharwood
ms.author: roharwoo
ms.date: 2025-04-15T00:00:00.0000000Z
locale: en-us
document_id: 87da2935-68c0-c3ef-21f7-1819700aa734
document_version_independent_id: 171eacc9-4d7b-bfe0-e191-c382125def84
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Install-the-Certification-Authority.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/cncg/server-certs/install-the-certification-authority
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/cncg/server-certs/Install-the-Certification-Authority.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: dfec531a-d889-9c7b-6776-94da3bf50b42
---

# Install the Certification Authority on Windows Server | Microsoft Learn

Follow these steps to set up Active Directory Certificate Services (AD CS). This allows you to issue server certificates for servers running Network Policy Server (NPS), Routing and Remote Access Service (RRAS), or both.

## Prerequisites

- Membership in both the **Enterprise Admins** and the root domain's **Domain Admins** group is the minimum requirement to complete this procedure.
- Before you install Active Directory Certificate Services, **you must name the computer, configure the computer with a static IP address, and join the computer to the domain**.

    - For more information on how to accomplish these tasks, see the Windows Server [Core network components](/en-us/windows-server/networking/core-network-guide/core-network-guide).
    - To perform this procedure, the computer on which you're installing AD CS must be joined to a domain where Active Directory Domain Services (AD DS) is installed.

## Install Active Directory Certificate Services using PowerShell

To use Windows PowerShell to install Active Directory Certificate Services, complete the following steps.

1. Open Windows PowerShell and type the following command, and then press ENTER.

    ```powershell
    Install-WindowsFeature -Name ADCS-Cert-Authority -IncludeManagementTools
    ```
2. After AD CS is installed, type the following command and press ENTER.

    ```powershell
    Install-AdcsCertificationAuthority -CAType EnterpriseRootCA  
    ```

For more information about this cmdlet, and its available parameters, see [Install-AdcsCertificationAuthority](/en-us/powershell/module/adcsdeployment/install-adcscertificationauthority).

## Install Active Directory Certificate Services using Server Manager

To use Server Manager to install Active Directory Certificate Services, complete the following steps.

1. Log on as a member of both the Enterprise Admins group and the root domain's Domain Admins group.
2. In Server Manager, select **Manage**, and then select **Add Roles and Features** to open the Add Roles and Features Wizard.
3. In **Before You Begin**, select **Next**.

    Note

    The **Before You Begin** page of the Add Roles and Features Wizard isn't displayed if you have previously selected **Skip this page by default**.
4. In **Select Installation Type**, ensure that **Role-Based or feature-based installation** is selected, and then select **Next**.
5. In **Select destination server**, ensure that **Select a server from the server pool** is selected. In **Server Pool**, ensure that the local computer is selected. Select **Next**.
6. In **Select Server Roles**, in **Roles**, select **Active Directory Certificate Services**. When you're prompted to add required features, select **Add Features**, and then select **Next**.
7. In **Select features**, select **Next**.
8. In **Active Directory Certificate Services**, read the provided information, and then select **Next**.
9. In **Confirm installation selections**, select **Install**. Don't close the wizard during the installation process. When installation is complete, select **Configure Active Directory Certificate Services on the destination server**. The AD CS Configuration wizard opens. Read the credentials information and, if needed, provide the credentials for an account that is a member of the Enterprise Admins group. Select **Next**.
10. In **Role Services**, select **Certification Authority**, and then select **Next**.
11. On the **Setup Type** page, verify that **Enterprise CA** is selected, and then select **Next**.
12. On the **Specify the type of the CA** page, verify that **Root CA** is selected, and then select **Next**.
13. On the **Specify the type of the private key** page, verify that **Create a new private key** is selected, and then select **Next**.
14. On the **Cryptography for CA** page, keep the default settings for CSP (**RSA#Microsoft Software Key Storage Provider**) and hash algorithm (**SHA2**), and determine the best key character length for your deployment. Large key character lengths provide optimal security; however, they can impact server performance and might not be compatible with legacy applications. It's recommended that you keep the default setting of 2048. Select **Next**.
15. On the **CA Name** page, keep the suggested common name for the CA or change the name according to your requirements. Ensure that you're certain the CA name is compatible with your naming conventions and purposes, because you can't change the CA name after you have installed AD CS. Select **Next**.
16. On the **Validity Period** page, in **Specify the validity period**, type the number and select a time value (Years, Months, Weeks, or Days). The default setting of five years is recommended. Select **Next**.
17. On the **CA Database** page, in **Specify the database locations**, specify the folder location for the certificate database and the certificate database log. If you specify locations other than the default locations, ensure that the folders are secured with access control lists (ACLs) that prevent unauthorized users or computers from accessing the CA database and log files. Select **Next**.
18. In **Confirmation**, select **Configure** to apply your selections, and then select **Close**.