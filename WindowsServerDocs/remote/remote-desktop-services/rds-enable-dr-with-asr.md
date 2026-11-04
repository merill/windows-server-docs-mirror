---
layout: Conceptual
title: Enable disaster recovery of RDS using Azure Site Recovery | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-enable-dr-with-asr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn how to enable disaster recovery of RDS using Azure Site Recovery.
ms.author: roharwoo
ms.date: 2024-07-03T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
locale: en-us
document_id: cfd2007a-0a3f-0310-dd86-fbd6d816a870
document_version_independent_id: 0e46eefd-e301-edd3-4bd0-ae76abba855d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-enable-dr-with-asr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-enable-dr-with-asr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-enable-dr-with-asr.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bba62c59-6b53-4be4-8b9d-6624f9184c22
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/f3a81ffb-ee36-4ec7-b54a-01b6681aff65
platformId: 04713eef-c2c3-0423-5b9a-b9c634d8632c
---

# Enable disaster recovery of RDS using Azure Site Recovery | Microsoft Learn

To ensure that your RDS deployment is adequately configured for disaster recovery, you need to protect all of the components that make up your RDS deployment:

- Active Directory
- SQL Server tier
- RDS components
- Network components

## Configure Active Directory and DNS replication

You need Active Directory on the disaster recovery site for your RDS deployment to work. You have two choices based on how complex your RDS deployment is:

- Option 1 - If you have a small number of applications and a single domain controller for your entire on-premises site, and you will be failing over the entire site together, use ASR-Replication to replicate the domain controller to the secondary site (true for both site-to-site and site-to-Azure scenarios).
- Option 2 - If you have a large number of applications and you're running an Active Directory forest, and you'll failover a few applications at a time, set up an additional domain controller on the disaster recovery site (either a secondary site or in Azure).

See [Protect Active Directory and DNS with Azure Site Recovery](/en-us/azure/site-recovery/site-recovery-active-directory) for details on making a domain controller available on the disaster recovery site. For the rest of this guidance, we assume that you've followed those steps and have the domain controller available.

## Set up SQL Server replication

See [Protect SQL Server using SQL Server disaster recovery and Azure Site Recovery](/en-us/azure/site-recovery/site-recovery-sql) for the steps to set up SQL Server replication.

## Enable protection for the RDS application components

Depending on your RDS deployment type you can enable protection for different component VMs (as listed in the table below) in Azure Site Recovery. Configure the relevant Azure Site Recovery elements based on whether your VMs are deployed on Hyper-V or VMWare.

| Deployment type | Protection steps |
| --- | --- |
| Personal virtual desktop (unmanaged) | 1. Make sure all virtualization hosts are ready with the RDVH role installed. 2. Connection Broker. 3. Personal desktops. 4. Gold template VM. 5. Web Access, License server, and Gateway server |
| Pooled virtual desktop (managed with no UPD) | 1. All virtualization hosts are ready with the RDVH role installed. 2. Connection Broker. 3. Gold template VM. 4. Web Access, License server, and Gateway server. |
| RemoteApps and Desktop Sessions (no UPD) | 1. Session Hosts. 2. Connection Broker. 3. Web Access, License server, and Gateway server. |