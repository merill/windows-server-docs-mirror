---
layout: Conceptual
title: Storage Reports Management | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/storage-reports-management
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to generate, schedule, and monitor storage reports
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 06153a04-3ad4-7706-4a79-c10d776811df
document_version_independent_id: e83b9421-f071-4523-e20e-099d9db1c13b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/storage-reports-management.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/storage-reports-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/storage-reports-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e834929-0ce1-4c1d-9c81-fcb14721edfb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/75670257-a3f0-4627-9981-8046f99219e6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 68dc912d-e7b1-094c-6928-82d817682a62
---

# Storage Reports Management | Microsoft Learn

On the **Storage Reports Management** node of the File Server Resource Manager Microsoft^®^ Management Console (MMC) snap-in, you can perform the following tasks:

- Schedule periodic storage reports that allow you to identify trends in disk usage.
- Monitor attempts to save unauthorized files for all users or a selected group of users.
- Generate storage reports instantly.

For example, you can:

- Schedule a report that will run every Sunday at midnight, generating a list that includes the most recently accessed files from the previous two days. With this information, you can monitor weekend storage activity and plan server down-time that will have less impact on users who are connecting from home over the weekend.
- Run a report at any time to identify all duplicate files in a volume on a server so that disk space can be quickly reclaimed without losing any data.
- Run a Files by File Group report to identify how storage resources are segmented across different file groups
- Run a Files by Owner report to analyze how individual users are using shared storage resources.

This section includes the following topics:

- [Schedule a Set of Reports](schedule-set-of-reports)
- [Generate Reports on Demand](generate-reports-on-demand)

Note

To set e-mail notifications and certain reporting capabilities, you must first configure the general File Server Resource Manager options.

## Additional References

- [Setting File Server Resource Manager Options](setting-file-server-resource-manager-options)