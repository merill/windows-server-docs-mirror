---
layout: Conceptual
title: add alias | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/add-alias
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the add alias command, which adds aliases to the alias environment.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: cd3465c4-5ab8-ce64-6450-59a75664b979
document_version_independent_id: 8438a7b9-0473-b97a-78d5-79238aef7f5a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/add-alias.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/add-alias
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/add-alias.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a72d331c-6378-8ca3-6b1c-bb7fb8d8c5a3
---

# add alias | Microsoft Learn

Adds aliases to the alias environment. If used without parameters, **add alias** displays help at the command prompt. Aliases are saved in the metadata file and will be loaded with the **load metadata** command.

## Syntax

```
add alias <aliasname> <aliasvalue>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<aliasname>` | Specifies the name of the alias. |
| `<aliasvalue>` | Specifies the value of the alias. |
| `? | Displays help at the command prompt. |

## Examples

To list all shadows, including their aliases, type:

```
list shadows all
```

The following excerpt shows a shadow copy to which the default alias, *VSS\_SHADOW\_x*, has been assigned:

```
* Shadow Copy ID = {ff47165a-1946-4a0c-b7f4-80f46a309278}
%VSS_SHADOW_1%
```

To assign a new alias with the name *System1* to this shadow copy, type:

```
add alias System1 %VSS_SHADOW_1%
```

Alternatively, you can assign the alias by using the shadow copy ID:

```
add alias System1 {ff47165a-1946-4a0c-b7f4-80f46a309278}
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [load metadata command](load-metadata)