---
layout: Conceptual
title: Update-ServerFiles | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-update-serverfiles
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for Update-ServerFiles, which updates files in the REMINST shared folder by using the latest files that are stored in the server's %Windir%\System32\RemInst folder.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 155c7083-3a8f-8661-e67e-f8838383c82b
document_version_independent_id: e1c94a19-4e41-7bbc-9595-b97ef2bbfbce
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-update-serverfiles.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-update-serverfiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-update-serverfiles.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7508bf69-905f-5e73-9eef-89622a2cf8ab
---

# Update-ServerFiles | Microsoft Learn

Updates files in the REMINST shared folder by using the latest files that are stored in the server's %Windir%\System32\RemInst folder. To ensure the validity of your Windows Deployment Services installation, you should run this command once after each server upgrade, service pack installation, or update to Windows Deployment Services files.

## Syntax

```
wdsutil [Options] /Update-ServerFiles [/Server:<Server name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |

## Examples

To update the files, type one of the following:

```
wdsutil /Update-ServerFiles
wdsutil /Verbose /Progress /Update-ServerFiles /Server:MyWDSServer
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)