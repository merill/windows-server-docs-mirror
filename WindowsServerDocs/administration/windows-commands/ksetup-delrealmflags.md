---
layout: Conceptual
title: ksetup delrealmflags | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-delrealmflags
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup delrealmflags command, which removes realm flags from the specified realm.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 1385a375-0e36-2677-0dd9-56a442f3c69b
document_version_independent_id: 112cfb96-0275-809b-92b8-874ab5b73819
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-delrealmflags.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-delrealmflags
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-delrealmflags.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 32ebef80-3785-8719-a519-3def90e3d0ee
---

# ksetup delrealmflags | Microsoft Learn

Removes realm flags from the specified realm.

## Syntax

```
ksetup /delrealmflags <realmname> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<realmname>` | Specifies the uppercase DNS name, such as CORP.CONTOSO.COM, and is listed as the default realm or **Realm=** when **ksetup** is run. |

#### Remarks

- The realm flags specify additional features of a Kerberos realm that aren't based on the Windows Server operating system. Computers that are running Windows Server, can use a Kerberos server to administer authentication in the Kerberos realm, instead of using a domain running a Windows Server operating system. This entry establishes the features of the realm, and are as follows:

| Value | Realm flag | Description |
| --- | --- | --- |
| 0xF | All | All realm flags are set. |
| 0x00 | None | No realm flags are set, and no additional features are enabled. |
| 0x01 | sendaddress | The IP address will be included within the ticket-granting tickets. |
| 0x02 | tcpsupported | Both the Transmission Control Protocol (TCP) and the User Datagram Protocol (UDP) are supported in this realm. |
| 0x04 | delegate | Everyone in this realm is trusted for delegation. |
| 0x08 | ncsupported | This realm supports name canonicalization, which allows for DNS and Realm naming standards. |
| 0x80 | rc4 | This realm supports RC4 encryption to enable cross-realm trust, which allows for the use of TLS. |

- Realm flags are stored in the registry under `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\Domains\<realmname>`. This entry doesn't exist in the registry by default. You can use the [ksetup addrealmflags command](ksetup-addrealmflags) to populate the registry.
- You can see the available and set realm flags by viewing the output of **ksetup** or `ksetup /dumpstate`.

### Examples

To list the available realm flags for the realm CONTOSO, type:

```
ksetup /listrealmflags
```

To remove two flags currently in the set, type:

```
ksetup /delrealmflags CONTOSO ncsupported delegate
```

To verify the realm flags have been removed, type `ksetup` and then view the output, looking for the text, **Realm flags =**.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)
- [ksetup listrealmflags command](ksetup-listrealmflags)
- [ksetup setrealmflags command](ksetup-setrealmflags)
- [ksetup addrealmflags command](ksetup-addrealmflags)
- [ksetup dumpstate command](ksetup-dumpstate)