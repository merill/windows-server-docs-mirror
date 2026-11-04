---
layout: Conceptual
title: Configure E-Mail Notifications | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/fsrm/configure-email-notifications
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: This article describes how to configure e-mail notifications
ms.date: 2017-07-07T00:00:00.0000000Z
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
locale: en-us
document_id: c751647e-a911-c0ce-0942-c1b59565bc16
document_version_independent_id: abab33f6-a5d2-4534-a2d8-9902d803711d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/fsrm/configure-email-notifications.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/fsrm/configure-email-notifications
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/fsrm/configure-email-notifications.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/4e834929-0ce1-4c1d-9c81-fcb14721edfb
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/75670257-a3f0-4627-9981-8046f99219e6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f9a72aca-742e-665a-b28c-03c8958b9c9d
---

# Configure E-Mail Notifications | Microsoft Learn

When you create quotas and file screens, you have the option of sending e-mail notifications to users when their quota limit is approaching or after they have attempted to save files that have been blocked. When you generate storage reports, you have the option of sending the reports to specific recipients by e-mail. If you want to routinely notify certain administrators about quota and file screening events, or send storage reports, you can configure one or more default recipients.

To send these notifications and storage reports, you must specify the SMTP server to be used for forwarding the e-mail messages.

## To configure e-mail options

1. In the console tree, right-click **File Server Resource Manager**, and then click **Configure Options**. The **File Server Resource Manager Options** dialog box opens.
2. On the **E-mail Notifications** tab, under **SMTP server name or IP address**, type the host name or the IP address of the SMTP server that will forward e-mail notifications and storage reports.
3. If you want to routinely notify certain administrators about quota or file screening events or e-mail storage reports, under **Default administrator recipients**, type each e-mail address.

    Use the format *account@domain*. Use semicolons to separate multiple accounts.
4. To specify a different "From" address for e-mail notifications and storage reports sent from File Server Resource Manager, under the **Default "From" e-mail address**, type the e-mail address that you want to appear in your message.
5. To test your settings, click **Send Test E-mail**.
6. Click **OK**.

## To configure e-mail options using PowerShell

You can use the `Set-FsrmSetting` cmdlet to set the e-mail configuration and the `Send-FsrmTestEmail` cmdlet to send a test email as shown in the following example:

```powershell
#   Setting FSRM email options
$MHT = @{
  SmtpServer        = 'SMTP.Contoso.Com'  
  FromEmailAddress  = 'FSRM@RContoso.Com'
  AdminEmailAddress = 'FSAdmin@Contoso.com'
}
Set-FsrmSetting @MHT

#   Sending a test email to check the setup
$MHT = @{
  ToEmailAddress = 'JerryG@Contoso.Com'
  Confirm        = $false
}
Send-FsrmTestEmail @MHT
```

## Additional References

- [Setting File Server Resource Manager Options](setting-file-server-resource-manager-options)