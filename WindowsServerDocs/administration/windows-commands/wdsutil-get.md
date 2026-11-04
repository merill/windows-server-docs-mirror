---
layout: Conceptual
title: wdsutil get | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil get command, which retrieves properties or attributes about the specified object.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2024-08-19T00:00:00.0000000Z
locale: en-us
document_id: bf3f7417-5509-0035-7163-a43bfcb4d922
document_version_independent_id: 1ad940b6-5d82-aef2-99d6-84b861a7bab1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: d83fd67b-a1f7-32e0-7f5a-d0cb8fd13bbd
---

# wdsutil get | Microsoft Learn

Retrieves properties or attributes about the specified object.

## Subcommands

| Subcommand | Description |
| --- | --- |
| [wdsutil get-alldevices command](wdsutil-get-alldevices) | Displays information about all prestaged computers. |
| [wdsutil get-allImagegroups command](wdsutil-get-allimagegroups) | Displays information about all image groups. |
| [wdsutil get-allimages command](wdsutil-get-allimages) | Displays information about all images. |
| [wdsutil get-allmulticasttransmissions command](wdsutil-get-allmulticasttransmissions) | Displays the attributes of all multicast transmissions. |
| [wdsutil get-allnamespaces command](wdsutil-get-allnamespaces) | Displays the attributes of all namespaces. |
| [wdsutil get-allservers command](wdsutil-get-allservers) | Displays information about all Windows Deployment Services servers. |
| [wdsutil get-autoadddevices command](wdsutil-get-autoadddevices) | Displays computers that are pending administrative approval on a specified server. |
| [wdsutil get-device command](wdsutil-get-device) | Displays the attributes of a pending computer. |
| [wdsutil get-image command](wdsutil-get-image) | Displays the attributes of an existing image. |
| [wdsutil get-imagefile command](wdsutil-get-imagefile) | Displays information about images in a specified `.wim` file. |
| [wdsutil get-imagegroup command](wdsutil-get-imagegroup) | Displays information about a specified image group. |
| [wdsutil get-multicasttransmission command](wdsutil-get-multicasttransmission) | Displays the attributes of a specified multicast transmission. |
| [wdsutil get-namespace command](wdsutil-get-namespace) | Displays the attributes of a specified namespace. |
| [wdsutil get-server command](wdsutil-get-server) | Displays information about a specified Windows Deployment Services server. |
| [wdsutil get-transportserver command](wdsutil-get-transportserver) | Displays information about a specified Transport Server. |
| [wdsutil get-driverpackage command](wdsutil-get-driverpackage) | Displays information about driver packages on a server. |
| [wdsutil get-driverpackagefile command](wdsutil-get-driverpackagefile) | Displays information about driver package, including the drivers and files it contains. |
| [wdsutil get-alldrivergroups command](wdsutil-get-alldrivergroups) | Displays information about all the driver groups on server. |
| [wdsutil get-drivergroup command](wdsutil-get-drivergroup) | Displays information about driver groups on a server. |
| [wdsutil get-alldriverpackages command](wdsutil-get-alldriverpackages) | Displays information about all the driver packages on a server that match the specified search criteria. |
| [wdsutil get-driverpackagefile command](wdsutil-get-driverpackagefile) | Displays information about a driver package, including the drivers and files it contains. |