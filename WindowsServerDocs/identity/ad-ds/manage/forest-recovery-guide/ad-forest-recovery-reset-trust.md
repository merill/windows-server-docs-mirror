---
layout: Conceptual
title: AD Forest Recovery - Resetting a trust password | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-reset-trust
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Resetting a trust password on one side of the trust'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
ms.custom: 398918dc-c8ab-41a6-a377-95681ec0b543, inhenkel
locale: en-us
document_id: aeeec992-7277-ed9e-9501-b3ea11123f6a
document_version_independent_id: aeeec992-7277-ed9e-9501-b3ea11123f6a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-reset-trust.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-reset-trust
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-reset-trust.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e546ae66-bb51-bf5b-ffdf-58c57394dd3e
---

# AD Forest Recovery - Resetting a trust password | Microsoft Learn

If the forest recovery is related to a security breach, use the following procedure to reset a trust password on one side of the trust. This includes implicit trusts between child and parent domains as well as explicit trusts between this domain (the trusting domain) and another domain (the trusted domain).

Reset the password on only the trusting domain side of the trust, also known as the incoming trust (the side where this domain belongs). Then, use the same password on the trusted domain side of the trust, also known as the outgoing trust. Reset the password of the outgoing trust when you restore the first DC in each of the other (trusted) domains.

Resetting the trust password ensures that the DC doesn't replicate with potentially bad DCs outside its domain. By setting the same trust password while restoring the first DC in each of the domains, you ensure that this DC replicates with each of the recovered DCs. Subsequent DCs in the domain that are recovered by installing AD DS will automatically replicate these new passwords during the installation process.

## Reset a trust password on one side of the trust

1. At a command prompt, type the following command, and then press ENTER:

    ```cli
    netdom experthelp trust
    ```
2. Use the syntax that this command provides for using the NetDom tool to reset the trust password. For example, if there are two domains in the forest—parent and child—and you're running this command on the restored DC in the parent domain, use the following command syntax:

    ```cli
    netdom trust parent domain name /domain:child domain name /resetOneSide /passwordT:password /userO:administrator /passwordO:*
    ```

    When you run this command in the child domain, use the following command syntax:

    ```cli
    netdom trust child domain name /domain:parent domain name /resetOneSide /passwordT:password /userO:administrator /passwordO:*
    ```

    Note

    **passwordT** should be the same value on both sides of the trust. Run this command only once (unlike the **netdom resetpwd** command) because it automatically resets the password twice.