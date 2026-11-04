---
layout: Conceptual
title: Scenario Implement Retention of Information on File Servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/solution-guides/scenario--implement-retention-of-information-on-file-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Scenario: Implement Retention of Information on File Servers'
author: robinharwood
ms.author: roharwoo
ms.date: 2022-04-01T00:00:00.0000000Z
ms.topic: solution-overview
locale: en-us
document_id: b1fa042f-0954-baa9-7344-d6d53db5c035
document_version_independent_id: 2abf0802-16c8-a10a-dc01-3d3bf8086367
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/solution-guides/Scenario--Implement-Retention-of-Information-on-File-Servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/solution-guides/scenario--implement-retention-of-information-on-file-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/solution-guides/Scenario--Implement-Retention-of-Information-on-File-Servers.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e834929-0ce1-4c1d-9c81-fcb14721edfb
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/75670257-a3f0-4627-9981-8046f99219e6
platformId: f0f52766-5156-62e4-417c-c8a5e54abf28
---

# Scenario Implement Retention of Information on File Servers | Microsoft Learn

A retention period is the amount of time that a document should be kept before it's expired. Depending on the organization, the retention period can be different. You can classify files in a folder as having a short, medium, or long-term retention period, and then assign a time frame for each period. You may want to keep a file indefinitely by putting it on legal hold.

## Scenario description

File Classification Infrastructure and File Server Resource Manager uses file management tasks and file classification to apply retention periods for a set of files. You can assign a retention period on a folder and then use a file management task to configure how long an assigned retention period is to last. When the files in the folder are about to expire, the owner of the file receives a notification email. You can also classify a file as being on legal hold so that the file management task won't expire the file.

You can find planning information for configuring retention in [Plan for Retention of Information on File Servers](plan-retention-information-file-servers).

You can find steps for classifying files for legal hold and configuring a retention period in [Deploy Implementing Retention of Information on File Servers (Demonstration Steps)](deploy-implementing-retention-of-information-on-file-servers--demonstration-steps-).

Note

That scenario only discusses how to manually classify a document for legal hold. However, it is possible to automatically classify documents for legal hold. One way to do this is to create a Windows PowerShell classifier that compares the file owner to a list of user accounts that are under legal hold. If the file owner is a part of the user account list, the file is classified for legal hold.

## In this scenario

This scenario is part of the Dynamic Access Control scenario. For more information about Dynamic Access Control, see:

- [Dynamic Access Control: Scenario Overview](dynamic-access-control--scenario-overview)