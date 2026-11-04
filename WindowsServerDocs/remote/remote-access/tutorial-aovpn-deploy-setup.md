---
layout: Conceptual
title: 'Tutorial: Deploy Always On VPN Infrastructure | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/remote/remote-access/tutorial-aovpn-deploy-setup
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: remote
ms.update-cycle: 1095-days
description: Learn how to deploy Always On VPN connections for Windows client computers that are working offsite, such as from home, a customer site, or a public location.
ms.topic: tutorial
ms.author: roharwoo
author: robinharwood
ms.date: 2025-05-07T00:00:00.0000000Z
locale: en-us
document_id: 6fba6237-837f-38e0-3859-014ff2cecc9c
document_version_independent_id: d1f3415b-c762-7ab1-2e74-7449456b1509
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/remote/remote-access/tutorial-aovpn-deploy-setup.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote/remote-access/tutorial-aovpn-deploy-setup
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/remote/remote-access/tutorial-aovpn-deploy-setup.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 4b6947e2-1642-0911-dc6b-fe45a65adc07
---

# Tutorial: Deploy Always On VPN Infrastructure | Microsoft Learn

Always On VPN is a remote access solution in Windows Server that provides seamless and secure connectivity for remote users to corporate networks. It supports advanced authentication methods and integrates with existing infrastructure, offering a modern alternative to traditional VPN solutions. This tutorial begins the series to deploy Always On VPN in a sample environment.

In this tutorial, you learn how to deploy a sample infrastructure for Always On VPN connections for remote domain-joined Windows client computers. To create a sample infrastructure, you:

- Create an Active Directory domain controller.
- Configure Group Policy for autoenrollment of certificates.
- Create a Network Policy Server (NPS) server.
- Create a VPN server.
- Create a VPN user and group.
- Configure the VPN server as a RADIUS client.
- Configure the NPS server as a RADIUS server.

To learn more about Always On VPN, including supported integrations, security and connectivity features, see [Always On VPN Overview](overview-always-on-vpn).

## Prerequisites

To complete the steps in this tutorial, you need to meet the following prerequisites:

- Three servers (physical or virtual) running a supported version Windows Server. These servers are the domain controller, NPS server, and VPN server.
- The server you use for the NPS server needs two physical network adapters installed: one to connect to the internet, and one to connect to the network where the domain controller is located.
- A user account on all machines that is a member of the local **Administrators** security group, or equivalent.

Important

Using Remote Access in Microsoft Azure isn't supported. For more information, see [Microsoft server software support for Microsoft Azure virtual machines](https://support.microsoft.com/help/2721672/microsoft-server-software-support-for-microsoft-azure-virtual-machines).

## Create the domain controller

