---
layout: Conceptual
title: netsh netio | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/netsh-netio
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: The netsh netio command  manages network binding filters in Windows.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-08-12T00:00:00.0000000Z
locale: en-us
document_id: 3b04a74a-06f3-f1c4-e8d8-00822389f1f5
document_version_independent_id: 3b04a74a-06f3-f1c4-e8d8-00822389f1f5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/netsh-netio.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/netsh-netio
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/netsh-netio.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 044670ef-4f29-1712-23eb-394b10a61c19
---

# netsh netio | Microsoft Learn

The `netsh netio` command is used to manage network binding filters, allowing administrators to control which clients can bind to specific network providers.

## Syntax

```
netsh netio [add | delete | dump | help | show | ?]
```

```
netsh netio add bindingfilter [npi=]<string> [client=]<string> [provider=]<string>
                              [type=](block|singleclient) [store=](active|persistent)
```

```
netsh netio delete bindingfilter [npi=]<string> [client=]<string> [provider=]<string>
                                 [store=](active|persistent)
```

```
netsh netio dump
```

```
netsh netio show bindingfilter [store=](active|persistent)
```

## Parameters

| Command | Description |
| --- | --- |
| netio `add bindingfilter` | Adds a new binding filter. - **npi** - Specifies the NPI (Network Programming Interface) GUID or name.<br>- **client** - Specifies the client GUID or name.<br>- **provider** - Specifies the provider GUID or name.<br>- **type** - Determines the filter type. `block` prevents the specified client from binding to the provider. `singleclient` allows only the specified client to bind to the provider (default).<br>- **store** - Specifies filter persistence. `active` indicates the filter is temporary and will disappear on the next boot. `persistent` indicates the filter remains in effect across reboots (default). |
| netio `delete bindingfilter` | Removes an existing binding filter. - **npi** - Specifies the NPI GUID or name.<br>- **client** - Specifies the client GUID or name.<br>- **provider** - Specifies the provider GUID or name.<br>- **store** - Specifies filter persistence. `active` indicates the filter removal is temporary will reappear after the system is rebooted. `persistent` indicates the filter removal is permanent and remains in effect across system reboots (default). |
| netio `dump` | Creates a script containing the current netio configuration. The script can be saved to a file and used to restore settings if they're altered or need to be replicated on another system. |
| netio `show bindingfilter` | Displays all binding filters. **store** - Specifies the filter persistence. `active` displays the filters in the stack (default). `persistent` displays all persistent filters. |
| `help`*or*`?` | Displays a list of commands and their descriptions in the current context. |

## Examples

To block a specified client from binding to a provider persistently, you can run the following command:

```cmd
netsh netio add bindingfilter npi="NPI_Name" client="Client_Name" provider="Provider_Name" type=block store=persistent
```

To permanently remove a binding filter, you can run the following command:

```cmd
netsh netio delete bindingfilter npi="NPI_Name" client="Client_Name" provider="Provider_Name" store=persistent
```

To display all active binding filters, you can run the following command:

```cmd
netsh netio show bindingfilter store=active
```