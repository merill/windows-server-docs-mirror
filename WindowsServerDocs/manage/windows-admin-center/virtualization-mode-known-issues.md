---
layout: Conceptual
title: Known issues for Windows Admin Center Virtualization Mode (preview) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/virtualization-mode-known-issues
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Track current known issues, limitations, causes, and workarounds for Windows Admin Center Virtualization Mode during preview.
author: robinharwood
ms.author: roharwoo
ms.topic: troubleshooting-known-issue
ms.date: 2025-11-17T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: d622e73d-0a2c-2813-716a-0e5931974477
document_version_independent_id: d622e73d-0a2c-2813-716a-0e5931974477
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/virtualization-mode-known-issues.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/virtualization-mode-known-issues
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/virtualization-mode-known-issues.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 7f549dd3-71f9-676e-9a95-08e2e9676c06
---

# Known issues for Windows Admin Center Virtualization Mode (preview) | Microsoft Learn

Important

Windows Admin Center Virtualization Mode is currently in PREVIEW. This information relates to a prerelease product that may be substantially modified before it's released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

This article lists current known issues and limitations for Windows Admin Center Virtualization Mode while it's in PREVIEW. It helps you identify symptoms, understand causes, and apply workarounds when resource onboarding or VM management behaves unexpectedly.

If you encounter issues not listed here, submit feedback from the portal or on a related docs page. This list will expand as new issues are validated.

| Issue | Description | Resolution summary |
| --- | --- | --- |
| Network ATC intent failure reports success | If a Network ATC intent fails to be created within the add resource workflow, the workflow might still succeed. | Verify adapters, VLAN, and QoS settings; review events; redeploy intent; ensure LLDP; re-add only after prerequisites |
| Pending reboot after feature install | If the Windows Server feature installation requires a reboot, Windows Admin Center doesn't handle the reboot during the add resource process. The add resource workflow succeeds even if a reboot is still required for the features to take effect. To continue, reboot the resources. | Detect pending reboot; restart hosts; verify feature state; retry incomplete intent steps |
| Cluster onboarding fails repeatedly | If the resource onboarding workflow fails for a cluster, you might need to install the required Windows Server features on every cluster node, reboot the nodes, and then try onboarding the cluster again. | Align feature installs; reboot nodes; verify health; retry onboarding |

## Resource onboarding reports success when a Network ATC intent fails

If a Network ATC network intent fails to be created within the add resource workflow, the workflow might still succeed.

**Resolution steps:**

To check and recreate the Network ATC network intent, perform the following steps.

1. Sign in to the Hyper-V host where you created the intent.
2. Open Event Viewer and navigate to **Applications and Services Logs** &gt; **Microsoft** &gt; **Windows** &gt; **Networking-NetworkAtc** &gt; **Admin** to review provisioning events for failures or warnings.
3. Check the provisioning status on each node by running `Get-NetIntentStatus`.
4. Resolve any identified issues, then follow one of these options to recreate the intent:
5. Re-create or redeploy the intent if required:

    - Rerun the Add resources workflow and create the intent again using the Networking tab in the Add Host workflow. For more information about the steps to add resources, see [Add resources in Windows Admin Center Virtualization Mode](add-virtualization-mode-resources).

    Or

    - To manually recreate the intent:

        1. Create a new intent using the PowerShell cmdlet `Add-NetIntent`. For more information about creating network intents, see [Deploy host networking with Network ATC](../../networking/network-atc/network-atc).
        2. Rerun the Add resources workflow and check the intent you created appears in the Networking tab. For more information about the steps to add resources, see [Add resources in Windows Admin Center Virtualization Mode](add-virtualization-mode-resources).

## Required reboot after feature installation not handled automatically

If the Windows Server feature installation requires a reboot, Windows Admin Center doesn't handle the reboot during the add resource process. The add resource workflow succeeds even if a reboot is still required for the features to take effect. To continue, reboot the resources.

**Resolution steps:**

To detect and complete required reboots and activate installed features, perform the following steps on the Hyper-V host.

1. To check whether a pending reboot is required, open an elevated PowerShell session and run the following command:

    ```powershell
    if (Test-Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Component Based Servicing\RebootPending') {
       Write-Host 'Pending reboot detected. Reboot before continuing.' -ForegroundColor Yellow
    } else {
       Write-Host 'No pending reboot detected.' -ForegroundColor Green
    }
    ```
2. Reboot the affected host or hosts.
3. After the restart, re-verify the installed features and re-run the Add resources. For more information about the steps to add resources, see [Add resources in Windows Admin Center Virtualization Mode](add-virtualization-mode-resources).

## Cluster resource onboarding fails repeatedly

If the resource onboarding workflow fails for a cluster, you might need to install the required Windows Server features on every cluster node, reboot the nodes, and then try to onboard the cluster again.

**Resolution steps:**

To align prerequisites across cluster nodes and retry resource onboarding, perform the following steps. Sign in to each cluster node to complete these steps.

1. Run PowerShell as an administrator on each node.
2. Validate the feature state with a single command:

    ```powershell
    $params = @{
       Name = @('Hyper-V','Failover-Clustering','Data-Center-Bridging','Network-ATC')
    }
    
    Get-WindowsFeature @params | Select-Object -Property Name, InstallState
    ```
3. Install any missing features by running the following commands:

    ```powershell
    Install-WindowsFeature Hyper-V -IncludeManagementTools
    Install-WindowsFeature Failover-Clustering
    Install-WindowsFeature Data-Center-Bridging
    Install-WindowsFeature Network-ATC
    ```

    To learn more about configuring these features, see:

    - Network ATC. For deployment guidance, see [Deploy host networking with Network ATC](../../networking/network-atc/network-atc).
    - Data Center Bridging. Included in the Network ATC guidance.
    - Hyper-V. For deployment guidance, see [Install Hyper-V](../../virtualization/hyper-v/get-started/install-hyper-v).
    - Failover Clustering. For more information about creating a cluster, see [Create a failover cluster](../../failover-clustering/create-failover-cluster).
4. Verify that all nodes are domain joined and that time synchronization is functioning correctly.
5. Validate cluster health with `Get-Cluster` and remediate any issues.
6. Re-run the resource onboarding workflow. To learn more about the steps to add resources, see [Add resources in Windows Admin Center Virtualization Mode](add-virtualization-mode-resources).

## Related information

- [Add resources in Windows Admin Center Virtualization Mode](add-virtualization-mode-resources)
- [Virtualization Mode overview](virtualization-mode-overview)
- [Manage virtual machines in Virtualization Mode](manage-virtualization-mode-virtual-machines)