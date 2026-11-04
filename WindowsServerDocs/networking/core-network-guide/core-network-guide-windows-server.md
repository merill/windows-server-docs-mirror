---
layout: Conceptual
title: Core network guidance for Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/core-network-guide/core-network-guide-windows-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This topic provides an overview of the Core Network Guide, which allows you to plan and deploy the core components required for a fully functioning network and a new Active Directory domain in a new forest with Windows Server 2016
ms.topic: concept-article
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: c9818999-40c8-8a7d-3815-768ec08076b4
document_version_independent_id: 5363eef0-4f5e-3f09-d40c-e04032223050
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/core-network-guide/core-network-guide-windows-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/core-network-guide/core-network-guide-windows-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/core-network-guide/core-network-guide-windows-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 30ac070c-7148-3cae-c166-8ca818189657
---

# Core network guidance for Windows Server | Microsoft Learn

This topic provides an overview of the Core network guidance for Windows Server® 2016, and contains the following sections.

- Introduction to the Windows Server Core Network
- Core Network Guide for Windows Server

## Introduction to the Windows Server Core Network

A core network is a collection of network hardware, devices, and software that provides the fundamental services for your organization's information technology (IT) needs.

A Windows Server core network provides you with many benefits, including the following.

- Core protocols for network connectivity between computers and other Transmission Control Protocol/Internet Protocol (TCP/IP) compatible devices. TCP/IP is a suite of standard protocols for connecting computers and building networks. TCP/IP is network protocol software provided with Microsoft® Windows® operating systems that implements and supports the TCP/IP protocol suite.
- Dynamic Host Configuration Protocol (DHCP) server automatic IP addressing. Manual configuration of IP addresses on all computers on your network is time-consuming and less flexible than dynamically providing computers and other devices with IP address leases from a DHCP server.
- Domain Name System (DNS) name resolution service. DNS allows users, computers, applications, and services to find the IP addresses of computers and devices on the network by using the Fully Qualified Domain Name of the computer or device.
- A forest, which is one or more Active Directory domains that share the same class and attribute definitions (schema), site and replication information (configuration), and forest-wide search capabilities (global catalog).
- A forest root domain, which is the first domain created in a new forest. The Enterprise Admins and Schema Admins groups, which are forest-wide administrative groups, are located in the forest root domain. In addition, a forest root domain, as with other domains, is a collection of computer, user, and group objects that are defined by the administrator in Active Directory Domain Services (AD DS). These objects share a common directory database and security policies. They can also share security relationships with other domains if you add domains as your organization grows. The directory service also stores directory data and allows authorized computers, applications, and users to access the data.
- A user and computer account database. The directory service provides a centralized user accounts database that allows you to create user and computer accounts for people and computers that are authorized to connect to your network and access network resources, such as applications, databases, shared files and folders, and printers.

A core network also allows you to scale your network as your organization grows and IT requirements change. For example, with a core network you can add domains, IP subnets, remote access services, wireless services, and other features and server roles provided by Windows Server 2016.

## Core Network Guide for Windows Server

The Windows Server 2016 Core Network Guide provides instructions on how to plan and deploy the core components required for a fully functioning network and a new Active Directory® domain in a new forest. Using this guide, you can deploy computers configured with the following Windows server components:

- The Active Directory Domain Services (AD DS) server role
- The Domain Name System (DNS) server role
- The Dynamic Host Configuration Protocol (DHCP) server role
- The Network Policy Server (NPS) role service of the Network Policy and Access Services server role
- The Web Server (IIS) server role
- Transmission Control Protocol/Internet Protocol version 4 (TCP/IP) connections on individual servers

This guide is available at the following location.

- The [Core Network Guide](core-network-guide) in the Windows Server 2016 Technical Library.