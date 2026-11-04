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
description: What is Windows Admin Center (Project Honolulu)
ms.topic: concept-article
author: davannaw-msft
ms.author: dawhite
ms.date: 2025-08-07T00:00:00.0000000Z
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
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 3e546a01-9f72-f439-20a4-c5e23bb1f56a
---

# What is Windows Admin Center | Microsoft Learn

Windows Admin Center is a locally deployed, browser-based management tool set that lets you manage your Windows Clients, Servers, and Clusters without needing to connect to the cloud. Windows Admin Center gives you full control over all aspects of your server infrastructure and is useful for managing servers on private networks that aren't connected to the Internet.

Windows Admin Center is the modern evolution of "in-box" management tools, like Server Manager and MMC. It complements System Center - it's not a replacement.

![Diagram of Windows Admin Center working with other solutions](../media/wac-complements.png)

## How does Windows Admin Center work?

Windows Admin Center runs in a web browser and manages Windows Server 2016 and later, Windows 11, Windows 10, and more through the **Windows Admin Center gateway** installed on Windows Server or domain-joined Windows 10 or 11. The gateway manages servers by using Remote PowerShell and WMI over WinRM. The gateway is included with Windows Admin Center in a single lightweight .msi package that you can [download](../overview).

The Windows Admin Center gateway, when published to DNS and given access through corresponding corporate firewalls, lets you securely connect to, and manage, your servers from anywhere with Microsoft Edge or Google Chrome.

The **Windows Admin Center gateway** uses a .NET 8 backend for enhanced performance, security, and improved cryptography. It also includes support for HTTP/2, reducing latency and enhancing the responsiveness of Windows Admin Center.

![Diagram of the Windows Admin Center architecture](../media/architecture.png)

### Multi-process, micro-service based architecture

The modernized gateway uses microservice architecture. Prior to this upgrade, Windows Admin Center performed all tasks in a single process. With this new model, we start one process for Windows Admin Center on application startup that serves as a process manager. As you use Windows Admin Center, more subprocesses are spun up to perform specific tasks.

Additionally, gateway plug-ins that are compatible with the modernized gateway also run their own collection of subprocesses under the Windows Admin Center service manager to perform their functions.

Changing from a monolithic service to a microservice model helps the modernized gateway be more flexible, scalable, and resilient.

### Kestrel HTTP web server

Previously, Windows Admin Center utilized [Katana](/en-us/aspnet/aspnet/overview/owin-and-katana) components, including a web server, on the backend. With the modernized gateway, we’ve shifted to an ASP.NET Core Kestrel web server. [Kestrel](/en-us/aspnet/core/fundamentals/servers/kestrel) is the recommended web server for ASP.NET Core applications. Additionally, Kestrel supports the HTTP/2 web protocol, where previously we had only supported HTTP1.1 with the Katana components. The upgrade from HTTP1.1 to HTTP/2 brings reduced latency to our application and increased responsiveness through enhanced features like multiplexing and server push.

## Learn how Windows Admin Center improves your management environment

### Familiar functionality

Windows Admin Center is the evolution of long-standing, well known management platforms like Microsoft Management Console (MMC), built from the ground up for the way systems are built and managed today. Windows Admin Center contains many of the familiar tools you currently use to manage Windows Servers and clients.

### Easy to install and use

[Install](../deploy/install) on a Windows computer, and start managing in minutes, or install on a Windows Server acting as a gateway to enable your entire organization to manage computers from their web browser.

### Complements existing solutions

Windows Admin Center works with solutions like System Center and Azure management and security, adding to their capabilities to perform detailed, single-machine management tasks.

### Manage from anywhere

Publish your Windows Admin Center gateway server to the public Internet, then you can connect to and manage your servers from anywhere, all in a secure manner.

### Enhanced security for your management platform

Windows Admin Center has many enhancements that make your management platform [more secure](../plan/user-access-options). Role-based access control lets you fine-tune which administrators have access to which management features. Gateway authentication options include local groups, local domain-based Active Directory, and cloud-based Microsoft Entra ID. Also, [gain insight](../use/logging) into management actions performed in your environment.

### Azure integration for on-premises and hybrid machines

Windows Admin Center has many points of [integration with Azure services](../azure/), including Microsoft Entra ID, Azure Backup, Azure Site Recovery, and more.

### Windows Admin Center in Azure

By using Windows Admin Center in the Azure portal, you can manage the Windows Server operating system of your Arc-enabled servers (preview) and Azure VMs.

You can securely manage your machines from anywhere–without needing a VPN, public IP address, or other inbound connectivity to your machine.

### Deploy hyper-converged and failover clusters

Windows Admin Center allows for [seamless deployment of hyper-converged and failover clusters](../use/deploy-hyperconverged-infrastructure) through an easy-to-use wizard.

### Manage hyper-converged clusters

Windows Admin Center offers the best experience for [managing hyper-converged clusters](../use/manage-hyper-converged) - including virtualized compute, storage, and networking components.

### Extensibility

Windows Admin Center was built with extensibility in mind from the beginning, with the ability for Microsoft and third party developers to build tools and solutions beyond the current offerings. Microsoft offers an [SDK](../extend/extensibility-overview) that enables developers to build their own tools for Windows Admin Center.

Tip

Ready to install Windows Admin Center? [Download now](../overview)