---
layout: Conceptual
title: Plan Multifactor Authentication for Remote Desktop Services | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-plan-mfa
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to plan and deploy Multifactor Authentication (MFA) with Remote Desktop Services (RDS) to enhance security and reduce unauthorized access risks.
ms.topic: concept-article
ai-usage: ai-assisted
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-30T00:00:00.0000000Z
locale: en-us
document_id: 0190d3bd-e8b0-0972-8bed-2cdedd9f36ec
document_version_independent_id: 9c7b7bc1-b01b-366a-a53d-1ad881808bf1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-plan-mfa.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-plan-mfa
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-plan-mfa.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 5c9f6c67-8528-21e6-0863-f5feef1ff881
---

# Plan Multifactor Authentication for Remote Desktop Services | Microsoft Learn

Multifactor Authentication (MFA) enhances the security of Remote Desktop Services (RDS) by requiring users to verify their identity through multiple authentication methods. This added layer of protection helps safeguard sensitive resources and reduces the risk of unauthorized access. This article provides an overview of the user experience, architecture components, and security benefits of integrating MFA with RDS, along with planning considerations for deployment.

## User Experience

For your end-users connecting to their desktops and applications, the experience is similar to any other second authentication measure to connect to the desired resource. The process typically involves:

1. Launch a desktop or RemoteApp.
2. Upon connecting to the RD Gateway for secure, remote access, receive a mobile application MFA challenge.
3. Correctly authenticate and get connected to their resources.

## Architecture components

RDS can integrate with Network Policy Server in Windows Server and its extension to Microsoft Entra ID. A typical RDS MFA implementation includes:

- **RD Gateway**: Acts as the entry point for remote connections.
- **Network Policy Server (NPS)**: Processes authentication requests and enforces policies.
- **Microsoft Entra ID**: Provides cloud-based MFA services.
- **NPS Extension**: Bridges on-premises NPS with cloud-based MFA.

For more information, see [Integrate your Remote Desktop Gateway infrastructure using the Network Policy Server (NPS) extension and Microsoft Entra ID](/en-us/entra/identity/authentication/howto-mfa-nps-extension-rdg).

When planning your MFA deployment, you should consider the following components:

- **User enrollment**: Plan how users will register their MFA methods.
- **Backup authentication**: Configure alternative methods for users who lose primary devices.
- **Conditional access**: Consider implementing location-based or device-based policies.
- **Network requirements**: Ensure firewall rules allow communication with MFA service endpoints.

## Security Benefits

Implementing MFA with Remote Desktop Services provides:

- **Reduced breach risk**: Even if passwords are compromised, extra verification prevents unauthorized access.
- **Compliance support**: Helps meet regulatory requirements for secure remote access.
- **Centralized management**: Unified MFA policies across cloud and on-premises resources.
- **Audit capabilities**: Detailed logging of authentication attempts and methods used.