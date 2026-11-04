---
layout: Conceptual
title: Deploy Remote Access in an Enterprise | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/deploy-remote-access-in-an-enterprise
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: This topic provides an introduction to the DirectAccess scenario in Windows Server 2016 for the Enterprise.
ms.topic: install-set-up-deploy
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 74a65263-b05e-732b-03a0-7b2b19ae058f
document_version_independent_id: 33578290-03c5-4f82-99e5-170af238efc2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/Deploy-Remote-Access-in-an-Enterprise.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/deploy-remote-access-in-an-enterprise
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/Deploy-Remote-Access-in-an-Enterprise.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 6975a45b-37e5-8e37-33ad-a407b88730c1
---

# Deploy Remote Access in an Enterprise | Microsoft Learn

This topic provides an introduction to the DirectAccess scenario for the Enterprise.

Important

To deploy DirectAccess using this guide, you must use a DirectAccess server that is running Windows Server 2016, Windows Server 2012 R2 or Windows Server 2012.

## Before you begin deploying, see the list of unsupported configurations, known issues, and prerequisites

- [DirectAccess Unsupported Configurations](../directaccess/directaccess-unsupported-configurations)
- [DirectAccess Known Issues](../directaccess/directaccess-known-issues)
- [Prerequisites for Deploying DirectAccess) Prerequisites](../directaccess/prerequisites-for-deploying-directaccess)

## Scenario description

Remote access includes a number of enterprise features, including deploying multiple Remote Access servers in a cluster load balanced with Windows Network Load Balancing (NLB) or an external load balancer, setting up a multisite deployment with Remote Access servers situated in dispersed geographical locations, and deploying DirectAccess with two-factor client authentication using a one-time password (OTP).

## In this scenario

Each enterprise scenario is described in a document that includes planning and deployment instructions. For more information, see:

- [Deploy Remote Access in a cluster](cluster/deploy-remote-access-in-cluster)
- [Deploy Multiple Remote Access Servers in a Multisite Deployment](multisite/deploy-multiple-remote-access-servers-in-a-multisite-deployment)
- [Deploy Remote Access with OTP Authentication](otp/deploy-ra-otp)
- [Deploy Remote Access in a Multi-Forest Environment](multi-forest/deploy-remote-access-in-a-multi-forest-environment)

## Practical applications

Remote access enterprise scenarios provide the following:

- **Increased availability**. Deploying multiple Remote Access servers in a cluster provides scalability and increases the capacity for throughput and number of users. Load balancing the cluster provides high availability. If a server in the cluster fails, remote users can continue to access the internal corporate network via a different server in the cluster. Failover is transparent as clients connect to the cluster using a virtual IP (VIP) address.
- **Ease-of-management**. A cluster or multisite deployment can be configured and managed as a single entity using the Remote Access Management console running on one of the cluster servers. In addition, a multisite deployment allows administrators to align Remote Access deployment to Active Directory sites, providing a simplified architecture. Shared settings can easily be set across cluster servers or on all multisite entry point servers. Remote Access settings can be managed from any of the servers in the cluster or deployment, or remotely using Remote Server Administration Tools (RSAT). In addition, the entire cluster or multisite deployment can be monitored from a single Remote Access Management console.
- **Cost efficiency**. A Remote Access multisite deployment allows enterprises to deploy Remote Access servers in multiple sites corresponding to client locations. This provides a predictable access experience for remote clients regardless of location, and reduces costs and intranet bandwidth by routing client traffic over the Internet to the closest Remote Access server.
- **Security**. Deploying strong client authentication with a one-time password (OTP) instead of standard Active Directory password increases security.

## Roles and features included in this scenario

The following table lists the roles and features used in the enterprise scenario.

| Role/feature | How it supports this scenario |
| --- | --- |
| Remote Access server role | The role is installed and uninstalled using the Server Manager console. This role encompasses both DirectAccess, which was previously a feature in Windows Server 2008 R2, and Routing and Remote Access Services which was previously a role service under the Network Policy and Access Services (NPAS) server role. The Remote Access role consists of two components:<br>1. DirectAccess and Routing and Remote Access Services (RRAS) VPN-DirectAccess and VPN are managed together in the Remote Access Management console.2. RRAS Routing-RRAS routing features are managed in the legacy Routing and Remote Access console.<br><br>The Remote Access Server Role is dependent on the following server features:<br><br>- Internet Information Services (IIS) - This feature is required to configure the network location server and default web probe.- Group Policy Management Console feature - feature is required by DirectAccess to create and manage the Group Policy Objects (GPOs) in Active Directory and must be installed as a required feature for the server role. |
| Remote Access Management Tools feature | This feature is installed as follows:<br>- It is installed by default on a Remote Access server when the Remote Access role is installed, and supports the Remote Management console user interface.- It can be optionally installed on a server not running the Remote Access server role. In this case it is used for remote management of a Remote Access computer running DirectAccess and VPN.<br><br>The Remote Access Management Tools feature consists of the following:<br><br>1. Remote Access GUI and Command Line Tools2. Remote Access module for Windows PowerShell<br><br>Dependencies include:<br><br>1. Group Policy Management Console2. RAS Connection Manager Administration Kit (CMAK)3. Windows PowerShell 3.04. Graphical Management Tools and Infrastructure |
| Windows NLB | This feature allows the load balancing of multiple Remote Access servers. |