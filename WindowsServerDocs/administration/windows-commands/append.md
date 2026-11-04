---
layout: Conceptual
title: append | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/append
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the append command, which allows programs to open data files in specified directories, as if they were in the current directory.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d9416e79-eccf-b7bb-e88f-fd65c0541563
document_version_independent_id: 917bd1e8-4066-c054-835b-dbcbf58aaa86
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/append.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/append
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/append.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 31818b1d-41a2-a7a2-2d42-0453a9148e1f
---

# append | Microsoft Learn

Allows programs to open data files in specified directories as if they were in the current directory. If used without parameters, **append** displays the appended directory list.

Note

This command is not supported in Windows 10.

## Syntax

```
append [[<drive>:]<path>[;...]] [/x[:on|:off]] [/path:[:on|:off] [/e]
append ;
```

### Parameters

| Parameter | Description |
| --- | --- |
| `[\<drive>:]<path>` | Specifies a drive and directory to append. |
| /x:on | Applies appended directories to file searches and launching applications. |
| /x:off | Applies appended directories only to requests to open files. The **/x:off** option is the default setting. |
| /path:on | Applies appended directories to file requests that already specify a path. **/path:on** is the default setting. |
| /path:off | Turns off the effect of **/path:on**. |
| /e | Stores a copy of the appended directory list in an environment variable named APPEND. **/e** may be used only the first time you use **append** after starting your system. |
| ; | Clears the appended directory list. |
| /? | Displays help at the command prompt. |

## Examples

To clear the appended directory list, type:

```
append ;
```

To store a copy of the appended directory to an environment variable named *append*, type:

```
append /e
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)