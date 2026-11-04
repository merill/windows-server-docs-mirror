---
layout: Conceptual
title: manage-bde tpm | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/manage-bde-tpm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the manage-bde tpm command, which configures the computer's Trusted Platform Module (TPM).
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-08-29T00:00:00.0000000Z
locale: en-us
document_id: c00fc666-2988-82e3-9391-b39dfab356ff
document_version_independent_id: 6f6452e7-9bad-4c4b-3d43-f3964327e60f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/manage-bde-tpm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/manage-bde-tpm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/manage-bde-tpm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c084d292-538c-4615-5ff2-3f953947cf82
---

# manage-bde tpm | Microsoft Learn

Configures the computer's Trusted Platform Module (TPM).

## Syntax

```
manage-bde -tpm [-turnon] [-takeownership <ownerpassword>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -turnon | Enables and activates the TPM, allowing the TPM owner password to be set. You can also use **-t** as an abbreviated version of this command. |
| -takeownership | Takes ownership of the TPM by setting an owner password. You can also use **-o** as an abbreviated version of this command. |
| `<ownerpassword>` | Represents the owner password that you specify for the TPM. |
| -computername | Specifies that manage-bde.exe is used to modify BitLocker protection on a different computer. You can also use **-cn** as an abbreviated version of this command. |
| `<name>` | Represents the name of the computer on which to modify BitLocker protection. Accepted values include the computer's NetBIOS name and the computer's IP address. |
| -? or /? | Displays brief Help at the command prompt. |
| -help or -h | Displays complete Help at the command prompt. |

### Examples

To turn on the TPM, type:

```
manage-bde -tpm -turnon
```

To take ownership of the TPM and set the owner password to *0wnerP@ss*, type:

```
manage-bde -tpm -takeownership 0wnerP@ss
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [TPM Management cmdlets for Windows PowerShell](/en-us/powershell/module/trustedplatformmodule/)
- [manage-bde command](manage-bde)