---
layout: Conceptual
title: Transfer Flexible Single Master Operations roles in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/manage-fsmo-roles
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn how to transfer FSMO roles in Active Directory Domain Services (AD DS) to optimize performance and simplify administration.
author: Orin-Thomas
ms.topic: how-to
ms.author: orthomas
contributor: orthomas
ms.date: 2024-07-01T00:00:00.0000000Z
locale: en-us
document_id: d6897e20-d537-81c8-035d-e8678f7130de
document_version_independent_id: d6897e20-d537-81c8-035d-e8678f7130de
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/manage-fsmo-roles.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/manage-fsmo-roles
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/manage-fsmo-roles.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 56efb8e3-773c-0b39-fa1b-9d508c6047f1
---

# Transfer Flexible Single Master Operations roles in Windows Server | Microsoft Learn

When you create a new domain, the Active Directory Domain Services Installation Wizard automatically assigns all the domain-level Flexible Single Master Operations (FSMO) to the first domain controller that is created in that domain. When you create a new forest, the wizard also assigns the two forest-level operations master roles to the first domain controller. After the domain is created and functioning, you might want to transfer various operations master roles to different domain controllers to optimize performance and simplify administration.

Consider moving the operations master role or roles when any of the following conditions exist:

- Inadequate service performance
- Failure of a domain controller that hosts an operations master role
- Decommissioning of a domain controller that hosts an operations master role
- Administrative configuration changes that affect operations master role placement

If an operations master role holder has failed or been decommissioned before you can transfer the role, you must seize and transfer the role to a healthy domain controller. If you can't fix the previous role holder, or if you seized the roles, remove the previous role holder from the domain and clean up its metadata. To learn more about metadata cleanup, see [Clean up Active Directory Domain Controller server metadata](../deploy/ad-ds-metadata-cleanup). If you plan to reuse the repaired computer as a domain control, we recommend you format and rebuild the computer instead of restoring the domain controller from a backup. Restored domain controllers would as be role holders again and cause a conflict.

## Prerequisites

Before you transfer an operations master role, you need to complete the following prerequisites.

- Review the article [Flexible Single Master Operations roles](understand-fsmo-roles) for other considerations before transferring an FSMO role.
- To transfer the Schema Master role, your account must be a member of the Schema Admins group and should also be a member of the Enterprise Admins group.
- To transfer the Domain Naming Master role, your account must be a member of the Enterprise Admins group.
- To transfer the PDC Emulator role, your account must be a member of the Domain Admins group.
- To transfer the RID Master role, your account must be a member of the Domain Admins group.
- To transfer the Infrastructure Master role, your account must be a member of the Domain Admins group.
- Your Active Directory domain is operational and free from replication errors. To learn more about replication errors, see [Diagnose Active Directory replication failures](/en-us/troubleshoot/windows-server/active-directory/diagnose-replication-failures).

## Find the current role holders

To determine which domain controller holds a specific operations master role, you can use the Active Directory Users and Computers snap-in or the PowerShell cmdlet `Get-ADDomainController`. To find the current role holders, run the following steps.

1. Sign on to a computer with the AD DS Remote Server Administration Tools (RSAT) installed.
2. Open a PowerShell window.
3. Run the following PowerShell commands to list the domain controllers and their operations master roles. The script lists the domain controllers in the domain and the operations master roles that they hold.

    ```powershell
    $domainControllers = Get-ADDomainController -Filter *
    foreach ($dc in $domainControllers) {
        Write-Output "Name: $($dc.Name)"
        Write-Output "OperationMasterRoles:"
        foreach ($role in $dc.OperationMasterRoles) {
            Write-Output "- $role"
        }
    }
    ```

## Transfer Schema master role

To transfer the Schema master role, follow these steps.

1. Run the following PowerShell command to transfer the Schema Master role to another domain controller. Replace `<TargetServer>` with the name of the domain controller that you want to transfer the role to.

    ```powershell
    Move-ADDirectoryServerOperationMasterRole -Identity <TargetServer> -OperationMasterRole SchemaMaster
    ```
