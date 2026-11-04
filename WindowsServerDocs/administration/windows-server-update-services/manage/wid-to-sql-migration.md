---
layout: Conceptual
title: Migrating the WSUS Database from (Windows Internal Database) WID to SQL | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-server-update-services/manage/wid-to-sql-migration
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: wsus
ms.update-cycle: 1095-days
description: Windows Server Update Service (WSUS) topic - How to migrate the WSUS database (SUSDB) from a Windows Internal Database instance to a Local or Remote instance of SQL Server.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2026-07-28T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: 29f08e7d-a6a0-23f3-f00e-bc8a1c8c5e2e
document_version_independent_id: 6b1b1c98-0a0a-6e41-558b-5cd85c33934d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-server-update-services/manage/wid-to-sql-migration.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-server-update-services/manage/wid-to-sql-migration
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-server-update-services/manage/wid-to-sql-migration.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 93e9283f-cf9d-a399-60d0-6a7a2779a11e
---

# Migrating the WSUS Database from (Windows Internal Database) WID to SQL | Microsoft Learn

Use the following steps to migrate the WSUS database (SUSDB) from a Windows Internal Database instance to a Local or Remote instance of SQL Server.

## Prerequisites

- SQL Instance. This can be the default **MSSQLServer** or a custom Instance.
- SQL Server Management Studio
- WSUS with WID role installed
- IIS (This is normally included when you install WSUS through Server Manager). It is not already installed, it will need to be.

## Migrating the WSUS database

### Stop the IIS and WSUS services on the WSUS server

From PowerShell (elevated), run:

```powershell
    Stop-Service IISADMIN
    Stop-Service WsusService
```

### Detach SUSDB from the Windows Internal Database

#### Using SQL Management Studio

1. Right-click **SUSDB** -&gt; **Tasks** -&gt; click **Detach**: ![Screenshot of SQL Server Management Studio showing the SUSDB &gt; Tasks &gt; Detach option selected.](images/image1.png)
2. Check **Drop Existing Connections** and click **OK** (optional, if active connections exist). ![Screenshot of the Detach Database dialog box with the Drop Existing Connections option selected and the OK option highlighted.](images/image2.png)

#### Using Command Prompt

Important

These steps show how to detach the WSUS database (SUSDB) from the Windows Internal Database instance by using the **sqlcmd** utility. For more information about the **sqlcmd** utility, see [sqlcmd Utility](/en-us/sql/tools/sqlcmd-utility).

1. Open an elevated command prompt
2. Run the following SQL command to detach the WSUS database (SUSDB) from the Windows Internal Database instance by using the **sqlcmd** utility:

```batchfile
        sqlcmd -S \\.\pipe\Microsoft##WID\tsql\query
        use master
        GO
        alter database SUSDB set single_user with rollback immediate
        GO
        sp_detach_db SUSDB
        GO
```

### Copy the SUSDB files to the SQL Server

1. Copy **SUSDB.mdf** and **SUSDB\_log.ldf** from the WID Data Folder (**%SystemDrive%**\**Windows\WID\Data**) to the SQL Instance Data Folder.

Tip

For example, if your SQL Instance Folder is **C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL**, and the WID Data folder is **C:\Windows\WID\Data,** copy the SUSDB files from **C:\Windows\WID\Data** to **C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data**

### Attach SUSDB to the SQL Instance

1. In **SQL Server Management Studio**, under the **Instance** node, right-click **Databases**, and then click **Attach**. ![Screenshot of SQL Server Management Studio showing the Databases &gt; Attach option selected.](images/image3.png)
2. In the **Attach Databases** box, under **Databases to attach**, click the **Add** button and locate the **SUSDB.mdf** file (copied from the WID Folder), and then click **OK**. ![Screenshot of the Attach Databases dialog box with the Add option highlighted.](images/image4.png)![Screenshot of the Locate Database Files dialog box with the S U S D B M D F file highlighted.](images/image5.png)

Tip

This is also able to be done using Transact-Sql. Please see the [SQL documentation for attaching a database](/en-us/sql/relational-databases/databases/attach-a-database) for its instructions.

Example (using paths from previous example):

```sql
   USE master;
   GO
   CREATE DATABASE SUSDB
   ON
       (FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data\SUSDB.mdf'),
       (FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log\SUSDB_Log.ldf')
       FOR ATTACH;
   GO
```

### Verify SQL Server and Database Logins and Permissions

#### SQL Server Login Permissions

After attaching the SUSDB, verify that **NT AUTHORITY\NETWORK SERVICE** has login permissions to the instance of SQL Server by doing the following:

1. Go into SQL Server Management Studio
2. Opening the Instance
3. Click **Security**
4. Click **Logins**

The **NT AUTHORITY\NETWORK SERVICE** account should be listed. If it is not, you need to add it by adding New Login Name.

Important

