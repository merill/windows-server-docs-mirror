---
layout: Conceptual
title: netsh winsock | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-winsock
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: The netsh winsock command manages the Windows Sockets (Winsock) API network communication in Windows.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-08-12T00:00:00.0000000Z
locale: en-us
document_id: 6801938e-8359-fc50-2503-17d769fafbdf
document_version_independent_id: 6801938e-8359-fc50-2503-17d769fafbdf
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-winsock.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-winsock
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-winsock.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 53949f5c-00a0-26e0-1da3-13eb4ca7b0a5
---

# netsh winsock | Microsoft Learn

The `netsh winsock` command manages the Windows Sockets (Winsock) API, which is responsible for network communication between applications and network services.

## Syntax

```
netsh winsock [audit | dump | help | remove | reset | set | show | ?]
```

```
netsh winsock audit trail
netsh winsock dump
netsh winsock remove provider <catalog id>
netsh winsock reset
netsh winsock set autotuning <on|off>
netsh winsock show <autotuning> <catalog>
```

## Parameters

| Command | Description |
| --- | --- |
| winsock `audit trail` | Displays the audit trail of Layered Service Providers (LSP) that are installed and uninstalled. |
| winsock `dump` | Creates a script containing the current Winsock configuration. The script can be saved to a file and used to restore settings if they're altered or need to be replicated on another system. |
| winsock `remove provider``<catalog id>` | Removes a specific Winsock LSP from the system using its catalog ID. This ID can be found when you run `winsock show catalog`. The Namespace Providers are presented as a GUID rather than a catalog ID. |
| winsock `reset` | Resets the Winsock catalog to a clean state, removing any custom LSPs to resolve network problems caused by corrupted Winsock settings. It doesn't affect Winsock Name Space Provider entries. |
| winsock `set autotuning` | This command toggles Winsock send autotuning, which enables dynamic send buffering to improve overall network throughput. Options are `on` or `off`. |
| winsock `show` | `autotuning` - Displays whether Winsock send autotuning is currently enabled or disabled. `catalog` - Displays the contents of the Winsock catalog, listing all registered Winsock LSPs and namespace providers. |
| `help`*or*`?` | Displays a list of commands and their descriptions in the current context. |

## Examples

To view the audit trail of LSPs, run the following command:

```cmd
netsh winsock audit trail
```

To remove a specific Winsock LSP using its catalog ID, run the following command:

```cmd
netsh winsock remove provider <catalog_id>
```

To enable Winsock send autotuning for better throughput, run the following command:

```cmd
netsh winsock set autotuning on
```

To display the contents of the Winsock catalog, run the following command:

```cmd
netsh winsock show catalog
```