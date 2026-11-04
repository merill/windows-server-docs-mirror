---
layout: Conceptual
title: Roles, Role Services, and Features not in Server Core containers - Windows Server, version 1803 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/server-core/server-core-container-removed-roles
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Learn about the roles and features we removed from the Server Core container image for Windows Server.
ms.mktglfcycl: manage
ms.sitesec: library
author: robinharwood
ms.author: roharwoo
ms.date: 2018-05-07T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: ca45d9b5-df21-5a91-53c8-33557c2775e2
document_version_independent_id: e5abe541-1bd3-27aa-940a-58d3c2395bdc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/server-core/server-core-container-removed-roles.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/server-core/server-core-container-removed-roles
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/server-core/server-core-container-removed-roles.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c783a8fb-cf36-41ad-90c6-0692a0540484
platformId: 245ddd18-45ea-97a2-59ae-9919e16e5d93
---

# Roles, Role Services, and Features not in Server Core containers - Windows Server, version 1803 | Microsoft Learn

In Windows Server, version 1803, we've [reduced the overall size of the Server Core container image to **1.58 GB**](https://blogs.technet.microsoft.com/virtualization/2018/01/22/a-smaller-windows-server-core-container-with-better-application-compatibility/). The way we've done this is by optimizing the architecture and removing things you don't need in a [Server Core container](/en-us/virtualization/windowscontainers/about/). Some were things that didn't work in containers, some were roles and features no one's been using.

Important

We removed these from the Server Core **container** image, not [Server Core itself](server-core-roles-and-services).

Here's the complete list of features and roles removed from the Server Core container image:

ADCertificateServicesRole AuthManager Bitlocker-Utilities BitLocker BITS BITSExtensions-Upload CCFFilter CertificateEnrollmentPolicyServer CertificateEnrollmentServer CertificateServices ClientForNFS-Infrastructure Containers CoreFileServer DataCenterBridging-LLDP-Tools DataCenterBridging Dedup-Core DeviceHealthAttestationService DFSN-Server DFSR-Infrastructure-ServerEdition DirectoryServices-ADAM DirectoryServices-DomainController DiskIo-QoS EnhancedStorage FailoverCluster-AdminPak FailoverCluster-AutomationServer FailoverCluster-CmdInterface FailoverCluster-FullServer FailoverCluster-PowerShell File-Services FileServerVSSAgent FRS-Infrastructure FSRM-Infrastructure-Services FSRM-Infrastructure HardenedFabricEncryptionTask HostGuardian HostGuardianService-Package IdentityServer-SecurityTokenService IPAMClientFeature IPAMServerFeature iSCSITargetServer-PowerShell iSCSITargetServer iSCSITargetStorageProviders iSNS\_Service Licensing LightweightServer Microsoft-Hyper-V-Management-Clients Microsoft-Hyper-V-Offline Microsoft-Hyper-V-Online Microsoft-Hyper-V Microsoft-Windows-FCI-Client-Package Microsoft-Windows-GroupPolicy-ServerAdminTools-Update Microsoft-Windows-Subsystem-Linux MSRDC-Infrastructure MultipathIo NetworkController NetworkControllerTools NetworkDeviceEnrollmentServices NetworkLoadBalancingFullServer NetworkVirtualization OnlineRevocationServices P2P-PnrpOnly PeerDist Printing-Client-Gui Printing-LPDPrintService Printing-Server-Foundation-Features Printing-Server-Role QWAVE RasRoutingProtocols Remote-Desktop-Services RemoteAccess RemoteAccessMgmtTools RemoteAccessPowerShell RemoteAccessServer ResumeKeyFilter RightsManagementServices-Role RightsManagementServices RMS-Federation SBMgr-UI ServerCore-Drivers-General-WOW64 ServerCore-Drivers-General ServerForNFS-Infrastructure ServerManager-Core-RSAT-Feature-Tools ServerMediaFoundation ServerMigration SessionDirectory SetupAndBootEventCollection ShieldedVMToolsAdminPack SMB1Protocol-Server SmbDirect SMBHashGeneration SmbWitness SNMP SoftwareLoadBalancer Storage-Replica-AdminPack Storage-Replica Tpm-PSH-Cmdlets UpdateServices-Database UpdateServices-Services UpdateServices-WidDatabase UpdateServices VmHostAgent VolumeActivation-Full-Role Web-Application-Proxy WebAccess WebEnrollmentServices Windows-Defender WindowsServerBackup WindowsStorageManagementService WINSRuntime WMISnmpProvider WorkFolders-Server WSS-Product-Package