---
layout: Conceptual
title: Create a security group for guarded hosts and register the group with HGS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-admin-trusted-attestation-creating-a-security-group
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Create a security group for guarded hosts and register the group with HGS'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2018-08-29T00:00:00.0000000Z
locale: en-us
document_id: 08a954cc-b264-0811-53f7-d3fb9cc5ad96
document_version_independent_id: 277f052a-4a75-4895-74d9-dc479398c8b7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-admin-trusted-attestation-creating-a-security-group.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-admin-trusted-attestation-creating-a-security-group
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-admin-trusted-attestation-creating-a-security-group.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: dbda5458-8ebe-6d71-918b-64f66fd5eda4
---

# Create a security group for guarded hosts and register the group with HGS | Microsoft Learn

Important

AD mode is deprecated beginning with Windows Server 2019. For environments where TPM attestation is not possible, configure [host key attestation](guarded-fabric-initialize-hgs-key-mode). Host key attestation provides similar assurance to AD mode and is simpler to set up.

This topic describes the intermediate steps to prepare Hyper-V hosts to become guarded hosts using Admin-trusted attestation (AD mode). Before taking these steps, complete the steps in [Configuring the fabric DNS for hosts that will become guarded hosts](guarded-fabric-configuring-fabric-dns-ad).

## Create a security group and add hosts

1. Create a new **GLOBAL** security group in the fabric domain and add Hyper-V hosts that will run shielded VMs. Restart the hosts to update their group membership.
2. Use Get-ADGroup to obtain the security identifier (SID) of the security group and provide it to the HGS administrator.

    ```powershell
    Get-ADGroup "Guarded Hosts"
    ```

    ![Get-AdGroup command with output](../media/guarded-fabric-shielded-vm/guarded-host-get-adgroup.png)

## Register the SID of the security group with HGS

1. On an HGS server, run the following command to register the security group with HGS. Re-run the command if necessary for additional groups. Provide a friendly name for the group. It does not need to match the Active Directory security group name.

    ```powershell
    Add-HgsAttestationHostGroup -Name "<GuardedHostGroup>" -Identifier "<SID>"
    ```
2. To verify the group was added, run [Get-HgsAttestationHostGroup](/en-us/powershell/module/hgsattestation/get-hgsattestationhostgroup).