---
layout: Conceptual
title: bitsadmin transfer | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/bitsadmin-transfer
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the bitsadmin transfer command, which transfers one or more files.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 99b005b4-7f53-d738-fa43-b6d910d6f478
document_version_independent_id: 1d82dbb8-9204-2724-f418-b6c35b3eb4e2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/bitsadmin-transfer.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/bitsadmin-transfer
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/bitsadmin-transfer.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ffee16f6-f099-64dd-0bf8-906ff98a85ff
---

# bitsadmin transfer | Microsoft Learn

Transfers one or more files. By default, the BITSAdmin service creates a download job that runs at **NORMAL** priority and updates the command window with progress information until the transfer is complete or until a critical error occurs,

The service completes the job if it successfully transfers all the files and cancels the job if a critical error occurs. The service does not create the job if it is unable to add files to the job or if you specify an invalid value for *type* or *job\_priority*. To transfer more than one file, specify multiple `<RemoteFileName>-<LocalFileName>` pairs. The pairs must be space-delimited.

Note

The BITSAdmin command continues to run if a transient error occurs. To end the command, press CTRL+C.

## Syntax

```
bitsadmin /transfer <name> [<type>] [/priority <job_priority>] [/ACLflags <flags>] [/DYNAMIC] <remotefilename> <localfilename>
```

### Parameters

| Parameter | Description |
| --- | --- |
| name | The name of the job. This command can't be a GUID. |
| type | Optional. Sets the type of job, including:<br>- **/DOWNLOAD.** The default value. Choose this type for download jobs.<br>- **/UPLOAD.** Choose this type for upload jobs. |
| priority | Optional. Sets the priority of the job, including:<br>- FOREGROUND<br>- HIGH<br>- NORMAL<br>- LOW |
| ACLflags | Optional. Indicates that you want to maintain the owner and ACL information with the file being downloaded. Specify one or more of the values, including:<br>- **o** - Copy owner information with file.<br>- **g** - Copy group information with file.<br>- **d** - Copy discretionary access control list (DACL) information with file.<br>- **s** - Copy system access control list (SACL) information with file. |
| /DYNAMIC | Configures the job using [**BITS\_JOB\_PROPERTY\_DYNAMIC\_CONTENT**](/en-us/windows/win32/api/bits5_0/ne-bits5_0-bits_job_property_id), which relaxes the server-side requirements. |
| remotefilename | The name of the file after it's transferred to the server. |
| localfilename | The name of the file that resides locally. |

## Examples

To start a transfer job named *myDownloadJob*:

```
bitsadmin /transfer myDownloadJob http://prodserver/audio.wma c:\downloads\audio.wma
```

## Related links

- [Command-Line Syntax Key](command-line-syntax-key)
- [bitsadmin command](bitsadmin)