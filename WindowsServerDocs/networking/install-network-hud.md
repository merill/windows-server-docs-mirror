---
layout: Conceptual
title: Install Network HUD on Windows Server clusters | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/install-network-hud
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Install Network HUD on Azure Arc-enabled Windows Server 2025 Datacenter cluster nodes, verify initialization, and view active health faults.
author: robinharwood
ms.author: roharwoo
ms.reviewer: baselkablawi
ms.date: 2026-11-17T00:00:00.0000000Z
ms.topic: install-set-up-deploy
ai-usage: ai-assisted
locale: en-us
document_id: 87372270-53da-8100-c8d5-7eed3092876a
document_version_independent_id: 87372270-53da-8100-c8d5-7eed3092876a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/install-network-hud.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/install-network-hud
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/install-network-hud.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/beac614b-f66d-40ed-a947-3996de709333
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a23d1459-ff4f-4288-9c98-4f3aadd3dfc9
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/9da05372-4706-43ec-a899-f436adab380d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d5608e6c-9521-4a4c-8ca0-7a000d2f4bfd
platformId: 5f442511-d6b0-044f-7e8e-33a2a6b1f925
---

# Install Network HUD on Windows Server clusters | Microsoft Learn

Network HUD is a host networking diagnostics tool that identifies configuration and operational conditions in physical Windows Server clusters. It helps cluster administrators investigate network reliability issues by correlating host and physical network information that they otherwise need to gather separately.

In this article, you install Network HUD on each Azure Arc-enabled machine in a Windows Server 2025 Datacenter cluster, verify detection initialization, and view active cluster health faults.

## Prerequisites for installing Network HUD

- A failover cluster with at least two physical machines that meet the [Storage Spaces Direct hardware requirements](../storage/storage-spaces/storage-spaces-direct-hardware-requirements). Network HUD doesn't support installation on virtual machines.
- Windows Server 2025 Datacenter installed on each cluster node.
- Hyper-V role and management tools installed on each cluster node.
- Network ATC configured with host networking intents. For more information, see [Network ATC overview](/en-us/azure/azure-local/concepts/network-atc-overview?pivots=windows-server).
- Storage Spaces Direct enabled. For more information, see [Deploy Storage Spaces Direct on Windows Server](../storage/storage-spaces/deploy-storage-spaces-direct).
- Data Center Bridging and Link Layer Discovery Protocol (LLDP) tools installed on each cluster node.
- Each cluster node connected to Azure Arc and enrolled in Windows Server Management enabled by Azure Arc. For more information, see [Windows Server Management enabled by Azure Arc](/en-us/azure/azure-arc/servers/windows-server-management-overview). Network HUD doesn't support offline installation.
- Validated physical switches that meet the applicable **Network switches for Azure Local** and **Network switch requirements** in [Physical network requirements for Azure Local](/en-us/azure/azure-local/concepts/physical-network-requirements).
- Connected physical switch ports that advertise the LLDP information required for the cluster nodes' traffic roles. Network HUD uses these advertisements for physical-network checks.
- The Azure Connected Machine Resource Administrator role, Contributor role, or a custom role with equivalent permissions on each Azure Arc-enabled server resource.
- Administrative access to the cluster nodes for local PowerShell checks.
- Access to a Windows Admin Center instance that can manage the cluster for the Windows Admin Center procedure.

## Install Network HUD on each cluster node

The Azure Arc extension installs the Network HUD service and PowerShell module. It doesn't configure the prerequisites.

