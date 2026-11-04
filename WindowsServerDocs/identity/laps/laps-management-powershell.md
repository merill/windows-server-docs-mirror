---
layout: Conceptual
title: Windows LAPS PowerShell Cmdlets Overview | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/laps/laps-management-powershell
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Explore Windows LAPS PowerShell cmdlets to manage passwords securely. Learn key features, benefits, and usage.
author: jay98014
ms.author: roharwoo
ms.date: 2025-05-06T00:00:00.0000000Z
ms.topic: concept-article
ai-usage: ai-assisted
locale: en-us
document_id: 912c3ec9-2d4b-049d-1d87-135859658346
document_version_independent_id: 912c3ec9-2d4b-049d-1d87-135859658346
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/laps/laps-management-powershell.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/laps/laps-management-powershell
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/laps/laps-management-powershell.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: a8196930-4fbc-cd5c-6671-5ba16424c204
---

# Windows LAPS PowerShell Cmdlets Overview | Microsoft Learn

Windows Local Administrator Password Solution (Windows LAPS) includes the LAPS PowerShell module. Learn about its cmdlets, features, and how they compare to legacy Microsoft LAPS cmdlets to help you manage passwords securely.

## Cmdlet descriptions and usage

The following table describes the cmdlets that are available in the LAPS PowerShell module:

| Name | Description |
| --- | --- |
| [`Get-LapsAADPassword`](/en-us/powershell/module/laps/get-lapsaadpassword) | Query Microsoft Entra ID for Windows LAPS passwords. |
| [`Get-LapsDiagnostics`](/en-us/powershell/module/laps/get-lapsdiagnostics) | Collect diagnostic information for investigating issues. |
| [`Find-LapsADExtendedRights`](/en-us/powershell/module/laps/find-lapsadextendedrights) | Discover which identities have been granted permissions for an Organizational Unit (OU) in Windows Server Active Directory. |
| [`Get-LapsADPassword`](/en-us/powershell/module/laps/get-lapsadpassword) | Query Windows Server Active Directory for Windows LAPS passwords. |
| [`Invoke-LapsPolicyProcessing`](/en-us/powershell/module/laps/invoke-lapspolicyprocessing) | Initiate a policy processing cycle. |
| [`Reset-LapsPassword`](/en-us/powershell/module/laps/reset-lapspassword) | Initiate an immediate password rotation. Use when backing up the password to either Microsoft Entra ID or Windows Server Active Directory. |
| [`Set-LapsADAuditing`](/en-us/powershell/module/laps/set-lapsadauditing) | Configure Windows LAPS-related auditing on OUs in Windows Server Active Directory. |
| [`Set-LapsADComputerSelfPermission`](/en-us/powershell/module/laps/set-lapsadcomputerselfpermission) | Configure an OU in Windows Server Active Directory to allow computer objects to update their Windows LAPS passwords. |
| [`Set-LapsADPasswordExpirationTime`](/en-us/powershell/module/laps/set-lapsadpasswordexpirationtime) | Update a computer's Windows LAPS password expiration time in Windows Server Active Directory. |
| [`Set-LapsADReadPasswordPermission`](/en-us/powershell/module/laps/set-lapsadreadpasswordpermission) | Grant permission to read the Windows LAPS password information in Windows Server Active Directory. |
| [`Set-LapsADResetPasswordPermission`](/en-us/powershell/module/laps/set-lapsadresetpasswordpermission) | Grant permission to update the Windows LAPS password expiration time in Windows Server Active Directory. |
| [`Update-LapsADSchema`](/en-us/powershell/module/laps/update-lapsadschema) | Extend the Windows Server Active Directory schema with the Windows LAPS schema attributes. |

Tip

- The `Invoke-LapsPolicyProcessing` and `Reset-LapsPassword` cmdlets aren't affected by whether the password currently is backed up to Microsoft Entra ID or Windows Server Active Directory. In this scenario, both options are supported.
- All cmdlets in the Windows LAPS PowerShell module support detailed logging when you use the `-Verbose` parameter.

For more detailed information on each cmdlet, see [LAPS PowerShell Module](/en-us/powershell/module/laps/).

## Comparing Windows LAPS and legacy Microsoft LAPS PowerShell

Legacy Microsoft LAPS includes a PowerShell module named `AdmPwd.PS`. The two modules have many functional similarities, but they also have many differences. This table provides a mapping between the two modules:

| Windows LAPS cmdlet | Legacy Microsoft LAPS cmdlet |
| --- | --- |
| `Get-LapsAADPassword` | Not applicable |
| `Get-LapsDiagnostics` | Not applicable |
| `Find-LapsADExtendedRights` | `Find-AdmPwdExtendedRights` |
| `Get-LapsADPassword` | `Get-AdmPwdPassword` |
| `Invoke-LapsPolicyProcessing` | Not applicable |
| `Reset-LapsPassword` | Not applicable |
| `Set-LapsADAuditing` | `Set-AdmPwdAuditing` |
| `Set-LapsADComputerSelfPermission` | `Set-AdmPwdComputerSelfPermission` |
| `Set-LapsADPasswordExpirationTime` | `Reset-AdmPwdPassword` |
| `Set-LapsADReadPasswordPermission` | `Set-AdmPwdReadPasswordPermission` |
| `Set-LapsADResetPasswordPermission` | `Set-AdmPwdResetPasswordPermission` |
| `Update-LapsADSchema` | `Update-AdmPwdADSchema` |

In addition to naming-related changes, the Windows LAPS PowerShell cmdlets for Windows Server Active Directory operate over an entirely different set of schema extensions. For more information, see [Windows LAPS schema extensions reference](laps-technical-reference#schema-extensions).