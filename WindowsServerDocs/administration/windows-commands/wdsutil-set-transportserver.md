---
layout: Conceptual
title: wdsutil set-transportserver | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-set-transportserver
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for Subcommand set-TransportServer, which sets configuration settings for a Transport Server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 45b316c5-3568-8b6f-5a47-fa2167506d78
document_version_independent_id: c53e5573-e4cd-e4ee-8806-b6230883af2d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-set-transportserver.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-set-transportserver
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-set-transportserver.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1b8c4c94-83fb-6e4a-2962-b9a9e98837a6
---

# wdsutil set-transportserver | Microsoft Learn

Sets configuration settings for a Transport Server.

## Syntax

```
wdsutil [Options] /Set-TransportServer [/Server:<Server name>]
     [/ObtainIpv4From:{Dhcp | Range}]
        [/start:<starting IP address>]
        [/End:<Ending IP address>]
     [/ObtainIpv6From:Range]\n\
        [/start:<start IP address>]\n\
        [/End:<End IP address>]
     [/startPort:<starting port>
        [/EndPort:<starting port>
     [/Profile:{10Mbps | 100Mbps | 1Gbps | Custom}]
     [/MulticastSessionPolicy]
             [/Policy:{None | AutoDisconnect | Multistream}]
                 [/Threshold:<Speed in KBps>]
                 [/StreamCount:{2 | 3}]
                 [/Fallback:{Yes | No}]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the Transport Server. This can be the NetBIOS name or the fully qualified domain name (FQDN). If no Transport Server name is specified, the local server is used. |
| [/ObtainIpv4From:{Dhcp | Range}] | Sets the source of the IPv4 addresses as follows:<br>- [/start: &lt;IP address&gt;] Sets the start of the IP address range. This is required and valid only if this option is set to **Range**.- [/End: &lt;IP address&gt;] Sets the end of the IP address range. This is required and valid only if this option is set to **Range**.- [/startPort: &lt;port&gt;] Sets the start of the port range.- [/EndPort: &lt;port&gt;] Sets the end of the port range. |
| [/ObtainIpv6From:Range] | Specifies the source of IPv6 addresses. This option only applies to Windows Server 2008 R2 and the only supported value is **Range**.<br>- [/start: &lt;IP address&gt;] Sets the start of the IP address range. This is required and valid only if this option is set to **Range**.- [/End: &lt;IP address&gt;] Sets the end of the IP address range. This is required and valid only if this option is set to **Range**.- [/startPort: &lt;port&gt;] Sets the start of the port range.- [/EndPort: &lt;port&gt;] Sets the end of the port range. |
| [/Profile: {10Mbps | 100Mbps | 1Gbps | Custom}] | Specifies the network profile to be used. This option is only available for servers running Windows Server 2008 or Windows Server 2003. |
| [/MulticastSessionPolicy] | Configures the transfer settings for multicast transmissions. This command is only available for Windows Server 2008 R2.<br>- [/Policy:{None | AutoDisconnect | Multistream}] Determines how to handle slow clients. **None** means to keep all clients in one session at the same speed. **AutoDisconnect** means that any clients that drop below the specified **/Threshold** are disconnected. **Multistream** means clients will be separated into multiple sessions as specified by **/StreamCount**.- [/Threshold:&lt;Speed in KBps&gt;] Sets the minimum transfer rate in KBps for **/Policy:AutoDisconnect**. Clients that drop below this rate are disconnected from multicast transmissions.- [/StreamCount:{2 | 3}] [/Fallback:{Yes | No}] Determines the number of sessions for **/Policy:Multistream**. **2** means two sessions (fast and slow), and **3** means three sessions (slow, medium, fast).- [/Fallback:{Yes | No}] Determines whether clients tha are disconnected will continue the transfer by using another method (if supported by the client). If you are using the WDS client, the computer will fall back to unicasting. Wdsmcast.exe does not support a fallback mechanism. This option also applies to clients that do not support **Multistream**. In that case, the computer will fall back to another method instead of moving to a slower transfer session. |

## Examples

To set the IPv4 address range for the server, type:

```
wdsutil /Set-TransportServer /ObtainIpv4From:Range /start:239.0.0.1 /End:239.0.0.100
```

To set the IPv4 address range, port range, and profile for the server, type:

```
wdsutil /Set-TransportServer /Server:MyWDSServer /ObtainIpv4From:Range /start:239.0.0.1 /End:239.0.0.100 /startPort:12000 /EndPort:50000 /Profile:10mbps
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil disable-transportserver command](wdsutil-disable-transportserver)
- [wdsutil enable-transportserver command](wdsutil-enable-transportserver)
- [wdsutil get-transportserver command](wdsutil-get-transportserver)
- [wdsutil start-transportserver command](wdsutil-start-transportserver)
- [wdsutil stop-transportserver command](wdsutil-stop-transportserver)