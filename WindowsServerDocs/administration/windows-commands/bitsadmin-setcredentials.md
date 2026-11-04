---
layout: Conceptual
title: bitsadmin setcredentials | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-setcredentials
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin setcredentials command, which adds credentials to a job.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 1445e7d9-6cc4-ff29-8abd-1bb6f5747986
document_version_independent_id: 510b14d5-f1bb-ce84-e51f-0bfb322fc067
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-setcredentials.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-setcredentials
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-setcredentials.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 26c8a464-ac95-cf23-b27d-631e959573f0
---

# bitsadmin setcredentials | Microsoft Learn

Adds credentials to a job.

Note

This command isn't supported by BITS 1.2 and earlier.

## Syntax

```
bitsadmin /setcredentials <job> <target> <scheme> <username> <password>
```

### Parameters

| Parameter | Description |
| --- | --- |
| job | The job's display name or GUID. |
| target | Use either **SERVER** or **PROXY**. |
| scheme | Use one of the following:<br>- **BASIC.** Authentication scheme where the user name and password are sent in clear-text to the server or proxy.<br>- **DIGEST.** A challenge-response authentication scheme that uses a server-specified data string for the challenge.<br>- **NTLM.** A challenge-response authentication scheme that uses the credentials of the user for authentication in a Windows network environment.<br>- **NEGOTIATE (also known as the Simple and Protected Negotiation protocol).** A challenge-response authentication scheme that negotiates with the server or proxy to determine which scheme to use for authentication. Examples are the Kerberos protocol and NTLM.<br>- **PASSPORT.** A centralized authentication service provided by Microsoft that offers a single logon for member sites. |
| user\_name | The name of the user. |
| password | The password associated with the provided *Username*. |

## Examples

To add credentials to the job named *myDownloadJob*:

```
bitsadmin /setcredentials myDownloadJob SERVER BASIC Edward password20
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)