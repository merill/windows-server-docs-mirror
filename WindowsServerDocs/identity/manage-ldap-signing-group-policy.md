---
layout: Conceptual
title: Configure LDAP Signing by Using Group Policy | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/manage-ldap-signing-group-policy
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: security
ms.update-cycle: 1095-days
description: Learn how to configure LDAP signing requirements on Windows Server domain controllers by using Group Policy to enhance security and prevent unauthorized access.
author: robinharwood
ms.author: roharwoo
ms.topic: how-to
ms.date: 2026-10-02T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: a81fb9c2-36e6-7f08-96bb-7ac8bfc895d7
document_version_independent_id: a81fb9c2-36e6-7f08-96bb-7ac8bfc895d7
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/manage-ldap-signing-group-policy.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/manage-ldap-signing-group-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/manage-ldap-signing-group-policy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: b627abb9-89b0-cac3-2ee5-fa6301ff774d
---

# Configure LDAP Signing by Using Group Policy | Microsoft Learn

Configuring your domain controllers to require LDAP signing improves the security of your Active Directory environment by rejecting unsigned LDAP binds. This article shows you how to configure LDAP server signing requirements by using Group Policy and how to identify clients that you need to update before enforcing this security requirement.

Unsigned network traffic is susceptible to replay attacks where an intruder intercepts authentication attempts and reuses credentials to impersonate legitimate users. Also, unsigned traffic is vulnerable to man-in-the-middle attacks where attackers can modify LDAP requests in transit. Requiring LDAP signing verifies integrity and prevents these attack vectors.

Note

Windows Server 2025 or later requires LDAP signing by default for new Active Directory deployments. During an upgrade, Windows Server preserves existing signing policies to prevent disruption; if no LDAP server signing policy exists, Windows Server 2025 requires signing by default. For more information about default security behavior and version differences, see [LDAP signing for Active Directory Domain Services](ad-ds/ldap-signing).

## Prerequisites

- An account with permission to edit the applicable Group Policy Objects and modify registry settings on the target server. Use just-in-time elevation if your organization grants these permissions through Domain Admins.
- Access to a domain controller or a computer with Active Directory Domain Services (AD DS) Remote Server Administration Tools (RSAT) installed
- Group Policy Management Console installed

## Identify clients that use unsigned LDAP binds

Before you require LDAP signing, identify which clients in your environment are currently making unsigned LDAP binds. Active Directory logs summary events to help you discover these clients without disrupting service.

On domain controllers that permit unsigned binds, `Event ID 2887` logs a 24-hour summary when unsigned binds occur. On domain controllers that require signing, `Event ID 2888` summarizes rejected unsigned binds.

To get detailed information about specific clients making unsigned binds:

1. Open **Event Viewer** on the domain controller.
2. Go to **Applications and Services Logs** &gt; **Directory Service**.
3. In the event list, locate `Event ID 2887` for summary information about unsigned binds.

To enable detailed logging that identifies specific client IP addresses:

1. Open **Registry Editor** on the domain controller.
2. Go to `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\NTDS\Diagnostics`.
3. Set the **16 LDAP Interface Events** value to **2** (Basic logging).
4. Monitor for `Event ID 2889`, which logs each unsigned bind attempt, including the client IP address and identity.
5. After the investigation, set **16 LDAP Interface Events** back to **0** to disable detailed logging.

After you identify all clients that need updates, configure them to request LDAP signing before you enforce signing requirements on your domain controllers.

## Configure LDAP signing requirements

Configure LDAP signing on both domain controllers and client computers to ensure secure LDAP communications across your environment.

### Client computers

Configure client computers to request LDAP signing when they communicate with domain controllers. Set up this configuration by using local policy on individual computers or through a domain Group Policy Object for enterprise-wide deployment. To prevent service disruptions, configure clients before you enforce signing on domain controllers. Verify client compliance by repeating the steps in the previous Identify clients that use unsigned LDAP binds section to check for unsigned bind attempts.

Note

All currently supported versions of Windows client use LDAP signing by default as LDAP clients. Manually configure this setting to set a specific signing level or ensure that legacy systems comply with your security requirements.

To configure LDAP signing on client computers by using Group Policy:

1. Open **Microsoft Management Console** by selecting **Start** &gt; **Run**, typing **mmc.exe**, and selecting **OK**.
2. Select **File** &gt; **Add/Remove Snap-in**.
3. Select **Group Policy Object Editor**, and then select **Add**.
4. Select **Browse**, and then select **Default Domain Policy** or your preferred Group Policy Object.
5. Select **OK**, and then select **Finish**.
6. Select **Close**, and then select **OK**.
7. Navigate to **Default Domain Policy** &gt; **Computer Configuration** &gt; **Policies** &gt; **Windows Settings** &gt; **Security Settings** &gt; **Local Policies** &gt; **Security Options**.
8. Open the context menu for **Network security: LDAP client signing requirements**, and then select **Properties**.
9. Select one of the following options:
    - **None**: The client doesn't request signing (not recommended)
    - **Negotiate signing**: The client requests signing if the server supports it (recommended for gradual deployment)
    - **Require signing**: The client requires signing for all LDAP traffic (recommended for maximum security)
10. Select **OK**.
11. Select **Yes** in the confirmation dialog.

After you configure this setting, client computers request LDAP signing based on the selected policy. The policy takes effect at the next Group Policy refresh. To apply it immediately, run [gpupdate](/en-us/windows-server/administration/windows-commands/gpupdate) with the `/force` option.

### Domain controllers

Domain controllers check the server LDAP signing requirement to decide whether they accept unsigned LDAP binds. You usually set this requirement through the Default Domain Controllers Policy. Select the operating system version that matches your domain controllers to see the appropriate configuration steps.