1. On the server you want to be the domain controller, install [Active Directory Domain Services (AD DS)](/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview). For detailed information on how to install AD DS, see [Install Active Directory Domain Services](/en-us/windows-server/identity/ad-ds/deploy/install-active-directory-domain-services--level-100-#to-install-ad-ds-by-using-server-manager).
2. Promote the Windows Server to domain controller. For this tutorial, you create a new forest and the domain to that new forest. For detailed information on how to install the domain controller, see [AD DS Installation](/en-us/windows-server/identity/ad-ds/deploy/ad-ds-installation-and-removal-wizard-page-descriptions#dns-options).
3. Install and configure the Certificate Authority (CA) on the domain controller. For detailed information on how to install the CA, see [Install the Certification Authority](/en-us/windows-server/networking/core-network-guide/cncg/server-certs/install-the-certification-authority).

## Configure Group Policy for autoenrollment of certificates

In this section, you create a Group Policy on the domain controller so that domain members automatically request user and computer certificates. This configuration enables VPN users to request and retrieve user certificates that automatically authenticate VPN connections. This policy also allows the NPS server to request server authentication certificates automatically.

1. On the domain controller, open the Group Policy Management console.
2. In the left pane, right-click your domain (for example, `corp.contoso.com`). Select **Create a GPO in this domain, and Link it here**.
3. On the **New GPO** dialog box, for **Name**, enter *Autoenrollment Policy*. Select **OK**.
4. In the left pane, right-click **Autoenrollment Policy**. Select **Edit** to open the **Group Policy Management Editor**.
5. In **Group Policy Management Editor**, complete the following steps to configure computer certificate autoenrollment:

    1. Navigate to **Computer Configuration** &gt; **Policies** &gt; **Windows Settings** &gt; **Security Settings** &gt; **Public Key Policies**.
    2. In the details pane, right-click **Certificate Services Client – Auto-Enrollment**. Select **Properties**.
    3. On the **Certificate Services Client – Auto-Enrollment Properties** dialog box, for **Configuration Model**, select **Enabled**.
    4. Select **Renew expired certificates, update pending certificates, and remove revoked certificates** and **Update certificates that use certificate templates**.
    5. Select **OK**.
6. In **Group Policy Management Editor**, complete the following steps to configure user certificate autoenrollment:

    1. Navigate to **User Configuration** &gt; **Policies** &gt; **Windows Settings** &gt; **Security Settings** &gt; **Public Key Policies**.
    2. In the details pane, right-click **Certificate Services Client – Auto-Enrollment** and select **Properties**.
    3. On the **Certificate Services Client – Auto-Enrollment Properties** dialog box, in **Configuration Model**, select **Enabled**.
    4. Select **Renew expired certificates, update pending certificates, and remove revoked certificates** and **Update certificates that use certificate templates**.
    5. Select **OK**.
    6. Close Group Policy Management Editor.
7. Apply the Group Policy to users and computers in the domain.
8. Close the Group Policy Management console.

## Create the NPS server

1. On the server you want to be the NPS server, install the [Network Policy and Access Services (NPS) role](/en-us/windows-server/networking/technologies/nps/nps-top). For detailed information on how to install NPS, see [Install Network Policy Server](/en-us/windows-server/networking/technologies/nps/nps-manage-install).
2. Register the NPS Server in Active Directory. For information on how to register NPS Server in Active Directory, see [Register an NPS in an Active Directory Domain](/en-us/windows-server/networking/technologies/nps/nps-manage-register).
3. Make sure that your firewalls allow the traffic that is necessary for both VPN and RADIUS communications to function correctly. For more information, see [Configure Firewalls for RADIUS Traffic](../../networking/technologies/nps/nps-firewalls-configure).
4. Create the NPS Servers group:

    1. On the domain controller, open Active Directory Users and Computers.
    2. Under your domain, right-click **Computers**. Select **New**, then select **Group**.
    3. In **Group name**, enter **NPS Servers**, then select **OK**.
    4. Right-click **NPS Servers** and select **Properties**.
    5. On the **Members** tab of the NPS Servers Properties dialog box, select **Add**.
    6. Select **Object Types**, select the **Computers** check box, then select **OK**.
    7. In **Enter the object names to select**, enter the hostname of the NPS server. Select **OK**.
    8. Close Active Directory Users and Computers.

## Create the VPN server

1. For the server that runs the VPN server, ensure that the machine has two physical network adapters installed: one to connect to the internet, and one to connect to the network where the domain controller is located.
2. Identify which network adapter connects to the internet and which network adapter connects to the domain. Configure the network adapter facing the internet with a public IP address, while the adapter facing the intranet can use an IP address from the local network.
3. For the network adapter connecting to the domain, set the DNS preferred IP address to the IP address of the domain controller.
4. Join the VPN server to the domain. For information on how to join a server to a domain, see [To join a server to a domain](/en-us/windows-server/identity/ad-fs/deployment/join-a-computer-to-a-domain#to-join-a-server-to-a-domain).
5. Open your firewall rules to allow UDP ports 500 and 4500 inbound to the external IP address applied to the public interface on the VPN server. For the network adapter connecting to the domain, allow the following UDP ports: 1812, 1813, 1645, and 1646.
6. Create the VPN Servers group:

    1. On the domain controller, open **Active Directory Users and Computers**.
    2. Under your domain, right-click **Computers**. Select **New**, then select **Group**.
    3. In **Group name**, enter **VPN Servers**, then select **OK**.
    4. Right-click **VPN Servers** and select **Properties**.
    5. On the **Members** tab of the VPN Servers Properties dialog box, select **Add**.
    6. Select **Object Types**, select the **Computers** check box, then select **OK**.
    7. In **Enter the object names to select**, enter the hostname of the VPN server. Select **OK**.
    8. Close Active Directory Users and Computers.
7. Follow the steps in [Install Remote Access as a VPN server](get-started-install-ras-as-vpn) to install the VPN server.
8. Open **Routing and Remote Access** from Server Manager.
9. Right-click the name of the VPN server, and then select **Properties**.
10. In **Properties**, select the **Security** tab and then:

    1. Select **Authentication provider** and select **RADIUS Authentication**.
    2. Select **Configure** to open the RADIUS Authentication dialog.
    3. Select **Add** to open the Add RADIUS Server dialog.

        1. In **Server name**, enter the Fully Qualified Domain Name (FQDN) of the NPS server, which is also a RADIUS server. For example, if the NetBIOS name of your NPS and domain controller server is `nps1` and your domain name is `corp.contoso.com`, enter `nps1.corp.contoso.com`.
        2. In **Shared secret**, select **Change** to open the Change Secret dialog box.
        3. In **New secret**, enter a text string.
        4. In **Confirm new secret**, enter the same text string, then select **OK**.
        5. Save this secret. You need it when you add this VPN server as a RADIUS client later in this tutorial.
    4. Select **OK** to close the **Add RADIUS Server** dialog.
    5. Select **OK** to close the **RADIUS Authentication** dialog.
11. On the VPN server Properties dialog, select **Authentication Methods...**.
12. Select **Allow machine certificate authentication for IKEv2**.
13. Select **OK**.
14. For **Accounting provider**, select **Windows Accounting**.
15. Select **OK** to close the Properties dialog.
16. A dialog prompts you to restart the server. Select **Yes**.

## Create VPN user and group

1. Create a VPN user by taking the following steps:

    1. On the domain controller, open the **Active Directory Users and Computers** console.
    2. Under your domain, right-click **Users**. Select **New**. For **User logon name**, enter any name. Select **Next**.
    3. Choose a password for the user.
    4. Deselect **User must change password at next logon**. Select **Password never expires**.
    5. Select **Finish**. Keep Active Directory Users and Computers open.
2. Create a VPN user group by taking the following steps:

    1. Under your domain, right-click **Users**. Select **New**, then select **Group**.
    2. In **Group name**, enter **VPN Users**, then select **OK**.
    3. Right-click **VPN Users** and select **Properties**.
    4. On the **Members** tab of the VPN Users Properties dialog box, select **Add**.
    5. On the Select Users dialog box, add the VPN user that you created and select **OK**.

## Configure VPN server as a RADIUS client

1. On the NPS server, open your firewall rules to allow UDP ports 1812, 1813, 1645, and 1646 inbound, including the Windows Firewall.
2. Open the **Network Policy Server** console.
3. In the NPS console, double-click **RADIUS Clients and Servers**.
4. Right-click **RADIUS Clients** and select **New** to open the **New RADIUS Client** dialog box.
5. Verify that the **Enable this RADIUS client** check box is selected.
6. In **Friendly name**, enter a display name for the VPN server.
7. In **Address (IP or DNS)**, enter the IP address or the FQDN of the VPN server.

    If you enter the FQDN, select **Verify** if you want to verify that the name is correct and maps to a valid IP address.
8. In **Shared secret**:

    1. Ensure that **Manual** is selected.
    2. Enter the secret that you created in the Create the VPN server section.
    3. For **Confirm shared secret**, reenter the shared secret.
9. Select **OK**. The VPN Server should appear in the list of RADIUS clients configured on the NPS server.

## Configure NPS server as a RADIUS server

1. Register a server certificate for the NPS server, with a certificate that meets the requirements in [Configure Certificate Templates for PEAP and EAP requirements](../../networking/technologies/nps/nps-manage-cert-requirements). To verify that your Network Policy Server (NPS) servers are enrolled with a server certificate from the certification authority (CA), see [Verify Server Enrollment of a Server Certificate](../../networking/core-network-guide/cncg/server-certs/verify-server-enrollment-of-a-server-certificate).
2. In the NPS console, select **NPS (Local)**.
3. In **Standard Configuration**, ensure that **RADIUS server for Dial-Up or VPN Connections** is selected.
4. Select **Configure VPN or Dial-Up** to open the **Configure VPN or Dial-Up** wizard.
5. Select **Virtual Private Network (VPN) Connections**, then select **Next**.
6. In **Specify Dial-Up or VPN Server**, in **RADIUS clients**, select the name of the VPN server.
7. Select **Next**.
8. In **Configure Authentication Methods**, complete the following steps:

    1. Clear **Microsoft Encrypted Authentication version 2 (MS-CHAPv2)**.
    2. Select **Extensible Authentication Protocol**.
    3. For **Type**, select **Microsoft: Protected EAP (PEAP)**. Then select **Configure** to open the **Edit Protected EAP Properties** dialog box.
    4. Select **Remove** to remove the Secured Password (EAP-MSCHAP v2) EAP type.
    5. Select **Add**. The Add EAP dialog box opens.
    6. Select **Smart Card or other certificate**, then select **OK**.
    7. Select **OK** to close Edit Protected EAP Properties.
9. Select **Next**.
10. In **Specify User Groups**, complete the following steps:

    1. Select **Add**. The **Select Users, Computers, Service Accounts, or Groups** dialog box opens.
    2. Enter **VPN Users**, then select **OK**.
    3. Select **Next**.
11. On **Specify IP Filters**, select **Next**.
12. On **Specify Encryption Settings**, select **Next**. Don't make any changes.
13. On **Specify a Realm Name**, select **Next**.
14. Select **Finish** to close the wizard.