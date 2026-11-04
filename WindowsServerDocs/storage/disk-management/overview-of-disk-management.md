---
layout: Conceptual
title: Overview of Disk Management | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/disk-management/overview-of-disk-management
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn how to use the Disk Management system utility in Windows to initialize drives, extend volumes, shrink partitions, and change drive letters.
ms.date: 2025-06-24T00:00:00.0000000Z
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: 71f2f298-d7e1-02d4-029f-38a6fa6f440b
document_version_independent_id: e69cb941-3ab6-8fdd-ff12-1f761eeb8241
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/disk-management/overview-of-disk-management.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/disk-management/overview-of-disk-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/disk-management/overview-of-disk-management.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4cf82621-cdad-c345-898b-a8bde5cdbf6a
---

# Overview of Disk Management | Microsoft Learn

Disk Management is a system utility in Windows for advanced storage operations. You can use the utility to see information about each drive on your computer and all partitions in each drive. The utility shows partition details, including statistics and the amount of space allocated or used.

Some of the tasks you can complete with Disk Management include:

- Set up a new drive on your computer by [initializing a new disk](initialize-new-disks)
- [Extend a basic volume](extend-a-basic-volume) into unclaimed space in a volume on the same drive
- [Shrink a basic volume or partition](shrink-a-basic-volume), such as to enable extending into a neighboring partition
- [Change a drive letter](change-a-drive-letter) or assign a new drive letter

## View drives and partitions

The following image shows the Disk Management overview for several drives. **Disk 0** has three partitions, and **Disk 1** has two partitions. On **Disk 0**, the *C:* drive for Windows uses the most disk space. Two other partitions for system operations and recovery use a smaller amount of disk space.

[![Screenshot that shows the Disk Management utility in Windows as described in the text.](media/disk-management.png)](media/disk-management.png#lightbox)

Windows typically includes three partitions on your main drive, which is usually the *C:\* drive:

| Partition | Purpose |
| --- | --- |
| **Local Disk (C:)** | Stores the Windows operating system installation. Common storage location for other apps and files. |
| **EFI System** | Supports the start (*boot*) process for the computer and operating system in modern computers. |
| **Recovery** | Stores tools that support Windows recovery operations when the computer doesn't start or in other problem scenarios. For more information, see [Recovery options in Windows](https://support.microsoft.com/windows/recovery-options-in-windows-31ce2444-7de3-818c-d626-e3b5a3024da5). |

Important

Disk Management might show the **EFI System** and **Recovery** partitions as 100 percent *free*. However, these partitions store critical files required for the computer to operate properly. As such, the partitions are usually close to full. The recommended practice is to not modify these partitions in any way.

## Prepare resources for tasks

Some Disk Management tasks require special information about your system like a BitLocker recovery key, or an existing resource such as a restore point. The following articles can help you prepare the information and resources you need to complete the tasks:

- [Create a recovery drive](https://support.microsoft.com/windows/create-a-recovery-drive-abb4691b-5324-6d4a-8766-73fab304c246)
- [Create a restore point for your system in Windows](https://support.microsoft.com/windows/system-protection-e9126e6e-fa64-4f5f-874d-9db90e57645a)
- [Back up and restore your PC with Windows Backup](https://support.microsoft.com/windows/back-up-and-restore-with-windows-backup-87a81f8a-78fa-456e-b521-ac0560e32338)
- [Find your BitLocker recovery key](https://support.microsoft.com/windows/find-your-bitlocker-recovery-key-6b71ad27-0b89-ea08-f143-056f5ab347d6)
- [Find lost files after you upgrade to Windows](https://support.microsoft.com/windows/find-lost-files-after-the-upgrade-to-windows-10-or-11-10af49aa-b372-b067-a334-2314401297a9)

## Use other tools for tasks

The Disk Management utility supports a wide range of drive tasks, but some tasks can be completed only by using another tool.

Here are some common disk management tasks that you need to complete by using other tools in Windows:

- [Free up drive space in Windows](https://support.microsoft.com/windows/free-up-drive-space-in-windows-85529ccb-c365-490d-b548-831022bc9b32)
- [Defragment or optimize your data drives in Windows](https://support.microsoft.com/windows/defragment-optimize-your-data-drives-in-windows-54d4fed1-c96e-46db-b843-8c6b34bd27a4)
- Pool multiple hard drives like a redundant array of independent disks (RAID) with [Storage Spaces in Windows](https://support.microsoft.com/windows/storage-spaces-in-windows-b6c8b540-b8d8-fb8a-e7ab-4a75ba11f9f2)

## Troubleshoot issues

When a Disk Management task reports an error, or a procedure doesn't work as expected, try one of the following options to resolve the issue:

- Review suggestions in the [Troubleshooting Disk Management](troubleshooting-disk-management) article.
- Search the [Microsoft Support Community](https://answers.microsoft.com) site for posts about files, folders, and storage.
- [Ask a question](https://answers.microsoft.com) to get input from Microsoft or other community members.
- [Contact Microsoft Support](https://support.microsoft.com/contactus/) about the issue.