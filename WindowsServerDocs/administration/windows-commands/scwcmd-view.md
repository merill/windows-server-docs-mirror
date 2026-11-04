---
layout: Conceptual
title: scwcmd view | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/scwcmd-view
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the scwcmd view command, which renders an .xml file by using a specified .xsl transform.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f7f103dd-9573-b95c-869f-be3af107295a
document_version_independent_id: 41db4c36-9993-8f7b-468f-21f1915cffca
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/scwcmd-view.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/scwcmd-view
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/scwcmd-view.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 75c3b579-d3c5-58f2-a20e-d5efee4142ba
---

# scwcmd view | Microsoft Learn

Renders an .xml file by using a specified .xsl transform. This command can be useful for displaying Security Configuration Wizard (SCW) .xml files by using different views.

## Syntax

```
scwcmd view /x:<Xmlfile.xml> [/s:<Xslfile.xsl>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /x:`<Xmlfile.xml>` | Specifies the .xml file to be viewed. This parameter must be specified. |
| /s:`<Xslfile.xsl>` | Specifies the .xsl transform to apply to the .xml file as part of the rendering process. This parameter is optional for SCW .xml files. When the **view** command is used to render a SCW .xml file, it will automatically try to load the correct default transform for the specified .xml file. If an .xsl transform is specified, the transform must be written under the assumption that the .xml file is in the same directory as the .xsl transform. |
| /? | Displays help at the command prompt. |

## Example

To view *Policyfile.xml* by using the *Policyview.xsl* transform, type:

```
scwcmd view /x:C:\policies\Policyfile.xml /s:C:\viewers\Policyview.xsl
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [scwcmd analyze command](scwcmd-analyze)
- [scwcmd configure command](scwcmd-configure)
- [scwcmd register command](scwcmd-register)
- [scwcmd rollback command](scwcmd-rollback)
- [scwcmd transform command](scwcmd-transform)