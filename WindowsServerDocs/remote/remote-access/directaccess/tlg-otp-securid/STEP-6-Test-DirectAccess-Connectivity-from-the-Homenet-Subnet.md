---
layout: Conceptual
title: STEP 6 Test DirectAccess Connectivity from the Homenet Subnet | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/directaccess/tlg-otp-securid/step-6-test-directaccess-connectivity-from-the-homenet-subnet
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to start to test connectivity from the Homenet subnet.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2023-04-01T00:00:00.0000000Z
locale: en-us
document_id: 5bd15b72-dab3-1468-8c24-2465f449a3f4
document_version_independent_id: c5e1f37b-8f68-2be5-db91-bf11631a027a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/directaccess/tlg-otp-securid/STEP-6-Test-DirectAccess-Connectivity-from-the-Homenet-Subnet.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/directaccess/tlg-otp-securid/step-6-test-directaccess-connectivity-from-the-homenet-subnet
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/directaccess/tlg-otp-securid/STEP-6-Test-DirectAccess-Connectivity-from-the-Homenet-Subnet.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 5ef101df-5c90-6c74-adf3-96bfcde3f864
---

# STEP 6 Test DirectAccess Connectivity from the Homenet Subnet | Microsoft Learn

The DirectAccess one-time password (OTP) deployment is now complete and you can start to test connectivity from the Homenet subnet.

## To test OTP functionality from the Homenet subnet on CLIENT1

1. On CLIENT1, make sure that you're logged on as **User1**.
2. On the **Start** screen, type `powershell.exe`, right-click **powershell**, select **Advanced**, and then select **Run as administrator**. If the **User Account Control** dialog box appears, confirm that the action it displays is what you want, and then select **Yes**.
3. In the Windows PowerShell window, type `gpupdate /force`, and press ENTER.
4. Unplug CLIENT1 from the Corpnet subnet and connect it to the Homenet subnet.
5. On CLIENT1, open Internet Explorer, and in the address bar, type `https://app1.corp.contoso.com/` and press ENTER. Press F5.

    The site shouldn't open.
6. On the **Start** screen, type *RSA*, and select **RSA SecurID Token**.
7. Wait until the RSA SecurID token changes the One-time password, and then select **Copy**.
8. Select the **Network connections** icon in the notification area to access the DA Media Manager.
9. Select **Contoso DirectAccess Connection**, and select **Continue**.
10. Press Control+Alt+Delete, and select the **One-time password (OTP)** tile.
11. Paste the previously copied eight digit tokencode, and select **OK**. Wait for authentication to complete. The DirectAccess Workplace Connection status is **Connected**.
12. In Internet Explorer, in the address bar, type `https://app1.corp.contoso.com/` and press ENTER. Press F5. You see the default IIS website on APP1.
13. In the Internet Explorer address bar, type `https://app2.corp.contoso.com/` and press ENTER. Press F5. You see the default IIS website on APP2.
14. On the **Start** screen, type `\\app1\files`, and press ENTER.
15. In the **Files** shared folder window, double-click the `Example.txt` file. You see the contents of the Example.txt file.
16. On the **Start** screen, type `\\app2\files`, and press ENTER.
17. In the **Files** shared folder window, double-click the `New Text Document.txt` file. You see the contents of the `New Text Document.txt` file.