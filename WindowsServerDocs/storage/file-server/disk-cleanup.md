---
layout: Conceptual
title: Using Disk Cleanup on Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/file-server/disk-cleanup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn how to use command-line options to configure the Disk Cleanup tool (Cleanmgr.exe) to automatically clear certain files.
ms.reviewer: cosmosdarwin
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2025-01-15T00:00:00.0000000Z
locale: en-us
document_id: 7226c88e-03b8-b123-e257-171dd4cb03ba
document_version_independent_id: 973ec668-3612-887a-a254-67e34bf70f04
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/file-server/disk-cleanup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/file-server/disk-cleanup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/file-server/disk-cleanup.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d08d52aa-cd85-15b3-c9fb-7fdbb09d3c97
---

# Using Disk Cleanup on Windows Server | Microsoft Learn

The Disk Cleanup tool clears unnecessary files in a Windows Server environment. This tool is available by default on Windows Server 2019 and Windows Server 2016, but you might have to take a few manual steps to enable it on earlier versions of Windows Server.

To start the Disk Cleanup tool, either run the Cleanmgr.exe file, or select **Start** &gt; **Windows Administrative Tools** &gt; **Disk Cleanup**.

You can also run Disk Cleanup by using the [cleanmgr Windows command](../../administration/windows-commands/cleanmgr), and use command-line options to direct Disk Cleanup to clean certain files.

Note

If you're just looking to free up disk space, consider using Azure File Sync with cloud tiering enabled. This method lets you cache your most frequently accessed files locally and tier your least frequently accessed files to the cloud, saving local storage space while maintaining performance. For more information, see [Planning for an Azure File Sync deployment](/en-us/azure/storage/files/storage-sync-files-planning).

## Enable Disk Cleanup on previous versions of Windows Server

The Disk Cleanup tool (cleanmgr.exe) isn't present by default before versions of Windows Server 2016 unless you have the Desktop Experience feature installed. Follow these steps to use the Add Roles and Features Wizard to install the Desktop Experience:

1. If Server Manager is already open, go to the next step. If Server Manager isn't open yet, launch it by doing one of the following options.

    - On the Windows desktop, select **Server Manager** in the Windows taskbar.
    - On the Windows **Start** menu, select the Server Manager tile.
2. On the **Manage** menu, select **Add Roles and Features**.
3. On the **Before you begin** page, verify that your destination server and network environment are prepared for the feature that you want to install. Select **Next**.
4. On the **Select installation type** page, select **Role-based or feature-based installation** to install all parts features on a single server. Select **Next**.
5. On the **Select destination server** page, select a server from the server pool, or select an offline `.VHD` file. Select **Next**.
6. On the **Select server roles** page, select **Next**.
7. On the **Select features** page, select **User Interface and Infrastructure**, and then select **Desktop Experience**.
8. In **Add features that are required for Desktop Experience?**, select **Add Features**.
9. Finish the installation, and then reboot the system.
10. Verify that the **Disk Cleanup** button appears in the Properties dialog box.

    ![Screenshot of the Disk Properties dialog with the Disk Cleanup button highlighted.](media/disk-cleanup.png)

## Manually add Disk Cleanup to Windows Server 2008 R2

To use cleanmgr.exe, install the Desktop Experience as described earlier, or copy the two files that are already present on the server, **cleanmgr.exe** and **cleanmgr.exe.mui**. Use the following table to locate the files for your operating system.

| Operating System | Architecture | File Location |
| --- | --- | --- |
| Windows Server 2008 R2 | 64-bit | C:\Windows\winsxs\amd64\_microsoft-windows-cleanmgr\_31bf3856ad364e35\_6.1.7600.16385\_none\_c9392808773cd7da\cleanmgr.exe |
| Windows Server 2008 R2 | 64-bit | C:\Windows\winsxs\amd64\_microsoft-windows-cleanmgr.resources\_31bf3856ad364e35\_6.1.7600.16385\_en-us\_b9cb6194b257cc63\cleanmgr.exe.mui |

Locate cleanmgr.exe and move the file to **%systemroot%\System32**.

Locate cleanmgr.exe.mui and move the files to **%systemroot%\System32\en-US**.

You can launch the Disk Cleanup tool by running Cleanmgr.exe from a Command Prompt window, or by selecting **Start** and entering **Cleanmgr** in the search field.

To set up the Disk Cleanup button to appear on a disk's Properties dialog, you need to install the Desktop Experience feature, as shown in the previous section.

## Related links

- [Free up drive space in Windows 10](https://support.microsoft.com/help/12425/windows-10-free-up-drive-space)
- [cleanmgr](../../administration/windows-commands/cleanmgr)