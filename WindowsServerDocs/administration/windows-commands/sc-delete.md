---
layout: Conceptual
title: sc delete | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/sc-delete
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the sc delete command, which deletes a service subkey from the registry.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-08-15T00:00:00.0000000Z
locale: en-us
document_id: 3ef8ad4c-710f-4a51-a0ed-cb2245f2051f
document_version_independent_id: b35a40fc-7798-c4ff-226c-20aad279fd39
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/sc-delete.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/sc-delete
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/sc-delete.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e3aeed57-6612-48a5-318d-cacfb049221c
---

# sc delete | Microsoft Learn

Deletes a service subkey from the registry. If the service is running or if another process has an open handle to the service, the service is marked for deletion.

Note

We don't recommend you to use this command to delete built-in operating system services such as DHCP, DNS, or Internet Information Services. To install, remove, or reconfigure operating system roles, services and components, see [Install or Uninstall Roles, Role Services, or Features](/en-us/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features)

## Syntax

```
sc <server> delete [service name]
```

### Parameters

| Parameter | Description |
| --- | --- |
| `<server>` | Specifies the name of the remote server on which the service is located. The name must use the Universal Naming Convention (UNC) format (for example, \\MyServer). To run `sc` locally, don't use this parameter. |
| `<service name>` | Specifies the service name returned by the **getkeyname** operation. |
| /? | Displays help at the command prompt. |

## Examples

To delete the service subkey **NewServ** from the registry on the local computer, type:

```
sc delete NewServ
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)