---
layout: Conceptual
title: What is KDFv2 for AD FS? | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/what-is-kdfv2
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: Describes the new Key Derivation Function (KDF) called "KDFv2" for AD FS
ms.topic: how-to
ms.date: 2024-02-13T00:00:00.0000000Z
locale: en-us
document_id: 375cd459-751a-a839-50fb-ec5e1dc89853
document_version_independent_id: 375cd459-751a-a839-50fb-ec5e1dc89853
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/what-is-kdfv2.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/what-is-kdfv2
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/what-is-kdfv2.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 744ea3c3-3445-96a3-37e7-9440fe7b701e
---

# What is KDFv2 for AD FS? | Microsoft Learn

On July 13, 2021, updates were released for AD FS to address token replay attacks, as described in [CVE-2021-33779](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-33779). These updates introduce new settings to enable and control a new, Key Derivation Function (KDF) called "KDFv2". This new version of KDF is more secure than the previous version. This document describes new settings enabled by the security fix for [CVE-2021-33779](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-33779), and how to enable these settings in different deployment scenarios. For product-specific KB numbers and related downloads, please refer to links provided in the CVE article.

## KDFv2 Settings:

KDFv2 may be configured by an Administrator on an AD FS server to run in one of several modes, which are as follows:

- **None - (Default value)** This is used to track if the KDFv2 setting value was ever changed. This value may not be set by an Administrator.
- **Disabled** - This value may be set in order to revert the Key Derivation Function to its original behavior, in case there are any issues encountered when enabling KDFv2.
- **Enabled** - Enable KDFv2 support. The ADFS server will advertise that it supports the new capabilities. If an initial Primary Refresh Token (PRT) request is sent from a client using the original KDF version, ADFS will accept the request and use the original KDF. This allows for support of unpatched clients.
- **Enforced** - Enable KDFv2 support and disallow (reject) initial PRT requests using the original KDF. Once an Administrator is comfortable that all clients have been patched, they may switch to enforced mode.

KDFv2 modes may be changed by an Administrator on an AD FS server via the following PowerShell commands:

- Enable KDFv2:

```powershell
Set-AdfsProperties -KdfV2Support enable 
```

- Disable KDFv2:

```powershell
Set-AdfsProperties -KdfV2Support disable 
```

- Enforce KDFv2:

```powershell
Set-AdfsProperties -KdfV2Support enforce 
```

An Administrator may run `Get-AdfsProperties` to check the current KDFv2 setting. The `KdfV2Support` value returned will match the configured mode.

## Deployment Scenarios

Depending on the OS version that AD FS servers are running when patched to support KDFv2, KDFv2 may be enabled automatically. Also, the OS-version-dependent events may be logged to indicate the state of KDFv2 in the farm. The following are possible deployment scenarios and expected behaviors.

### Scenario 1: Windows Server 2019 or above is installed on all AD FS servers in a farm. One or more farm nodes are unpatched.

Expected behavior: If all nodes in farm aren't patched then the below error event will be logged indicating recommended remediation actions. This event will be logged every 24 hours until all nodes in the farm are patched. Once all nodes are patched, KDFv2 will be enabled automatically for all systems in the farm via the "Enable" mode.

```
 Source: AD FS 
 Level: Error 
 ID: 181 
 Message: AD FS could not enable the new KDFv2 feature automatically because of missing Windows Updates on one or more nodes of the farm. Please make sure that all the farm nodes are patched with the latest Windows Updates. AD FS checks regularly for the required updates to enable the new KDFv2 feature. An event 182 will be logged when a check is successful. For more information on this, please see https://go.microsoft.com/fwlink/?linkid=2153807. 
```

### Scenario 2: Windows Server 2016 is installed on one or more servers in a farm. All servers are running Windows 2016 or greater. One or more farm nodes are unpatched.

Expected behavior: If all nodes in farm aren't patched then the below error event will be logged indicating recommended remediation actions. This event will be logged every 24 hours until all nodes in the farm are patched. Once all nodes are patched, KDFv2 must be manually enabled on all servers in the farm.

```
 Source: AD FS 
 Level: Error 
 ID: 185 
 Message: KDFv2 feature is not enabled on AD FS farm. Please make sure that all the farm nodes are patched with latest Windows Updates and the KDFv2 feature is enabled to enhance the security of the farm. For more information on this, please see https://go.microsoft.com/fwlink/?linkid=2153807. 
```

### Scenario 3: Windows Server 2019 or above is installed on all ADFS servers in a farm. All servers in the farm have been patched.

Expected behavior: Once KDFv2 has been enabled automatically on the farm as described in Scenario 1 above, then the below event will be logged.

```
 Source: AD FS 
 Level: Information 
 ID: 182 
 Message: AD FS enabled the new KDFv2 feature successfully. For more information on this, please see https://go.microsoft.com/fwlink/?linkid=2153807. 
```

Note

Event 182 will not be logged if any servers in a farm are running Windows Server 2016.

### Scenario 4: Administrator has disabled KDFv2 on one or more servers in their environment.

Expected behavior: The below log message will be logged on each system in the farm where KDFv2 has been disabled, on ADFS service start.

```
 Source: AD FS 
 Level: Warning 
 ID: 183 
 Message: KDFv2 feature is disabled on AD FS farm. Please make sure that all the farm nodes are patched with latest Windows Updates and the KDFv2 feature is enabled to enhance the security of the farm. For more information on this, please see https://go.microsoft.com/fwlink/?linkid=2153807. 
```

## Next

- [AD FS Troubleshooting](../troubleshooting/ad-fs-tshoot-overview)