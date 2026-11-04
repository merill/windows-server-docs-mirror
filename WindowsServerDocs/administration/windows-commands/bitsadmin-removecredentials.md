---
layout: Conceptual
title: bitsadmin removecredentials | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-removecredentials
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin removecredentials command, which removes credentials from a job.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 0c0b0313-b5d4-beeb-8453-a7d46eb5cb38
document_version_independent_id: c03dbf3e-4bd4-6eb9-9b25-9e3b53d1c9d7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-removecredentials.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-removecredentials
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-removecredentials.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 2fa0b4a2-2e69-dfce-c5b9-d9b5b437f731
---

# bitsadmin removecredentials | Microsoft Learn

Removes credentials from a job.

Note

This command isn't supported by BITS 1.2 and earlier.

## Syntax

```
bitsadmin /removecredentials <job> <target> <scheme>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| target | Use either **SERVER** or **PROXY**. |
| scheme | Use one of the following:<br>- **BASIC.** Authentication scheme where the user name and password are sent in clear-text to the server or proxy.<br>- **DIGEST.** A challenge-response authentication scheme that uses a server-specified data string for the challenge.<br>- **NTLM.** A challenge-response authentication scheme that uses the credentials of the user for authentication in a Windows network environment.<br>- **NEGOTIATE (also known as the Simple and Protected Negotiation protocol).** A challenge-response authentication scheme that negotiates with the server or proxy to determine which scheme to use for authentication. Examples are the Kerberos protocol and NTLM.<br>- **PASSPORT.** A centralized authentication service provided by Microsoft that offers a single logon for member sites. |

## Examples

To remove credentials from the job named *myDownloadJob*:

```
bitsadmin /removecredentials myDownloadJob SERVER BASIC
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)