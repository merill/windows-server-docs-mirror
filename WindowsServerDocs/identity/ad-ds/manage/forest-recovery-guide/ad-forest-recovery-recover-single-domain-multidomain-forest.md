---
layout: Conceptual
title: Active Directory Forest Recovery - Recovering a single domain in a multidomain forest | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-recover-single-domain-multidomain-forest
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: In certain scenarios, it may be necessary to recover only a single domain within a forest that has multiple domains, rather than a full forest recovery. This topic covers considerations for recovering a single domain and possible strategies for recovery.
ms.author: roharwoo
author: robinharwood
ms.date: 2023-07-10T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 267a982e-b9ce-ed0c-584a-f89a93e02f2c
document_version_independent_id: 267a982e-b9ce-ed0c-584a-f89a93e02f2c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-recover-single-domain-multidomain-forest.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-recover-single-domain-multidomain-forest
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-recover-single-domain-multidomain-forest.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
platformId: efe7f327-8042-abdb-30db-38defe766120
---

# Active Directory Forest Recovery - Recovering a single domain in a multidomain forest | Microsoft Learn

In certain scenarios, it may be necessary to recover only a single domain within a forest that has multiple domains, rather than a full forest recovery. This topic covers considerations for recovering a single domain and possible strategies.

Similar to the forest recovery process, you restore one or more DCs from backup in the domain and perform metadata cleanup of remaining DCs. New domain controllers are then added by joining new members, installing AD DS roles and promoting them. You can also use **DC Cloning** or **Install from Media** for the task.

A single domain recovery presents a unique challenge for rebuilding global catalog (GC) servers. For example, if the first domain controller (DC) for the domain is restored from a backup that was created one week earlier, then all other GCs in the forest will have more up-to-date data for that domain than the restored DC. To re-establish GC data consistency, there are a couple options:

- Unhost the recovered domains partition from all GCs in the forest, except those in the recovered domain, at the same time and once complete, rehost all GCs in the forest. Also make sure you don't overload the remaining GCs. In large environments, coordinating this activity can be very complex.
- Follow the forest recovery process to recover the domain, and then remove lingering objects from GCs in other domains.

The following sections provide general considerations for each option. The complete set of steps that need to be done for the recovery will vary for different Active Directory environments.

## Rehost all GCs

Warning

The login name and password of the default Domain Administrator user account (“RID-500”) for all domains must available, and the account(s) enabled for use in case a problem that prevents access to a GC for logon.

Note

To allow logon without the GC verification, it's possible also to configure `HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Lsa\\IgnoreGCFailures` value to 1.

*If unknown, obtain the***Domain ID***by using `whoami /all` for another account in each domain or run the following command to identify the RID 500.*`\$DomainSID = (Get-ADDomain).DomainSID.Value``\$ObjSID = New-Object``System.Security.Principal.SecurityIdentifier("\$DomainSID-500")``\$RID500 = \$ObjSID.Translate([System.Security.Principal.NTAccount])``\$RID500.Value`

Rehosting all GCs can be done using `repadmin /unhost` and `repadmin /rehost` commands (part of `repadmin /experthelp`). You would run the `repadmin` commands on every GC in each domain that isn't recovered. It needs to be ensured, that all GCs don't hold a copy of the recovered domain anymore. To achieve this, unhost the domain partition first from all domain controllers across all none-recovered domains of the forest first. Since GCs don't contain the partition anymore, you can rehost it. When rehosting, consider the site and replication structure of your forest. For example, finish the rehost of one DC per site prior to rehosting the other DCs of that site.

This option can be advantageous for a small organization that has only a few domain controllers for each domain. All of the GCs could be rebuilt on a Friday night and, if necessary, complete replication for all read-only domain partitions before Monday morning. However, if you need to recover a large domain that covers sites across the globe, rehosting the read-only domain partition on all GCs for other domains can significantly impact operations and potentially require down time.

## Check for and remove lingering objects

On the GCs of all other domains in the forest, you check and remove the potentially lingering objects for the read-only partition of the recovered domain.

The source for the lingering object cleanup must be a DC in the recovered domain. To be certain that the source DC doesn't have any lingering objects for any domain partitions, you can remove the global catalog.

Removing lingering objects is advantageous for larger organizations that can't risk the down time associated with rehosting the domain naming context.

For more information, see [Use repadmin to remove lingering objects](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc785298%28v=ws.10%29).