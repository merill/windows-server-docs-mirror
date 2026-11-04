---
layout: Conceptual
title: netsh wcn | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-wcn
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: The netsh wcn command configures, manages, and troubleshoots Wireless Configuration Network (WCN) settings on Windows devices.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-29T00:00:00.0000000Z
locale: en-us
document_id: e04a5c33-6952-ab52-be7f-e318fdccc266
document_version_independent_id: e04a5c33-6952-ab52-be7f-e318fdccc266
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-wcn.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-wcn
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-wcn.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 2a8a631e-0f3f-1400-5842-50e38b34ef24
---

# netsh wcn | Microsoft Learn

The `netsh wcn` command allows administrators to configure and manage Wireless Configuration Network (WCN) settings on local or remote Windows devices. It provides commands to query, enroll, and export wireless configuration details.

## Syntax

```
netsh wcn [dump] [enroll] [query] [help] [?]
netsh wcn enroll [enrolleeUUID=] <string> [password=] <string> [profile=] <string> [interface=] <string> [type=] (auto | ethernet | 802dot11)
netsh wcn query [SSID=] <string> [interface=] <string>
```

## Parameters

| Parameter | Description |
| --- | --- |
| `dump` | Exports the current WCN settings and configuration as a script for documentation or replication on another system. |
| `enroll` | Initiates the process to connect to a wireless network using WCN protocols. - `enrolleeUUID` - Specifies the Wi-Fi Protected Setup (WPS) Universally Unique Identifier (UUID) of the device you wish to enroll. This is a unique identifier provided by the device.<br>- `password` - The WPS password or PIN associated with the device. This is used during the enrollment process to authenticate the device to the network.<br>- `profile` - The name of the network profile to be used. This profile contains the configuration settings for the network connection.<br>- `interface` - Specifies the friendly name of the network interface on which the enrollment process is performed. If omitted, the default network interface is used. This parameter is optional.<br>- `type` - Determines the transport method to be used for the enrollment. This can specify different transport technologies, such as: **auto** (automatically selects the available network interfaces), **ethernet** (a wired Ethernet connection), **802dot11** (a wireless 802.11 connection).  This parameter is optional. |
| `query` | Retrieves and displays detailed information about a WCN device, including network settings, security details, and device-specific information. - `ssid` - Specifies the SSID (Service Set Identifier) of the 802.11 wireless network you wish to query.<br>- `interface` - Specifies the friendly name of the network interface you want to use for the query. This parameter is optional. |
| `help` or `?` | Provides a list of commands available in the `netsh wcn` context. |

## Examples

To initiate the enrollment process for a device with a specific UUID using a wireless 802.11 connection, run the following command:

```cmd
netsh wcn enroll enrolleeUUID=your-device-uuid password=your-password profile=your-ssid type=802dot11
```

To enroll a device using a wired Ethernet connection on a specified network interface, run the following command:

```cmd
netsh wcn enroll enrolleeUUID=your-device-uuid password=your-password profile=your-ssid interface=your-interface-name type=ethernet
```

To query a wireless network with a specific SSID using the default network interface, run the following command:

```cmd
netsh wcn query SSID=your-network-ssid
```

To query detailed information about a wireless network with a specific SSID using a specified network interface, run the following command:

```cmd
netsh wcn query SSID=your-network-ssid interface=your-interface-name
```

## Remarks

The `enroll` parameter starts WPS enrollment with the device identified by the enrollee UUID. The specified network profile is applied using the chosen interface, or the default if none is given.

The device password is usually a 4-digit or 8-digit PIN. Refer to your device's documentation for its UUID and PIN. If no transport type is set, or "auto" is used, the system selects the best available option.