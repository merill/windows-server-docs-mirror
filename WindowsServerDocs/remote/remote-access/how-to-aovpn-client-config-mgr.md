---
layout: Conceptual
title: Deploy Always On VPN profile to Windows 10+ clients with Microsoft Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/how-to-aovpn-client-config-mgr
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to deploy Always On VPN profile to Windows clients with Microsoft Endpoint Configuration Manager.
ms.topic: install-set-up-deploy
ms.date: 2023-03-14T00:00:00.0000000Z
ms.author: roharwoo
author: robinharwood
locale: en-us
document_id: f05be8b8-a1af-e1d9-e224-5ca870edcdd9
document_version_independent_id: f05be8b8-a1af-e1d9-e224-5ca870edcdd9
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/how-to-aovpn-client-config-mgr.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/how-to-aovpn-client-config-mgr
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/how-to-aovpn-client-config-mgr.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 300304c9-2e9f-c129-2e8c-a183efb5e99e
---

# Deploy Always On VPN profile to Windows 10+ clients with Microsoft Configuration Manager | Microsoft Learn

In this how-to article, we'll show you how to use Configuration Manager deploy Always On VPN profiles using a ProfileXML PowerShell configuration PowerShell script.

## Prerequisites

- You should have Configuration Manager installed and configured. To learn how to install Configuration Manager, see [Set up a Configuration Manager lab](/en-us/mem/configmgr/core/get-started/set-up-your-lab).
- You should have already created a ProfileXML PowerShell configuration script. If you don't know how to create a ProfileXML configuration script, see [Tutorial: Deploy Always On VPN - Configure Always On VPN client connections](tutorial-aovpn-deploy-configure-client).

### Create a user collection

To use Configuration Manager to deploy an Always On VPN profile to Windows 10 or newer client computers, you'll need to create a group of machines or users to whom you'll deploy the profile.

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace.
2. On the **Home** ribbon, in the **Create** group, select **Create User Collection**.
3. On the General page, complete the following steps:

    1. In **Name**, type **VPN Users**.
    2. Select **Browse**, select **All Users** and select **OK**.
    3. Select **Next**.
4. On the Membership Rules page, complete the following steps:

    1. In **Membership rules**, select **Add Rule**, and select **Direct Rule**.
    2. On the **Welcome** page, select **Next**.
    3. On the Search for Resources page, in **Value**, type the name of the user you want to add or, if you are adding users to this collection dynamically for a larger-scale deployment, use a query rule to add users. The resource name includes the user's domain. To include results based on a partial match, insert the **%** character at either end of your search criterion. For example, to find all users containing the string "lori," type **%lori%**. Select **Next**.
    4. On the Select Resources page, select the users you want to add to the group, and select **Next**.
    5. On the Summary page, select **Next**.
    6. On the Completion page, select **Close**.
5. Back on the Membership Rules page of the Create User Collection Wizard, select **Next**.
6. On the Summary page, select **Next**.
7. On the Completion page, select **Close**.

After you create the user group to receive the VPN profile, you can create a package and program to deploy your Windows PowerShell ProfileXML configuration script.

### Create a package containing a ProfileXML configuration script

1. Host the ProfileXML configuration script on a network share that the site server computer account can access.
2. In the Configuration Manager console, go to the **Software Library** workspace, expand **Application Management**, and select the **Packages** node.
3. In the **Home** tab of the ribbon, in the **Create** group, select **Create Package**.
4. On the Package page, complete the following steps:

    1. In **Name**, type a name, such as **Windows client Always On VPN Profile**.
    2. Select the **This package contains source files** check box, and select **Browse**.
    3. In the Set Source Folder dialog box, select **Browse**, select the file share containing the ProfileXML script, and select **OK**. Make sure you select a network path, not a local path. In other words, the path should be something like *\fileserver\vpnscript*, not *c:\vpnscript*.
5. Select **Next**.
6. On the Program Type page, select **Next**.
7. On the Standard Program page, complete the following steps:

    1. In **Name**, type **VPN Profile Script**.
    2. In **Command line**, type `PowerShell.exe -ExecutionPolicy Bypass -File        "{your-script-name.ps1}"`.
    3. In **Run mode**, select **Run with administrative rights**.
    4. Select **Next**.
8. On the Requirements page, complete the following steps:

    1. Select **This program can run only on specified platforms**.
    2. Select the **All Windows 10 (32-bit)** and **All Windows 10 (64-bit)** check boxes.
    3. In **Estimated disk space**, type **1**.
    4. In **Maximum allowed run time (minutes)**, type **15**.
    5. Select **Next**.
9. On the Summary page, select **Next**.
10. On the Completion page, select **Close**.

With the package and program created, you are now ready to deploy it to the **VPN Users** group.

### Deploy the ProfileXML configuration package

1. In the Configuration Manager console, open Software Library\Application Management\Packages.
2. In **Packages**, select **Windows client Always On VPN Profile**.
3. On the **Programs** tab, at the bottom of the details pane, right-select **VPN Profile Script**, select **Properties**, and complete the following steps:

    a. On the **Advanced** tab, in **When this program is assigned to a computer**, select **Once for every user who logs on**.

    b. Select **OK**.
4. Right-click **VPN Profile Script** and select **Deploy** to start the Deploy Software Wizard.
5. On the General page, complete the following steps:

    a. Beside **Collection**, select **Browse**.

    b. In the **Collection Types** list (top left), select **User Collections**.

    c. Select **VPN Users**, and select **OK**.

    d. Select **Next**.
6. On the Content page, complete the following steps:

    a. Select **Add**, and select **Distribution Point**.

    b. In **Available distribution points**, select the distribution points to which you want to distribute the ProfileXML configuration script, and select **OK**.

    c. Select **Next**.
7. On the Deployment settings page, select **Next**.
8. On the Scheduling page, complete the following steps:

    a. Select **New** to open the Assignment Schedule dialog box.

    b. Select **Assign immediately after this event**, and select **OK**.

    c. Select **Next**.
9. On the User Experience page, complete the following steps:

    1. Select the **Software Installation** check box.
    2. Select **Summary**.
10. On the Summary page, select **Next**.
11. On the Completion page, select **Close**.

With the ProfileXML configuration script deployed, sign in to a Windows client computer with the user account you selected when you built the user collection. Verify the configuration of the VPN client.

### Verify the configuration of the VPN client

1. In Control Panel, under **System &gt; Security**, select **Configuration Manager**.
2. In the Configuration Manager Properties dialog, on the **Actions** tab, complete the following steps:

    a. Select **Machine Policy Retrieval & Evaluation Cycle**, select **Run Now**, and select **OK**.

    b. Select **User Policy Retrieval & Evaluation Cycle**, select **Run Now**, and select **OK**.

    c. Select **OK**.
3. Close the Control Panel.

You should see the new VPN profile shortly.