---
layout: Conceptual
title: DirectAccess | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/directaccess
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: You can use this topic for a brief overview of DirectAccess in Windows Server.
ms.topic: overview
ms.author: roharwoo
author: robinharwood
ms.date: 2022-11-16T00:00:00.0000000Z
ms.custom: os_security, network_security
locale: en-us
document_id: fa82e6ef-7f35-9672-2ca3-9006de31b2cf
document_version_independent_id: 1dca040b-d5ba-8449-627b-b3069bd9be0e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/DirectAccess.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/directaccess
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/DirectAccess.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f689f5f1-38d0-6af5-cc4e-29994ce92b15
---

# DirectAccess | Microsoft Learn

Important

Microsoft highly recommends that you use Always On VPN instead of DirectAccess for new deployments. For more information, see [Always on VPN](../overview-always-on-vpn).

You can use this topic for a brief overview of DirectAccess, including the server and client operating systems that support DirectAccess, and for links to additional DirectAccess documentation for Windows Server.

Note

In addition to this topic, the following DirectAccess documentation is available.

- [DirectAccess Deployment Paths in Windows Server](directaccess-deployment-paths-in-windows-server)
- [Prerequisites for Deploying DirectAccess](prerequisites-for-deploying-directaccess)
- [DirectAccess Unsupported Configurations](directaccess-unsupported-configurations)
- [DirectAccess Test Lab Guides](directaccess-test-lab-guides)
- [DirectAccess Known Issues](directaccess-known-issues)
- [DirectAccess Capacity Planning](directaccess-capacity-planning)
- [DirectAccess Offline Domain Join](directaccess-offline-domain-join)
- [Troubleshooting DirectAccess](troubleshooting-directaccess)
- [Deploy a Single DirectAccess Server Using the Getting Started Wizard](single-server-wizard/deploy-a-single-directaccess-server-using-the-getting-started-wizard)
- [Deploy a Single DirectAccess Server with Advanced Settings](single-server-advanced/deploy-a-single-directaccess-server-with-advanced-settings)
- [Add DirectAccess to an Existing Remote Access (VPN) Deployment](add-to-existing-vpn/add-directaccess-to-an-existing-remote-access-vpn-deployment)

DirectAccess allows connectivity for remote users to organization network resources without the need for traditional Virtual Private Network (VPN) connections. With DirectAccess connections, remote client computers are always connected to your organization - there is no need for remote users to start and stop connections, as is required with VPN connections. In addition, your IT administrators can manage DirectAccess client computers whenever they are running and Internet connected.

Important

Do not attempt to deploy Remote Access on a virtual machine (VM) in Microsoft Azure. Using Remote Access in Microsoft Azure is not supported. You cannot use Remote Access in an Azure VM to deploy VPN, DirectAccess, or any other Remote Access feature in Windows Server. For more information, see [Microsoft server software support for Microsoft Azure virtual machines](https://support.microsoft.com/help/2721672/microsoft-server-software-support-for-microsoft-azure-virtual-machines).

DirectAccess provides support only for domain-joined clients that include operating system support for DirectAccess.

The following client operating systems support DirectAccess.

- Windows 11 Enterprise
- Windows 10 Enterprise
- Windows 10 Enterprise 2015 Long Term Servicing Branch (LTSB)
- Windows 8.1 Enterprise