---
layout: Conceptual
title: bitsadmin setsecurityflags | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setsecurityflags
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setsecurityflags command, which sets security flags for HTTP to determine if BITS should check the certificate revocation list, ignore certain certificate errors, and define the policy to use when a server redirects the HTTP request.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 65df5111-254b-39c0-44d5-c48ca502c8ff
document_version_independent_id: ae067877-bb45-fd73-ff10-71d8d8f759ed
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setsecurityflags.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setsecurityflags
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setsecurityflags.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b02ccb0d-f7a7-7852-e8af-50aa914f3504
---

# bitsadmin setsecurityflags | Microsoft Learn

Sets security flags for HTTP to determine if BITS should check the certificate revocation list, ignore certain certificate errors, and define the policy to use when a server redirects the HTTP request. The value is an unsigned integer.

## Syntax

```
bitsadmin /setsecurityflags <job> <value>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| value | Can include one or more of the following notification flags, including:<br>- Set the least significant bit to enable CRL Check.<br>- Set the 2nd bit from the right to ignore incorrect common names in the server certificate.<br>- Set the 3rd bit from the right to ignore incorrect dates in the server certificate.<br>- Set the 4th bit from the right to ignore incorrect certification authorities in the server certificate.<br>- Set the 5th bit from the right to ignore incorrect usage of the server certificate.<br>- Set the 9th through the 11th bits from the right to implement your specified redirection policy, including:<br>    - **0,0,0.** Redirects are automatically allowed.<br>    - **0,0,1.** Remote name in the **IBackgroundCopyFile** interface is updated if a redirect occurs.<br>    - **0,1,0.** BITS fails the job if a redirect occurs.<br>- Set the 12th bit from the right to allow redirection from HTTPS to HTTP. |

## Examples

To set the security flags to enable a CRL check for the job named *myDownloadJob*:

```
bitsadmin /setsecurityflags myDownloadJob 0x0001
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)