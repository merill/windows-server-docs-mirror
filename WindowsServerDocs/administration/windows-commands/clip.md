---
layout: Conceptual
title: clip | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/clip
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the clip command, which redirects the command output from the command line to the Windows clipboard.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 2a20292e-07a7-9d9d-6155-be2e660dbf7f
document_version_independent_id: 2b073c8a-3363-0583-090f-670899996f24
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/clip.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/clip
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/clip.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6a9d8b73-6bd3-4503-9f52-5866e37bdff4
---

# clip | Microsoft Learn

Redirects the command output from the command line to the Windows clipboard. You can use this command to copy data directly into any application that can receive text from the Clipboard. You can also paste this text output into other programs.

## Syntax

```
<command> | clip
clip < <filename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<command>` | Specifies a command whose output you want to send to the Windows clipboard. |
| `<filename>` | Specifies a file whose contents you want to send to the Windows clipboard. |
| /? | Displays help at the command prompt. |

## Examples

To copy the current directory listing to the Windows clipboard, type:

```
dir | clip
```

To copy the output of a program called *generic.awk* to the Windows clipboard, type:

```
awk -f generic.awk input.txt | clip
```

To copy the contents of a file called *readme.txt* to the Windows clipboard, type:

```
clip < readme.txt
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)