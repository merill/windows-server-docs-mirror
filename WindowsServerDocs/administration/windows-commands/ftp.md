---
layout: Conceptual
title: ftp | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ftp
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ftp command, which transfers files to and from a computer running a File Transfer Protocol (ftp) server service.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-10-17T00:00:00.0000000Z
locale: en-us
document_id: 2c843767-45f0-2950-7a75-2ad114ddccee
document_version_independent_id: 3c155efe-e587-7141-5fa5-30ab9fd90bbc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ftp.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ftp
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ftp.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: 5bac74ab-b75c-b50f-51dc-97f22736c59f
---

# ftp | Microsoft Learn

Transfers files to and from a computer running a File Transfer Protocol (ftp) server service. This command can be used interactively or in batch mode by processing ASCII text files.

## Syntax

```
ftp [-v] [-d] [-i] [-n] [-g] [-s:<filename>] [-a] [-A] [-x:<sendbuffer>] [-r:<recvbuffer>] [-b:<asyncbuffers>][-w:<windowssize>][<host>] [-?]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -v | Suppresses display of remote server responses. |
| -d | Enables debugging, displaying all commands passed between the FTP client and FTP server. |
| -i | Disables interactive prompting during multiple file transfers. |
| -n | Suppresses auto-login upon initial connection. |
| -g | Disables file name globbing. **Glob** permits the use of the asterisk (\*) and question mark (?) as wildcard characters in local file and path names. |
| -s:`<filename>` | Specifies a text file that contains **ftp** commands. These commands run automatically after **ftp** starts. This parameter allows no spaces. Use this parameter instead of redirection (`<`). **Note:** In Windows 8 and Windows Server 2012 or later operating systems, the text file must be written in UTF-8. |
| -a | Specifies that any local interface can be used when binding the ftp data connection. |
| -A | Logs onto the ftp server as anonymous. |
| -x:`<sendbuffer> ` | Overrides the default SO\_SNDBUF size of 8192. |
| -r:`<recvbuffer>` | Overrides the default SO\_RCVBUF size of 8192. |
| -b:`<asyncbuffers>` | Overrides the default async buffer count of 3. |
| -w:`<windowsize>` | Specifies the size of the transfer buffer. The default window size is 65535 bytes. |
| `<host>` | Specifies the computer name, IP address, or IPv6 address of the ftp server to which to connect. The host name or address, if specified, must be the last parameter on the line. |
| -? | Displays help at the command prompt. |

#### Remarks

- The **ftp** command-line parameters are case-sensitive.
- This command is available only if the **Internet Protocol (TCP/IP)** protocol is installed as a component in the properties of a network adapter in Network Connections.
- The **ftp** command can be used interactively. After it is started, **ftp** creates a sub-environment in which you can use **ftp** commands. You can return to the command prompt by typing the **quit** command. When the **ftp** sub-environment is running, it is indicated by the `ftp >` command prompt. For more information, see the **ftp** commands.
- The **ftp** command supports the use of IPv6 when the IPv6 protocol is installed.

### Examples

To log on to the ftp server named `ftp.example.microsoft.com`, type:

```
ftp ftp.example.microsoft.com
```

To log on to the ftp server named `ftp.example.microsoft.com` and run the **ftp** commands contained in a file named *resync.txt*, type:

```
ftp -s:resync.txt ftp.example.microsoft.com
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Additional FTP guidance](/en-us/previous-versions/orphan-topics/ws.10/cc756013%28v=ws.10%29)
- [IP version 6](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc738636%28v=ws.10%29)
- [IPv6 applications](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc782509%28v=ws.10%29)