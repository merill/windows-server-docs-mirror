---
layout: Conceptual
title: wdsutil disconnect-client | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-disconnect-client
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the wdsutil disconnect-client command, which disconnects a client from a multicast transmission or namespace.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d340e7ca-2acb-df77-cf88-a74b2fb2c51b
document_version_independent_id: af599fe9-3fd8-ffc9-28b6-8d94094abd00
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-disconnect-client.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-disconnect-client
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-disconnect-client.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: a864bb52-8091-2a3b-9e79-edebf3ed0edf
---

# wdsutil disconnect-client | Microsoft Learn

Disconnects a client from a multicast transmission or namespace. Unless you specify **/Force**, the client will fall back to another transfer method (if it's supported by the client).

## Syntax

```
wdsutil /Disconnect-Client /ClientId:<Client ID> [/Server:<Server name>] [/Force]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /ClientId:`<ClientID>` | Specifies the ID of the client to be disconnected. To view the ID of a client, run the `wdsutil /get-multicasttransmission /show:clients` command. |
| [/Server:`<Servername>`] | Specifies the name of the server. This can be the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server is used. |
| [/Force] | Stops the installation completely and does not use a fallback method. Because Wdsmcast.exe doesn't support any fallback mechanism, the default behavior is as follows:<br>- **If you're using the Windows Deployment Services client:** The client continues the installation by using unicasting.<br>- **If you aren't using the Windows Deployment Services client:** The installation fails.<br><br>**Important:** We strongly recommend using this parameter cautiously because if the installation fails, the computer can be left in an unusable state. |

## Examples

To disconnect a client, type:

```
wdsutil /Disconnect-Client /ClientId:1
```

To disconnect a client and force the installation to fail, type:

```
wdsutil /Disconnect-Client /Server:MyWDSServer /ClientId:1 /Force
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-multicasttransmission command](wdsutil-get-multicasttransmission)
- [Windows Deployment Services cmdlets](/en-us/powershell/module/wds)