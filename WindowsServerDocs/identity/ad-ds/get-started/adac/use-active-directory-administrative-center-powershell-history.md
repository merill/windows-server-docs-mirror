---
layout: Conceptual
title: Use the Active Directory Administrative Center Windows PowerShell History Viewer in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/adac/use-active-directory-administrative-center-powershell-history
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: Learn how to use the Windows PowerShell History Viewer in Active Directory Administrative Center to construct Windows PowerShell scripts.
ms.author: roharwoo
author: robinharwood
ms.date: 2024-09-05T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: d60f9514-323c-855f-4309-fbee497e0722
document_version_independent_id: d60f9514-323c-855f-4309-fbee497e0722
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/get-started/adac/use-active-directory-administrative-center-powershell-history.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/get-started/adac/use-active-directory-administrative-center-powershell-history
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/get-started/adac/use-active-directory-administrative-center-powershell-history.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 2a9cb5e2-e5e9-fbae-c704-4121a35c6635
---

# Use the Active Directory Administrative Center Windows PowerShell History Viewer in Windows Server | Microsoft Learn

Active Directory Administrative Center now provides a complete history of all the Windows PowerShell cmdlets it runs and their arguments and values. You can copy the cmdlet history elsewhere for learning, modification, and re-use. You can create task notes to assist with understanding what your Active Directory Administrative Center commands resulted in Windows PowerShell. You can also filter the history to find points of interest.

In this article, you'll learn how to use the Windows PowerShell History Viewer in Active Directory Administrative Center (ADAC) to construct a Windows PowerShell script.

## Prerequisites

Before you can use the Windows PowerShell History Viewer in Active Directory Administrative Center (ADAC), you need to complete the following prerequisites.

- You must be using a supported version of Windows Server. To learn more about supported versions of Windows Server, see [Release information](../../../../get-started/windows-server-release-info).
- You must have the following Remote Server Administration Tools (RSAT) installed:

    - Active Directory Administrative Center (ADAC)
    - Active Directory module for Windows PowerShell.
- Have a basic understanding of Windows PowerShell. For example, you need to know how piping in Windows PowerShell works. For more information about piping in Windows PowerShell, see [about_Pipelines](/en-us/powershell/module/microsoft.powershell.core/about/about_pipelines).

## Construct a script

The Active Directory Administrative Center Windows PowerShell History Viewer's purpose is for you to learn through practical experience. As actions are executed in the user interface, the equivalent Windows PowerShell command is shown to the user in Windows PowerShell History Viewer.

Using the Active Directory Administrative Center (ADAC), create a user and then use the Windows PowerShell History Viewer to construct a Windows PowerShell script.

1. Sign in to a computer that has the Active Directory module for Windows PowerShell installed.
2. Open Active Directory Administrative Center, either from the Tools menu of the Server Manager console or by running an elevated PowerShell session and typing **dsac.exe**.
3. Select the appropriate target domain in the navigation pane.
4. Navigate to the organizational unit where you want to create the user.
5. In the **Tasks** pane, under **Users**, select **New**, then **User**.
6. Fill in the required fields and click **OK**.
7. Expand the **Windows PowerShell History** pane at the bottom of the ADAC screen.
8. Review the command that was just generated, copy it, and paste it into your desired editor to construct your script. For example, you can now modify the command to create a different user, or create a user in a different organizational unit.

You can repeat this process for other tasks in Active Directory Administrative Center.