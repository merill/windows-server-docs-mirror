---
layout: Conceptual
title: nslookup set type | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup-set-type
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nslookup set type command, which changes the resource record type for the query.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c3a37213-4994-3137-aeff-67b92f05b321
document_version_independent_id: 59b93afc-5deb-23d6-48e2-ac82d7089b82
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nslookup-set-type.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nslookup-set-type
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nslookup-set-type.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5f11cc12-0e5a-977b-cea7-25c19dfa7d44
---

# nslookup set type | Microsoft Learn

Changes the resource record type for the query. For information about resource record types, see [Request for Comment (Rfc) 1035](https://tools.ietf.org/html/rfc1035).

Note

This command is the same as the [nslookup set querytype](nslookup-set-querytype) command.

## Syntax

```
set type=<resourcerecordtype>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<resourcerecordtype>` | Specifies a DNS resource record type. The default resource record type is **A**, but you can use any of the following values:<br>- **A:** Specifies a computer's IP address.<br>- **ANY:** Specifies a computer's IP address.<br>- **CNAME:** Specifies a canonical name for an alias.<br>- **GID** Specifies a group identifier of a group name.<br>- **HINFO:** Specifies a computer's CPU and type of operating system.<br>- **MB:** Specifies a mailbox domain name.<br>- **MG:** Specifies a mail group member.<br>- **MINFO:** Specifies mailbox or mail list information.<br>- **MR:** Specifies the mail rename domain name.<br>- **MX:** Specifies the mail exchanger.<br>- **NS:** Specifies a DNS name server for the named zone.<br>- **PTR:** Specifies a computer name if the query is an IP address; otherwise, specifies the pointer to other information.<br>- **SOA:** Specifies the start-of-authority for a DNS zone.<br>- **TXT:** Specifies the text information.<br>- **UID:** Specifies the user identifier.<br>- **UINFO:** Specifies the user information.<br>- **WKS:** Describes a well-known service. |
| /? | Displays help at the command prompt. |
| /help | Displays help at the command prompt. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [nslookup set type](nslookup-set-querytype)