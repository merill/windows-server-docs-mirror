---
layout: Conceptual
title: tftp | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tftp
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the tftp command, which transfers files to and from a remote computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 09365b16-ea23-1c6b-ef22-0b359b8b4ce5
document_version_independent_id: 28509cbe-e899-2d7c-1de8-b601c20b70f7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tftp.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tftp
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tftp.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d25d8adc-4533-c75b-af5d-36d1be8c949c
---

# tftp | Microsoft Learn

Transfers files to and from a remote computer, typically a computer running UNIX, that is running the Trivial File Transfer Protocol (tftp) service or daemon. tftp is typically used by embedded devices or systems that retrieve firmware, configuration information, or a system image during the boot process from a tftp server.

> 
> [IMPORTANT] The tftp protocol doesn't support any authentication or encryption mechanism, and as such can introduce a security risk when present. Installing the tftp client is not recommended for systems connected to the Internet. A tftp server service is no longer provided by Microsoft for security reasons.

## Syntax

```
tftp [-i] [<host>] [{get | put}] <source> [<destination>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -i | Specifies binary image transfer mode (also called octet mode). In binary image mode, the file is transferred in one-byte units. Use this mode when transferring binary files. If you don't use the **-i** option, the file is transferred in ASCII mode. This is the default transfer mode. This mode converts the end-of-line (EOL) characters to an appropriate format for the specified computer. Use this mode when transferring text files. If a file transfer is successful, the data transfer rate is displayed. |
| `<host>` | Specifies the local or remote computer. |
| get | Transfers the file *destination* on the remote computer to the file *source* on the local computer. |
| put | Transfers the file *source* on the local computer to the file *destination* on the remote computer. Because the tftp protocol doesn't support user authentication, the user must be logged onto the remote computer, and the files must be writable on the remote computer. |
| `<source>` | Specifies the file to transfer. |
| `<destination>` | Specifies where to transfer the file. |

## Examples

To copy the file *boot.img* from the remote computer *Host1*, type:

```
tftp  -i Host1 get boot.img
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)