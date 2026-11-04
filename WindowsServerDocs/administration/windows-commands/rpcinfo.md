---
layout: Conceptual
title: rpcinfo | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/rpcinfo
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the rpcinfo command, which lists the programs on a remote computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: 16aae30f-ea97-45bf-8e07-47390d480ac2
document_version_independent_id: 2d0a3062-6e72-444b-2769-fda9e5a44c11
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/rpcinfo.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/rpcinfo
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/rpcinfo.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2247586c-101b-b4e9-2e1d-f1c7ee14a882
---

# rpcinfo | Microsoft Learn

Lists programs on remote computers. The **rpcinfo** command-line utility makes a remote procedure call (RPC) to an RPC server and reports what it finds.

## Syntax

```
rpcinfo [/p [<node>]] [/b <program version>] [/t <node program> [<version>]] [/u <node program> [<version>]]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /p `[<node>]` | lists all programs registered with the port mapper on the specified host. If you do not specify a node (computer) name, the program queries the port mapper on the local host. |
| /b `<program version>` | Requests a response from all network nodes that have the specified program and version registered with the port mapper. You must specify both a program name or number and a version number. |
| /t `<node program> [\<version>]` | Uses the TCP transport protocol to call the specified program. You must specify both a node (computer) name and a program name. If you do not specify a version, the program calls all versions. |
| /u `<node program> [\<version>]` | Uses the UDP transport protocol to call the specified program. You must specify both a node (computer) name and a program name. If you do not specify a version, the program calls all versions. |
| /? | Displays help at the command prompt. |

## Examples

To list all programs registered with the port mapper, type:

```
rpcinfo /p [<node>]
```

To request a response from network nodes that have a specified program, type:

```
rpcinfo /b <program version>
```

To use Transmission Control Protocol (TCP) to call a program, type:

```
rpcinfo /t <node program> [<version>]
```

Use User Datagram Protocol (UDP) to call a program:

```
rpcinfo /u <node program> [<version>]
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)