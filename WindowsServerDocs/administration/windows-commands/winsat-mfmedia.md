---
layout: Conceptual
title: winsat mfmedia | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/winsat-mfmedia
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference for winsat mfmedia, which measures the performance of video decoding (playback) using the Media Foundation framework.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2017-10-16T00:00:00.0000000Z
locale: en-us
document_id: 96cd2c7b-fbc1-3b73-2b4a-a670cac90957
document_version_independent_id: d8b02a89-a475-4bec-60cb-2703464792bc
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/winsat-mfmedia.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/winsat-mfmedia
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/winsat-mfmedia.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 9cf5232c-b5b1-c677-e790-d460f6c1b15b
---

# winsat mfmedia | Microsoft Learn

Measures the performance of video decoding (playback) using the Media Foundation framework.

## Syntax

```
winsat mfmedia <parameters>
```

### Parameters

| Parameters | Description |
| --- | --- |
| -input &lt;file name&gt; | Required: Specify the file containing the video clip to be played or encoded. The file can be in any format that can be rendered by Media Foundation. |
| -dumpgraph | Specify that the filter graph should be saved to a GraphEdit-compatible file before the assessment starts. |
| -ns | Specify that the filter graph should run at the normal playback speed of the input file. By default, the filter graph runs as fast as possible, ignoring presentation times. |
| -play | Run the assessment in decode mode and play any supplied audio content in the file specified in **-input** using the default DirectSound device. By default, audio playback is disabled. |
| -nopmp | Do not make use of the Media Foundation Protected Media Pipeline (MFPMP) process during the assessment. |
| -pmp | Always make use of the MFPMP process during the assessment.Note: If **-pmp** or **-nopmp** is not specified, MFPMP will be used only when necessary. |
| -v | Send verbose output to STDOUT, including status and progress information. Any errors will also be written to the command window. |
| -xml &lt;file name&gt; | Save the output of the assessment as the specified XML file. If the specified file exists, it will be overwritten. |
| -idiskinfo | Save information about physical volumes and logical disks as part of the **&lt;SystemConfig&gt;** section in the XML output. |
| -iguid | Create a globally unique identifier (GUID) in the XML output file. |
| -note note text | Add the note text to the **&lt;note&gt;** section in the XML output file. |
| -icn | Include the local computer name in the XML output file. |
| -eef | Enumerate extra system information in the XML output file. |

## Examples

- To runs the assessment with the input file that is used during a **winsat formal** assessment, without employing the Media Foundation Protected Media Pipeline (MFPMP), on a computer where c:\windows is the location of the Windows folder. 

    ```
    winsat mfmedia -input c:\windows\performance\winsat\winsat.wmv -nopmp
    ```

## Remarks

- Membership in the local Administrators group, or equivalent, is the minimum required to use **winsat**. The command must be executed from an elevated command prompt window.
- To open an elevated command prompt window, click **Start**, click **Accessories**, right-click **Command Prompt**, and click **Run as administrator**.

## Related links