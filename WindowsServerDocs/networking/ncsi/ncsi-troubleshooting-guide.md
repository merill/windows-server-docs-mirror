---
layout: Conceptual
title: Network Connectivity Status Indicator troubleshooting guide for Windows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/ncsi/ncsi-troubleshooting-guide
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This guide demonstrates how to perform diagnostics using the Network Connectivity Status Indicator (NCSI) to troubleshoot and determine Internet connectivity.
ms.topic: troubleshooting-general
ms.date: 2023-06-06T00:00:00.0000000Z
ms.author: roharwoo
author: robinharwood
ms.contributors: rnitsch
locale: en-us
document_id: 19e5ab49-e195-6be0-63ac-1ac8f68a6556
document_version_independent_id: 19e5ab49-e195-6be0-63ac-1ac8f68a6556
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/ncsi/ncsi-troubleshooting-guide.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/ncsi/ncsi-troubleshooting-guide
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/ncsi/ncsi-troubleshooting-guide.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 08fbe99b-7a6c-341f-15cb-3f18da5f8f6c
---

# Network Connectivity Status Indicator troubleshooting guide for Windows | Microsoft Learn

Troubleshooting NCSI (Network Connectivity Status Indicator) issues are generally performed with packet capture data but NCSI event logs can also be a useful tool when correlated with the packet traffic. This guide serves to assist users on how diagnosing NCSI issues from common scenarios.

## View NCSI data using Event Viewer

