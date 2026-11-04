---
layout: Conceptual
title: How to determine the minimum staging area DFSR needs for a replicated folder | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/troubleshoot/how-to-determine-the-minimum-staging-area-dfsr-needs-for-a-replicated-folder
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: troubleshoot
ms.update-cycle: 1095-days
description: This article is a quick reference guide on how to calculate the minimum staging area needed for DFSR to function properly.
ms.date: 2020-06-10T00:00:00.0000000Z
author: robinharwood
ms.author: roharwoo
ms.topic: troubleshooting
locale: en-us
document_id: 11c0955e-76ac-760e-5aec-96ac6aaa726a
document_version_independent_id: ef870f86-01c0-19c1-bbae-be2966a60bd8
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/troubleshoot/how-to-determine-the-minimum-staging-area-dfsr-needs-for-a-replicated-folder.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../storage/toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: troubleshoot/how-to-determine-the-minimum-staging-area-dfsr-needs-for-a-replicated-folder
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/troubleshoot/how-to-determine-the-minimum-staging-area-dfsr-needs-for-a-replicated-folder.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 225ec604-3a59-550d-04f2-0bdd3058a946
---

# How to determine the minimum staging area DFSR needs for a replicated folder | Microsoft Learn

This article is a quick reference guide on how to calculate the minimum staging area needed for DFSR to function properly. Values lower than these may cause replication to go slowly or stop altogether.

Keep in mind these are *minimums only*. When considering staging area size, the bigger the staging area the better, up to the size of the Replicated Folder. See the section "How to determine if you have a staging area problem" and the blog posts linked at the end of this article for more details on why it is important to have a properly sized staging area.

## General guidance

The staging area quota must be as large as the 32 largest files in the Replicated Folder.

Initial Replication will make much more use of the staging area than day-to-day replication. Setting the staging area higher than the minimum during initial replication is strongly encouraged if you have the drive space available.

## How do you find these X largest files?

Use a PowerShell script to find the 32 or 9 largest files and determine how many gigabytes they add up to. Before beginning, enable maximum path length support, first added in Windows Server 2016 using [Maximum Path Length Limitation](/en-us/windows/win32/fileio/maximum-file-path-limitation?tabs=cmd)

1. Run the following command:

    ```Powershell
    Get-ChildItem c:\\temp -recurse | Sort-Object length -descending | select-object -first 32 | ft name,length -wrap –auto
    ```

    This command will return the file names and the size of the files in bytes. Useful if you want to know what 32 files are the largest in the Replicated Folder so you can “visit” their owners.
2. Run the following command:

    ```Powershell
    Get-ChildItem c:\\temp -recurse | Sort-Object length -descending | select-object -first 32 | measure-object -property length –sum
    ```

    This command will return the total number of bytes of the 32 largest files in the folder without listing the file names.
3. Run the following command:

    ```Powershell
    $big32 = Get-ChildItem c:\\temp -recurse | Sort-Object length -descending | select-object -first 32 | measure-object -property length –sum
    
    $big32.sum /1gb
    ```

    This command will get the total number of bytes of 32 largest files in the folder and do the math to convert bytes to gigabytes for you. This command is two separate lines. You can paste both them into the PowerShell command shell at once or run them back to back.

## Manual Walkthrough

Running command 1 will return results similar to the output below. This example only uses 16 files for brevity. Always use 32 for Windows 2008 and later operating systems.

### Example Data returned by PowerShell

| Name | Length |
| --- | --- |
| **File5.zip** | 10286089216 |
| **archive.zip** | 6029853696 |
| **BACKUP.zip** | 5751522304 |
| **file9.zip** | 5472683008 |
| **MENTOS.zip** | 5241586688 |
| **File7.zip** | 4321264640 |
| **file2.zip** | 4176765952 |
| **frd2.zip** | 4176765952 |
| **BACKUP.zip** | 4078994432 |
| **File44.zip** | 4058424320 |
| **file11.zip** | 3858056192 |
| **Backup2.zip** | 3815138304 |
| **BACKUP3.zip** | 3815138304 |
| **Current.zip** | 3576931328 |
| **Backup8.zip** | 3307488256 |
| **File999.zip** | 3274982400 |

### How to use this data to determine the minimum staging area size:

- Name = Name of the file.
- Length = bytes
- One Gigabyte = 1073741824 Bytes

