---
layout: Conceptual
title: tpmtool | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/tpmtool
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the tpmtool command, which gets information about the Trusted Platform Module.
ms.topic: reference
author: robinharwood
ms.author: roharwoo
ms.date: 2019-05-07T00:00:00.0000000Z
locale: en-us
document_id: 8ca4b399-8d38-b98c-99eb-80aebeb1d4f2
document_version_independent_id: df0242c5-746b-f4d5-c254-7a8573b400ce
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/tpmtool.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/tpmtool
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/tpmtool.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fe286dbb-b266-484b-6bac-bcfff976a867
---

# tpmtool | Microsoft Learn

This utility can be used to get information about the [Trusted Platform Module (TPM)](/en-us/windows/security/information-protection/tpm/trusted-platform-module-overview).

Important

Some information may relate to the pre-released product, which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

## Syntax

```
tpmtool /parameter [<arguments>]
```

### Parameters

| Parameter | Description |
| --- | --- |
| getdeviceinformation | Displays the basic information of the TPM. See the [Win32_Tpm::IsReadyInformation method parameters](/en-us/windows/win32/secprov/win32-tpm-isreadyinformation#parameters) article for details about the information flag values. |
| gatherlogs [output directory path] | Collects TPM logs and places them in the specified directory. If that directory doesn't exist, it's created. By default, the log files are placed in the current directory. The possible files generated are:<br>- TpmEvents.evtx<br>- TpmInformation.txt<br>- SRTMBoot.dat<br>- SRTMResume.dat<br>- DRTMBoot.dat<br>- DRTMResume.dat |
| drivertracing `[start | stop]` | Starts or stops collecting TPM driver traces. The trace log, *TPMTRACE.etl*, is created and placed in the current directory. |
| /? | Displays help at the command prompt. |

## Examples

To display the basic information of the TPM, type:

```
tpmtool getdeviceinformation
```

To collect TPM logs and place them in the current directory, type:

```
tpmtool gatherlogs
```

To collect TPM logs and place them in `C:\Users\Public`, type:

```
tpmtool gatherlogs C:\Users\Public
```

To collect TPM driver traces, type:

```
tpmtool drivertracing start
# Run scenario
tpmtool drivertracing stop
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [COM Error Codes (TPM, PLA, FVE)](/en-us/windows/win32/com/com-error-codes-6)