---
layout: Conceptual
title: Install the Federation Service Proxy Role Service | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/install-the-federation-service-proxy-role-service
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Install the Federation Service Proxy Role Service'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: install-set-up-deploy
locale: en-us
document_id: 62d63acf-f630-68d7-fd34-8aef52509d50
document_version_independent_id: 04b1b178-b577-2773-8157-f8709351b1af
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Install-the-Federation-Service-Proxy-Role-Service.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/install-the-federation-service-proxy-role-service
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Install-the-Federation-Service-Proxy-Role-Service.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b4e67939-f680-4441-4fe1-5b088cdde8a4
---

# Install the Federation Service Proxy Role Service | Microsoft Learn

After you configure a computer with the prerequisite applications and certificates, you are ready to install the Federation Service Proxy role service of Active Directory Federation Services (AD FS). You can use the following procedure to install the Federation Service Proxy role service. When you install the Federation Service Proxy role service on a computer, that computer becomes a federation server proxy.

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

### To install the Federation Service Proxy role service using the Server Manager

1. On the **Start** screen, type**Server Manager**, and then press ENTER.
2. Click **Manage**, and then click **Add Roles and Features** to start the Add Roles and Features Wizard.
3. On the **Before you begin** page, click **Next**.
4. On the **Select installation type** page, click **Role-based or Feature-based installation**, and click **Next**.
5. On the **Select destination server** page, click **Select a server from the server pool**, verify that the target computer is highlighted, and then click **Next**.
6. On the **Select server roles** page, click **Remote Access**, and then click next.

    Note

    If you are prompted to install additional .NET Framework or Windows Process Activation Service features, click **Add Features** to install them.
7. On the **Select role services** page, select the **Federation Service Proxy** check box, and then click **Next**.
8. After you verify the information on the **Confirm installation selections** page, select the **Restart the destination server automatically if required** check box, and then click **Install**.
9. On the **Installation progress** page, verify that everything installed correctly, and then click **Close**.

### To install the Federation Service Proxy role service using PowerShell

1. Open Windows PowerShell (Run as Administrator)
2. Type the following command and press **Enter**:

    ```
    Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
    ```

## Additional references

- [Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server)
- [Checklist: Setting Up a Federation Server Proxy](checklist--setting-up-a-federation-server-proxy)