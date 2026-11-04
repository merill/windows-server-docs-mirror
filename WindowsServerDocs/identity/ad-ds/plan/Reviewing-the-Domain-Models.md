---
layout: Conceptual
title: Reviewing the Domain Models | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/reviewing-the-domain-models
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Reviewing the Domain Models'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 2c190e3e-ccc9-6d51-8c49-25b99876d027
document_version_independent_id: 28e80b2b-517d-7aa4-d5ef-ff401bab5c45
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Reviewing-the-Domain-Models.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/reviewing-the-domain-models
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Reviewing-the-Domain-Models.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 52ec84c4-7ff7-d31b-5cbc-71b8669cc6df
---

# Reviewing the Domain Models | Microsoft Learn

The following factors impact the domain design model that you select:

- Amount of available capacity on your network that you are willing to allocate to Active Directory Domain Services (AD DS). The goal is to select a model that provides efficient replication of information with minimal impact on available network bandwidth.
- Number of users in your organization. If your organization includes a large number of users, deploying more than one domain enables you to partition your data and gives you more control over the amount of replication traffic that will pass through a given network connection. This makes it possible for you to control where data is replicated and reduce the load created by replication traffic on slow links in your network.

The simplest domain design is a single domain. In a single domain design, all information is replicated to all of the domain controllers. If necessary, however, you can deploy additional regional domains. This might occur if portions of the network infrastructure are connected by slow links, and the forest owner wants to be sure that replication traffic does not exceed the capacity that has been allocated to AD DS.

It is best to minimize the number of domains that you deploy in your forest. This reduces the overall complexity of the deployment and, as a result, reduces total cost of ownership. The following table lists the administrative costs associated with adding regional domains.

| Cost | Implications |
| --- | --- |
| Management of multiple service administrator groups | Each domain has its own service administrator groups that need to be managed independently. The membership of these service administrator groups must be carefully controlled. |
| Maintaining consistency among Group Policy settings that are common to multiple domains | Group Policy settings that need to be applied forest-wide must be applied separately to each individual domain in the forest. |
| Maintaining consistency among access control and auditing settings that are common to multiple domains | Access control and auditing settings that need to be applied across the forest must be applied separately to each individual domain in the forest. |
| Increased likelihood of objects moving between domains | The greater the number of domains, the greater the likelihood that users will need to move from one domain to another. This move can potentially impact end users. |

Note

Windows Server fine-grained password and account lockout policies can also impact the domain design model that you select. Before this release of Windows Server 2008, you could apply only one password and account lockout policy, which is specified in the domain Default Domain Policy, to all users in the domain. As a result, if you wanted different password and account lockout settings for different sets of users, you had to either create a password filter or deploy multiple domains. You can now use fine-grained password policies to specify multiple password policies and to apply different password restrictions and account lockout policies to different sets of users within a single domain. For more information about fine-grained password and account lockout policies, see the article [AD DS Fine-Grained Password and Account Lockout Policy Step-by-Step Guide](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc770842%28v=ws.10%29).

## Single domain model

A single domain model is the easiest to administer and the least expensive to maintain. It consists of a forest that contains a single domain. This domain is the forest root domain, and it contains all of the user and group accounts in the forest.

A single domain forest model reduces administrative complexity by providing the following advantages:

- Any domain controller can authenticate any user in the forest.
- All domain controllers can be global catalogs, so you do not need to plan for global catalog server placement.

In a single domain forest, all directory data is replicated to all geographic locations that host domain controllers. While this model is the easiest to manage, it also creates the most replication traffic of the two domain models. Partitioning the directory into multiple domains limits the replication of objects to specific geographic regions but results in more administrative overhead.

## Regional domain model

All object data within a domain is replicated to all domain controllers in that domain. For this reason, if your forest includes a large number of users that are distributed across different geographic locations connected by a wide area network (WAN), you might need to deploy regional domains to reduce replication traffic over the WAN links. Geographically based regional domains can be organized according to network WAN connectivity.

The regional domain model enables you to maintain a stable environment over time. Base the regions used to define domains in your model on stable elements, such as continental boundaries. Domains based on other factors, such as groups within the organization, can change frequently and might require you to restructure your environment.

The regional domain model consists of a forest root domain and one or more regional domains. Creating a regional domain model design involves identifying what domain is the forest root domain and determining the number of additional domains that are required to meet your replication requirements. If your organization includes groups that require data isolation or service isolation from other groups in the organization, create a separate forest for these groups. Domains do not provide data isolation or service isolation.