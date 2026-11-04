---
layout: Conceptual
title: ksetup dumpstate | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/ksetup-dumpstate
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the ksetup dumpstate command, which displays the current state of realm settings for all realms that are defined on the computer.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 161a2c30-8240-bddf-3de3-569d55d217d5
document_version_independent_id: 32b5605a-ecb6-a043-0593-e2a34a913064
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/ksetup-dumpstate.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/ksetup-dumpstate
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/ksetup-dumpstate.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4ad6dcd4-f104-3767-4057-9cbcd2e3fa80
---

# ksetup dumpstate | Microsoft Learn

Displays the current state of realm settings for all realms that are defined on the computer. This command displays the same output as the **ksetup** command.

## Syntax

```
ksetup /dumpstate
```

### Remarks

- The output of this command includes the default realm (the domain that the computer is a member of) and all the realms that are defined on this computer. The following is included for each realm:

    - All the Key Distribution Centers (KDCs) that are associated with this realm.
    - All the **set realm** flags for this realm.
    - The KDC password.
- This command doesn't display the domain name specified by DNS detection or by the command `ksetup /domain`.
- This command doesn't display the computer password set by using the command `ksetup /setcomputerpassword`.

## Examples

To locate the Kerberos realm configurations on a computer, type:

```
ksetup /dumpstate
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [ksetup command](ksetup)