2. When prompted, type **Yes** or Y to confirm the transfer.
3. To confirm that the Schema Master role has been transferred, run the following PowerShell command:

    ```powershell
    Get-ADDomainController -Identity <TargetServer> | Select-Object OperationMasterRoles
    ```

If the domain controller that currently holds the Schema Master role has failed, you can use the `Move-ADDirectoryServerOperationMasterRole` with the **Force** parameter to seize the role and move it to a functional domain controller.

## Transfer Domain Naming Master role

To transfer the Domain Naming Master role, run the following PowerShell command:

1. Run the following PowerShell command to transfer the Domain Naming Master role to another domain controller. Replace `<TargetServer>` with the name of the domain controller that you want to transfer the role to.

    ```powershell
    Move-ADDirectoryServerOperationMasterRole -Identity <TargetServer> -OperationMasterRole DomainNamingMaster
    ```
2. When prompted, type **Yes** or Y to confirm the transfer.
3. To confirm that the Domain Naming Master role has been transferred, run the following PowerShell command:

    ```powershell
    Get-ADDomainController -Identity <TargetServer> | Select-Object OperationMasterRoles
    ```

If the domain controller that currently holds the Domain Naming Master role has failed, you can use the `Move-ADDirectoryServerOperationMasterRole` with the **Force** parameter to seize the role and move it to a functional domain controller.

## Transfer PDC Emulator role

To transfer the PDC Emulator role, run the following PowerShell command:

1. Run the following PowerShell command to transfer the PDC Emulator role to another domain controller. Replace `<TargetServer>` with the name of the domain controller that you want to transfer the role to.

    ```powershell
    Move-ADDirectoryServerOperationMasterRole -Identity <TargetServer> -OperationMasterRole PDCEmulator
    ```
2. When prompted, type **Yes** or Y to confirm the transfer.
3. To confirm that the PDC Emulator role has been transferred, run the following PowerShell command:

    ```powershell
    Get-ADDomainController -Identity <TargetServer> | Select-Object OperationMasterRoles
    ```

If the domain controller that currently holds the PDC Emulator role has failed, you can use the `Move-ADDirectoryServerOperationMasterRole` with the **Force** parameter to seize the role and move it to a functional domain controller.

## Transfer RID Master role

To transfer the RID Master role, follow these steps.

1. Run the following PowerShell command to transfer the RID Master role to another domain controller. Replace `<TargetServer>` with the name of the domain controller that you want to transfer the role to.

    ```powershell
    Move-ADDirectoryServerOperationMasterRole -Identity <TargetServer> -OperationMasterRole RIDMaster
    ```
2. When prompted, type **Yes** or Y to confirm the transfer.
3. To confirm that the RID Master role has been transferred, run the following PowerShell command:

    ```powershell
    Get-ADDomainController -Identity <TargetServer> | Select-Object OperationMasterRoles
    ```

If the domain controller that currently holds the RID Master role has failed, you can use the `Move-ADDirectoryServerOperationMasterRole` with the **Force** parameter to seize the role and move it to a functional domain controller.

## Transfer Infrastructure Master role

To transfer the Infrastructure Master role, follow these steps.

1. Run the following PowerShell command to transfer the Infrastructure Master role to another domain controller. Replace `<TargetServer>` with the name of the domain controller that you want to transfer the role to.

    ```powershell
    Move-ADDirectoryServerOperationMasterRole -Identity <TargetServer> -OperationMasterRole InfrastructureMaster
    ```
2. When prompted, type **Yes** or Y to confirm the transfer.
3. To confirm that the Infrastructure Master role has been transferred, run the following PowerShell command:

    ```powershell
    Get-ADDomainController -Identity <TargetServer> | Select-Object OperationMasterRoles
    ```

If the domain controller that currently holds the Infrastructure Master role has failed, you can use the `Move-ADDirectoryServerOperationMasterRole` with the **Force** parameter to seize the role and move it to a functional domain controller.