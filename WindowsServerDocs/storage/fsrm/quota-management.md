---
layout: Conceptual
title: Quota Management | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/quota-management
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to create and manage quotas
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: aa69e99d-d1cf-a8ae-a0e7-e211127e1f4b
document_version_independent_id: 70b526b3-4ffd-8fa6-3bab-f1f1e899ca68
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/quota-management.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/quota-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/quota-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e834929-0ce1-4c1d-9c81-fcb14721edfb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/75670257-a3f0-4627-9981-8046f99219e6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: a80c11fd-b33d-d8f0-482f-87d49adcc8a7
---

# Quota Management | Microsoft Learn

On the **Quota Management** node of the File Server Resource Manager Microsoft^®^ Management Console (MMC) snap-in, you can perform the following tasks:

- Create quotas to limit the space allowed for a volume or folder, and generate notifications when the quota limits are approached or exceeded.
- Generate auto apply quotas that apply to all existing subfolders in a volume or folder and to any subfolders that are created in the future.
- Define quota templates that can be easily applied to new volumes or folders and then used across an organization.

For example, you can:

- Place a 200 megabyte (MB) limit on users' personal server folders, with an email notification sent to you and the user when 180 MB of storage has been exceeded.
- Set a flexible 500 MB quota on a group's shared folder. When this storage limit is reached, all users in the group are notified by e-mail that the storage quota has been temporarily extended to 520 MB so that they can delete unnecessary files and comply with the preset 500 MB quota policy.
- Receive a notification when a temporary folder reaches 2 gigabytes (GB) of usage, yet not limit that folder's quota because it is necessary for a service running on your server.

This section includes the following topics:

- [Create a Quota](create-quota)
- [Create an Auto Apply Quota](create-auto-apply-quota)
- [Create a Quota Template](create-quota-template)
- [Edit Quota Template Properties](edit-quota-template-properties)
- [Edit Auto Apply Quota Properties](edit-auto-apply-quota-properties)

Note

To set e-mail notifications and reporting capabilities, you must first configure the general File Server Resource Manager options. If you're just looking to free up space on a volume, consider using Azure File Sync with cloud tiering enabled. This allows you to cache your most frequently accessed files locally and tier your least frequently accessed files to the cloud, saving local storage space while maintaining performance. For details, see [Planning for an Azure File Sync deployment](/en-us/azure/storage/files/storage-sync-files-planning).

## Additional References

- [Setting File Server Resource Manager Options](setting-file-server-resource-manager-options)