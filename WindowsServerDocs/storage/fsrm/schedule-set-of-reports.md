---
layout: Conceptual
title: Schedule a Set of Reports | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/schedule-set-of-reports
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to generate a set of reports on a regular schedule
ms.date: 2024-12-10T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: ba54491c-7e01-ef12-c889-b4addf43c9af
document_version_independent_id: 5bb909a3-705b-a76a-679e-de2ae8352216
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/schedule-set-of-reports.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/schedule-set-of-reports
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/schedule-set-of-reports.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e834929-0ce1-4c1d-9c81-fcb14721edfb
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/75670257-a3f0-4627-9981-8046f99219e6
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: 5cf0abad-1098-a7d4-a27c-30f49ccf5b91
---

# Schedule a Set of Reports | Microsoft Learn

To generate a set of reports on a regular schedule, you schedule a *report task.* The report task specifies which reports to generate and what parameters to use; which volumes and folders to report on; how often to generate the reports and which file formats to save them in.

Scheduled reports are saved in a default location, which you can specify in the **File Server Resource Manager Options** dialog box. If an administrator decides to change the default locations where reports are generated, it's crucial to secure any new Universal Naming Convention (UNC) path with access limited to authorized users. Secured access helps to ensure paths are configured to prevent exploitation.

Note

To minimize the impact of report processing on performance, generate multiple reports on the same schedule so that the data is only gathered once. To quickly add reports to existing report tasks, you can use the **Add or Remove Reports for a Report Task** action. This allows you to add or remove reports from multiple report tasks and to edit the report parameters. To change schedules or delivery addresses, you must edit individual report tasks.

## To schedule a Report Task

1. Select the **Storage Reports Management** node.
2. Either right-select **Storage Reports Management** and select **Schedule a New Report Task** or select **Schedule a New Report Task** from the **Actions** pane to open the **Storage Reports Task Properties** dialog box.
3. To select volumes or folders on which to generate reports:

    - Under **Scope**, select **Add**.
    - Navigate to the volume or folder where you want to generate the reports, select it, and then select **OK** to add the path to the list.
    - Add as many volumes or folders as you want to include in the reports. (To remove a volume or folder, select the path and then select **Remove**).
4. To specify which reports to generate:

    -Under **Report data**, select each report that you want to include. By default, all reports are generated for a scheduled report task.

    To edit the parameters of a report:

    - Select the report label, and then select **Edit Parameters**.
    - In the **Report Parameters** dialog box, edit the parameters as needed, and then select **OK**.
    - To see a list of parameters for all the selected reports, select **Review Selected Reports**. Then select **Close**.
5. To specify the formats for saving the reports:

    - Under **Report formats**, select one or more formats for the scheduled reports. By default, reports are generated in Dynamic HTML (DHTML). You can also select HTML, XML, CSV, and text formats. The reports are saved to the default location for scheduled reports.
6. To deliver copies of the reports to administrators by e-mail:

    - On the **Delivery** tab, select the **Send reports to the following administrators** check box, and then enter the names of the administrative accounts that will receive reports.
    - Use the format *account@domain*, and use semicolons to separate multiple accounts.
7. To schedule the reports:

    On the **Schedule** tab, select **Create Schedule**, and then in the **Schedule** dialog box, select **New**. This displays a default schedule set for 9:00 A.M. daily, but you can modify the default schedule.

    - To specify a frequency for generating the reports, select an interval from the **Schedule Task** drop-down list. You can schedule daily, weekly, or monthly reports, or generate the reports only once. You can also generate reports at system startup or logon, or when the computer has been idle for a specified time.
    - To provide additional scheduling information for the chosen interval, modify or set the values in the **Schedule Task** options. These options change based on the interval that you choose. For example, for a weekly report, you can specify the number of weeks between reports and on which days of the week to generate reports.
    - To specify the time of day when you want to generate the report, type or select the value in the **Start time** box.
    - To access additional scheduling options (including a start date and end date for the task), select **Advanced**.
    - To save the schedule, select **OK**.
    - To create an additional schedule for a task (or modify an existing schedule), on the **Schedule** tab, select **Edit Schedule**.
8. To save the report task, select **OK**.

The report task is added to the **Storage Reports Management** node. Tasks are identified by the reports to be generated, the namespace to be reported on, and the report schedule.

In addition, you can view the current status of the report (whether or not the report is running), the last run time and the result of that run, and the next scheduled run time.

## Additional References

- [Storage Reports Management](storage-reports-management)
- [Setting File Server Resource Manager Options](setting-file-server-resource-manager-options)