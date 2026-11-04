---
layout: Conceptual
title: Pktmon support for Microsoft Network Monitor (Netmon) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/pktmon/pktmon-netmon-support
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Describes how to install and configure Microsoft Network Monitor (Netmon) to read Pktmon-generated ETL files.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2021-10-27T00:00:00.0000000Z
locale: en-us
document_id: e28e601d-3a48-36cc-c1f1-6638c9ca38d1
document_version_independent_id: b54244fc-4ff7-6ebf-bc51-b880a3ae8ade
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/pktmon/pktmon-netmon-support.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/pktmon/pktmon-netmon-support
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/pktmon/pktmon-netmon-support.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 35aadeef-b812-743f-786d-a064907b6341
---

# Pktmon support for Microsoft Network Monitor (Netmon) | Microsoft Learn

Packet Monitor (Pktmon) generates logs in ETL format. These logs can be analyzed using Microsoft Network Monitor (Netmon) by using special parsers. This topic explains how to analyze Packet Monitor-generated ETL files within Netmon.

## Network Monitor setup and configuration

Follow these steps to install and configure Netmon to parse Packet Monitor-generated ETL files:

1. [Install Network Monitor 3.4](https://www.microsoft.com/download/details.aspx?id=4865).
2. Start Network Monitor elevated and set Windows as Active parser profile at (Tools / Options / Parser Profiles).
3. Copy etl\_Microsoft-Windows-PktMon-Events.npl from [here](https://github.com/microsoft/NetMon_Parsers_for_PacketMon/blob/main/etl_Microsoft-Windows-PktMon-Events.npl) to "%PROGRAMDATA%\Microsoft\Network Monitor 3\NPL\NetworkMonitor Parsers\Windows"
4. Copy stub\_etl\_Microsoft-Windows-PktMon-Events.npl from [here](https://github.com/microsoft/NetMon_Parsers_for_PacketMon/blob/main/stub_etl_Microsoft-Windows-PktMon-Events.npl) to "%PROGRAMDATA%\Microsoft\Network Monitor 3\NPL\NetworkMonitor Parsers\Windows\Stubs"
5. Rename stub\_etl\_Microsoft-Windows-PktMon-Events.npl to etl\_Microsoft-Windows-PktMon-Events.npl
6. Include etl\_Microsoft-Windows-PktMon-Events.npl into NetworkMonitor\_Parsers\_sparser.npl at "%PROGRAMDATA%\Microsoft\Network Monitor 3\NPL\NetworkMonitor Parsers"
7. Restart Network Monitor elevated for rebuilding the parsers.