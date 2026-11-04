---
layout: Conceptual
title: Upgrade a guarded fabric to Windows Server 2019 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/guarded-fabric-shielded-vm/guarded-fabric-upgrade-to-2019
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Upgrade a guarded fabric to Windows Server 2019'
ms.topic: upgrade-and-migration-article
author: robinharwood
ms.author: roharwoo
ms.date: 2018-11-21T00:00:00.0000000Z
locale: en-us
document_id: 837d8f1d-af60-d217-b476-acaf55d3b430
document_version_independent_id: 03e34f63-a60d-3c2c-9c9b-07f65cd5d1cf
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-upgrade-to-2019.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/guarded-fabric-shielded-vm/guarded-fabric-upgrade-to-2019
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/guarded-fabric-shielded-vm/guarded-fabric-upgrade-to-2019.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: fb85748e-8b7f-726f-b132-f80885eee881
---

# Upgrade a guarded fabric to Windows Server 2019 | Microsoft Learn

This article describes the steps necessary to upgrade an existing guarded fabric from Windows Server 2016, Windows Server version 1709 or Windows Server version 1803 to Windows Server 2019.

## What's new in Windows Server 2019

When you run a guarded fabric on Windows Server 2019, you can take advantage of several new features:

**Host Key Attestation** is our newest attestation mode, designed to make it easier to run shielded VMs when your Hyper-V hosts don't have TPM 2.0 devices available for TPM attestation. Host Key Attestation uses key pairs to authenticate hosts with HGS, removing the requirement for hosts to be joined to an Active Directory domain, eliminating the AD trust between HGS and the corporate forest, and reducing the number of open firewall ports. Host Key Attestation replaces Active Directory attestation, which is deprecated in Windows Server 2019.

**V2 Attestation Version** - To support Host Key Attestation and new features in the future, we've introduced versioning to HGS. A fresh install of HGS on Windows Server 2019 will result in the server using v2 attestation, which means it can support Host Key attestation for Windows Server 2019 hosts and still support v1 hosts on Windows Server 2016. In-place upgrades to 2019 will remain at version v1 until you manually enable v2. Most cmdlets now have a -HgsVersion parameter that lets you specify if you want to work with legacy or modern attestation policies.

**Support for Linux shielded VMs** - Hyper-V hosts running Windows Server 2019 can run Linux shielded VMs. While Linux shielded VMs have been around since Windows Server version 1709, Windows Server 2019 is the first Long Term Servicing Channel release to support them.

**Branch office improvements** - We've made it easier to run shielded VMs in branch offices with support for offline shielded VMs and fallback configurations on Hyper-V hosts.

**TPM host binding** - For the most secure workloads, where you want a shielded VM to run only on the first host where it was created but no other, you can now bind the VM to that host using the host's TPM. This is best used for privileged access workstations and branch offices, rather than general datacenter workloads that need to migrate between hosts.

## Compatibility matrix

Before you upgrade your guarded fabric to Windows Server 2019, review the following compatibility matrix to see if your configuration is supported.

| - | WS2016 HGS | WS2019 HGS |
| --- | --- | --- |
| **WS2016 Hyper-V Host** | Supported | Supported^1^ |
| **WS2019 Hyper-V Host** | Unsupported^2^ | Supported |

^1^ Windows Server 2016 hosts can only attest against Windows Server 2019 HGS servers using the v1 attestation protocol. New features that are exclusively available in the v2 attestation protocol, including Host Key Attestation, aren't supported for Windows Server 2016 hosts.

^2^ Microsoft is aware of an issue preventing Windows Server 2019 hosts using TPM attestation from successfully attesting against a Windows Server 2016 HGS server. This limitation will be addressed in a future update for Windows Server 2016.

## Upgrade HGS to Windows Server 2019

We recommend upgrading your HGS cluster to Windows Server 2019 before you upgrade your Hyper-V hosts to ensure that all hosts, whether they're running Windows Server 2016 or 2019, can continue to attest successfully.

