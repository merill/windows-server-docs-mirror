---
layout: Conceptual
title: Stand-Alone Federation Server Using WID | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/design/stand-alone-federation-server-using-wid
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Stand-Alone Federation Server Using WID'
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: aa96ed19-016a-c593-699d-18f6bff4c92e
document_version_independent_id: 8da91ed5-4cc3-12cc-8e87-18b0954ee0a5
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/design/Stand-Alone-Federation-Server-Using-WID.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/design/stand-alone-federation-server-using-wid
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/design/Stand-Alone-Federation-Server-Using-WID.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b356b5a7-e423-53e1-a7d0-7a17e3164765
---

# Stand-Alone Federation Server Using WID | Microsoft Learn

A stand-alone federation server in Active Directory Federation Services (AD FS) consists of a single server that hosts a Federation Service configured to use the Windows Internal Database (WID). This AD FS topology is for test labs. We do not recommend it for production environments because it has a limit of only one federation server, and it cannot be used to scale up to more servers.

If you want to add additional federation servers to your test lab, you must rebuild the Federation Service from scratch by deploying any of the other topologies mentioned later in this section. Therefore, we recommend that you use this topology for a test lab or a proof-of-concept environment in your private testing network in which a single federation server is adequate, as shown in the following illustration.

![server using WID](media/fedserverwid.gif)

## Test lab considerations

This section describes various considerations about the intended audience, benefits, and limitations that are associated with this topology for test lab environments.

### Who should use this topology?

- Information technology (IT) professionals or IT architects who want to evaluate or develop a proof of concept for this technology

### What are the benefits of using this topology?

- Easy to set up in a test lab environment

### What are the limitations of using this topology?

- Only one federation server per Federation Service (no capability to scale up to a farm)
- Not redundant (only a single instance of the AD FS configuration database exists)