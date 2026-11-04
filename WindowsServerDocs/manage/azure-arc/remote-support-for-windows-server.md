---
layout: Conceptual
title: How to configure remote support for Arc-enabled Windows servers (preview) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/manage/azure-arc/remote-support-for-windows-server
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: manage
ms.update-cycle: 1095-days
description: Learn how to configure, grant, and revoke remote support assistance for your Arc-enabled Windows server.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2025-03-04T00:00:00.0000000Z
locale: en-us
document_id: 418b1456-04b0-74d0-3e3c-1a03357e56ab
document_version_independent_id: 418b1456-04b0-74d0-3e3c-1a03357e56ab
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/manage/azure-arc/remote-support-for-windows-server.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../administration/toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: manage/azure-arc/remote-support-for-windows-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/manage/azure-arc/remote-support-for-windows-server.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/beac614b-f66d-40ed-a947-3996de709333
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/9da05372-4706-43ec-a899-f436adab380d
platformId: 4da83504-2648-2d39-7050-f1d3a1bfe007
---

# How to configure remote support for Arc-enabled Windows servers (preview) | Microsoft Learn

By enabling Remote Support (preview), you allow a Microsoft Support professional to resolve your issue faster by accessing your device remotely for troubleshooting. You have complete control over the level of access that Microsoft support professionals have, the duration of access, and your consent is required to access your device. Microsoft support can only access your device after you submitted a support request. To learn how to create a request, see [Create an Azure support request](/en-us/azure/azure-portal/supportability/how-to-create-azure-support-request).

Once remote support is activated, Microsoft Support gains temporary access to your device. Access is made through a secure, audited, and compliant channel that uses HTTPS over port 443 with TLS 1.2 encrypted traffic. The actions Microsoft support professionals can perform are limited to what you allow, using [Just Enough Administration](/en-us/powershell/scripting/security/remoting/jea/overview) (JEA). This process involves authenticated access between you and Microsoft support for diagnostics, troubleshooting, and remediation actions.

To streamline setup and improve support issue resolution, the remote support Arc extension can preinstall the remote support agent on all cluster nodes and configure scheduled tasks for JEA. The JEA workflow is as follows:

![A screenshot of the Just Enough Administrator remote support workflow.](../media/azure-arc/azure-arc-remote-support-just-enough-administration.png)

## Prerequisites

- Your device must be running an Arc-enabled on-premises Windows Server 2016 or later operating system with a minimum of 4 GB of memory.
- If you’re new to Azure Arc, your device must be onboarded. To learn more, see [Quickstart: Connect hybrid machines with Azure Arc-enabled servers](/en-us/azure/azure-arc/servers/learn/quick-enable-hybrid-vm).
- You must use [Windows Server Pay-as-you-go](../../get-started/windows-server-pay-as-you-go) or [Software Assurance](/en-us/azure/azure-arc/servers/windows-server-management-overview) license types.

### Configure remote support

To configure remote support, perform the following steps:

1. Navigate to the [Azure portal](https://portal.azure.com/), then select your Windows server Arc-enabled device. This virtual machine (VM) should be the Hyper-V host.
2. In the left pane, navigate to **Windows management**, then select **Remote Support (preview)**.
3. On the **Remote Support (preview)** screen, select **Setup**.

    [![A screenshot of the Azure portal with the remote support tool selected under the Windows management node.](../media/azure-arc/azure-arc-remote-support.png)](../media/azure-arc/azure-arc-remote-support.png#lightbox)
4. Once the setup completes, the **Remote Support Sessions** screen is displayed.

    [![A screenshot of the remote support tool's remote support sessions page.](../media/azure-arc/azure-arc-remote-support-sessions.png)](../media/azure-arc/azure-arc-remote-support-sessions.png#lightnox)
5. To grant access for a remote support session, select **+ Grant access** at the top of the page.
6. Specify the **Access level** and **Access period** for your session.

    [![A screenshot of the remote support tool's grant remote support access level and access period screen.](../media/azure-arc/azure-arc-remote-support-grant-remote-support-access.png)](../media/azure-arc/azure-arc-remote-support-grant-remote-support-access.png#lightbox)
7. Read the terms and conditions before selecting the **I agree to these terms and conditions** checkbox, then select **Grant access**.

## Configure remote support access

Users can also edit the level of access and duration at any time. To make these changes post-configuration, follow these steps:

1. In the left pane, navigate to **Windows management**, then select **Remote Support (preview)**.
2. Select **Configure access** at the top of the page.

    [![A screenshot of the remote support tool's configure remote support access screen.](../media/azure-arc/azure-arc-remote-support-configure-remote-support-access.png)](../media/azure-arc/azure-arc-remote-support-configure-remote-support-access.png#lightbox)
3. Once modifications are made, select **Save changes**.

## Revoke remote support access

If remote support access is no longer needed, users can elect to revoke access at any time. To revoke access, follow these steps:

1. In the left pane, navigate to **Windows management**, then select **Remote Support (preview)**.
2. Select **Revoke access** at the top of the page, then select **Revoke access** on the **Revoke remote support access?** screen.

    [![A screenshot of the remote support tool's revoke remote support access screen.](../media/azure-arc/azure-arc-remote-support-revoke-remote-support-access.png)](../media/azure-arc/azure-arc-remote-support-revoke-remote-support-access.png#lightbox)

## Remote support terms and conditions

The following terms and conditions outline how data is handled during remote support sessions. Read them carefully before granting access.

```
By approving this request, the Microsoft support organization or the Azure engineering team
supporting this feature ("Microsoft Support Engineer") will be given direct access to your device
for troubleshooting purposes and/or resolving the technical issue described in the Microsoft
support case.

During a remote support session, a Microsoft Support Engineer may need to collect logs. By enabling
remote support, you have agreed to a diagnostics log collection by a Microsoft Support Engineer to
address a support case. You also acknowledge and consent to the upload and retention of those logs
in an Azure storage account managed and controlled by Microsoft. These logs may be accessed by
Microsoft in the context of a support case and to improve the health of Windows Server.

The data will be used only to troubleshoot failures that are subject to a support ticket, and will
not be used for marketing, advertising, or any other commercial purposes without your consent. The
data may be retained for up to ninety (90) days and will be handled following our standard privacy
practices.

Any data previously collected with your consent will not be affected by the revocation of your
permission.
```

For more information about how Microsoft processes personal data, including what data is processed and for what purposes, see the [Microsoft Privacy Statement](https://www.microsoft.com/privacy/privacystatement).