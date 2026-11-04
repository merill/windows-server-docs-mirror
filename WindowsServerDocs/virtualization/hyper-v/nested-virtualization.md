---
layout: Conceptual
title: What is Nested Virtualization for Hyper-V? | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/nested-virtualization
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Nested virtualization in Hyper-V lets you run Hyper-V inside a VM. Learn how it works, supported scenarios, and when to use it in your environment.
author: robinharwood
ms.author: roharwoo
ms.topic: concept-article
ms.date: 2025-06-10T00:00:00.0000000Z
locale: en-us
document_id: dbeb6f36-6435-e79b-4c53-032dfc6e5989
document_version_independent_id: dbeb6f36-6435-e79b-4c53-032dfc6e5989
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/nested-virtualization.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/nested-virtualization
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/nested-virtualization.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: f9aa7868-f03e-0c2e-3726-5e0b8f6f2077
---

# What is Nested Virtualization for Hyper-V? | Microsoft Learn

Nested virtualization is a feature that lets you run Hyper-V inside a Hyper-V virtual machine (VM). This article explains how nested virtualization works, its benefits, and when to use it in your environment. For example, nested virtualization can be useful for:

- Running applications or emulators in a nested VM
- Testing software releases on VMs
- Reducing deployment times for training environments
- Using Hyper-V isolation for containers

Modern processors include hardware features that make virtualization faster and more secure. Hyper-V relies on these processor extensions to run virtual machines, for example, Intel VT-x and AMD-V. Nested virtualization makes this hardware support available to guest virtual machines.

The following diagram shows Hyper-V without nesting. The Hyper-V hypervisor takes full control of the hardware virtualization capabilities (orange arrow), and doesn't expose them to the guest operating system.

![Diagram of the levels of Hyper V with Nested Virtualization disabled.](media/no-nesting.png)

In contrast, the following diagram shows Hyper-V with Nested Virtualization enabled. In this case, Hyper-V exposes the hardware virtualization extensions to its virtual machines. With nesting enabled, a guest virtual machine can install its own hypervisor and run its own guest VMs.

![Diagram of the levels of Hyper V with Nested Virtualization enabled.](media/nesting.png)

## Dynamic Memory and Runtime Memory Resize

When Hyper-V is running inside a virtual machine, the virtual machine must be turned off to adjust its memory. Meaning that even if dynamic memory is enabled, the amount of memory doesn't fluctuate. Simply enabling nested virtualization has no effect on dynamic memory or runtime memory resize.

For virtual machines without dynamic memory enabled, attempting to adjust the amount of memory while running fails. The incompatibility only occurs while Hyper-V is running in the VM.

## Non-Microsoft virtualization apps

Virtualization applications other than Hyper-V aren't supported in Hyper-V virtual machines, and are likely to fail. Virtualization applications include any software that requires hardware virtualization extensions.

## Supported scenarios

Using a nested Hyper-V VM in production is supported for both Azure and on-premises in the following scenarios. We also recommend you make sure that your services and applications are also supported.

Nested Virtualization isn't suitable for Windows Server Failover Clustering, and performance sensitive applications. We recommended you fully evaluate the services and applications.

### Hyper-V VMs on Hyper-V VMs

Running Hyper-V VMs nested on Hyper-V VMs is great for test labs and evaluation environments. Especially where configurations can be easily modified and saved states can be used to revert to specific configurations. Test labs don't typically require the same service level agreement (SLA) as production environments.

Production environments running Hyper-V VMs running on Hyper-V VMs are supported. Ensure that your services and applications are also supported. If you use a nested Hyper-V VM in production, make sure you fully evaluate whether your services or applications provide the expected behavior.

To learn more about setting up Nested Virtualization on Azure, see our Tech Community blog [How to Setup Nested Virtualization for Azure VM/VHD](https://techcommunity.microsoft.com/t5/itops-talk-blog/how-to-setup-nested-virtualization-for-azure-vm-vhd/ba-p/1115338).

### Non-Microsoft virtualization on Hyper-V virtualization

While it might be possible for non-Microsoft virtualization to run on Hyper-V, Microsoft doesn't test this scenario. Non-Microsoft virtualization on Hyper-V virtualization isn't supported. Ensure your hypervisor vendor supports this scenario.

### Hyper-V virtualization on non-Microsoft virtualization

While it might be possible for Hyper-V virtualization to run on non-Microsoft virtualization, Microsoft doesn't test this scenario. Hyper-V virtualization on non-Microsoft virtualization isn't supported. Ensure your hypervisor vendor supports this scenario.

### Azure Local nested on Hyper-V VMs

Azure Local is designed and tested to run on validated physical hardware. Azure Local can run nested in a virtual machine for evaluation, but production environments in a nested configuration aren't supported.

To learn more about Azure Local nested on Hyper-V VMs, see [Nested virtualization in Azure Local](/en-us/azure/azure-local/manage/enable-nested-virtualization).

### Hyper-V isolated containers running nested on Hyper-V

Microsoft offers Hyper-V isolation for containers. This isolation mode offers enhanced security and broader compatibility between host and container versions. With Hyper-V isolation, multiple container instances run concurrently on a host. Each container runs inside of a highly optimized virtual machine and effectively gets its own kernel. Since a Hyper-V isolated container offers isolation through a hypervisor layer between itself and the container host, when the container host is a Hyper-V based virtual machine, there's performance overhead. The associated performance overhead occurs in terms of container start-up time, storage, network, and CPU operations.

When a Hyper-V isolated container is run in a Hyper-V VM, it's running nested. Using a Hyper-V VM opens many useful scenarios but also increases latency, as there are two levels of hypervisors running above the physical host.

Running Hyper-V isolated containers nested on Hyper-V is supported. One level of nested virtualization is supported in production, which allows for isolated container deployments.

To learn more about Nested Hyper-V Containers, see [Performance tuning Windows Server Containers](/en-us/windows-server/administration/performance-tuning/role/windows-server-container/).

### Run WSL2 in a Hyper-V VM running nested on Hyper-V

Windows Subsystem for Linux (WSL) is a feature of the Windows operating system that enables you to run a Linux file system, along with Linux command-line tools and GUI apps, directly on Windows.

Running WSL2 in a Hyper-V VM running nested on Hyper-V is supported.

To learn more about how to enabled WSL 2 to run in a VM, see [Frequently Asked Questions about Windows Subsystem for Linux](/en-us/windows/wsl/faq#can-i-run-wsl-2-in-a-virtual-machine-).