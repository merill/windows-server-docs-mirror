---
layout: Conceptual
title: Add a Federation Server to a Federation Server Farm | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/add-a-federation-server-to-a-federation-server-farm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Add a Federation Server to a Federation Server Farm'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 6d9663e6-ab72-ea9d-2a89-467e6328e926
document_version_independent_id: 64a7e6af-8b9f-0af6-87c5-05ee529368c2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Add-a-Federation-Server-to-a-Federation-Server-Farm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/add-a-federation-server-to-a-federation-server-farm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Add-a-Federation-Server-to-a-Federation-Server-Farm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: e25b911b-d8af-7e64-2e12-c8a12df003d3
---

# Add a Federation Server to a Federation Server Farm | Microsoft Learn

After you install the Federation Service role service and configure the required certificates on a computer, you are ready to configure the computer to become a federation server. You can use the following procedure to join a computer to a new federation server farm.

You join a computer to a farm with the AD FS Federation Server Configuration Wizard. When you use this wizard to join a computer to an existing farm, the computer is configured with a read-only copy of the AD FS configuration database and it must receive updates from a primary federation server.

Note

For the Federated Web Single-Sign-On (SSO) design, you must have at least one federation server in the account partner organization and at least one federation server in the resource partner organization. For more information, see [Where to Place a Federation Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807127%28v=ws.11%29).

Membership in **Administrators**, or equivalent, on the local computer is the minimum required to complete this procedure. Review details about using the appropriate accounts and group memberships at [Local and Domain Default Groups](/en-us/previous-versions/orphan-topics/ws.10/dd728026%28v=ws.10%29) (http://go.microsoft.com/fwlink/?LinkId=83477).

### To add a federation server to a federation server farm

1. There are two ways to start the AD FS Federation Server Configuration Wizard. To start the wizard, do one of the following:

    - After the Federation Service role service installation is complete, open the AD FS Management snap-in and click the **AD FS Federation Server Configuration Wizard** link on the **Overview** page or in the **Actions** pane.
    - Anytime after the setup wizard is complete, open Windows Explorer, navigate to the **C:\Windows\ADFS** folder, and double-click **FsConfigWizard.exe**.
2. On the **Welcome** page, verify that **Add a federation server to an existing Federation Service** is selected, and then click **Next**.
3. If the AD FS database that you selected already exists, the **Existing AD FS Configuration Database Detected** page appears. If that occurs, click **Delete database**, and then click **Next**.

Caution

Select this option only when you are sure that the data in this AD FS database is not important or that it is not used in a production federation server farm.
4. On the **Specify the Primary Federation Server and Service Account** page, under **Primary federation server name**, type the computer name of the primary federation server in the farm, and then click **Browse**. In the **Browse** dialog box, locate the domain account that is used as the service account by all other federation servers in the existing federation server farm, and then click **OK**. Type the password and confirm it, and then click **Next**:

    Note

    For more information about specifying a service account for a federation server farm, see [Manually Configure a Service Account for a Federation Server Farm](manually-configure-a-service-account-for-a-federation-server-farm). Each federation server in the federation server farm must specify the same service account for the farm to be operational. For example, if the service account that was created was contoso\ADFS2SVC, each computer you configure for the federation server role and that will participate in the same farm must specify contoso\ADFS2SVC at this step in the Federation Server Configuration Wizard for the farm to be operational.
5. On the **Ready to Apply Settings** page, review the details. If the settings appear to be correct, click **Next** to begin configuring AD FS with these settings.
6. On the **Configuration Results** page, review the results. When all the configuration steps are finished, click **Close** to exit the wizard.

## Additional references

[Checklist: Setting Up a Federation Server](checklist--setting-up-a-federation-server)