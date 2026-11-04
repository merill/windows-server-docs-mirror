---
layout: Conceptual
title: ftp remotehelp | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp-remotehelp_1
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp remotehelp command, which displays help for remote commands.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: dc98c4a7-ef56-1b3a-70b2-f29403bab6a4
document_version_independent_id: e02c354d-0b4a-6a65-91bd-348507b5e6d3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp-remotehelp_1.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp-remotehelp_1
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp-remotehelp_1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ac9cd34a-219e-1690-6e73-3ba042d67523
---

# ftp remotehelp | Microsoft Learn

Displays help for remote commands.

## Syntax

```
remotehelp [<command>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[<command>]` | Specifies the name of the command about which you want help. If `<command>` isn't specified, this command displays a list of all remote commands. You can also run remote commands using [ftp quote](ftp-quote) or [ftp literal](ftp-literal_1). |

### Examples

To display a list of remote commands, type:

```
remotehelp
```

To display the syntax for the *feat* remote command, type:

```
remotehelp feat
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ftp quote](ftp-quote)
- [ftp literal](ftp-literal_1)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)