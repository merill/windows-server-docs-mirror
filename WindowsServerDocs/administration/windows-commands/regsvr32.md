---
layout: Conceptual
title: regsvr32 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/regsvr32
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the regsvr32 command, which registers .dll files as command components in the registry.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 9ba03ce5-dfcb-8492-9938-3eef9a744c3a
document_version_independent_id: b3b1fe77-7cb2-cb83-c986-cbfb9a569d1a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/regsvr32.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/regsvr32
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/regsvr32.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 33f88f78-1632-b74f-1727-22694d4908e9
---

# regsvr32 | Microsoft Learn

Registers .dll files as command components in the registry.

## Syntax

```
regsvr32 [/u] [/s] [/n] [/i[:cmdline]] <Dllname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| /u | Unregisters server. |
| /s | Prevents displaying messages. |
| /n | Prevents calling **DllRegisterServer**. This parameter requires you to also use the **/i** parameter. |
| /i:`<cmdline>` | Passes an optional command-line string (*cmdline*) to **DllInstall**. If you use this parameter with the **/u** parameter, it calls **DllUninstall**. |
| `<Dllname>` | The name of the .dll file that will be registered. |
| /? | Displays help at the command prompt. |

### Examples

To register the .dll for the Active Directory Schema, type:

```
regsvr32 schmmgmt.dll
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)