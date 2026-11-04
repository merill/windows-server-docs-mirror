---
layout: Conceptual
title: Post-Deployment Steps for Network Controller | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/sdn/technologies/network-controller/post-deploy-steps-nc
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: sdn
ms.update-cycle: 1095-days
description: This topic provides certificate configuration instructions for non-Kerberos deployments of Network Controller in Windows Server 2019 and 2016 Datacenter.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2021-10-28T00:00:00.0000000Z
locale: en-us
document_id: 8406cdfe-7175-9466-7f7a-ed7c9dbc8230
document_version_independent_id: b05bf981-368d-dfc3-6c73-5d5768edc284
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/sdn/technologies/network-controller/post-deploy-steps-nc.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/sdn/technologies/network-controller/post-deploy-steps-nc
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/sdn/technologies/network-controller/post-deploy-steps-nc.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: fa916d3d-5467-adb5-ff0d-1e4dec377ead
---

# Post-Deployment Steps for Network Controller | Microsoft Learn

When you install Network Controller, you can choose Kerberos or non-Kerberos deployments.

For non-Kerberos deployments, you must configure certificates.

## Configure certificates for non-Kerberos deployments

If the computers or virtual machines (VMs) for Network Controller and the management client are not domain-joined, you must configure certificate-based authentication by completing the following steps.

- Create a certificate on the Network Controller for Computer authentication. The certificate subject name must be same as the DNS name of the Network Controller computer or VM.
- Create a certificate on the management client. This certificate must be trusted by the Network Controller.
- Enroll a certificate on the Network Controller computer or VM. The certificate must meet the following requirements.

    - Both the Server Authentication purpose and the Client Authentication purpose must be configured in Enhanced Key Usage (EKU) or Application Policies extensions. The object identifier for Server Authentication is 1.3.6.1.5.5.7.3.1. The object identifier for Client Authentication is 1.3.6.1.5.5.7.3.2.
    - The certificate subject name should resolve to:

        - The IP address of the Network Controller computer or VM, if Network Controller is deployed on a single computer or VM.
        - The REST IP address, if Network Controller is deployed on multiple computers, multiple VMs, or both.
    - This certificate must be trusted by all the REST clients. The certificate must also be trusted by the Software Load Balancing (SLB) Multiplexer (MUX) and the southbound host computers that are managed by Network Controller.
    - The certificate can be enrolled by a Certification Authority (CA) or can be a self-signed certificate. Self-signed certificates are not recommended for production deployments, but are acceptable for test lab environments.
    - The same certificate must be provisioned on all the Network Controller nodes. After creating the certificate on one node, you can export the certificate (with private key) and import it on the other nodes.

For more information, see [Network Controller](/en-us/azure/azure-local/concepts/network-controller-overview?context=/windows-server/context/windows-server-edge-networking).