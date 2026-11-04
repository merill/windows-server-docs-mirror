---
layout: Conceptual
title: Define File Groups for Screening | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/define-file-groups-for-screening
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to define file groups to create a namespace for file screen, file screen exception, or files by file group storage reports
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 0f465638-57fb-5017-b865-1845d855f692
document_version_independent_id: a15a0662-a4fe-a105-016d-c9e10ffbff54
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/define-file-groups-for-screening.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/define-file-groups-for-screening
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/define-file-groups-for-screening.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 2efcc902-6686-5d2f-c141-546d616dc13a
---

# Define File Groups for Screening | Microsoft Learn

A *file group* is used to define a namespace for a file screen, file screen exception, or **Files by File Group** storage report. It consists of a set of file name patterns, which are grouped by the following:

- **Files to include**: files that belong in the group
- **Files to exclude**: files that do not belong in the group

Note

For convenience, you can create and edit file groups while you edit the properties of file screens, file screen exceptions, file screen templates, and **Files by File Group** reports. Any file group changes that you make from these property sheets are not limited to the current item that you are working on.

## To create a File Group

1. In **File Screening Management**, click the **File Groups** node.
2. On the **Actions** pane, click **Create File Group**. This opens the **Create File Group Properties** dialog box.

    (Alternatively, while you edit the properties of a file screen, file screen exception, file screen template, or **Files by File Group** report, under **Maintain file groups**, click **Create**.)
3. In the **Create File Group Properties** dialog box, type a name for the file group.
4. Add files to include and files to exclude:

    - For each set of files that you want to include in the file group, in the **Files to include** box, enter a file name pattern, and then click **Add**.
    - For each set of files that you want to exclude from the file group, in the **Files to exclude** box, enter a file name pattern, and then click **Add**. Note that standard wildcard rules apply, for example, **\*.exe** selects all executable files.
5. Click **OK**.

## Additional References

- [File Screening Management](file-screening-management)
- [Create a File Screen](create-file-screen)
- [Create a File Screen Exception](create-file-screen-exception)
- [Create a File Screen Template](create-file-screen-template)
- [Storage Reports Management](storage-reports-management)