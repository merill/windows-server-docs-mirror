---
layout: Conceptual
title: Command line process auditing | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/component-updates/command-line-process-auditing
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Command line process auditing'
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
ms.custom:
- inhenkel
- sfi-image-nochange
locale: en-us
document_id: 2d156913-647b-0cdb-3a44-aca23e1d08e2
document_version_independent_id: 7c7c9f9c-9531-6c78-2d5a-3c35006db15c
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/component-updates/Command-line-process-auditing.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/component-updates/command-line-process-auditing
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/component-updates/Command-line-process-auditing.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: c7677974-6c9d-d0c3-02ff-7a5b83327517
---

# Command line process auditing | Microsoft Learn

**Author**: Justin Turner, Senior Support Escalation Engineer with the Windows group

Note

This content is written by a Microsoft customer support engineer, and is intended for experienced administrators and systems architects who are looking for deeper technical explanations of features and solutions in Windows Server 2012 R2 than topics on TechNet usually provide. However, it has not undergone the same editing passes, so some of the language may seem less polished than what is typically found on TechNet.

## Overview

- The pre-existing process creation audit event ID 4688 will now include audit information for command line processes.
- It will also log SHA1/2 hash of the executable in the Applocker event log

    - Application and Services Logs\Microsoft\Windows\AppLocker
- You enable via GPO, but it's disabled by default

    - "Include command line in process creation events"

![Screenshot that highlights the Process Command Line.](media/command-line-process-auditing/gtr_adds_event4688.gif)

**Figure SEQ Figure \\* ARABIC 16 Event 4688**

Review the updated event ID 4688 in REF \_Ref366427278 \h Figure 16. Prior to this update none of the information for **Process Command Line** gets logged. Because of this additional logging we can now see that not only was the wscript.exe process started, but that it was also used to execute a VB script.

## Configuration

To see the effects of this update, you'll need to enable two policy settings.

### You must have Audit Process Creation auditing enabled to see event ID 4688.

To enable the Audit Process Creation policy, edit the following group policy:

**Policy location:** Computer Configuration &gt; Policies &gt; Windows Settings &gt; Security Settings &gt; Advanced Audit Configuration &gt; Detailed Tracking

**Policy Name:** Audit Process Creation

**Supported on:** Windows 7 and above

**Description/Help:**

This security policy setting determines whether the operating system generates audit events when a process is created (starts) and the name of the program or user that created it.

These audit events can help you understand how a computer is being used and to track user activity.

Event volume: Low to medium, depending on system usage

**Default:** Not configured

### In order to see the additions to event ID 4688, you must enable the new policy setting: Include command line in process creation events

**Table SEQ Table \\* ARABIC 19 Command line process policy setting**

| Policy Configuration | Details |
| --- | --- |
| **Path** | Administrative Templates\System\Audit Process Creation |
| **Setting** | **Include command line in process creation events** |
| **Default setting** | Not Configured (not enabled) |
| **Supported on:** | ? |
| **Description** | This policy setting determines what information is logged in security audit events when a new process has been created.<br>This setting only applies when the Audit Process Creation policy is enabled. If you enable this policy setting the command line information for every process will be logged in plain text in the security event log as part of the Audit Process Creation event 4688, "a new process has been created," on the workstations and servers on which this policy setting is applied.<br><br>If you disable or don't configure this policy setting, the process's command line information won't be included in Audit Process Creation events.<br><br>Default: Not configured<br><br>Note: When this policy setting is enabled, any user with access to read the security events will be able to read the command line arguments for any successfully created process. Command line arguments can contain sensitive or private information such as passwords or user data. |

![Screenshot that shows ](media/command-line-process-auditing/gtr_adds_includeclisetting.gif)

When you use Advanced Audit Policy Configuration settings, you need to confirm that these settings aren't overwritten by basic audit policy settings. Event 4719 is logged when the settings are overwritten.

![Screenshot that shows the Include command line in process creation events dialog box.](media/command-line-process-auditing/gtr_adds_event4719.gif)

The following procedure shows how to prevent conflicts by blocking the application of any basic audit policy settings.

### To ensure that Advanced Audit Policy Configuration settings aren't overwritten

![command-line auditing](media/command-line-process-auditing/gtr_adds_advauditpolicy.gif)

1. Open the Group Policy Management console
2. Right-click Default Domain Policy, and then select Edit.
3. Double-click Computer Configuration, double-click Policies, and then double-click Windows Settings.
4. Double-click Security Settings, double-click Local Policies, and then select Security Options.
5. Double-click Audit: Force audit policy subcategory settings (Windows Vista or later) to override audit policy category settings, and then select Define this policy setting.
6. Select Enabled, and then select OK.