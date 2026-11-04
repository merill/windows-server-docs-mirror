---
layout: Conceptual
title: Virtualized Domain Controller Technical Reference Appendix | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/reference/virtual-dc/virtualized-domain-controller-technical-reference-appendix
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Virtualized Domain Controller Technical Reference Appendix'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 41c45585-2085-fb33-f1c2-895b021f8b6b
document_version_independent_id: 42e30bd7-a3db-b984-bb8d-c5b708135374
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/reference/virtual-dc/Virtualized-Domain-Controller-Technical-Reference-Appendix.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/reference/virtual-dc/virtualized-domain-controller-technical-reference-appendix
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/reference/virtual-dc/Virtualized-Domain-Controller-Technical-Reference-Appendix.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 9d950f88-dbc7-5f29-ac39-3e23dfeee21a
---

# Virtualized Domain Controller Technical Reference Appendix | Microsoft Learn

This topic covers:

- Terminology
- FixVDCPermissions.ps1

## Terminology

- **Snapshot** - The state of a virtual machine at a particular point in time. It is dependent on the chain of previous snapshots taken, on the hardware, and on the virtualization platform.
- **Clone** - A complete and separate copy of a virtual machine. It is dependent on the virtual hardware (hypervisor).
- **Full Clone** - A full clone is an independent copy of a virtual machine that shares no resources with the parent virtual machine after the cloning operation. Ongoing operation of a full clone is entirely separate from the parent virtual machine.
- **Differencing disk** - A copy of a virtual machine that shares virtual disks with the parent virtual machine in an ongoing manner. This usually conserves disk space and allows multiple virtual machines to use the same software installation.
- **VM Copy**- A file system copy of all the related files and folders of a virtual machine.
- **VHD File Copy** - A copy of a virtual machine's VHD
- **VM Generation ID** - a 128-bit integer given to the virtual machine by the hypervisor. This ID is stored in memory and reset every time a snapshot is applied. The design uses a hypervisor-agnostic mechanism for surfacing the VM-Generation ID in the virtual machine. The Hyper-V implementation exposes the ID in the ACPI table of the virtual machine.
- **Import/Export** - A Hyper-V feature that allows the user to save the entire virtual machine (VM files, VHD and the machine configuration). It then allows users to using that set of files to bring the machine back on the same machine as the same VM (Restore), on a different machine as the same VM (Move), or a new VM (copy)

## FixVDCPermissions.ps1

```
# Unsigned script, requires use of set-executionpolicy remotesigned -force
# You must run the Windows PowerShell console as an elevated administrator

# Load Active Directory Windows PowerShell Module and switch to AD DS drive
import-module activedirectory
cd ad:

## Get Domain NC
$domainNC = get-addomain

## Get groups and obtain their SIDs
$dcgroup = get-adgroup "Cloneable Domain Controllers"

$sid1 = (get-adgroup $dcgroup).sid

## Get the DACL of the domain
$acl = get-acl $domainNC

## The following object specific ACE grants extended right 'Allow a DC to create a clone of itself' for the CDC group to the Domain NC
## 3e0f7e18-2c7a-4c10-ba82-4d926db99a3e is the schemaIDGuid for 'DS-Clone-Domain-Controller"

$objectguid = new-object Guid 3e0f7e18-2c7a-4c10-ba82-4d926db99a3e
$ace1 = new-object System.DirectoryServices.ActiveDirectoryAccessRule $sid1,"ExtendedRight","Allow",$objectguid

## Add the ACE in the ACL and set the ACL on the object

$acl.AddAccessRule($ace1)
set-acl -aclobject $acl $domainNC
write-host "Done writing new VDC permissions."
cd c:
```