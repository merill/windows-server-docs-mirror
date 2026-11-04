---
layout: Conceptual
title: Install the Federation Service Role Service | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/install-the-federation-service-role-service
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Install the Federation Service Role Service'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: install-set-up-deploy
locale: en-us
document_id: 1f7b3c63-8f59-609d-b5ae-5360a72ebb9b
document_version_independent_id: a2694730-9c30-0bcd-2dfa-c0762f70eb2c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Install-the-Federation-Service-Role-Service.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/install-the-federation-service-role-service
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Install-the-Federation-Service-Role-Service.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ccfb153c-c136-8182-8033-3ff583f839a4
---

# Install the Federation Service Role Service | Microsoft Learn

Now that you have properly configured a computer with the prerequisite applications and certificates, you are ready to install the Federation Service role service of Active Directory Federation Services (AD FS). When you install the Federation Service on a computer, that computer becomes a federation server.

Note

For the Federated Web Single-Sign-On (SSO) design, you must have at least one federation server in the account partner organization and at least one federation server in the resource partner organization. For more information, see [Where to Place a Federation Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807127%28v=ws.11%29).

You can use the following procedure to install the Federation Service role service of AD FS on a computer that will become the first federation server or on a computer that will become a federation server for an existing federation server farm.

## Prerequisites

Verify that an SSL certificate with the private key has already been installed or imported into the local certificate store (Personal store) before you start this procedure. If you will be using a token-signing certificate that is issued by a certification authority (CA), verify that a token-signing certificate with the private key has already been installed or imported into the local certificate store (Personal store) before you start this procedure. As an alternative, you can create a self-signed, token-signing certificate using the Add Roles Wizard, as described in this procedure. For more information about token-signing certificates, see [Certificate Requirements for Federation Servers](../design/certificate-requirements-for-federation-servers).

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29).

#### To install the Federation Service role service

1. On the **Start** screen, type**Server Manager**, and then press ENTER.
2. Click **Manage**, and then click **Add Roles and Features** to start the Add Roles and Features Wizard.
3. On the **Before you begin** page, click **Next**.
4. On the **Select installation type** page, click **Role-based or Feature-based installation**, and click **Next**.
5. On the **Select destination server** page, click **Select a server from the server pool**, verify that the target computer is highlighted, and then click **Next**.
6. On the **Select server roles** page, click **Active Directory Federation Services**, and then click next.

    Note

    If you are prompted to install additional .NET Framework or Windows Process Activation Service features, click **Add Features** to install them.
7. On the **Select features** page, verify that the features are set, and then click **Next**.
8. On the **Active Directory Federation Service (AD FS)** page, click **Next**.
9. On the **Select role services** page, select the **Federation Service** check box, and then click **Next**.
10. On the **Web Server Role (IIS)** page, click **Next**.
11. On the **Select role services** page, click **Next**.
12. After you verify the information on the **Confirm installation selections** page, select the **Restart the destination server automatically if required** check box, and then click **Install**.
13. On the **Installation progress** page, verify that everything installed correctly, and then click **Close**.