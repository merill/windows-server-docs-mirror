---
layout: Conceptual
title: Use GPUs with Discrete Device Assignment in clustered VMs on Windows Server and Azure Local | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/deploy/use-gpu-with-clustered-vm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Learn how to use GPUs with clustered virtual machines (VMs) to provide GPU acceleration to workloads in the clustered VMs on Windows Server and Azure Local.
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2026-01-30T00:00:00.0000000Z
zone_pivot_groups: windows-os
locale: en-us
document_id: c0aedbe1-32e8-bd5e-377a-d19fc5e7c963
document_version_independent_id: c0aedbe1-32e8-bd5e-377a-d19fc5e7c963
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/deploy/use-gpu-with-clustered-vm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/deploy/use-gpu-with-clustered-vm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/deploy/use-gpu-with-clustered-vm.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/289b8734-3abd-4162-bc19-e661c3f4c940
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a94795e-9024-410d-b38e-b67941440893
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9ec3a4ca-f635-d44a-0ecc-5daa247d6e53
---

# Use GPUs with Discrete Device Assignment in clustered VMs on Windows Server and Azure Local | Microsoft Learn

You can include graphics processing units (GPUs) in your clusters to provide GPU acceleration to workloads running in clustered VMs. GPU acceleration can be provided via Discrete Device Assignment (DDA), which allows you to dedicate one or more physical GPUs to a VM, or through GPU Partitioning. Clustered VMs can take advantage of GPU acceleration, and clustering capabilities such as high availability via failover.

In this article, you'll learn how to use GPUs with clustered VMs to provide GPU acceleration to workloads using Discrete Device Assignment. This article guides you through preparing the cluster, assigning a GPU to a cluster VM, and failing over that VM using Windows Admin Center and PowerShell.

Tip

Live migration of virtual machines (VMs) using GPUs provided by DDA isn't currently supported, but VMs can be automatically restarted and placed where GPU resources are available if there's a failure. Looking to use Live Migration in clustered VMs? Consider using GPU partitioning. GPU partitioning allows you to share a fraction of the GPU instead of the entire GPU. To learn more about when to use GPU partition and support for live migration, see [Partition and assign GPUs to a virtual machine](../partition-assign-vm-gpu).

## Prerequisites

There are several requirements and things to consider before you begin to use GPUs with clustered VMs:

::: zone pivot="azure-local"

- You need Azure Local 2311.2 and later.
- Review how to manage GPUs in Azure Local 2311.2 and later, see [Prepare GPUs for Azure Local](/en-us/azure/azure-local/manage/gpu-preparation).

::: zone-end

::: zone pivot="windows-server"

- You need a Windows Server Failover cluster running Windows Server 2025 or later.
- Windows Server 2025 Datacenter edition is required for using DDA with GPU Pools in clustered VMs.

::: zone-end

- You must have a familiarity with Failover clustering and Hyper-V.
- You must install the same make and model of the GPUs across all the servers in your cluster.
- Review and follow the instructions from your GPU manufacturer to install the necessary drivers and software on each server in the cluster.
- Depending on your hardware vendor, you might also need to configure any GPU licensing requirements.
- You need a machine with Windows Admin Center installed. This machine could be one of your cluster nodes.

::: zone pivot="windows-server"

- Create a VM to assign the GPU to. Prepare that VM for DDA by setting its cache behavior, stop action, and memory-mapped I/O (MMIO) properties according to the instructions in [Deploy graphics devices using Discrete Device Assignment](/en-us/windows-server/virtualization/hyper-v/deploy/deploying-graphics-devices-using-dda).
- Prepare the GPUs in each server by installing security mitigation drivers on each server, disabling the GPUs, and dismounting them from the host. To learn more about this process, see [Deploy graphics devices by using Discrete Device Assignment](deploying-graphics-devices-using-dda).

::: zone-end

::: zone pivot="azure-local"

