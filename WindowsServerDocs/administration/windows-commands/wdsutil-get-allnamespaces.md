---
layout: Conceptual
title: wdsutil get-allnamespaces | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wdsutil-get-allnamespaces
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wdsutil get-allnamespaces, which displays information about all namespaces on a server.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: fde62d48-8cdc-6163-930b-8a5c9ee64ec5
document_version_independent_id: 021d77e4-7707-5eaa-7d48-3d720bd64893
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wdsutil-get-allnamespaces.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wdsutil-get-allnamespaces
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wdsutil-get-allnamespaces.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 3894bc18-eb29-79f2-135e-1610774a7ee3
---

# wdsutil get-allnamespaces | Microsoft Learn

Displays information about all namespaces on a server.

## Syntax

Windows Server 2008:

```
wdsutil /Get-AllNamespaces [/Server:<Server name>] [/ContentProvider:<name>] [/Show:Clients] [/ExcludedeletePending]
```

Windows Server 2008 R2:

```
wdsutil /Get-AllNamespaces [/Server:<Server name>] [/ContentProvider:<name>] [/details:Clients] [/ExcludedeletePending]
```

### Parameters

| Parameter | Windows Server 2008 | Windows Server 2008 R2 |
| --- | --- | --- |
| [/Server:&lt;Server name&gt;] | Specifies the name of the server. This can be either the NetBIOS name or the fully qualified domain name (FQDN). If no server name is specified, the local server will be used. |  |
| [/ContentProvider:&lt;name&gt;] | Displays the namespaces for the specified content provider only. |  |
| [/Show:Clients] | Only supported for Windows Server 2008. Displays information about client computers that are connected to the namespace. |  |
| [/details:Clients] | Only supported for Windows Server 2008 R2. Displays information about client computers that are connected to the namespace. |  |
| [/ExcludedeletePending] | Excludes any deactivated transmissions from the list. |  |

## Examples

To view all namespaces, type:

```
wdsutil /Get-AllNamespaces
```

To view all namespaces except those that are deactivated, type:

- Windows Server 2008 

    ```
    wdsutil /Get-AllNamespaces /Server:MyWDSServer /ContentProvider:MyContentProv /Show:Clients /ExcludedeletePending
    ```
- Windows Server 2008 R2 

    ```
    wdsutil /Get-AllNamespaces /Server:MyWDSServer /ContentProvider:MyContentProv /details:Clients /ExcludedeletePending
    ```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [wdsutil new-namespace command](wdsutil-new-namespace)
- [wdsutil remove-namespace command](wdsutil-remove-namespace)
- [wdsutil start-nmespace command](wdsutil-start-namespace)