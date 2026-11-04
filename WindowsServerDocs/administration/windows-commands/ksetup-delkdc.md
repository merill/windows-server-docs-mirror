---
layout: Conceptual
title: ksetup delkdc | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-delkdc
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup delkdc command, which deletes instances of Key Distribution Center (KDC) names for the Kerberos realm.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d8c24c33-9aff-40db-48b9-83ad708c1fd0
document_version_independent_id: 039e6600-9c0d-4938-fbc3-ef9375ebe8e3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-delkdc.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-delkdc
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-delkdc.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: cc0b10c8-5ffb-7658-b444-4f8a289fda07
---

# ksetup delkdc | Microsoft Learn

Deletes instances of Key Distribution Center (KDC) names for the Kerberos realm.

The mapping is stored in the registry, under `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\LSA\Kerberos\Domains`. After running this command, we recommend making sure the KDC was removed and no longer appears in the list.

Note

To remove realm configuration data from multiple computers, use the **Security Configuration Template** snap-in with policy distribution, instead of using the **ksetup** command explicitly on individual computers.

## Syntax

```
ksetup /delkdc <realmname> <KDCname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<realmname>` | Specifies the uppercase DNS name, such as CORP.CONTOSO.COM. This is the default realm that appears when you run the **ksetup** command, and it's the realm from which you want to delete the KDC. |
| `<KDCname>` | Specifies the case-sensitive, fully-qualified domain name, such as mitkdc.contoso.com. |

### Examples

To view all of the associations between the Windows realm and the non-Windows realm, and to determine which ones to remove, type:

```
ksetup
```

To remove the association, type:

```
ksetup /delkdc CORP.CONTOSO.COM mitkdc.contoso.com
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)
- [ksetup addkdc command](ksetup-addkdc)