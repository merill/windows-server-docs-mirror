---
layout: Conceptual
title: nfsstat | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/nfsstat
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the nfsstat command, which displays statistical info about the Network File System (NFS) and Remote Procedure Call (RPC) calls.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 29cc6a44-9b86-016c-5481-9c64d1e951b7
document_version_independent_id: 5a888c83-5291-7e5d-3bc5-0e2bb6afdd56
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/nfsstat.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/nfsstat
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/nfsstat.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 136eeb93-a6a8-e4b9-0e89-91710cf1dfc5
---

# nfsstat | Microsoft Learn

A command-line utility that displays statistical info about the Network File System (NFS) and Remote Procedure Call (RPC) calls. Used without parameters, this command displays all of the statistical data without resetting anything.

## Syntax

```
nfsstat [-c][-s][-n][-r][-z][-m]
```

### Parameters

| Parameter | Description |
| --- | --- |
| -c | Displays only the client-side NFS and RPC and NFS calls sent and rejected by the client. To display NFS or RPC information only, combine this flag with the **-n** or **-r** parameter. |
| -s | Displays only the server-side NFS and RPC and NFS calls sent and rejected by the server. To display NFS or RPC information only, combine this flag with the **-n** or **-r** parameter. |
| -m | Displays information about mount flags set by mount options, mount flags internal to the system, and other mount information. |
| -n | Displays NFS information for both the client and server. To display only the NFS client or server information, combine this flag with the **-c** or **-s** parameter. |
| -r | Displays RPC information for both the client and server. To display only the RPC client or server information, combine this flag with the **-c** or **-s** parameter. |
| -z | Resets the call statistics. This flag is only available to the root user and can be combined with any of the other parameters to reset particular sets of statistics after displaying them. |

### Examples

To display information about the number of RPC and NFS calls sent and rejected by the client, type:

```
nfsstat -c
```

To display and print the client NFS call-related information, type:

```
nfsstat -cn
```

To display RPC call-related information for both the client and server, type:

```
nfsstat -r
```

To display information about the number of RPC and NFS calls received and rejected by the server, type:

```
nfsstat -s
```

To reset all call-related information to zero on the client and server, type:

```
nfsstat -z
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [Services for Network File System Command Reference](services-for-network-file-system-command-reference)
- [NFS cmdlets reference](/en-us/powershell/module/nfs)