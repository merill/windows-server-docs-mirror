---
layout: Conceptual
title: telnet | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/telnet
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the telnet command, which communicates with a computer running the telnet server service.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2022-06-21T00:00:00.0000000Z
locale: en-us
document_id: f3233a31-8788-33ca-a734-c486dafb544d
document_version_independent_id: b0e761ac-472c-73b9-a656-dced985750ff
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/telnet.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/telnet
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/telnet.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bbc4c76c-8520-2eaf-c0f2-e11d1880b072
---

# telnet | Microsoft Learn

Communicates with a computer running the telnet server service. Running this command without any parameters, lets you enter the telnet context, as indicated by the telnet prompt (**Microsoft telnet&gt;**). From the telnet prompt, you can use telnet commands to manage the computer running the telnet client.

Important

You must install the telnet client software before you can run this command. For more information, see [Installing telnet](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754293%28v=ws.10%29).

## Syntax

```
telnet [/a] [/e <escapechar>] [/f <filename>] [/l <username>] [/t {vt100 | vt52 | ansi | vtnt}] [<host> [<port>]] [/?]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /a | Attempts automatic logon. Same as **/l** option, except that it uses the currently logged on user's name. |
| /e `<escapechar>` | Specifies the escape character used to enter the telnet client prompt. |
| /f `<filename>` | Specifies the file name used for client side logging. |
| /l `<username>` | Specifies the user name to log on with on the remote computer. |
| /t `{vt100 | vt52 | ansi | vtnt}` | Specifies the terminal type. Supported terminal types are **vt100**, **vt52**, **ansi**, and **vtnt**. |
| `<host> [<port>]` | Specifies the hostname or IP address of the remote computer to connect to, and optionally the TCP port to use (default is TCP port 23). |
| /? | Displays help at the command prompt. |

## Examples

To use telnet to connect to the computer running the telnet Server Service at *telnet.microsoft.com*, type:

```
telnet telnet.microsoft.com
```

To use telnet to connect to the computer running the telnet Server Service at *telnet.microsoft.com* on TCP port 44 and to log the session activity in a local file called *telnetlog.txt*, type:

```
telnet /f telnetlog.txt telnet.microsoft.com 44
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Installing telnet](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754293%28v=ws.10%29)
- [telnet Technical Reference](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754987%28v=ws.10%29)