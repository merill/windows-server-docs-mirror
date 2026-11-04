---
layout: Conceptual
title: ksetup mapuser | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-mapuser
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup mapuser command, which maps the name of a Kerberos principal to an account.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d64cd961-9439-707b-481c-1a1e4f1094df
document_version_independent_id: d694e092-beb5-0014-4bc6-8c0e8315a96b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-mapuser.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-mapuser
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-mapuser.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ab600e62-aebd-02c3-509c-7c7b37319ef6
---

# ksetup mapuser | Microsoft Learn

Maps the name of a Kerberos principal to an account.

## Syntax

```
ksetup /mapuser <principal> <account>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<principal>` | Specifies the fully-qualified domain name of any principal user. For example, mike@corp.CONTOSO.COM. If you don't specify an account parameter, mapping is deleted for the specified principal. |
| `<account>` | Specifies any account or security group name that exists on this computer, such as **Guest**, **Domain Users**, or **Administrator**. If this parameter is omitted, mapping is deleted for the specified principal. |

#### Remarks

- An account can be specifically identified, such as **Domain Guests**, or you can use a wildcard character (\*) to include all accounts.
- The computer only authenticates the principals of the given realm if they present valid Kerberos tickets.
- Whenever changes are made to the external Key Distribution Center (KDC) and the realm configuration, a restart of the computer where the setting was changed is required.

### Examples

To see the current mapped settings and the default realm, type:

```
ksetup
```

To map Mike Danseglio's account within the Kerberos realm CONTOSO to the guest account on this computer, granting him all the privileges of a member of the built-in Guest account without having to authenticate to this computer, type:

```
ksetup /mapuser mike@corp.CONTOSO.COM guest
```

To remove the mapping of Mike Danseglio's account to the guest account on this computer to prevent him from authenticating to this computer with his credentials from CONTOSO, type:

```
ksetup /mapuser mike@corp.CONTOSO.COM
```

To map Mike Danseglio's account within the CONTOSO Kerberos realm to any existing account on this computer, type:

```
ksetup /mapuser mike@corp.CONTOSO.COM *
```

Note

If only the Standard User and Guest accounts are active on this computer, Mike's privileges are set to those.

To map all accounts within the CONTOSO Kerberos realm to any existing account of the same name on this computer, type:

```
ksetup /mapuser * *
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)