---
layout: Conceptual
title: netsh wfp | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-wfp
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: The netsh wfp command manages the Windows Filtering Platform (WFP) to capture, display, and analyze network traffic in Windows.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-08-11T00:00:00.0000000Z
locale: en-us
document_id: a70e4eb8-547b-0bd3-3ceb-0186bb49aeb6
document_version_independent_id: a70e4eb8-547b-0bd3-3ceb-0186bb49aeb6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-wfp.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-wfp
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-wfp.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5ac1e7a0-48ea-1245-a2d6-89704bf27603
---

# netsh wfp | Microsoft Learn

The `netsh wfp` command is used to manage and troubleshoot the Windows Filtering Platform (WFP). It enables you to capture, display, and analyze filtering rules, network events, and diagnostics related to network traffic filtering. This tool is useful for administrators who need to investigate network policies, monitor traffic, and resolve issues with WFP configuration.

## Syntax

```
netsh wfp [capture | dump | help | set | show | ?]
```

```
netsh wfp capture start cab=<on|off> traceonly=<on|off> keywords=<none|bcast|mcast|bcast+mcast> file=<path>
netsh wfp capture status
netsh wfp capture stop
```

```
netsh wfp dump
```

```
netsh wfp set options netevents=<on|off> keywords=<none|bcast|mcast|bcast+mcast> txnwatchdog=<milliseconds>
```

```
netsh wfp show appid file=<path>
               boottimepolicy file=<path|->
               filters file=<path|-> protocol=<ipprotocol> localaddr=<ipaddress> remoteaddr=<ipaddress> localport=<port>
                       appid=<path> userid=<user> dir=<in|out> verbose=<on|off>
               ikeevents file=<path|-> remoteaddr=<ipaddress>
               netevents file=<path|-> protocol=<ipprotocol> localaddr=<ipaddress> remoteaddr=<ipaddress> localport=<port>
                         remoteport=<port> appid=<path> userid=<user> timewindow=<seconds>
               options optionsfor=<netevents|keywords|txnwatchdog>
               security type=<callout|engine|filter|ikesadb|ipsecsadb|layer|netevents|provider|providercontext|sublayer>
                        guid=<guid>
               state file=<path|->
               sysports file=<path|->
```

## Parameters

