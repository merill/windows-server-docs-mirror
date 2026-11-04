---
layout: Conceptual
title: Active Directory Domain Services Replication Priority Boost | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/replication-priority-boost
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn about what the Active Directory Domain Services Replication Priority Boost feature is and how to manage it.
ms.author: roharwoo
author: robinharwood
ms.topic: how-to
ms.date: 2024-10-21T00:00:00.0000000Z
locale: en-us
document_id: f7179918-0d90-fb3c-b5e2-92cc9365e983
document_version_independent_id: f7179918-0d90-fb3c-b5e2-92cc9365e983
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/replication-priority-boost.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/replication-priority-boost
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/replication-priority-boost.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: b5ba6ca6-bb39-b4a5-5837-726d55af25ff
---

# Active Directory Domain Services Replication Priority Boost | Microsoft Learn

> 
> Applies to: Windows Server 2025, Windows Server 2022

Active Directory is a distributed system, which means changes you apply to one domain controller (DC) replicate to other DCs in the system automatically. Because changes can happen concurrently on multiple DCs, your deployment needs a priority system to manage these changes. In a priority system, when the destination DC retrieves its replication tasks from the other DCs that are its replication partners, the system serves these tasks based on priority.

Replication priority in Active Directory is hardcoded to use fixed heuristic rules. For example, the configuration naming context (NC) has a higher priority than the domain NC because topology changes are of higher importance. Similarly, the intra-site partner has higher priority than an inter-site partner because a DC's geographic proximity is more relevant for DCs in the same site. DCs in the same group all share the same priority.

The built-in priority heuristics work fine in most cases. However, there are scenarios where they aren't the most efficient approach. For example, in some environments, sites aren't designed according to proximity but functionality, such as with primary versus backup sites. In these cases, inter-site changes are more relevant than intra-site changes. There may also be scenarios when either the changes in the configuration DC aren't important or you choose to use only a specific partner DC instead of other DCs in the same group.

Replication Priority Boost is useful in scenarios that involve an administrator performing an over-the-wire DC promo that requires replication of a large DIT file. If the replication is interrupted because of a reboot or network issues, the replication can restart using a different replication partner. Administrators can work around these issues by specifying a prioritization boost on the `repsFrom` attribute to prioritize one or more specific replication partners.

In this article, you learn how to use Replication Priority Boost.

## System requirements and compatibility

There are no specific system requirements for enabling Replication Priority Boost in Windows Server 2025. The feature is also compatible with systems running a Windows Server 2022 DC as the replication source DC if the destination DC is running Windows Server 2025.

## Configure the boost factor

Use Replication Priority Boost to manage priority levels to get the most efficient replication order to match your deployment's needs. Replication Priority Boost uses a root directory system agent-specific entry (rootDSE) modifier, called [**setPriorityBoost**](/en-us/openspecs/windows_protocols/ms-adts/ee15e25a-a5b1-4229-904b-6f48cee9b793), to add a boost factor to the system to designate priority. To read the boost factor after it's set, there's a rootDSE attribute called [**msDS-PriorityBoost**](/en-us/openspecs/windows_protocols/ms-adts/b04b3102-2fd6-426c-9549-4f941b2d6233).

### Recommended boost values

When using `setPriorityBoost` to add a boost factor, you need to specify a boost factor value. The following list recommends a boost factor value to set depending on your configuration:

| Scenario | Boost factor value |
| --- | --- |
| Boost an intra-site replication partner higher priority than its peer intra-site replication partners. | 2 |
| Boost a domain NC higher priority than the configuration NC. | 10 |
| Boost an inter-site DC higher priority than an intra-site DC, if the inter-site source DC **doesn't** have [DRS_NEVER_NOTIFY](/en-us/openspecs/windows_protocols/ms-drsr/ac9c8a11-cd46-4080-acbf-9faa86344030) bit set with the destination DC. | 2 |
| Boost an inter-site DC higher priority than an intra-site DC, if the inter-site source DC has [DRS_NEVER_NOTIFY](/en-us/openspecs/windows_protocols/ms-drsr/ac9c8a11-cd46-4080-acbf-9faa86344030) bit set with the destination DC. | 18 |

## Set and read the priority boost

The Active Directory administrator adds, or sets the boost factor on top of the built-in priority level. To add the priority boost, the administrator must change the value specified in the Lightweight Directory Access Protocol (LDAP) modify operation.

### Set the priority boost

The following steps show how to set the replication priority boost.

1. Run **Ldp.exe** to start the **Ldp** program.
2. Select the **Connection** menu and select **Connect**. Enter in the Server name and Port number for your DC. Select **OK**.

    ![Screenshot showing the connection dialog including the server name and port number.](media/replication-priority-boost/connect-to-server.png)
3. Select the **Browse** menu, then select **Modify**.
4. In the **Edit Entry Attribute** field, enter:

    ```Cmd
    setPriorityBoost
    ```
5. In **Values**, type the values for your destination DC in the format: **`<naming context>:<partner DC>:<boost factor>`**. For example:

    ```Cmd
    CN=app1:ae732425-2e31-4246-98a5-60ce2e1c8101:5
    ```
6. Confirm that the Operation is **Add**.
7. Select **Enter** to update the **Entry List**.
8. Select **Run** to set the priority boost.

    ![Screenshot showing how to modify the rootDSE using setPriorityBoost.](media/replication-priority-boost/set-priority-boost.png)
9. The Ldp output window shows that the modify call was successful.

    ```cmd
    ----------
    ***Call Modify...
    ldap_modify_s(Id, '(null)',[1] attrs);
    Modified "".
    ----------
    ```

### Read the priority boost

To read the priority boost, and confirm the priority boost is set, you need to search using the *msDS-PriorityBoost* attribute.

1. Select the **Browse** menu, then **Search**.
2. Leave **Base DN** as-is, and the **Filter** set to: **(objectClass=\*)**. The **Scope** is **Base**.
3. In the Attributes field, enter **`"msDS-PriorityBoost;parameter=CN=<naming context>:<partner DC>"`**, replacing the values for your naming context and partner DC. Ensure that the whole value is within quotes. For example:

    ```Cmd
    "msDS-PriorityBoost;parameter=CN=app1:ae732425-2e31-4246-98a5-60ce2e1c8101"
    ```
4. Select **Run** to run the search and read the priority boost.

    ![Screenshot of how to read the priority using the rootDSE msDS-PriorityBoost.](media/replication-priority-boost/search-priority-boost.png)
5. If successful, the Ldp output window returns the priority boost, including the partner DC and priority boost factor.

    ```cmd
    ----------
    ***Searching...
    ldap_search_s(Id, "(null)", 0, "(objectclass=*)", attrList, 0, &msg)
    Getting 1 entries:
    Dn: (RootDSE)
        msDS-PriorityBoost;parameter=CN=app1:ae732425-2e31-4246-98a5-60ce2e1c8101: 5;
    ```