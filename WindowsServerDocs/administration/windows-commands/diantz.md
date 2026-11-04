---
layout: Conceptual
title: diantz | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/diantz
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the diantz command, which packages existing files into a cabinet (.cab) file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 747bd1ab-4afe-9601-b80d-a094b0842474
document_version_independent_id: 8701d0ee-d173-296a-758a-8cbd0242eb54
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/diantz.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/diantz
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/diantz.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 732efd8a-5bba-d0b2-30eb-0d2bbfd2ad23
---

# diantz | Microsoft Learn

Package existing files into a cabinet (.cab) file. This command performs the same actions as the updated [makecab command](makecab).

## Syntax

```
diantz [/v[n]] [/d var=<value> ...] [/l <dir>] <source> [<destination>]
diantz [/v[<n>]] [/d var=<value> ...] /f <directives_file> [...]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<source>` | File to compress. |
| `<destination>` | File name to give compressed file. If omitted, the last character of the source file name is replaced with an underscore (\_) and used as the destination. |
| /f `<directives_file>` | A file with **diantz** directives (may be repeated). |
| /d var=`<value>` | Defines variable with specified value. |
| /l `<dir>` | Location to place destination (default is current directory). |
| /v[`<n>`] | Set debugging verbosity level (0=none,...,3=full). |
| /? | Displays help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Microsoft Cabinet format](/en-us/previous-versions/bb417343%28v=msdn.10%29)