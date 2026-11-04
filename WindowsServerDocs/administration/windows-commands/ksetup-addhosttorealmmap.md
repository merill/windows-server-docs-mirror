---
layout: Conceptual
title: ksetup addhosttorealmmap | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-addhosttorealmmap
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup addhosttorealmmap command, which adds a service principal name (SPN) mapping between the stated host and the realm.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 4e21a29b-ad56-2f49-c190-afb45c7e4a6a
document_version_independent_id: 2ec7fcfb-0504-d331-005b-acb2b14cbacd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-addhosttorealmmap.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-addhosttorealmmap
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-addhosttorealmmap.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f3fc9631-c448-c6fd-0976-dc26a283a852
---

# ksetup addhosttorealmmap | Microsoft Learn

Adds a service principal name (SPN) mapping between the stated host and the realm. This command also allows you to map a host or multiple hosts that are sharing the same DNS suffix to the realm.

The mapping is stored in the registry, under **HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\HostToRealm**.

## Syntax

```
ksetup /addhosttorealmmap <hostname> <realmname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<hostname>` | The host name is the computer name, and it can be stated as the computer's fully qualified domain name. |
| `<realmname>` | The realm name is stated as an uppercase DNS name, such as CORP.CONTOSO.COM. |

### Examples

To map the host computer *IPops897* to the *CONTOSO* realm, type:

```
ksetup /addhosttorealmmap IPops897 CONTOSO
```

Check the registry to make sure the mapping occurred as intended.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)
- [ksetup delhosttorealmmap command](ksetup-delhosttorealmmap)