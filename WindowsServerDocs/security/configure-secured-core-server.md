---
layout: Conceptual
title: Configure Secured-core server for Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/security/configure-secured-core-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how to configure Secured-core server in Windows Server using the Windows Security app, Group Policy and Windows Admin Center.
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2023-05-26T00:00:00.0000000Z
ms.custom: template-how-to-pattern
locale: en-us
document_id: 3926b54a-b620-59e6-d23d-272c173087e7
document_version_independent_id: 3926b54a-b620-59e6-d23d-272c173087e7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/security/configure-secured-core-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: security/configure-secured-core-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/security/configure-secured-core-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: a62ad3ef-684b-4415-6b01-c4c8b679ec19
---

# Configure Secured-core server for Windows Server | Microsoft Learn

Secured-core is a collection of capabilities that offers built-in hardware, firmware, driver and operating system security features. This article shows you how to configure Secured-core server by using Windows Admin Center, the Windows Server Desktop Experience, and Group Policy.

Secured-core server is designed to deliver a secure platform for critical data and applications. For more information, see [What is Secured-core server?](secured-core-server)

## Prerequisites

Before you can configure Secured-core server, you must have the following security components installed and enabled in the BIOS:

- Secure Boot.
- Trusted Platform Module (TPM) 2.0.
- System firmware must meet preboot DMA protection requirements and set appropriate flags in ACPI tables to opt into and enable Kernel DMA Protection. To learn more about Kernel DMA Protection, see [Kernel DMA Protection (Memory Access Protection) for OEMs](/en-us/windows-hardware/design/device-experiences/oem-kernel-dma-protection).
- A processor with support enabled in the BIOS for:
    - Virtualization extensions.
    - Input/Output Memory Management Unit (IOMMU).
    - Dynamic Root of Trust for Measurement (DRTM).
    - Transparent Secure Memory Encryption is also required for AMD based systems.

Important

Enabling each of the security features in the BIOS can vary based on your hardware vendor. Make sure to check your hardware manufacturer's Secured-core server enablement guide.

