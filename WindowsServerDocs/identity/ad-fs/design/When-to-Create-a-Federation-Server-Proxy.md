---
layout: Conceptual
title: When to Create a Federation Server Proxy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/when-to-create-a-federation-server-proxy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: When to Create a Federation Server Proxy'
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: da507e2f-d09e-2e25-90cf-808c6430821f
document_version_independent_id: c904fdff-c630-cf5b-2883-7cf8d6e2a7b6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/When-to-Create-a-Federation-Server-Proxy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/when-to-create-a-federation-server-proxy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/When-to-Create-a-Federation-Server-Proxy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ae083026-ee76-ebba-8ac0-fc4bd0b3f593
---

# When to Create a Federation Server Proxy | Microsoft Learn

Creating a federation server proxy in your organization adds additional security layers to your Active Directory Federation Services (AD FS) deployment. Consider deploying a federation server proxy in your organization's perimeter network when you want to:

- Prevent external client computers from directly accessing your federation servers. By deploying a federation server proxy in your perimeter network, you effectively isolate your federation servers so that they can be accessed only by client computers that are logged in to the corporate network through federation server proxies, which act on behalf of the external client computers. Federation server proxies do not have access to the private keys that are used to produce tokens. For more information, see [Where to Place a Federation Server Proxy](where-to-place-a-federation-server-proxy).
- Provide a convenient way to differentiate the sign-in experience for users who are coming from the Internet as opposed to users who are coming from your corporate network using Windows Integrated Authentication. A federation server proxy collects credentials or home realm details from Internet client computers by using the logon, logout, and identity provider discovery (homerealmdiscovery.aspx) pages that are stored on the federation server proxy.

    In contrast, client computers that come from the corporate network encounter a different experience, based on the configuration of the federation server. The corporate network federation server is often configured for Windows Integrated Authentication, which provides a seamless sign-in experience for users on the corporate network.

The role that a federation server proxy plays in your organization depends on whether you place the federation server proxy in the account partner organization or in the resource partner organization. For example, when a federation server proxy is placed in the perimeter network of the account partner, its role is to collect the user credential information from browser clients. When a federation server proxy is placed in the perimeter network of the resource partner, it relays security token requests to a resource federation server and produces organizational security tokens in response to the security tokens that are provided by its account partners.

For more information, see [Review the Role of the Federation Server Proxy in the Account Partner](review-the-role-of-the-federation-server-proxy-in-the-account-partner) and [Review the Role of the Federation Server Proxy in the Resource Partner](review-the-role-of-the-federation-server-proxy-in-the-resource-partner)

## How to create a federation server proxy

You can create a federation server proxy using either the AD FS Federation Server Proxy Configuration Wizard or the Fsconfig.exe command-line tool. For instructions about how to do this, see [Configure a Computer for the Federation Server Proxy Role](../deployment/configure-a-computer-for-the-federation-server-proxy-role).

For general information about how to set up all the prerequisites necessary to deploy a federation server proxy, see [Checklist: Setting Up a Federation Server Proxy](../deployment/checklist--setting-up-a-federation-server-proxy).