Upgrading your HGS cluster will require you to temporarily remove one node from the cluster at a time while it's upgraded. This will reduce the capacity of your cluster to respond to requests from your Hyper-V hosts and could result in slow response times or service outages for your tenants. Ensure you have sufficient capacity to handle your attestation and key release requests before upgrading an HGS server.

To upgrade your HGS cluster, perform the following steps on each node of your cluster, one node at a time:

1. Remove the HGS server from your cluster by running `Clear-HgsServer` in an elevated PowerShell prompt. This cmdlet will remove the HGS replicated store, HGS websites, and node from the failover cluster.
2. If your HGS server is a domain controller (default configuration), you'll need to run `adprep /forestprep` and `adprep /domainprep` on the first node being upgraded to prepare the domain for an OS upgrade. See the [Active Directory Domain Services upgrade documentation](../../identity/ad-ds/deploy/upgrade-domain-controllers#supported-in-place-upgrade-paths) for more information.
3. Perform an [in-place upgrade](../../get-started/install-upgrade-migrate) to Windows Server 2019.
4. Run [Initialize-HgsServer](guarded-fabric-configure-additional-hgs-nodes) to join the node back to the cluster.

Once all nodes have been upgraded to Windows Server 2019, you can optionally upgrade the HGS version to v2 to support new features such as Host Key Attestation.

```powershell
Set-HgsServerVersion  v2
```

## Upgrade Hyper-V hosts to Windows Server 2019

Before you upgrade your Hyper-V hosts to Windows Server 2019, ensure that your HGS cluster is already upgraded to Windows Server 2019 and that you've moved all VMs off the Hyper-V server.

1. If you're using Windows Defender Application Control code integrity policies on your server (always the case when using TPM attestation), ensure that the policy is either in audit mode or disabled before attempting to upgrade the server. [Learn how to disable a WDAC policy](/en-us/windows/security/threat-protection/windows-defender-application-control/disable-windows-defender-application-control-policies).
2. Follow the guidance in the [Windows Server upgrade content](../../get-started/install-upgrade-migrate) to upgrade your host to Windows Server 2019. If your Hyper-V host is part of a failover cluster, consider using a [Cluster Operating System Rolling Upgrade](../../failover-clustering/cluster-operating-system-rolling-upgrade).
3. [Test and re-enable](/en-us/windows/security/threat-protection/windows-defender-application-control/audit-windows-defender-application-control-policies) your Windows Defender Application Control policy, if you had one enabled before the upgrade.
4. Run `Get-HgsClientConfiguration` to check if **IsHostGuarded = True**, meaning the host is successfully passing attestation with your HGS server.
5. If you're using TPM attestation, you might need to [re-capture the TPM baseline or code integrity policy](guarded-fabric-add-host-information-for-tpm-trusted-attestation) after the upgrade to pass attestation.
6. Start running shielded VMs on the host again!

## Switch to Host Key Attestation

Follow the steps below if you're currently running Active Directory-based attestation and want to upgrade to Host Key Attestation. Note that Active Directory-based attestation is deprecated in Windows Server 2019 and may be removed in a future release.

1. Ensure that your HGS server is operating in v2 attestation mode by running the following command. Existing v1 hosts will continue to attest even when the HGS server is upgraded to v2.

    ```powershell
    Set-HgsServerVersion v2
    ```
2. [Generate host keys](guarded-fabric-create-host-key) from each of your Hyper-V hosts and register them with HGS. Because HGS is still operating in Active Directory mode, you'll receive a warning that the new host keys aren't immediately effective. This is intentional, as you don't want to change to host key mode until all of your hosts can attest with host keys successfully.
3. Once host keys have been registered for every host, you can configure HGS to use host key attestation mode:

    ```powershell
    Set-HgsServer -TrustHostKey
    ```

    If you run into trouble with host key mode and need to revert back to Active Directory-based attestation, run the following command on HGS:

    ```powershell
    Set-HgsServer -TrustActiveDirectory
    ```