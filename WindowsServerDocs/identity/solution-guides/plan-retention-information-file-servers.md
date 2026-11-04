---
layout: Conceptual
title: Plan for retention of information on file servers | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/solution-guides/plan-retention-information-file-servers
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Plan how you can retain information on file servers.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2022-04-01T00:00:00.0000000Z
locale: en-us
document_id: 32264732-660e-1779-9984-0fd38399fa7c
document_version_independent_id: 32264732-660e-1779-9984-0fd38399fa7c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/solution-guides/plan-retention-information-file-servers.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/solution-guides/plan-retention-information-file-servers
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/solution-guides/plan-retention-information-file-servers.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: b4cfd5b4-67ed-a692-665b-ca2c6f8d07b7
---

# Plan for retention of information on file servers | Microsoft Learn

A data retention policy is important for any organization. You can use the following information to plan how you retain information in your organization.

## Determine the retention schedule

Determining how long data is stored on file servers in your network and developing a data retention schedule offers the following advantages:

- Limits the amount of data to store which lowers the overall cost of storage in your organization
- Reduces liability
- Satisfies regulations

When you're determining your retention schedule, you should ensure that the retention schedule meets the regulatory compliance of the industry your organization is in. For example, if your company is a healthcare provider, you should understand the HIPAA regulations.

## Identify files to be retained

Before you can implement your data retention policy, you must first identify the data that is stored on each file server. Once the data has been identified, you should mark the folders with a retention period and retention start date. Also, you should remove the Delete Child permission from any folders that could contain files that are being retained. This will ensure that the files aren't accidentally deleted.

Important

Classification properties should not be specified as a date. You should use the retention period to classify the file. If the retention period should change, you can update the retention period interval without having to classify every file again.

## Considerations for multiple computers

There are several things to consider when you've more than one file server in your organization:

- Data retention policies are usually the same across the organization so you can reuse the same set of rules on multiple computers.
- The Data Classification Toolkit uses Windows PowerShell cmdlets to import and export classification rules. You should use this to export the configuration from a baseline computer and import to another computer to ensure that the configuration is the same.
- You should use dynamic name spaces when the source and destination servers use the same drive letters for the storage on the server. When you create a new file share by using Server Manager, you can specify the name space.