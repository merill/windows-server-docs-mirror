---
layout: Conceptual
title: reg export | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/reg-export
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the reg export command, which copies the specified subkeys, entries, and values of the local computer into a file for transfer to other servers.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: eb71cbce-b632-bcb7-19dd-c24ba5e1aaf6
document_version_independent_id: dd89df96-9132-e610-65f0-573f4188b1ec
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/reg-export.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/reg-export
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/reg-export.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 60c3a46e-730f-8131-fd05-da3e404464db
---

# reg export | Microsoft Learn

Copies the specified subkeys, entries, and values of the local computer into a file for transfer to other servers.

## Syntax

```
reg export <keyname> <filename> [/y]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<keyname>` | Specifies the full path of the subkey. The export operation only works with the local computer. The *keyname* must include a valid root key. Valid root keys for the local computer are: **HKLM**, **HKCU**, **HKCR**, **HKU**, and **HKCC**. If the registry key name contains a space, enclose the key name in quotes. |
| `<filename>` | Specifies the name and path of the file to be created during the operation. The file must have a .reg extension. |
| /y | Overwrites any existing file with the name *filename* without prompting for confirmation. |
| /? | Displays help at the command prompt. |

#### Remarks

- The return values for the **reg export** operation are:

    | Value | Description |
    | --- | --- |
    | 0 | Success |
    | 1 | Failure |

### Examples

To export the contents of all subkeys and values of the key MyApp to the file AppBkUp.reg, type:

```
reg export HKLM\Software\MyCo\MyApp AppBkUp.reg
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)