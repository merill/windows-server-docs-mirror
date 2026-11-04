---
layout: Conceptual
title: nslookup ls | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup-ls
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nslookup ls command, which lists DNS domain information.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 0599c368-a3f2-e61b-2e36-1b89a0fa1bf0
document_version_independent_id: fea52dee-0776-59a6-40a5-dd70e5806e01
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nslookup-ls.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nslookup-ls
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nslookup-ls.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: db40444b-5e72-f554-00c5-ea9a113f45ad
---

# nslookup ls | Microsoft Learn

Lists DNS domain information.

## Syntax

```
ls [<option>] <DNSdomain> [{[>] <filename>|[>>] <filename>}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<option>` | The valid options include:<br>- **-t:** Lists all records of the specified type. For more information, see [nslookup set querytype](nslookup-set-querytype).<br>- **-a:** Lists aliases of computers in the DNS domain. This parameter is the same as **-t CNAME**<br>- **-d:** Lists all records for the DNS domain. This parameter is the same as **-t ANY**<br>- **-h:** Lists CPU and operating system information for the DNS domain. This parameter is the same as **-t HINFO**<br>- **-s:** Lists well-known services of computers in the DNS domain. This parameter is the same as **-t WKS**. |
| `<DNSdomain>` | Specifies the DNS domain for which you want information. |
| `<filename>` | Specifies a file name to use for the saved output. You can use the greater than (`>`) and double greater than (`>>`) characters to redirect the output in the usual manner. |
| /? | Displays help at the command prompt. |
| /help | Displays help at the command prompt. |

#### Remarks

- The default output of this command includes computer names and their associated IP addresses.
- If your output is directed to a file, hash marks are added for every 50 records received from the server.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [nslookup set querytype](nslookup-set-querytype)