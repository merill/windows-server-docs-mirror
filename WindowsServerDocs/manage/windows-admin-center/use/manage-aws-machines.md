---
layout: Conceptual
title: Manage Windows Server on Amazon EC2 Using Windows Admin Center | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/use/manage-aws-machines
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Learn how to use Windows Admin Center to connect and manage Windows Server on Amazon EC2.
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2023-07-05T00:00:00.0000000Z
locale: en-us
document_id: 5e932803-a842-cdb6-3f33-2540107d7546
document_version_independent_id: 5e932803-a842-cdb6-3f33-2540107d7546
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/use/manage-aws-machines.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/use/manage-aws-machines
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/use/manage-aws-machines.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 5da9e014-a584-1ab9-4cb6-bc28a3f14367
---

# Manage Windows Server on Amazon EC2 Using Windows Admin Center | Microsoft Learn

By using Windows Admin Center, you can manage Windows Server machines running on Amazon EC2 in Amazon Web Services. In this article, you learn how to prepare and connect a Windows Server machine running on Amazon EC2 to Windows Admin Center by using a public IP address.

## Prerequisites

- Have a running Amazon EC2 instance.
- Configure WinRM for HTTPS. WinRM HTTPS requires a server authentication certificate for a local computer, with a CN that matches the public name of your Windows Server Amazon EC2 instance. For more information, see [How to configure WINRM for HTTPS](/en-us/troubleshoot/windows-client/system-management-components/configure-winrm-for-https).
- Enable inbound connections for your Amazon EC2 instance. For more information, see the [AWS documentation](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/authorizing-access-to-an-instance.html).
    - For **Type**, select **WinRM-HTTPS**. For the port range, enter **5986**.
    - For **Source**, select **IP Addresses**, and then enter the source IP address that corresponds to your Windows Admin Center gateway.

Note

Alternatively, you can connect to your Amazon EC2 instance via HTTP by selecting **WinRM-HTTP** and entering **5985** as your port range. However, we recommend that you consider the security implications.

## Prepare your machine

Configure your Windows Server Amazon EC2 instance by using the following steps:

1. Enable WinRM access to your target Amazon EC2 instance by running the `winrm quickconfig` command in PowerShell on the target EC2 instance.
2. Enable inbound connections to port 5986 for WinRM over HTTPS by running the following PowerShell script on the target EC2 instance: `Set-NetFirewallRule -Name WINRM-HTTPS-In-TCP-PUBLIC -RemoteAddress Any`. Alternatively, you can configure port 5985 for WinRM over HTTP.

## Connect to your machine

Add your Windows Server Amazon EC2 instance as a connection in Windows Admin Center:

1. In the Azure portal, open Windows Admin Center.
2. On the **Add or create resource** menu, in the **Servers** section, select **Add**.
3. For **Server name**, enter the public IPv4 address of your Amazon EC2 instance.
4. Select **Use another account for this connection** and enter your Windows credentials.