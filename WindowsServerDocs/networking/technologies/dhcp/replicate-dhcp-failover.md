---
layout: Conceptual
title: Replicate DHCP failover in Windows Server | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/networking/technologies/dhcp/replicate-dhcp-failover
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: networking
ms.update-cycle: 1095-days
description: Follow the steps to replicate DHCP failover, using either the DHCP Console, or Windows PowerShell.
ms.author: roharwoo
author: robinharwood
ms.date: 2025-04-25T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 58b80e9c-5a4d-bf38-965f-37ca628df602
document_version_independent_id: 58b80e9c-5a4d-bf38-965f-37ca628df602
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/networking/technologies/dhcp/replicate-dhcp-failover.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: networking/technologies/dhcp/replicate-dhcp-failover
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/networking/technologies/dhcp/replicate-dhcp-failover.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: a0cdc631-a2ef-ae02-d5c6-b534d8215631
---

# Replicate DHCP failover in Windows Server | Microsoft Learn

Replication is the process of copying settings from one or more failover-enabled DHCP scopes to on a DHCP server to the server’s failover partner.

Three types of replication are available:

- **Server replication**: This type of replication copies the configuration of all failover-enabled scopes on the local server to its failover partner servers.
- **Relationship replication**: This type of replication copies the configuration of all DHCP scopes that are part of a selected failover relationship to the failover partner server.
- **Scope replication**: This type of replication copies the configuration of a selected DHCP scope to the failover partner server.

Follow the steps for the type of replication you want to perform, using either the DHCP console, or Windows PowerShell.

## Prerequisites

- At least Windows Server 2012
- The DHCP server role is installed
- An existing failover relationships work exists
- Membership in the **Administrators** group, or equivalent, is the minimum required to complete these procedures.

Important

Replication can be initiated from either DHCP server in a failover relationship. Settings on the failover partner server are overwritten with the settings that are configured on the server where replication is initiated. Therefore, it's important to always ensure replication is initiated on the server that's configured with the settings you wish to use.

## Replicate failover settings at the server level

To replicate failover settings at the server level, follow these steps.

# [DHCP console](#tab/dhcp-console)
1. On a DHCP server, open Server Manager, select **Tools** and then select **DHCP**.
2. In the DHCP console, right-click **IPv4**, and then select **Replicate Failover Scopes**.
3. Select **OK** in the alert that appears.
4. In the **Failover Scope Configuration Replication** dialog box, verify that replication was successful, and then select **Close**.

# [PowerShell](#tab/powershell)
1. On a computer with the Windows PowerShell DHCP Server module installed, right-click **Windows PowerShell** and then select **Run as Administrator**.
2. Type the following command, and then press Enter. Replace the example values with values used in your environment.

    ```powershell
    Invoke-DhcpServerv4FailoverReplication –ComputerName dhcp1.contoso.com -Force
    ```
3. Verify that the scope IDs are listed in the command output for all failover enabled scopes on the DHCP server.

In this example, the primary DHCP server is named **dhcp1.contoso.com**. If the **ComputerName** parameter isn't specified, the command is run on the local server.

---

## Replicate failover settings at the relationship level

To replicate failover settings at the relationship level, follow these steps.

# [DHCP console](#tab/dhcp-console)
1. On a DHCP server, open Server Manager, select **Tools** and then select **DHCP**.
2. In the DHCP console, right-click any failover-enabled scope, and then select **Replicate Relationship**.
3. Select **OK** in the alert that appears.
4. In the **Failover Scope Configuration Replication** dialog box, verify that replication was successful, and then select **Close**.

# [PowerShell](#tab/powershell)
1. On a computer with the Windows PowerShell DHCP Server module installed, right-click **Windows PowerShell** and then select **Run as Administrator**.
2. Type the following command, and then press Enter. Replace the example values with values used in your environment.

    ```powershell
    Invoke-DhcpServerv4FailoverReplication –ComputerName dhcp1.contoso.com –Name dhcp1-dhcp2 -Force
    ```
3. Verify that the scope IDs are listed in the command output for all failover enabled scopes that are configured to use the specified failover relationship.

In this example, the primary DHCP server is named **dhcp1.contoso.com** and the failover relationship name is **dhcp1-dhcp2**. If the **ComputerName** parameter isn't specified, the command is run on the local server.

---

## Replicate failover settings at the scope level

To replicate failover settings at the scope level, follow these steps:

# [DHCP console](#tab/dhcp-console)
1. On a DHCP server, open Server Manager, select **Tools** and then select **DHCP**.
2. In the DHCP console, right-click any failover-enabled scope, and then select **Replicate Scope**.
3. In the **Failover Scope Configuration Replication** dialog box, verify that replication was successful, and then select **Close**.

# [PowerShell](#tab/powershell)
1. On a computer with the Windows PowerShell DHCP Server module installed, right-click **Windows PowerShell** and then select **Run as Administrator**.
2. Type the following command, and then press Enter. Replace the example values with values used in your environment.

    ```powershell
    Invoke-DhcpServerv4FailoverReplication –ComputerName dhcp1.contoso.com –ScopeID 10.0.10.0,10.0.20.0 -Force
    ```
3. Verify that the scope IDs are listed in the command output for all scopes that were specified on the command line.

In this example, the primary DHCP server is named **dhcp1.contoso.com**, and the DHCP scope IDs specified are **10.0.10.0** and **10.0.20.0**. If the **ComputerName** parameter isn't specified, the command is run on the local server.

---