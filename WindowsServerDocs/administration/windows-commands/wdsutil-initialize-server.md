---
layout: Conceptual
title: wdsutil initialize-server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-initialize-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil initialize-server, which configures a Windows Deployment Services server for initial use after the server role has been installed.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 31ef4ac5-5260-90f0-9c5f-70db00e5e288
document_version_independent_id: 233d8867-cfa0-3c32-57fd-f87dee4aeb26
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-initialize-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-initialize-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-initialize-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: da8ff356-2c91-0c30-8331-18541dbbc729
---

# wdsutil initialize-server | Microsoft Learn

Configures a Windows Deployment Services server for initial use after the server role has been installed. After you run this command, you should use the [wdsutil add-Image command](wdsutil-add-image) command to add images to the server.

## Syntax

```
wdsutil /Initialize-Server [/Server:<Server name>] /remInst:<Full path> [/Authorize]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |
| /remInst:&lt;Full path&gt; | Specifies the full path and name of the remoteInstall folder. If the specified folder does not already exist, this option will create it when the command is run. You should always enter a local path, even in the case of a remote computer. For example: **D:\remoteInstall**. |
| [/Authorize] | Authorizes the server in Dynamic Host Control Protocol (DHCP). This option is necessary only if DHCP rogue detection is enabled, meaning that the Windows Deployment Services PXE server must be authorized in DHCP before client computers can be serviced. Note that DHCP rogue detection is disabled by default. |

## Examples

To initialize the server and set the remoteInstall shared folder to the F: drive, type.

```
wdsutil /Initialize-Server /remInst:F:\remoteInstall
```

To initialize the server and set the remoteInstall shared folder to the C: drive, type.

```
wdsutil /verbose /Progress /Initialize-Server /Server:MyWDSServer /remInst:C:\remoteInstall
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil disable-server command](wdsutil-disable-server)
- [wdsutil enable-server command](wdsutil-enable-server)
- [wdsutil get-server command](wdsutil-get-server)
- [wdsutil set-server command](wdsutil-set-server)
- [wdsutil start-server command](wdsutil-start-server)
- [wdsutil stop-server command](wdsutil-stop-server)
- [wdsutil uninitialize-server command](wdsutil-uninitialize-server)