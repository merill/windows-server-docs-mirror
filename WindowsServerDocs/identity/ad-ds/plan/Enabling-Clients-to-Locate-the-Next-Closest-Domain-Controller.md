---
layout: Conceptual
title: Enabling Clients to Locate the Next Closest Domain Controller | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/enabling-clients-to-locate-the-next-closest-domain-controller
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Enabling Clients to Locate the Next Closest Domain Controller'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: b67d10d5-54b0-51c8-32d1-e7aa6af32b42
document_version_independent_id: 999728d8-6d5e-3444-fa4d-baddaf51d588
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Enabling-Clients-to-Locate-the-Next-Closest-Domain-Controller.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/enabling-clients-to-locate-the-next-closest-domain-controller
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Enabling-Clients-to-Locate-the-Next-Closest-Domain-Controller.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: db8cd446-75b4-a0e0-1ab8-e9088fca7d66
---

# Enabling Clients to Locate the Next Closest Domain Controller | Microsoft Learn

If you have a domain controller that runs Windows Server 2008 or newer, you can make it possible for client computers that run Windows Vista or newer or Windows Server 2008 or newer to locate domain controllers more efficiently by enabling the **Try Next Closest Site** Group Policy setting. This setting improves the Domain Controller Locator (DC Locator) by helping to streamline network traffic, especially in large enterprises that have many branch offices and sites.

This new setting can affect how you configure site link costs because it affects the order in which domain controllers are located. For enterprises that have many hub sites and branch offices, you can significantly reduce Active Directory traffic on the network by ensuring that clients fail over to the next closest hub site when they cannot find a domain controller in the closest hub site.

As a general best practice, you should simplify your site topology and site link costs as much as possible if you enable the **Try Next Closest Site** setting. In enterprises with many hub sites, this can simplify any plans that you make for handling situations in which clients in one site need to fail over to a domain controller in another site.

By default, the **Try Next Closest Site** setting is not enabled. When the setting is not enabled, DC Locator uses the following algorithm to locate a domain controller:

- Try to find a domain controller in the same site.
- If no domain controller is available in the same site, try to find any domain controller in the domain.

Note

This is the same algorithm that DC Locator used in previous versions of Active Directory. For more information, see the article [How DNS Support for Active Directory Works](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc759550%28v=ws.10%29).

If you enable the **Try Next Closest Site** setting, DC Locator uses the following algorithm to locate a domain controller:

- Try to find a domain controller in the same site.
- If no domain controller is available in the same site, try to find a domain controller in the next closest site. A site is closer if it has a lower site-link cost than another site with a higher site-link cost.
- If no domain controller is available in the next closest site, try to find any domain controller in the domain.

The **Try Next Closest Site** setting works in coordination with automatic site coverage. For example, if the next closest site has no domain controller, DC Locator tries to find the domain controller that performs automatic site coverage for that site.

By default, DC Locator does not consider any site that contains a read-only domain controller (RODC) when it determines the next closest site. In addition, when the client gets a response from a domain controller that runs a version earlier than Windows Server 2008, the DC Locator behavior is the same as when then setting is not enabled.

For example, assume that a site topology has four sites with the site link values in the following illustration. In this example, all the domain controllers are writable domain controllers that run Windows Server 2008 or newer.

![enabling clients to locate dc](media/enabling-clients-to-locate-the-next-closest-domain-controller/beff4087-fb2a-463b-96ac-d440a9e29b75.gif)

When the **Try Next Closest Site** Group Policy setting is enabled in this example, if a client computer in Site\_B tries to locate a domain controller, it first tries to find a domain controller in its own Site\_B. If none is available in Site\_B, it tries to find a domain controller in Site\_A.

If the setting is not enabled, the client tries to find a domain controller in Site\_A, Site\_C, or Site\_D if no domain controller is available in Site\_B.

Note

The **Try Next Closest Site** setting works in coordination with automatic site coverage. For example, if the next closest site has no domain controller, DC Locator tries to find the domain controller that performs automatic site coverage for that site.

To apply the **Try Next Closest Site** setting, you can create a Group Policy object (GPO) and link it to the appropriate object for your organization, or you can modify the Default Domain Policy to have it affect all clients that run Windows Vista or newer and Windows Server 2008 or newer in the domain. For more information about how to set the **Try Next Closest Site** setting, see [Enable Clients to Locate a Domain Controller in the Next Closest Site](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc772592%28v=ws.10%29).