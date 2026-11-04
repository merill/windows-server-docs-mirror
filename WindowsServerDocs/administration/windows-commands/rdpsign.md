---
layout: Conceptual
title: rdpsign | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/rdpsign
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: windows-commands
ms.update-cycle: 1095-days
description: Reference article for the rdpsign command, which enables you to digitally sign a Remote Desktop Protocol (.rdp) file.
ms.topic: reference
ms.author: roharwoo
author: robinharwood
ms.date: 2018-07-11T00:00:00.0000000Z
locale: en-us
document_id: d1c96184-10e3-b330-3130-31f7411871b9
document_version_independent_id: a3e63554-0212-1aca-8ce2-cec442f7b0e2
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/administration/windows-commands/rdpsign.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: administration/windows-commands/rdpsign
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/administration/windows-commands/rdpsign.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e10a756b-c002-4cbb-8cf6-f0fab0633697
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a741da3-90b9-472d-8fd6-830aafecaac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 56522817-7d14-7024-dc61-0751ad6a4acc
---

# rdpsign | Microsoft Learn

Enables you to digitally sign a Remote Desktop Protocol (.rdp) file.

Note

To find out what's new in the latest version, see [What's New in Remote Desktop Services in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323%28v=ws.11%29).

## Syntax

```
rdpsign /sha1 <hash> [/q | /v |] [/l] <file_name.rdp>
```

### Parameters

| Parameter | Description |
| --- | --- |
| /sha1 `<hash>` | Specifies the thumbprint, which is the Secure Hash Algorithm 1 (SHA1) hash of the signing certificate that is included in the certificate store. Used in Windows Server 2012 R2 and older. |
| /sha256 `<hash>` | Specifies the thumbprint, which is the Secure Hash Algorithm 256 (SHA256) hash of the signing certificate that is included in the certificate store. Replaces /sha1 in Windows Server 2016 and newer. |
| /q | Quiet mode. No output when the command succeeds and minimal output if the command fails. |
| /v | verbose mode. Displays all warnings, messages, and status. |
| /l | Tests the signing and output results without actually replacing any of the input files. |
| `<file_name.rdp>` | The name of the .rdp file. You must specify the .rdp file (or files) to sign by using the full file name. Wildcard characters are not accepted. |
| /? | Displays help at the command prompt. |

#### Remarks

- The SHA1 or SHA256 certificate thumbprint should represent a trusted .rdp file publisher. To obtain the certificate thumbprint, open the **Certificates** snap-in, double-click the certificate that you want to use (either in the local computer's certificates store or in your personal certificates store), click the **details** tab, and then in the **Field** list, click **Thumbprint**.

    Note

    When you copy the thumbprint for use with the rdpsign.exe tool, you must remove any spaces.
- The signed output files overwrite the input files.
- If multiple files are specified, and if any of the .rdp files can't be read or written to, the tool continues to the next file.

### Examples

To sign an .rdp file named *file1.rdp*, navigate to the folder where you saved the .rdp file, and then type:

```
rdpsign /sha1 hash file1.rdp
```

Note

The *hash* value represents the SHA1 certificate thumbprint, without any spaces.

To test whether digital signing will succeed for an .rdp file without actually signing the file, type:

```
rdpsign /sha1 hash /l file1.rdp
```

To sign multiple .rdp files that are named, *file1.rdp*, *file2.rdp*, and *file3.rdp*, type (including the spaces between file names):

```
rdpsign /sha1 hash file1.rdp file2.rdp file3.rdp
```