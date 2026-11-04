---
layout: Conceptual
title: reg delete | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/reg-delete
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the reg delete command, which deletes a key, subkey, or entries from the registry.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2022-10-20T00:00:00.0000000Z
locale: en-us
document_id: c2a03b57-702b-7270-deac-e12d055bf1ad
document_version_independent_id: d76457f5-2bee-4600-8f2d-6c7166b9de1f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/reg-delete.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/reg-delete
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/reg-delete.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 91ff52cf-7c1b-a49d-e4cf-ecb6a6888117
---

# reg delete | Microsoft Learn

Deletes a subkey or entries from the registry.

## Syntax

```
reg delete <keyname> [{/v valuename | /ve | /va}] [/f]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<keyname1>` | Specifies the full path of the subkey or entry to be deleted. To specify a remote computer, include the computer name (in the format `\\<computername>\`) as part of the *keyname*. Omitting `\\<computername>\` causes the operation to default to the local computer. The *keyname* must include a valid root key. Valid root keys for the local computer are: **HKLM**, **HKCU**, **HKCR**, **HKU**, and **HKCC**. If a remote computer is specified, valid root keys are: **HKLM** and **HKU**. If the registry key name contains a space, enclose the key name in quotes. |
| /v `<valuename>` | Deletes a specific entry under the subkey. If no entry is specified, then all entries and subkeys under the subkey will be deleted. |
| /ve | Specifies that only entries that have no value will be deleted. |
| /va | Deletes all entries within the specified key. Subkey entries that reside within the specified key are not deleted. |
| /f | Deletes the existing registry subkey or entry without asking for confirmation. |
| /? | Displays help at the command prompt. |

#### Remarks

- The return values for the **reg delete** operation are:

    | Value | Description |
    | --- | --- |
    | 0 | Success |
    | 1 | Failure |

### Examples

To delete the registry key Timeout and its all subkeys and values, type:

```
reg delete HKLM\Software\MyCo\MyApp\Timeout
```

To delete the registry value MTU under HKLM\Software\MyCo on the computer named ZODIAC, type:

```
reg delete \\ZODIAC\HKLM\Software\MyCo /v MTU
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)