First, sum the total number of bytes. Next divide the total by 1073741824. Microsoft Excel is an easy way to do this.

### Example

From the example above the total number of bytes = 75241684992. To get the minimum staging area quota needed you need to divide 75241684992 by 1073741824.

> 
> 75241684992 / 1073741824 = 70.07 GB

Based on this data you would set my staging area to 71 GB if you round up to the nearest whole number.

### Real World Scenario:

While a manual walkthrough is interesting it is likely not the best use of your time to do the math yourself. To automate the process, use command 3 from the examples above. The results will look like this

Using the example command 3 without any extra effort except for rounding to the nearest whole number, you can determine that you need a 6 GB staging area quota for d:\docs.

## Do you need to reboot or restart the DFSR service for the changes to be picked Up?

Changes to the staging area quota do not require a reboot or restart of the service to take effect. You will need to wait on AD replication and DFSR’s AD polling cycle for the changes to be applied.

## How to determine if you have a staging area problem

You detect staging area problems by monitoring for specific events IDs on your DFSR servers. The list of events is 4202, 4204, 4206, 4208 and 4212. The texts of these events are listed below. It is important to distinguish between 4202 and 4204 and the other events. It is possible to log a high number of 4202 and 4204 events under normal operating conditions.

### Staging Area Events

> 
> Event ID: **4202** Severity: **Warning**
> 
> The DFS Replication service has detected that the staging space in use for the replicated folder at local path (path) is above the high watermark. The service will attempt to delete the oldest staging files. Performance may be affected.
> 
> Event ID: **4204** Severity: **Informational**
> 
> The DFS Replication service has successfully deleted old staging files for the replicated folder at local path (path). The staging space is now below the high watermark.
> 
> Event ID: **4206** Severity: **Warning**
> 
> The DFS Replication service failed to clean up old staging files for the replicated folder at local path (path). The service might fail to replicate some large files and the replicated folder might get out of sync. The service will automatically retry staging space cleanup in (x) minutes. The service may start cleanup earlier if it detects some staging files have been unlocked.
> 
> Event ID: **4208** Severity: **Warning**
> 
> The DFS Replication service detected that the staging space usage is above the staging quota for the replicated folder at local path (path). The service might fail to replicate some large files and the replicated folder might get out of sync. The service will attempt to clean up staging space automatically.
> 
> Event ID: **4212** Severity: **Error**
> 
> The DFS Replication service could not replicate the replicated folder at local path (path) because the staging path is invalid or inaccessible.

## What is the difference between 4202 and 4208?

Events 4202 and 4208 have similar text; i.e. DFSR detected the staging area usage exceeds the high watermark. The difference is that 4208 is logged after staging area cleanup has run and the staging quota is still exceeded. 4202 is a normal and expected event whereas 4208 is abnormal and requires intervention.

## How many 4202, 4204 events are too many?

There is no single answer to this question. Unlike 4206, 4208 or 4212 events, which are always bad and indicate action is needed, 4202 and 4204 events occur under normal operating conditions. Seeing many 4202 and 4204 events *may* indicate a problem. Things to consider:

1. Is the Replicated Folder (RF) logging 4202 performing initial replication? If so, it is normal to log 4202 and 4204 events. You will want to keep these to down to as few as possible during Initial Replication by providing as much staging area as possible
2. Simply checking the total number of 4202 events is not sufficient. You have to know how many were logged per RF. If you log twenty 4202 events for one RF in a 24 hour period that is high. However if you have 20 Replicated Folders and there is one event per folder, you are doing well.
3. You should examine several days of data to establish trends.

We usually counsel customers to allow no more than one 4202 event per Replicated Folder per day under normal operating conditions. “Normal” meaning no Initial Replication is occurring. We base this on the reasoning that:

1. Time spent cleaning up the staging area is time spent not replicating files. Replication is paused while the staging area is cleared.
2. DFSR benefits from a full staging area using it for RDC and cross-file RDC or replicating the same files to other members
3. The more 4202 and 4204 events you log the greater the odds you will run into the condition where DFSR cannot clean up the staging area or will have to prematurely purge files from the staging area.
4. 4206, 4208 and 4212 events are, in my experience, always preceded and followed by a high number of 4202 and 4204 events.

While allowing for only one 4202 event per RF per day is conservative, it greatly decreases your odds of running into staging area problems and better utilizes your DFSR server’s resources for the intended purpose of replicating files.