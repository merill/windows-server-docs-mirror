---
layout: Conceptual
title: Manage Resources in Multiple Active Directory Forests | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/ipam/manage-resources-in-multiple-active-directory-forests
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Learn how to use IPAM to manage domain controllers, DHCP servers, and DNS servers in multiple Active Directory forests.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: dd7cb4d7-d5b8-ed2c-06dd-d3da871abb23
document_version_independent_id: b5e8ead8-18f1-06a5-043b-27162380f69e
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/ipam/Manage-Resources-in-Multiple-Active-Directory-Forests.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/ipam/manage-resources-in-multiple-active-directory-forests
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/ipam/Manage-Resources-in-Multiple-Active-Directory-Forests.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d9c4221d-9e4e-c734-7400-290103b9c751
---

# Manage Resources in Multiple Active Directory Forests | Microsoft Learn

You can use this topic to learn how to use IPAM to manage domain controllers, DHCP servers, and DNS servers in multiple Active Directory forests.

To use IPAM to manage resources in remote Active Directory forests, each forest that you want to manage must have a two way trust with the forest where IPAM is installed.

To start the discovery process for different Active Directory forests, open Server Manager and click IPAM. In the IPAM client console, click **Configure Server Discovery**, and then click **Get forests**. This initiates a background task that discovers trusted forests and their domains. After the discovery process completes, click **Configure Server Discovery**, which opens the following dialog box.

![Configure Server Discovery](../../media/manage-resources-in-multiple-active-directory-forests/ipam_serverdiscovery.jpg)

Note

For Group Policy-based provisioning for an Active Directory Cross Forest scenario, ensure that you run the following Windows PowerShell cmdlet on the IPAM server and not on the trusting domain DCs. As an example, if your IPAM server is joined to the forest corp.contoso.com and the trusting forest is fabrikam.com, you can run the following Windows PowerShell cmdlet on the IPAM server in corp.contoso.com for Group Policy-based provisioning on the fabrikam.com forest. To run this cmdlet, you must be a member of the Domain Admins group in the fabrikam.com forest.

```powershell
    Invoke-IpamGpoProvisioning -Domain fabrikam.COM -GpoPrefixName IPAMSERVER -IpamServerFqdn IPAM.CORP.CONTOSO.COM
```

In the **Configure Server Discovery** dialog box, click **Select the forest**, and then choose the forest that you want to manage with IPAM. Also select the domains that you want to manage, and then click **Add**.

In **Select the server roles to discover**, for each domain that you want to manage, specify the type of servers to discover. The options are **Domain controller**, **DHCP server**, and **DNS server**.

By default, domain controllers, DHCP servers, and DNS servers are discovered - so if you do not want to discover one of these types of servers, ensure that you deselect the checkbox for that option.

In the example illustration above, the IPAM server is installed in the contoso.com forest, and the root domain of the fabrikam.com forest is added for IPAM management. The selected server roles allow IPAM to discover and manage domain controllers, DHCP servers, and DNS servers in the fabrikam.com root domain and the contoso.com root domain.

After you have specified forests, domains, and server roles, click **OK**. IPAM performs discovery, and when discovery completes, you can manage resources in both the local and remote forest.