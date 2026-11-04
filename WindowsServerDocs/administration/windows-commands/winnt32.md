---
layout: Conceptual
title: winnt32 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/winnt32
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for winnt32, which performs an installation of, or upgrade to, a product in Windows Server 2003.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: a724bb49-321e-b6c0-5a9c-878d88d3f499
document_version_independent_id: ccff5e6a-27a4-4774-6533-152635bf2b3f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/winnt32.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/winnt32
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/winnt32.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: b198f1ea-ed77-d74f-c0e3-86cb47d24a64
---

# winnt32 | Microsoft Learn

Performs an installation of or upgrade to a product in Windows Server 2003. You can run **winnt32** at the command prompt on a computer running Windows 95, Windows 98, Windows Millennium edition, Windows NT, Windows 2000, Windows XP, or a product in the Windows Server 2003. If you run **winnt32** on a computer running Windows NT version 4.0, you must first apply Service Pack 5 or later.

## Syntax

```
winnt32 [/checkupgradeonly] [/cmd: <CommandLine>] [/cmdcons] [/copydir:{i386|ia64}\<FolderName>] [/copysource: <FolderName>] [/debug[<Level>]:[ <FileName>]] [/dudisable] [/duprepare: <pathName>] [/dushare: <pathName>] [/emsport:{com1|com2|usebiossettings|off}] [/emsbaudrate: <BaudRate>] [/m: <FolderName>]  [/makelocalsource] [/noreboot] [/s: <Sourcepath>] [/syspart: <DriveLetter>] [/tempdrive: <DriveLetter>] [/udf: <ID>[,<UDB_File>]] [/unattend[<Num>]:[ <AnswerFile>]]
```

#### Parameters

| Parameter | Description |
| --- | --- |
| /checkupgradeonly | Checks your computer for upgrade compatibility with products in Windows Server 2003.<br>if you use this option with **/unattend**, no user input is required. Otherwise, the results are displayed on the screen, and you can save them under the file name you specify. The default file name is **upgrade.txt** in the systemroot folder. |
| /cmd | Instructs setup to carry out a specific command before the final phase of setup. This occurs after your computer has restarted and after setup has collected the necessary configuration information, but before setup is complete. |
| &lt;CommandLine&gt; | Specifies the commandline to be carried out before the final phase of setup. |
| /cmdcons | On an x86-based computer, installs the recovery Console as a startup option. The recovery Console is a command-line interface from which you can perform tasks such as starting and stopping services and accessing the local drive (including drives formatted with NTFS). You can only use the **/cmdcons** option after setup is finished. |
| /copydir | creates an additional folder within the folder in which the operating system files are installed. for example, for x86 and x64-based computers, you could create a folder called *Private\_drivers* within the i386 source folder for your installation, and place driver files in the folder. type **/copydir:i386**\*Private\_drivers* to have setup copy that folder to your newly installed computer, making the new folder location **systemroot**\*Private\_drivers*.<br>- **i386** specifies i386- **ia64** specifies ia64<br><br>You can use **/copydir** to create as many additional folders as you want. |
| &lt;FolderName&gt; | Specifies the folder that you created to hold modifications for your site. |
| /copysource | creates a temporary additional folder within the folder in which the operating system files are installed. You can use **/copysource** to create as many additional folders as you want.<br>Unlike the folders **/copydir** creates, **/copysource** folders are deleted after Setup completes. |
| /debug | creates a debug log at the level specified, for example, **/debug4:Debug.log**. The default log file is **C:\ systemroot\winnt32.log**, and |
| &lt;level&gt; | Level Values and descriptions<br>- 0: Severe Errors- 1: Errors- 2: Default level. Warnings- 3: Information- 4: detailed information for debugging<br><br>Each level includes the levels below it. |
| /dudisable | Prevents Dynamic Update from running. Without Dynamic Update, setup runs only with the original setup files. This option will disable Dynamic Update even if you use an answer file and specify Dynamic Update options in that file. |
| /duprepare | Carries out preparations on an installation share so that it can be used with Dynamic Update files that you downloaded from the Windows Update Web site. This share can then be used for installing Windows XP for multiple clients. |
| &lt;pathName&gt; | Specifies full path name. |
| /dushare | Specifies a share on which you previously downloaded Dynamic Update files (updated files for use with Setup) from the Windows Update Web site, and on which you previously ran **/duprepare:***&lt; pathName&gt;*. When run on a client, specifies that the client installation will make use of the updated files on the share specified in &lt;pathName&gt;. |
| /emsport | Enables or disables Emergency Management Services during setup and after the server operating system has been installed. With Emergency Management Services, you can remotely manage a server in emergency situations that would typically require a local keyboard, mouse, and monitor, such as when the network is unavailable or the server is not functioning properly. Emergency Management Services has specific hardware requirements, and is available only for products in Windows Server 2003.<br>- **com1** is applicable only for x86-based computers (not Itanium architecture-based computers).- **com2**is applicable only for x86-based computers (not Itanium architecture-based computers).- Default. Uses the setting specified in the BIOS Serial Port Console Redirection (SPCR) table, or, in Itanium architecture-based systems, through the EFI console device path. If you specify **usebiossettings** and there is no SPCR table or appropriate EFI console device path, Emergency Management Serices will not be enabled.- **off** disables Emergency Management Services. You can later enable it by modifying the boot settings. |
| /emsbaudrate | for x86-based computers, specifies the baud rate for Emergency Management Services. (The option is not applicable for Itanium architecture-based computers.) Must be used with **/emsport:com1** or **/emsport:com2** (otherwise, **/emsbaudrate** is ignored). |
| &lt;BaudRate&gt; | Specifies baudrate of 9600, 19200, 57600, or 115200. 9600 is the default. |
| /m | Specifies that setup copies replacement files from an alternate location. Instructs setup to look in the alternate location first, and if files are present, to use them instead of the files from the default location. |
| /makelocalsource | Instructs setup to copy all installation source files to your local hard disk. Use **/makelocalsource** when installing from a cd to provide installation files when the cd is not available later in the installation. |
| /noreboot | Instructs setup to not restart the computer after the file copy phase of setup is completed so that you can run another command. |
| /s | Specifies the source location of the files for your installation. To simultaneously copy files from multiple servers, type the **/s:**&lt;Sourcepath&gt; option multiple times (up to a maximum of eight). If you type the option multiple times, the first server specified must be available, or setup will fail. |
| &lt;Sourcepath&gt; | Specifies full source path name. |
| /syspart | On an x86-based computer, specifies that you can copy setup startup files to a hard disk, mark the disk as active, and then install the disk into another computer. When you start that computer, it automatically starts with the next phase of setup.<br>You must always use the **/tempdrive** parameter with the **/syspart** parameter.<br><br>You can start **winnt32** with the **/syspart** option on an x86-based computer running Windows NT 4.0, Windows 2000, Windows XP, or a product in Windows Server 2003. If the computer is running Windows NT version 4.0, it requires Service Pack 5 or later. The computer cannot be running Windows 95, Windows 98, or Windows Millennium edition. |
| &lt;DriveLetter&gt; | Specifies the drive letter. |
| /tempdrive | directs setup to place temporary files on the specified partition.<br>for a new installation, the server operating system will also be installed on the specified partition.<br><br>for an upgrade, the **/tempdrive** option affects the placement of temporary files only; the operating system will be upgraded in the partition from which you run **winnt32**. |
| /udf | Indicates an identifier (&lt;ID&gt;) that setup uses to specify how a Uniqueness Database (UDB) file modifies an answer file (see the **/unattend** option). The UDB overrides values in the answer file, and the identifier determines which values in the UDB file are used. For example, **/udf:RAS\_user,Our\_company.udb** overrides settings specified for the RAS\_user identifier in the Our\_company.udb file. If no &lt;UDB\_file&gt; is specified, setup prompts the user to insert a disk that contains the **$Unique$.udb** file. |
| &lt;ID&gt; | Indicates an identifier used to specify how a Uniqueness Database (UDB) file modifies an answer file. |
| &lt;UDB\_file&gt; | Specifies a Uniqueness Database (UDB) file. |
| /unattend | On an x86-based computer, upgrades your previous version of Windows NT 4.0 Server (with Service Pack 5 or later) or Windows 2000 in unattended setup mode. All user settings are taken from the previous installation, so no user intervention is required during setup. |
| &lt;num&gt; | Specifies the number of seconds between the time that setup finishes copying the files and when it restarts your computer. You can use &lt;Num&gt; on any computer running Windows 98, Windows Millennium edition, Windows NT, Windows 2000, Windows XP, or a product in Windows Server 2003 . If the computer is running Windows NT version 4.0, it requires Service Pack 5 or later. |
| &lt;AnswerFile&gt; | Provides setup with your custom specifications |
| /? | Displays help at the command prompt. |

