---
layout: FAQ
title: Remote Desktop clients FAQ | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/remotepc/remote-pc-connections-faq
summary: >
  <blockquote>

  </blockquote>

  <p>Now that you set up the Remote Desktop client on your device (Android, Mac, iOS, or Windows), you might have questions. Here are answers to the most commonly asked questions about the Remote Desktop clients.</p>

  <ul>

  <li><a href="/windows-server/remote/remote-desktop-services/clients/remote-desktop-client-faq#setting-up">Setting up</a></li>

  <li><a href="/windows-server/remote/remote-desktop-services/clients/remote-desktop-client-faq#connection,-gateway,-and-networks">Connections, gateway, and networks</a></li>

  <li><a href="/windows-server/remote/remote-desktop-services/clients/remote-desktop-client-faq#web-client">Web client</a></li>

  <li><a href="/windows-server/remote/remote-desktop-services/clients/remote-desktop-client-faq#monitors,-audio,-and-mouse">Monitors, audio, and mouse</a></li>

  <li><a href="/windows-server/remote/remote-desktop-services/clients/remote-desktop-client-faq#mac-client---hardware-questions">Mac hardware</a></li>

  <li><a href="/windows-server/remote/remote-desktop-services/clients/remote-desktop-client-faq#specific-errors">Specific error messages</a></li>

  </ul>

  <p>Most these questions apply to all of the clients, but there are a few client specific items.</p>

  <p>If you have more questions that you'd like us to answer, visit the <a href="https://answers.microsoft.com/">Microsoft Support Community</a> to ask your question.</p>
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Frequently asked questions about the Remote Desktop clients
ms.topic: faq
author: robinharwood
ms.author: roharwoo
ms.date: 2025-02-14T00:00:00.0000000Z
ms.localizationpriority: medium
locale: en-us
document_id: d8a65b47-e9ed-ceab-3605-b07fd6d82551
document_version_independent_id: 476262f4-b99e-38f5-443b-142024b8db5f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/remotepc/remote-pc-connections-faq.yml
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: faq
toc_rel: ../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/remotepc/remote-pc-connections-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/remotepc/remote-pc-connections-faq.yml
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a9a969db-83ea-6fbe-8a0c-031bf050bd32
---

# Remote Desktop clients FAQ | Microsoft Learn

Now that you set up the Remote Desktop client on your device (Android, Mac, iOS, or Windows), you might have questions. Here are answers to the most commonly asked questions about the Remote Desktop clients.

