---
layout: Conceptual
title: Appendix A - Reviewing Key AD DS Terms | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/appendix-a--reviewing-key-ad-ds-terms
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Appendix A: Reviewing Key AD DS Terms'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: glossary
locale: en-us
document_id: 68195515-af70-da81-05f1-40868b941000
document_version_independent_id: d38780b7-77e0-091d-9901-1ff62d936f3f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/plan/Appendix-A--Reviewing-Key-AD-DS-Terms.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/plan/appendix-a--reviewing-key-ad-ds-terms
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/plan/Appendix-A--Reviewing-Key-AD-DS-Terms.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 525e1663-d2af-abbf-0da9-3dc099049bdc
---

# Appendix A - Reviewing Key AD DS Terms | Microsoft Learn

The following terms are relevant to the deployment process for Windows Server 2008 Active Directory Domain Services (AD DS).

## Active Directory domain

An administrative unit in a computer network that, for management convenience, groups several capabilities, including the following:

- **Network-wide user identity**. In domains, user identities can be created once and then referenced on any computer that is joined to the forest in which the domain is located. Domain controllers that make up a domain store user accounts and user credentials, such as passwords or certificates, securely.
- **Authentication**. Domain controllers provide authentication services for users. They also supply additional authorization data, such as user group memberships. Administrators can use these services to control access to resources on the network.
- **Trust relationships**. Domains extend authentication services to users in other domains in their own forest by means of automatic bidirectional trusts. Domains also extend authentication services to users in domains in other forests by means of either forest trusts or manually created external trusts.
- **Policy administration**. A domain is a scope of administrative policies, such as password complexity and password reuse rules.
- **Replication**. A domain defines a partition of the directory tree that provides data that is adequate to provide required services and that is replicated between domain controllers. In this way, all domain controllers are peers in a domain, and they are managed as a unit.

## Active Directory forest

A collection of one or more Active Directory domains that share a common logical structure, directory schema, and network configuration, as well as automatic, two-way, transitive trust relationships. Each forest is a single instance of the directory, and it defines a security boundary.

## Active Directory functional level

An AD DS setting that enables advanced domain-wide or forest-wide AD DS features.

## Migration

The process of moving an object from a source domain to a target domain, while preserving or modifying characteristics of the object to make it accessible in the new domain.

## Domain restructure

A migration process that involves changing the domain structure of a forest. A domain restructure can involve either the consolidation or the addition of domains, and it can take place between forests or within a forest.

## Domain consolidation

A restructuring process that involves eliminating AD DS domains by merging their contents with the contents of other domains.

## Domain upgrade

The process of upgrading the directory service of a domain to a later version of the directory service. This includes upgrading the operating system on all domain controllers and raising the AD DS functional level where applicable.

## In-place domain upgrade

The process of upgrading the operating systems of all domain controllers in a given domain, for example, upgrading Windows Server 2003 to Windows Server 2008 , and raising the functional level of the domain, if applicable, while leaving domain objects, such as users and groups, in place.

## Forest root domain

The first domain that is created in the Active Directory forest. This domain is automatically designated as the forest root domain. It provides the foundation for the Active Directory forest infrastructure.

## Regional domain

A child domain that is created in a geographic region to optimize replication traffic.