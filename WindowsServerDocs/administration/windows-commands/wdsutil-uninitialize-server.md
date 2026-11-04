---
layout: Conceptual
title: wdsutil uninitialize-server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-uninitialize-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for uninitialize-Server, which reverts changes made to the server during the initial server configuration.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 160b63c0-6c7a-73d3-ad02-fe987c249885
document_version_independent_id: a0447a6f-b81a-9c35-ea45-d0ae00b1d0f1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-uninitialize-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-uninitialize-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-uninitialize-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 31fda24d-4a99-1fd4-22b0-a4c1f1b2662d
---

# wdsutil uninitialize-server | Microsoft Learn

Reverts changes made to the server during the initial server configuration. This includes changes made by either the **/initialize-server** option or the Windows Deployment Services mmc snap-in. Note that this command resets the server to an unconfigured state. This command does not modify the contents of the remoteInstall shared folder. Rather, it resets the server's state so that you can reinitialize the server.

## Syntax

```
wdsutil [Options] /Uninitialize-Server [/Server:<Server name>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |

## Examples

To reinitialize the server, type one of the following:

```
wdsutil /Uninitialize-Server
wdsutil /verbose /Uninitialize-Server /Server:MyWDSServer
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil disable-server command](wdsutil-disable-server)
- [wdsutil enable-server command](wdsutil-enable-server)
- [wdsutil get-server command](wdsutil-get-server)
- [wdsutil initialize-server command](wdsutil-initialize-server)
- [wdsutil set-server command](wdsutil-set-server)
- [wdsutil start-server command](wdsutil-start-server)
- [wdsutil stop-server command](wdsutil-stop-server)