---
layout: Conceptual
title: nslookup set | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup-set
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nslookup set command, which changes configuration settings affecting how lookups behave.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a9d4af8b-35af-3393-a97d-7b9293d67d94
document_version_independent_id: bf0a5bc6-f575-e3c3-224d-cf70e6759e50
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nslookup-set.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nslookup-set
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nslookup-set.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 7c8149bc-f053-dbb9-8b41-20e54593727c
---

# nslookup set | Microsoft Learn

Changes configuration settings that affect how lookups function.

## Syntax

```
set all [class | d2 | debug | domain | port | querytype | recurse | retry | root | search | srchlist | timeout | type | vc] [options]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [nslookup set all](nslookup-set-all) | Lists all current settings. |
| [nslookup set class](nslookup-set-class) | Changes the query class, which specifies the protocol group of the information. |
| [nslookup set d2](nslookup-set-d2) | Turns the verbose debugging mode on or off. |
| [nslookup set debug](nslookup-set-debug) | Turns off debugging mode completely. |
| [nslookup set domain](nslookup-set-domain) | Changes the default Domain Name System (DNS) domain name to the specified name. |
| [nslookup set port](nslookup-set-port) | Changes the default TCP/UDP Domain Name System (DNS) name server port to the specified value. |
| [nslookup set querytype](nslookup-set-querytype) | Changes the resource record type for the query. |
| [nslookup set recurse](nslookup-set-recurse) | Tells the Domain Name System (DNS) name server to query other servers if it doesn't find any information. |
| [nslookup set retry](nslookup-set-retry) | Sets the number of retries. |
| [nslookup set root](nslookup-set-root) | Changes the name of the root server used for queries. |
| [nslookup set search](nslookup-set-search) | Appends the Domain Name System (DNS) domain names in the DNS domain search list to the request until an answer is received. |
| [nslookup set srchlist](nslookup-set-srchlist) | Changes the default Domain Name System (DNS) domain name and search list. |
| [nslookup set timeout](nslookup-set-timeout) | Changes the initial number of seconds to wait for a reply to a lookup request. |
| [nslookup set type](nslookup-set-type) | Changes the resource record type for the query. |
| [nslookup set vc](nslookup-set-vc) | Specifies whether to use a virtual circuit when sending requests to the server. |

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)