1. In the [Azure portal](https://portal.azure.com), search for and select **Machines - Azure Arc**.
2. Select a cluster node.
3. On the node's **Overview** page, under **Capabilities**, select the **Network HUD** tile.

    [![Screenshot of an Azure Arc-enabled server Overview page in the Azure portal, with Capabilities selected and Network HUD marked Not Configured.](media/install-network-hud/network-hud-azure-arc.png)](media/install-network-hud/network-hud-azure-arc.png#lightbox)
4. Select **Enable**.
5. Wait until the Azure Arc extension operation succeeds and the **Network HUD** tile reports **Enabled**.
6. Repeat these steps for every cluster node. Install the extension on each Azure Arc-enabled machine, rather than once per cluster.

## Verify Network HUD extension deployment

In the Azure portal, verify the extension deployment on every cluster node.

1. Open each node's Azure Arc resource.
2. Under **Settings**, select **Extensions**, and then inspect the Network HUD extension deployment status.
3. If a deployment failed, review its error details before retrying the deployment.

## Verify Network HUD initialization

Perform these checks locally on every cluster node.

1. Open PowerShell as an administrator.
2. Verify that the `NetworkHUD` service is running:

    ```powershell
    Get-Service -Name NetworkHUD
    ```
3. Verify that the Network HUD PowerShell module is available:

    ```powershell
    Get-Module -ListAvailable -Name Az.StackHCI.NetworkHUD
    ```
4. Use `Get-WinEvent` to query events 105, 106, and 111 in the `Microsoft-Windows-Networking-NetworkHUD/Operational` log since the current service start time:

    ```powershell
    $service = Get-CimInstance -ClassName Win32_Service -Filter "Name = 'NetworkHUD'"
    $serviceStartTime = (Get-Process -Id $service.ProcessId).StartTime
    
    Get-WinEvent -FilterHashtable @{
        LogName      = 'Microsoft-Windows-Networking-NetworkHUD/Operational'
        ProviderName = 'Microsoft-Windows-Networking-NetworkHUD'
        Id           = 105, 106, 111
        StartTime    = $serviceStartTime
    } -MaxEvents 20 |
        Select-Object TimeCreated, Id, LevelDisplayName, Message
    ```
5. Verify that the current service startup has event 105, which confirms initialization, and event 111, which confirms that Network HUD loaded scenarios. Event 106 reports an initialization failure.

A running service confirms only that the service started. It doesn't confirm that Network HUD detections initialized.

## View active Network HUD health faults

After you confirm initialization, view active health faults by using Windows Admin Center or PowerShell.

# [Windows Admin Center](#tab/windowsadmincenter)
1. Open Windows Admin Center and connect to your Windows Server 2025 Datacenter cluster.
2. In the cluster view, view alerts on the dashboard or select the notification bell icon.

    [![Windows Admin Center cluster dashboard displaying active alerts, including a Network HUD networking fault.](media/network-hud/windows-admin-center-alerts.png)](media/network-hud/windows-admin-center-alerts.png#lightbox)
3. Look for Network HUD alerts.
4. Select an alert to view its details and recommended actions.

    ![Windows Admin Center fault detail pane for a Network HUD alert showing fields and recommended remediation actions.](media/install-network-hud/windows-admin-center-alert-detail.png)

Network HUD clears an alert after it no longer detects the underlying condition.

Clearing an alert doesn't mean that Network HUD automatically repaired the underlying issue.

# [PowerShell](#tab/powershell)
1. Open PowerShell as an administrator on a cluster node.
2. Import the Failover Clusters module:

    ```powershell
    Import-Module FailoverClusters
    ```
3. Get active cluster health faults for Network HUD:

    ```powershell
    Get-HealthFault | Where-Object Reason -like '*HUD*'
    ```

Run the command once on any cluster node. An empty result means that the query returned no active Network HUD health faults. It doesn't confirm that Network HUD detections initialized.

---

## Troubleshoot Network HUD installation and initialization failures

Troubleshoot locally on the affected node.

1. If you can't enable Network HUD, review extension errors in the Azure portal and logs on the affected node.
2. Verify that the required Windows features are installed, Network ATC intents are configured, Storage Spaces Direct is enabled, the node is connected to Azure Arc, and Windows Server Management enabled by Azure Arc enrollment is active.
3. Import the Network HUD PowerShell module:

    ```powershell
    Import-Module Az.StackHCI.NetworkHUD
    ```
4. Review recent Network HUD Operational events for service initialization and scenario loading:

    ```powershell
    Get-NetHUDLog -OperationalLog
    ```
5. Review recent Network HUD Diagnostic events for scenario results:

    ```powershell
    Get-NetHUDLog -ContentLog
    ```

    Diagnostic event 102 reports scenario success, and event 103 reports scenario failure. These diagnostic events aren't cluster health faults.
6. If you can't import the `Az.StackHCI.NetworkHUD` module, investigate the extension deployment status and Azure Arc extension logs.
7. If the extension deployment failed, follow [Troubleshoot Azure Arc-enabled servers VM extension issues](/en-us/azure/azure-arc/servers/troubleshoot-vm-extensions).

Don't treat a running service, an empty health-fault query, or missing log output as evidence that initialization succeeded. Review Operational events 105, 106, and 111 to determine initialization status.