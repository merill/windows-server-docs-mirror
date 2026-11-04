---
layout: Conceptual
title: CA Backup and Restore Windows PowerShell cmdlets | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/component-updates/ca-backup-and-restore-windows-powershell-cmdlets
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: CA Backup and Restore Windows PowerShell cmdlets'
author: robinharwood
ms.author: roharwoo
ms.date: 2023-05-16T00:00:00.0000000Z
ms.topic: how-to
ms.custom:
- inhenkel
- sfi-image-nochange
locale: en-us
document_id: 7a200a93-59b1-9db1-ed61-8441dd7bb8f1
document_version_independent_id: f3edf34c-5a58-6c4d-e037-51384f7bf7fb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/component-updates/CA-Backup-and-Restore-Windows-PowerShell-cmdlets.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/component-updates/ca-backup-and-restore-windows-powershell-cmdlets
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/component-updates/CA-Backup-and-Restore-Windows-PowerShell-cmdlets.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9e2a3275-f495-3e8b-52e6-0069fb4b7da3
---

# CA Backup and Restore Windows PowerShell cmdlets | Microsoft Learn

> 
> **Author**: Justin Turner, Senior Support Escalation Engineer with the Windows group

Note

This content is written by a Microsoft customer support engineer, and is intended for experienced administrators and systems architects who are looking for deeper technical explanations of features and solutions in Windows Server 2012 R2 than topics on TechNet usually provide. However, it has not undergone the same editing passes, so some of the language may seem less polished than what is typically found on TechNet.

## Overview

The ADCSAdministration Windows PowerShell module was introduced in Window Server 2012. Two new cmdlets were added to this module in Window Server 2012 R2 to support the Backup and Restore of a CA.

- Backup-CARoleService
- Restore-CARoleService

## Backup-CARoleService

**ADCSAdministration Cmdlet: Backup-CARoleService**

| Arguments -**Bold**arguments are required | Description |
| --- | --- |
| **-Path** | - String - location to save the backup- This is the only unnamed parameter- positional parameter<br>**Example:**<br><br>Backup-CARoleService.-Path c:\adcsbackup1<br><br>Backup-CARoleService c:\adcsbackup2 |
| -KeyOnly | - Backup the CA certificate without the database<br>**Example:**<br><br>Backup-CARoleService c:\adcsbackup3 -KeyOnly |
| -Password | - Specifies the password to protect CA certificates and private keys- Must be a secure string- Not valid with the -DatabaseOnly parameter<br>Example:<br><br>Backup-CARoleService c:\adcsbackup4 -Password (Read-Host -prompt "Password:" -AsSecureString)<br><br>Backup-CARoleService c:\adcsbackup5 -Password (ConvertTo-SecureString "Pa55w0rd!" -AsPlainText -Force) |
| -DatabaseOnly | - Backup the database without the CA certificate<br>Backup-CARoleService c:\adcsbackup6 -DatabaseOnly |
| -Force | 1. Allows you to overwrite the backup that pre-exists in the location specified in the -Path parameter<br>Backup-CARoleService c:\adcsbackup1 -Force |
| -Incremental | - Perform an incremental backup<br>Backup-CARoleService c:\adcsbackup7 -Incremental |
| -KeepLog | 1. Instructs the command to keep log files. If the switch isn't specified, log files are truncated by default except in the Incremental scenario<br>Backup-CARoleService c:\adcsbackup7 -KeepLog |

### -Password &lt;Secure String&gt;

If the -Password parameter is used, the supplied password must be a secure string. Use the **Read-Host** cmdlet to launch an interactive prompt for secure password entry, or use the **ConvertTo-SecureString** cmdlet to specify the password in-line.

Review the following examples

**Specifying a secure string for the Password parameter using Read-Host**

```powershell
Backup-CARoleService c:\adcsbackup4 -Password (Read-Host -prompt "Password:" -AsSecureString)
```

**Specifying a secure string for the Password parameter using ConvertTo-SecureString**

```powershell
Backup-CARoleService c:\adcsbackup5 -Password (ConvertTo-SecureString "Pa55w0rd!" -AsPlainText -Force)
```

## Restore-CARoleService

**ADCSAdministration Cmdlet: Restore-CARoleService**

| Arguments -**Bold**arguments are required | Description |
| --- | --- |
| **-Path** | - String - location to restore backup from- This is the only unnamed parameter- positional parameter<br>**Example:**<br><br>Restore-CARoleService.-Path c:\adcsbackup1 -Force<br><br>Restore-CARoleService c:\adcsbackup2 -Force |
| -KeyOnly | - Restore the CA certificate without the database- Must be specified if the backup was taken with the -KeyOnly option<br>**Example:**<br><br>Restore-CARoleService c:\adcsbackup3 -KeyOnly -Force |
| -Password | - Specifies the password of the CA certificates and private keys- Must be a secure string<br>**Example:**<br><br>Restore-CARoleService c:\adcsbackup4 -Password (read-host -prompt "Password:" -AsSecureString) -Force<br><br>Restore-CARoleService c:\adcsbackup5 -Password (ConvertTo-SecureString "Pa55w0rd!" -AsPlainText -Force) -Force |
| -DatabaseOnly | - Restore the database without the CA certificate<br>Restore-CARoleService c:\adcsbackup6 -DatabaseOnly |
| -Force | - Allows you to overwrite the preexisting keys- Is an optional parameter but when restoring in-place, it is likely required<br>Restore-CARoleService c:\adcsbackup1 -Force |

### Issues

A nonpassword protected backup is taken if the ConvertTo-SecureString function fails while using the Backup-CARoleService with the -Password parameter.

![CA backup and restore](media/ca-backup-and-restore-windows-powershell-cmdlets/gtr_adds_backupcarole.gif)

### Common errors

| Action | Error | Comment |
| --- | --- | --- |
| **Restore-CARoleService C:\ADCSBackup** | Restore-CARoleService : The process can't access the file because it's being used by another process. (Exception from HRESULT:<br>0x80070020) | Stop the Active Directory Certificate Services service prior to running the Restore-CARoleService cmdlet |
| **Restore-CARoleService C:\ADCSBackup** | Restore-CARoleService : The directory isn't empty. (Exception from HRESULT: 0x80070091) | Use the -Force parameter to overwrite preexisting keys |
| **Backup-CARoleService C:\ADCSBackup -Password (Read-Host -Prompt "Password:" -AsSecureString) -DatabaseOnly** | Backup-CARoleService : Parameter set can't be resolved using the specified named parameters. | The -Password parameter is only used to password protect private keys and is therefore invalid when you aren't backing them up |
| **Restore-CARoleService C:\ADCSBack15 -Password (Read-Host -Prompt "Password:" -AsSecureString) -DatabaseOnly** | Restore-CARoleService : Parameter set can't be resolved using the specified named parameters. | The -Password parameter is only used to password protect private keys and is therefore invalid when you aren't restoring them |
| **Restore-CARoleService C:\ADCSBack14 -Password (Read-Host -Prompt "Password:" -AsSecureString)** | Restore-CARoleService : The system can't find the file specified. (Exception from HRESULT: 0x80070002) | The path specified doesn't contain a valid database backup. Perhaps the path is invalid or the backup was taken with the -KeysOnly option? |