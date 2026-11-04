---
layout: Conceptual
title: Customize the RDS title “Work Resources” using PowerShell on Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-work-resources
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Provides description of how to change workspace name from default in Windows Server.
author: robinharwood
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: how-to
ms.author: roharwoo
locale: en-us
document_id: 7bd85ef0-08b1-e2df-6b80-5863127aeea4
document_version_independent_id: 14b3f8e8-c5e9-57fc-d2c8-30cb3bd21b8d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-work-resources.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-work-resources
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-work-resources.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: 784d0ba4-d773-63c3-3b43-4fcdf73c9296
---

# Customize the RDS title “Work Resources” using PowerShell on Windows Server | Microsoft Learn

When using Windows Server to access RemoteApps or desktops through RD WebAccess or the new Remote Desktop app, you may have noticed that the workspace is titled “Work Resources" by default. You can easily change the title by using PowerShell cmdlets.

To change the title, open up a new PowerShell window on the connection broker server and import the RemoteDesktop module with the following command.

```powershell
    Import-Module RemoteDesktop
```

Next, use the Set-RDWorkspace command to change the workspace name.

```powershell
    Set-RDWorkspace [-Name] <string> [-ConnectionBroker <string>]  [<CommonParameters>]
```

For example, you can use the following command to change the workpsace name to "Contoso RemoteApps":

```powershell
    Set-RDWorkspace -Name "Contoso RemoteApps" -ConnectionBroker broker01.contoso.com
```

If you are running multiple Connection Brokers in High Availability mode, you must run this against the active broker. You can use this command:

```powershell
    Set-RDWorkspace -Name "Contoso RemoteApps" -ConnectionBroker (Get-RDConnectionBrokerHighAvailability).ActiveManagementServer
```

For more information about the Set-RDWorkspace cmdlet, see the [Set-RDSWorkspace](/en-us/powershell/module/remotedesktop/set-rdworkspace) reference.