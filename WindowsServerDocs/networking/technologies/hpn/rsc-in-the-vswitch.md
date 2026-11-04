---
layout: Conceptual
title: Receive Segment Coalescing (RSC) in the vSwitch | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/hpn/rsc-in-the-vswitch
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Receive Segment Coalescing (RSC) in the vSwitch is a feature in Windows Server 2019 and Windows 10 October 2018 Update that helps reduce host CPU utilization and increases throughput for virtual workloads by coalescing multiple TCP segments into fewer, but larger segments. Processing fewer, large segments (coalesced) is more efficient than processing numerous, small segments.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-25T00:00:00.0000000Z
locale: en-us
document_id: 87eae592-d83e-2e46-aec8-cbd78a915ce6
document_version_independent_id: ff2cdd1e-5d03-e86a-28ed-466bf9ada325
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/hpn/rsc-in-the-vswitch.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/hpn/rsc-in-the-vswitch
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/hpn/rsc-in-the-vswitch.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 9f84d665-2c7a-dffc-9451-2873f2b73d96
---

# Receive Segment Coalescing (RSC) in the vSwitch | Microsoft Learn

Receive Segment Coalescing (RSC) in the vSwitch is a feature in Windows Server 2019 and Windows 10 October 2018 Update that helps reduce host CPU utilization and increases throughput for virtual workloads by coalescing multiple TCP segments into fewer, but larger segments. Processing fewer, large segments (coalesced) is more efficient than processing numerous, small segments. To learn more, see [Host network requirements for Azure Local](/en-us/azure/azure-local/concepts/host-network-requirements?context=/windows-server/context/windows-server-edge-networking).

Windows Server 2012 and later included a hardware-only offload version (implemented in the physical network adapter) of the technology also known as Receive Segment Coalescing. This offloaded version of RSC is still available in later versions of Windows. However, it is incompatible with virtual workloads and was disabled once a physical network adapter is attached to a vSwitch. For more information on the hardware-only version of RSC, see [Receive Segment Coalescing (RSC)](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh997024%28v=ws.11%29).

## Scenarios that benefit from RSC in the vSwitch

Workloads whose datapath traverses a virtual switch benefits from this feature.

For example:

- Host Virtual NICs including:

    - Software Defined Networking
    - Hyper-V Host
    - Storage Spaces Direct
- Hyper-V Guest Virtual NICs
- Software Defined Networking GRE Gateways
- Container

Workloads that are not compatible with this feature include:

- Software Defined Networking IPSEC Gateways
- SR-IOV enabled virtual NICs
- SMB Direct

## Configure RSC in the vSwitch

By default, on external vSwitches, RSC is enabled.

**View the current settings:**

```PowerShell
Get-VMSwitch -Name vSwitchName | Select-Object *RSC*
```

**Enable or Disable RSC in the vSwitch**

Important

Important: RSC in the vSwitch can be enabled and disabled on the fly without impact to existing connections.

**Disable RSC in the vSwitch**

```PowerShell
Set-VMSwitch -Name vSwitchName -EnableSoftwareRsc $false
```

**Re-enable RSC in the vSwitch**

```PowerShell
Set-VMSwitch -Name vSwitchName -EnableSoftwareRsc $True
```

For more information, see [Set-VMSwitch](/en-us/powershell/module/hyper-v/set-vmswitch).