---
layout: Conceptual
title: STEP 7 Test DirectAccess Connectivity from the Internet | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-otp-securid/step-7-test-directaccess-connectivity-from-the-internet
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to start to test connectivity from the internet.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 116badc8-4cf2-7b21-1d3c-945ae03e4456
document_version_independent_id: 081a37b3-5199-08eb-b7d5-57d58fc953d3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-otp-securid/STEP-7-Test-DirectAccess-Connectivity-from-the-Internet.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-otp-securid/step-7-test-directaccess-connectivity-from-the-internet
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-otp-securid/STEP-7-Test-DirectAccess-Connectivity-from-the-Internet.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ae028791-5e9b-c139-97af-0a43a5c89e80
---

# STEP 7 Test DirectAccess Connectivity from the Internet | Microsoft Learn

The DirectAccess one-time password (OTP) deployment has been tested from the Homenet subnet, and can now be tested from the Internet.

### To test OTP functionality from the Internet on CLIENT1

1. On CLIENT1 make sure that you are logged on as **User1**. Connect CLIENT1 to the Corpnet subnet.
2. On the **Start** screen, type**powershell.exe**, right-click **powershell**, click **Advanced**, and then click **Run as administrator**. If the **User Account Control** dialog box appears, confirm that the action it displays is what you want, and then click **Yes**.
3. In the Windows PowerShell window, type **gpupdate /force** and press ENTER.
4. Unplug CLIENT1 from the Homenet subnet, connect it to the Internet, and restart the computer.
5. On CLIENT1, open Internet Explorer, and in the address bar, type **`https://app1.corp.contoso.com/`** and press ENTER. Press F5.

    The site should not open.
6. On the **Start** screen, type**RSA**, and click **RSA SecurID Token**.
7. Wait until the RSA SecurID token changes the One-time password, and then click **Copy**.
8. Click the **Network connections** icon in the notification area to access the DA Media Manager.
9. Click **Workplace Connection**, and click **Continue**.
10. Press Control+Alt+Delete, and click the **One-time password (OTP)** tile.
11. Paste the previously copied eight digit tokencode, and click **OK**. Wait for authentication to complete. The DirectAccess Workplace Connection status will now be **Connected**.
12. In Internet Explorer, in the address bar, type **`https://app1.corp.contoso.com/`** and press ENTER. Press F5. You will see the default IIS website on APP1.
13. In the Internet Explorer address bar, type **`https://app2.corp.contoso.com/`** and press ENTER. Press F5. You will see the default IIS website on APP2.
14. On the **Start** screen, type**\\app1\files**, and press ENTER.
15. In the **Files** shared folder window, double-click the **Example.txt** file. You will see the contents of the Example.txt file.
16. On the **Start** screen, type**\\app2\files**, and press ENTER.
17. In the **Files** shared folder window, double-click the **New Text Document.txt** file. You will see the contents of the New Text Document.txt file.