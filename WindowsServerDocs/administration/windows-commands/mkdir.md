---
layout: Conceptual
title: mkdir | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/mkdir
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the mkdir command, which creates a directory or subdirectory.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b13bb018-dd2f-76cb-eb4c-27f75822a222
document_version_independent_id: 3eb99a88-6823-3271-cb5d-8c95da1d8de3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/mkdir.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/mkdir
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/mkdir.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 87d79750-9dee-1ebb-8faf-190ea7371e86
---

# mkdir | Microsoft Learn

Creates a directory or subdirectory. Command extensions, which are enabled by default, allow you to use a single **mkdir** command to create intermediate directories in a specified path.

Note

This command is the same as the [md command](md).

## Syntax

```
mkdir [<drive>:]<path>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<drive>`: | Specifies the drive on which you want to create the new directory. |
| `<path>` | Specifies the name and location of the new directory. The maximum length of any single path is determined by the file system. This is a required parameter. |
| /? | Displays help at the command prompt. |

### Examples

To create a directory named *Directory1* within the current directory, type:

```
mkdir Directory1
```

To create the directory tree *Taxes\Property\Current* within the root directory, with command extensions enabled, type:

```
mkdir \Taxes\Property\Current
```

To create the directory tree *Taxes\Property\Current* within the root directory as in the previous example, but with command extensions disabled, type the following sequence of commands:

```
mkdir \Taxes
mkdir \Taxes\Property
mkdir \Taxes\Property\Current
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [md command](md)