You can find hardware certified for Secured-core server from the [Windows Server Catalog](https://www.windowsservercatalog.com/), and Azure Local servers in the [Azure Local Catalog](https://azurelocalsolutions.azure.microsoft.com/#/catalog?FeatureSupported=securedCoreServer).

## Enable security features

To configure Secured-core server you need to enable specific Windows Server security features, select the relevant method and follow the steps.

# [GUI](#tab/gui)
Here's how to enable Secured-core server using the user interface.

1. From the Windows desktop, open the **Start** menu, select **Windows Administrative Tools**, open **Computer Management**.
2. In Computer management, select **Device Manager**, resolve any device error if necessary.
    1. For AMD based systems, confirm the DRTM Boot Driver device is present before continuing
3. From Windows desktop, open the **Start** menu, select **Windows Security**.
4. Select **Device security &gt; Core isolation details**, then enable **Memory Integrity** and **Firmware Protection**. You might not be able to enable Memory Integrity until you've enabled Firmware Protection first and restarted your server.
5. Restart your server when prompted.

Once your server has restarted, your server is enabled for Secured-core server.

# [Windows Admin Center](#tab/WAC)
Here's how to enable Secured-core server using Windows Admin Center.

1. Sign into your Windows Admin Center portal.
2. Select the server you want to connect to.
3. Select **Security** using the left-hand panel, then select the **Secured-core** tab.
4. Check the Security Features with a status of *Not configured*, then select **Enable**.
5. When notified, select **Schedule system reboot** to persist the changes.
6. Select either the **Restart immediately** or **Schedule restart** at a time suitable for your workload.

Once your server has restarted, your server is enabled for Secured-core server.

# [Group Policy](#tab/group-policy)
Here's how to enable Secured-core server for domain members using Group Policy.

1. Open the **Group Policy Management Console**, create or edit a policy applied to your server.
2. In the console tree, select **Computer Configuration &gt; Administrative Templates &gt; System &gt; Device Guard**.
3. For the setting, right-click **Turn On Virtualization Based Security** and select **Edit**.
4. Select **Enabled**, from the drop down menus select the following:

    1. Select **Secure Boot and DMA Protection** for the Platform Security Level.
    2. Select either **Enabled without lock** or **Enabled with UEFI lock** for Virtualization Based Protect of Code Integrity.
    3. Select **Enabled** for the Secure Launch Configuration.

Caution

If you use **Enabled with UEFI lock** for Virtualization Based Protect of Code Integrity, it cannot be disabled remotely. To disable the feature, you must set the Group Policy to **Disabled** as well as remove the security functionality from each computer, with a physically present user, in order to clear configuration persisted in UEFI.
5. Select **OK** to complete the configuration.
6. Restart your server to apply the Group Policy.

Once your server has restarted, your server is enabled for Secured-core server.

---

## Verify Secured-core server configuration

Now that you've configured Secured-core server, select the relevant method to verify your configuration.

# [GUI](#tab/gui)
Here's how to verify your Secured-core server is configured using the user interface.

1. From the Windows desktop, open the **Start** menu, type `msinfo32.exe`to open System Information. From the System Summary page, confirm:
    1. **Secure Boot State** and **Kernel DMA Protection** is On.
    2. **Virtualization-based security** is Running.
    3. **Virtualization-based security Services** Running shows **Hypervisor enforced Code Integrity** and **Secure Launch**.

        [![Screenshot showing the System Information application window with Secured-core enabled.](media/secured-core/secured-core-msinfo32.png)](media/secured-core/secured-core-msinfo32.png#lightbox)

# [Windows Admin Center](#tab/WAC)
Here's how to verify your Secured-core server is configured using Windows Admin Center.

1. Sign into your Windows Admin Center portal.
2. Select the server you want to connect to.
3. Select **Security** using the left-hand panel, then select the **Secured-core** tab.
4. Check the all Security Features have a status of *Configured*.

    [![Screenshot showing the Windows Admin Center security extension in a browser window with Secured-core enabled.](media/secured-core/windows-admin-center-server.png)](media/secured-core/windows-admin-center-server.png#lightbox)

# [Group Policy](#tab/group-policy)
To verify Group Policy has applied to your server, run the following command from an elevated command prompt.

```cli
gpresult /SCOPE COMPUTER /R /V
```

In the output, confirm the Device Guard settings are applied under the Administrative Templates section. The following example shows the output when the settings are applied.

```cli
        Administrative Templates
        ------------------------
            GPO: Local Group Policy
                Folder Id: SOFTWARE\Policies\Microsoft\Windows\DeviceGuard\LsaCfgFlags
                Value:       3, 0, 0, 0
                State:       Enabled

            GPO: Local Group Policy
                Folder Id: SOFTWARE\Policies\Microsoft\Windows\DeviceGuard\RequirePlatformSecurityFeatures
                Value:       3, 0, 0, 0
                State:       Enabled

            GPO: Local Group Policy
                Folder Id: SOFTWARE\Policies\Microsoft\Windows\DeviceGuard\EnableVirtualizationBasedSecurity
                Value:       1, 0, 0, 0
                State:       Enabled

            GPO: Local Group Policy
                Folder Id: SOFTWARE\Policies\Microsoft\Windows\DeviceGuard\HypervisorEnforcedCodeIntegrity
                Value:       2, 0, 0, 0
                State:       Enabled

            GPO: Local Group Policy
                Folder Id: SOFTWARE\Policies\Microsoft\Windows\DeviceGuard\HVCIMATRequired
                Value:       0, 0, 0, 0
                State:       Enabled

            GPO: Local Group Policy
                Folder Id: SOFTWARE\Policies\Microsoft\Windows\DeviceGuard\ConfigureSystemGuardLaunch
                Value:       1, 0, 0, 0
                State:       Enabled
```

Verify your Secured-core server is configured by following the steps.

1. From the Windows desktop, open the **Start** menu, type `msinfo32.exe`to open System Information. From the System Summary page, confirm:
    1. **Secure Boot State** and **Kernel DMA Protection** is On.
    2. **Virtualization-based security** is Running.
    3. **Virtualization-based security Services** Running shows **Hypervisor enforced Code Integrity** and **Secure Launch**.

        [![Screenshot showing the System Information application window with Secured-core enabled.](media/secured-core/secured-core-msinfo32.png)](media/secured-core/secured-core-msinfo32.png#lightbox)

---