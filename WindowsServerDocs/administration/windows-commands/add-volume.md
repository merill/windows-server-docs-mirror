---
layout: Conceptual
title: add volume | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/add-volume
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the add volume command, which adds volumes to the shadow copy Set, which is the set of volumes to be shadow copied.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 7e37aa54-67f3-c4bd-5f2b-9d2073f512f2
document_version_independent_id: 6c3e8990-8562-af29-8f4f-4d020205f48c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/add-volume.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/add-volume
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/add-volume.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d47c7a1a-fd27-50c3-fc2b-2250e600a44f
---

# add volume | Microsoft Learn

Adds volumes to the Shadow Copy Set, which is the set of volumes to be shadow copied. When a shadow copy is created, an environment variable links the alias to the shadow ID, so the alias can then be used for scripting.

Volumes are added one at a time. Each time a volume is added, it's checked to make sure VSS supports shadow copy creation for that volume. This check can be invalidated by later use of the **set context** command.

This command is necessary to create shadow copies. If used without parameters, **add volume** displays help at the command prompt.

## Syntax

```
add volume <volume> [provider <providerid>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<volume>` | Specifies a volume to add to the Shadow Copy Set. At least one volume is required for shadow copy creation. |
| `[provider \<providerid>]` | Specifies the Provider ID for a registered provider to use to create the shadow copy. If **provider** is not specified, the default provider is used. |

## Examples

To view the current list of registered providers, at the `diskshadow>` prompt, type:

```
list providers
```

The following output displays a single provider, which will be used by default:

```
* ProviderID: {b5946137-7b9f-4925-af80-51abd60b20d5}
        Type: [1] VSS_PROV_SYSTEM
        Name: Microsoft Software Shadow Copy provider 1.0
        Version: 1.0.0.7
        CLSID: {65ee1dba-8ff4-4a58-ac1c-3470ee2f376a}
1 provider registered.
```

To add drive C: to the Shadow Copy Set and assign an alias named *System1*, type:

```
add volume c: alias System1
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [set context command](set-context)