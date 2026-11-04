---
layout: Conceptual
title: Deploy Security Auditing with Central Audit Policies (Demonstration Steps) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/solution-guides/deploy-security-auditing-with-central-audit-policies--demonstration-steps-
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: 'Learn more about: Deploy Security Auditing with Central Audit Policies (Demonstration Steps)'
author: robinharwood
ms.author: roharwoo
ms.date: 2024-02-13T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: e631fb23-34d6-bd20-0173-39e0b66c57a9
document_version_independent_id: 95cd99bd-75d5-adc2-7776-7f6bc093cd1d
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/solution-guides/Deploy-Security-Auditing-with-Central-Audit-Policies--Demonstration-Steps-.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/solution-guides/deploy-security-auditing-with-central-audit-policies--demonstration-steps-
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/solution-guides/Deploy-Security-Auditing-with-Central-Audit-Policies--Demonstration-Steps-.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: df0c7da5-1112-4480-ce80-8deb11286bdc
---

# Deploy Security Auditing with Central Audit Policies (Demonstration Steps) | Microsoft Learn

In this scenario, you will audit access to files in the Finance Documents folder by using the Finance Policy that you created in [Deploy a Central Access Policy (Demonstration Steps)](deploy-a-central-access-policy--demonstration-steps-). If a user who is not authorized to access the folder attempts to access it, the activity is captured in the event viewer. The following steps are required to test this scenario.

| Task | Description |
| --- | --- |
| [Configure Global Object Access](deploy-security-auditing-with-central-audit-policies--demonstration-steps-#BKMK_1) | In this step, you configure the global object access policy on the domain controller. |
| [Update Group Policy Settings](deploy-security-auditing-with-central-audit-policies--demonstration-steps-#BKMK_2) | Sign in to the file server and apply the Group Policy update. |
| [Verify that the global object access policy has been applied](deploy-security-auditing-with-central-audit-policies--demonstration-steps-#BKMK_3) | View the relevant events in the event viewer. The events should include metadata for the country and document type. |

## Configure global object access policy

In this step, you configure the global object access policy in the domain controller.

#### To configure a global object access policy

1. Sign in to the domain controller DC1 as contoso\administrator with the password **pass@word1**.
2. In Server Manager, point to **Tools**, and then click **Group Policy Management**.
3. In the console tree, double-click **Domains**, double-click **contoso.com**, click **Contoso**, and then double-click **File Servers**.
4. Right-click **FlexibleAccessGPO**, and click **Edit**.
5. Double-click **Computer Configuration**, double-click **Policies**, and then double-click **Windows Settings**.
6. Double-click **Security Settings**, double-click **Advanced Audit Policy Configuration**, and then double-click **Audit Policies**.
7. Double-click **Object Access**, and then double-click **Audit File System**.
8. Select the **Configure the following events** check box, select the **Success** and **Failure** check boxes, and then click **OK**.
9. In the navigation pane, double-click **Global Object Access Auditing**, and then double-click **File system**.
10. Select the **Define this policy setting** check box, and click **Configure**.
11. In the **Advanced Security Settings for Global File SACL** box, click **Add**, then click **Select a principal**, type **Everyone**, and then click **OK**.
12. In the **Auditing Entry for Global File SACL** box, select **Full control** in the **Permissions** box.
13. In the **Add a condition:** section, click **Add a condition** and in the drop-down lists select [**Resource**] [**Department**] [**Any of**] [**Value**] [**Finance**].
14. Click **OK** three times to complete the configuration of the global object access audit policy setting.
15. In the navigation pane, click **Object Access**, and in the results pane, double-click **Audit Handle Manipulation**. Click **Configure the following audit events**, **Success**, and **Failure**, click **OK**, and then close the flexible access GPO.

## Update Group Policy settings

In this step, you update the Group Policy settings after you have created the audit policy.

#### To update Group Policy settings

1. Sign in to the file server, FILE1 as contoso\Administrator, with the password **pass@word1**.
2. Press the Windows key+R, then type **cmd** to open a Command Prompt window.

    Note

    If the **User Account Control** dialog box appears, confirm that the action it displays is what you want, and then click **Yes**.
3. Type **gpupdate /force** and then press ENTER.

## Verify that the global object access policy has been applied

After the Group Policy settings have been applied, you can verify that the audit policy settings were applied correctly.

#### To verify that the global object access policy has been applied

1. Sign in to client computer, CLIENT1 as Contoso\MReid. Browse to the folder HYPERLINK "file:///\\\\ID\_AD\_FILE1\\Finance" \\ FILE1\Finance Documents, and modify Word Document 2.
2. Sign in to the file server, FILE1 as contoso\administrator. Open Event Viewer, browse to **Windows Logs**, select **Security**, and confirm that your activities resulted in audit events **4656** and **4663** (even though you did not set explicit auditing SACLs on the files or folders that you created, modified, and deleted).

Important

A new logon event is generated on the computer where the resource is located, on behalf of the user for whom effective access is being checked. When analyzing security audit logs for user sign-in activity, to differentiate between logon events that are generated because of effective access and those generated because of an interactive network user sign in, the Impersonation Level information is included. When the logon event is generated because of effective access, the Impersonation Level will be Identity. A network interactive user sign in typically generates a logon event with the Impersonation Level = Impersonation or Delegation.

## See also

- [Scenario: File Access Auditing](scenario--file-access-auditing)
- [Plan for File Access Auditing](plan-for-file-access-auditing)
- [Dynamic Access Control: Scenario Overview](dynamic-access-control--scenario-overview)