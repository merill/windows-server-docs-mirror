---
layout: Conceptual
title: ksetup setcomputerpassword | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-setcomputerpassword
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup setcomputerpassword command, which sets the password for the local computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 7d3c919f-16fd-b795-b6c6-0de417af301f
document_version_independent_id: 146838ad-a1a8-0d6b-765e-03caeff56ded
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-setcomputerpassword.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-setcomputerpassword
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-setcomputerpassword.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 12564289-9a9e-8ac8-ba8a-090a28ed07ab
---

# ksetup setcomputerpassword | Microsoft Learn

Sets the password for the local computer. This command affects the computer account only and requires a restart for the password change to take effect.

Important

The computer account password isn't displayed in the registry or as output from the **ksetup** command.

## Syntax

```
ksetup /setcomputerpassword <password>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<password>` | Specifies the supplied password to set the computer account on the local computer. The password can only be set by using an account with administrative privileges, and the password must be from 1 to 156 alphanumeric or special characters. |

### Examples

To change the computer account password on the local computer from *IPops897* to *IPop$897!*, type:

```
ksetup /setcomputerpassword IPop$897!
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)