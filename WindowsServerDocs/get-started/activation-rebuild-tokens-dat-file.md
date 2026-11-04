---
layout: Conceptual
title: Rebuild the Tokens.dat file | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/get-started/activation-rebuild-tokens-dat-file
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: getting-started
ms.update-cycle: 365-days
description: Provides a list of steps for how to rebuild the Tokens.dat file when troubleshooting Windows activation issues.
ms.topic: troubleshooting
ms.date: 2021-06-22T00:00:00.0000000Z
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 07bdf421-565b-5e12-141c-c80b9858df37
document_version_independent_id: 8bad2676-c778-b9e0-bfbd-e8698bbc3c10
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/get-started/activation-rebuild-tokens-dat-file.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: get-started/activation-rebuild-tokens-dat-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/get-started/activation-rebuild-tokens-dat-file.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: c99af18d-0c9d-a7d6-b909-4b25487ec00e
---

# Rebuild the Tokens.dat file | Microsoft Learn

When you troubleshoot Windows activation issues, you may have to rebuild the Tokens.dat file. This article describes in detail how to do this.

## Resolution

To rebuild the Tokens.dat file, follow these steps:

1. Open an elevated Command Prompt window: **For Windows 10**

    1. Open the **Start** menu, and enter **cmd**.
    2. In the search results, right-click **Command Prompt**, and the select **Run as administrator**.

    **For Windows 8.1**

    1. Swipe in from the right edge of the screen, and then tap **Search**. Or, if you are using a mouse, point to the lower-right corner of the screen, and then select **Search**.
    2. In the search box, enter **cmd**.
    3. Swipe across or right-click the displayed **Command Prompt** icon.
    4. Tap or click **Run as administrator**.

    **For Windows 7**

    1. Open the **Start** menu, and enter **cmd**.
    2. In the search results, right-click **cmd.exe**, and the select **Run as administrator**.
2. Enter the list of commands that is appropriate for your operating system.

    For Windows 10, Windows Server 2016 and later versions of Windows, enter the following commands in sequence:

    ```cmd
    net stop sppsvc
    cd %Systemdrive%\Windows\System32\spp\store\2.0\
    ren tokens.dat tokens.bar
    net start sppsvc
    cscript.exe %windir%\system32\slmgr.vbs /rilc
    ```

    For Windows 8.1, Windows Server 2012 and Windows Server 2012 R2, enter the following commands in sequence:

    ```cmd
    net stop sppsvc
    cd %Systemdrive%\Windows\System32\spp\store\
    ren tokens.dat tokens.bar
    net start sppsvc
    cscript.exe %windir%\system32\slmgr.vbs /rilc
    ```

    For Windows 7, Windows Server 2008 and Windows Server 2008 R2, enter the following commands in sequence:

    ```cmd
    net stop sppsvc
    cd %Systemdrive%\Windows\ServiceProfiles\NetworkService\AppData\Roaming\Microsoft\SoftwareProtectionPlatform
    ren tokens.dat tokens.bar
    net start sppsvc
    cscript.exe %windir%\system32\slmgr.vbs /rilc
    ```
3. Restart the computer.

## More information

After you rebuild the Tokens.dat file, you must reinstall your product key by using one of the following methods:

- At the same elevated prompt command, type the following command, and then press Enter:

    ```cmd
    cscript.exe %windir%\system32\slmgr.vbs /ipk <Product key>
    ```

    Important

    Do not use the **/upk** switch to uninstall a product key. To install a product key over an existing product key, use the **/ipk** switch.
- Right-click **My Computer**, select **Properties**, and then select **Change product key**.

For more information about KMS client setup keys, see [KMS client setup keys](kmsclientkeys).