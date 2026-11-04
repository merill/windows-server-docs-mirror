---
layout: Conceptual
title: Detect, enable, and disable SMBv1, SMBv2, and SMBv3 in Windows | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/file-server/troubleshoot/detect-enable-and-disable-smbv1-v2-v3
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: See various ways to detect, enable, and disable the Server Message Block (SMB) protocol (SMBv1, SMBv2, and SMBv3) in Windows client and server environments.
author: robinharwood
ms.topic: how-to
ms.author: roharwoo
ms.date: 2025-02-28T00:00:00.0000000Z
locale: en-us
document_id: 8a91db45-ca3c-7a2e-3f32-2f5b57837b03
document_version_independent_id: b83cbaab-c0df-d6e7-a67f-f4c99a46e30a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/file-server/Troubleshoot/detect-enable-and-disable-smbv1-v2-v3.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/file-server/troubleshoot/detect-enable-and-disable-smbv1-v2-v3
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/file-server/Troubleshoot/detect-enable-and-disable-smbv1-v2-v3.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 939b1b8c-abaa-6175-bf7f-2e5cc33d00db
---

# Detect, enable, and disable SMBv1, SMBv2, and SMBv3 in Windows | Microsoft Learn

This article describes how to enable and disable Server Message Block (SMB) version 1 (SMBv1), SMB version 2 (SMBv2), and SMB version 3 (SMBv3) on SMB client and server components.

