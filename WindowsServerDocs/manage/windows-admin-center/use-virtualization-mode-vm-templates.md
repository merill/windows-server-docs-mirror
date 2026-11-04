---
layout: Conceptual
title: Use VM templates in Windows Admin Center Virtualization Mode (preview) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/use-virtualization-mode-vm-templates
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn how to convert VMs to templates, deploy new VMs from templates, and convert templates back to VMs in Windows Admin Center Virtualization Mode.
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2026-05-13T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 364f877c-584b-c7d0-98f7-a0772354ff29
document_version_independent_id: 364f877c-584b-c7d0-98f7-a0772354ff29
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/use-virtualization-mode-vm-templates.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/use-virtualization-mode-vm-templates
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/use-virtualization-mode-vm-templates.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 76196c06-9aa1-4195-d166-4e1b72588133
---

# Use VM templates in Windows Admin Center Virtualization Mode (preview) | Microsoft Learn

Virtual machine (VM) templates in Windows Admin Center Virtualization Mode let you save a configured VM as a reusable, read-only blueprint. Instead of manually creating each VM, you define a configuration once and deploy consistent VMs across your Hyper-V hosts.

This article walks you through converting a VM to a template, deploying new VMs from a template, and converting a template back to a regular VM.

Important

Windows Admin Center Virtualization Mode is currently in PREVIEW. This information relates to a prerelease product that may be substantially modified before it's released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Prerequisites

- Windows Admin Center Virtualization Mode installed and available. For more information, see [Install Windows Admin Center Virtualization Mode](install-virtualization-mode).
- At least one resource group that contains one or more Hyper-V hosts that you added by using the **Compute** profile. For more information, see [Add resources in Windows Admin Center Virtualization Mode](add-virtualization-mode-resources).
- An account with the *Gateway Administrator* role or equivalent permissions and local Administrator rights on each Hyper-V host.
- At least one existing VM on a managed Hyper-V host. The VM must be shut down before you can convert it to a template. For more information about creating VMs, see [Manage virtual machines in Windows Admin Center Virtualization Mode](manage-virtualization-mode-virtual-machines).

## Convert a VM to a template

When you convert a VM to a template, you make it read-only and a `{Template}{Read-only}` prefix is automatically added to its name in the resource pane. The original VM isn't available as a running VM after conversion.

Tip

Before you convert a VM to a template, run sysprep on the VM to generalize it. Sysprep removes machine-specific information and prepares the VM for deployment as a template. For more information about sysprep, see [Sysprep (Generalize) a Windows installation](/en-us/windows-hardware/manufacture/desktop/sysprep--generalize--a-windows-installation).

To convert a VM to a template, follow these steps:

1. Open the Windows Admin Center Virtualization Mode gateway site, and then sign in with an account that has the *Gateway Administrator* role or equivalent permissions.
2. In the resource pane, expand the resource group and host, and then locate the VM you want to convert.
3. Verify the VM is shut down. If the VM is running, power it off before continuing.
4. Select the ellipsis (**...**) next to the VM name or right-click the VM name, and then select **Convert to Template**.
5. A notification appears when conversion starts. To monitor progress, select the notification bell icon to open the **Workflow status** panel. The workflow validates VM eligibility, converts the VM, updates the database, and verifies template creation.
6. When the workflow completes, the VM appears in the resource pane with the `{Template}{Read-only}` prefix.

## Deploy a new VM from a template

When you deploy a VM from a template, you create a new VM based on the template's configuration. The template stays unchanged and is available for future deployments.

To deploy a new VM from a template, follow these steps:

1. In the **resource pane**, find the template you want to deploy. Templates display with the `{Template}{Read-only}` prefix.
2. Select the ellipsis (**...**) next to the template name or right-click the template, and then select **Deploy VM**.
3. In the **Deploy VM from template** panel, complete the following required fields:

    | Field | Description |
    | --- | --- |
    | **Virtual machine name** | Enter a name for the new VM. Use your organizational naming conventions. |
    | **Storage path** | Enter the storage path for the new VM files (for example, `C:\ProgramData\Microsoft\Windows\Hyper-V\Virtual Machines`). |
4. Select **Deploy** to start the deployment.
5. A notification confirms that the deployment starts. To monitor progress, select the notification bell icon to open the **Workflow status** panel. The workflow validates the template, exports it, imports a new VM, starts the VM, and restores the template.
6. When the workflow completes, the new VM appears in the resource pane under the host and starts automatically. Select the VM to view its properties, including state, generation, memory, and operating system details.

## Convert a template back to a VM

If you no longer need a template, you can convert it back to a regular VM. This action removes the read-only status and makes the VM editable again.

To convert a template back to a VM:

1. In the **resource pane**, locate the template you want to convert back. Templates display with the `{Template}{Read-only}` prefix.
2. Select the ellipsis (**...**) next to the template name, and then select **Convert to VM**.
3. In the **Convert to VM** confirmation dialog, review the template name, and then select **Convert** to confirm.
4. A notification confirms the conversion started. To monitor progress, select the notification bell icon to open the **Workflow status** panel.
5. When the workflow completes, the template is converted back to a regular VM and the `{Template}{Read-only}` prefix is removed from its name in the resource pane.