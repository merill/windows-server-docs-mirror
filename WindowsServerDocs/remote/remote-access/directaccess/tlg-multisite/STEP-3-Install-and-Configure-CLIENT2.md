---
layout: Conceptual
title: STEP 3 Install and Configure CLIENT2 | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-multisite/step-3-install-and-configure-client2
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to install and configure CLIENT2.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 28558ae6-f4e8-5c86-0355-b3c3ad8bcff7
document_version_independent_id: 338d77f6-ced0-1950-2a15-51395ad04543
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/STEP-3-Install-and-Configure-CLIENT2.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-multisite/step-3-install-and-configure-client2
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-multisite/STEP-3-Install-and-Configure-CLIENT2.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 27dbdd9b-ec80-de0c-5759-54b5d7b3aa1c
---

# STEP 3 Install and Configure CLIENT2 | Microsoft Learn

CLIENT2 is a Windows 7® computer that is used to demonstrate the backwards compatibility of Remote Access running on Windows Server 2016 servers.

1. To install the operating system on CLIENT2. Install Windows® 7 Enterprise or Windows® 7 Ultimate on CLIENT2.
2. To join CLIENT2 to the CORP domain. Join CLIENT2 to the corp.contoso.com domain.

## To install the operating system on CLIENT2

1. Start the installation of Windows 7.
2. When you are prompted for a user name, type **User1**. When you are prompted for a computer name, type **CLIENT2**.
3. When you are prompted for a password, type a strong password twice.
4. When you are prompted for protection settings, click **Use recommended settings**.
5. When you are prompted for your computer's current location, click **Work network**.
6. Connect CLIENT2 to a network that has Internet access and run Windows Update to install the latest updates for Windows 7 , and then disconnect from the Internet.
7. Connect CLIENT2 to the Corpnet subnet.

## User account control

When you configure the Windows 7 operating system, you are required to click **Continue** on the **User Account Control** (UAC) dialog box for some tasks. Several of the configuration tasks require UAC approval. When you are prompted, always click **Continue** to authorize these changes.

## To join CLIENT2 to the CORP domain

1. Click **Start**, right-click **Computer**, and then click **Properties**.
2. On the **System** page, in the **Computer name, domain, and workgroup settings** area, click **Change settings**.
3. On the **System Properties** dialog box, on the **Computer Name** tab, click **Change**.
4. On the **Computer Name/Domain Changes** dialog box, click **Domain**, type **corp.contoso.com**, and then click **OK**.
5. When you are prompted for a user name and password, type the user name and password for the User1 domain account, and then click **OK**.
6. When you see a dialog box that welcomes you to the corp.contoso.com domain, click **OK**.
7. When you see a dialog box that prompts you to restart the computer, click **OK**.
8. On the **System Properties** dialog box, click **Close**, and when you see a dialog that prompts you to restart the computer, click **Restart Now**.
9. After the computer restarts, log on as CORP\User1.