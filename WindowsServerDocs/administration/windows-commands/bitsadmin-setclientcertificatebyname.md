---
layout: Conceptual
title: bitsadmin setclientcertificatebyname | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setclientcertificatebyname
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setclientcertificatebyname command, which specifies the subject name of the client certificate to use for client authentication in an HTTPS (SSL) request.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 116a558a-f4af-864c-9ca2-4174354cca4f
document_version_independent_id: a35b5b5a-5183-abcf-bc63-d7567f17cc76
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setclientcertificatebyname.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setclientcertificatebyname
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setclientcertificatebyname.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 10b36ecf-e87c-6dbf-f67b-8f3fda8eece6
---

# bitsadmin setclientcertificatebyname | Microsoft Learn

Specifies the subject name of the client certificate to use for client authentication in an HTTPS (SSL) request.

## Syntax

```
bitsadmin /setclientcertificatebyname <job> <store_location> <store_name> <subject_name>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| store\_location | Identifies the location of a system store to use for looking up the certificate. Possible values include:<br>- 1 (CURRENT\_USER)<br>- 2 (LOCAL\_MACHINE)<br>- 3 (CURRENT\_SERVICE)<br>- 4 (SERVICES)<br>- 5 (USERS)<br>- 6 (CURRENT\_USER\_GROUP\_POLICY)<br>- 7 (LOCAL\_MACHINE\_GROUP\_POLICY)<br>- 8 (LOCAL\_MACHINE\_ENTERPRISE) |
| store\_name | The name of the certificate store. Possible values include:<br>- CA (Certification Authority certificates)<br>- MY (Personal certificates)<br>- ROOT (Root certificates)<br>- SPC (Software Publisher Certificate) |
| subject\_name | Name of the certificate. |

## Examples

To specify the name of the client certificate *myCertificate* to use for client authentication in an HTTPS (SSL) request for the job named *myDownloadJob*:

```
bitsadmin /setclientcertificatebyname myDownloadJob 1 MY myCertificate
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)