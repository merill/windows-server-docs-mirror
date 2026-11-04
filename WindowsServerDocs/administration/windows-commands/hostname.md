---
layout: Conceptual
title: hostname | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/hostname
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the hostname command, which displays the host name portion of the full computer name of the computer.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: c4e01700-60c9-ae17-6296-963cc80d5438
document_version_independent_id: 8dc84763-6f4b-558b-439b-b35e41ed663f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/hostname.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/hostname
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/hostname.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c7a34c5b-b8b8-6e7e-f7c6-ee231084ff13
---

# hostname | Microsoft Learn

Displays the host name portion of the full computer name of the computer.

Important

This command is available only if the Internet Protocol (TCP/IP) protocol is installed as a component in the properties of a network adapter in Network.

## Syntax

```
hostname
```

### Parameters

| Parameter | Description |
| --- | --- |
| /? | Displays help at the command prompt. |

Any parameter different than `/?` produces an error message and sets the errorlevel to 1.

### Notes

- Environment variable `%COMPUTERNAME%` usually will print the same string as `hostname`, but in uppercase.
- If environment variable `_CLUSTER_NETWORK_NAME_` is defined, `hostname` will print its value.

### Examples

- To display the name of the computer, type:

```shell
hostname
```

- To display the name of the computer in uppercase:

```shell
echo %COMPUTERNAME%
```

- To alter the hostname output:

```shell
set "_CLUSTER_NETWORK_NAME_=Altered Computer Name"
hostname
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)