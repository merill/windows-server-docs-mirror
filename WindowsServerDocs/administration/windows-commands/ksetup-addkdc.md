---
layout: Conceptual
title: ksetup addkdc | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-addkdc
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup addkdc command, which ads a Key Distribution Center (KDC) address for the given Kerberos realm.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f1423ffa-abc1-2958-683f-9015a9cedd1f
document_version_independent_id: 68452ebe-ad5b-b6d0-60dd-29d9e84612a1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-addkdc.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-addkdc
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-addkdc.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: be4bdd3e-53b9-2db9-8aad-b0054fb2b7fd
---

# ksetup addkdc | Microsoft Learn

Adds a Key Distribution Center (KDC) address for the given Kerberos realm

The mapping is stored in the registry, under **HKEY\_LOCAL\_MACHINE\System\CurrentControlSet\Control\LSA\Kerberos\Domains** and the computer must be restarted before the new realm setting will be used.

Note

To deploy Kerberos realm configuration data to multiple computers, you must use the **Security Configuration Template** snap-in and policy distribution, explicitly on individual computers. You can't use this command.

## Syntax

```
ksetup /addkdc <realmname> [<KDCname>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<realmname>` | Specifies the uppercase DNS name, such as CORP.CONTOSO.COM. This value also appears as the default realm when **ksetup** is run, and is the realm to which you want to add the other KDC. |
| `<KDCname>` | Specifies the case-insensitive, fully-qualified domain name, such as mitkdc.contoso.com. If the KDC name is omitted, DNS will locate KDCs. |

### Examples

To configure a non-Windows KDC server and the realm that the workstation should use, type:

```
ksetup /addkdc CORP.CONTOSO.COM mitkdc.contoso.com
```

To set the local computer account password to p@sswrd1% on the same computer as in the previous example, and then to restart the computer, type:

```
ksetup /setcomputerpassword p@sswrd1%
```

To verify the default realm name for the computer or to verify that this command worked as intended, type:

```
ksetup
```

Check the registry to make sure the mapping occurred as intended.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)
- [ksetup setcomputerpassword command](ksetup-setcomputerpassword)