- Follow the steps in [Plan for deploying devices by using Discrete Device Assignment](/en-us/windows-server/virtualization/hyper-v/plan/plan-for-deploying-devices-using-discrete-device-assignment?context=/azure-stack/context/hci-context) to prepare GPU devices in the cluster.
- Make sure your device has enough MMIO space allocated within the VM. For more information, see [MMIO Space](/en-us/windows-server/virtualization/hyper-v/plan/plan-for-deploying-devices-using-discrete-device-assignment?context=/azure-stack/context/hci-context#mmio-space).
- Create a VM to assign the GPU to. Prepare that VM for DDA by setting its cache behavior, stop action, and memory-mapped I/O (MMIO) properties according to the instructions in [Deploy graphics devices using Discrete Device Assignment](/en-us/windows-server/virtualization/hyper-v/deploy/deploying-graphics-devices-using-dda?pivots=azure-stack-hci&amp;context=/windows-server/context/windows-server-virtualization).
- Prepare the GPUs in each server by installing security mitigation drivers on each server, disabling the GPUs, and dismounting them from the host. To learn more about this process, see [Deploy graphics devices by using Discrete Device Assignment](deploying-graphics-devices-using-dda?pivots=azure-stack-hci&amp;context=/azure-stack/context/hci-context).

Note

Your system must be supported Azure Local solution with GPU support. To browse options, visit the [Azure Local Catalog](https://azurestackhcisolutions.azure.microsoft.com/#/catalog?gpuSupport=GPU_P&amp;gpuSupport=DDA).

::: zone-end

## Prepare the cluster

When the prerequisites are complete, you can prepare the cluster to use GPUs with clustered VMs.

Preparing the cluster involves creating a resource pool that contains the GPUs that are available for assignment to VMs. The cluster uses this pool to determine VM placement for any started or moved VMs that are assigned to the GPU resource pool.

# [Windows Admin Center](#tab/windows-admin-center)
Using Windows Admin Center, follow these steps to prepare the cluster to use GPUs with clustered VMs.

To prepare the cluster and assign a VM to a GPU resource pool:

1. Launch Windows Admin Center and make sure the **GPUs** extension is already installed.
2. Select **Cluster Manager** from the top dropdown menu and connect to your cluster.
3. From the **Settings** menu, select **Extensions** &gt; **GPUs**.
4. On the **Tools** menu, under **Extensions**, select **GPUs** to open the tool.

    [![Screenshot of the GPU tool in Windows Admin Center.](media/use-gpu-with-clustered-vm/gpu-extension.png)](media/use-gpu-with-clustered-vm/gpu-extension.png#lightbox)
5. On tool's main page, select the **GPU pools** tab, and then select **Create GPU pool**.

    [![Screenshot of the Create GPU pools page in Windows Admin Center.](media/use-gpu-with-clustered-vm/create-gpu-pool.png)](media/use-gpu-with-clustered-vm/create-gpu-pool.png#lightbox)
6. On the **New GPU pool** page, specify the following and then select **Save**:

    1. **Server** name
    2. **GPU pool** name
    3. **GPUs** that you want to add to the pool

    [![Screenshot of the New GPU pool page in Windows Admin Center to specify servers, pool name, and GPUs.](media/use-gpu-with-clustered-vm/new-gpu-pool.png)](media/use-gpu-with-clustered-vm/new-gpu-pool.png#lightbox)

    After the process completes, you'll receive a success prompt that shows the name of the new GPU pool and the host server.

# [PowerShell](#tab/powershell)
Follow these steps to prepare the cluster to use GPUs with clustered VMs using PowerShell.

1. Create a new empty resource pool on each server containing the clustered GPU resources. Make sure to provide the same pool name on each server.

    In PowerShell, run the following cmdlet as an administrator:

    ```PowerShell
     New-VMResourcePool -ResourcePoolType PciExpress -Name "GpuChildPool"
    ```
2. Add the dismounted GPUs from each server to the resource pool that you created in the previous step.

    In PowerShell, run the following commands:

    ```PowerShell
     $gpu = Get-VMHostAssignableDevice
    
     Add-VMHostAssignableDevice -HostAssignableDevice $gpu -ResourcePoolName "GpuChildPool"
    ```

You now have a cluster-wide resource pool (named `GpuChildPool`) that is populated with assignable GPUs. The cluster uses this pool to determine VM placement for any started or moved VMs that are assigned to the GPU resource pool.

---

## Assign a VM to a GPU resource pool

You can now assign a VM to a GPU resource pool. You can assign one or more VMs to a clustered GPU resource pool, and remove a VM from a clustered GPU resource pool.

# [Windows Admin Center](#tab/windows-admin-center)
Follow these steps to assign an existing VM to a GPU resource pool using Windows Admin Center.

Note

You also need to install drivers from your GPU manufacturer inside the VM so that apps in the VM can take advantage of the GPU assigned to them.

1. On the **Assign VM to GPU pool** page, specify the following, then select **Assign**:

    1. **Server** name
    2. **GPU pool** name
    3. **Virtual machine** that you want to assign the GPU to from the GPU pool.

    You can also define advanced setting values for memory-mapped IO (MMIO) spaces to determine resource requirements for a single GPU.

    [![Screenshot of the Assign VM to GPU pool page in Windows Admin Center where you assign a VM to a GPU from the GPU pool.](media/use-gpu-with-clustered-vm/assign-vm-to-gpu-pool.png)](media/use-gpu-with-clustered-vm/assign-vm-to-gpu-pool.png#lightbox)

    After the process completes, you'll receive a confirmation prompt that shows you successfully assigned the GPU from the GPU resource pool to the VM, which displays under **Assigned VMs**.

    [![Screenshot of success prompt showing GPU assigned to a VM and the VM displaying under Assigned VMs.](media/use-gpu-with-clustered-vm/gpu-assigned-to-vm-confirmed.png)](media/use-gpu-with-clustered-vm/gpu-assigned-to-vm-confirmed.png#lightbox)

To unassign a VM from a GPU resource pool:

1. On the **GPU pools** tab, select the GPU that you want to unassign, and then select **Unassign VM**.
2. On the **Unassign VM from GPU pool** page, in the **Virtual machines** list box, specify the name of the VM, and then select **Unassign**.

    [![Screenshot of Unassign VM from GPU pool page showing VM to be unassigned.](media/use-gpu-with-clustered-vm/unassign-vm-from-gpu-pool.png)](media/use-gpu-with-clustered-vm/unassign-vm-from-gpu-pool.png#lightbox)

    After the process completes, you receive a success prompt that the VM has been unassigned from the GPU pool, and under **Assignment status** the GPU shows **Available (Not assigned)**.

# [PowerShell](#tab/powershell)
Follow these steps to assign an existing VM to a GPU resource pool using PowerShell.

1. Configure the cluster VM resource’s default offline action as `force-shutdown` rather than `save`. Make sure to replace `<vmname>` with the name of the VM that you want to assign to the GPU resource pool.

    In PowerShell, run the following cmdlet:

    ```PowerShell
     Get-ClusterResource -name <vmname> | Set-ClusterParameter -Name "OfflineAction" -Value 3
    ```
2. Assign the resource pool that you created earlier to the VM. Assigning the resource pool declares to the cluster that the VM requires an assigned device from the `GpuChildPool` pool when it's started or moved.

    In PowerShell, run the following cmdlet:

    ```PowerShell
     Get-ClusterResource -name <vmname> | Add-VMAssignableDevice -ResourcePoolName "GpuChildPool"
    ```

    Note

    To add more than one GPU to the VM, first check that the resource pool contains multiple assignable GPUs. Then, run the previous command again for each GPU you want to add.

    You can also remove an assigned GPU from a VM. To do so, in PowerShell, run the following command. Make sure to replace `<vmname>` with the name of the VM that you want to assign to the GPU resource pool.

    ```PowerShell
     Add-VMAssignableDevice -VMName $vm -ResourcePoolName "GpuChildPool"
    
     $vm | Remove-VMAssignableDevice
    ```

---

When you start the VM, the cluster ensures that the VM is placed on a server with available GPU resources from this cluster-wide pool. The cluster also assigns the GPU to the VM through DDA, which allows the GPU to be accessed from workloads inside the VM.

## Fail over a VM with an assigned GPU

::: zone pivot="windows-server"

To test the cluster’s ability to fail over your GPU workload, perform a drain operation on the server where the VM is running with an assigned GPU. Performing a drain operation on the server causes the cluster to restart the VM on another server in the cluster, as long as another server has sufficient available resources in the pool that you created.

To drain the server, follow the instructions in [Failover cluster maintenance procedures](/en-us/azure/azure-local/manage/maintain-servers?context=/windows-server/context/windows-server-virtualization). The cluster restarts the VM on another server in the cluster, as long as another server has sufficient available GPU resources in the pool that you created.

::: zone-end

::: zone pivot="azure-local"

To test the cluster’s ability to fail over your GPU workload, perform a drain operation on the server where the VM is running with an assigned GPU. Performing a drain operation on the server causes the cluster to restart the VM on another server in the cluster, as long as another server has sufficient available resources in the pool that you created.

To drain the server, follow the instructions in [Failover cluster maintenance procedures](/en-us/azure/azure-local/manage/maintain-servers?context=/windows-server/context/windows-server-failover-clustering). The cluster restarts the VM on another server in the cluster, as long as another server has sufficient available GPU resources in the pool that you created.

::: zone-end