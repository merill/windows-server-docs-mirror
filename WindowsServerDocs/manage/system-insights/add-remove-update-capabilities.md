---
layout: Conceptual
title: Add, remove, and update capabilities in System Insights | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/system-insights/add-remove-update-capabilities
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: manage
ms.update-cycle: 1095-days
description: Learn how to add, remove, and update capabilities in System Insights to manage data collection and prediction features. Discover platform support and best practices.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2025-06-06T00:00:00.0000000Z
locale: en-us
document_id: 5f978424-bfd6-76a7-5ecb-d4e3e5931e1a
document_version_independent_id: 7bb192cf-9b80-af94-fb0c-185313bdfd5e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/system-insights/add-remove-update-capabilities.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../administration/toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/system-insights/add-remove-update-capabilities
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/system-insights/add-remove-update-capabilities.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: b66a7a19-35d7-434f-b76b-e3604c4441c3
---

# Add, remove, and update capabilities in System Insights | Microsoft Learn

System Insights enables you to create new capabilities that use the existing data collection and management functionality. Once these capabilities are created, however, it's equally important that you also have the platform support to manage the addition, removal, and updates of these capabilities.

This topic describes the high-level functionality to add, remove, and update capabilities in System Insights.

## Add a capability

System Insights allows you to add new capabilities anytime using the **Add-InsightsCapability** cmdlet. The **Add-InsightsCapability** requires you to specify a capability name and the capability library. The capability library contains the capability description, data sources, and prediction logic.

```PowerShell
Add-InsightsCapability -Name Sample capability -Library C:\SampleCapability.dll
```

After a capability is added to System Insights, you can immediately invoke and manage the capability using PowerShell or Windows Admin Center.

## Update a capability

System Insights enables you to update a capability using the **Update-InsightsCapability** cmdlet.

```PowerShell
Update-InsightsCapability -Name Sample capability -Library C:\SampleCapabilityv2.dll
```

Updating a capability allows you to specify a new capability library, which allows you to change the capability description, the data sources, and the prediction logic associated with that capability. Importantly, updating a capability preserves all configuration and historical information about that capability, including custom schedules, actions, and historical prediction results.

## Remove a capability

You can remove capabilities in System Insights using the **Remove-InsightsCapability** cmdlet.

```PowerShell
Remove-InsightsCapability -Name Sample capability
```

Note

The default forecasting capabilities can't be removed.

Removing a capability permanently deletes the capability and all associated information, including the schedule, any remediation actions, and past prediction results.

Consider disabling a capability rather than removing it if you're worried about permanently deleting all information associated with the capability.