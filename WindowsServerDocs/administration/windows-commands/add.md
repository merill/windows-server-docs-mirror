---
layout: Conceptual
title: add (diskshadow) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/add
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the add command, which adds volumes to the set of volumes that are to be shadow copied, or adds aliases to the alias environment.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-10-13T00:00:00.0000000Z
locale: en-us
document_id: d14b1b21-e221-8213-b132-904e60ab22e1
document_version_independent_id: a6007a06-c46b-270f-b7c6-3a45c4ce9288
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/add.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/add
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/add.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 35a39adf-3431-e8f1-84ea-605c2ffa7adb
---

# add (diskshadow) | Microsoft Learn

Adds volumes to the set of volumes that are to be shadow copied, or adds aliases to the alias environment. If used without subcommands, **add** lists the current volumes and aliases.

Note

Aliases are not added to the alias environment until the shadow copy is created. Aliases that you need immediately should be added by using **add alias**.

## Syntax

```
add
add volume <volume> [provider <providerid>]
add alias <aliasname> <aliasvalue>
```

### Parameters

| Parameter | Description |
| --- | --- |
| volume | Adds a volume to the Shadow Copy Set, which is the set of volumes to be shadow copied. See [add volume](add-volume) for syntax and parameters. |
| alias | Adds the given name and value to the alias environment. See [add alias](add-alias) for syntax and parameters. |
| /? | Displays help at the command line. |

## Examples

To display the volumes added and the aliases that are currently in the environment, type:

```
add
```

The following output shows that drive C has been added to the Shadow Copy Set:

```
Volume c: alias System1    GUID \\?\Volume{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}\
1 volume in Shadow Copy Set.
No Diskshadow aliases in the environment.
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)