---
layout: Conceptual
title: pnpunattend | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/pnpunattend
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the pnpunattend command, which audits the device drivers on a computer, as well as performs silent driver installations.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: 949f84c0-2d39-9f0f-4876-e10f32a651df
document_version_independent_id: 389185eb-2855-4ada-5a2f-0e4ad72f4957
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/pnpunattend.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/pnpunattend
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/pnpunattend.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 12a7c896-14ab-68a4-4b3d-e20e2ec75c45
---

# pnpunattend | Microsoft Learn

Audits a computer for device drivers, and perform unattended driver installations, or search for drivers without installing and, optionally, report the results to the command line. Use this command to specify the installation of specific drivers for specific hardware devices.

## Prerequisites

Preliminary preparation is required for older versions of the Windows operating system. Prior to using this command, you must complete the following tasks:

1. Create a directory for the drivers you want to install. For example, create a folder at **C:\Drivers\Video** for video adapter drivers.
2. Download and extract the driver package for your device. Copy the contents of the subfolder that contains the INF file for your version of the operating system and any subfolders to the video folder that you created. For example, copy the video driver files to **C:\Drivers\Video**.
3. Add a system environment path variable to the folder you created in step 1.For example, **C:\Drivers\Video**.
4. Create the following registry key, and then for the **DriverPaths** key you create, set the **Value Data** to **1**.
5. For Windows® 7 navigate the registry path: **HKEY\_LOCAL\_Machine\Software\Microsoft\Windows NT\CurrentVersion\**, and then create the keys: **UnattendSettings\PnPUnattend\DriverPaths\**

## Syntax

```
PnPUnattend.exe auditsystem [/help] [/?] [/h] [/s] [/l]
```

### Parameters

| Parameter | Description |
| --- | --- |
| auditsystem | Specifies online driver install.<br>Required, except when this command is run with either the **/help** or **/?** parameters. |
| /s | Optional. Specifies to search for drivers without installing. |
| /l | Optional. Specifies to display the log information for this command in the command prompt. |
| `/? | /help` | Optional. Displays help for this command at the command prompt. |

### Examples

To command shows how to use the **PNPUnattend.exe** to audit a computer for possible driver updates, and then report the findings to the command prompt, type:

```
pnpunattend auditsystem /s /l
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)