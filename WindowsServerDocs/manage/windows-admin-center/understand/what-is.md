---
layout: Conceptual
title: What is Windows Admin Center | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/understand/what-is
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn what Windows Admin Center is, how its Administration and Virtualization modes work, and how it helps you manage Windows servers, clients, and clusters.
ms.topic: concept-article
author: davannaw-msft
ms.author: dawhite
ms.date: 2025-08-07T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 5fe3f40d-c04f-55bf-df8d-846ef2411108
document_version_independent_id: 4eb546b9-3821-70bb-3257-8cdd6a26f57a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/understand/what-is.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/understand/what-is
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/understand/what-is.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 3e546a01-9f72-f439-20a4-c5e23bb1f56a
---

# What is Windows Admin Center | Microsoft Learn

You deploy Windows Admin Center locally as a browser-based management platform with two modes that share a common platform core. **Administration Mode** provides general management for Windows clients, servers, and clusters. **Virtualization Mode** provides centralized management for Hyper-V hosts, clusters, storage, and networking at scale. Install the modes separately because they use different management architectures. For more information about Virtualization Mode, see [What is Windows Admin Center Virtualization Mode?](../virtualization-mode-overview)

Administration Mode lets you manage systems without connecting to the cloud and is useful for servers on private networks that aren't connected to the internet. Administration Mode modernizes "in-box" management tools such as Server Manager and Microsoft Management Console (MMC). It complements System Center; it doesn't replace it.

![Diagram of Windows Admin Center working with other solutions](../media/wac-complements.png)

## How do Windows Admin Center modes work?

In Administration Mode, Windows Admin Center runs in a web browser and connects directly to one managed system at a time through the **Windows Admin Center gateway**. Administration Mode manages Windows Server 2016 and later, Windows 11, Windows 10, and more. You can install its gateway on Windows Server or domain-joined Windows 10 or 11. The gateway manages servers by using Remote PowerShell and Windows Management Instrumentation (WMI) over Windows Remote Management (WinRM). A single lightweight .msi package, available from the [Windows Admin Center overview](../overview), includes the Administration Mode gateway.

After you publish the Administration Mode gateway to DNS and configure the corresponding corporate firewall rules, you can securely connect to and manage your servers from anywhere with Microsoft Edge or Google Chrome.

The **Administration Mode gateway** uses a .NET 10 backend for improved performance, security, and cryptography. It also includes support for HTTP/2, reducing latency and enhancing the responsiveness of Windows Admin Center.

![Diagram of the Windows Admin Center Administration Mode architecture.](../media/architecture.png)

### Administration Mode architecture

The modernized Administration Mode gateway uses microservice architecture. Before this upgrade, the gateway performed all tasks in a single process. With this new model, one process starts with Administration Mode and serves as a process manager. As you use Administration Mode, the process manager starts more subprocesses to perform specific tasks.

Gateway plug-ins that are compatible with the modernized Administration Mode gateway also run their own collection of subprocesses under the Windows Admin Center service manager to perform their functions.

Changing from a monolithic service to a microservice model helps the modernized gateway be more flexible, scalable, and resilient.

#### Kestrel HTTP web server

Previously, the Administration Mode gateway utilized [Katana](/en-us/aspnet/aspnet/overview/owin-and-katana) components, including a web server, on the backend. The modernized gateway uses an ASP.NET Core Kestrel web server. [Kestrel](/en-us/aspnet/core/fundamentals/servers/kestrel) is the recommended web server for ASP.NET Core applications. Kestrel supports the HTTP/2 web protocol, where the Administration Mode gateway previously supported only HTTP/1.1 with the Katana components. The upgrade from HTTP/1.1 to HTTP/2 brings reduced latency to the application and increased responsiveness through features like multiplexing and server push.

### Virtualization Mode architecture

Virtualization Mode uses a separate, centralized gateway and a stateful architecture. The gateway maintains a database, and local agents on managed Hyper-V hosts collect data and perform operations. This architecture supports persistent connections and parallel operations across virtualization infrastructure instead of the direct, per-session WinRM connections that Administration Mode uses. For more information, see [How Virtualization Mode works](../virtualization-mode-overview#how-it-works).

## Learn how Windows Admin Center improves your management environment

### Familiar functionality

Windows Admin Center is the evolution of long-standing, well known management platforms like Microsoft Management Console (MMC), built from the ground up for the way systems are built and managed today. Windows Admin Center contains many of the familiar tools you currently use to manage Windows Servers and clients.

### Easy to install and use

[Install Administration Mode](../deploy/install) on a Windows computer to begin managing it locally, or install it on Windows Server as a gateway so that people in your organization can manage computers from their web browsers.

### Complements existing solutions

Windows Admin Center works with solutions like System Center and Azure management and security, adding to their capabilities to perform detailed, single-machine management tasks.

### Manage from anywhere

Publish your Administration Mode gateway server to the public Internet to securely connect to and manage your servers from anywhere.

### Enhanced security for your management platform

Administration Mode has many [security and user access options](../plan/user-access-options) that make your management platform more secure. Role-based access control lets you fine-tune which administrators have access to which management features. Administration Mode gateway authentication options include local groups, local domain-based Active Directory, and cloud-based Microsoft Entra ID. Also, [review event logs](../use/logging) to learn about management actions in your environment.

### Azure integration for on-premises and hybrid machines

Windows Admin Center has many points of [integration with Azure services](../azure/), including Microsoft Entra ID, Azure Backup, Azure Site Recovery, and more.

### Windows Admin Center in Azure

By using Windows Admin Center in the Azure portal, you can manage the Windows Server operating system of your Azure Arc-enabled servers and Azure VMs.

You can securely manage your machines from anywhere–without needing a VPN, public IP address, or other inbound connectivity to your machine.

### Deploy hyper-converged and failover clusters

Windows Admin Center provides a wizard for deploying [hyperconverged infrastructure](../use/deploy-hyperconverged-infrastructure) and failover clusters.

### Manage hyper-converged clusters

Windows Admin Center offers the best experience for [managing hyper-converged clusters](../use/manage-hyper-converged) - including virtualized compute, storage, and networking components.

### Extensibility

Windows Admin Center was built with extensibility in mind from the beginning, with the ability for Microsoft and third party developers to build tools and solutions beyond the current offerings. Microsoft offers an [SDK](../extend/extensibility-overview) that enables developers to build their own tools for Windows Admin Center.

Tip

To install Windows Admin Center, [download Windows Admin Center](../overview).