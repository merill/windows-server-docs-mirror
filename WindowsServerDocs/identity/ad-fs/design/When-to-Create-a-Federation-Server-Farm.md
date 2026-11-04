---
layout: Conceptual
title: When to Create a Federation Server Farm | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/when-to-create-a-federation-server-farm
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: When to Create a Federation Server Farm'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 4ca945b2-52c1-970a-c076-0c693d9f666f
document_version_independent_id: 2bf38d6a-5ac1-3986-5ef5-4392b3ef427e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/When-to-Create-a-Federation-Server-Farm.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/when-to-create-a-federation-server-farm
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/When-to-Create-a-Federation-Server-Farm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: dd29be6b-b0ec-0940-6795-2fe328376bd5
---

# When to Create a Federation Server Farm | Microsoft Learn

Consider creating a federation server farm in Active Directory Federation Services (AD FS) when you have a larger AD FS deployment and you want to provide fault tolerance, load-balancing, or scalability to your organization's Federation Service. The act of creating two or more federation servers in the same network, configuring each of them to use the same Federation Service, and adding the public key of each server's token-signing certificates to the AD FS Management snap-in creates a federation server farm.

You can create a federation server farm or install additional federation servers to an existing farm by using the AD FS Federation Server Configuration Wizard. For more information, see [When to Create a Federation Server](when-to-create-a-federation-server).

Note

When you choose the option to create a **New federation server farm** using the AD FS Federation Server Configuration Wizard, the wizard will attempt to create a container object (for sharing certificates) in Active Directory. Therefore, it is important that you first log on to the computer, where you are setting up the federation server role, with an account that has sufficient permissions in Active Directory to create this container object.

Before federation servers can be grouped as a farm, they must first be clustered so that requests that arrive at a single fully qualified domain name (FQDN) are routed to the various federation servers in the server farm. You can create the server cluster by deploying Network Load Balancing (NLB) inside the corporate network. This guide assumes that NLB has been configured appropriately to cluster each of the federation servers in the farm.

For more information about how to configure a cluster FQDN using Microsoft NLB technology, see [Specifying the Cluster Parameters](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc781505%28v=ws.10%29).

## Best practices for deploying a federation server farm

We recommend the following best practices for deploying a federation server in a production environment:

- If you will be deploying multiple federation servers at the same time or you know that you will be adding more servers to the farm over time, consider creating a server image of an existing federation server in the farm and then installing from that image when you need to create additional federation servers quickly.

    Note

    If you do decide to use the server image method for deploying additional federation servers, you do not have to complete the tasks in [Checklist: Setting Up a Federation Server](../deployment/checklist--setting-up-a-federation-server) every time that you want to add a new server to the farm.
- Use NLB or some other form of clustering to allocate a single IP address for many federation server computers.
- Reserve a static IP address for each federation server in the farm and, depending on your Domain Name System (DNS) configuration, insert an exclusion for each IP address in Dynamic Host Configuration Protocol (DHCP). Microsoft NLB technology requires that each server that participates in the NLB cluster be assigned a static IP address.
- If the AD FS configuration database will be stored in a SQL database, avoid editing the SQL database from multiple federation servers at the same time.

## Configuring federation servers for a farm

The following table describes the tasks that must be completed so that each federation server can participate in a farmed environment.

| Task | Description |
| --- | --- |
| If you are using SQL Server to store the AD FS configuration database | A federation server farm consists of two or more federation servers that share the same AD FS configuration database and token-signing certificates. The configuration database can be stored in either Windows Internal Database or in a SQL Server database. If you plan to store the configuration database in a SQL database, make sure that the configuration database is accessible so that it can be accessed by all new federation servers that participate in the farm. **Note:** For farm scenarios, it is important that the configuration database be located on a computer that does not also participate as a federation server in that farm. Microsoft NLB does not allow any of the computers that participate in a farm to communicate with one another. **Note:** Ensure that the identity of the AD FS AppPool in Internet Information Services (IIS)) on every federation server that participates in the farm has Read access to the configuration database. |
| Obtain and share certificates | You can obtain a single server authentication certificate from a public certification authority (CA)—for example, VeriSign. You can then configure the certificate so that all federation servers share the same private key portion of the certificate. For more information about how to share the same certificate, see [Checklist: Setting Up a Federation Server](../deployment/checklist--setting-up-a-federation-server). **Note:** The AD FS Management snap-in refers to server authentication certificates for federation servers as service communication certificates.<br>For more information, see [Certificate Requirements for Federation Servers](certificate-requirements-for-federation-servers). |
| Point to the same SQL Server instance | If the AD FS configuration database will be stored in a SQL database, the new federation server must point to the same SQL Server instance that is used by other federation servers in the farm so that the new server can participate in the farm. |