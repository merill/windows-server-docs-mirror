---
layout: Conceptual
title: Create a Custom File Management Task | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/create-custom-file-management-task
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to create a custom file management task and custom tasks.
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 22512da5-9596-0c89-cbdd-9664cf1d2fb4
document_version_independent_id: 817acc98-a008-a83c-d0bf-e24ef8254cbf
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/create-custom-file-management-task.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/create-custom-file-management-task
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/create-custom-file-management-task.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 91f72bfb-3434-067d-95e8-a2dad18a4b78
---

# Create a Custom File Management Task | Microsoft Learn

Expiration is not always a desired action to be performed on files. File management tasks allow you to run custom commands as well.

Note

This procedure assumes that you are familiar with file management tasks, and therefore only covers the **Action** tab where custom settings are configured.

## To create a custom task

1. Click the **File Management Tasks** node.
2. Right-click **File Management Tasks**, and then click **Create File Management Task** (or click **Create File Management Task** in the **Actions** pane). This opens the **Create File Management Task** dialog box.
3. On the **Action** tab, enter the following information:

    - **Type**. Select **Custom** from the drop-down menu.
    - **Executable**. Type or browse to a command to run when the file management task processes files. This executable must be set to be writable by Administrators and System only. If any other users have write access to the executable, it will not run correctly.
    - **Command settings**. To configure the arguments passed to the executable when a file management job processes files, edit the text box labeled **Arguments**. To insert additional variables in the text, place the cursor in the location in the text box where you want to insert the variable, select the variable that you want to insert, and then click **Insert Variable**. The text that is in brackets inserts variable information that the executable can receive. For example, the [Source File Path] variable inserts the name of the file that should be processed by the executable. Optionally, click the **Working directory** button to specify the location of the custom executable.
    - **Command Security**. Configure the security settings for this executable. By default, the command is run as Local Service, which is the most restrictive account available.
4. Click **OK**.

## Additional References

- [Classification Management](classification-management)
- [File Management Tasks](file-management-tasks)