---
layout: Conceptual
title: Configure DNS forwarding and domain trust | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-configure-dns-forwarding-and-trust
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Configure DNS forwarding in the HGS domain and a one-way trust with the fabric domain'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: 3b4f38e7-9548-ae7d-04ea-88423ab26caf
document_version_independent_id: 09a30788-4fa9-01b0-913c-085e8b7656e1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configure-dns-forwarding-and-trust.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-configure-dns-forwarding-and-trust
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-configure-dns-forwarding-and-trust.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: dcaf6c29-0028-a20c-6866-12c618398c4d
---

# Configure DNS forwarding and domain trust | Microsoft Learn

Important

AD mode is deprecated beginning with Windows Server 2019. For environments where TPM attestation is not possible, configure [host key attestation](guarded-fabric-initialize-hgs-key-mode). Host key attestation provides similar assurance to AD mode and is simpler to set up.

Use the following steps to set up DNS forwarding and establish a one-way trust with the fabric domain. These steps allow the HGS to locate the fabric domain controllers and validate group membership of the Hyper-V hosts.

1. Run the following command in an elevated PowerShell session to configure DNS forwarding. Replace fabrikam.com with the name of the fabric domain and type the IP addresses of DNS servers in the fabric domain. For higher availability, point to more than one DNS server.

    ```powershell
    Add-DnsServerConditionalForwarderZone -Name "fabrikam.com" -ReplicationScope "Forest" -MasterServers <DNSserverAddress1>, <DNSserverAddress2>
    ```
2. To create a one-way forest trust, run the following command in an elevated Command Prompt:

    Replace `bastion.local` with the name of the HGS domain and `fabrikam.com` with the name of the fabric domain. Provide the password for an admin of the fabric domain.

    ```powershell
    netdom trust bastion.local /domain:fabrikam.com /userD:fabrikam.com\Administrator /passwordD:<password> /add
    ```