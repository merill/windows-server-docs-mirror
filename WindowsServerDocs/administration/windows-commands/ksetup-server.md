---
layout: Conceptual
title: ksetup server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup server command, which allows you to specify a name for a computer running the Windows operating system, so changes made by the ksetup command update the target computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b2b706ce-71a3-516b-f9fb-b4f4a19358be
document_version_independent_id: 6ccb7127-8e90-b3ae-5b6c-2a850677e7fd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c5fcee17-b9c5-8d12-f6cb-d5d26c782872
---

# ksetup server | Microsoft Learn

Allows you to specify a name for a computer running the Windows operating system, so changes made by the **ksetup** command update the target computer.

The target server name is stored in the registry under `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\LSA\Kerberos`. This entry isn't reported when you run the **ksetup** command.

Important

There's no way to remove the targeted server name. Instead, you can change it back to the local computer name, which is the default.

## Syntax

```
ksetup /server <servername>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<servername>` | Specifies the full computer name on which the configuration will be effective, such as *IPops897.corp.contoso.com*.<br>If an incomplete fully-qualified domain computer name is specified, the command will fail. |

### Examples

To make your **ksetup** configurations effective on the *IPops897* computer, which is connected on the Contoso domain, type:

```
ksetup /server IPops897.corp.contoso.com
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)