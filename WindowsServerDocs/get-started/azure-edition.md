---
layout: Conceptual
title: What is Azure Edition for Windows Server? | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/azure-edition
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: Discover Azure Edition features including hotpatch, SMB over QUIC, and annual product updates for Azure virtualization.
author: robinharwood
ms.author: roharwoo
ms.topic: overview
ms.date: 2025-08-13T00:00:00.0000000Z
ms.custom:
- ai-gen-docs-bap
- ai-gen-description
- ai-seo-date:08/13/2025
locale: en-us
document_id: b932b82a-fba0-d7b1-b572-49c7da4c8886
document_version_independent_id: b932b82a-fba0-d7b1-b572-49c7da4c8886
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/azure-edition.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/azure-edition
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/azure-edition.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: a4ff3217-46b9-147c-47a1-1df55bee41b5
---

# What is Azure Edition for Windows Server? | Microsoft Learn

Windows Server Datacenter: Azure Edition is an edition of Windows Server focused on innovation and virtualization optimized to run on Azure. Azure Edition features a Long-Term Servicing Channel (LTSC) and yearly product updates, with two major product updates in the first 3 years. Azure Edition also brings new functionality to Windows Server users faster than the Standard and Datacenter editions of Windows Server.

The annual Azure Edition updates are delivered using Windows Update, rather than a full OS upgrade. As part of this annual update cadence, the Azure Edition Insider preview program gives the opportunity to access early builds - leading to general availability. To get started with Azure Edition Insider preview, visit the [Azure Edition preview](https://aka.ms/createWSAEpreview) Azure Marketplace offer. Details regarding each preview is shared in release announcements posted to the [Windows Server Insiders](https://techcommunity.microsoft.com/t5/windows-server-insiders/bd-p/WindowsServerInsiders) space on Microsoft Tech Community.

## Key differences

The following table summarizes the key differences:

| Description | Windows Server Standard, Datacenter | Windows Server Datacenter: Azure Edition |
| --- | --- | --- |
| New releases | Typically 2-3 years | Typically 2-3 years |
| Product updates | With new release | Yearly, with two major updates in the first 3 years |
| Support | 5 years of mainstream support, plus 5 years of extended support | 5 years of mainstream support, plus 5 years of extended support |
| Servicing channels | Long-Term Servicing Channel | Long-Term Servicing Channel |
| Who can use it? | All customers through all channels | Software Assurance, [Windows Server subscription](/en-us/azure/azure-local/manage/vm-activate), and cloud customers only |
| Installation options | Server Core, Server with Desktop Experience, [Nano Server container image](/en-us/virtualization/windowscontainers/manage-containers/container-base-images) | Server Core and Server with Desktop Experience only. Windows Server containers aren't supported. |
| Operating system environments (OSE) | Physical or virtual | Virtual only |
| Associated virtualization rights | 2 virtual OSE for Standard, Unlimited virtual OSEs for Datacenter | None |

Capabilities vary by image, see Getting started with Windows Server Datacenter: Azure Edition for more detail.

Tip

For more information, see the [Microsoft Software Licensing Terms](https://www.microsoft.com/useterms/). The licensing terms might vary based on the distribution channel, for example, a Commercial Licensing program, Retail, Original Equipment Manufacturer (OEM), and so on.

## Key capabilities

### Hotpatch

Beginning with Windows Server 2022 Datacenter: Azure Edition, Hotpatch gives you the ability to apply security updates on your VM without rebooting. When used with Azure, [Azure Guest Patching Service](/en-us/azure/virtual-machines/automatic-vm-guest-patching), along with Automanage for Window Server, automate the onboarding, configuration, and orchestration of hotpatching. To learn more, see [Hotpatch for new virtual machines](hotpatch).

#### Supported platforms

To learn more about what operating systems support Hotpatch for VMs running on Azure and Azure Stack HCI, see [Supported platforms](/en-us/windows-server/get-started/hotpatch#supported-platforms).

Note

Hotpatch isn't supported on Windows Server containers base images.

### SMB over QUIC

Beginning with Windows Server 2022 Datacenter: Azure Edition, SMB over QUIC offers an "SMB VPN" for telecommuters, mobile device users, and branch offices. SMB over QUIC provides secure, reliable connectivity to edge file servers over untrusted networks like the Internet. [QUIC](https://datatracker.ietf.org/doc/rfc9000/) is an IETF-standardized protocol used in HTTP/3, designed for maximum data protection with TLS 1.3 and requires encryption that can't be disabled. SMB behaves normally within the QUIC tunnel, meaning the user experience doesn't change. SMB features like multichannel, signing, compression, continuous availability, and directory leasing work normally.

SMB over QUIC is also integrated with [Azure Automanage machine best practices for Windows Server](/en-us/azure/automanage/automanage-windows-server) to help make SMB over QUIC management easier. QUIC uses certificates to provide its encryption and organizations often struggle to maintain complex public key infrastructures. Azure Automanage machine best practices ensure that certificates don't expire without warning and that SMB over QUIC stays enabled for maximum continuity of service.

To learn more, see [SMB over QUIC](/en-us/windows-server/storage/file-server/smb-over-quic) and [SMB over QUIC management with Automanage machine best practices](/en-us/azure/automanage/automanage-smb-over-quic).

### Storage Replica compression for data transfer

Beginning with Update 1 for Windows Server 2022 Datacenter: Azure Edition, you can compress Storage Replica data between source and destination server. The compression results in fewer network packets to transfer the same amount of data, allowing for more throughputs, and less network utilization. Higher data throughput should also result in lowering synchronization time for when you need it most, for example in a disaster recovery scenario.

To learn more about Storage Replica features, see [Storage Replica features](/en-us/windows-server/storage/storage-replica/storage-replica-overview#storage-replica-features)

### Extended network for Azure

Beginning with Windows Server 2022 Datacenter: Azure Edition, Azure Extended Network enables you to stretch an on-premises subnet into Azure to let on-premises virtual machines keep their original on-premises private IP addresses when migrating to Azure. To learn more, see[Azure Extended Network](/en-us/windows-server/manage/windows-admin-center/azure/azure-extended-network).

## Get started with Windows Server Datacenter: Azure Edition

To get started using Azure Edition, use your preferred method to create an Azure or Azure Local VM, and select the *Windows Server Datacenter: Azure Edition* image that you would like to use.

Important

Some capabilities have specific configuration steps to perform during VM creation, and some capabilities that are in preview have specific opt-in and portal viewing requirements. See the individual capability articles to learn more about using that capability with your VM.

Caution

Once Windows Server Datacenter: Azure Edition is installed it isn't possible to switch the OS back to a non-Azure Edition OS. If you didn't mean to install Azure Edition, reinstalling the previous OS is required to switch back.

To learn more about creating virtual machine using Azure or Azure Local, see [Create a Windows virtual machine in the Azure portal](/en-us/azure/virtual-machines/windows/quick-create-portal) and [Deploy Windows Server Azure Edition VMs in Azure Local](/en-us/azure/azure-local/manage/windows-server-azure-edition-23h2).