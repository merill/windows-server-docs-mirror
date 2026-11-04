---
layout: Conceptual
title: AD Forest Recovery - Raising RID pools | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-raise-rid-pool
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: AD Forest Recovery - Raising the value of available RID pools'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
ms.custom:
- c37bc129-a5e0-4219-9ba7-b4cf3a9fc9a4
- inhenkel
- sfi-image-nochange
locale: en-us
document_id: 861144bc-8787-9018-393b-fb91237bf9ad
document_version_independent_id: 861144bc-8787-9018-393b-fb91237bf9ad
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-raise-rid-pool.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-raise-rid-pool
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/forest-recovery-guide/ad-forest-recovery-raise-rid-pool.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: b8058ba8-9509-fc12-323c-c9e653916df4
---

# AD Forest Recovery - Raising RID pools | Microsoft Learn

Use the following procedure to raise the value of the relative ID (RID) pools that the RID operations master will allocate after that DC is restored. By raising the value of the available RID pools, you can ensure that no DC allocates a RID for a security principal that was created after the backup that was used to restore the domain.

## Active Directory RID Pools and rIDAvailablePool

Each domain has an object **CN=RID Manager$,CN=System,DC**=&lt;*domain\_name*&gt;. This object has an attribute named **rIDAvailablePool**. This attribute value maintains the global RID space for an entire domain. The value is a large integer with upper and lower parts. The upper part defines the number of security principals that can be allocated for each domain (0x3FFFFFFF or just over 1 billion). The lower part is the number of RIDs that have been allocated in the domain.

Note

In Windows Server 2016 and 2012, the number of security principals that can be allocated is increased to just over 2 billion. For more information, see [Managing RID issuance](../managing-rid-issuance).

- Sample Value: 4611686014132422708
- Low Part: 2100 (beginning of the next RID pool to be allocated)
- Upper Part: 1073741823 (total number of RIDs that can be created in a domain)

When you increase the value of the large integer, you increase the value of the low part. For example, if you add 100,000 to the sample value of 4611686014132422708 for a sum of 4611686014132522708, the new low part is 102100. This indicates that the next RID pool that will be allocated by the RID master will begin with 102100 instead of 2100.

### Raise the value of available RID pools using adsiedit and the calculator

1. Open Server Manager, select **Tools** and select **ADSI Edit**.
2. Right-click, select **Connect to** and connect do the Default Naming Context and select **OK**. ![Screenshot that shows how to connect to the Default Naming Context](media/adsi1.png)
3. Browse to the following distinguished name path: **CN=RID Manager$,CN=System,DC=&lt;domain name&gt;**. ![Screenshot that shows how to browse to the distinguished name path.](media/adsi2.png)
4. Right-click and select the properties of **CN=RID Manager$**.
5. Select the attribute **rIDAvailablePool**, select **Edit**, and then copy the large integer value to the clipboard. ![Screenshot that shows the selected rIDAvailablePool attribute.](media/adsi3.png)
6. Start calculator, and from the **View** menu, select **Scientific Mode**.
7. Add 100,000 to the current value. ![Screenshot that shows where to add 100,000 to the current value.](media/adsi4.png)
8. Using ctrl-c, or the **Copy** command from the **Edit** menu, copy the value to the clipboard.
9. In the edit dialog of adsiedit, paste this new value. ![ADSI Edit](media/adsi5.png)
10. Select **OK** in the dialog, and **Apply** in the property sheet to update the **rIDAvailablePool** attribute.

### Raise the value of available RID pools using LDP

1. At the command prompt, type the following command, and then press ENTER: **ldp**
2. Select **Connection**, select **Connect**, type the name of RID manager, and then select **OK**. ![Screenshot that shows where to type the name of the RID manager.](media/ldp1.png)
3. Select **Connection**, select **Bind**, select **Bind with credentials** and type your administrative credentials, and then select **OK**. ![Screenshot that shows the Bind with credentials option.](media/ldp2.png)
4. Select **View**, select **Tree** and then type the following distinguished name path: CN=RID Manager$,CN=System,DC=*domain name*![Screenshot that shows where you type the distinguished name path.](media/ldp3.png)
5. Select **Browse**, and then select **Modify**.
6. Add 100,000 to the current **rIDAvailablePool** value, and then type the sum into **Values**.
7. In **Dn**, type `cn=RID Manager$,cn=System,dc=`*&lt;domain name&gt;*.
8. In **Edit Entry Attribute**, type `rIDAvailablePool`.
9. Select **Replace** as the operation, and then select **Enter**. ![Screenshot that shows the Replace option.](media/ldp4.png)
10. Select **Run** to run the operation. Select **Close**.
11. To validate the change, select **View**, select **Tree**, and then type the following distinguished name path: CN=RID Manager$,CN=System,DC=*domain name*. Check the **rIDAvailablePool** attribute. ![LDP](media/ldp5.png)