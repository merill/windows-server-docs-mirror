---
layout: Conceptual
title: tapicfg install | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tapicfg-install
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the tapicfg install command, which creates a TAPI application directory partition.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2020-09-29T00:00:00.0000000Z
locale: en-us
document_id: d0fc7913-beb3-1304-97f9-f23cc383f959
document_version_independent_id: 92a5f417-b8d2-1055-7fa5-550d440fcb71
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tapicfg-install.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tapicfg-install
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tapicfg-install.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: f0edab12-2746-ac31-0d76-36e4a1e677d3
---

# tapicfg install | Microsoft Learn

Creates a TAPI application directory partition.

Important

You must be a member of the Enterprise Admins group in active directory to run this command.

## Syntax

```
tapicfg install /directory:<partitionname> [/server:<DCname>] [/forcedefault]
```

### Parameters

| Parameter | Description |
| --- | --- |
| install `/directory:<partitionname>` | Required. Specifies the DNS name of the TAPI application directory partition to be created. This name must be a fully-qualified domain name. |
| /server: `<DCname>` | Specifies the DNS name of the domain controller on which the TAPI application directory partition is created. If the domain controller name isn't specified, the name of the local computer is used. |
| /forcedefault | Specifies that this directory is the default TAPI application directory partition for the domain. There can be multiple TAPI application directory partitions in a domain.<br>if this directory is the first TAPI application directory partition created on the domain, it's automatically set as the default, regardless of whether you use the **/forcedefault** option. |
| /? | Displays help at the command prompt. |

#### Remarks

- This command-line tool can be run on any computer that is a member of the domain.
- User-supplied text (such as the names of TAPI application directory partitions, servers, and domains) with International or Unicode characters are only displayed correctly if appropriate fonts and language support are installed.
- You can still use Internet Locator Service (ILS) servers in your organization, if ILS is needed to support certain applications, because TAPI clients running Windows XP or a Windows Server 2003 operating system can query either ILS servers or TAPI application directory partitions.
- You can use **tapicfg** to create or remove service connection points. If the TAPI application directory partition is renamed for any reason (for example, if you rename the domain in which it resides), you must remove the existing service connection point and create a new one that contains the new DNS name of the TAPI application directory partition to be published. Otherwise, TAPI clients are unable to locate and access the TAPI application directory partition. You can also remove a service connection point for maintenance or security purposes (for example, if you do not want to expose TAPI data on a specific TAPI application directory partition).

## Examples

To create a TAPI application directory partition named *tapifiction.testdom.microsoft.com* on a server named *testdc.testdom.microsoft.com*, and then set it as the default TAPI application directory partition for the new domain, type:

```
tapicfg install /directory:tapifiction.testdom.microsoft.com /server:testdc.testdom.microsoft.com /forcedefault
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [tapicfg remove](tapicfg-remove)
- [tapicfg publishscp](tapicfg-publishscp)
- [tapicfg removescp](tapicfg-removescp)
- [tapicfg show](tapicfg-show)
- [tapicfg makedefault](tapicfg-makedefault)