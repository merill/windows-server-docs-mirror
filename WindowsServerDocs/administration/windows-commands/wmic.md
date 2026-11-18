---
layout: Conceptual
title: wmic | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/wmic
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for wmic, which displays WMI information inside an interactive command shell.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-19T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: da66c962-ba67-2ed4-dd50-99142632a981
document_version_independent_id: 8d394b19-cbe3-42be-0f25-aebf2323b538
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/wmic.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/wmic
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/wmic.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 8f562ab3-1a37-8326-6628-e5b03ca563c1
---

# wmic | Microsoft Learn

Displays WMI information inside an interactive command shell.

Important

The Windows Management Instrumentation (WMI) command-line (WMIC) utility is deprecated as of Windows 10, version 21H1, and as of the 21H1 semi-annual channel release of Windows Server. Beginning with Windows Server 2025, WMIC is available as a Feature on Demand (FOD). To add WMIC, use the `DISM /Add-Capability` command. The announced Windows Server 2028 (preview) release removes the WMIC utility. Windows Server 2028 is in preview, and this removal announcement doesn't mean that WMIC is absent from current preview builds. WMIC might still be available in current preview builds, and the removal plans can change before release. This deprecation and removal apply only to the WMIC utility; WMI itself is not removed. Windows PowerShell replaces this utility for WMI (see [Chapter 7 - Working with WMI](/en-us/powershell/scripting/learn/ps101/07-working-with-wmi)). Use PowerShell or programmatically query WMI as a replacement for WMIC. For more information, see [Features removed or no longer developed in Windows Server](../../get-started/removed-deprecated-features-windows-server) and [Windows 10 features we're no longer developing](/en-us/windows/deployment/planning/windows-10-deprecated-features).

## Syntax

```cmd
wmic </parameter>
```

## Sub-commands

The following sub-commands are available:

| Sub-command | Description |
| --- | --- |
| logicaldisk | Displays properties of all the logical disks on this computer. |
| class | Escapes from the default alias mode of WMIC to access classes in the WMI schema directly. |
| path | Escapes from the default alias mode of WMIC to access instances in the WMI schema directly. |
| context | Displays the current values of all global switches. |
| [quit | exit] | Exits the WMIC command shell. |

## Examples

To display the current values of all global switches, type:

```cmd
wmic context
```

Output similar to the following displays:

```output
NAMESPACE    : root\cimv2
ROLE         : root\cli
NODE(S)      : BOBENTERPRISE
IMPLEVEL     : IMPERSONATE
[AUTHORITY   : N/A]
AUTHLEVEL    : PKTPRIVACY
LOCALE       : ms_409
PRIVILEGES   : ENABLE
TRACE        : OFF
RECORD       : N/A
INTERACTIVE  : OFF
FAILFAST     : OFF
OUTPUT       : STDOUT
APPEND       : STDOUT
USER         : N/A
AGGREGATE    : ON
```

To display all properties of all logical disks on the computer, type:

```cmd
wmic logicaldisk
```

Output similar to the following displays:

```output
Access                    Description        InstallDate                   PowerManagementSupported   StatusInfo
Availability              DeviceID           LastErrorCode                 ProviderName               SupportsDiskQuotas
BlockSize                 DriveType          MaximumComponentLength        Purpose                    SupportsFileBasedCompression
Caption                   ErrorCleared       MediaType                     QuotasDisabled             SystemCreationClassName
Compressed                ErrorDescription   Name                          QuotasIncomplete           SystemName
ConfigManagerErrorCode    ErrorMethodology   NumberOfBlocks                QuotasRebuilding           VolumeDirty
ConfigManagerUserConfig   FileSystem         PNPDeviceID                   Size                       VolumeName
CreationClassName         FreeSpace          PowerManagementCapabilities   Status                     VolumeSerialNumber

0   C:   FALSE   Win32_LogicalDisk   Local Fixed Disk   C:   3   NTFS   543237451776   255   12   C:                                                                                                                                              1021771247616   FALSE   TRUE   Win32_ComputerSystem   <TheDeviceName>   <TheVolumeName>   0011AABB
```

To get the name of the logical disks, type:

```cmd
wmic logicaldisk get name
```

Output similar to the following displays:

```output
Name
C:
```

To change the language ID used by the command line to English (locale ID 409), type:

```cmd
wmic /locale:ms_409
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)