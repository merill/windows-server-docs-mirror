---
layout: Conceptual
title: reg restore | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/reg-restore
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the reg restore command, which writes saved subkeys and entries back to the registry.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c1a2332d-714b-9b8e-182b-9706035a62fe
document_version_independent_id: 6eb19511-356a-ab8b-e559-31964f2e4b0e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/reg-restore.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/reg-restore
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/reg-restore.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cca9486a-96fb-9366-f67f-d5b51a28f11e
---

# reg restore | Microsoft Learn

Writes saved subkeys and entries back to the registry.

## Syntax

```
reg restore <keyname> <filename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<keyname>` | Specifies the full path of the subkey to be restored. The restore operation only works with the local computer. The *keyname* must include a valid root key. Valid root keys for the local computer are: **HKLM**, **HKCU**, **HKCR**, **HKU**, and **HKCC**. If the registry key name contains a space, enclose the key name in quotes. |
| `<filename>` | Specifies the name and path of the file with content to be written into the registry. This file must be created in advance by using the **reg save** command, and must have a .hiv extension. |
| /? | Displays help at the command prompt. |

#### Remarks

- Before editing any registry entries, you must save the parent subkey using the **reg save** command. If the edit fails, you can then restore the original subkey using the **reg restore** operation.
- The return values for the **reg restore** operation are:

    | Value | Description |
    | --- | --- |
    | 0 | Success |
    | 1 | Failure |

### Examples

To restore the file named NTRKBkUp.hiv into the key HKLM\Software\Microsoft\ResKit, and overwrite the existing contents of the key, type:

```
reg restore HKLM\Software\Microsoft\ResKit NTRKBkUp.hiv
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [reg save command](reg-save)