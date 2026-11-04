---
layout: Conceptual
title: Monthly Delta update ISV support without WSUS | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-server-update-services/deploy/monthly-delta-update-isv-support-without-wsus
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: wsus
ms.update-cycle: 1095-days
description: Windows Server Update Service (WSUS) topic - How Independent Software Vendors (ISV) can temporarily use Monthly Delta update instead of WSUS Express update delivery to reduce package size
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: b9b26133-1ae3-1088-a213-8b139f73d393
document_version_independent_id: 1a338fd0-3893-0ac6-807d-576d3eaa15f7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-server-update-services/deploy/monthly-delta-update-isv-support-without-WSUS.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-server-update-services/deploy/monthly-delta-update-isv-support-without-wsus
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-server-update-services/deploy/monthly-delta-update-isv-support-without-WSUS.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6582dd28-6756-78db-3391-f96b28a11581
---

# Monthly Delta update ISV support without WSUS | Microsoft Learn

Windows 10 Update downloads can be large because every package contains all previously released fixes to ensure consistency and simplicity.

Since version 7, Windows has been able to reduce the size of Windows Update downloads with a feature called [Express](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc708456%28v=ws.10%29#Anchor_2), and although consumer devices support it by default, Windows 10 enterprise devices require Windows Server Update Services (WSUS) to take advantage of Express. If you have WSUS available, see [Express update delivery ISV support](express-update-delivery-isv-support). We recommend using it to enable Express update delivery.

If you do not currently have WSUS installed, but you need smaller update package sizes in the interim, you can use Monthly Delta update. Delta update reduces package sizes substantially, but not as much as with WSUS Express update delivery. We recommend that you deploy WSUS Express update whenever possible for the greatest reduction in package sizes. Following is a chart comparing Delta, Cumulative and Express download sizes for Windows 10 version 1607:

![Screenshot of a chart comparing Delta, Cumulative and Express download sizes for Windows 10 version 1607.](../../media/express-update-delivery-isv-support/delta-1.png)

## What is Monthly Delta update?

There are two variants of the monthly security update: Delta and Cumulative.

Monthly Delta update is new, and an interim solution for ISVs who do not have WSUS available to help reduce update package sizes.

Important

**Delta update is available for servicing of Windows 10, version 1607 (Anniversary Update), version 1703 (Creators Update), and version 1709 (Fall Creators Update).** For releases after version 1709, you will need to implement a deployment infrastructure that supports [Express update delivery](express-update-delivery-isv-support) to continue taking advantage of incremental updates.

By using Monthly Delta update, packages will only contain one month's updates. Monthly Cumulative contains all the updates up to that update release, resulting in a large file that grows each month. Both Delta and Monthly updates are released on the second Tuesday of each month, also known as Update Tuesday. The following table compares Delta and Cumulative updates:

| - | Monthly**Delta**update | Monthly**Cumulative**update |
| --- | --- | --- |
| **Scope** | Single update with **only new fixes for that month** | Single update with all new fixes for that month and all previous months |
| **Application** | Can only be applied if the previous month's update was applied (Cumulative or Delta) | Can be applied at any time |
| **Delivery** | **Published only to Windows Update Catalog** where it can be downloaded for use with other tools or processes. Not offered to PCs that are connected to Windows Update | Published to Windows Update (where all consumer PCs will install it), WSUS, and the Windows Update Catalog |

Delta and Cumulative have the same KB number, with the same classification, and release at the same time. Updates can be distinguished by either the update title in the catalog, or by the MSU file name:

- 2017-02 *\***Delta Update**\** for Windows 10 Version 1607 for x64-based Systems (KB1234567)
- 2017-02 *\***Cumulative Update**\** for Windows 10 Version 1607 for x86-based Systems (KB1234567)

### When to use Monthly Delta Update

If size of the update to the client device is a concern, we recommend using Delta update on the devices that have the previous month's update, and Cumulative update on the devices that are falling behind. This way, all devices only require a single update to bring them up to date. This requires a small adjustment in the overall update management process, as you will have to deploy different updates based on how up-to-date the devices are in the organization:

![Diagram showing how you will have to deploy different updates based on how up-to-date the devices are in the organization.](../../media/express-update-delivery-isv-support/delta-2.png)

### Prevent deployment of Delta and Cumulative updates in the same month

Since Delta update and Cumulative update are available at the same time, it's important to understand what happens if you deploy both updates in the same month.

If you approve and deploy the same version of the Delta and Cumulative update, you will not only generate additional network traffic since both will be downloaded to the PC, but you may not be able to reboot your computer to Windows after restart.

If both Delta and Cumulative updates are inadvertently installed and your computer is no longer booting, you can recover with the following steps:

1. Boot into WinRE command prompt
2. List the packages in a pending state:

    `x:\windows\system32\dism.exe /image:<drive letter for windows directory> /Get-Packages >> <path to text file>`

> 
> **Example**: ` x:\windows\system32\dism.exe /image:c:\ /Get-Packages >> c:\temp\packages.txt`
3. Open the text file where you piped **get-packages**. If you see any install pending patches, run **remove-package** for each package name:

    `dism.exe /image:<drive letter for windows directory> /remove-package /packagename:<package name>`

> 
> **Example**: `x:\windows\system32\dism.exe /image:c:\ /remove-package /packagename:Package_for_KB4014329~31bf3856ad364e35~amd64~~10.0.1.0`

    Note

    Do not remove uninstall pending patches.

Important

**Delta update is available for servicing of Windows 10, version 1607 (Anniversary Update), version 1703 (Creators Update), and version 1709 (Fall Creators Update).** For releases after version 1709, you will need to implement a deployment infrastructure that supports [Express update delivery](express-update-delivery-isv-support) to continue taking advantage of incremental updates.