1. To open the **Event Viewer**, right-click on **Start** &gt; **Event Viewer**. *Alternatively*, open the Run prompt by pressing **Win+R** and typing eventviewer.exe. [![Screenshot of the Start button context menu with Event Viewer highlighted.](../media/ncsi/ncsi-troubleshooting-guide/ncsi-event-viewer-1.jpg)](../media/ncsi/ncsi-troubleshooting-guide/ncsi-event-viewer-1.jpg#lightbox)
2. Expand **Applications and Service Logs** &gt; **Microsoft** &gt; **Windows** &gt; **NCSI**. [![Screenshot of the Event Viewer with expanded Applications and Service Logs, Microsoft, Windows, and NCSI highlighted.](../media/ncsi/ncsi-troubleshooting-guide/ncsi-event-viewer-2.jpg)](../media/ncsi/ncsi-troubleshooting-guide/ncsi-event-viewer-2.jpg#lightbox)
3. Right-click **NCSI**, select **View** &gt; **Show Analytic and Debug Logs**. [![Screenshot of the Event Viewer with NCSI highlighted with Show Analytic and Debug Logs enabled.](../media/ncsi/ncsi-troubleshooting-guide/ncsi-event-viewer-3.jpg)](../media/ncsi/ncsi-troubleshooting-guide/ncsi-event-viewer-3.jpg#lightbox)
4. Right-click on **Analytic** under the **NCSI** folder, select **Enable Log**. *A dialog box may notify you that you may lose Analytic and Debug log events when logging is enabled. Select **Ok** to proceed.*[![Screenshot of the Event Viewer with the NCSI Analytic event logging enabled.](../media/ncsi/ncsi-troubleshooting-guide/ncsi-event-viewer-4.jpg)](../media/ncsi/ncsi-troubleshooting-guide/ncsi-event-viewer-4.jpg#lightbox)

## Retrieve NCSI data using Event Viewer

Performing the actions mentioned above will facilitate in data retrieval. For easier analysis, convert the generated logs to text format. While in the **Event Viewer**, follow these steps:

1. Expand **Applications and Service Logs** &gt; **Microsoft** &gt; **Windows** &gt; **NCSI**.
2. Right-click on **Analytic**, select **Save All Events As**. [![Screenshot of the Event Viewer with the NCSI Analytic event with save all events being enabled.](../media/ncsi/ncsi-troubleshooting-guide/ncsi-event-viewer-5.jpg)](../media/ncsi/ncsi-troubleshooting-guide/ncsi-event-viewer-5.jpg#lightbox)
3. The "Save As" dialog box opens. Set the "save as type" to text (\*.txt), name your file and select your location. Select **Save**. [![Screenshot of the save as dialog window with NCSI logs being saved to the documents folder.](../media/ncsi/ncsi-troubleshooting-guide/ncsi-event-viewer-6.jpg)](../media/ncsi/ncsi-troubleshooting-guide/ncsi-event-viewer-6.jpg#lightbox)

Here's an example of a successful connection output:

```output
Information    4/26/2023 12:17:46 PM    Microsoft-Windows-NCSI    4013    Internet Connectivity Detection    Active Internet Probe started on interface {611346db-8fbb-473d-808b-6c7573b3ef4d}
Information    4/26/2023 12:17:46 PM    Microsoft-Windows-NCSI    4017    Internet Connectivity Detection    Active Internet Probe (HTTP) started on interface {611346db-8fbb-473d-808b-6c7573b3ef4d}
Information    4/26/2023 12:17:48 PM    Microsoft-Windows-NCSI    4005    Wait for Internet Connectivity     Entered State: Internet Connectivity Interface Luid: 0x6008001000000
Information    4/26/2023 12:18:07 PM    Microsoft-Windows-NCSI    4018    Internet Connectivity Detection    Active Internet Probe (HTTP) finished on interface {611346db-8fbb-473d-808b-6c7573b3ef4d}
Information    4/26/2023 12:18:07 PM    Microsoft-Windows-NCSI    4014    Internet Connectivity Detection    Active Internet Probe finished on interface {611346db-8fbb-473d-808b-6c7573b3ef4d} (false)
```

Here's an example of a failed connection output:

```output
Information    4/26/2023 12:01:02 PM    Microsoft-Windows-NCSI    4013    Internet Connectivity Detection    Active Internet Probe started on interface {611346db-8fbb-473d-808b-6c7573b3ef4d}
Information    4/26/2023 12:01:02 PM    Microsoft-Windows-NCSI    4017    Internet Connectivity Detection    Active Internet Probe (HTTP) started on interface {611346db-8fbb-473d-808b-6c7573b3ef4d}
Information    4/26/2023 12:01:04 PM    Microsoft-Windows-NCSI    4005    Wait for Internet Connectivity     Entered State: Local Connectivity Interface Luid: 0x6008001000000
Information    4/26/2023 12:03:23 PM    Microsoft-Windows-NCSI    4018    Internet Connectivity Detection    Active Internet Probe (HTTP) finished on interface {611346db-8fbb-473d-808b-6c7573b3ef4d}
Warning        4/26/2023 12:03:23 PM    Microsoft-Windows-NCSI    4051    None                               Active probe result code on interface {611346db-8fbb-473d-808b-6c7573b3ef4d} (0x6008001000000 Family: V4) = 12007
```

Correlate both the **Analytic** and **Operational** NCSI events with the packet capture timestamps to determine whether the active probe was fired, if it completed, and why it failed. To learn more about Winhttp error codes, see [error messages (Winhttp.h)](/en-us/windows/win32/winhttp/error-messages).

## How to reproduce a problem scenario

You can troubleshoot an issue by forcing an active probe to see if it completes. The easiest way to do this is to cause a network change event. The following demonstrates this on both wired and wireless connections:

**Wired**

1. Disconnect the Ethernet cable. (Alternatively, you can disable the network adapter in Advanced network settings).
2. Use a packet capture software, such as wireshark, and wait 30 seconds to collect the data.
3. Reconnect the Ethernet cable. (Or enable the network adapter in Advanced network settings if it was previously disabled).
4. Wait 60 seconds before stopping the capture to ensure ample time for active probe to be attempted.

**Wireless**

1. Start the packet capture prior to the connection.
2. Connect to the wireless network.
3. Wait 60 seconds to ensure the active probe activity has fully transpired.
4. Stop the network capture.

## Additional references

- [NCSI Overview](ncsi-overview)
- [NCSI FAQ](ncsi-frequently-asked-questions)