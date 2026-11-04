---
layout: Conceptual
title: netsh dhcpclient | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-dhcpclient
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the netsh dhcpclient command, which configures and manages the DHCP client settings.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-28T00:00:00.0000000Z
locale: en-us
document_id: eeb40631-3e36-faa3-153c-bbac28d08385
document_version_independent_id: eeb40631-3e36-faa3-153c-bbac28d08385
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-dhcpclient.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-dhcpclient
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-dhcpclient.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7e617447-afec-b4db-84cf-bd5e5acc1b91
---

# netsh dhcpclient | Microsoft Learn

The `netsh dhcpclient` command is used to configure and manage settings for the DHCP client, including enabling tracing and exporting diagnostic logs.

## Syntax

```
netsh dhcpclient [list | help | ? | trace]
netsh dhcpclient list
netsh dhcpclient trace <enable> <disable>
netsh dhcpclient trace <dump>
```

## Parameters

| Command | Description |
| --- | --- |
| list | Lists the available commands in the `netsh dhcpclient` context. |
| trace `<enable>` | `<disable>``<dump>` | Controls tracing for the DHCP client, allowing you to enable or disable it. This feature is helpful for troubleshooting as it generates detailed logs of DHCP client activities. You can retrieve the last 100 traces to review recent DHCP interactions. `enable` - Enables tracing for the DHCP client. `disable` - Disables tracing for the DHCP client. `dump` - Exports the last 100 traces. |
| help or ? | Provides help for the list of commands available in the `netsh dhcpclient` context. |

## Example

To enable tracing for the DHCP client, run the following command:

```cmd
netsh dhcpclient trace enable
```

To dump the last 100 traces for review in a specified path, run the following command:

```cmd
netsh dhcpclient trace dump > C:\NetshTrace\dhcp_trace.txt
```