---
layout: Conceptual
title: Checklist - Setting Up a Federation Server Proxy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/checklist--setting-up-a-federation-server-proxy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Checklist: Setting Up a Federation Server Proxy'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: checklist
locale: en-us
document_id: edd77e6f-9629-4a83-cc69-d79d99a6d274
document_version_independent_id: dab5fa29-6bf3-65de-9de5-42faa8fd6d9d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server-Proxy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/deployment/checklist--setting-up-a-federation-server-proxy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server-Proxy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 010c86a0-ca1b-7b62-36b8-0917af37ed99
---

# Checklist - Setting Up a Federation Server Proxy | Microsoft Learn

This checklist includes the deployment tasks for preparing a server running Windows Server® 2012 for the federation server proxy role in Active Directory Federation Services (AD FS).

Note

Complete the tasks in this checklist in order. When a reference link takes you to a procedure, return to this topic after you complete the steps in that procedure so that you can proceed with the remaining tasks in this checklist.

![Icon for the Setting Up a federation server proxy check list.](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**Checklist: Setting Up a federation server proxy**

| Task | Reference |
| --- | --- |
| Before you begin deploying your AD FS federation server proxies, review the AD FS deployment topology types and their associated server placement and network layout recommendations. | ![Icon for the Determine Your AD FS Deployment Topology link you can use in reference to setting up a federation proxy server.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Determine Your AD FS Deployment Topology](../design/determine-your-ad-fs-deployment-topology)<br>![Icon for the Planning Federation Server Proxy Placement link you can use in reference to setting up a federation proxy server.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Planning Federation Server Proxy Placement](../design/planning-federation-server-proxy-placement)<br><br>![Icon for the Where to Place a Federation Server Proxy link you can use in reference to setting up a federation proxy server.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Where to Place a Federation Server Proxy](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807048%28v=ws.11%29) |
| Review AD FS capacity planning guidance to determine the proper number of federation server proxies you should use in your production environment. | ![Icon for the Planning for Federation Server Proxy Capacity link you can use in reference to setting up a federation proxy server.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Planning for Federation Server Proxy Capacity](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/gg749898%28v=ws.11%29) |
| Determine whether a single federation server proxy or a federation server proxy farm is better for your deployment. **Note:** Federation servers also perform federation server proxy responsibilities. | ![Icon for the When to Create a Federation Server Proxy link you can use in reference to setting up a federation proxy server.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[When to Create a Federation Server Proxy](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807032%28v=ws.11%29)<br>![Icon for the When to Create a Federation Server Proxy Farm link you can use in reference to setting up a federation proxy server.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[When to Create a Federation Server Proxy Farm](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807082%28v=ws.11%29) |
| Determine whether this new federation server proxy will be created in the perimeter network of the account partner organization or the resource partner organization. | ![Icon for the Review the Role of the Federation Server Proxy in the Account Partner link you can use in reference to setting up a federation proxy server.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Review the Role of the Federation Server Proxy in the Account Partner](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807109%28v=ws.11%29)<br>![Icon for the Review the Role of the Federation Server Proxy in the Resource Partner link you can use in reference to setting up a federation proxy server.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Review the Role of the Federation Server Proxy in the Resource Partner](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807052%28v=ws.11%29) |
| Before you install AD FS on a computer that will become a federation server proxy, read about the importance of obtaining a server authentication certificate—for federation server proxy farms—adding or sharing certificates across all the servers in a farm. | ![Icon for the Certificate Requirements for Federation Server Proxies link you can use in reference to setting up a federation proxy server.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Certificate Requirements for Federation Server Proxies](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807054%28v=ws.11%29) |
| Review information in the AD FS Design Guide about how to update Domain Name System (DNS) in the perimeter network so that successful name resolution for federation servers and federation server proxies can occur. | ![Icon for the Name Resolution Requirements for Federation Server Proxies link you can use in reference to setting up a federation proxy server.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Name Resolution Requirements for Federation Server Proxies](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807055%28v=ws.11%29) |
| Determine whether the federation server proxy must be joined to a domain. Although federation server proxies do not have to be joined to a domain, they are easier to manage with remote administration and Group Policy features when they are joined to a domain. | ![Icon for the Join a Computer to a Domain link you can use in reference to setting up a federation proxy server.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Join a Computer to a Domain](../../ad-ds/manage/join-computer-to-domain) |
| Depending on how the DNS infrastructure in your perimeter network is configured, complete one of the procedures in the topics on the right before you deploy a federation server proxy in your organization. **Note:** Do not perform both procedures. Read [Name Resolution Requirements for Federation Server Proxies](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807055%28v=ws.11%29) to determine which procedure best suits the requirements of your organization. | ![Icon for the Configure Name Resolution for a Federation Server Proxy in a DNS Zone That Serves Only the Perimeter Network link you can use in reference to setting up a federation proxy server.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Configure Name Resolution for a Federation Server Proxy in a DNS Zone That Serves Only the Perimeter Network](configure-name-resolution-for-federation-server-proxy-in-dns-zone-serving-only-perimeter-network)<br>![Icon for the Configure Name Resolution for a Federation Server Proxy in a DNS Zone That Serves Both the Perimeter Network and Internet Clients link you can use in reference to setting up a federation proxy server.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Configure Name Resolution for a Federation Server Proxy in a DNS Zone That Serves Both the Perimeter Network and Internet Clients](configure-name-resolution-for-federation-server-proxy-in-dns-zone-serving-only-perimeter-network) |
| After you obtain a server authentication certificate, you must install it in Internet Information Services (IIS) on the default Web site of the federation server proxy. | ![Icon for the Import a Server Authentication Certificate to the Default Web Site link you can use in reference to setting up a federation proxy server.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Import a Server Authentication Certificate to the Default Web Site](import-a-server-authentication-certificate-to-the-default-web-site) |
| (Optional) As an alternative to obtaining a server authentication certificate from a certification authority (CA), you can use IIS to acquire a sample certificate for your federation server proxy.<br>Because IIS generates a self-signed certificate that does not originate from a trusted source, use it to create a self-signed certificate only in the following scenarios:<br><br>- When you have to create a Secure Sockets Layer (SSL) channel between your server and a limited, known group of users- When you have to troubleshoot third-party certificate problems **Caution:** It is not a security best practice to deploy a federation server proxy in a production environment using a self-signed, server authentication certificate. | ![Icon for the IIS: Create a Self-Signed Server Certificate link you can use in reference to setting up a federation proxy server.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[IIS: Create a Self-Signed Server Certificate](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753127%28v=ws.10%29) |
| Install the Federation Service Proxy role service on the computer that will become the federation server proxy. | ![Icon for the Install the Federation Service Proxy Role Service link you can use in reference to setting up a federation proxy server.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Install the Federation Service Proxy Role Service](install-the-federation-service-proxy-role-service) |
| Configure the AD FS software on the computer to act in the federation server proxy role by using the AD FS Federation Server Proxy Configuration Wizard. | ![Icon for the Configure a Computer for the Federation Server Proxy Role link you can use in reference to setting up a federation proxy server.](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Configure a Computer for the Federation Server Proxy Role](configure-a-computer-for-the-federation-server-proxy-role) |
| Using Event Viewer, verify that the federation server proxy service has started. | ![setting up a federated proxy server](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Verify That a Federation Server Proxy Is Operational](verify-that-a-federation-server-proxy-is-operational) |