---
layout: Conceptual
title: Running Data Deduplication | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/data-deduplication/run
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: 'Learn more about: Running Data Deduplication'
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2022-02-18T00:00:00.0000000Z
locale: en-us
document_id: 0329c2dd-339b-609b-f774-b45d4f797d37
document_version_independent_id: eacf6698-a92f-7924-1344-c0b96a166e66
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/data-deduplication/run.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/data-deduplication/run
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/data-deduplication/run.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: f8fde79b-df4c-a2be-ecc2-ecdee7a838fa
---

# Running Data Deduplication | Microsoft Learn

## Running Data Deduplication jobs manually

You can run every scheduled Data Deduplication job manually by using the following PowerShell cmdlets:

- [`Start-DedupJob`](/en-us/powershell/module/deduplication/start-dedupjob/): Starts a new Data Deduplication job
- [`Stop-DedupJob`](/en-us/powershell/module/deduplication/stop-dedupjob/): Stops a Data Deduplication job already in progress (or removes it from the queue)
- [`Get-DedupJob`](/en-us/powershell/module/deduplication/get-dedupjob/): Shows all the active and queued Data Deduplication jobs

All [settings that are available when you schedule a Data Deduplication job](advanced-settings#modifying-job-schedules-available-settings) are also available when you start a job manually except for the scheduling-specific settings. For example, to start an [Optimization](understand#job-info-optimization) job manually with high priority, maximum CPU usage, and maximum memory usage, execute the following PowerShell command with administrator privilege:

```PowerShell
Start-DedupJob -Type Optimization -Volume <Your-Volume-Here> -Memory 100 -Cores 100 -Priority High
```

## Monitoring Data Deduplication

### Job successes

Because Data Deduplication uses a post-processing model, it is important that [Data Deduplication jobs](understand#job-info) succeed. An easy way to check the status of the most recent job is to use the [`Get-DedupStatus`](/en-us/powershell/module/deduplication/get-dedupstatus/) PowerShell cmdlet. Periodically check the following fields:

- For the [Optimization job](understand#job-info-optimization), look at `LastOptimizationResult` (0 = Success), `LastOptimizationResultMessage`, and `LastOptimizationTime` (should be recent).
- For the [Garbage Collection job](understand#job-info-gc), look at `LastGarbageCollectionResult` (0 = Success), `LastGarbageCollectionResultMessage`, and `LastGarbageCollectionTime` (should be recent).
- For the [Integrity Scrubbing job](understand#job-info-scrubbing), look at `LastScrubbingResult` (0 = Success), `LastScrubbingResultMessage`, and `LastScrubbingTime` (should be recent).

Note

More detail on job successes and failures can be found in the Windows Event Viewer under `\Applications and Services Logs\Windows\Deduplication\Operational`.

### Optimization rates

One indicator of [Optimization job](understand#job-info-optimization) failure is a downward-trending optimization rate which might indicate that the Optimization jobs are not keeping up with the rate of changes, or churn. You can check the optimization rate by using the [`Get-DedupStatus`](/en-us/powershell/module/deduplication/get-dedupstatus/) PowerShell cmdlet.

Important

`Get-DedupStatus` has two fields that are relevant to the optimization rate: `OptimizedFilesSavingsRate` and `SavingsRate`. These are both important values to track, but each has a unique meaning.

- `OptimizedFilesSavingsRate` applies only to the files that are 'in-policy' for optimization (`space used by optimized files after optimization / logical size of optimized files`).
- `SavingsRate` applies to the entire volume (`space used by optimized files after optimization / total logical size of the optimization`).

## Disabling Data Deduplication

To turn off Data Deduplication, run the [Unoptimization job](understand#job-info-unoptimization). To undo volume optimization, run the following command:

```PowerShell
Start-DedupJob -Type Unoptimization -Volume <Desired-Volume>
```

Important

The Unoptimization job will fail if the volume does not have sufficient space to hold the unoptimized data.

## Frequently Asked Questions

**Is there a System Center Operations Manager Management Pack available to monitor Data Deduplication?** Yes. Data Deduplication can be monitored through the System Center Management Pack for File Server. For more information, see the [Guide for System Center Management Pack for File Server 2012 R2](https://download.microsoft.com/download/6/F/7/6F7A33B9-9383-48ED-9252-23C2C8AD1BDA/MPGuide_FileServer2012R2.doc) document.