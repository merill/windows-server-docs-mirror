---
layout: Conceptual
title: ksetup removerealm | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-removerealm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup removerealm command, which deletes all information for the specified realm from the registry.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 69960a51-ca24-2ea8-51c8-b4ef2a9f8302
document_version_independent_id: 10344d25-12eb-698f-b508-3b537bcfaf35
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-removerealm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-removerealm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-removerealm.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0c5a6dfe-4005-7582-47a0-ea54762e3e5f
---

# ksetup removerealm | Microsoft Learn

Deletes all information for the specified realm from the registry.

The realm name is stored in the registry under `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos` and `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Lsa\Kerberos`. This entry doesn't exist in the registry by default. You can use the [ksetup addrealmflags](ksetup-addrealmflags) command to populate the registry.

Important

You can't remove the default realm name from the domain controller because this resets its DNS information, and removing it might make the domain controller unusable.

## Syntax

```
ksetup /removerealm <realmname>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<realmname>` | Specifies the uppercase DNS name, such as CORP.CONTOSO.COM, and is listed as the default realm or **Realm=** when **ksetup** is run. |

### Examples

To remove an erroneous realm name (.CON instead of .COM) from the local computer, type:

```
ksetup /removerealm CORP.CONTOSO.CON
```

To verify the removal, you can run the **ksetup** command and review the output.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)
- [ksetup setrealm command](ksetup-setrealm)