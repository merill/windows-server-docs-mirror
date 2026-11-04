---
layout: Conceptual
title: PowerShell | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/powershell
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the PowerShell command, which opens the PowerShell console from a command prompt.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: 3705aad6-a409-9bff-b98d-c548d4af829f
document_version_independent_id: 263857f1-1214-d14d-98b4-19f9ab4bcd89
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/powershell.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/powershell
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/powershell.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b0d1ed61-222f-1e96-1228-6e435c8a88a5
---

# PowerShell | Microsoft Learn

Windows PowerShell is a task-based command-line shell and scripting language designed especially for system administration. Built on the .NET Framework, Windows PowerShell helps IT professionals and power users control and automate the administration of the Windows operating system and applications that run on Windows.

## Using PowerShell.exe

The **PowerShell.exe** command-line tool starts a Windows PowerShell session in a Command Prompt window. When you use **PowerShell.exe**, you can use its optional parameters to customize the session. For example, you can start a session that uses a particular execution policy or one that excludes a Windows PowerShell profile. Otherwise, the session is the same as any session that is started in the Windows PowerShell console.

- To start a Windows PowerShell session in a Command Prompt window, type `PowerShell`. A **PS** prefix is added to the command prompt to indicate that you are in a Windows PowerShell session.
- To start a session with a particular execution policy, use the **ExecutionPolicy** parameter, and type:

    ```powershell
    PowerShell.exe -ExecutionPolicy Restricted
    ```
- To start a Windows PowerShell session without your Windows PowerShell profiles, use the **NoProfile** parameter, and type:

    ```powershell
    PowerShell.exe -NoProfile
    ```
- To start a session , use the **ExecutionPolicy** parameter, and type:

    ```powershell
    PowerShell.exe -ExecutionPolicy Restricted
    ```
- To see the PowerShell.exe help file, type:

    ```powershell
    PowerShell.exe -help
    PowerShell.exe -?
    PowerShell.exe /?
    ```
- To end a Windows PowerShell session in a Command Prompt window, type `exit`. The typical command prompt returns.

### Remarks

- For a complete list of the **PowerShell.exe** command-line parameters, see [about_PowerShell.Exe](/en-us/powershell/module/microsoft.powershell.core/about/about_powershell_exe).
- For information about other ways to start Windows PowerShell, see [Starting Windows PowerShell](/en-us/powershell/scripting/windows-powershell/starting-windows-powershell).
- Windows PowerShell runs on the Server Core installation option of Windows Server operating systems. However, features that require a graphic user interface, such as the [Windows PowerShell Integrated Scripting Environment (ISE)](/en-us/previous-versions/hh849182%28v=technet.10%29), and the [Out-GridView](/en-us/powershell/module/microsoft.powershell.utility/out-gridview) and [Show-Command](/en-us/powershell/module/microsoft.powershell.utility/show-command) cmdlets, don't run on Server Core installations.

## Related links

- [about_PowerShell.Exe](/en-us/powershell/module/microsoft.powershell.core/about/about_powershell_exe)
- [about_PowerShell_Ise.exe](/en-us/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe)
- [Windows PowerShell](/en-us/powershell/)