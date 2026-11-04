---
layout: Conceptual
title: reg save | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/reg-save
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the reg save command, which saves a copy of specified subkeys, entries, and values of the registry in a specified file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f9f50d22-f53a-87da-b0a1-ad284404998e
document_version_independent_id: 961f31f2-4403-4ec3-6664-1aeb2ba6ab15
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/reg-save.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/reg-save
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/reg-save.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 82d551b4-85ea-e70a-8f1b-dbc60e18e3aa
---

# reg save | Microsoft Learn

Saves a copy of specified subkeys, entries, and values of the registry in a specified file.

## Syntax

```
reg save <keyname> <filename> [/y]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<keyname>` | Specifies the full path of the subkey. To specify a remote computer, include the computer name (in the format `\\<computername>\`) as part of the *keyname*. Omitting `\\<computername>\` causes the operation to default to the local computer. The *keyname* must include a valid root key. Valid root keys for the local computer are: **HKLM**, **HKCU**, **HKCR**, **HKU**, and **HKCC**. If a remote computer is specified, valid root keys are: **HKLM** and **HKU**. If the registry key name contains a space, enclose the key name in quotes. |
| `<filename>` | Specifies the name and path of the created file. If no path is specified, the current path is used. |
| /y | Overwrites an existing file with the name *filename* without prompting for confirmation. |
| /? | Displays help at the command prompt. |

#### Remarks

- Before editing any registry entries, you must save the parent subkey using the **reg save** command. If the edit fails, you can then restore the original subkey using the **reg restore** operation.
- The return values for the **reg save** operation are:

    | Value | Description |
    | --- | --- |
    | 0 | Success |
    | 1 | Failure |

### Examples

To save the hive MyApp into the current folder as a file named AppBkUp.hiv, type:

```
reg save HKLM\Software\MyCo\MyApp AppBkUp.hiv
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [reg restore command](reg-restore)