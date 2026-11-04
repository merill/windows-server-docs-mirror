---
layout: Conceptual
title: Share devices with Hyper-V Windows virtual machines | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/enhanced-session-mode
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: See how to share devices with Hyper-V virtual machines. Find out how to give a virtual machine access to USB devices, audio, microphones, and mounted drives.
keywords: windows 10, windows 11, hyper-v
ms.custom: sfi-image-nochange
author: robinharwood
ms.author: roharwoo
ms.date: 2026-01-21T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 7c01a464-5ccc-a421-2d87-69eb04e8fac1
document_version_independent_id: 7c01a464-5ccc-a421-2d87-69eb04e8fac1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/enhanced-session-mode.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/enhanced-session-mode
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/enhanced-session-mode.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
platformId: 76299e71-129b-4612-9285-5b1d0c3d946b
---

# Share devices with Hyper-V Windows virtual machines | Microsoft Learn

When you use Enhanced Session Mode in the Virtual Machine Connection (VMConnect) tool, you can connect to Hyper-V virtual machines (VMs) by using Remote Desktop Protocol (RDP). Not only does this capability improve your general VM viewing experience, using RDP also provides a way for the VM and your computer to share devices. This functionality is only available for Windows VMs.

Using RDP in Enhanced Session Mode offers many benefits:

- Makes VMs resizable and high-DPI aware
- Improves VM integration:
    - Shared clipboard
    - File sharing via dragging or copying and pasting
- Makes device sharing possible:
    - Microphone and speakers
    - USB devices
    - Data disks, including drive C
    - Printers

Because RDP is turned on by default in Windows, you probably already use RDP to connect to your Windows VMs. This article highlights some of the benefits and hidden options in the connection settings dialog. It shows you how to see your session type, enter Enhanced Session Mode, and configure your session settings.

## Check the session type

You can check your connection type by using the Enhanced Session Mode icon on the VMConnect toolbar. You can also use this button to switch between Basic Session Mode and Enhanced Session Mode.

![Screenshot of VMConnect. On the toolbar, an icon is highlighted that indicates whether enhanced session mode is turned on.](media/enhanced-session-mode/enhanced-session-mode-button-location.png)

