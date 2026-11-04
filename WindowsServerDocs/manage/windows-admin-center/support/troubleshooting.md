---
layout: Conceptual
title: Windows Admin Center common troubleshooting steps | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/support/troubleshooting
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-admin-center
ms.update-cycle: 365-days
feedback_product_url: https://aka.ms/wacfeedback
description: Windows Admin Center common troubleshooting steps
ms.topic: troubleshooting-general
author: robinharwood
ms.author: roharwoo
ms.date: 2025-06-24T00:00:00.0000000Z
locale: en-us
document_id: f168bf93-cc54-2a7e-2c1c-7c649a8458d2
document_version_independent_id: 0edf20e5-268c-b5df-93a6-85186eb4ba86
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/windows-admin-center/support/troubleshooting.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/windows-admin-center/support/troubleshooting
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/windows-admin-center/support/troubleshooting.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 3b3853c0-b417-4fec-7793-a0d9ba14cbbd
---

# Windows Admin Center common troubleshooting steps | Microsoft Learn

This article describes how to diagnose and resolve issues in Windows Admin Center. If you're having an issue with a specific tool, check to see if you're experiencing a [known issue](known-issues).

## Prerequisites

Windows Admin Center is supported on the following operating systems:

- For Windows client, your device must be running Windows 10 version 1709 or later (Fall Creators Update).
- For Windows Server, your device must be running Windows Server 2016 or later.

## The Windows Admin Center installer fails to load

```error
The Module 'Microsoft.PowerShell.LocalAccounts' could not be loaded.
```

This failure can happen if your default PowerShell module path has been modified or removed. To resolve this issue, make sure that `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules` is the first item in your PSModulePath environment variable. You can set this path by running the following command in an elevated PowerShell window:

```powershell
[Environment]::SetEnvironmentVariable("PSModulePath","%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules;" + ([Environment]::GetEnvironmentVariable("PSModulePath","User")),"User")
```

## The Windows Admin Center gateway installation failed

If your installation fails, or Windows Admin Center fails to open after install, try uninstalling and reinstalling. This issue can happen if you have an older version of a modernized gateway build installed, and you're trying to update to a newer version.

## I receive an error in my web browser

```error
This site/page can't be reached
```

**If the Windows Admin Center app is installed as a standalone app**:

