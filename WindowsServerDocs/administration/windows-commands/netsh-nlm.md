---
layout: Conceptual
title: netsh nlm | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-nlm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: The netsh nlm command manages the Network Location Manager (NLM) settings to override network connection quality classification in Windows.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-10-09T00:00:00.0000000Z
locale: en-us
document_id: 8fe50b44-afd0-83c7-cc7b-ac30b1b59082
document_version_independent_id: 8fe50b44-afd0-83c7-cc7b-ac30b1b59082
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-nlm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-nlm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-nlm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cd561f1f-9883-a570-f387-d67001b3c2d2
---

# netsh nlm | Microsoft Learn

The `netsh nlm` command allows admins to manage the Network Location Manager (NLM) settings and behavior by manually overriding how Windows classifies the network connection quality.

## Syntax

```
netsh nlm [ dump | enum | help | query | set | show | ?]
```

```
netsh nlm enum <connection> <network>
```

```
netsh nlm query all
```

```
netsh nlm set connectionquality [<guid> [good|bad|ignore]]
```

```
netsh nlm show <connectivity> <cost>
```

## Parameters

| Command | Description |
| --- | --- |
| nlm `dump` | Creates a script containing the current context configuration. The script can be saved to a file and used to restore settings if they're altered or need to be replicated on another system. |
| nlm `enum` | `connection` - Enumerates the current INetworkConnection objects. `network` - Enumerates the current INetwork objects. |
| nlm `query all` | Queries all network states from all supported services and writes to a file. A file path and name must be specified to save results. |
| nlm `set connectionquality` | Manually sets the connection quality of a network interface, overriding the connection quality classification by the Network classifier. `guid` - Is the interface GUID. `good` - Forces Windows to consider the specified network interface’s connection quality as stable and reliable. `bad` - Forces Windows to consider the specified network interface’s connection quality as unreliable where certain features might disable themselves, or services might limit their operations. `ignore` - Forces Windows to not override its own assessment. Windows determines the connection quality by itself, based on its normal detection algorithms (reverting automatic classification). |
| nlm `show` | `connectivity` - Displays the current connectivity state from the INetworkListManager. `cost` - Displays the current cost from the INetworkCostManager. |
| `help`*or*`?` | Displays a list of commands and their descriptions in the current context. |

## Examples

To enumerate the current network connections, run the following command:

```cmd
netsh nlm enum connection
```

To query all network states and save the results to a file, run the following command:

```cmd
netsh nlm query all <Filepath\Filename>
```

To manually set the connection quality of a network interface to "good", run the following command:

```cmd
netsh nlm set connectionquality <My_GUID> good
```

To display the current connectivity state, run the following command:

```cmd
netsh nlm show connectivity
```