- [Setting up](/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-client-faq#setting-up)
- [Connections, gateway, and networks](/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-client-faq#connection,-gateway,-and-networks)
- [Web client](/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-client-faq#web-client)
- [Monitors, audio, and mouse](/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-client-faq#monitors,-audio,-and-mouse)
- [Mac hardware](/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-client-faq#mac-client---hardware-questions)
- [Specific error messages](/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-client-faq#specific-errors)

Most these questions apply to all of the clients, but there are a few client specific items.

If you have more questions that you'd like us to answer, visit the [Microsoft Support Community](https://answers.microsoft.com/) to ask your question.

## Setting up

### Which PCs can I connect to?

Check out the [supported configuration](remote-desktop-supported-config) article for information about what PCs you can connect to.

### How do I set up a PC for Remote Desktop?

I have my device set up, but I don't think the PC's ready. Help?

The Remote Desktop Setup Wizard walks you through getting your PC ready for remote access. Download and run that tool on your PC to get everything set.

Otherwise, if you prefer to do things manually, read on.

For Windows, complete the following steps:

1. On the device you want to connect to, open **Settings**.
2. Select **System** and then **Remote Desktop**.
3. Use the slider to enable Remote Desktop.
4. In general, it's best to keep the PC awake and discoverable to facilitate connections. Select **Show settings** to go to the power settings for your PC, where you can change this setting. 
    Note

    You can't connect to a PC that's asleep or hibernating, so make sure the settings for sleep and hibernation on the remote PC are set to **Never**. (Hibernation isn't available on all PCs.)

Make note of the name of this PC under **How to connect to this PC**. You need this name to configure the clients.

You can grant permission for specific users to access this PC - to do that, select **Select users that can remotely access this PC**. Members of the Administrators group automatically have access.

For Windows 8.1, follow the instructions to allow remote connections in [Connect to another desktop using Remote Desktop Connections](https://support.microsoft.com/help/17463/windows-7-connect-to-another-computer-remote-desktop-connection#1TC=windows-8).

## Connection, gateway, and networks

### Why can't I connect using Remote Desktop?

Here are some possible solutions to common problems you might encounter when trying to connect to a remote PC. If these solutions don't work, you can find more help on the [Microsoft Community website](https://answers.microsoft.com).

- **The remote PC can't be found.** Make sure you have the right PC name, and then check to see if you entered that name correctly. If you still can't connect, try using the IP address of the remote PC instead of the PC name.
- **There's a problem with the network.** Make sure you have internet connection.
- **The Remote Desktop port might be blocked by a firewall.** If you're using Windows Firewall, follow these steps:

    1. Open Windows Firewall.
    2. Select **Allow an app or feature through Windows Firewall**.
    3. Select **Change settings**. You might be asked for an admin password or to confirm your choice.
    4. Under **Allowed apps and features**, select **Remote Desktop**, and then tap or select **OK**.

        If you're using a different firewall, make sure the port for Remote Desktop (usually 3389) is open.
- **Remote connections might not be set up on the remote PC.** To fix this problem, scroll back up to How do I set up a PC for Remote Desktop? question in this article.
- **The remote PC might only allow PCs to connect that have Network Level Authentication set up.**
- **The remote PC might be turned off.** You can't connect to a PC that's off, asleep, or hibernating. Make sure the settings for sleep and hibernation on the remote PC are set to **Never** (hibernation isn't available on all PCs.).

### Why can't I find or connect to my PC?

Check the following things:

- Is the PC on and awake?
- Did you enter the right name or IP address?

    Important

    Using the PC name requires your network to resolve the name correctly through DNS. In many home networks, you have to use the IP address instead of the host name to connect.
- Is the PC on a different network? Did you configure the PC to let outside connections through? Check out [Allow access to your PC from outside your network](remote-desktop-allow-outside-access) for help.
- Are you connecting to a supported Windows version?

### Why can't I sign in to a remote PC?

If you can see the sign-in screen of the remote PC but you can't sign in, you might not be added to the Remote Desktop Users Group or to any group with administrator rights on the remote PC. Ask your system admin to do add you to the appropriate group.

### Which connection methods are supported for company networks?

If you want to access your office desktop from outside your company network, your company must provide you with a means of remote access. The RD Client currently supports the following connection methods:

- Terminal Server Gateway or Remote Desktop Gateway
- Remote Desktop Web Access
- VPN (through iOS built-in VPN options)

### VPN doesn't work

VPN issues can have several causes. The first step is to verify that the VPN works on the same network as your PC or Mac computer. If you can't test with a PC or Mac, you can try to access a company intranet web page with your device's browser.

Other things to check:

- **The 3G network blocks or corrupts VPN.** There are several 3G providers in the world who seem to block or corrupt 3G traffic. Verify VPN connectivity works correctly for over a minute.
- **L2TP or PPTP VPNs.** If you're using L2TP or PPTP in your VPN, set Send All Traffic to ON in the VPN configuration.
- **VPN is misconfigured.** A misconfigured VPN server can be the reason why the VPN connections never worked or stopped working after some time. Ensure testing with the iOS device's web browser or a PC or Mac on the same network if this problem occurs.

### How can I test if VPN is working properly?

Verify that VPN is enabled on your device. You can test your VPN connection by going to a webpage on your internal network or using a web service which is only available via the VPN.

### How do I configure L2TP or PPTP VPN connections?

If you're using L2TP or PPTP in your VPN, make sure to set **Send all traffic** to **ON** in the VPN configuration.

## Web client

### Which browsers can I use?

The web client supports Microsoft Edge, Mozilla Firefox (v55.0 and later), Safari, and Google Chrome.

### What PCs can I use to access the web client?

The web client supports Windows, macOS, Linux, and ChromeOS. Mobile devices aren't supported at this time.

### Can I use the web client in a Remote Desktop deployment without a gateway?

No. The client requires a Remote Desktop Gateway to connect. Don't know what that means? Ask your admin about it.

### Does the Remote Desktop web client replace the Remote Desktop Web Access page?

No. The Remote Desktop web client is hosted at a different URL than the Remote Desktop Web Access page. You can use either the web client or the Web Access page to view the remote resources in a browser.

### Can I embed the web client in another web page?

This feature isn't supported at the moment.

## Monitors, audio, and mouse

### How do I use all of my monitors?

To use two or more screens, complete the following steps:

1. Right-click the remote desktop that you want to enable multiple screens for, and then select **Edit**.
2. Enable **Use all monitors** and **Full screen**.

### Is bi-directional sound supported?

Bi-directional sound can be configured in the Windows client on a per-connection basis. The relevant settings can be accessed in the **Remote audio** section of the **Local Resources** options tab.

### What can I do if the sound doesn't play?

Sign out of the session (don't just disconnect, sign all the way out), and then sign in again.

## Mac client - hardware questions

### Is retina resolution supported?

Yes, the remote desktop client supports retina resolution.

### How do I enable secondary right-click?

In order to make use of right-click inside an open session you have three options:

- Standard PC two button USB mouse
- Apple Magic Mouse: To enable right-click, select **System Preferences** in the dock, select **Mouse**, and then enable **Secondary select**.
- Apple Magic Trackpad or MacBook Trackpad: To enable right-click, select **System Preferences** in the dock, select **Trackpad**, and then enable **Secondary select**.

### Is AirPrint supported?

No, the Remote Desktop client doesn't support AirPrint for both Mac or iOS clients.

### Why do incorrect characters appear in the session?

If you're using an international keyboard, you might see an issue where the characters that appear in the session don't match the characters you typed on the Mac keyboard.

This problem can occur in the following scenarios:

- You're using a keyboard that the remote session doesn't recognize. When Remote Desktop doesn't recognize the keyboard, it defaults to the language last used with the remote PC.
- You're connecting to a previously disconnected session on a remote PC and that remote PC uses a different keyboard language than the language you're currently trying to use.

You can fix this issue by manually setting the keyboard language for the remote session. See the steps in the next section.

### How do language settings affect keyboards in a remote session?

There are many types of Mac keyboard layouts. Some of these layouts are Mac specific or custom layouts for which an exact match might not be available on the version of Windows you're remoting into. The remote session maps your keyboard to the best matching keyboard language available on the remote PC.

If your Mac keyboard layout is set to the PC version of the language keyboard (for example, French – PC) all your keys should be mapped correctly and your keyboard should just work.

If your Mac keyboard layout is set to the Mac version of a keyboard (for example, French) the remote session maps you to the PC version of the French language. Some of the Mac keyboard shortcuts you're used to using on OSX don't work in the remote Windows session.

If your keyboard layout is set to a variation of a language and if the remote session can't map you to that exact variation, the remote session maps you to the closest language. For example, if you have a Canadian-French, the remote session maps your layout to French. Some of the Mac keyboard shortcuts you're used to using on OSX don't work in the remote Windows session.

If your keyboard layout is set to a layout the remote session can't match at all, your remote session defaults to give you the language you last used with that PC. In this case, or in cases where you need to change the language of your remote session to match your Mac keyboard, you can manually set the keyboard language in the remote session to the language that is the closest match to the one you wish to use as follows.

Use the following instructions to change the keyboard layout inside the remote desktop session:

1. From inside the remote session, open Region and Language. Select **Start &gt; Settings &gt; Time and Language**. Open **Region and Language**.
2. Add the language you want to use. Then close the Region and Language window.
3. Now, in the remote session, you see the ability to switch between languages. (In the right side of the remote session, near the clock.) Select the language you want to switch to (such as **Eng**).

You might need to close and restart the application you're currently using for the keyboard changes to take effect.

## Specific errors

### Why do I get an "Insufficient privileges" error?

You aren't allowed to access the session you want to connect to. The most likely cause is that you're trying to connect to an admin session. Only administrators are allowed to connect to the console. Verify that the console switch is off in the advanced settings of the remote desktop. If connecting to the console isn't the source of the problem contact your system administrator for further assistance.

### Why does the client say that there's no CAL?

When a remote desktop client connects to a Remote Desktop server, the server issues a Remote Desktop Services Client Access License (RDS CAL) stored by the client. Whenever the client connects again it uses its RDS CAL and the server doesn't issue another license. The server issues another license if the RDS CAL on the device is missing or corrupt. When the maximum number of licensed devices is reached, the server doesn't issue new RDS CALs. Contact your network administrator for assistance.

### Why did I get an "Access Denied" error?

The "Access Denied" error is a generated by the Remote Desktop Gateway and the result of incorrect credentials during the connection attempt. Verify your username and password. If the connection worked before and the error occurred recently, you possibly changed your Windows user account password and need to update it in the remote desktop settings.

### What does the "Failed to parse NTLM challenge" error mean?

Misconfiguration on the remote PC causes this error. Make sure the RDP security level setting on the remote PC is set to "Client Compatible." Talk to your system admin if you need assistance with configuring this setting.

### What does "TS\_RAP You aren't allowed to connect to the given host" mean?

This error happens when a Resource Authorization Policy on the gateway server stops your user name from connecting to the remote PC. This problem can happen in the following instances:

- The remote PC name is the same as the name of the gateway. Then, when you try to connect to the remote PC, the connection goes to the gateway instead, which you probably don't have permission to access. If you need to connect to the gateway, don't use the external gateway name as PC name. Instead use "localhost" or the IP address (127.0.0.1), or the internal server name.
- Your user account isn't a member of the user group for remote access.