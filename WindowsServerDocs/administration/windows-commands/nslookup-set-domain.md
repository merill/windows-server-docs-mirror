---
layout: Conceptual
title: nslookup set domain | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup-set-domain
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nslookup set domain command, which changes the default Domain Name System (DNS) domain name to the specified name.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: df87ebc9-e238-8898-9b4f-2c3eab0cf71c
document_version_independent_id: 9f4f3dde-3d53-526a-3095-402601d1c4c5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nslookup-set-domain.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nslookup-set-domain
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nslookup-set-domain.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 8d1d7f22-b9bd-7a8f-3c39-f98b578f2b87
---

# nslookup set domain | Microsoft Learn

Changes the default Domain Name System (DNS) domain name to the specified name.

## Syntax

```
set domain=<domainname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<domainname>` | Specifies a new name for the default DNS domain name. The default value is the name of the host. |
| /? | Displays help at the command prompt. |
| /help | Displays help at the command prompt. |

#### Remarks

- The default DNS domain name is appended to a lookup request depending on the state of the **defname** and **search** options.
- The DNS domain search list contains the parents of the default DNS domain if it has at least two components in its name. For example, if the default DNS domain is mfg.widgets.com, the search list is named both mfg.widgets.com and widgets.com.
- Use the [nslookup set srchlist](nslookup-set-srchlist) command to specify a different list and the [nslookup set all](nslookup-set-all) command to display the list.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [nslookup set srchlist](nslookup-set-srchlist)
- [nslookup set all](nslookup-set-all)