---
layout: Conceptual
title: attach vdisk | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/attach-vdisk
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the attach vdisk command, which attaches (sometimes called mounts or surfaces) a virtual hard disk (VHD) so that it appears on the host computer as a local hard disk drive.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 1dcedf1a-0adb-f598-8e28-15e3c9067e3a
document_version_independent_id: cc5641d6-f7f4-0200-bb44-742173d289ce
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/attach-vdisk.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/attach-vdisk
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/attach-vdisk.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/062d60c9-ee0f-402e-a046-b4e67c3572d6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/17d3b3f6-a66e-4c69-9774-14a73c38e669
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8a2893e6-e6c1-c91e-853b-cc19f7512d75
---

# attach vdisk | Microsoft Learn

Attaches (sometimes called mounts or surfaces) a virtual hard disk (VHD) so that it appears on the host computer as a local hard disk drive. If the VHD already has a disk partition and file system volume when you attach it, the volume inside the VHD is assigned a drive letter.

Important

You must choose and detach a VHD for this operation to succeed. Use the **select vdisk** command to select a VHD and shift the focus to it.

## Syntax

```
attach vdisk [readonly] { [sd=<SDDL>] | [usefilesd] } [noerr]
```

### Parameters

| Parameter | Description |
| --- | --- |
| readonly | Attaches the VHD as read-only. Any write operation returns an error. |
| `sd=<SDDL string>` | Sets the user filter on the VHD. The filter string must be in the Security Descriptor Definition Language (SDDL) format. By default the user filter allows access like on a physical disk. SDDL strings can be complex, but in its simplest form, a security descriptor that protects access is known as a discretionary access control list (DACL). It uses the form: `D:<dacl_flags><string_ace1><string_ace2>`... `<string_acen>`<br>Common DACL flags are:<br><br>- **A**. Allow access<br>- **D**. Deny access<br><br>Common rights are:<br>- **GA**. All access<br>- **GR**. Read access<br>- **GW**. Write access<br><br>Common user accounts are:<br>- **BA**. Built in administrators<br>- **AU**. Authenticated users<br>- **CO**. Creator owner<br>- **WD**. Everyone<br><br>Examples:<br>- **D:P:(A;;GR;;;AU**. Gives read-access to all authenticated users.<br>- **D:P:(A;;GA;;;WD**. Gives everyone full access. |
| usefilesd | Specifies that the security descriptor on the .vhd file should be used on the VHD. If the **Usefilesd** parameter is not specified, the VHD will not have an explicit security descriptor unless it is specified with the **Sd** parameter. |
| noerr | Used for scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error code. |

## Examples

To attach the selected VHD as read-only, type:

```
attach vdisk readonly
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [select vdisk](select-vdisk)
- [compact vdisk](compact-vdisk)
- [detail vdisk](detail-vdisk)
- [detach vdisk](detach-vdisk)
- [expand vdisk](expand-vdisk)
- [merge vdisk](merge-vdisk)
- [list](list)