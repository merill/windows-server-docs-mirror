---
layout: Conceptual
title: atmadm | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/atmadm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the atmadm command, which monitors connections and addresses that are registered by the atM call Manager on an asynchronous transfer mode (atM) network.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a79e5001-b50a-c310-d65b-8480330bd4c3
document_version_independent_id: 47d60da8-585c-273d-c332-d0b784258eda
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/atmadm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/atmadm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/atmadm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 3acd0c4c-170a-db82-a0cb-e9a549a11a34
---

# atmadm | Microsoft Learn

Monitors connections and addresses that are registered by the atM call Manager on an asynchronous transfer mode (atM) network. You can use **atmadm** to display statistics for incoming and outgoing calls on atM adapters. Used without parameters, **atmadm** displays statistics for monitoring the status of active atM connections.

## Syntax

```
atmadm [/c][/a][/s]
```

#### Parameters

| Parameter | Description |
| --- | --- |
| /c | Displays call information for all current connections to the atM network adapter installed on this computer. |
| /a | Displays the registered atM network service access point (NSAP) address for each adapter installed in this computer. |
| /s | Displays statistics for monitoring the status of active atM connections. |
| /? | Displays help at the command prompt. |

### Remarks

- The **atmadm /c** command produces output similar to the following:

    ```
    Windows atM call Manager Statistics
    atM Connections on Interface : [009] Olicom atM PCI 155 Adapter
       Connection   VPI/VCI   remote address/
                              Media Parameters (rates in bytes/sec)
       In  PMP SVC    0/193   47000580FFE1000000F21A2E180020481A2E180B
                              Tx:UBR,Peak 0,Avg 0,MaxSdu 1516
                              Rx:UBR,Peak 16953936,Avg 16953936,MaxSdu 1516
       Out P-P SVC    0/192   47000580FFE1000000F21A2E180020481A2E180B
                              Tx:UBR,Peak 16953936,Avg 16953936,MaxSdu 1516
                              Rx:UBR,Peak 16953936,Avg 16953936,MaxSdu 1516
       In  PMP SVC    0/191   47000580FFE1000000F21A2E180020481A2E180B
                              Tx:UBR,Peak 0,Avg 0,MaxSdu 1516
                              Rx:UBR,Peak 16953936,Avg 16953936,MaxSdu 1516
       Out P-P SVC    0/190   47000580FFE1000000F21A2E180020481A2E180B
                              Tx:UBR,Peak 16953936,Avg 16953936,MaxSdu 1516
                              Rx:UBR,Peak 16953936,Avg 16953936,MaxSdu 1516
       In  P-P SVC    0/475   47000580FFE1000000F21A2E180000C110081501
                              Tx:UBR,Peak 16953984,Avg 16953984,MaxSdu 9188
                              Rx:UBR,Peak 16953936,Avg 16953936,MaxSdu 9188
       Out PMP SVC    0/194   47000580FFE1000000F21A2E180000C110081501 (0)
                              Tx:UBR,Peak 16953984,Avg 16953984,MaxSdu 9180
                              Rx:UBR,Peak 0,Avg 0,MaxSdu 0
       Out P-P SVC    0/474   4700918100000000613E5BFE010000C110081500
                              Tx:UBR,Peak 16953984,Avg 16953984,MaxSdu 9188
                              Rx:UBR,Peak 16953984,Avg 16953984,MaxSdu 9188
       In  PMP SVC    0/195   47000580FFE1000000F21A2E180000C110081500
                              Tx:UBR,Peak 0,Avg 0,MaxSdu 0
                              Rx:UBR,Peak 16953936,Avg 16953936,MaxSdu 9180
    ```

    The following table contains descriptions of each element in the **atmadm /c** sample output.

    | Type of Data | Screen Display | Description |
    | --- | --- | --- |
    | Connection Information | In/Out | Direction of the call. **In** is to the atM network adapter from another device. **Out** is from the atM network adapter to another device. |
    | PMP | Point-to-multipoint call. |  |
    | P-P | Point-to-point call. |  |
    | SVC | Connection is on a switched virtual circuit. |  |
    | PVC | Connection is on a permanent virtual circuit. |  |
    | VPI/VCI Information | VPI/VCI | Virtual path and virtual channel of the incoming or outgoing call. |
    | Remote address/Media Parameters | 47000580FFE1000000F21A2E180000C110081500 | NSAP address of the calling **(In)** or called **(Out)** atM device. |
    | Tx | The **Tx**parameter includes the following three elements:<br>    - Default or specified bit-rate type (UBR, CBR, VBR, or ABR)<br>    - Default or specified line speed<br>    - Specified service data unit (SDU) size. |  |
    | Rx | The **Rx**parameter includes the following three elements:<br>    - Default or specified bit-rate type (UBR, CBR, VBR, or ABR)<br>    - Default or specified line speed<br>    - Specified SDU size. |  |
- The **atmadm /a** command produces output similar to the following:

    ```
    Windows atM call Manager Statistics
    atM addresses for Interface : [009] Olicom atM PCI 155 Adapter
    47000580FFE1000000F21A2E180000C110081500
    ```
- The **atmadm /s** command produces output similar to the following:

    ```
    Windows atM call Manager Statistics
    atM call Manager statistics for Interface : [009] Olicom atM PCI 155 Adapter
    Current active calls                        = 4
    Total successful Incoming calls             = 1332
    Total successful Outgoing calls             = 1297
    Unsuccessful Incoming calls                 = 1
    Unsuccessful Outgoing calls                 = 1
    calls Closed by remote                      = 1302
    calls Closed Locally                        = 1323
    Signaling and ILMI Packets Sent            = 33655
    Signaling and ILMI Packets Received        = 34989
    ```

    The following table contains descriptions of each element in the **atmadm /s** sample output.

    | Call Manager Statistic | Description |
    | --- | --- |
    | Current active calls | Calls currently active on the atM adapter installed on this computer. |
    | Total successful Incoming calls | Calls successfully received from other devices on this atM network. |
    | Total successful Outgoing calls | Calls successfully completed to other atM devices on this network from this computer. |
    | Unsuccessful Incoming calls | Incoming calls that failed to connect to this computer. |
    | Unsuccessful Outgoing calls | Outgoing calls that failed to connect to another device on the network. |
    | Calls Closed by remote | Calls closed by a remote device on the network. |
    | Calls Closed Locally | Calls closed by this computer. |
    | Signaling and ILMI Packets Sent | Number of integrated local management interface (ILMI) packets sent to the switch to which this computer is attempting to connect. |
    | Signaling and ILMI Packets Received | Number of ILMI packets received from the atM switch. |

## Examples

To display call information for all current connections to the atM network adapter installed on this computer, type:

```
atmadm /c
```

To display the registered atM network service access point (NSAP) address for each adapter installed in this computer, type:

```
atmadm /a
```

To display statistics for monitoring the status of active atM connections, type:

```
atmadm /s
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)