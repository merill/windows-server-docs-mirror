---
layout: Conceptual
title: Configure secure protocol options for Windows HTTP Services (WinHTTP) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/configure-secure-protocol-options-winhttp
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: This article provides information about how to configure secure protocol options for Windows HTTP Services (WinHTTP).
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.date: 2024-03-27T00:00:00.0000000Z
locale: en-us
document_id: 18ef291d-9d40-a9e7-72b4-310f61eb50ed
document_version_independent_id: 18ef291d-9d40-a9e7-72b4-310f61eb50ed
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/configure-secure-protocol-options-winhttp.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/configure-secure-protocol-options-winhttp
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/configure-secure-protocol-options-winhttp.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 85afe696-f052-5d5b-dd1c-b1673515e895
---

# Configure secure protocol options for Windows HTTP Services (WinHTTP) | Microsoft Learn

This how-to guide shows you how to use the `DefaultSecureProtocols` registry entry to choose which protocols for the Windows HTTP Services (WinHTTP).

The `DefaultSecureProtocols` registry entry allows you to specify which SSL protocols should be used when the `WINHTTP_OPTION_SECURE_PROTOCOLS` flag is used. The setting allows applications that were built to use the WinHTTP default flag to be able to use the newer TLS protocols or prevent older SSL based natively without any need for updates to the application.

## Prerequisites

- Calculate the value of `DefaultSecureProtocols` with [WINHTTP_OPTION_SECURE_PROTOCOLS](/en-us/windows/win32/winhttp/option-flags#winhttp_option_secure_protocols).
- Confirm that your account has Administrative rights to the system.
- Make sure that [PowerShell is installed](/en-us/powershell/scripting/install/installing-powershell-on-windows).

## Configure DefaultSecureProtocols

Select which architecture type to add and set the `DefaultSecureProtocols` registry entry:

# [x86](#tab/x86)
1. Open an elevated PowerShell prompt.
2. To create and set the `DefaultSecureProtocols` registry key, run the following command and replace `{value}` with the `DefaultSecureProtocols` value that you selected from Calculate the value.

    ```powershell
    Get-Item -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp" | New-ItemProperty -Name "DefaultSecureProtocols" -Value "{value}"
    ```
3. Either reboot the machine or restart whichever services are using WinHTTP.

# [x64](#tab/x64)
1. Open an elevated PowerShell prompt.
2. To create and set the `DefaultSecureProtocols` registry key, run the following commands and replace `{value}` with the `DefaultSecureProtocols` value that you selected from Calculate the value.

    ```powershell
    # Addresses 64-bit applications
    Get-Item -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp" | New-ItemProperty -Name "DefaultSecureProtocols" -Value "{value}"
    
    # Addresses 32-bit applications
    Get-Item -Path "HKLM:\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp" | New-ItemProperty -Name "DefaultSecureProtocols" -Value "{value}"
    ```
3. Either reboot the machine or restart whichever services are using WinHTTP.

Note

On x64 based systems, having both registry keys present simultaneously is required to ensure proper addressing for both types of applications.

---