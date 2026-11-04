---
layout: Conceptual
title: View Task details and Notifications | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/server-manager/view-task-details-and-notifications
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: administration
ms.update-cycle: 1095-days
description: Learn how to view the status of user tasks or requests, see if a task failed, and troubleshoot problems by accessing detailed error messages about task failures.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: d642407d-8599-a42a-b89d-e07ee22840e9
document_version_independent_id: 91990549-2abb-ca6d-affe-6295a6f91b16
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/server-manager/view-task-details-and-notifications.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/server-manager/view-task-details-and-notifications
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/server-manager/view-task-details-and-notifications.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: d1da5345-e18e-7840-9d69-cb0305213a99
---

# View Task details and Notifications | Microsoft Learn

In Server Manager in Windows Server 2012 R2 or Windows Server 2012, when you perform management tasks such as adding roles and features, starting services, refreshing data that is displayed in the Server Manager console, or creating a custom group of servers, a notification is displayed in the **Notifications** area of the Server Manager console header. Notifications, and the **Task details** dialog box that you can open from the **Notifications** menu by clicking the flag icon, display the status of user tasks or requests, show you if a task failed, and help you troubleshoot problems by pointing to detailed error messages about task failures.

## The Notifications area

The **Notifications** area in the Server Manager menu bar, marked by a flag icon, displays the results of tasks that you start in Server Manager. Notifications inform you whether tasks that you started in Server Manager were successful or failed. When notifications are available for you to view, the number of available notifications is displayed next to the flag icon. If a task failed, could only be partially completed (for example, if it could not be completed on all of the remote servers on which you wanted to perform the task), or completed with warnings, the **Notifications** flag becomes red. Tasks for which notifications are displayed include the following.

- Manually refreshing the data displayed in Server Manager (notifications are displayed for automatic refreshes only if the refreshes fail)
- starting or stopping services
- Installing or uninstalling roles, role services, and features
- starting a Best Practices Analyzer (BPA) scan
- adding remote servers to manage (notifications are displayed for failures to contact or refresh the data displayed for remote servers)

Items in the **Notifications** menu show a progress bar, a brief description of the task, the name of the target server for the task (or one of the target servers, if multiple target servers were selected), a link to a related control or dialog box if applicable, and a **Tasks** menu. The **Tasks** menu shows commands that apply to the active notification (the notification over which your mouse cursor is hovered). For example, if you stop a service, you can click **Restart** on the **Tasks** menu in the notification to restart the service.

Notifications are particularly useful for installing or uninstalling roles, role services, and features. For example, if you start a feature installation on a remote server, you can close the add Roles and Features Wizard while the installation is still in progress, but the active task remains in the **Notifications** list. The **Notifications** item shows a progress bar for the installation, and lets you reopen the add Roles and Features Wizard, if needed, by clicking **add Roles and Features Wizard**. The items in this list notify you if an installation failed, or if additional configuration steps are required to finish deploying the feature.

Notifications also play an IMPORTANT part in troubleshooting problems with tasks or processes in Server Manager. For more information about how to use messages in the **Notifications** area and **Task details** dialog box to troubleshoot unsuccessful tasks or processes, see the [Server Manager forum](/en-us/answers/topics/windows-server-manager.html).

To delete a notification that you no longer want to see from the **Notifications** list, hover your mouse cursor over the notification, and then click **remove Task** (**X**).

## Viewing and troubleshooting tasks by using Task details

The **Task details** command at the bottom of the **Notifications** menu opens the **Task details** dialog box, which provides full descriptions of task events (starting, stopping, warnings, successes, or failures). Like other list controls in Server Manager, such as **Events**, **Services**, and **Best Practices Analyzer** tiles, you can filter and create queries to run on the tasks that are displayed in the **Task details** dialog box. (for more information about filtering and creating queries on list controls, see [Filter, sort, and query Data in Server Manager Tiles](filter-sort-and-query-data-in-server-manager-tiles).) In the top pane, you can review notifications as they have been displayed in the **Notifications** menu, and see how many notifications have been generated about the same task. selecting a notification in the top pane displays full details about the notification in the bottom pane.

The bottom pane is particularly useful for troubleshooting failed tasks. If Server Manager cannot connect to or get data for a server that is a member of the server pool, entries in this pane often contain detailed messages, including the full text of underlying Windows remote Management (WinRM), networking, or security problems that prevent Server Manager from communicating with a target server.