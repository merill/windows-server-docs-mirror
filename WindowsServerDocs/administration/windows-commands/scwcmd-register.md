---
layout: Conceptual
title: scwcmd register | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/scwcmd-register
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the scwcmd register command, which extends or customizes the Security Configuration Wizard (SCW) Security Configuration Database by registering a Security Configuration Database file that contains role, task, service, or port definitions.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: f0af489b-4e52-fec6-ce5e-b538c0856666
document_version_independent_id: d2fe8d9f-3504-d370-127a-c32f4ef86cc4
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/scwcmd-register.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/scwcmd-register
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/scwcmd-register.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 75a2726c-abc2-0ae7-9713-ae8697cafa4d
---

# scwcmd register | Microsoft Learn

Extends or customizes the Security Configuration Wizard (SCW) Security Configuration Database by registering a Security Configuration Database file that contains role, task, service, or port definitions.

## Syntax

```
scwcmd register /kbname:<MyApp> [/kbfile:<kb.xml>] [/kb:<path>] [/d]
```

### Parameters

| Parameter | Description |
| --- | --- |
| /kbname:`<MyApp>` | Specifies the name under which the Security Configuration Database extension will be registered. This parameter must be specified. |
| /kbfile:`<kb.xml>` | Specifies the path and file name of the Security Configuration Database file used to extend or customize the base Security Configuration Database. To validate that the Security Configuration Database file is compliant with the SCW schema, use the `%windir%\security\KBRegistrationInfo.xsd` schema definition file. This option must be provided unless the **/d** parameter is specified. |
| /kb:`<path>` | Specifies the path to the directory that contains the SCW Security Configuration Database files to be updated. If this option is not specified, `%windir%\security\msscw\kbs` is used. |
| /d | Unregisters a Security Configuration Database extension from the Security Configuration Database. The extension to unregister is specified by the **/kbname** parameter. (The **/kbfile** parameter shouldn't be specified.) The Security Configuration Database to unregister the extension from is specified by the **/kb** parameter. |
| /? | Displays help at the command prompt. |

## Examples

To register the Security Configuration Database file named *SCWKBForMyApp.xml* under the name *MyApp* in the location `\\kbserver\kb`, type:

```
scwcmd register /kbfile:d:\SCWKBForMyApp.xml /kbname:MyApp /kb:\\kbserver\kb
```

To unregister the Security Configuration Database *MyApp*, located at `\\kbserver\kb`, type:

```
scwcmd register /d /kbname:MyApp /kb:\\kbserver\kb
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [scwcmd analyze command](scwcmd-analyze)
- [scwcmd configure command](scwcmd-configure)
- [scwcmd rollback command](scwcmd-rollback)
- [scwcmd transform command](scwcmd-transform)
- [scwcmd view command](scwcmd-view)