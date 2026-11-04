---
layout: Conceptual
title: AD Forest Recovery - Redeploy remaining DCs | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-restore-additional-dcs
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD Forest Recovery - Redeploy remaining DCs'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
ms.custom: 5a291f65-794e-4fc3-996e-094c5845a383, inhenkel
locale: en-us
document_id: 378bf2e9-54fe-8359-fdef-01e2f08efed1
document_version_independent_id: 378bf2e9-54fe-8359-fdef-01e2f08efed1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-restore-additional-dcs.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-restore-additional-dcs
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-restore-additional-dcs.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: a367d8de-f552-5ebf-c66d-203d8bf81c91
---

# AD Forest Recovery - Redeploy remaining DCs | Microsoft Learn

The steps up to this point apply to all forests: find a valid backup for each domain, recover the domains in isolation, reconnect them, reset the global catalog, and clean up. In this next step, you'll redeploy the forest. The way to do this will greatly depend on your forest design, your service level agreements, site structure, available bandwidth, and numerous other factors. You'll need to design your own redeployment plan based on the principles and suggestions in this section, in a way that is best suited to your business requirements.

The next step is to install AD DS on all DCs that were present before the forest recovery took place. If the DCs still exist, the AD DS service will need to be removed forcibly, or the DCs can be reinstalled. Any existing backups for these DCs can't be reused, because the corresponding metadata has been removed during forest recovery. In an uncomplicated environment this redeployment process can be as simple as reconnecting the recovered DCs to the production network, and promoting new DCs as needed.

In a large enterprise faced with a worldwide infrastructure, a more sophisticated plan is needed. The first phase is usually to restore AD as a service; install strategically placed DCs such that all critical business divisions and applications can start working again. (It may be acceptable for branch offices to temporarily have reduced performance as a result of this.) As a second phase, all remaining and less critical DCs are redeployed.

There are two methods to install additional DCs, both of which can be automated:

## Clone

You can automate the recovery of all virtualized DCs in a domain after you restore a single virtualized DC from backup. For more information about cloning and prerequisites, see [Introduction to Active Directory Domain Services (AD DS) Virtualization (Level 100)](../managing-rid-issuance).

## Reinstall AD DS using Windows Powershell

To expedite reinstalling AD DS, you can use Install from Media (IFM) option to reduce replication traffic during the installation. For more information about using the `ntdsutil ifm` command to create installation media, see [Installing AD DS from Media](../managing-rid-issuance).

Consider the following additional points for each replica DC that is recovered in the forest by virtualized DC cloning or by installing AD DS (as opposed to restoring from backup):

- All software on a DC that is used as the source for cloning must be able to be cloned. Applications and services that can't be cloned should be removed before cloning is initiated. If that isn't possible, an alternative virtualized DC should be chosen as the source.
- If you clone additional virtualized DCs from the first virtualized DC to be restored, the source DC will need to be shut down while its VHDX file is copied. Then, it will need to be running and available online when the clone virtual DCs are first started. If the downtime required by the shutdown isn't acceptable for the first recovered DC, deploy an additional virtualized DC by installing AD DS to act as the source for cloning.
- There is no restriction on the host name of the cloned virtualized DC or the server on which you want to install AD DS. You can use a new host name or the host name that was in use previously. For more information about DNS host name syntax, see [Creating DNS Computer Names](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc785282%28v=ws.10%29) ([https://go.microsoft.com/fwlink/?LinkId=74564](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc785282%28v=ws.10%29)).
- Configure each server with the first DNS server in the forest (the first DC that was restored in the root domain) as the preferred DNS server in the TCP/IP properties of its network adapter. For more information, see [Configure TCP/IP to use DNS](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc779282%28v=ws.10%29).
- Redeploy all RODCs in the domain, either by virtualized DC cloning if several RODCs are deployed in a central location, or by the traditional method of rebuilding them by removing and reinstalling AD DS if they're deployed individually in isolated located locations such as branch offices.
    - Rebuilding RODCs ensures that they don't contain any lingering objects and can help prevent replication conflicts from occurring later. When you remove AD DS from an RODC, *choose the option to retain DC metadata*. Using this option retains the krbtgt account for the RODC and retains the permissions for the delegated RODC administrator account and the Password Replication Policy (PRP), and prevents you from having to use Domain Admin credentials to remove and reinstall AD DS on an RODC. It also retains the DNS server and global catalog roles if they're installed on the RODC originally.
    - When you rebuild DCs (RODCs or writeable DCs), there may be increased replication traffic during their reinstallation. To help reduce that impact, you can stagger the schedule of the RODC installations, and you can use the Install From Media (IFM) option. If you use the IFM option, run the `ntdsutil ifm` command on a writeable DC that you trust to be free of damaged data. This helps prevent possible corruption from appearing on the RODC after the AD DS reinstallation is complete. For more information about IFM, see [Installing AD DS from Media](../managing-rid-issuance).
    - For more information about rebuilding RODCs, see [RODC Removal and Reinstallation](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc779282%28v=ws.10%29).
- If a DC was running the DNS Server service before the forest malfunction, install and configure the DNS Server service during the installation of AD DS. Otherwise, configure its former DNS clients with other DNS servers.
- If you require additional global catalogs to share authentication or query load for users or applications, you can either add the global catalog to the source virtualized DC before cloning or you can make a DC a global catalog server during the installation of AD DS.