---
layout: Conceptual
title: Step 3 Plan a Load-Balanced Cluster Deployment | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/ras/cluster/plan/step-3-plan-a-load-balanced-cluster-deployment
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to plan the load-balancing configuration and cluster deployment.
ms.topic: how-to
ms.author: roharwoo
author: robinharwood
ms.date: 2020-08-07T00:00:00.0000000Z
locale: en-us
document_id: 5fe516d0-e7c7-cbdd-4cb2-201d3dda8748
document_version_independent_id: 031ee793-e803-2375-27e2-eacc80b2c84a
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/ras/cluster/plan/Step-3-Plan-a-Load-Balanced-Cluster-Deployment.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/ras/cluster/plan/step-3-plan-a-load-balanced-cluster-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/ras/cluster/plan/Step-3-Plan-a-Load-Balanced-Cluster-Deployment.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/f98c9a19-e481-4f15-8047-76b641e6ed57
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/f5685781-a4fd-40f1-8126-59abde4643bf
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9c258172-3961-a096-a08a-8980fd80743b
---

# Step 3 Plan a Load-Balanced Cluster Deployment | Microsoft Learn

The next step is to plan the load-balancing configuration and cluster deployment.

| Task | Description |
| --- | --- |
| 3.1 Plan load balancing | Decide whether to use Windows Network Load Balancing (NLB), or an external load balancer (ELB). |
| 3.2 Plan IP-HTTPS | If a self-signed certificate is not used, the Remote Access server needs an SSL certificate on each server in the cluster, in order to authenticate IP-HTTPS connections. |
| 3.3 Plan for VPN client connections | Note the requirements for VPN client connections. |
| 3.4 Plan the network location server | If the network location server website is hosted on the Remote Access server, and a self-signed certificate is not used, ensure that each server in the cluster has a server certificate to authenticate the connection to the website. |

## 3.1 Plan load balancing

Remote Access can be deployed on a single server, or on a cluster of Remote Access servers. Traffic to the cluster can be load balanced to provide high availability and scalability for DirectAccess clients. There are two load balancing options:

- **Windows NLB**-Windows NLB is a Windows server feature. To use it, you do not require additional hardware because all the servers in the cluster are responsible for managing the traffic load. Windows NLB supports a maximum of eight servers in a Remote Access cluster.
- **External load balancer**-Using an external load balancer requires external hardware to manage the traffic load between the Remote Access cluster servers. In addition, using an external load balancer supports a maximum of 32 Remote Access servers in a cluster. Some points to keep in mind when configuring external load balancing are:

    - The administrator must ensure that the Virtual IPs configured through the Remote Access load balancing wizard are used on the external load balancers (like F5 Big-Ip Local Traffic Manager system). When external load balancing is enabled, the IP addresses on the external and internal interfaces will be promoted to Virtual IP addresses, and have to be plumbed on the load balancers. This is done so that the administrator does not have to change the DNS entry for the public name of the cluster deployment. Also, the IPsec tunnel endpoints are derived from the server IPs. If the administrator provides separate Virtual IPs, then the client will not be able to connect to the server. See example for configuring DirectAccess with External Load Balancing in 3.1.1 External Load Balancer configuration example.
    - Many external load balancers (including F5) do not support load balancing of 6to4 and ISATAP. If the Remote Access server is an ISATAP router, the ISATAP function should be moved to a different computer. Also, when ISATAP function is on a different computer, the DirectAccess servers must have native IPv6 connectivity with the ISATAP router. Note that this connectivity should be present before configuring DirectAccess.
    - For external load balancing, if Teredo has to be used, all the Remote Access servers must have two consecutive public IPv4 addresses as dedicated IP addresses. The Virtual IPs of the cluster also must have two consecutive public IPv4 addresses. This is not true for Windows NLB where only the Virtual IPs of the cluster must have two consecutive public IPv4 addresses. If Teredo is not used, two consecutive IP addresses are not required.
    - The administrator can switch from Windows NLB to external load balancer and vice versa. Note that the administrator cannot switch from external load balancer to Windows NLB if he has more than 8 servers in the external load balancer deployment.

### 3.1.1 External Load Balancer configuration example

This section describes the configuration steps for enabling an external load balancer on a new Remote Access deployment. When using an external load balancer, the Remote Access cluster may look like the figure below, where the Remote Access servers are connected to the corporate network through a load balancer on the internal network, and to the Internet through a load balancer connected to the external network:

![External Load Balancer configuration example](../../../../media/step-3-plan-a-load-balanced-cluster-deployment/elbdiagram-ura_enterprise_nlb-.png)

##### Planning information

1. External VIPs (IPs that the client will use to connect to Remote Access) were decided to be 131.107.0.102, 131.107.0.103
2. Load balancer on external network self-IPs - 131.107.0.245 (Internet), 131.107.1.245

    The perimeter network (also known as demilitarized zone and DMZ) is between the load balancer on the external network and the Remote Access server.
