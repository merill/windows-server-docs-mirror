---
layout: Conceptual
title: Confirm guarded hosts can attest | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-confirm-hosts-can-attest-successfully
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Confirm guarded hosts can attest'
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2019-09-25T00:00:00.0000000Z
locale: en-us
document_id: f3c04358-57c4-6bbe-f961-b81a9090c981
document_version_independent_id: a4ee92fb-a77e-221d-4eab-6bb59d89c510
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-confirm-hosts-can-attest-successfully.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-confirm-hosts-can-attest-successfully
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-confirm-hosts-can-attest-successfully.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c89972e1-0a93-4ce3-b588-9c24d08ca424
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b2144970-2aee-47fb-9df2-af491ca710ec
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e51ec398-5969-d422-c8f2-42081bf5521d
---

# Confirm guarded hosts can attest | Microsoft Learn

A fabric administrator needs to confirm that Hyper-V hosts can run as guarded hosts. Complete the following steps on at least one guarded host:

1. If you have not already installed the Hyper-V role and Host Guardian Hyper-V Support feature, install them with the following command:

    ```powershell
    Install-WindowsFeature Hyper-V, HostGuardian -IncludeManagementTools -Restart
    ```
2. Make sure the Hyper-V host can resolve the HGS DNS name and has network connectivity to reach port 80 (or 443 if you set up HTTPS) on the HGS server.
3. Configure the host's Key Protection and Attestation URLs:

    - **Through Windows PowerShell**: You can configure the Key Protection and Attestation URLs by executing the following command in an elevated Windows PowerShell console. For &lt;FQDN&gt;, use the Fully Qualified Domain Name (FQDN) of your HGS cluster (for example, hgs.bastion.local, or ask the HGS administrator to run the **Get-HgsServer** cmdlet on the HGS server to retrieve the URLs).

        ```PowerShell
        Set-HgsClientConfiguration -AttestationServerUrl 'http://<FQDN>/Attestation' -KeyProtectionServerUrl 'http://<FQDN>/KeyProtection'
        ```

        To configure a fallback HGS server, repeat this command and specify the fallback URLs for the Key Protection and Attestation services. For more information, see [Fallback configuration](guarded-fabric-manage-branch-office#fallback-configuration).
    - **Through VMM**: If you are using System Center Virtual Machine Manager (VMM), you can configure Attestation and Key Protection URLs in VMM. For details, see [Configure global HGS settings](/en-us/system-center/vmm/guarded-deploy-host#configure-global-hgs-settings) in **Provision guarded hosts in VMM**.

> 
> **Notes**
> 
>     - If the HGS administrator [enabled HTTPS on the HGS server](guarded-fabric-configure-hgs-https), begin the URLs with `https://`.
>     - If the HGS administrator enabled HTTPS on the HGS server and used a self-signed certificate, you will need to import the certificate into the Trusted Root Certificate Authorities store on every host. To do this, run the following command on each host: `PowerShell Import-Certificate -FilePath "C:\temp\HttpsCertificate.cer" -CertStoreLocation Cert:\LocalMachine\Root `
>     - If you've configured HGS Client to use HTTPS and have disabled TLS 1.0 systemwide, see our [modern TLS guidance](guarded-fabric-troubleshoot-hosts#modern-tls)
>
4. To initiate an attestation attempt on the host and view the attestation status, run the following command:

    ```powershell
    Get-HgsClientConfiguration
    ```

    The output of the command indicates whether the host passed attestation and is now guarded. If `IsHostGuarded` does not return **True**, you can run the HGS diagnostics tool, [Get-HgsTrace](/en-us/powershell/module/hgsdiagnostics/get-hgstrace), to investigate. To run diagnostics, enter the following command in an elevated Windows PowerShell prompt on the host:

    ```powershell
    Get-HgsTrace -RunDiagnostics -Detailed
    ```

    Important

    If you're using Windows Server 2019 or Windows 10, version 1809 or later, and are using code integrity policies, `Get-HgsTrace` return a failure for the **Code Integrity Policy Active** diagnostic. You can safely ignore this result when it is the only failing diagnostic.