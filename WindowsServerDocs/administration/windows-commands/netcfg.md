---
layout: Conceptual
title: netcfg | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netcfg
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the netcfg command, which installs the Windows Preinstallation Environment (WinPE), a lightweight version of Windows used to deploy workstations.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: e1a5d57a-9b6d-97b5-68ef-596ea616ab3f
document_version_independent_id: 74c36f72-cfee-5fbb-e410-fb4cb7449cdc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netcfg.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netcfg
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netcfg.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e5975a37-dec8-e2d1-d64c-bc05bf7fe782
---

# netcfg | Microsoft Learn

Installs the Windows Preinstallation Environment (WinPE), a lightweight version of Windows used to deploy workstations.

## Syntax

```
netcfg [/v] [/e] [/winpe] [/l ] /c /i
```

### Parameters

| Parameter | Description |
| --- | --- |
| /v | Runs in verbose (detailed) mode. |
| /e | Uses servicing environment variables during install and uninstall. |
| /winpe | Installs TCP/IP, NetBIOS, and Microsoft Client for Windows preinstallation environment (WinPE). |
| /l | Provides the location of the INF file. |
| /c | Provides the class of the component to be installed; **protocol**, **service**, or **client**. |
| /i `<comp-ID>` | Provides the component ID. |
| /s | Provides the type of components to show, including **\ta** for adapters or **n** for net components. |
| /b | Displays the binding paths, when followed by a string containing the name of the path. |
| /q `<comp-ID>` | Queries whether component ID is installed |
| /u `<comp-ID>` | Uninstalls the component ID. |
| /m | Outputs the binding map to NetworkBindingMap.txt in the current directory. Using with /v will also display the binding map to the console. |
| /d | Performs a cleanup on all networking devices. This will require a reboot. |
| /x | Performs a cleanup on networking devices, skipping those without physical object names. This will require a reboot. |
| /? | Displays help at the command prompt. |

### Examples

To install the protocol *example* using c:\oemdir\example.inf, type:

```
netcfg /l c:\oemdir\example.inf /c p /i example
```

To install the *MS\_Server* service, type:

```
netcfg /c s /i MS_Server
```

To install TCP/IP, NetBIOS and Microsoft Client for Windows preinstallation environment, type:

```
netcfg /v /winpe
```

To display if component *MS\_IPX* is installed, type:

```
netcfg /q MS_IPX
```

To uninstall component *MS\_IPX*, type:

```
netcfg /u MS_IPX
```

To show all installed net components, type:

```
netcfg /s n
```

To display binding paths containing *MS\_TCPIP*, type:

```
netcfg /b ms_tcpip
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)