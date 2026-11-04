---
layout: Conceptual
title: cmstp | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/cmstp
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for cmstp, which installs or removes a Connection Manager service profile.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 861522a0-a4ac-0877-06d4-7f139a483d57
document_version_independent_id: 2df079bf-927a-01ec-3443-5d2e869d18df
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/cmstp.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/cmstp
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/cmstp.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b3689ff9-3240-06d9-1cf8-10bf3dd62c45
---

# cmstp | Microsoft Learn

Installs or removes a Connection Manager service profile. Used without optional parameters, **cmstp** installs a service profile with default settings appropriate to the operating system and to the user's permissions.

## Syntax

Syntax 1 - This is the typical syntax used in a custom installation application. To use this syntax, you must run **cmstp** from the directory that contains the `<serviceprofilefilename>.exe` file.

```
<serviceprofilefilename>.exe /q:a /c:cmstp.exe <serviceprofilefilename>.inf [/nf] [/s] [/u]
```

Syntax 2

```
cmstp.exe [/nf] [/s] [/u] [drive:][path]serviceprofilefilename.inf
```

#### Parameters

| Parameter | Description |
| --- | --- |
| `<serviceprofilefilename>.exe` | Specifies, by name, the installation package that contains the profile that you want to install.<br>Required for Syntax 1, but not valid for Syntax 2. |
| /q:a | Specifies that the profile should be installed without prompting the user. The verification message that the installation has succeeded will still appear.<br>Required for Syntax 1, but not valid for Syntax 2. |
| [drive:][path] `<serviceprofilefilename>.inf` | Required. Specifies, by name, the configuration file that determines how the profile should be installed.<br>The [drive:][path] parameter isn't valid for Syntax 1. |
| /nf | Specifies that the support files should not be installed. |
| /s | Specifies that the service profile should be installed or uninstalled silently (without prompting for user response or displaying verification message). This is the only parameter that you can use in combination with **/u**. |
| /u | Specifies that the service profile should be uninstalled. |
| /? | Displays help at the command prompt. |

## Examples

To install the *fiction* service profile without any support files, type:

```
fiction.exe /c:cmstp.exe fiction.inf /nf
```

To silently install the *fiction* service profile for a single user, type:

```
fiction.exe /c:cmstp.exe fiction.inf /s /su
```

To silently uninstall the *fiction* service profile, type:

```
fiction.exe /c:cmstp.exe fiction.inf /s /u
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)