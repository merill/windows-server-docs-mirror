---
layout: Conceptual
title: Selecting the Forest Root Domain | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/selecting-the-forest-root-domain
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Selecting the Forest Root Domain'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 83d759d6-1086-3c3c-a6fe-c5e6c3edbef2
document_version_independent_id: ae4cd61b-2fc0-fac3-d212-d5917fe4e37f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Selecting-the-Forest-Root-Domain.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/selecting-the-forest-root-domain
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Selecting-the-Forest-Root-Domain.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 7b28feaf-8b87-27ce-5472-4fd38abf9e43
---

# Selecting the Forest Root Domain | Microsoft Learn

The first domain that you deploy in an Active Directory forest is called the forest root domain. This domain remains the forest root domain for the life cycle of the AD DS deployment.

The forest root domain contains the Enterprise Admins and Schema Admins groups. These service administrator groups are used to manage forest-level operations such as the addition and removal of domains and the implementation of changes to the schema.

Selecting the forest root domain involves determining if one of the Active Directory domains in your domain design can function as the forest root domain or if you need to deploy a dedicated forest root domain.

For information about deploying a forest root domain, see [Deploying a Windows Server 2008 Forest Root Domain](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731174%28v=ws.10%29).

## Choosing a regional or dedicated forest root domain

If you are applying a single domain model, the single domain functions as the forest root domain. If you are applying a multiple domain model, you can choose to deploy a dedicated forest root domain or select a regional domain to function as the forest root domain.

### Dedicated forest root domain

A dedicated forest root domain is a domain that is created specifically to function as the forest root. It does not contain any user accounts other than the service administrator accounts for the forest root domain. Also, it does not represent any geographical region in your domain structure. All other domains in the forest are children of the dedicated forest root domain.

Using a dedicated forest root provides the following advantages:

- Operational separation of forest service administrators from domain service administrators. In a single domain environment, members of the Domain Admins and built-in Administrators groups can use standard tools and procedures to make themselves members of the Enterprise Admins and Schema Admins groups. In a forest that uses a dedicated forest root domain, members of the Domain Admins and built-in Administrators groups in the regional domains cannot make themselves members of the forest-level service administrator groups by using standard tools and procedures.
- Protection from operational changes in other domains. A dedicated forest root domain does not represent a particular geographical region in your domain structure. For this reason, it is not affected by reorganizations or other changes that result in the renaming or restructuring of domains.
- Serves as a neutral root so that no country or region appears to be subordinate to another region. Some organizations might prefer to avoid the appearance that one country or region is subordinate to another country or region in the namespace. When you use a dedicated forest root domain, all regional domains can be peers in the domain hierarchy.

In a multiple-regional-domain environment in which a dedicated forest root is used, the replication of the forest root domain has minimal impact on the network infrastructure. This is because the forest root only hosts the service administrator accounts. The majority of the user accounts in the forest and other domain-specific data are stored in the regional domains.

One disadvantage to using a dedicated forest root domain is that it creates additional management overhead to support the additional domain.

### Regional domain as a forest root domain

If you choose not to deploy a dedicated forest root domain, you must select a regional domain to function as the forest root domain. This domain is the parent domain of all of the other regional domains and will be the first domain that you deploy. The forest root domain contains user accounts and is managed in the same way that the other regional domains are managed. The primary difference is that it also includes the Enterprise Admins and Schema Admins groups.

The advantage of selecting a regional domain to function as the forest root domain is that it does not create the additional management overhead that maintaining an additional domain creates. Select an appropriate regional domain to be the forest root, such as the domain that represents your headquarters or the region that has the fastest network connections. If it is difficult for your organization to select a regional domain to be the forest root domain, you can choose to use a dedicated forest root model instead.

## Assigning the forest root domain name

The forest root domain name is also the name of the forest. The forest root name is a Domain Name System (DNS) name that consists of a prefix and a suffix in the form of prefix.suffix. For example, an organization might have the forest root name corp.contoso.com. In this example, corp is the prefix and contoso.com is the suffix.

Select the suffix from a list of existing names on your network. For the prefix, select a new name that has not been used on your network previously. By attaching a new prefix to an existing suffix, you create a unique namespace. Creating a new namespace for Active Directory Domain Services (AD DS) ensures that any existing DNS infrastructure does not need to be modified to accommodate AD DS.

### Selecting a suffix

To select a suffix for the forest root domain:

1. Contact the DNS owner for the organization for a list of registered DNS suffixes that are in use on the network that will host AD DS. Note that the suffixes used on the internal network might be different than the suffixes used externally. For example, an organization might use contosopharma.com on the Internet and contoso.com on the internal corporate network.
2. Consult the DNS owner to select a suffix for use with AD DS. If no suitable suffixes exist, register a new name with an Internet naming authority.

We recommend that you use DNS names that are registered with an Internet authority in the Active Directory namespace. Only registered names are guaranteed to be globally unique. If another organization later registers the same DNS domain name (or if your organization merges with, acquires, or is acquired by another company that uses the same DNS name), the two infrastructures cannot interact with one another.

Caution

Do not use single-label DNS names. For more information, see [Deployment and operation of Active Directory domains that are configured by using single-label DNS names](https://support.microsoft.com/help/300684/). Also, we do not recommend using unregistered suffixes, such as .local .

### Selecting a prefix

If you chose a registered suffix that is already in use on the network, select a prefix for the forest root domain name by using the prefix rules in the table below. Add a prefix that is not currently in use to create a new subordinate name. For example, if your DNS root name is contoso.com, you can create the Active Directory forest root domain name concorp.contoso.com if the namespace concorp.contoso.com is not already in use on the network. This new branch of the namespace will be dedicated to AD DS and can be integrated easily with the existing DNS implementation.

If you selected a regional domain to function as a forest root domain, you might need to select a new prefix for the domain. Because the forest root domain name affects all of the other domain names in the forest, a regionally based name might not be appropriate. If you are using a new suffix that is not currently in use on the network, you can use it as the forest root domain name without choosing an additional prefix.

The following table lists the rules for selecting a prefix for a registered DNS name.

| Rule | Explanation |
| --- | --- |
| Select a prefix that is not likely to become outdated. | Avoid names such as a product line or operating system that might change in the future. We recommend using generic names such as corp or ds. |
| Select a prefix that includes Internet standard characters only. | A-Z, a-z, 0-9, and (-), but not entirely numerical. |
| Include 15 characters or fewer in the prefix. | If you choose a prefix length of 15 characters or less, the NetBIOS name is the same as the prefix. |

It is important for the Active Directory DNS owner to work with the DNS owner for the organization to obtain ownership of the name that will be used for the Active Directory namespace. For more information about designing a DNS infrastructure to support AD DS, see [Creating a DNS Infrastructure Design](creating-a-dns-infrastructure-design).

## Documenting the forest root domain name

Document the DNS prefix and suffix that you select for the forest root domain. At this point, identify what domain will be the forest root. You can add the forest root domain name information to the "Domain Planning" worksheet that you created to document your plan for new and upgraded domains and your domain names. To open it, download Job\_Aids\_Designing\_and\_Deploying\_Directory\_and\_Security\_Services.zip from [Job Aids for Windows Server 2003 Deployment Kit](https://microsoft.com/download/details.aspx?id=9608) and open "Domain Planning" (DSSLOGI\_5.doc).