If you disable or remove SMBv1, you might encounter compatibility issues with old computers or software. SMBv1 has significant security vulnerabilities, and [we strongly encourage you not to use it](https://techcommunity.microsoft.com/t5/storage-at-microsoft/stop-using-smb1/ba-p/425858). [SMBv1 isn't installed by default](smbv1-not-installed-by-default-in-windows) in any edition of Windows 11 or Windows Server 2019 and later versions. SMBv1 also isn't installed by default in Windows 10, except Home and Pro editions. We recommend that instead of reinstalling SMBv1, you update the SMB server that still requires it. For a list of partners that require SMBv1 and their updates that remove the requirement, see [SMB1 Product Clearinghouse](https://aka.ms/stillneedssmb1).

In Windows 11, version 24H2 and Windows Server 2025, SMB signing is required by default, which can prevent connections to workgroup computers, guest-authenticated shares, or third-party SMB servers that don't support signing. Changing which SMB protocol versions you enable doesn't change this signing requirement. Don't disable SMB protocol versions or SMB signing to work around these connection failures. Instead, enable SMB signing on the remote server, or update or replace devices that don't support SMB signing. For more information, see [Control SMB signing behavior](../smb-signing).

## Disable SMBv2 or SMBv3 for troubleshooting

We recommend keeping SMBv2 and SMBv3 enabled, but you might find it useful to disable one temporarily for troubleshooting. For more information, see Use the command line or Registry Editor to manage SMB protocols.

Disabling SMBv3 deactivates the following functionality:

- Transparent failover: Provides clients with a way to reconnect without interruption to cluster nodes during maintenance or failover
- Scale-out: Supplies concurrent access to shared data on all file cluster nodes
- SMB Multichannel: Facilitates aggregation of network bandwidth and fault tolerance if multiple paths are available between the client and server
- SMB Direct: Adds remote direct memory access (RDMA) networking support for high performance, with low latency and low CPU use
- Encryption: Provides end-to-end encryption and offers protection from eavesdropping on untrustworthy networks
- Directory leasing: Improves application response times in branch offices through caching
- Performance optimization: Optimizes small random read/write I/O operations

Disabling SMBv2 deactivates the following functionality:

- Request compounding: Supports sending multiple SMBv2 requests as a single network request
- Larger reads and writes: Improves the use of faster networks
- Caching of folder and file properties: Gives clients the ability to keep local copies of folders and files
- Durable handles: Provides a way for a connection to transparently reconnect to the server after a temporary disconnection
- Improved message signing: Uses a hash-based message authentication code (HMAC) secure hash algorithm (SHA) with a 256-bit digest (HMAC SHA-256) instead of Message-Digest Algorithm 5 (MD5) as a hashing algorithm
- Improved scalability for file sharing: Greatly increases the number of users, shares, and open files per server
- Support for symbolic links
- Client oplock leasing model: Limits the data transferred between the client and server, improving performance on high-latency networks and increasing SMB server scalability
- Large maximum transmission unit (MTU) support: Supports full use of 10 Gigabit Ethernet (GbE)
- Improved energy efficiency: Provides a way for clients that have open files to a server to sleep

The SMBv2 protocol was introduced in Windows Vista and Windows Server 2008. The SMBv3 protocol was introduced in Windows 8 and Windows Server 2012. For more information about SMBv2 and SMBv3 capabilities, see the following articles:

- [Overview of file sharing using the SMB 3 protocol in Windows Server](../file-server-smb-overview)
- [1.3 Overview](/en-us/openspecs/windows_protocols/ms-smb2/4287490c-602c-41c0-a23e-140a1f137832)

## Use PowerShell to remove SMBv1

You can use the [Get-WindowsOptionalFeature](/en-us/powershell/module/dism/get-windowsoptionalfeature), [Disable-WindowsOptionalFeature](/en-us/powershell/module/dism/disable-windowsoptionalfeature), and [Enable-WindowsOptionalFeature](/en-us/powershell/module/dism/enable-windowsoptionalfeature) PowerShell commands to detect, disable, and enable an SMBv1 client or server. Run the commands at an elevated command prompt.

Note

The computer restarts after you run the PowerShell commands to disable or enable SMBv1.

- Detect:

    ```powershell
    Get-WindowsOptionalFeature -Online -FeatureName SMB1Protocol
    ```
- Disable:

    ```powershell
    Disable-WindowsOptionalFeature -Online -FeatureName SMB1Protocol
    ```
- Enable:

    ```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName SMB1Protocol
    ```

Tip

You can detect the SMBv1 status without elevation by running the [Get-SmbServerConfiguration](/en-us/powershell/module/smbshare/get-smbserverconfiguration) command: `Get-SmbServerConfiguration | Format-List EnableSMB1Protocol`.

### Remove SMBv1

# [Server](#tab/server)
SMBv1 isn't installed by default on Windows Server 2019 and later versions. On earlier versions of Windows Server, you can use Server Manager to remove SMBv1:

1. On the server that you want to remove SMBv1 from, open Server Manager.
2. On the Server Manager Dashboard, under **Configure this local server**, select **Add roles and features**.
3. On the **Before you begin** page, select **Start the Remove Roles and Features Wizard**, and then on the following page, select **Next**.
4. On the **Select destination server** page, under **Server Pool**, ensure that the server you want to remove the feature from is selected, and then select **Next**.
5. On the **Remove server roles** page, select **Next**.
6. On the **Remove features** page, clear the checkbox for **SMB 1.0/CIFS File Sharing Support**, and then select **Next**.

    ![Screenshot of the Remove features page in the Server Manager dashboard. In the Features list, SMBv1 is highlighted.](media/detect-enable-and-disable-smbv1-v2-v3-1.png)
7. On the **Confirm removal selections** page, confirm that the feature is listed, and then select **Remove**.

# [Client](#tab/client)
On Windows 8.1, Windows 10, and Windows 11, you can use Remove Programs to disable SMBv1.

To disable SMBv1 on these operating systems, take the following steps:

1. In **Control Panel**, select **Programs and Features**.
2. Under **Control Panel Home**, select **Turn Windows features on or off** to open the **Windows Features** dialog.
3. In the **Windows Features** dialog, scroll down the list, clear the checkbox for **SMB 1.0/CIFS File Sharing Support**, and then select **OK**.

    ![Screenshot of the Windows Features dialog. In the Turn Windows features on or off list, an arrow is pointing at SMBv1.](media/detect-enable-and-disable-smbv1-v2-v3-2.png)
4. After Windows applies the change, on the confirmation page, select **Restart now**.

---

## Use the command line or Registry Editor to manage SMB protocols

Starting with the Windows 10 Fall Creators Update and Windows Server 2019, SMBv1 is no longer installed by default. For more information, see [SMBv1 is not installed by default in Windows 10 version 1709, Windows Server version 1709, and later versions](smbv1-not-installed-by-default-in-windows).

When you enable or disable SMBv2 in Windows 8 or Windows Server 2012, SMBv3 is also enabled or disabled. This behavior occurs because these protocols share the same stack.

# [Server](#tab/server)
You can use the [Set-SMBServerConfiguration](/en-us/powershell/module/smbshare/set-smbserverconfiguration) cmdlet to enable or disable the SMBv1, SMBv2, and SMBv3 protocols on a server component. You can use the [Get-SmbServerConfiguration](/en-us/powershell/module/smbshare/get-smbserverconfiguration) cmdlet to retrieve the SMB server configuration.

You don't have to restart the computer after you run the **Set-SMBServerConfiguration** cmdlet.

### SMBv1

- Detect:

    ```powershell
    Get-SmbServerConfiguration | Select EnableSMB1Protocol
    ```
- Disable:

    ```powershell
    Set-SmbServerConfiguration -EnableSMB1Protocol $false
    ```
- Enable:

    ```powershell
    Set-SmbServerConfiguration -EnableSMB1Protocol $true
    ```

For more information, see [Stop using SMB1](https://techcommunity.microsoft.com/blog/filecab/stop-using-smb1/425858).

### SMBv2 and SMBv3

- Detect:

    ```powershell
    Get-SmbServerConfiguration | Select EnableSMB2Protocol
    ```
- Disable:

    ```powershell
    Set-SmbServerConfiguration -EnableSMB2Protocol $false
    ```
- Enable:

    ```powershell
    Set-SmbServerConfiguration -EnableSMB2Protocol $true
    ```

### Enable or disable SMB on Windows 7, Windows Server 2008 R2, Windows Vista, and Windows Server 2008

To enable or disable SMB protocols on an SMB Server that runs Windows 7, Windows Server 2008 R2, Windows Vista, or Windows Server 2008, use Windows PowerShell or Registry Editor, as explained in the following sections.

#### Use Windows PowerShell

You can use the [Get-Item](/en-us/powershell/module/microsoft.powershell.management/get-item), [Get-ItemProperty](/en-us/powershell/module/microsoft.powershell.management/get-itemproperty), and [Set-ItemProperty](/en-us/powershell/module/microsoft.powershell.management/set-itemproperty) cmdlets to detect, enable, and disable SMB protocols.

Note

The commands in the following sections require PowerShell 2.0 or later.

##### SMBv1 on an SMB server

- Detect:

    ```powershell
    Get-Item HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters | ForEach-Object {Get-ItemProperty $_.pspath}
    ```

    The default configuration is `Enabled`. As a result, no registry named value is created, so the command doesn't return an `SMB1` value.
- Disable:

    ```powershell
    Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" SMB1 -Type DWORD -Value 0 -Force
    ```
- Enable:

    ```powershell
    Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" SMB1 -Type DWORD -Value 1 -Force
    ```

Note

You must restart the computer after you make these changes.

For more information, see [Stop using SMB1](https://techcommunity.microsoft.com/blog/filecab/stop-using-smb1/425858).

##### SMBv2 and SMBv3 on an SMB server

- Detect:

    ```powershell
    Get-ItemProperty HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters | ForEach-Object {Get-ItemProperty $_.pspath}
    ```
- Disable:

    ```powershell
    Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" SMB2 -Type DWORD -Value 0 -Force
    ```
- Enable:

    ```powershell
    Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" SMB2 -Type DWORD -Value 1 -Force
    ```

Note

You must restart the computer after you make these changes.

#### Use Registry Editor

Important

Follow the steps in this section carefully. Serious problems might occur if you modify the registry incorrectly. Before you modify it, [back up the registry for restoration](https://support.microsoft.com/help/322756) in case problems occur.

To enable or disable SMBv1 on an SMB server, open Registry Editor and go to the following registry key path:

**HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters**

Configure an entry that has the following properties:

- For the name, use **SMB1**.
- For the type, use **REG\_DWORD**.
- For the data, use **0** for **Disabled** and **1** for **Enabled**. The default value is **1**, or **Enabled**. In this case, no registry key is created.

To enable or disable SMBv2 on an SMB server, open Registry Editor and go to the following registry key path:

**HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters**

Configure an entry that has the following properties:

- For the name, use **SMB2**.
- For the type, use **REG\_DWORD**.
- For the data, use **0** for **Disabled** and **1** for **Enabled**. The default value is **1**, or **Enabled**. In this case, no registry key is created.

Note

 You must restart the computer after you make these changes.

# [Client](#tab/client)
Here's how to detect the status, enable, and disable SMB protocols on an SMB client that runs Windows client and Windows Server.

### SMBv1 on an SMB client

- Detect:

    ```cmd
    sc.exe qc lanmanworkstation
    ```
- Disable:

    ```cmd
    sc.exe config lanmanworkstation depend= bowser/mrxsmb20/nsi
    sc.exe config mrxsmb10 start= disabled
    ```
- Enable:

    ```cmd
    sc.exe config lanmanworkstation depend= bowser/mrxsmb10/mrxsmb20/nsi
    sc.exe config mrxsmb10 start= auto
    ```

For more information, see [Stop using SMB1](https://techcommunity.microsoft.com/blog/filecab/stop-using-smb1/425858).

### SMBv2 and SMBv3 on an SMB client

- Detect:

    ```cmd
    sc.exe qc lanmanworkstation
    ```
- Disable:

    ```cmd
    sc.exe config lanmanworkstation depend= bowser/mrxsmb10/nsi
    sc.exe config mrxsmb20 start= disabled
    ```
- Enable:

    ```cmd
    sc.exe config lanmanworkstation depend= bowser/mrxsmb10/mrxsmb20/nsi
    sc.exe config mrxsmb20 start= auto
    ```

Note

- You must run these commands at an elevated command prompt.
- You must restart the computer after you make these changes.

---

## Use Group Policy to disable SMBv1

This section shows you how to use Group Policy to disable SMBv1. You can use this method on various versions of Windows.

# [Server](#tab/server)
### SMBv1

You can disable SMBv1 on an SMB server by configuring the following new item in the registry:

- Key path: **HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters**
- Registry entry: **SMB1**
- Entry type: **REG\_DWORD**
- Entry data: **0**, for **Disabled**

To use Group Policy to configure this item, take the following steps:

1. Open Group Policy Management Console. Right-click the Group Policy object (GPO) that should contain the new preference item, and then select **Edit**.
2. In the console tree under **Computer Configuration**, expand the **Preferences** folder, and then expand the **Windows Settings** folder.
3. Right-click the **Registry** node, point to **New**, and then select **Registry Item**.

    ![Screenshot of the console tree in Group Policy Management Console. The Registry shortcut menus are visible, with New highlighted in the first menu.](media/detect-enable-and-disable-smbv1-v2-v3-3.png)
4. In the **New Registry Properties** dialog, select or enter the following values:

    - **Action**: **Create**
    - **Hive**: **HKEY\_LOCAL\_MACHINE**
    - **Key Path**: **SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters**
    - **Value name**: **SMB1**
    - **Value type**: **REG\_DWORD**
    - **Value data**: **0**

    ![Screenshot of the New Registry Properties dialog. Values are visible in the action, hive, key path, name, type, and data fields.](media/detect-enable-and-disable-smbv1-v2-v3-4.png)

This procedure disables the SMBv1 server components. You must apply this policy to all necessary workstations, servers, and domain controllers in the domain.

Note

 You can set Windows Management Instrumentation (WMI) filters to exclude specific operating systems or to exclude client or server operating systems. For more information, see [Group Policy Filtering](../../../identity/ad-ds/manage/group-policy/group-policy-processing#group-policy-filtering) and [Create WMI Filters for the GPO](/en-us/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc947846%28v=ws.10%29).

Important

Some systems require access to the SYSVOL folder or other file shares but don't support SMBv2 or SMBv3. Examples of such systems include legacy Windows systems and older Linux and partner systems. Be careful when you disable SMBv1 on domain controllers on these systems.

# [Client](#tab/client)
### SMBv1

To disable the SMBv1 client, you need to update the services registry key to prevent the start of the **MRxSMB10** driver. Then you need to remove the dependency on **MRxSMB10** from the entry for **LanmanWorkstation** so that it can start normally without requiring **MRxSMB10** to first start.

This section shows you how to update and replace the default values in the following two items in the registry:

- Key path: **HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\services\mrxsmb10**
    - Registry entry: **Start**
    - Entry type: **REG\_DWORD**
    - Entry data: **4**, for **Disabled**
- Key path: **HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Services\LanmanWorkstation**
    - Registry entry: **DependOnService**
    - Entry type: REG\_MULTI\_SZ
    - Entry data: **Bowser**,**MRxSmb20**,**NSI**

Note

 The default value includes **MRxSMB10**, which is now removed as dependency.

To configure these entries by using Group Policy, take the following steps:

1. Open Group Policy Management Console. Right-click the GPO that should contain the new preference item, and then select **Edit**.
2. In the console tree under **Computer Configuration**, expand the **Preferences** folder, and then expand the **Windows Settings** folder.
3. Right-click the **Registry** node, point to **New**, and then select **Registry Item**.
4. In the **New Registry Properties** dialog, select or enter the following values:

    - **Action**: **Update**
    - **Hive**: **HKEY\_LOCAL\_MACHINE**
    - **Key Path**: **SYSTEM\CurrentControlSet\services\mrxsmb10**
    - **Value name**: **Start**
    - **Value type**: **REG\_DWORD**
    - **Value data**: **4**

    ![Screenshot of the Start Properties dialog. Values are visible in the action, hive, key path, name, type, and data fields.](media/detect-enable-and-disable-smbv1-v2-v3-5.png)
5. To remove the dependency on the **MRxSMB10** driver that was disabled, open the **New Registry Properties** dialog, and then select or enter the following values:

    - **Action**: **Replace**
    - **Hive**: **HKEY\_LOCAL\_MACHINE**
    - **Key Path**: **SYSTEM\CurrentControlSet\Services\LanmanWorkstation**
    - **Value name**: **DependOnService**
    - **Value type**: **REG\_MULTI\_SZ**
    - **Value data**:
        - **Bowser**
        - **MRxSmb20**
        - **NSI**

    Note

    Don't include bullet points in the three **Value data** strings. List only the strings, as shown in the following screenshot.

    ![Screenshot of the DependOnService Properties dialog. Values are visible in the action, hive, key path, name, type, and data fields.](media/detect-enable-and-disable-smbv1-v2-v3-6.png)

    The default value includes **MRxSMB10** in many versions of Windows. By replacing the default value with these three strings, you effectively remove **MRxSMB10** as a dependency for **LanmanWorkstation**. Instead of the four default values, you use these three values.

    Note

    When you use Group Policy Management Console, you don't have to use quotation marks or commas. Just type each entry on individual lines.
6. To finish disabling SMBv1, restart the targeted systems.

---

### Audit SMBv1 usage

To determine which clients attempt to connect to an SMB server by using SMBv1, you can enable auditing on Windows Server and Windows clients. To enable or disable auditing, use the [Set-SmbServerConfiguration](/en-us/powershell/module/smbshare/set-smbserverconfiguration) cmdlet. To check the auditing status, use the [Get-SmbServerConfiguration](/en-us/powershell/module/smbshare/get-smbserverconfiguration) cmdlet.

- Enable:

    ```powershell
    Set-SmbServerConfiguration -AuditSmb1Access $true
    ```
- Disable:

    ```powershell
    Set-SmbServerConfiguration -AuditSmb1Access $false
    ```
- Detect:

    ```powershell
    Get-SmbServerConfiguration | Select AuditSmb1Access
    ```

After you enable SMBv1 auditing, you can check the `Microsoft-Windows-SMBServer\Audit` event log for access events. Each time a client attempts to use SMBv1 to connect to a server, an entry that has an event ID of 3000 appears in the log.

### Check Group Policy settings

If all the settings are in the same GPO, Group Policy Management displays the following settings:

![Screenshot of the Group Policy Management Editor registry. Three items are visible: DependOnService, SMB1, and Start.](media/detect-enable-and-disable-smbv1-v2-v3-7.png)

### Test and validate the policy

After you complete the configuration steps in Group Policy Management Console, give Group Policy time to apply the updates to its settings. If needed for testing, run `gpupdate /force` at a command prompt, and then review the target computers to make sure that the registry settings are applied correctly. Make sure SMBv2 and SMBv3 are functioning for all other systems in the environment.

Note

After you test the policy, restart the target systems.