---
layout: Conceptual
title: bootcfg | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bootcfg
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bootcfg command, which configures, queries, or changes Boot.ini file settings.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: df938686-02ee-ad5c-6ddd-59cdf57be947
document_version_independent_id: b6273508-8b73-08a9-b5a1-515e93733ce6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bootcfg.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bootcfg
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bootcfg.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 601c3726-e777-4b60-eb8d-f1f405c9f172
---

# bootcfg | Microsoft Learn

Configures, queries, or changes Boot.ini file settings.

## Syntax

```
bootcfg <parameter> [arguments...]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [bootcfg addsw](bootcfg-addsw) | Adds operating system load options for a specified operating system entry. |
| [bootcfg copy](bootcfg-copy) | Makes a copy of an existing boot entry, to which you can add command-line options. |
| [bootcfg dbg1394](bootcfg-dbg1394) | Configures 1394 port debugging for a specified operating system entry. |
| [bootcfg debug](bootcfg-debug) | Adds or changes the debug settings for a specified operating system entry. |
| [bootcfg default](bootcfg-default) | Specifies the operating system entry to designate as the default. |
| [bootcfg delete](bootcfg-delete) | Deletes an operating system entry in the [operating systems] section of the Boot.ini file. |
| [bootcfg ems](bootcfg-ems) | Enables the user to add or change the settings for redirection of the Emergency Management Services console to a remote computer. |
| [bootcfg query](bootcfg-query) | Queries and displays the [boot loader] and [operating systems] section entries from Boot.ini. |
| [bootcfg raw](bootcfg-raw) | Adds operating system load options specified as a string to an operating system entry in the [operating systems] section of the Boot.ini file. |
| [bootcfg rmsw](bootcfg-rmsw) | Removes operating system load options for a specified operating system entry. |
| [bootcfg timeout](bootcfg-timeout) | Changes the operating system time-out value. |