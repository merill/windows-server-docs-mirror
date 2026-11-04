---
layout: Conceptual
title: AD FS Troubleshooting - Microsoft Entra Connect Health Data | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/troubleshooting/ad-fs-tshoot-connect-health
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: Learn how to troubleshoot data freshness from the Microsoft Entra Connect Health agent for Active Directory Federation Services.
ms.date: 2024-10-14T00:00:00.0000000Z
ms.topic: troubleshooting-general
locale: en-us
document_id: e4d577f3-5ae3-27d0-abc8-44c3f8d286d6
document_version_independent_id: e4d577f3-5ae3-27d0-abc8-44c3f8d286d6
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-connect-health.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/troubleshooting/ad-fs-tshoot-connect-health
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/troubleshooting/ad-fs-tshoot-connect-health.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 789f4b35-a2cb-b129-73b7-3ed9ec9a309a
---

# AD FS Troubleshooting - Microsoft Entra Connect Health Data | Microsoft Learn

This article describes troubleshooting steps for the Microsoft Entra Connect Health for Active Directory Federation Services (AD FS) data freshness alert: "Health service data is not up to date."

## Check if your AD FS security audits are enabled

You can configure AD FS to do service auditing of user sign-ins to reveal a level of detail. For the Usage Analytics feature to gather and analyze data, the Microsoft Entra Connect Health agent needs the information in the AD FS audit logs. These logs aren't enabled by default. On your AD FS servers, use the following procedures to enable auditing and to locate the audit logs. To check the status of AD FS security audits:

1. Select **Start**, point to **Administrative Tools**, and then select **Local Security Policy**.
2. Double-click **Local Policies**, and then select **Audit Policy**.
3. On the details pane, double-click **Audit object access**.
4. Check the status of the audit object policy on the **Audit object access properties** page.

## Enable AD FS audit events

Depending on your machine settings, we have steps here to enable AD FS audit events:

`Run Restart-Service AdHealth*`

## If you use AD FS on Windows Server 2016, make sure Verbose AuditLevel is set

Use these commands:

`Set-AD FSProperties -AuditLevel Verbose`

`Run Restart-Service AdHealth*`

## Check for multiple service member entries in config.json

Go to *C:\Program Files\Azure Ad Connect Health ADFS Agent\Insights\config.json*. Open the file in a JSON editor or look for multiple instances of the string `ServiceType: AdFederationService`.

## Look for runtime errors in the agent debug trace

1. In the event viewer, enable analytic and debug logs.
2. Find `Applications and Service logs\ADHealth-AD FS\Debug`.
3. Right-click, increase the size to **100032**, and enable the log. Disable and then reenable to clear.
4. Restart the insight service by running `Restart-Service AdHealth*`.
5. Wait for five minutes, and then refresh the log.
6. Select Ctrl+F to find `AgentType = Insights`. Look for logs with error/authorization information.
7. If errors look to be related to OAuth/token issuance, reregister to refresh the agent key for the insights service. Then run `Register-AzureADConnectHealthAD FSAgent`.
8. Otherwise, you can run the insights service in console mode to catch errors. Go to *C:\Program Files\Azure Ad Connect Health ADFS Agent\Insights* and run `Microsoft.Identity.Health.ADFS.InsightsService.exe /console`.
9. Look at the debug log and find exception items.