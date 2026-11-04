---
layout: Conceptual
title: Prepare for Windows Local Administrator Password Solution (LAPS) Deployment and Migration | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/laps/laps-scenarios-migration
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Prepare to deploy and migrate Windows Local Administrator Password Solution (Windows LAPS) with recommended scenarios. Start your migration today.
ms.topic: how-to
author: jay98014
ms.author: roharwoo
ms.date: 2025-05-16T00:00:00.0000000Z
locale: en-us
document_id: b825600c-2528-6e0f-ef56-99dd88c98e2a
document_version_independent_id: b825600c-2528-6e0f-ef56-99dd88c98e2a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/laps/laps-scenarios-migration.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/laps/laps-scenarios-migration
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/laps/laps-scenarios-migration.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: be97d22e-0ea1-0d24-2b34-15e1b0aa856c
---

# Prepare for Windows Local Administrator Password Solution (LAPS) Deployment and Migration | Microsoft Learn

Windows Local Administrator Password Solution (Windows LAPS) helps you securely manage local administrator passwords on Windows devices using Microsoft Entra ID or Active Directory. This article explains how to migrate from legacy Microsoft LAPS to Windows LAPS for improved security and management.

It's possible to use both Windows LAPS and legacy LAPS in a side-by-side scenario. For the side-by-side scenario to be successful, both policies must target different local accounts. Your long term goal however should be to migrate away from legacy LAPS to Windows LAPS.

## Prerequisites

Before you begin the migration process, ensure that you configured Windows LAPS. For more information, see [Get started with Windows LAPS and Microsoft Entra ID](laps-scenarios-azure-active-directory) or [Get started with Windows LAPS and Windows Server Active Directory](laps-scenarios-windows-server-active-directory).

## Migration scenarios from legacy LAPS to Windows LAPS on existing devices

Microsoft recommends migrating from legacy LAPS to Windows LAPS. This section describes procedures for accomplishing that migration on existing devices.

There are two basic approaches that can be used. The first approach is an immediate transition, while the second approach uses a period of side-by-side coexistence followed by a final transition.

### Immediate transition approach

You can migrate from legacy LAPS to Windows LAPS on existing devices using the following process:

1. Disable or remove the legacy LAPS policy.
2. Create and apply a Windows LAPS policy.
3. Monitor the managed device to confirm a successful transition.
4. Remove the legacy LAPS software.

The first two steps should be performed simultaneously (or as nearly so as possible).

The easiest approach when configuring the Windows LAPS policy is to target the same account that was previously targeted in the legacy LAPS policy. If you choose to target a different account, then you need to create the new account before you apply the Windows LAPS policy. The first account should be removed if it's no longer needed.

The Windows LAPS policy might also be configured with features, such as being backed up to Microsoft Entra ID, or enable Active Directory password encryption, that weren't available with legacy LAPS.

When a Windows LAPS policy is first applied, the managed device performs an immediate rotation of the local account password. For more information, see [How a Windows LAPS policy is applied to a new client device](laps-concepts-overview#how-a-windows-laps-policy-is-applied-to-a-new-client-device). You should [monitor](laps-scenarios-migration#monitor-a-successful-transition) the managed device to ensure the transition is successful.

Once the transition is complete, the final step should be to remove the legacy LAPS software from the managed device.

### Transient side-by-side coexistence approach

You might want to implement a more gradual migration procedure from legacy LAPS to Windows LAPS. The high-level steps to perform this transition on existing devices are as follows:

1. Configure the managed device with a second local account.
2. Create and apply a Windows LAPS policy.
3. Monitor the managed device to confirm a successful application of the Windows LAPS policy.
4. Disable or remove the legacy LAPS policy.
5. Remove the legacy LAPS software.
6. Remove the extra account.

With this approach, you need to create a second local account since having both a Windows LAPS policy and legacy LAPS policy targeting the same account isn't supported.

After confirming that Windows LAPS is working properly, you can leave the managed device in this state for as long as needed before performing the rest of the migration steps.

## Monitor a successful transition

There are multiple approaches to monitoring for a successful outcome once you transition a managed device to a Windows LAPS policy:

- You can monitor the managed device's [Windows LAPS event log channel](laps-management-event-log) for successful password update events (for either Microsoft Entra ID or AD). A centralized event log collection solution can help here.
- When storing passwords in Active Directory, you can look for the appearance of a new or updated `msLAPS-PasswordExpirationTime` attribute on the managed device's AD computer object. The [`Get-LapsADPassword`](/en-us/powershell/module/laps/get-lapsadpassword) PowerShell cmdlet can be used to automate this analysis.
- When storing passwords in Microsoft Entra ID, you can check the Microsoft Entra ID or Intune management portals to verify that the device password is updated. The [`Get-LapsAADPassword`](/en-us/powershell/module/laps/get-lapsaadpassword) PowerShell cmdlet can be used to automate this analysis.

## Remove the legacy LAPS software from a managed device

The specific steps required to remove the legacy LAPS software from the managed device depend on how that software was initially installed.

- If you installed legacy LAPS using the MSI installer package, you can manually uninstall the legacy LAPS software from add/remove programs, or run the following command from the command line running as an administrator on the device:

    ```cmd
    msiexec.exe /q /uninstall {97E2CA7B-B657-4FF7-A6DB-30ECC73E1E28}
    ```
- If you installed legacy LAPS by manually copying and registering the legacy LAPS CSE `AdmPwd.dll` file, you need to manually unregister and then delete `AdmPwd.dll`. Run the following command from the command line running as an administrator on the device. If you copied `AdmPwd.dll` to a different location, you need to adjust the path accordingly. You can find the location of the file by checking the registry key `HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\GPExtensions\{D76B9641-3288-4f75-942D-087DE603E3EA}` for the `DllName` value.

    ```cmd
    regsvr32.exe /s /u AdmPwd.dll
    delete C:\windows\system32\AdmPwd.dll
    ```