| Icon | Connection state |
| --- | --- |
| [![](media/enhanced-session-mode/enhanced-session-mode-basic.png)](media/enhanced-session-mode/enhanced-session-mode-basic.png#lightbox) | You're currently running in Enhanced Session Mode. Selecting this icon reconnects you to your VM in Basic Mode. |
| [![](media/enhanced-session-mode/enhanced-session-mode-connect.png)](media/enhanced-session-mode/enhanced-session-mode-connect.png#lightbox) | You're currently running in Basic Session Mode, but Enhanced Session Mode is available. Selecting this icon reconnects you to your VM in Enhanced Session Mode. |
| [![](media/enhanced-session-mode/enhanced-session-mode-stop.png)](media/enhanced-session-mode/enhanced-session-mode-stop.png#lightbox) | You're currently running in Basic Session Mode. Enhanced Session Mode isn't available for this VM. |

## Configure a VM for Remote Desktop

Enhanced Session Mode requires Remote Desktop to be turned on in the VM. In the Settings app or Start menu, search for **Remote Desktop settings**. Turn on the **Enable Remote Desktop** toggle.

![Screenshot of the Remote Desktop page in the Settings app. The Enable Remote Desktop toggle is in the on position.](media/enhanced-session-mode/remote-desktop-settings.png)

Windows 10 (version 2004 and later) and Windows 11 require an extra setting. If the VMConnect window background doesn't display a sign-in prompt, disable Windows Hello sign-in:

1. Sign in to the VM in basic session mode.
2. Go to **Settings** &gt; **Accounts** &gt; **Sign-in options**.
3. Turn off **For improved security, only allow Windows Hello sign-in for Microsoft accounts on this device**.

    | Windows 11 | Windows 10 |
    | --- | --- |
    | [![Screenshot of the Sign-in options page in VMConnect in Windows 11. The toggle for requiring Windows Hello sign-in is highlighted.](media/enhanced-session-mode/sign-in-options-windows-11.png)](media/enhanced-session-mode/sign-in-options-windows-11.png#lightbox) | [![Screenshot of the Sign-in options page in Settings in Windows 10. The toggle for requiring Windows Hello sign-in is highlighted.](media/enhanced-session-mode/sign-in-options.png)](media/enhanced-session-mode/sign-in-options.png#lightbox) |
4. Sign out of the VM or reboot it before you close the VMConnect window.

    To verify, check that the VMConnect window displays an Enhanced Session Mode sign-in prompt after reconnecting.

## Share drives and devices

You can find the device sharing capabilities of Enhanced Session Mode in the connection dialog that opens when you connect to a VM:

![Screenshot of the connection dialog. Below the size, which is set to 1366 by 768 pixels, a Show Options button is visible.](media/enhanced-session-mode/enhanced-session-mode-default-view.png)

By default, Enhanced Session Mode provides VMs with access to the following resources:

- Clipboard
- Printers
- Audio playback (to host speakers)

To share devices with your VM or to change the default settings:

1. In VMConnect, select the virtual machine that you want to connect to.
2. Select **Show Options**.

    ![Screenshot of the connection dialog. The Show Options button is highlighted.](media/enhanced-session-mode/enhanced-session-mode-show-options.png)
3. Select **Local Resources**, and then adjust the settings.

    ![Screenshot of the connection dialog. The Local Resources tab is highlighted.](media/enhanced-session-mode/enhanced-session-mode-local-resources.png)

    To verify, check that elected resources are available after connecting to the VM.

### Share storage and USB devices

Enhanced Session Mode also supports sharing additional device types, such as:

| Device type | Examples |
| --- | --- |
| Storage | Local drives (including C:), removable drives |
| USB devices | Flash drives, external storage |
| Security devices | Smart cards, Windows Hello companion devices |

To share these devices with a VM:

1. Under **Local devices and resources**, select **More**.

    ![Screenshot of the Local Resources tab of the connection dialog. Under local devices and resources, the More button is highlighted.](media/enhanced-session-mode/enhanced-session-mode-more-devices.png)
2. Select the devices that you want to share with the VM. The system drive, which is drive C on Windows, is especially helpful for file sharing.

    ![Screenshot of the Local Resources page. In a list of devices, the line for Smart cards is selected.](media/enhanced-session-mode/enhanced-session-mode-drives-usb.png)

    To verify, check that shared drives appear under **This PC** in File Explorer within the VM.

### Share audio devices (speakers and microphones)

By default, VMs transfer audio to the host machine using the currently selected audio device. You can configure the following audio settings:

| Setting | Options |
| --- | --- |
| Remote audio playback | Play on this computer, Play on remote computer, Do not play |
| Remote audio recording | Record from this computer (microphone pass-through), Do not record |

To change audio settings:

1. Select **Settings** to configure remote audio settings.

    ![Screenshot of the Local Resources tab of the connection dialog. Under Remote audio, the Settings button is highlighted.](media/enhanced-session-mode/enhanced-session-mode-audio.png)
2. Configure audio and microphone settings.

    ![Screenshot of the Audio settings page. Remote audio is set to play on this computer, and remote audio recording is turned off.](media/enhanced-session-mode/enhanced-session-mode-audio-settings.png)

    For local VMs, **Play on this computer** and **Play on remote computer** produce the same result.

    To verify, check that audio plays through the configured device, and microphone input is detected if recording is enabled.

## Reopen the connection settings

If you don't see the connection dialog or the **Show Options** button, try opening VMConnect independently from either the Windows menu or the command line as an administrator.

```PowerShell
vmconnect.exe
```

VMConnect opens and displays the connection dialog with **Show Options** available.