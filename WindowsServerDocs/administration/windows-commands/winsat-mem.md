---
layout: Conceptual
title: winsat mem | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/winsat-mem
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for winsat mem command that tests system memory bandwidth using a process similar to the large memory-to-memory buffer copies in multimedia processing.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2023-04-01T00:00:00.0000000Z
locale: en-us
document_id: e3a3f2ff-2324-421e-60cf-9b4d89eda67a
document_version_independent_id: 7347e614-cdb6-3148-07a2-e13d14214670
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/winsat-mem.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/winsat-mem
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/winsat-mem.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f44aac40-7c9f-976b-6f24-11f0e31be84a
---

# winsat mem | Microsoft Learn

Applies to: Windows Server (All supported versions)

The `winsat mem` command tests system memory bandwidth using a process similar to the large memory-to-memory buffer copies in multimedia processing.

## Syntax

```CLI
winsat mem <parameters>
```

### Parameters

| Parameter | Description |
| --- | --- |
| `-up` | Force memory testing with only one thread. The default is to run one thread per physical CPU or core. |
| `-rn` | Specify that the assessment's threads should run at normal priority. The default is to run at priority 15. |
| `-nc` | Specify that the assessment should allocate memory and flag it as uncached. This flag means that the processor's caches is bypassed for copy operations. The default is to run in cached space. |
| `-do <n>` | Specify the distance in bytes, between the end of the source buffer and the beginning of the destination buffer. The default is 64 bytes. The maximum allowable destination offset is 16 MB. Specifying an invalid destination offset results in an error.Note: Zero is a valid value for `<n>`, but negative numbers aren't. |
| `-mint <n>` | Specify the minimum run time in seconds for the assessment. The default is 2.0. The minimum value is 1.0. The maximum value is 30.0.Note: Specifying a `-mint` value greater than the `-maxt` value when the two parameters are used in combination results in an error. |
| `-maxt <n>` | Specify the maximum run time in seconds for the assessment. The default is 5.0. The minimum value is 1.0. The maximum value is 30.0. If used in combination with the `-mint` parameter, the assessment will begin to do periodic statistical checks of its results after the period of time specified in `-mint`. If the statistical checks pass, then the assessment finishes before the period of time specified in `-maxt` has elapsed. If the assessment runs for the period of time specified in `-maxt` without satisfying the statistical checks, then the assessment finishes at that time and return the results it has collected. |
| `-buffersize <n>` | Specify the buffer size that the memory copy test should use. Twice this amount is allocated per CPU, which determines the amount of data copied from one buffer to another. The default is 16 MB. This value is rounded to the nearest 4-KB boundary. The maximum value is 384 MB. The minimum value is 64 KB. Specifying an invalid buffer size results in an error. |
| `-v` | Send verbose output to STDOUT, including status and progress information. Any errors are also be written to the command window. |
| `-xml <file name>` | Save the output of the assessment as the specified XML file. If the specified file exists, it will be overwritten. |
| `-idiskinfo` | Save information about physical volumes and logical disks as part of the `<SystemConfig>` section in the XML output. |
| `-iguid` | Create a globally unique identifier (GUID) in the XML output file. |
| `-note <note text>` | Add the note text to the `<note text>` section in the XML output file. |
| `-icn` | Include the local computer name in the XML output file. |
| `-eef` | Enumerate extra system information in the XML output file. |

## Examples

- To run the assessment for a minimum of 4 seconds and no longer than 12 seconds, using a 32-MB buffer size and saving the results in XML format to the file `memtest.xml`:

```CLI
  winsat mem -mint 4.0 -maxt 12.0 -buffersize 32MB -xml memtest.xml
```

## Remarks

- Minimum requirement to use the `winsat mem` command is membership in the local Administrators group (or equivalent). `Winsat mem` must be executed from an elevated command prompt window.
- To open an elevated command prompt window, select **Start**, select **Accessories**, right-select **Command Prompt**, and select **Run as administrator**.