# [Windows Server 2025](#tab/windows-server-2025)
New Active Directory deployments on Windows Server 2025 or later require LDAP signing by default. The **Domain controller: LDAP server signing requirements enforcement** Group Policy setting configures this default, which is separate from the **Domain controller: LDAP server signing requirements** policy.

The **Domain controller: LDAP server signing requirements enforcement** policy takes precedence over the **Domain controller: LDAP server signing requirements** policy. When you configure both policies, the enforcement policy setting applies. This configuration ensures that new deployments automatically have stronger security defaults while allowing administrators to explicitly modify the behavior if needed.

To configure LDAP signing enforcement on Windows Server 2025:

1. Open **Microsoft Management Console** by selecting **Start** &gt; **Run**, typing **mmc.exe**, and selecting **OK**.
2. Select **File** &gt; **Add/Remove Snap-in**.
3. Select **Group Policy Management Editor**, and then select **Add**.
4. Select **Browse** next to Group Policy Object.
5. In the **Browse for a Group Policy Object** dialog, select **Default Domain Controllers Policy** under your domain, and then select **OK**.
6. Select **Finish**, and then select **OK**.
7. Go to **Default Domain Controllers Policy** &gt; **Computer Configuration** &gt; **Policies** &gt; **Windows Settings** &gt; **Security Settings** &gt; **Local Policies** &gt; **Security Options**.
8. Open the context menu for **Domain controller: LDAP server signing requirements enforcement**, and then select **Properties**.
9. Turn on **Define this policy setting**, and choose one of the following options:
    - **Default:** **Not Configured**, which has the same effect as **Enabled** (default for new deployments).
    - **Enabled:** The enforcement policy requires LDAP signing regardless of the **Domain controller: LDAP server signing requirements** policy.
    - **Disabled:** The **Domain controller: LDAP server signing requirements** policy determines the LDAP signing requirement.
10. Select **OK**.
11. Select **Yes** in the confirmation dialog.

Important

If you're upgrading from an earlier version of Windows Server to Windows Server 2025, Windows Server preserves existing LDAP signing policies to prevent disruption. Review your current policy settings and update them as appropriate for your security requirements.

# [Windows Server 2022 or earlier](#tab/windows-server-2022)
To set up LDAP signing on domain controllers:

1. Open **Microsoft Management Console** by selecting **Start** &gt; **Run**, typing **mmc.exe**, and selecting **OK**.
2. Select **File** &gt; **Add/Remove Snap-in**.
3. Select **Group Policy Management Editor**, and then select **Add**.
4. Select **Browse** next to Group Policy Object.
5. In the **Browse for a Group Policy Object** dialog, select **Default Domain Controllers Policy** under your domain, and then select **OK**.
6. Select **Finish**, and then select **OK**.
7. Go to **Default Domain Controllers Policy** &gt; **Computer Configuration** &gt; **Policies** &gt; **Windows Settings** &gt; **Security Settings** &gt; **Local Policies** &gt; **Security Options**.
8. Open the context menu for **Domain controller: LDAP server signing requirements**, and then select **Properties**.
9. Turn on **Define this policy setting**, and choose one of the following options:
    - **None**: A domain controller accepts both signed and unsigned LDAP binds (not recommended)
    - **Require signing**: A domain controller rejects unsigned LDAP binds (recommended)
10. Select **OK**.
11. Select **Yes** in the confirmation dialog.

---

Group Policy applies this setting during the next policy refresh cycle. To apply it immediately, run `gpupdate /force` on your domain controllers. When set to **Require signing**, domain controllers reject LDAP simple binds over non-SSL/TLS connections and SASL binds that don't request signing.

## Configure LDAP signing for Active Directory Lightweight Directory Services

For Active Directory Lightweight Directory Services (AD LDS) instances, configure LDAP signing through a registry setting instead of Group Policy. Use this method to set signing requirements independently for each AD LDS instance.

To configure LDAP signing for an AD LDS instance:

1. Open **Registry Editor** on the server hosting the AD LDS instance.
2. Go to `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\<InstanceName>\Parameters`.
3. Create a new **DWORD (32-bit) Value** named `LDAPServerIntegrity`.
4. Set the value to **2** to enable signing requirements.
5. Close **Registry Editor**.

The setting takes effect immediately without a restart. The `LDAPServerIntegrity` value accepts the following values:

- **0**: Disables signing (default).
- **2**: Requires signing.

## Verify LDAP signing configuration

After you configure LDAP signing requirements, verify that the configuration works as expected. Test the configuration by attempting an unsigned LDAP bind. If the LDAP signing policy requires signing, the domain controller rejects the bind.

Verify LDAP signing enforcement:

Warning

This test sends simple-bind credentials without TLS. Run it only in an isolated lab, use a nonprivileged disposable test account, and never enter production credentials.

1. On a computer with AD DS Admin Tools, open **LDP.exe** by selecting **Start** &gt; **Run**, typing **ldp.exe**, and selecting **OK**.
2. Select **Connection** &gt; **Connect**.
3. Type your domain controller name in **Server** and **389** in **Port**, and then select **OK**.
4. After you connect, select **Connection** &gt; **Bind**.
5. Under **Bind type**, select **Simple bind**.
6. Enter credentials and select **OK**.

If the domain controller enforces the LDAP signing requirement, you receive an error message: "Ldap\_simple\_bind\_s() failed: Strong Authentication Required." This error confirms that the domain controller rejects unsigned LDAP binds.

For production validation, monitor Event Viewer for Event ID `2888`. This event logs a summary every 24 hours showing how many unsigned bind attempts the domain controller rejected.