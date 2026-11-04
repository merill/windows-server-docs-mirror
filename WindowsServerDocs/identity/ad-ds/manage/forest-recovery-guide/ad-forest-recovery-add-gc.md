---
layout: Conceptual
title: AD Forest Recovery - Adding the GC | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-add-gc
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD Forest Recovery - Adding the GC'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
ms.custom: 5a291f65-794e-4fc3-996e-094c5845a383, inhenkel
locale: en-us
document_id: abc0c1b3-6cb2-91a7-6e62-88c754b493bd
document_version_independent_id: abc0c1b3-6cb2-91a7-6e62-88c754b493bd
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-add-gc.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-add-gc
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-add-gc.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 6d58e700-80f7-0a5b-cd2f-19bf8798f885
---

# AD Forest Recovery - Adding the GC | Microsoft Learn

Use the following procedure to add the global catalog to a DC.

## Add the global catalog

1. Select **Start**, point to **All Programs**, point to **Administrative Tools**, and then select **Active Directory Sites and Services**.
2. In the console tree, expand the **Sites** container, and then select the appropriate site that contains the target server.
3. Expand the **Servers** container, and then expand the server object for the DC to which you want to add the global catalog.
4. Right-click **NTDS Settings**, and then select **Properties**.
5. Select the **Global Catalog** check box.

![Add GC](media/adsi1.png)

## Add the global catalog using repadmin

- Open an elevated command prompt, type the following command, and press ENTER:

    ```cli
    repadmin.exe /options DC_NAME +IS_GC
    ```

The following are ways to speed up the process of adding the global catalog to the DC in the root domain:

- Ideally, the DC in the root domain should be a replication partner of the restored DCs in the nonroot domains. If so, confirm that the Knowledge Consistency Checker (KCC) has created the corresponding **repsFrom** object for the source DC and partition in the root DC. You can confirm this by running the `repadmin /showreps /v` command.
- If there's no **repsFrom** object created, create this object for the configuration partition. This way, the DC in the root domain can determine which DCs in the nonroot domain have been deleted. You can do this with the following commands:

    ```cli
    repadmin /add ConfigurationNamingContext DestinationDomainController SourceDomainControllerCNAME
    ```

    ```cli
    repadmin /options DSA -Disable_NTDSCONN_XLATE
    ```

    The format for the *SourceDomainControllerCNAME* is:

    ```cli
    sourceDCGuid._msdcs.root domain
    ```

    For example, the repadmin /add command for the configuration partition of the contoso.com domain could be:

    ```cli
    repadmin /add cn=configuration,DC=contoso,DC=com DC01 937ef930-7356-43c8-88dc-8baaaa781cf6._msdcs.dDSP17A22.contoso.com
    ```
- If the **repsFrom** object is present, try to sync the DC in the root domain with the DC in the nonroot domain as follows:

    ```cli
    repadmin /sync DomainNamingContext DestinationDomainController SourceDomainControllerGUID
    ```

    Where *DestinationDomainController* is the DC in the root domain and *SourceDomainController* is the restored DC in the nonroot domain.
- The root domain DNS server should have the alias (CNAME) resource records for the source DC. Ensure that the parent DNS zone contains delegation resource records (name server (NS) and host (A) resource records) for the correct DCs (the DCs that have been restored from backup) in the child zone.
- Make sure that the DC in the root domain is contacting the correct Key Distribution Center (KDC) in the nonroot domain. To test this, at the command prompt, type the following command, and then press ENTER:

    ```cli
    nltest /dsgetdc:nonroot domain name /KDC /Force
    ```