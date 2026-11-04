---
layout: Conceptual
title: nslookup set srchlist | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup-set-srchlist
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nslookup set srchlist command, which changes the default Domain Name System (DNS) domain name and search list.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 1271ad1c-99da-d014-83f4-990ecea80db7
document_version_independent_id: 047b5878-431e-b19b-82d8-cdbcecc7982f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nslookup-set-srchlist.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nslookup-set-srchlist
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nslookup-set-srchlist.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: aea137f8-7a4f-7d65-4672-1dfe9e2b13c4
---

# nslookup set srchlist | Microsoft Learn

Changes the default Domain Name System (DNS) domain name and search list. This command overrides the default DNS domain name and search list of the [nslookup set domain](nslookup-set-domain) command.

## Syntax

```
set srchlist=<domainname>[/...]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<domainname>` | Specifies new names for the default DNS domain and search list. The default domain name value is based on the host name. You can specify a maximum of six names separated by slashes (/). |
| /? | Displays help at the command prompt. |
| /help | Displays help at the command prompt. |

#### Remarks

- Use the [nslookup set all](nslookup-set-all) command to display the list.

### Examples

To set the DNS domain to *mfg.widgets.com* and the search list to the three names:

```
set srchlist=mfg.widgets.com/mrp2.widgets.com/widgets.com
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [nslookup set domain](nslookup-set-domain)
- [nslookup set all](nslookup-set-all)