| Command | Description |
| --- | --- |
| netsh `wfp capture start` | Starts a capture session for network events processed by WFP. **cab** - Specifies whether to compress the output files into a single `.cab` archive. - `on` (default): Combines all files into one `.cab` file.<br>- `off`: Leaves files uncompressed, useful for manual troubleshooting.<br>**traceonly** - Determines if only event tracing data is collected. - `on`: Captures only event tracing, resulting in smaller output files.<br>- `off` (default): Captures all relevant data.<br>**keywords** - Sets the network event keywords for the capture session. Options include: - `NONE`: Excludes both to minimize file size for extended captures.<br>- `BCAST`: Includes broadcast events.<br>- `MCAST`: Includes multicast events.<br>- `BCAST+MCAST` Includes both broadcast & multicast events (default).<br>**file** - Specifies the output file name. The default is `wfpdiag.cab`. If the `cab` parameter is set to `on`, the file name shouldn't include the extension since the `.cab` is automatically added to the output file. |
| netsh `wfp capture status` | Displays the status of the current capture session, indicating whether a session is active and providing details about the ongoing capture process. |
| netsh `wfp capture stop` | Stops an active capture session that was started with the `capture start` command. Use this command to end data collection and finalize the output files for analysis. |
| netsh `wfp dump` | Generates a script reflecting the current WFP configuration. You can save this script to a file and later use it to restore any modified settings. |
| netsh `wfp set options` | Configures global options for the Windows Filtering Platform. Only one option parameter can be modified per command execution. **netevents** - Enables or disables the collection of network events. - `on`: Network events are captured.<br>- `off`: Network event collection is disabled.<br>**keywords** - Specifies which types of network events to capture. Options include: - `NONE`: No broadcast or multicast events are captured (default).<br>- `BCAST`: Captures broadcast events only.<br>- `MCAST`: Captures multicast events only.<br>- `BCAST+MCAST`: Captures both broadcast and multicast events.<br>**txnwatchdog** - Sets the timeout (in milliseconds) for transaction watchdog events. Provide an integer value to specify the timeout. If set to zero or not specified, an event is triggered for every transaction. |
| netsh `wfp show appid` | Displays the device path of the executable using `file=<path>` format. |
| netsh `wfp show boottimepolicy` | Displays the boot-time policy and filters using `file=<path>` as the output file name. By default, the output is saved as `btpol.xml`. If you set this parameter to a dash (`file=-`), the output is displayed directly in the console instead of being saved to a file. |
| netsh `wfp show filters` | Displays filters matching the specified traffic parameters. - **file** - Specifies the output file name in the `file=<path>` format. The default is `filters.xml`. If set to a dash (`file=-`), the output is displayed in the console instead of being saved to a file.<br>- **protocol** - The IP protocol number, for example, use `6` for TCP or `17` for UDP. To learn more, see [IANA Protocol Numbers](https://www.iana.org/assignments/protocol-numbers/protocol-numbers.xhtml).<br>- **localaddr** / **remoteaddr** - Specifies the local or remote IP addresses respectively. Both must be either IPv4 or IPv6, and if both are specified, they must belong to the same address family.<br>- **localport** / **remoteport** - Specifies the local or remote port numbers respectively.<br>- **appid** - The application path on the local host that is sending or receiving traffic. Accepts either an NT path (`\device\harddiskvolume1\windows\system32\ftp.exe`) or a DOS path (`C:\Windows\System32\ftp.exe`). The specified path must exist.<br>- **userid** - The user associated with the traffic on the local host. Can be a security identifier (SID) such as `S-1-5-18` or a user name such as `NT AUTHORITY\SYSTEM`.<br>- **dir** - The direction of the connection. By default, both inbound and outbound filters are shown. Use `IN` to display only inbound filters or `OUT` for outbound filters.<br>- **verbose** - Controls the level of detail in the output. Set to `ON` to display all matching filters, or `OFF` (default) to suppress filters unlikely to affect connectivity. |
| netsh `wfp show ikeevents` | Displays recent Internet Key Exchange (IKE) epoch events matching the specified parameters. - **file** - Specifies the output file name for the results in the format `file=<path>`. The default is `netevents.xml`. If you set this parameter to a dash (`file=-`), the output is displayed directly in the console instead of being saved to a file.<br>- **remoteaddr** - The remote IP address to filter events by. Accepts either an IPv4 or IPv6 address. |
| netsh `wfp show netevents` | Displays recent network events matching the specified traffic parameters. - **file** - Specifies the output file name in the `file=<path>` format. The default is `filters.xml`. If set to a dash (`file=-`), the output is displayed in the console instead of being saved to a file.<br>- **protocol** - The IP protocol number, for example, use `6` for TCP or `17` for UDP.<br>- **localaddr** / **remoteaddr** - Specifies the local or remote IP addresses respectively. Both must be either IPv4 or IPv6, and if both are specified, they must belong to the same address family.<br>- **localport** / **remoteport** - Specifies the local or remote port numbers respectively.<br>- **appid** - The application path on the local host that is sending or receiving traffic. Accepts either an NT path (`\device\harddiskvolume1\windows\system32\ftp.exe`) or a DOS path (`C:\Windows\System32\ftp.exe`). The specified path must exist.<br>- **userid** - The user associated with the traffic on the local host. Can be a security identifier (SID) such as `S-1-5-18` or a user name such as `NT AUTHORITY\SYSTEM`.<br>- **timewindow** - Limits the displayed network events to a specified time frame in seconds. |
| netsh `wfp show options` | Specifies which global WFP option to display in `optionsfor=` format. Options are: - `NETEVENTS`: Shows whether network event diagnostics are enabled or disabled.<br>- `KEYWORDS`: Displays the types of network events (such as broadcast or multicast) that are being captured for diagnostics.<br>- `TXNWATCHDOG`: Displays the current timeout value (in milliseconds) for the transaction watchdog event. |
| netsh `wfp show security` | Displays the specified security descriptor. **type** - Specifies the WFP object type whose security descriptor you want to display in `type=` format. Options include: - `CALLOUT`<br>- `ENGINE`<br>- `FILTER`<br>- `IKESADB`<br>- `IPSECSADB`<br>- `LAYER`<br>- `NETEVENTS`<br>- `PROVIDER`<br>- `PROVIDERCONTEXT`<br>- `SUBLAYER`**guid** - For object types that support individual security descriptors, this parameter specifies the object's GUID in `guid=<guid>` format. If omitted, the command uses `IID_NULL` to retrieve the security descriptor for the entire type container. The following object types support per-object security descriptors:<br>- `callout`<br>- `filter`<br>- `layer`<br>- `provider`<br>- `providercontext`<br>- `sublayer` |
| netsh `wfp show state` | Displays the current state of WFP and IPsec. **file** - Specifies the output file name in `file=` format. By default, the output is saved as `wfpstate.xml`. If you set this parameter to a dash (`file=-`), the output is displayed directly in the console instead of being saved to a file. |
| netsh `wfp show sysports` | Displays system ports used by the TCP/IP Stack and RPC subsystem. **file** - Specifies the output file name in `file=` format. By default, the output is saved as `sysports.xml`. If you set this parameter to a dash (`file=-`), the output is displayed directly in the console instead of being saved to a file. |
| `help`*or*`?` | Displays a list of commands and their descriptions in the current context. |

## Examples

To start a capture session for network events and compress the output files into a single `.cab` archive, run the following command:

```cmd
netsh wfp capture start cab=on
```

To start a capture session that collects only event tracing data and includes both broadcast and multicast events, run the following command:

```cmd
netsh wfp capture start traceonly=on keywords=BCAST+MCAST
```

To enable the collection of network events and capture broadcast events only, run the following command:

```cmd
netsh wfp set options netevents=on keywords=BCAST
```

To set the transaction watchdog timeout to 5,000 milliseconds, run the following command:

```cmd
netsh wfp set options txnwatchdog=5000
```

To display the application path for a specified file, run the following command:

```
netsh wfp show appid file="C:\folder\app.exe"
```

To display whether network event diagnostics are enabled or disabled, run the following command:

```cmd
netsh wfp show options optionsfor=NETEVENTS
```

To display the security descriptor for a specific WFP object type, for example, a filter with a known GUID, run the following command:

```cmd
netsh wfp show security type=FILTER guid=YourGUID
```