---
layout: Conceptual
title: ksetup delhosttorealmmap | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-delhosttorealmmap
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup delhosttorealmmap command, which removes a service principal name (SPN) mapping between the stated host and the realm.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 286a562b-b25b-629b-1126-3b9b4d2cbbd3
document_version_independent_id: dc381b4d-d8e4-ae23-31b2-6d9001bd24ae
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-delhosttorealmmap.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-delhosttorealmmap
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-delhosttorealmmap.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a4b68ab3-402a-4a5d-d408-73575eeb1560
---

# ksetup delhosttorealmmap | Microsoft Learn

Removes a service principal name (SPN) mapping between the stated host and the realm. This command also removes any mapping between a host to realm (or multiple hosts to realm).

The mapping is stored in the registry, under `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\HostToRealm`. After running this command, we recommend making sure the mapping appears in the registry.

## Syntax

```
ksetup /delhosttorealmmap <hostname> <realmname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<hostname>` | Specifies the fully-qualified domain name of the computer. |
| `<realmname>` | Specifies the uppercase DNS name, such as CORP.CONTOSO.COM. |

### Examples

To change the configuration of the realm CONTOSO, and to delete the mapping of the host computer IPops897 to the realm, type:

```
ksetup /delhosttorealmmap IPops897 CONTOSO
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)
- [ksetup addhosttorealmmap command](ksetup-addhosttorealmmap)