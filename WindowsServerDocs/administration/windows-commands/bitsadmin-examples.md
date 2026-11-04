---
layout: Conceptual
title: bitsadmin examples | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-examples
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Examples showing how to use the bitsadmin tool to perform the most common tasks.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-05-31T00:00:00.0000000Z
locale: en-us
document_id: 02aa3815-68e8-f163-38ce-0f17673b08fc
document_version_independent_id: df054fce-6a8b-62df-c9cd-ca040da5c18b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-examples.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-examples
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-examples.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 28edfa33-57ee-334b-eae8-74fcdc1caabf
---

# bitsadmin examples | Microsoft Learn

The following examples show how to use the `bitsadmin` tool to perform the most common tasks.

## Transfer a file

To create a job, add files, activate the job in the transfer queue, and to complete the job:

`bitsadmin /transfer myDownloadJob /download /priority normal https://downloadsrv/10mb.zip c:\\10mb.zip`

BITSAdmin continues to show progress information in the MS-DOS window until the transfer completes or an error occurs.

## Create a download job

To create a download job named *myDownloadJob*:

```
bitsadmin /create myDownloadJob
```

BITSAdmin returns a GUID that uniquely identifies the job. Use the GUID or job name in subsequent calls. The following text is sample output.

### Sample output

`created job {C775D194-090F-431F-B5FB-8334D00D1CB6}`

## Add files to the download job

To add a file to the job:

```
bitsadmin /addfile myDownloadJob https://downloadsrv/10mb.zip c:\\10mb.zip
```

Repeat this call for each file you want to add. If multiple jobs use *myDownloadJob* as their name, you must use the job's GUID to uniquely identify it for completion.

## Activate the download job

After you create a new job, BITS automatically suspends the job. To activate the job in the transfer queue:

```
bitsadmin /resume myDownloadJob
```

If multiple jobs use *myDownloadJob* as their name, you must use the job's GUID to uniquely identify it for completion.

## Determine the progress of the download job

The **/info** switch returns the state of the job and the number of files and bytes transferred. When the state is shown as `TRANSFERRED`, it means that BITS has successfully transferred all files in the job. You can also add the **/verbose** argument to get complete details of the job, and **/list** or **/monitor** to get all the jobs in the transfer queue.

To return the state of the job:

```
bitsadmin /info myDownloadJob /verbose
```

If multiple jobs use *myDownloadJob* as their name, you must use the job's GUID to uniquely identify it for completion.

## Complete the download job

To complete the job after the state changes to `TRANSFERRED`:

```
bitsadmin /complete myDownloadJob
```

You must run the `/complete` switch before the files in the job become available. If multiple jobs use *myDownloadJob* as their name, you must use the job's GUID to uniquely identify it for completion.

## Monitor jobs in the transfer queue using the /list switch

To return the state of the job and the number of files and bytes transferred for all jobs in the transfer queue:

```
bitsadmin /list
```

### Sample output

```
{6AF46E48-41D3-453F-B7AF-A694BBC823F7} job1 SUSPENDED 0 / 0 0 / 0
{482FCAF0-74BF-469B-8929-5CCD028C9499} job2 TRANSIENT_ERROR 0 / 1 0 / UNKNOWN

Listed 2 job(s).
```

## Monitor jobs in the transfer queue using the /monitor switch

To return the state of the job and the number of files and bytes transferred for all jobs in the transfer queue, refreshing the data every 5 seconds:

```
bitsadmin /monitor
```

Note

To stop the refresh, press CTRL+C.

### Sample output

```
MONITORING BACKGROUND COPY MANAGER(5 second refresh)
{6AF46E48-41D3-453F-B7AF-A694BBC823F7} job1 SUSPENDED 0 / 0 0 / 0
{482FCAF0-74BF-469B-8929-5CCD028C9499} job2 TRANSIENT_ERROR 0 / 1 0 / UNKNOWN
{0B138008-304B-4264-B021-FD04455588FF} job3 TRANSFERRED 1 / 1 100379370 / 100379370
```

## Monitor jobs in the transfer queue using the /info switch

To return the state of the job and the number of files and bytes transferred:

```
bitsadmin /info
```

### Sample output

```
GUID: {482FCAF0-74BF-469B-8929-5CCD028C9499} DISPLAY: myDownloadJob
TYPE: DOWNLOAD STATE: TRANSIENT_ERROR OWNER: domain\user
PRIORITY: NORMAL FILES: 0 / 1 BYTES: 0 / UNKNOWN
CREATION TIME: 12/17/2002 1:21:17 PM MODIFICATION TIME: 12/17/2002 1:21:30 PM
COMPLETION TIME: UNKNOWN
NOTIFY INTERFACE: UNREGISTERED NOTIFICATION FLAGS: 3
RETRY DELAY: 600 NO PROGRESS TIMEOUT: 1209600 ERROR COUNT: 0
PROXY USAGE: PRECONFIG PROXY LIST: NULL PROXY BYPASS LIST: NULL
ERROR FILE:    https://downloadsrv/10mb.zip -> c:\10mb.zip
ERROR CODE:    0x80072ee7 - The server name or address could not be resolved
ERROR CONTEXT: 0x00000005 - The error occurred while the remote file was being
processed.
DESCRIPTION:
JOB FILES:
0 / UNKNOWN WORKING https://downloadsrv/10mb.zip -> c:\10mb.zip
NOTIFICATION COMMAND LINE: none
```

## Delete jobs from the transfer queue

To remove all jobs from the transfer queue, use the /reset switch:

```
bitsadmin /reset
```

### Sample output

```
{DC61A20C-44AB-4768-B175-8000D02545B9} canceled.
{BB6E91F3-6EDA-4BB4-9E01-5C5CBB5411F8} canceled.
2 out of 2 jobs canceled.
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)