If the SQL Instance is on a different machine from WSUS, the WSUS Server's computer account should be listed in the format **[FQDN]\[WSUSComputerName]$**. If not, the steps below can be used to add it, replacing **NT AUTHORITY\NETWORK SERVICE** with the WSUS Server's computer account (**[FQDN]\[WSUSComputerName]$**) This would be ***in addition to*** granting rights to **NT AUTHORITY\NETWORK SERVICE**

##### Adding NT AUTHORITY\NETWORK SERVICE and granting it rights

1. Right Click **Logins** and click **New Login…**![Screenshot of SQL Server Management Studio showing the Logins &gt; New Login option selected.](images/image6.png)
2. On the **General** page, fill out the **Login name** (**NT AUTHORITY\NETWORK SERVICE**), and set the **Default database** to SUSDB. ![Screenshot of the General page of the Login dialog box showing the Login name and Defualt database fields populated.](images/image7.png)
3. On the **Server Roles** page, ensure **public** and **sysadmin** are selected. ![Screenshot of the Server Roles page of the Login dialog box showing the public and sysadmin options selected.](images/image8.png)
4. On the **User Mapping**page:
    - Under **Users mapped to this login**: select **SUSDB**
    - Under **Database role membership for: SUSDB**, ensure the following are checked:
        - **public**
        - **webService**![Screenshot of the User Mapping page of the Login dialog box showing the public and webService options selected.](images/image9.png)
5. Click **OK**

You should now see **NT AUTHORITY\NETWORK SERVICE** under Logins. ![Screenshot of the Object Explorer showing N T AUTHORITY NETWORK SERVICE under Logins.](images/image10.png)

#### Database Permissions

1. Right-click the SUSDB
2. Select **Properties**
3. Click **Permissions**

The **NT AUTHORITY\NETWORK SERVICE** account should be listed.

1. If it is not, add the account.
2. On the Login name textbox, enter the WSUS machine in the following format:

> 
> [**FQDN]\[WSUSComputerName]$**
3. Verify that the **Default database** is set to **SUSDB**.

    Tip

    In the following example, the FQDN is **Contosto.com** and the WSUS machine name is **WsusMachine**:

    ![Screenshot of the Login dialog box showing that the FQDN is Contosto.com** and the W S U S machine name is W s u s Machine.](images/image11.png)
4. On the **User Mapping** page, select the **SUSDB** Database under **Users mapped to this login**
5. Check **webservice** under the **Database role membership for: SUSDB**: ![Screenshot of the User Mapping page of the Login dialog box showing the SUSDB and webService options selected.](images/image12.png)
6. Click **OK** to save settings.

    Note

    You may need to restart the SQL Service for the changes to take effect.

### Edit the registry to point WSUS to the SQL Server Instance

Important

Follow the steps in this section carefully. Serious problems might occur if you modify the registry incorrectly. Before you modify it, [back up the registry for restoration](https://support.microsoft.com/help/322756) in case problems occur.

1. Click **Start**, click **Run**, type **regedit**, and then click **OK**.
2. Locate the following key: **HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\UpdateServices\Server\Setup\SqlServerName**
3. In the **Value** text box, type **[ServerName]\[InstanceName]**, and then click **OK**. If the instance name is the default instance, type **[ServerName]**.
4. Locate the following key: **HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Update Services\Server\Setup\Installed Role Services\UpdateServices-WidDatabase**![Screenshot of the Registry Editor dialog box with the UpdateServices-WidDatabase key highlighted.](images/image13.png)
5. Rename the Key to **UpdateServices-Database**![Screenshot of the Registry Editor dialog box showing the key name update to UpdateServices-Database.](images/image14.png)

    Note

    If you do not update this key, then **WsusUtil** will attempt to service the WID rather than the SQL Instance to which you have migrated.

### Start the IIS and WSUS services on the WSUS server

From PowerShell (elevated), run:

```powershell
    Start-Service IISADMIN
    Start-Service WsusService
```

Note

If you are using the WSUS Console, close and restart it.

If you migrated the WSUS database to a remote SQL Server, secure the connection by enabling SQL Server Extended Protection for Authentication (EPA). For more information, see [Secure the SQL Server connection](../deploy/2-configure-wsus#234-secure-the-sql-server-connection-if-needed).

## Uninstalling the WID role (not recommended)

Warning

Removing the WID role also removes a database folder (**%SystemDrive%\Program Files\Update Services\Database**) that contains scripts required by WSUSUtil.exe for post-installation tasks. If you choose to uninstall the WID role, make sure you back up the **%SystemDrive%\Program Files\Update Services\Database** folder beforehand.

Using PowerShell:

```powershell
Uninstall-WindowsFeature -Name 'Windows-Internal-Database'
```

After the WID role is removed, verify that the following registry key is present: **HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Update Services\Server\Setup\Installed Role Services\UpdateServices-Database**