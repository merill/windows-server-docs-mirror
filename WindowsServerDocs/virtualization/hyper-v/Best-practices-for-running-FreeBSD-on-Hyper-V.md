---
layout: Conceptual
title: Best practices for running FreeBSD on Hyper-V | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/best-practices-for-running-freebsd-on-hyper-v
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: hyper-v
ms.update-cycle: 1095-days
description: Provides recommendations for running FreeBSD on virtual machines
ms.topic: best-practice
ms.author: roharwoo
author: robinharwood
ms.date: 2021-01-08T00:00:00.0000000Z
locale: en-us
document_id: 3478bff8-f57f-679a-192d-46faeab23015
document_version_independent_id: e4c1b6a1-4a87-a524-ecf6-d3022fb4eaa1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/virtualization/hyper-v/Best-practices-for-running-FreeBSD-on-Hyper-V.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: virtualization/hyper-v/best-practices-for-running-freebsd-on-hyper-v
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/virtualization/hyper-v/Best-practices-for-running-FreeBSD-on-Hyper-V.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2ed91286-6cf7-4b83-810d-75d0ee3b09dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6735bd7e-4f7b-457d-b58c-29e6f0198677
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 8a2e240c-132c-af3f-b321-15d6b371f4af
---

# Best practices for running FreeBSD on Hyper-V | Microsoft Learn

This topic contains a list of recommendations for running FreeBSD as a guest operating system on a Hyper-V virtual machine.

## Enable CARP in FreeBSD 10.2 on Hyper-V

The Common Address Redundancy Protocol (CARP) allows multiple hosts to share the same IP address and Virtual Host ID (VHID) to help provide high availability for one or more services. If one or more hosts fail, the other hosts transparently take over so users won't notice a service failure.To use CARP in FreeBSD 10.2, follow the instructions in the [FreeBSD handbook](https://www.freebsd.org/doc/en/books/handbook/carp.html) and do the following in Hyper-V Manager.

- Verify the virtual machine has a Network Adapter and it's assigned a virtual switch. Select the virtual machine and select **Actions** &gt; **Settings**.

![Screenshot of virtual machine settings with network adapter selected](media/hyper-v_settings_networkadapter.png)

- Enable MAC address spoofing. To do this,

    1. Select the virtual machine and select **Actions** &gt; **Settings**.
    2. Expand **Network Adapter** and select **Advanced Features**.
    3. Select **Enable MAC Address spoofing**.

## Create labels for disk devices

During startup, device nodes are created as new devices are discovered. This can mean that device names can change when new devices are added. If you get a ROOT MOUNT ERROR during startup, you should create labels for each IDE partition to avoid conflicts and changes. To learn how, see [Labeling Disk Devices](https://www.freebsd.org/doc/handbook/geom-glabel.html). Below are examples.

Important

Make a backup copy of your fstab before making any changes.

1. Reboot the system into single user mode. This can be accomplished by selecting boot menu option 2 for FreeBSD 10.3+ (option 4 for FreeBSD 8.x), or performing a 'boot -s' from the boot prompt.
2. In Single user mode, create GEOM labels for each of the IDE disk partitions listed in your fstab (both root and swap). Below is an example of FreeBSD 10.3.

    ```bash
    # cat  /etc/fstab
    # Device           Mountpoint      FStype  Options   Dump   Pass#
    /dev/da0p2         /               ufs     rw        1       1
    /dev/da0p3         none            swap    sw        0       0
    
    # glabel  label rootfs  /dev/da0p2
    # glabel  label swap   /dev/da0p3
    # exit
    ```

    Additional information on GEOM labels can be found at: [Labeling Disk Devices](https://www.freebsd.org/doc/handbook/geom-glabel.html).
3. The system will continue with multi-user boot. After the boot completes, edit /etc/fstab and replace the conventional device names, with their respective labels. The final /etc/fstab will look like this:

    ```
    # Device                Mountpoint      FStype  Options         Dump    Pass#
    /dev/label/rootfs       /               ufs     rw              1       1
    /dev/label/swap         none            swap    sw              0       0
    ```
4. The system can now be rebooted. If everything went well, it will come up normally and mount will show:

    ```
    # mount
    /dev/label/rootfs on / (ufs, local, journaled soft-updates)
    devfs on /dev (devfs, local, mutilabel)
    ```

## Use a wireless network adapter as the virtual switch

If the virtual switch on the host is based on wireless network adapter, reduce the ARP expiration time to 60 seconds by the following command. Otherwise the networking of the VM may stop working after a while.

```
   # sysctl net.link.ether.inet.max_age=60
```

See also

- [Supported FreeBSD virtual machines on Hyper-V](supported-freebsd-virtual-machines-on-hyper-v)