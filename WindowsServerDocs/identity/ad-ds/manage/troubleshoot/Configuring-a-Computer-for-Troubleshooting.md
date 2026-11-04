---
layout: Conceptual
title: Configuring a Computer for Troubleshooting | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/troubleshoot/configuring-a-computer-for-troubleshooting
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: 'Learn more about: Configuring a Computer for Troubleshooting'
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: troubleshooting-general
locale: en-us
document_id: 9b339e74-8008-9d18-bd83-1921054172f5
document_version_independent_id: 3e3e4e2f-c0d0-df88-83c0-ea88d4a67cd1
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/manage/troubleshoot/Configuring-a-Computer-for-Troubleshooting.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/manage/troubleshoot/configuring-a-computer-for-troubleshooting
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/manage/troubleshoot/Configuring-a-Computer-for-Troubleshooting.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 98d9c322-fda5-a478-b44d-12320a1a9bd4
---

# Configuring a Computer for Troubleshooting | Microsoft Learn

Before you use advanced troubleshooting techniques to identify and fix Active Directory problems, configure your computers for troubleshooting. You should also have a basic understanding of troubleshooting concepts, procedures, and tools.

For information about monitoring tools for Windows Server, see the Step-by-Step Guide for [Performance and Reliability Monitoring in Windows Server](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771692%28v=ws.10%29)

## Configuration tasks for troubleshooting

To configure your computer for troubleshooting Active Directory Domain Services (AD DS), perform the following tasks:

### Install Remote Server Administration Tools for AD DS

When you install AD DS to create a domain controller, the administrative tools that you use to manage AD DS are installed automatically. If you want to manage domain controllers remotely from a computer that is not a domain controller, you can install the Remote Server Administration Tools (RSAT) on a member server or workstation that is running a supported version of Windows. RSAT replaces Windows Support Tools from Windows Server 2003.

For information about installing RSAT, see the article [Remote Server Administration Tools](../../../../remote/remote-server-administration-tools).

### Configure Reliability and Performance Monitor

Windows Server includes the Windows Reliability and Performance Monitor, which is a Microsoft Management Console (MMC) snap-in that combines the functionality of previous stand-alone tools, including Performance Logs and Alerts and System Monitor. This snap-in provides a graphical user interface (GUI) for customizing Data Collector Sets and Event Trace Sessions.

Reliability and Performance Monitor also includes Reliability Monitor, an MMC snap-in that tracks changes to the system and compares them to changes in system stability, providing a graphical view of their relationship.

### Set logging levels

If the information that you receive in the Directory Service log in Event Viewer is not sufficient for troubleshooting, raise the logging levels by using the appropriate registry entry in **HKEY\_LOCAL\_MACHINE\SYSTEM\CurrentControlSet\Services\NTDS\Diagnostics**.

By default, the logging levels for all entries are set to **0**, which provides the minimum amount of information. The highest logging level is **5**. Increasing the level for an entry causes additional events to be logged in the Directory Service event log.

Use the following procedure to change the logging level for a diagnostic entry. Membership in **Domain Admins**, or equivalent, is the minimum required to complete this procedure.

Warning

We recommend that you do not directly edit the registry unless there is no other alternative. Modifications to the registry are not validated by the registry editor or by Windows before they are applied, and as a result, incorrect values can be stored. This can result in unrecoverable errors in the system. When possible, use Group Policy or other Windows tools, such as MMC snap-ins, to accomplish tasks, rather than editing the registry directly. If you must edit the registry, use extreme caution.

To change the logging level for a diagnostic entry

1. Click **Start** &gt; **Run** &gt; type **regedit** &gt; click **OK**.
2. Navigate to the entry for which you want to set logging in.
    - EXAMPLE: HKEY\_LOCAL\_MACHINESYSTEMCurrentControlSetServicesNTDSDiagnostics
3. Double-click the entry, and in **Base**, click **Decimal**.
4. In **Value**, type an integer from **0** through **5**, and then click **OK**.