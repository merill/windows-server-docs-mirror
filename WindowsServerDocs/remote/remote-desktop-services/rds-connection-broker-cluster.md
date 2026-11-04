---
layout: Conceptual
title: Configure RD Connection Broker for High Availability | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/rds-connection-broker-cluster
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote-desktop-services
ms.update-cycle: 1095-days
description: Learn to configure the Remote Desktop Connection Broker for high availability in Remote Desktop Services.
ms.topic: how-to
ai-usage: ai-assisted
ms.author: roharwoo
author: robinharwood
ms.date: 2025-07-02T00:00:00.0000000Z
ms.custom: sfi-ropc-nochange
locale: en-us
document_id: 1a82d598-92fc-591e-4f41-ba172fe9d305
document_version_independent_id: 1a82d598-92fc-591e-4f41-ba172fe9d305
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-desktop-services/rds-connection-broker-cluster.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-desktop-services/rds-connection-broker-cluster
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-desktop-services/rds-connection-broker-cluster.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ddab3cd8-636f-4a91-896e-1c23f399a6bd
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f409bb5d-e203-40c5-9d95-0ee717231beb
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: d56d48fa-1dfa-7103-e924-588e9306a409
---

# Configure RD Connection Broker for High Availability | Microsoft Learn

To ensure the reliability and scalability of your Remote Desktop Services infrastructure, you can configure the Remote Desktop Connection Broker for high availability. This article shows you how to set up a highly available Connection Broker cluster, including prerequisites, database configuration, load balancing, and final deployment steps. By following these instructions, you can minimize downtime and optimize performance for your remote desktop environment.

## Prerequisites

Before you begin, you need to meet the following prerequisites:

- Set up a server to act as a second RD Connection Broker. This server can be either a physical server or a VM.
- Set up a database for the Connection Broker. You can use [Azure SQL Database](/en-us/azure/azure-sql/database/single-database-create-quickstart#create-a-new-aure-sql-database) instance or SQL Server in your local environment. We give an example using Azure SQL, but the steps still apply to SQL Server. You need to find the connection string for the database and make sure you have the correct ODBC driver.

## Configure the database for the Connection Broker

1. Find the connection string for the database you created - you need it both to identify the version of ODBC driver you need and later, when you're configuring the Connection Broker itself (step 3), so save the string somewhere you can reference it easily. Here's how you find the connection string for Azure SQL:

    1. In the Azure portal, select **Browse &gt; Resource groups** and select the resource group for the deployment.
    2. Select the SQL database you created (for example, CB-DB1).
    3. Select **Settings** &gt; **Properties** &gt; **Show database connection strings**.
    4. Copy the connection string for **ODBC (includes Node.js)**, which should look like this. Replace the `<values>` with your values. You use this entire string, with your included password, when connecting to the database.

        ```connectionstring
        Driver={ODBC Driver 13 for SQL Server};Server=tcp:<YourHost>,<HostPort>;Database=<DatabaseName>;Uid=<UserID>;Pwd=<Password>;Encrypt=yes;TrustServerCertificate=no;Connection Timeout=30;
        ```
2. Install the ODBC driver on the new Connection Broker:

    1. If you're using a VM for the Connection Broker, create a public IP address for the first RD Connection Broker. (You only have to do this step if the RDMS virtual machine doesn't already have a public IP address to allow RDP connections.)

        1. In the Azure portal, select **Browse &gt; Resource groups**, select the resource group for the deployment, and then select the first RD Connection Broker virtual machine (for example, Contoso-Cb1).
        2. Select **Settings &gt; Network interfaces**, and then select the corresponding network interface.
        3. Select **Settings &gt; IP address**.
        4. For **Public IP address**, select **Enabled**, and then select **IP address**.
        5. If you have an existing public IP address you want to use, select it from the list. Otherwise, select **Create new**, enter a name, and then select **OK** and then **Save**.
    2. Connect to the first RD Connection Broker:

        1. In the Azure portal, select **Browse &gt; Resource groups**, select the resource group for the deployment, and then select the first RD Connection Broker virtual machine (for example, Contoso-Cb1).
        2. Select **Connect &gt; Open** to open the Remote Desktop client.
        3. In the client, select **Connect**, and then select **Use another user account**. Enter the user name and password for a domain administrator account.
        4. Select **Yes** when warned about the certificate.
    3. Download the [ODBC driver for SQL Server](/en-us/sql/connect/odbc/download-odbc-driver-for-sql-server) that matches the version in the ODBC connection string. For the example string, we need to install the version 13 ODBC driver.
    4. Copy the `sqlincli.msi` file to the first RD Connection Broker server.
    5. Open the `sqlincli.msi` file and install the native client.
    6. Repeat steps 1-5 for each RD Connection Brokers (for example, Contoso-Cb2).
    7. Install the ODBC driver on each server that runs the connection broker.