## Remarks

If you are deploying Windows XP on client computers, you can use the version of winnt32.exe that comes with Windows XP. Another way to deploy Windows XP is to use winnt32.msi, which works through Windows Installer, part of the IntelliMirror set of technologies. For more information about client deployments, see the Windows Server 2003 Deployment Kit, which is described in [Using the Windows Deployment and Resource Kits](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc779317%28v=ws.10%29).

On an Itanium-based computer, **winnt32** can be run from the Extensible Firmware Interface (EFI) or from Windows Server 2003 Enterprise, Windows Server 2003 R2 Enterprise, Windows Server 2003 R2 Datacenter, or Windows Server 2003 Datacenter. Also, on an Itanium architecture-based computer, **/cmdcons** and **/syspart** are not available, and options relating to upgrades are not available. for more information about hardware compatibility, see [Hardware compatibility](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc757927%28v=ws.10%29). for more detailed information about using Dynamic Update and installing multiple clients, see the Windows Server 2003 Deployment Kit, which is described in [Using the Windows Deployment and Resource Kits](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc779317%28v=ws.10%29). for information about modifying boot settings, see the Windows Deployment and Resource Kits for Windows Server 2003. For more information, see [Using the Windows Deployment and Resource Kits](/en-us/previous-versions/windows/it-pro/windows-server-2003/cc779317%28v=ws.10%29). Using the **/unattend** command-line option to automate setup affirms that you have read and accepted the Microsoft License Agreement for Windows Server 2003. Before using this command-line option to install Windows Server 2003 on behalf of an organization other than your own, you must confirm that the end user (whether an individual, or a single entity) has received, read, and accepted the terms of the Microsoft License Agreement for that product. OEMs may not specify this key on machines being sold to end users.

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)