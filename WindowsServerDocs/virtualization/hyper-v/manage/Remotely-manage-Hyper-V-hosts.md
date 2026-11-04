---
layout: Conceptual
title: Remotely Manage Hyper-V Hosts | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/manage/remotely-manage-hyper-v-hosts
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Describes version compatibility between Hyper-V hosts and Hyper-V Manager and how to connect to remote hosts in different environments.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-06-30T00:00:00.0000000Z
locale: en-us
document_id: c4cb8cb4-b3d3-3833-c72a-b100d5078966
document_version_independent_id: 438b5485-1c26-b95b-11b1-b592dfc0117f
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/manage/Remotely-manage-Hyper-V-hosts.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/manage/remotely-manage-hyper-v-hosts
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/manage/Remotely-manage-Hyper-V-hosts.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
platformId: 7c825435-034c-e7a6-df72-26ba91feacef
---

# Remotely Manage Hyper-V Hosts | Microsoft Learn

This article lists the supported combinations of Hyper-V hosts and Hyper-V Manager versions and describes how to connect to remote and local Hyper-V hosts so you can manage them.

Hyper-V Manager lets you manage a small number of Hyper-V hosts, both remote and local. It's installed when you install the Hyper-V Management Tools, which you can do either through a full Hyper-V installation or a tools-only installation. If you do a tools-only installation, you can use the tools on computers that don't meet the hardware requirements to host Hyper-V. For details about hardware for Hyper-V hosts, see [System requirements](../host-hardware-requirements). If Hyper-V Manager isn't installed, follow the instructions to Install Hyper-V Manager.

## Connect to a Hyper-V host

To connect to a Hyper-V host from Hyper-V Manager, right-click **Hyper-V Manager** in the left pane, and then select **Connect to Server**.

## Manage Hyper-V on a local computer

Hyper-V Manager doesn't list any computers that host Hyper-V until you add the computer, including a local computer. To do this:

1. In the left pane, right-click **Hyper-V Manager**.
2. Select **Connect to Server**.
3. From **Select Computer**, select **Local computer** and then select **OK**.

If you can't connect:

- It's possible that only the Hyper-V tools are installed. To check whether Hyper-V platform is installed, look for the Virtual Machine Management service. To do so, open the Services desktop app: select **Start**, select the **Start Search** box, type **services.msc**, and then select **Enter**. If the Virtual Machine Management service isn't listed, install the Hyper-V platform by following the instructions in [Install Hyper-V](../get-started/install-the-hyper-v-role-on-windows-server).
- Check whether your hardware meets the requirements. See [System requirements](../host-hardware-requirements).
- Ensure that your user account belongs to the Administrators group or the Hyper-V Administrators group.

## Manage Hyper-V hosts remotely

To manage remote Hyper-V hosts, enable remote management on both the local computer and the remote host.

On Windows Server, open Server Manager &gt;**Local Server** &gt;**Remote management** and then select **Allow remote connections to this computer**.

Or, from either operating system, open Windows PowerShell as Administrator and run:

```PowerShell
Enable-PSRemoting
```

### Connect to hosts in the same domain

To add a remote Hyper-V host to Hyper-V Manager, select **Another computer** in the **Select Computer** dialog and enter the remote host's hostname, NetBIOS name, or fully qualified domain name (FQDN).

Hyper-V Manager offers more types of remote connections, which are described in the following sections.

### Connect to a remote host as a different user

This lets you connect to the Hyper-V host when you're not running on the local computer as a user that's a member of either the Hyper-V Administrators group or the Administrators group on the Hyper-V host. To do this:

1. In the left pane, right-click **Hyper-V Manager**.
2. Select **Connect to Server**.
3. Select **Connect as another user** in the **Select Computer** dialog.
4. Select **Set User**.

### Connect to a remote host by using an IP address

To do this:

1. In the left pane, right-click **Hyper-V Manager**.
2. Select **Connect to Server**.
3. Enter the IP address into the **Another Computer** box.

### Connect to a remote host outside your domain, or with no domain

To do this:

1. On the Hyper-V host to be managed, open a Windows PowerShell session as Administrator.
2. Create the necessary firewall rules for private network zones:

    ```PowerShell
    Enable-PSRemoting
    ```
3. To allow remote access on public zones, enable firewall rules for CredSSP and WinRM:

    ```PowerShell
    Enable-WSManCredSSP -Role server
    ```

    For details, see [Enable-PSRemoting](/en-us/powershell/module/microsoft.powershell.core/enable-psremoting) and [Enable-WSManCredSSP](/en-us/powershell/module/microsoft.wsman.management/enable-wsmancredssp).

Next, configure the computer you'll use to manage the Hyper-V host.

1. Open a Windows PowerShell session as Administrator.
2. Run these commands:

    ```PowerShell
    Set-Item WSMan:\localhost\Client\TrustedHosts -Value "fqdn-of-hyper-v-host"
    ```

    ```PowerShell
    Enable-WSManCredSSP -Role client -DelegateComputer "fqdn-of-hyper-v-host"
    ```
3. You might also need to configure the following group policy:

    - **Computer Configuration** &gt; **Administrative Templates** &gt; **System** &gt; **Credentials Delegation** &gt; **Allow delegating fresh credentials with NTLM-only server authentication**
    - Select **Enable** and add *wsman/fqdn-of-hyper-v-host*.
4. Open Hyper-V Manager.
5. In the left pane, right-click **Hyper-V Manager**.
6. Select **Connect to Server**.

For cmdlet details, see [Set-Item](/en-us/powershell/module/microsoft.powershell.management/set-item) and [Enable-WSManCredSSP](/en-us/powershell/module/microsoft.wsman.management/enable-wsmancredssp).

## Install Hyper-V Manager

To use a UI tool, choose the one that's appropriate for the operating system on the computer where you'll run Hyper-V Manager:

On Windows Server, open Server Manager &gt; **Manage** &gt; **Add roles and features**. Move to the **Features** page and expand **Remote server administration tools** &gt; **Role administration tools** &gt; **Hyper-V management tools**.

On Windows, Hyper-V Manager is available on [any Windows operating system that includes Hyper-V](/en-us/virtualization/hyper-v-on-windows/reference/hyper-v-requirements).

1. On the Windows desktop, select the Start button and begin typing **Programs and features**.
2. In the search results, select **Programs and Features**.
3. In the left pane, select **Turn Windows features on or off**.
4. Expand the Hyper-V folder and select **Hyper-V Management Tools**.
5. To install Hyper-V Manager, select **Hyper-V Management Tools**. If you want to also install the Hyper-V module, select that option.

To use Windows PowerShell, run the following command as Administrator:

```PowerShell
add-windowsfeature rsat-hyper-v-tools
```