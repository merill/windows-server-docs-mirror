---
layout: Conceptual
title: Server Core vs Server with Desktop Experience install options | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/install-options-server-core-desktop-experience
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: Learn the differences between the Server Core and Server with Desktop Experience install options.
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2025-04-15T00:00:00.0000000Z
locale: en-us
document_id: 9290b927-b79b-0d1f-7fab-e9a8e994b65c
document_version_independent_id: d1beb9ba-f8c3-1ed4-8248-589a5baf8892
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/install-options-server-core-desktop-experience.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/install-options-server-core-desktop-experience
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/install-options-server-core-desktop-experience.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ee9269e9-ac8a-0294-bc10-0a57cab2969e
---

# Server Core vs Server with Desktop Experience install options | Microsoft Learn

When you install Windows Server using the setup wizard, you can choose between Server Core or Server with Desktop Experience install options. With Server Core, the standard graphical user interface (the Desktop Experience) isn't installed; you manage the server from the command line using PowerShell, the [Server Configuration tool (SConfig)](../administration/server-core/server-core-sconfig), or by remote methods. Server with Desktop Experience installs the standard graphical user interface and all tools, including client experience features.

We recommend that you choose the Server Core install option unless you have a particular need for the extra user interface elements and graphical management tools that are included in the Server with Desktop Experience install option.

The setup wizard lists the install options. In this list, editions without **Desktop Experience** are the Server Core install options:

- Windows Server Standard
- Windows Server Standard with Desktop Experience
- Windows Server Datacenter
- Windows Server Datacenter with Desktop Experience

Note

Unlike some previous releases of Windows Server, you can't convert between Server Core and Server with Desktop Experience after installation. You'll need to do a [clean installation](install-upgrade-migrate) if you install later decide to use a different option.

## Differences

There are some key differences between Server Core and Server with Desktop Experience:

| Component | Server Core | Server with Desktop Experience |
| --- | --- | --- |
| User interface | Minimal, command line driven (PowerShell, [SConfig](../administration/server-core/server-core-sconfig), cmd) | Standard Windows graphical user interface |
| Disk space | Smaller requirement | Larger requirement |
| Install, configure, uninstall server roles locally | PowerShell | Server Manager or PowerShell |
| Roles and Features | Some roles and features aren't available. For more information, see [Roles, Role Services, and Features not in Windows Server - Server Core](../administration/server-core/server-core-removed-roles).Some of the features from Server with Desktop Experience for application compatibility can be installed with the [App Compatibility Feature on Demand (FOD)](server-core-app-compatibility-feature-on-demand). | All roles and features are available, including those for application compatibility. |
| Remote management | Yes, can be managed remotely using GUI tools, such as Windows Admin Center, Remote Server Administration Tools (RSAT), or Server Manager, or by PowerShell. | Yes, can be managed remotely using GUI tools, such as Windows Admin Center, Remote Server Administration Tools (RSAT), or Server Manager, or by PowerShell. |
| Potential attack surface | Greatly reduced attack surface | No reduction |
| Microsoft Management Console | Not installed - can be installed with the [App Compatibility Feature on Demand (FOD)](server-core-app-compatibility-feature-on-demand). | Installed |

Note

For RSAT, you must use the version included with Windows 10 or later.