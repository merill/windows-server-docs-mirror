---
layout: Conceptual
title: Integrating AD DS into an Existing DNS Infrastructure | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/integrating-ad-ds-into-an-existing-dns-infrastructure
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Integrating AD DS into an Existing DNS Infrastructure'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: best-practice
locale: en-us
document_id: 6f711107-a801-e7f9-00d8-2d225261c22f
document_version_independent_id: eaca64d1-be05-58f1-06b8-e78497e4f5a9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Integrating-AD-DS-into-an-Existing-DNS-Infrastructure.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/integrating-ad-ds-into-an-existing-dns-infrastructure
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Integrating-AD-DS-into-an-Existing-DNS-Infrastructure.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 87166687-4ff2-37a3-54ce-67fbb5dadddf
---

# Integrating AD DS into an Existing DNS Infrastructure | Microsoft Learn

If your organization already has an existing Domain Name System (DNS) Server service, the DNS for Active Directory Domain Services (AD DS) owner must work with the DNS owner for your organization to integrate AD DS into the existing infrastructure. This involves creating a DNS server and DNS client configuration.

## Creating a DNS server configuration

When integrating AD DS with an existing DNS namespace, we recommend that you do the following:

- Install the DNS Server service on every domain controller in the forest. This provides fault tolerance if one of the DNS servers is unavailable. In this way, domain controllers don't need to rely on other DNS servers for name resolution. This also simplifies the management environment because all domain controllers have a uniform configuration.
- Configure the Active Directory forest root domain controller to host the DNS zone for the Active Directory forest.
- Configure the domain controllers for each regional domain to host the DNS zones that correspond to their Active Directory domains.
- Configure the zone containing the Active Directory forest-wide locator records (that is, the \_msdcs.*forestname* zone) to replicate to every DNS server in the forest by using the forest-wide DNS application directory partition.

    Note

    When the DNS Server service is installed with the Active Directory Domain Services Installation Wizard (we recommend this option), all the previous tasks are performed automatically. For more information, see [Deploying a Windows Server 2008 Forest Root Domain](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731174%28v=ws.10%29).

    Note

    AD DS uses forest-wide locator records to enable replication partners to find each other and to enable clients to find global catalog servers. AD DS stores the forest-wide locator records in the \_msdcs.*forestname* zone. Because the information in the zone must be widely available, this zone is replicated to all DNS servers in the forest by means of the forest-wide DNS application directory partition.

The existing DNS structure remains intact. You don't need to move any servers or zones. You simply need to create a delegation to your Active Directory-integrated DNS zones from your existing DNS hierarchy.

## Creating the DNS client configuration

To configure DNS on client computers, the DNS for AD DS owner must specify the computer naming scheme and how the clients locate DNS servers. The following table lists our recommended configurations for these design elements.

| Design element | Configuration |
| --- | --- |
| Computer naming | Use default naming. When a computer using a Windows operating system joins a domain, the computer assigns itself a fully qualified domain name (FQDN) that comprises the host name of the computer and the name of the Active Directory domain. |
| Client resolver configuration | Configure client computers to point to any DNS server on the network. |

Note

Active Directory clients and domain controllers can dynamically register their DNS names even if they are not pointing to the DNS server that is authoritative for their names.

A computer might have a different existing DNS name if the organization previously, statically registered the computer in DNS or if the organization previously deployed an integrated Dynamic Host Configuration Protocol (DHCP) solution. If your client computers already have a registered DNS name, when the domain to which they're joined is upgraded to Windows Server 2008 AD DS, they'll have two different names:

- The existing DNS name
- The new fully qualified domain name (FQDN)

Clients can still be located by either name. Any existing DNS, DHCP, or integrated DNS/DHCP solution is left intact. The new primary names are created automatically and updated with dynamic update. They're cleaned up automatically with scavenging.

If you want to take advantage of Kerberos authentication when connecting to a server running Windows 2000, Windows Server 2003, or Windows Server 2008, you must make sure that the client connects to the server by using the primary name.