- Check to make sure Windows Admin Center is running in the System tray. You can also open **Task Manager** and check if **Windows Admin Center** is running.
- Make sure you're using either Microsoft Edge or Google Chrome as your web browser with the latest updates.
- Did you select the correct certificate on [first launch](../use/get-started#open-windows-admin-center-on-a-windows-pc)?

    Try opening your browser in a private or incognito window. If Windows Admin Center loads successfully, clear your browser cache in your regular session and try again.
- Did you recently upgrade Windows 10 to a new build or version?

    This might have cleared your trusted hosts settings. See the Configure TrustedHosts list section.

**If the Windows Admin Center app is installed as a Gateway on Windows Server**:

- Make sure you're using either Microsoft Edge or Google Chrome as your web browser with the latest updates.
- Open **Task Manager**, select the **Services** tab, then make sure that **ServerManagementGateway** or **Windows Admin Center** is running.
- Test the network connection to the Gateway. Run the following command. Replace `<Port>` and `<Gateway>` with your port number and gateway hostname (or IP address):

    ```powershell
    Test-NetConnection -Port <Port> -ComputerName <Gateway> -InformationLevel Detailed
    ```

**If the Windows Admin Center app is installed in an Azure Windows Server VM**:

- Verify and update the inbound port rule for HTTPS through the [network security group](/en-us/azure/virtual-network/network-security-groups-overview) or firewall settings.

**Ensure the Windows Remote Management (WinRM) service is running on both the gateway machine and managed node**:

1. Open the run dialog by pressing the **Windows Key** + **R**.
2. Type **services.msc** and then press **Enter**.
3. In the **Services** window, check if the **WinRM** service is running and set to automatically start.

## I'm receiving WinRM error messages while managing servers

WinRM doesn't allow credential delegation by default. To allow delegation, the computer needs to have Credential Security Support Provider (CredSSP) enabled temporarily.

If you're receiving WinRM error messages, try the [Manual troubleshooting](/en-us/azure/azure-local/manage/troubleshoot-credssp#manual-troubleshooting) section of [Troubleshoot CredSSP](/en-us/azure/azure-local/manage/troubleshoot-credssp) to resolve them.

**Did you upgrade your server from Windows 2016 to a later release?**

- This might have cleared your trusted hosts settings. See the Configure TrustedHosts list section to update your settings.

## I'm receiving a TLS error message

```error
Can't connect securely to this page. This might be because the site uses outdated or unsafe TLS security settings.
```

Your machine is restricted to HTTP/2 connections. Windows Admin Center uses integrated Windows authentication, which isn't supported in HTTP/2. Add the following two registry values under **HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Services\Http\Parameters** on the machine running the browser to remove the HTTP/2 restriction:

```powershell
$registryPath = "HKLM:\SYSTEM\CurrentControlSet\Services\Http\Parameters"
New-ItemProperty -Path $registryPath -Name "EnableHttp2Cleartext" -PropertyType DWORD -Value 0 -Force
New-ItemProperty -Path $registryPath -Name "EnableHttp2Tls" -PropertyType DWORD -Value 0 -Force
```

## I'm having trouble with the Remote Desktop, Events, and PowerShell tools

These three tools require the web socket protocol, which is commonly blocked by proxy servers and firewalls. If you're using Google Chrome, there's a [known issue](known-issues#google-chrome) with web sockets and NTLM authentication.

## I can connect to some servers, but not others

- Sign in to the gateway machine locally and run `Enter-PSSession -ComputerName <machine name>` in an elevated PowerShell window, replacing `<machine name>` with the name of the machine you're trying to manage in Windows Admin Center.

    - If the session connects successfully, the PowerShell prompt updates to show you're connected to the target machine. This indicates that connectivity and permissions are likely configured correctly.
    - If the session doesn't successfully connect, it might relate to WinRM issues, network connectivity problems, or authorization issues.
- If your environment uses a workgroup instead of a domain, see using Windows Admin Center in a workgroup.

## I'm receiving a page authorization error message

```error
You are not authorized to view this page. If you recently updated Windows Admin Center, you may need to restart your browser, and then refresh the page.
```

Make sure to select the **Windows Admin Center Client** certificate when prompted on the first launch, and not any other certificate. If you select any other certificate, you'll receive this error message. To resolve this error, restart your browser and refresh the page, and select the **Windows Admin Center Client** certificate. If you continue to get the same error, try clearing the browser cache or switching to another browser. If none of these troubleshooting steps resolve the issue, you may need to uninstall Windows Admin Center, reboot your device, and reinstall it.

## Using Windows Admin Center in a workgroup

### What account are you using?

Make sure the credentials you're using are a member of the target server's local administrators group. In some cases, WinRM also requires membership in the Remote Management Users group. If you're using a local user account that is **not the built-in administrator account**, you'll need to enable the policy on the target machine by running the following command in an elevated PowerShell window on the target machine:

```powershell
$registryPath = "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System"
New-ItemProperty -Path $registryPath -Name "LocalAccountTokenFilterPolicy" -PropertyType DWORD -Value 1 -Force
```

### Are you connecting to a workgroup machine on a different subnet?

To connect to a workgroup machine that isn't on the same subnet as the gateway, make sure the firewall port for WinRM (TCP 5985) allows inbound traffic on the target machine. You can run the following command in an elevated PowerShell window on the target machine to create this firewall rule:

- **Windows Server device**

    ```powershell
    Set-NetFirewallRule -Name WINRM-HTTP-In-TCP-PUBLIC -RemoteAddress Any
    ```
- **Windows client device**

    ```powershell
    Set-NetFirewallRule -Name WINRM-HTTP-In-TCP -RemoteAddress Any
    ```

### Configure TrustedHosts list

When you install Windows Admin Center, you can allow it to automatically manage the gateway's TrustedHosts setting. This is necessary in workgroup environments or when using local administrator credentials within a domain. If you choose not to let Windows Admin Center manage this setting, you'll need to configure TrustedHosts manually.

To modify TrustedHosts using PowerShell, run the following commands in an elevated PowerShell window:

1. View your current TrustedHosts setting.

    ```powershell
    Get-Item WSMan:\localhost\Client\TrustedHosts
    ```

    Warning

    If the current settings of your TrustedHosts file isn't empty, running the following commands overwrite your settings. We recommend that you export the current settings to a text file so you can restore it later if needed. The following command exports only the entries from the **Value** column:

    `(Get-Item WSMan:\localhost\Client\TrustedHosts).Value | Out-File C:\OldTrustedHosts.txt`

    Replace the `Out-File` location with your location of choice.
2. Set TrustedHosts to the IP, FQDN, or NetBIOS name of the machines you intend to manage:

    ```powershell
    Set-Item WSMan:localhost\Client\TrustedHosts -Value '192.168.1.1,server01.contoso.com,server02'
    ```

    Tip

    For an easy way to set all TrustedHosts at once, you can use a wildcard.

    ```powershell
    Set-Item WSMan:\localhost\Client\TrustedHosts -Value '*'
    ```
3. When you're done testing, you can issue the following command to clear your TrustedHosts setting:

    ```powershell
    Clear-Item WSMan:localhost\Client\TrustedHosts
    ```
4. If you previously exported your settings and want to restore them, run the following command and replace the `Get-Content` location to where you previously exported your text file:

    ```powershell
    $oldTrustedHosts = Get-Content C:\OldTrustedHosts.txt
    Set-Item WSMan:\localhost\Client\TrustedHosts -Value $oldTrustedHosts
    ```

### Can I use Windows Admin Center with workgroup clusters?

At this time we do not recommend using Windows Admin Center to manage workgroup clusters. As an alternative, PowerShell can be used for workgroup cluster management.

## I previously had Windows Admin Center installed, and now nothing else can use the same TCP/IP port

Run these two commands in an elevated command shell window:

```
netsh http delete sslcert ipport=0.0.0.0:443
netsh http delete urlacl url=https://+:443/
```

## Azure features don't work properly in Microsoft Edge

Microsoft Edge has [known issues](https://github.com/AzureAD/azure-activedirectory-library-for-js/wiki/Known-issues-on-Edge) related to security zones that affect Azure login in Windows Admin Center.

If you're having trouble using Azure features when using Microsoft Edge, perform these steps to add the required URLs:

1. Select **Start**, type **Internet Options** and open it.
2. Select the **Security** tab, select **Trusted sites**, then select the **Sites** button.
3. Add the following URLs in the **Add the website to the zone** field and select **Add** for each one:

    - Your gateway URL
    - `https://login.microsoftonline.com`
    - `https://login.live.com`
4. Select **Close** and then select **OK**.
5. Open **Microsoft Edge**, paste this link in the search bar `edge://settings/content/popups?search=pop-up`, then press **Enter**.

    1. Under the **Allowed to send pop-ups and use redirects** section, select **Add site**.
    2. Add the following URLs and select **Add** to add each one:

        - Your gateway URL
        - `https://login.microsoftonline.com`
        - `https://login.live.com`

## Provide feedback on issues

Go to Event Viewer &gt; Application and Services &gt; Microsoft-ServerManagementExperience and look for any errors or warnings.

File a bug on the [Windows Admin Center](https://aka.ms/wacfeedback) feedback intake that describes your issue.

Include any errors or warning you find in the event log including the following information:

- Platform where Windows Admin Center is **installed** (Windows client or Windows Server).

    - If installed on a Server device, provide the Windows version (**Windows Key + R**, type **winver**, then press **Enter**) of **the machine running the browser** to access Windows Admin Center:
    - Are you using the self-signed certificate created by the installer?
    - If you're using your own certificate, does the subject name match the machine?
    - If you're using your own certificate, does it specify an alternate subject name?
- Did you install with the default port setting?

    - If not, which port did you specify?
- Is the machine where Windows Admin Center is **installed** joined to a domain?
- Is the machine that you're **trying to manage** joined to a domain?
- Provide the Windows version (**Windows Key + R**, type **winver**, then press **Enter**) where Windows Admin Center is **installed**:
- What browser are you using?
- If you're using Google Chrome, what is the version?

    - Open Google Chrome, type **chrome://version**, then press **Enter**.

## How can I collect HAR files for feedback?

An HTTP Archive Format (HAR) file is a log of a web browser's interaction with a site. This information is crucial for troubleshooting and debugging.

To collect a HAR file in Microsoft Edge or Google Chrome, follow these steps:

1. Open your browser, press **F12** to open Developer Tools window, then select the **Network** tab.
2. Select the **Clear** icon to clean up the network log.
3. Select the **Preserve log** check box.
4. Reproduce the issue.
5. After reproducing the issue, select the icon to **Export HAR**.
6. Specify where you want to save the HAR log and select **Save**.

Warning

Before sharing your HAR files with Microsoft, review and redact any sensitive data, such as passwords or personal information.