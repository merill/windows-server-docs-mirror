---
layout: Conceptual
title: wdsutil new-namespace | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-new-namespace
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil new-namespace, which creates and configures a new namespace.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 137327b1-b3f3-b2d9-67cd-dd0ec3c26b67
document_version_independent_id: c61ab320-f219-b135-d913-a92c73017f7a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-new-namespace.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-new-namespace
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-new-namespace.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e923f240-7fa8-d199-6a96-a81d0760e8ca
---

# wdsutil new-namespace | Microsoft Learn

Creates and configures a new namespace. You should use this option when you have only the Transport Server role service installed. If you have both the Deployment Server role service and the Transport Server role service installed (which is the default), use [wdsutilnew-MulticastTransmission command](wdsutil-new-multicasttransmission). Note that you must register the content provider before you use this option.

## Syntax

```
wdsutil [Options] /New-Namespace [/Server:<Server name>]
     /FriendlyName:<Friendly name>
     [/Description:<Description>]
     /Namespace:<Namespace name>
     /ContentProvider:<Name>
     [/ConfigString:<Configuration string>]
     /Namespacetype: {AutoCast | ScheduledCast}
         [/time:<YYYY/MM/DD:hh:mm>]
         [/Clients:<Number of clients>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server is used. |
| /FriendlyName:&lt;Friendly name&gt; | Specifies the friendly name of the namespace. |
| [/Description:&lt;Description&gt;] | Sets the description of the namespace. |
| /Namespace:&lt;Namespace name&gt; | Specifies the name of the namespace. Note that this is not the friendly name, and it must be unique.<br>- **Deployment Server role service**: The syntax for this option is /Namespace:WDS:&lt;Image group&gt;/&lt;Image name&gt;/&lt;Index&gt;. For example: **WDS:ImageGroup1/install.wim/1**- **Transport Server role service**: This value should match the name given when the namespace was created on the server. |
| /ContentProvider:&lt;Name&gt;] | Specifies the name of the content provider that will provide content for the namespace. |
| [/ConfigString:&lt;Configuration string&gt;] | Specifies the configuration string for the content provider. |
| /Namespacetype: {AutoCast | ScheduledCast} | Specifies the settings for the transmission. You specify the settings using the following options:<br>- [/time: &lt;time&gt;] - Sets the time that the transmission should start by using the following format: YYYY/MM/DD:hh:mm. This option applies only to Scheduled-Cast transmissions.- [/Clients: &lt;Number of clients&gt;] - Sets the minimum number of clients to wait for before the transmission starts. This option applies only to Scheduled-Cast transmissions. |

## Examples

To create an Auto-Cast namespace, type:

```
wdsutil /New-Namespace /FriendlyName:Custom AutoCast Namespace /Namespace:Custom Auto 1 /ContentProvider:MyContentProvider /Namespacetype:AutoCast
```

To create a Scheduled-Cast namespace, type:

```
wdsutil /New-Namespace /Server:MyWDSServer /FriendlyName:Custom Scheduled Namespace /Namespace:Custom Auto 1 /ContentProvider:MyContentProvider
/Namespacetype:ScheduledCast /time:2006/11/20:17:00 /Clients:20
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil get-allnamespaces command](wdsutil-get-allnamespaces)
- [wdsutil remove-namespace command](wdsutil-remove-namespace)
- [wdsutil start-namespace command](wdsutil-start-namespace)