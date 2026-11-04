---
layout: Conceptual
title: reg copy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/reg-copy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the reg copy command, which copies a registry entry to a specified location on the local or remote computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9eccebe1-2184-1c49-8319-c66dcf9baf74
document_version_independent_id: beaa1cda-d916-c52b-4f64-97a8d1c7d06e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/reg-copy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/reg-copy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/reg-copy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ab113d20-f6cc-39cb-64a9-a2236a7139a5
---

# reg copy | Microsoft Learn

Copies a registry entry to a specified location on the local or remote computer.

## Syntax

```
reg copy <keyname1> <keyname2> [/s] [/f]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<keyname1>` | Specifies the full path of the subkey or entry to be added. To specify a remote computer, include the computer name (in the format `\\<computername>\`) as part of the *keyname*. Omitting `\\<computername>\` causes the operation to default to the local computer. The *keyname* must include a valid root key. Valid root keys for the local computer are: **HKLM**, **HKCU**, **HKCR**, **HKU**, and **HKCC**. If a remote computer is specified, valid root keys are: **HKLM** and **HKU**. If the registry key name contains a space, enclose the key name in quotes. |
| `<keyname2>` | Specifies the full path of the second subkey to be compared. To specify a remote computer, include the computer name (in the format `\\<computername>\`) as part of the *keyname*. Omitting `\\<computername>\` causes the operation to default to the local computer. The *keyname* must include a valid root key. Valid root keys for the local computer are: **HKLM**, **HKCU**, **HKCR**, **HKU**, and **HKCC**. If a remote computer is specified, valid root keys are: **HKLM** and **HKU**. If the registry key name contains a space, enclose the key name in quotes. |
| /s | Copies all subkeys and entries under the specified subkey. |
| /f | Copies the subkey without prompting for confirmation. |
| /? | Displays help at the command prompt. |

#### Remarks

- This command doesn't ask for confirmation when copying a subkey.
- The return values for the **reg compare** operation are:

    | Value | Description |
    | --- | --- |
    | 0 | Success |
    | 1 | Failure |

### Examples

To copy all subkeys and values under the key MyApp to the key SaveMyApp, type:

```
reg copy HKLM\Software\MyCo\MyApp HKLM\Software\MyCo\SaveMyApp /s
```

To copy all values under the key MyCo on the computer named ZODIAC to the key MyCo1 on the current computer, type:

```
reg copy \\ZODIAC\HKLM\Software\MyCo HKLM\Software\MyCo1
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)