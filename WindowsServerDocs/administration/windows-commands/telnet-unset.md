---
layout: Conceptual
title: telnet unset | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/telnet-unset
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the telnet unset command, which turns off previously set options.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 7acc63e3-0859-99ad-e2f9-07ddd1d1d4ec
document_version_independent_id: 648da987-9412-bb8d-3395-cd2eca85c263
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/telnet-unset.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/telnet-unset
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/telnet-unset.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f88617e7-acc6-52be-f809-c3d9d29edbe3
---

# telnet unset | Microsoft Learn

Turns off previously set options.

## Syntax

```
u {bsasdel | crlf | delasbs | escape | localecho | logging | ntlm} [?]
```

### Parameters

| Parameter | Description |
| --- | --- |
| bsasdel | Sends **backspace** as a **backspace**. |
| crlf | Sends the **Enter** key as a CR. Also known as line feed mode. |
| delasbs | Sends **delete** as **delete**. |
| escape | Removes the escape character setting. |
| localecho | Turns off localecho. |
| logging | Turns off logging. |
| ntlm | Turns off NTLM authentication. |
| ? | Displays help for this command. |

## Example

Turn off logging.

```
u logging
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)