## Configure load balancing on the RD Connection Brokers

You can use a load balancer, such as Azure load balancer; if not, you can set up DNS round-robin.

### Create a load balancer

1. Create an Azure Load Balancer

    1. In the Azure portal, select **Browse &gt; Load balancers &gt; Add**.
    2. Enter a name for the new load balancer (for example, `hacb`).
    3. Select **Internal** for the **Scheme**, **Virtual Network** for your deployment (for example, Contoso-VNet), and the **Subnet** with all of your resources (for example, default).
    4. Select **Static** for the **IP address assignment** and enter a **Private IP address** that isn't currently in use (for example, 10.0.0.32).
    5. Select the appropriate **Subscription**, the **Resource group** with all of your resources, and the appropriate **Location**.
    6. Select **Create**.
2. Create a [probe](/en-us/azure/load-balancer/load-balancer-custom-probe-overview) to monitor which servers are active:

    1. In Azure portal, select **Browse &gt; Load Balancers**, and then select the load balancer you created, for example, `CBLB`. Select **Settings**.
    2. Select **Probes &gt; Add**.
    3. Enter a name for the probe (for example, **RDP**), select **TCP** as the **Protocol**, enter **3389** for the **Port**, and then select **OK**.
3. Create the backend pool of the Connection Brokers:

    1. In **Settings**, select **Backend address pools &gt; Add**.
    2. Enter a name (for example, CBBackendPool), then select **Add a virtual machine**.
    3. Choose an availability set (for example, CbAvSet), and then select **OK**.
    4. Select **Choose the virtual machines**, select each virtual machine, and then select **Select &gt; OK &gt; OK**.
4. Create the RDP load balancing rule:

    1. In **Settings**, select **Load balancing rules**, and then select **Add**.
    2. Enter a name (for example, RDP), select **TCP** for the **Protocol**, enter **3389** for both **Port** and **Backend port**, and select **OK**.
5. Add a DNS record for the Load Balancer:

    1. Connect to the RDMS server virtual machine (for example, Contoso-CB1). Check out the [Prepare the RD Connection Broker VM](rds-prepare-vms) article for steps on how you connect to the VM.
    2. In Server Manager, select **Tools &gt; DNS**.
    3. In the left-hand pane, expand **DNS**, select the DNS machine, select **Forward Lookup Zones**, and then select your domain name (for example, Contoso.com). (It might take a few seconds to process the query to the DNS server for the information.)
    4. Select **Action &gt; New Host (A or AAAA)**.
    5. Enter the name (for example, `hacb`) and the IP address specified earlier (for example, 10.0.0.32).

### Configure DNS round-robin

The following steps are an alternative to creating an Azure Internal Load Balancer.

1. Connect to the RDMS server in the Azure portal. using Remote Desktop Connection client
2. Create DNS records:

    1. In Server Manager, select **Tools &gt; DNS**.
    2. In the left-hand pane, expand **DNS**, select the DNS machine, select **Forward Lookup Zones**, and then select your domain name (for example, Contoso.com). (It might take a few seconds to process the query to the DNS server for the information.)
    3. Select **Action** and **New Host (A or AAAA)**.
    4. Enter the **DNS Name** for the RD Connection Broker cluster (for example, `hacb`), and then enter the **IP address** of the first RD Connection Broker.
    5. Repeat steps 3-4 for each RD Connection Broker, providing each unique IP address for each record.

For example, if the IP addresses for the two RD Connection Broker virtual machines are 10.0.0.8 and 10.0.0.9, you would create two DNS host records:

- Host name: `hacb.contoso.com`, IP address: `10.0.0.8`
- Host name: `hacb.contoso.com`, IP address: `10.0.0.9`

## Configure the Connection Brokers for high availability

1. Add the new RD Connection Broker server to Server Manager:

    1. In Server Manager, select **Manage &gt; Add Servers**.
    2. Select **Find Now**.
    3. Select the newly created RD Connection Broker server (for example, Contoso-Cb2) and select **OK**.
2. Configure high availability for the RD Connection Broker:

    1. In Server Manager, select **Remote Desktop Services &gt; Overview**.
    2. Right-click **RD Connection Broker**, and then select **Configure High Availability**.
    3. Page through the wizard until you get to the Configuration type section. Select **Shared database server**, and then select **Next**.
    4. Enter the DNS name for the RD Connection Broker cluster.
    5. Enter the connection string for the SQL DB, and then page through the wizard to establish high availability.
3. Add the new RD Connection Broker to the deployment

    1. In Server Manager, select **Remote Desktop Services &gt; Overview**.
    2. Right-click the RD Connection Broker, and then select **Add RD Connection Broker Server**.
    3. Page through wizard until you get to Server Selection, then select the newly created RD Connection Broker server (for example, Contoso-CB2).
    4. Complete the wizard, accepting the default values.
4. Configure trusted certificates on RD Connection Broker servers and clients.