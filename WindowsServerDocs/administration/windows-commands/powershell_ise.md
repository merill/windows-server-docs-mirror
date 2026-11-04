---
layout: Conceptual
title: PowerShell_ise | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/powershell_ise
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the PowerShell_ise command, which starts a Windows PowerShell Integrated Scripting Environment (ISE) session.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 6cc70dad-cc80-d9a4-ddd4-b6dd4c045851
document_version_independent_id: d1c51d2d-877a-c587-73fe-1b1b75237476
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/powershell_ise.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/powershell_ise
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/powershell_ise.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 17cbf332-d7e9-eec4-11e4-10ec2a8cc941
---

# PowerShell_ise | Microsoft Learn

Windows PowerShell Integrated Scripting Environment (ISE) is a graphical host application that enables you to read, write, run, debug, and test scripts and modules in a graphic-assisted environment. Key features such as IntelliSense, Show-Command, snippets, tab completion, syntax-coloring, visual debugging, and context-sensitive Help provide a rich scripting experience.

## Using PowerShell.exe

The **PowerShell\_ISE.exe** tool starts a Windows PowerShell ISE session. When you use **PowerShell\_ISE.exe**, you can use its optional parameters to open files in Windows PowerShell ISE or to start a Windows PowerShell ISE session with no profile or with a multithreaded apartment.

- To start a Windows PowerShell ISE session in a Command Prompt window, in Windows PowerShell, or at the **Start** menu, type:

    ```powershell
    PowerShell_Ise.exe
    ```
- To open a script (.ps1), script module (.psm1), module manifest (.psd1), XML file, or any other supported file in Windows PowerShell ISE, type:

    ```powershell
    PowerShell_Ise.exe <filepath>
    ```

    In Windows PowerShell 3.0, you can use the optional **File** parameter as follows:

    ```powershell
    PowerShell_Ise.exe -file <filepath>
    ```
- To start a Windows PowerShell ISE session without your Windows PowerShell profiles, use the **NoProfile** parameter. (The **NoProfile** parameter is introduced in Windows PowerShell 3.0.), type:

    ```powershell
    PowerShell_Ise.exe -NoProfile
    ```
- To see the PowerShell\_ISE.exe help file, type:

    ```powershell
    PowerShell_Ise.exe -help
    PowerShell_Ise.exe -?
    PowerShell_Ise.exe /?
    ```

### Remarks

- For a complete list of the **PowerShell\_ISE.exe** command-line parameters, see [about_PowerShell_Ise.Exe](/en-us/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe).
- For information about other ways to start Windows PowerShell, see [Starting Windows PowerShell](/en-us/powershell/scripting/windows-powershell/starting-windows-powershell).
- Windows PowerShell runs on the Server Core installation option of Windows Server operating systems. However, because Windows PowerShell ISE requires a graphic user interface, it does not run on Server Core installations.

## Related links

- [about_PowerShell_Ise.exe](/en-us/powershell/module/microsoft.powershell.core/about/about_powershell_exe)