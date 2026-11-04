---
layout: Conceptual
title: AD FS Troubleshooting - SQL Connectivity | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-sql
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: Learn how to troubleshoot various aspects of Active Directory Federation Services as it relates to SQL connectivity.
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: troubleshooting-general
ms.custom:
- sfi-image-nochange
- sfi-ropc-nochange
locale: en-us
document_id: 9041555c-7b22-259c-e17c-d15e89a4ae97
document_version_independent_id: e8dac622-6c1a-4e7b-145f-91964427a07a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-sql.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/troubleshooting/ad-fs-tshoot-sql
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-sql.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: ad7820f0-0318-9983-0b0a-c19c1104f8fa
---

# AD FS Troubleshooting - SQL Connectivity | Microsoft Learn

With Active Directory Federation Services (AD FS), you can use remote SQL servers for AD FS farm data. You see issues if the AD FS servers in your farm can't communicate with the back-end SQL servers. This article provides basic steps to test the communication with the back-end servers.

## Acquire the SQL database connection string

The first thing to test when you check SQL connectivity is if AD FS has the correct SQL connection information. Use PowerShell for this task.

1. Open Windows PowerShell.
2. Enter `$adfs = gwmi -Namespace root/ADFS -Class SecurityTokenService`, and then select the Enter key.
3. Enter `$adfs.ConfigurationDatabaseConnectionString`, and then select the Enter key.

The connection string information appears.

![Screenshot that shows the PowerShell command screen running commands.](media/ad-fs-tshoot-sql/sql2.png)

## Create a UDL file to test connectivity

A Universal Data Link (UDL) file is a text file that contains a database connection string. By using the information you obtained, you can test whether or not the SQL server is responding to connections.

1. Open Notepad and save the file as **test.udl**. In the **Save as type** dropdown list, select **All Files**.
2. Double-click **test.udl**.
3. Fill in the following information:

    1. **Select or enter a server name:** Use the data source from the preceding connection string.
    2. **Enter information to log on to the server:** Use the AD FS service account or an account that has permissions to sign in remotely. If the account is a Windows account, use Integrated Windows Authentication. Otherwise, enter the username and password.
    3. **Select the database on the server:** Use the Initial Catalog from the preceding string. An example is `AdfsConfigurationV3`.

    ![Screenshot that shows the Connection dialog.](media/ad-fs-tshoot-sql/sql4.png)
4. Select **Test Connection**.

    ![Screenshot that shows the message Test connection succeeded.](media/ad-fs-tshoot-sql/sql3.png)

## Use SQL Server Management Studio to test connectivity

You can also [download](https://go.microsoft.com/fwlink/?linkid=864329) and install SQL Server Management Studio (SSMS) to test database connectivity.

1. Download and install SSMS.

    ![Screenshot that shows the installation process.](media/ad-fs-tshoot-sql/sql5.png)
2. Open SSMS and enter the server name from the preceding data source.
3. Use the AD FS service account or an account that has permissions to sign in remotely. If the account is a Windows account, use Integrated Windows Authentication. Otherwise, enter the username and password.

    ![Screenshot that shows the Connect to Server pane.](media/ad-fs-tshoot-sql/sql6.png)
4. After the left pane populates, expand databases and verify that you can see the AD FS databases.

    ![Screenshot that shows the AD FS databases.](media/ad-fs-tshoot-sql/sql7.png)