---
layout: Conceptual
title: Advanced Data Deduplication settings | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/data-deduplication/advanced-settings
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: 'Learn more about: Advanced Data Deduplication settings'
ms.topic: concept-article
author: robinharwood
ms.author: roharwoo
ms.date: 2022-02-18T00:00:00.0000000Z
locale: en-us
document_id: afbeabe4-15fa-65dd-9fe2-126ceadc96a1
document_version_independent_id: 7a8534d6-56b3-ae36-463c-158ebb5e86bc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/data-deduplication/advanced-settings.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/data-deduplication/advanced-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/data-deduplication/advanced-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2df8a909-2ab0-ead5-5de3-e8fce4ff501a
---

# Advanced Data Deduplication settings | Microsoft Learn

This document describes how to modify advanced [Data Deduplication](overview) settings. For [recommended workloads](install-enable#enable-dedup-candidate-workloads), the default settings should be sufficient. The main reason to modify these settings is to improve Data Deduplication's performance with other kinds of workloads.

## Modifying Data Deduplication job schedules

The [default Data Deduplication job schedules](understand#job-info) are designed to work well for recommended workloads and be as non-intrusive as possible (excluding the *Priority Optimization* job that is enabled for the [**Backup** usage type](understand#usage-type-backup)). When workloads have large resource requirements, it is possible to ensure that jobs run only during idle hours, or to reduce or increase the amount of system resources that a Data Deduplication job is allowed to consume.

### Changing a Data Deduplication schedule

Data Deduplication jobs are scheduled via Windows Task Scheduler and can be viewed and edited there under the path Microsoft\Windows\Deduplication. Data Deduplication includes several cmdlets that make scheduling easy.

- [`Get-DedupSchedule`](/en-us/powershell/module/deduplication/get-dedupschedule) shows the current scheduled jobs.
- [`New-DedupSchedule`](/en-us/powershell/module/deduplication/new-dedupschedule) creates a new scheduled job.
- [`Set-DedupSchedule`](/en-us/powershell/module/deduplication/set-dedupschedule) modifies an existing scheduled job.
- [`Remove-DedupSchedule`](/en-us/powershell/module/deduplication/remove-dedupschedule) removes a scheduled job.

The most common reason for changing when Data Deduplication jobs run is to ensure that jobs run during off hours. The following step-by-step example shows how to modify the Data Deduplication schedule for a *sunny day* scenario: a hyper-converged Hyper-V host that is idle on weekends and after 7:00 PM on week nights. To change the schedule, run the following PowerShell cmdlets in an Administrator context.

1. Disable the scheduled hourly [Optimization](understand#job-info-optimization) jobs.

    ```PowerShell
     Set-DedupSchedule -Name BackgroundOptimization -Enabled $false
     Set-DedupSchedule -Name PriorityOptimization -Enabled $false
    ```
2. Remove the currently scheduled [Garbage Collection](understand#job-info-gc) and [Integrity Scrubbing](understand#job-info-scrubbing) jobs.

    ```PowerShell
     Get-DedupSchedule -Type GarbageCollection | ForEach-Object { Remove-DedupSchedule -InputObject $_ }
     Get-DedupSchedule -Type Scrubbing | ForEach-Object { Remove-DedupSchedule -InputObject $_ }
    ```
3. Create a nightly Optimization job that runs at 7:00 PM with high priority and all the CPUs and memory available on the system.

    ```PowerShell
     New-DedupSchedule -Name "NightlyOptimization" -Type Optimization -DurationHours 11 -Memory 100 -Cores 100 -Priority High -Days @(1,2,3,4,5) -Start (Get-Date "2016-08-08 19:00:00")
    ```

    Note

    The *date* part of the `System.Datetime` provided to `-Start` is irrelevant (as long as it's in the past), but the *time* part specifies when the job should start.
4. Create a weekly Garbage Collection job that runs on Saturday starting at 7:00 AM with high priority and all the CPUs and memory available on the system.

    ```PowerShell
     New-DedupSchedule -Name "WeeklyGarbageCollection" -Type GarbageCollection -DurationHours 23 -Memory 100 -Cores 100 -Priority High -Days @(6) -Start (Get-Date "2016-08-13 07:00:00")
    ```
5. Create a weekly Integrity Scrubbing job that runs on Sunday starting at 7 AM with high priority and all the CPUs and memory available on the system.

    ```PowerShell
     New-DedupSchedule -Name "WeeklyIntegrityScrubbing" -Type Scrubbing -DurationHours 23 -Memory 100 -Cores 100 -Priority High -Days @(0) -Start (Get-Date "2016-08-14 07:00:00")
    ```

### Available job-wide settings

You can toggle the following settings for new or scheduled Data Deduplication jobs:

| Parameter name | Definition | Accepted values | Why would you want to set this value? |
| --- | --- | --- | --- |
| Type | The type of the job that should be scheduled | - Optimization<br>- GarbageCollection<br>- Scrubbing | This value is required because it is the type of job that you want to schedule. This value cannot be changed after the task has been scheduled. |
| Priority | The system priority of the scheduled job | - High<br>- Normal<br>- Low | This value helps the system determine how to allocate CPU time. *High* will use more CPU time, *low* will use less. |
| Days | The days that the job is scheduled | An array of integers 0-6 representing the days of the week:<br>- 0 = Sunday<br>- 1 = Monday<br>- 2 = Tuesday<br>- 3 = Wednesday<br>- 4 = Thursday<br>- 5 = Friday<br>- 6 = Saturday | Scheduled tasks have to run on at least one day. |
| Cores | The percentage of cores on the system that a job should use | Integers 0-100 (indicates a percentage) | To control what level of impact a job will have on the compute resources on the system |
| DurationHours | The maximum number of hours a job should be allowed to run | Positive integers | To prevent a job for running into a workload's non-idle hours |
| Enabled | Whether the job will run | True/false | To disable a job without removing it |
| Full | For scheduling a full Garbage Collection job | Switch (true/false) | By default, every fourth job is a full Garbage Collection job. With this switch, you can schedule full Garbage Collection to run more frequently. |
| InputOutputThrottle | Specifies the amount of input/output throttling applied to the job | Integers 0-100 (indicates a percentage) | Throttling ensures that jobs don't interfere with other I/O-intensive processes. |
| Memory | The percentage of memory on the system that a job should use | Integers 0-100 (indicates a percentage) | To control what level of impact the job will have on the memory resources of the system |
| Name | The name of the scheduled job | String | A job must have a uniquely identifiable name. |
| ReadOnly | Indicates that the scrubbing job processes and reports on corruptions that it finds, but does not run any repair actions | Switch (true/false) | You want to manually restore files that sit on bad sections of the disk. |
| Start | Specifies the time a job should start | `System.DateTime` | The *date* part of the `System.Datetime` provided to *Start* is irrelevant (as long as it's in the past), but the *time* part specifies when the job should start. |
| StopWhenSystemBusy | Specifies whether Data Deduplication should stop if the system is busy | Switch (True/False) | This switch gives you the ability to control the behavior of Data Deduplication--this is especially important if you want to run Data Deduplication while your workload is not idle. |

## Modifying Data Deduplication volume-wide settings

### Toggling volume settings

You can set the volume-wide default settings for Data Deduplication via the [usage type](understand#usage-type) that you select when you enable a deduplication for a volume. Data Deduplication includes cmdlets that make editing volume-wide settings easy:

- [`Get-DedupVolume`](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730705%28v=ws.11%29)
- [`Set-DedupVolume`](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730705%28v=ws.11%29)

The main reasons to modify the volume settings from the selected usage type are to improve read performance for specific files (such as multimedia or other file types that are already compressed) or to fine-tune Data Deduplication for better optimization for your specific workload. The following example shows how to modify the Data Deduplication volume settings for a workload that most closely resembles a general purpose file server workload, but uses large files that change frequently.

1. See the current volume settings for Cluster Shared Volume 1.

    ```PowerShell
     Get-DedupVolume -Volume C:\ClusterStorage\Volume1 | Select *
    ```
2. Enable OptimizePartialFiles on Cluster Shared Volume 1 so that the MinimumFileAge policy applies to sections of the file rather than the whole file. This ensures that the majority of the file gets optimized even though sections of the file change regularly.

    ```PowerShell
     Set-DedupVolume -Volume C:\ClusterStorage\Volume1 -OptimizePartialFiles
    ```

### Available volume-wide settings

| Setting name | Definition | Accepted values | Why would you want to modify this value? |
| --- | --- | --- | --- |
| ChunkRedundancyThreshold | The number of times that a chunk is referenced before a chunk is duplicated into the hotspot section of the Chunk Store. The value of the hotspot section is that so-called "hot" chunks that are referenced frequently have multiple access paths to improve access time. | Positive integers | The main reason to modify this number is to increase the savings rate for volumes with high duplication. In general, the default value (100) is the recommended setting, and you shouldn't need to modify this. |
| ExcludeFileType | File types that are excluded from optimization | Array of file extensions | Some file types, particularly multimedia or files that are already compressed, do not benefit very much from being optimized. This setting allows you to configure which types are excluded. |
| ExcludeFolder | Specifies folder paths that should not be considered for optimization | Array of folder paths | If you want to improve performance or keep content in particular paths from being optimized, you can exclude certain paths on the volume from consideration for optimization. |
| InputOutputScale | Specifies the level of IO parallelization (IO queues) for Data Deduplication to use on a volume during a post-processing job | Positive integers ranging 1-36 | The main reason to modify this value is to decrease the impact on the performance of a high IO workload by restricting the number of IO queues that Data Deduplication is allowed to use on a volume. Note that modifying this setting from the default may cause Data Deduplication's post-processing jobs to run slowly. |
| MinimumFileAgeDays | Number of days after the file is created before the file is considered to be in-policy for optimization. | Positive integers (inclusive of zero) | The **Default** and **Hyper-V** usage types set this value to 3 to maximize performance on hot or recently created files. You may want to modify this if you want Data Deduplication to be more aggressive or if you do not care about the extra latency associated with deduplication. |
| MinimumFileSize | Minimum file size that a file must have to be considered in-policy for optimization | Positive integers (bytes) greater than 32 KB | The main reason to change this value is to exclude small files that may have limited optimization value to conserve compute time. |
| NoCompress | Whether the chunks should be compressed before being put into the Chunk Store | True/False | Some types of files, particularly multimedia files and already compressed file types, may not compress well. This setting allows you to turn off compression for all files on the volume. This would be ideal if you are optimizing a dataset that has a lot of files that are already compressed. |
| NoCompressionFileType | File types whose chunks should not be compressed before going into the Chunk Store | Array of file extensions | Some types of files, particularly multimedia files and already compressed file types, may not compress well. This setting allows compression to be turned off for those files, saving CPU resources. |
| OptimizeInUseFiles | When enabled, files that have active handles against them will be considered as in-policy for optimization. | True/false | Enable this setting if your workload keeps files open for extended periods of time. If this setting is not enabled, a file would never get optimized if the workload has an open handle to it, even if it's only occasionally appending data at the end. |
| OptimizePartialFiles | When enabled, the MinimumFileAge value applies to segments of a file rather than to the whole file. | True/false | Enable this setting if your workload works with large, often edited files where most of the file content is untouched. If this setting is not enabled, these files would never get optimized because they keep getting changed, even though most of the file content is ready to be optimized. |
| Verify | When enabled, if the hash of a chunk matches a chunk we already have in our Chunk Store, the chunks are compared byte-by-byte to ensure they are identical. | True/false | This is an integrity feature that ensures that the hashing algorithm that compares chunks does not make a mistake by comparing two chunks of data that are actually different but have the same hash. In practice, it is extremely improbable that this would ever happen. Enabling the verification feature adds significant overhead to the optimization job. |

## Modifying Data Deduplication system-wide settings

Data Deduplication has additional system-wide settings that can be configured via [the registry](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc755256%28v=ws.11%29). These settings apply to all of the jobs and volumes that run on the system. Extra care must be given whenever editing the registry.

For example, you may want to disable full Garbage Collection. More information about why this may be useful for your scenario can be found in Frequently asked questions. To edit the registry with PowerShell:

- If Data Deduplication is running in a cluster:

    ```PowerShell
      Set-ItemProperty -Path HKLM:\System\CurrentControlSet\Services\ddpsvc\Settings -Name DeepGCInterval -Type DWord -Value 0xFFFFFFFF
      Set-ItemProperty -Path HKLM:\CLUSTER\Dedup -Name DeepGCInterval -Type DWord -Value 0xFFFFFFFF
    ```
- If Data Deduplication is not running in a cluster:

    ```PowerShell
      Set-ItemProperty -Path HKLM:\System\CurrentControlSet\Services\ddpsvc\Settings -Name DeepGCInterval -Type DWord -Value 0xFFFFFFFF
    ```

### Available system-wide settings

| Setting name | Definition | Accepted values | Why would you want to change this? |
| --- | --- | --- | --- |
| WlmMemoryOverPercentThreshold | This setting allows jobs to use more memory than Data Deduplication judges to actually be available. For example, a setting of 300 would mean that the job would have to use three times the assigned memory to get canceled. | Positive integers (a value of 300 means 300% or 3 times) | If you have another task that will stop if Data Deduplication takes more memory |
| DeepGCInterval | This setting configures the interval at which regular Garbage Collection jobs become [full Garbage Collection jobs](advanced-settings#faq-full-v-regular-gc). A setting of n would mean that every n^th^ job was a full Garbage Collection job. Note that full Garbage Collection is always disabled (regardless of the registry value) for volumes with the [Backup Usage Type](understand#usage-type-backup). `Start-DedupJob -Type GarbageCollection -Full` may be used if full Garbage Collection is desired on a Backup volume. | Integers (-1 indicates disabled) | See [this frequently asked question](advanced-settings#faq-why-disable-full-gc) |

## Frequently asked questions

**I changed a Data Deduplication setting, and now jobs are slow or don't finish, or my workload performance has decreased. Why?** These settings give you a lot of power to control how Data Deduplication runs. Use them responsibly, and [monitor performance](run#monitoring-dedup).

**I want to run a Data Deduplication job right now, but I don't want to create a new schedule--can I do this?** Yes, [all jobs can be run manually](run#running-dedup-jobs-manually).

**What is the difference between full and regular Garbage Collection?** There are two types of [Garbage Collection](understand#job-info-gc):

- *Regular Garbage Collection* uses a statistical algorithm to find large unreferenced chunks that meet a certain criteria (low in memory and IOPs). Regular Garbage Collection compacts a chunk store container only if a minimum percentage of the chunks is unreferenced. This type of Garbage Collection runs much faster and uses fewer resources than full Garbage Collection. The default schedule of the regular Garbage Collection job is to run once a week.
- *Full Garbage Collection* does a much more thorough job of finding unreferenced chunks and freeing more disk space. Full Garbage Collection compacts every container even if just a single chunk in the container is unreferenced. Full Garbage Collection will also free space that may have been in use if there was a crash or power failure during an Optimization job. Full Garbage Collection jobs will recover 100 percent of the available space that can be recovered on a deduplicated volume at the cost of requiring more time and system resources compared to a regular Garbage Collection job. The full Garbage Collection job will typically find and release up to 5 percent more of the unreferenced data than a regular Garbage Collection job. The default schedule of the full Garbage Collection job is to run every fourth time Garbage Collection is scheduled.

**Why would I want to disable full Garbage Collection?**

- Garbage Collection could adversely affect the volume's lifetime shadow copies and the size of incremental backup. High churn or I/O-intensive workloads may see a degradation in performance by full Garbage Collection jobs.
- You can manually run a full Garbage Collection job from PowerShell to clean up leaks if you know your system crashed.