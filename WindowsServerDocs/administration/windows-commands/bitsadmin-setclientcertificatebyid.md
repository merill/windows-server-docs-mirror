---
layout: Conceptual
title: bitsadmin setclientcertificatebyid | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setclientcertificatebyid
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setclientcertificatebyid command, which specifies the identifier of the client certificate to use for client authentication in an HTTPS (SSL) request
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 16159299-9b59-f594-7c65-ecc7ba0a8888
document_version_independent_id: b684e9eb-955f-5f7d-a911-68813a264e31
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setclientcertificatebyid.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setclientcertificatebyid
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setclientcertificatebyid.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b0745625-91df-08a8-ee54-e6351fd6597f
---

# bitsadmin setclientcertificatebyid | Microsoft Learn

Specifies the identifier of the client certificate to use for client authentication in an HTTPS (SSL) request.

## Syntax

```
bitsadmin /setclientcertificatebyid <job> <store_location> <store_name> <hexadecimal_cert_id>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| store\_location | Identifies the location of a system store to use for looking up the certificate, including:<br>- CURRENT\_USER<br>- LOCAL\_MACHINE<br>- CURRENT\_SERVICE<br>- SERVICES<br>- USERS<br>- CURRENT\_USER\_GROUP\_POLICY<br>- LOCAL\_MACHINE\_GROUP\_POLICY<br>- LOCAL\_MACHINE\_ENTERPRISE. |
| store\_name | The name of the certificate store, including:<br>- CA (Certification Authority certificates)<br>- MY (Personal certificates)<br>- ROOT (Root certificates)<br>- SPC (Software Publisher Certificate). |
| hexadecimal\_cert\_id | A hexadecimal number representing the hash of the certificate. |

## Examples

To specify the identifier of the client certificate to use for client authentication in an HTTPS (SSL) request for the job named *myDownloadJob*:

```
bitsadmin /setclientcertificatebyid myDownloadJob BG_CERT_STORE_LOCATION_CURRENT_USER MY A106B52356D3FBCD1853A41B619358BD
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)