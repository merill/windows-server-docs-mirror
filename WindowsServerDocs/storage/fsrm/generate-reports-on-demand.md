---
layout: Conceptual
title: Generate reports on demand in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/generate-reports-on-demand
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to generate reports on demand to analyze disk usage in the Windows Server environment using FSRM (File Server Resource Manager).
ms.date: 2024-12-10T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 4d72ab13-be6f-4b7b-2383-816509afd51d
document_version_independent_id: be3f4e21-bd51-e59c-0f50-fcdd59efeecb
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/generate-reports-on-demand.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/generate-reports-on-demand
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/generate-reports-on-demand.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e834929-0ce1-4c1d-9c81-fcb14721edfb
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/75670257-a3f0-4627-9981-8046f99219e6
platformId: a5a548d4-725f-408e-7470-eab209c7e78e
---

# Generate reports on demand in Windows Server | Microsoft Learn

You can generate reports on demand using the **File Server Resource Manager** (FSRM). With these reports, you can analyze the different aspects of current disk usage on the server. Current data is gathered before the reports are generated.

When you generate reports on demand, reports are saved to a default location unless otherwise specified in **FSRM &gt; Action &gt; Configure Options &gt; Report Locations**. No report task is created for later use. You can view the reports immediately after they're generated or e-mail the reports to a group of administrators. If an administrator decides to change the default locations where reports are generated, they must also secure any new Universal Naming Convention (UNC) path with access limited to authorized users. Secured access ensures you can configure paths to prevent exploitation.

Note

If you choose to open the reports immediately, you must wait while the reports are generated. Processing time varies depending on the types of reports and the scope of the data.

## Prerequisites

The following must be installed to use this feature:

- A Windows Server with the **File and Storage Services** role service installed. To learn more, see [Install or Uninstall Roles, Role Services, or Features](/en-us/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features).
- An account with Administrative privileges.

## How to generate reports

1. Select **Start**
2. select **Windows Administrative Tools** and then select **File Server Resource Management**.
3. Select **Storage Reports Management**, right-select **Storage Reports Management**, and then select **Generate Reports Now**.
4. In the **Storage Reports Task Properties** dialog box, select the data you want to include from the **Report data** selection box.
5. Under **Report formats**, select one or more formats for your report. The default is set to *Dynamic HTML (DHTML)*. Other available formats are HTML, XML, CSV, and Text. The default save location for the reports are stored in **C:\StorageReports** unless changed.
6. Select the **Scope** tab, select **Add**, and then navigate to the volume or folder that you want to generate the reports from. Finally, select **OK** to add it to your report scope.

    - You can add as many volumes or folders as you want to include in the reports.
    - To remove a volume or folder, select its name in the list, then select **Remove**.
    - You can also include the following data types by selecting them within the **Scope**tab:
        - Application Files
        - Backup and Archival Files
        - Group Files
        - User Files
7. When you're finished, select **OK**.
8. Select one of the following two available options:

    - Generate reports in the background
    - Wait for reports to be generated and then display them
9. When you're finished, select **OK**.

The following animation demonstrates the steps to generate a report using the **Generate Reports Now** feature.

![A video demonstrating how to generate a report using the generate reports now feature in the File Server Resource Manager for Windows Server.](../media/generate-reports-now-gif.gif)

## Generate custom reports

To customize your reports, perform the following:

1. In the **Storage Reports Task Properties** dialog box, select the data you want to include from the **Report data** selection box.
2. Select **Edit Parameters**. In the **Report Parameters** dialog box, edit the parameters as needed, then select **OK**.

    Tip

    Each report data label has its own set of parameters. When customizing reports, it's recommended to select one report label at a time in making modifications.

    To see a list of parameters set for all the selected reports, select **Review Selected Reports**, then select **Close** when complete.
3. After customizing your report, select the report output type from **Report format**, select **OK**, select how you want your report generated, and then select **OK**.

## Deliver reports via email

To deliver copies of the reports to administrators by e-mail:

1. In the **Storage Reports Task Properties** dialog box, complete your selection of the report data you want to generate along with the **Report format** of choice.
2. Select the **Delivery** tab, select the **Send reports to the following administrators** check box, then enter the names of the administrative accounts that receive reports in *account@domain* formatting using the semicolon (**;**) to indicate multiple accounts.
3. Select **OK**, select how you want your report generated, and then select **OK**.

    Note

    In order to use this feature, an SMTP server must be configured to prevent e-mail delivery failure.

## Additional references

- [Storage Reports Management](storage-reports-management)
- [Setting File Server Resource Manager Options](setting-file-server-resource-manager-options)