3. IP addresses for the Remote Access server on the perimeter network - 131.107.1.102, 131.107.1.103
4. IP addresses for the Remote Access server on the ELB network (i.e. between the Remote Access server and the load balancer on the internal network) - 30.11.1.101, 2006:2005:11:1::101
5. Load balancer on internal network self-IPs - 30.11.1.245 2006:2005:11:1::245 (ELB), 30.1.1.245 2006:2005:1:1::245 (Corpnet)
6. Internal VIPs (IP addresses used for client web-probe and for network location server, if installed on the Remote Access servers) were decided to be 30.1.1.10, 2006:2005:1:1::10

##### Steps

1. Configure the Remote Access server's external network adapter (that is connected to the perimeter network) with addresses 131.107.0.102, 131.107.0.103. This step is required for the DirectAccess configuration to detect the correct IPsec tunnel endpoints.
2. Configure the Remote Access server's internal network adapter (that is connected to the ELB network) with the web-probe/network location server IP addresses (30.1.1.10, 2006:2005:1:1::10). This step is required for allowing clients to access the web-probe IP, so the network connectivity assistant correctly indicates the connection status to DirectAccess. This step also allows access to the network location server, if it is configured on the DirectAccess server.

    Note

    Make sure that the domain controller is reachable from the Remote Access server with this configuration.
3. Configure DirectAccess single server on the Remote Access server.
4. Enable external load balancing in the DirectAccess configuration. Use 131.107.1.102 as the external dedicated IP address (DIP) (131.107.1.103 will be selected automatically), use 30.11.1.101, 2006:2005:11:1::101 as the internal DIPs.
5. Configure the external virtual IPs (VIP) on the external load balancer with addresses 131.107.0.102 and 131.107.0.103. Also, configure the internal VIPs on the external load balancer with addresses 30.1.1.10 and 2006:2005:1:1::10.
6. The Remote Access server will now be configured with the planned IP addresses, and the external and internal IP addresses for the cluster will be configured according to the planned IP addresses.

## 3.2 Plan IP-HTTPS

1. **Certificate requirements**-During deployment of the single Remote Access server you selected to use either an IP-HTTPS certificate issued by a public or internal certification authority (CA), or a self-signed certificate. For the cluster deployment, you must use identical type of certificate on each member of the Remote Access cluster. That is, if you used a certificate issued by a public CA (recommended), you must install a certificate issued by a public CA on each member of the cluster. The subject name of the new certificate should be identical to the subject name of the IP-HTTPS certificate currently used in your deployment. Note that if you are using self-signed certificates these will be configured automatically on each server during cluster deployment.
2. **Prefix requirements**-Remote Access enables load balancing of both SSL-based traffic and DirectAccess traffic. To load balance all IPv6 based DirectAccess traffic, Remote Access must examine the IPv4 tunneling for all transition technologies. Because IP-HTTPS traffic is encrypted, examining the content of the IPv4 tunnel is not possible. To enable IP-HTTPS traffic to be load balanced, you must allocate a wide enough IPv6 prefix so that a different IPv6 /64 prefix can be assigned to every cluster member. You can configure a maximum of 32 servers in a load balanced cluster; therefore, you must specify a /59 prefix. This prefix must be routable to the internal IPv6 address of the Remote Access cluster, and is configured in the Remote Access Server Setup wizard.

    Note

    The prefix requirements are relevant only in an IPv6 enabled internal network (IPv6-only, or IPV4+IPv6). In an IPv4 only corporate network, the client prefix is automatically configured and the administrator cannot change it.

## 3.3 Plan for VPN client connections

There are a number of considerations for VPN client connections:

- VPN client traffic cannot be load balanced if VPN client addresses are allocated using DHCP. A static address pool is required.
- RRAS can be enabled on a load-balanced cluster that has been deployed for DirectAccess only, using **Enable VPN** on the Tasks pane of the Remote Access Management console.
- Any VPN changes completed in the Routing and Remote Access Management console (rrasmgmt.msc) will have to be replicated manually on all Remote Access servers in the cluster.
- To enable VPN IPv6 client traffic to be load balanced, you must specify a 59-bit IPv6 prefix.

## 3.4 Plan the network location server

If you are running the network location server website on the single Remote Access server, during deployment you selected to use either a certificate issued by an internal certification authority (CA), or a self-signed certificate. Note the following:

1. Each member of the Remote Access cluster must have a certificate for the network location server that corresponds to the DNS entry for the network location server website.
2. The certificate for each cluster server must be issued in the same way as the certificate on the single Remote Access server current network location server certificate. For example, if you used a certificate issued by an internal CA, you must install a certificate issued by the internal CA on each member of the cluster.
3. If you used a self-signed certificate, a self-signed certificate will be configured automatically for each server during cluster deployment.
4. The subject name of the certificate must not be identical to the name of any of the servers in the Remote Access deployment.