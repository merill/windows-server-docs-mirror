---
layout: Conceptual
title: Connect to a Remote Computer | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/connect-to-remote-computer
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to connect to a remote computer to manage storage resources from File Server Resource Manager
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 51fb8f77-373c-860b-786a-b5abd306a49c
document_version_independent_id: 18a25a5d-db35-bb6e-9b00-8a4c77df8cbf
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/connect-to-remote-computer.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/connect-to-remote-computer
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/connect-to-remote-computer.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e834929-0ce1-4c1d-9c81-fcb14721edfb
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/75670257-a3f0-4627-9981-8046f99219e6
platformId: 9a33ec15-e4ac-5225-8b76-dfe4bd70c381
---

# Connect to a Remote Computer | Microsoft Learn

To manage storage resources on a remote computer, you can connect to the computer from File Server Resource Manager. While you are connected, File Server Resource Manager allows you to manage quotas, screen files, manage classifications, schedule file management tasks, and generate reports with those remote resources.

Note

File Server Resource Manager can manage resources on either the local computer or a remote computer, but not both at the same time.

## To connect to a remote computer from File Server Resource Manager

1. In **Administrative Tools**, click **File Server Resource Manager**.
2. In the console tree, right-click **File Server Resource Manager**, and then click **Connect to Another Computer**.
3. In the **Connect to Another Computer** dialog box, click **Another computer**. Then type the name of the server you want to connect to (or click **Browse** to search for a remote computer).
4. Click **OK**.

Important

The **Connect to Another Computer** command is available only when you open File Server Resource Manager from **Administrative Tools**. When you access File Server Resource Manager from Server Manager, the command is not available.

## Additional considerations

To manage remote resources with File Server Resource Manager:

- You must be logged on to the local computer with a domain account that is a member of the **Administrators** group on the remote computer.
- The remote computer must be running Windows Server, and File Server Resource Manager must be installed.
- The **Remote File Server Resource Manager Management** exception on the remote computer must be enabled. Enable this exception by using Windows Firewall in Control Panel.

## Additional References

- [Managing Remote Storage Resources](managing-remote-storage-resources)