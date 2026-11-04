---
layout: Conceptual
title: SMB over QUIC | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/storage/file-server/smb-over-quic
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: storage
ms.update-cycle: 1095-days
description: Learn about SMB over QUIC, a secure alternative to TCP for file sharing in Windows and Windows Server that enables encrypted access to file servers over untrusted networks.
ms.topic: how-to
author: robinharwood
ms.author: roharwoo
ms.contributor: inhenkel
ms.date: 2025-07-24T00:00:00.0000000Z
ms.custom: sfi-image-nochange
locale: en-us
document_id: 64dadae1-7656-54e0-099d-620229836135
document_version_independent_id: 8f86a34d-ce81-d571-e118-29169a2c0df3
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/storage/file-server/smb-over-quic.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: storage/file-server/smb-over-quic
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/storage/file-server/smb-over-quic.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 4b824e29-6fe6-cbc8-3a16-d4fb52712a60
---

# SMB over QUIC | Microsoft Learn

SMB over QUIC introduces an alternative to the TCP network transport, providing secure, reliable connectivity to edge file servers over untrusted networks like the Internet. QUIC is an IETF-standardized protocol with many benefits when compared with TCP:

- All packets are always encrypted and handshake is authenticated with TLS 1.3
- Parallel streams of reliable and unreliable application data
- Exchanges application data in the first round trip (0-RTT)
- Improved congestion control and loss recovery
- Survives a change in the clients IP address or port

SMB over QUIC offers an "SMB VPN" for telecommuters, mobile device users, and high security organizations. The server certificate creates a TLS 1.3-encrypted tunnel over the internet-friendly UDP port 443 instead of the legacy TCP port 445. All SMB traffic, including authentication and authorization within the tunnel is never exposed to the underlying network. SMB behaves normally within the QUIC tunnel, meaning the user experience doesn't change. SMB features like multichannel, signing, compression, continuous availability, directory leasing, and so on, work normally.

A file server administrator must opt in to enabling SMB over QUIC. It isn't on by default and a client can't force a file server to enable SMB over QUIC. Windows SMB clients still use TCP by default and will only attempt SMB over QUIC if the TCP attempt first fails or if intentionally requiring QUIC using `NET USE /TRANSPORT:QUIC` or `New-SmbMapping -TransportType QUIC`.

Note

It's not recommended to define particular names for DFS namespaces in scenarios involving SMB and QUIC connections with external endpoints. This is because the internal DFS namespace names are going to be referenced, and these references are usually not reachable for an external client in current releases of Windows.

## Prerequisites

To use SMB over QUIC, you need the following things:

- An SMB server running on one of the following operating systems.

    - Windows Server 2022 Datacenter: Azure Edition ([Microsoft Server Operating Systems](https://aka.ms/ws2022ae-ga)) or later
    - Any edition of Windows Server 2025 or later
- A Windows 11 device ([Windows for business](https://www.microsoft.com/windows/business))
- The SMB server and client must be joined to an Active Directory domain or the client must have a local user account on the SMB server. The SMB server must have access to at least one domain controller for authentication, but no domain controller requires any internet access. We recommended using SMB over QUIC with Active Directory domains however it isn't required. You can also use SMB over QUIC on a workgroup-joined server with local user credentials and NTLM.
- Your server must be accessible to clients on its public interface by adding a firewall allow rule to allow SMB over QUIC. By default SMB over QUIC uses UDP/443 inbound. Do **not** allow TCP/445 inbound to the file server. To learn about how to change the default port, see [Configure alternative SMB ports](smb-ports).
- The file server must have access to at least one domain controller for authentication, but no domain controller requires any internet access.
- Windows Admin Center (WAC) ([Homepage](https://aka.ms/windowsadmincenter))
- A Public Key Infrastructure (PKI) to issue certificates like Active Directory Certificate Server or access to a trusted third party certificate issuer like Verisign, Digicert, Let's Encrypt, etc.
- Administrative privileges or equivalent for the SMB server you're configuring.

## Deploy SMB over QUIC

### Step 1: Install a server certificate

1. Create a Certificate Authority-issued certificate with the following properties:

    - Key usage: digital signature
    - Purpose: Server Authentication (EKU 1.3.6.1.5.5.7.3.1)
    - Signature algorithm: SHA256RSA *(or greater)*
    - Signature hash: SHA256 *(or greater)*
    - Public key algorithm: ECDSA\_P256 *(or greater. Can also use RSA with at least 2048 length)*
    - Subject Alternative Name (SAN): *(A DNS name entry for each fully qualified DNS name used to reach the SMB server)*
    - Subject: *(CN= anything, but must exist)*
    - Private key included: yes

    ![Screenshot of certificate settings showing Signature algorithm with a value of sha256RSA, signature hash algorithm value of sha256, and Subject value of ws2022-quic.](media/smb-over-quic/cert1.png)

    ![Screenshot of certificate settings under the Detail tab showing Public key value of ECC (256 bits), public key parameters ECDSA-P256 and Application policies 1 application Certificate Policy. ](media/smb-over-quic/cert2.png)

    ![Screenshot of certificate details showing subject alternative name value as DNS Name equals contoso.com, and Key Usage value as Digital Signature, Non-Repudiated.](media/smb-over-quic/certificate-details.png)

    If using a Microsoft Enterprise Certificate Authority, you can create a certificate template and allow the file server administrator to supply the DNS names when requesting it. For more information on creating a certificate template, review [Designing and Implementing a PKI: Part III Certificate Templates](https://techcommunity.microsoft.com/t5/ask-the-directory-services-team/designing-and-implementing-a-pki-part-iii-certificate-templates/ba-p/397860). For a demonstration of creating a certificate for SMB over QUIC using a Microsoft Enterprise Certificate Authority, watch this video:

    For requesting a third-party certificate, consult your vendor documentation.
2. If using a Microsoft Enterprise Certificate Authority:

    1. Start *MMC.EXE* on the file server.
    2. Add the **Certificates** snap-in, and select the **Computer account**.
    3. Expand **Certificates (Local Computer)**, **Personal**, then right-click **Certificates** and select **Request New Certificate**.
    4. Select **Next**
    5. Select **Active Directory Enrollment Policy**
    6. Select **Next**
    7. Select the certificate template for SMB over QUIC that was published in Active Directory.
    8. Select **More information is required to enroll for this certificate. Click here to configure settings.**
    9. So users can use to locate the file server, fill in the value **Subject** with a common name and **Subject Alternative Name** with one or more DNS names.
    10. Select **Ok** and then select **Enroll**.

    ![An image showing the Microsoft Management Console Certificate Enrollment with SMB over QUIC selected.](media/smb-over-quic/select-cert.png)

    ![An image showing the Certificate Properties windows of the selected certificate.](media/smb-over-quic/certificate-properties-subject.png)

Note

Don't use IP addresses for SMB over QUIC server Subject Alternative Names.

- IP addresses will require the use of NTLM, even if Kerberos is available from a domain controller or through KDC Proxy.
- Azure IaaS VMs running SMB over QUIC use NAT for a public interface back to a private interface. SMB over QUIC does not support using the IP address for the server name through a NAT, you must use a fully qualified DNS name that resolves to the public interface IP address only in this case.

Note

If you're using a certificate file issued by a third party certificate authority, you can use the Certificates snap-in or WAC to import it.

### Step 2: Configure SMB over QUIC

To configure SMB over QUIC, select your preferred method and follow the steps.

Important

If you're using Windows Server 2025, you need to use the PowerShell method to configure SMB over QUIC. The Windows Admin Center method is not currently supported for Windows Server 2025.

For a demonstration of configuring and using SMB over QUIC, watch this video:

# [Windows Admin Center](#tab/windows-admin-center)
1. Sign in to your file server as an administrator.
2. Install the latest version of WAC on a management PC or the file server. You need the latest version of the **Files & File Sharing** extension. It's installed automatically by WAC if **Automatically update extensions** is enabled in **Settings &gt; Extensions**.
3. Connect to the server with WAC and select the **Settings** icon in the lower left. In the **File shares (SMB server)** section, under **File sharing across the internet with SMB over QUIC**, select **Configure**.
4. Select a certificate under **Select a computer certificate for this file server**, select the server addresses clients can connect to or select **Select all**, and select **Enable**.

    ![An image showing the configuration screen for SMB over QUIC in Windows Admin Center.](media/smb-over-quic/wac1.png)
5. Ensure that the certificate and SMB over QUIC report are healthy.

    ![An image showing all of the certificates available for the configured SMB over QUIC setting in Windows Admin Center.](media/smb-over-quic/windows-admin-center-certificates.png)
6. Select the **Files and File Sharing** menu option. Note your existing SMB shares or create a new one.

# [PowerShell](#tab/powershell)
1. Sign in to your file server as an administrator.
2. Open an elevated PowerShell prompt.
3. List the certificates in the server's certificate store by running the following command.

    ```powershell
    Get-ChildItem -Path Cert:\LocalMachine\My
    ```
4. Run the following command to store the certificate in a variable. Replace `<subject name>` with the subject name of the certificate you want to use.

    ```powershell
    $serverCert = Get-ChildItem -Path Cert:\LocalMachine\My | Where-Object {$_.Subject -Match "<subject name>"}
    ```
5. Verify the certificate matches the one you want to use by running the following command.

    ```powershell
    $serverCert
    ```
6. To enable SMB over QUIC using the certificate thumbprint of the matched certificate, run the following command. Make sure to replace `<server FQDN>` with the fully qualified domain name of the SMB over QUIC server.

    ```powershell
    New-SmbServerCertificateMapping -Name <server FQDN> -ThumbPrint $serverCert.Thumbprint -Storename My
    ```

---

If you want to apply control to SMB over client, you can use Client Access Control. To learn more how to restrict which clients can access SMB over QUIC servers, see [Configure SMB over QUIC client access control](configure-smb-over-quic-client-access-control).

### Step 3: Connect to SMB shares

1. Join your Windows client device to your domain. Be certain the names of the SMB over QUIC file server's certificate subject alternative names are published to DNS and are fully qualified **or** added to the HOST files for your Windows client. Ensure that the server's certificate subject alternative names are published to DNS **or** added to the HOSTS files for your Windows client.
2. Move your Windows client device to an external network where it no longer has any network access to domain controllers or the file server's internal IP addresses.
3. In Windows File Explorer, in the Address Bar, type the UNC path to a share on the file server and confirm you can access data in the share. Alternatively, you can use `NET USE /TRANSPORT:QUIC` or `New-SmbMapping -TransportType QUIC` with a UNC path. Examples:

    ```cmd
    REM Automatically tries TCP then QUIC
    NET USE * \\fsedge1.contoso.com\sales
    
    REM Tries only QUIC
    NET USE * \\fsedge1.contoso.com\sales /TRANSPORT:QUIC
    ```

    ```powershell
    #Tries only QUIC
    New-SmbMapping -LocalPath 'Z:' -RemotePath '\\fsedge1.contoso.com\sales' -TransportType QUIC
    ```

## Manage SMB over QUIC

# [PowerShell](#tab/powershell2)
Admins can disable SMB over QUIC for a server by running the following command:

```powershell
Set-SmbServerConfiguration -EnableSMBQUIC $false
```

To disable SMB over QUIC for a client device, run the following command:

```powershell
Set-SmbClientConfiguration -EnableSMBQUIC $false
```

SMB over QUIC can be enabled on either the server or client by setting `$false` to `$true`.

Admins can now specify an SMB over QUIC server exception list on the client. A client can connect to a server when SMB over QUIC is disabled on the client as long as the server IP address, NetBIOS name or FQDN is in the exception list. To learn more, see [Enable exceptions to NTLM blocking](/en-us/windows-server/storage/file-server/smb-ntlm-blocking?tabs=group-policy#enable-exceptions-to-ntlm-blocking). A server exception list can be created by running the following command:

```powershell
Set-SmbClientConfiguration -DisabledSMBQUICServerExceptionList "<Server01>, <Server02>, <Server03>"
```

# [Group Policy](#tab/grouppolicy)
To disable SMB over QUIC for the server, perform the following:

1. Select **Start**, type **gpedit.msc** and select **Enter**.
2. In the **Group Policy** UI, navigate to **Computer Configuration\Administrative Templates\Network\Lanman Server**, select **Enable SMB over QUIC**, and then select **Disabled**.

To enable SMB over QUIC, set this policy to **Enabled**.

To disable SMB over QUIC for a client device, perform the following:

1. In the **Group Policy** UI, navigate to **Computer Configuration\Administrative Templates\Network\Lanman Workstation**, select **Enable SMB over QUIC**, and then select **Disabled**.

To enable SMB over QUIC, set this policy to **Enabled**.

To enable a server exception list for SMB over QUIC, perform the following:

1. In the **Group Policy** UI, navigate to **Computer Configuration\Administrative Templates\Network\Lanman Workstation**, select **Disabled SMB over QUIC Server Exception List**, and then select **Enabled**.
2. In the **Disabled SMB over QUIC Server Exception List** options box, add the server *IP address*, *NetBIOS name* or *FQDN*. Use a comma to add multiple values.
3. Once the exception list is populated, select **OK**.

---

### SMB over QUIC client auditing

Auditing is used to track client connections for SMB over QUIC, with events being written to an event log. The Event Viewer captures this information for the QUIC transport protocol. This feature is available to SMB Client starting with Windows 11, version 24H2 To view these logs, follow these steps:

1. Open the **Event Viewer**.
2. Navigate to **Applications and Services Logs\Microsoft\Windows\SMBClient\Connectivity**.
3. Monitor event ID **30832**.

### Configure the KDC Proxy (optional, but recommended)

By default, a Windows client device won't have access to an Active Directory domain controller when connecting to an SMB over QUIC file server. This means authentication uses NTLMv2, where the file server authenticates on behalf of the client. No NTLMv2 authentication or authorization occurs outside the TLS 1.3-encrypted QUIC tunnel. However, we still recommend using Kerberos as a general security best practice and don't recommend creating new NTLMv2 dependencies in deployments. To allow this, you can configure the KDC proxy to forward ticket requests on the user's behalf, all while using an internet-friendly HTTPS encrypted communication channel. The KDC Proxy is supported by SMB over QUIC and highly recommended.

Note

You cannot configure the WAC in gateway mode using TCP port 443 on a file server where you are configuring KDC Proxy. When configuring WAC on the file server, change the port to one that is not in use and is not 443. If you have already configured WAC on port 443, re-run the WAC setup MSI and choose a different port when prompted.

# [Windows Admin Center](#tab/windows-admin-center1)
1. Ensure you're using WAC version 2110 or later.
2. Configure SMB over QUIC normally. Starting in WAC 2110, the option to configure KDC proxy in SMB over QUIC is automatically enabled and you don't need to perform extra steps on the file servers. The default KDC proxy port is 443 and assigned automatically by WAC.

    Note

    You cannot configure an SMB over QUIC server joined to a Workgroup using WAC. You must join the server to an Active Directory domain or follow the steps in configuring the KDC proxy either in PowerShell or Group Policy.

# [PowerShell](#tab/powershell1)
1. On the file server, in an elevated PowerShell prompt, run:

    ```powershell
    NETSH http add urlacl url=https://+:443/KdcProxy user="NT authority\Network Service"
    
    Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\KPSSVC\Settings" -Name "HttpsClientAuth" -Value 0 -Type DWord -Force
    
    Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\KPSSVC\Settings" -Name "DisallowUnprotectedPasswordAuth" -Value 0 -Type DWord -Force
    
    Get-SmbServerCertificateMapping
    ```
2. Copy the thumbprint value from the certificate associated with SMB over QUIC certificate (there may be multiple lines but they'll all have the same thumbprint) and paste it as the **Certhash** value for the following command:

    ```powershell
    $guid = [Guid]::NewGuid()
    Add-NetIPHttpsCertBinding -IPPort 0.0.0.0:443 -CertificateHash <thumbprint> -CertificateStoreName "My" -ApplicationId "{$guid}" -NullEncryption $false
    ```
3. Add the file server's SMB over QUIC names as SPNs in Active Directory for Kerberos. For example:

    ```powershell
    NETDOM computername ws2022-quic.corp.contoso.com /add fsedge1.contoso.com`
    ```
4. Set the KDC Proxy service to automatic and start it:

    ```powershell
    Set-Service -Name kpssvc -StartupType Automatic
    
    Start-Service -Name kpssvc
    ```

# [Group Policy](#tab/group-policy1)
1. Configure the following group policy to apply to the Windows client device:

    **Computer Configuration\Administrative Templates\System\Kerberos\Specify KDC proxy servers for Kerberos clients**

    The format of this group policy setting is a value name of your fully qualified Active Directory domain name and the value becomes the external name you specified for the QUIC server. For example, where the Active Directory domain is named `corp.contoso.com` and the external DNS domain is named `contoso.com`:

    `value name: corp.contoso.com`

    `value: <https fsedge1.contoso.com:443:kdcproxy />`

    This Kerberos realm mapping means that if user `ned@corp.contoso.com` tried to connect to a file server name `fs1edge.contoso.com"`, the KDC proxy knows to forward the kerberos tickets to a domain controller in the internal `corp.contoso.com` domain. The communication with the client will be over HTTPS on port 443 and user credentials aren't directly exposed on the client-file server network.
2. Create a Windows Defender Firewall rule that inbound-enables TCP port 443 for the KDC Proxy service to receive authentication requests.
3. Ensure that edge firewalls allow HTTPS on port 443 inbound to the file server.
4. Apply the group policy and restart the Windows client device.

---

Note

Automatic configuration of the KDC Proxy will come later in the SMB over QUIC and these server steps will not be necessary.

## Certificate expiration and renewal

An expired SMB over QUIC certificate that you replace with a new certificate from the issuer will contain a new thumbprint. While you can automatically renew SMB over QUIC certificates when they expire using Active Directory Certificate Services, a renewed certificate gets a new thumbprint as well. This effectively means that SMB over QUIC must be reconfigured when the certificate expires, as a new thumbprint must be mapped. Select your new certificate in WAC for the existing SMB over QUIC configuration or use the `Set-SMBServerCertificateMapping` PowerShell command to update the mapping for the new certificate. You can use Azure Automanage for Windows Server to detect impending certificate expiration and prevent an outage. For more information, review [Azure Automanage for Windows Server](/en-us/azure/automanage/automanage-windows-server-services-overview).

## Notes

- For customers not using Azure public cloud, Windows Server 2022 Datacenter: Azure Edition is available on Azure Local beginning with version 22H2.
- We recommended using SMB over QUIC with Active Directory domains but isn't a requirement. You can also use SMB over QUIC on a workgroup-joined server with local user credentials and NTLM, or Azure IaaS with Microsoft Entra joined Windows Servers. Microsoft Entra joined Windows Servers for non-Azure IaaS based machines isn't supported. Microsoft Entra joined Windows Servers don't support credentials for remote Windows security operations because Microsoft Entra ID doesn't contain user or group SIDs. Microsoft Entra joined Windows Servers must use either a domain-based or local user account to access the SMB over QUIC share.
- You can't configure SMB over QUIC using WAC when the SMB server is in a workgroup (that is, not AD domain joined). Per this scenario, you must use the [New-SMBServerCertificateMapping](/en-us/powershell/module/smbshare/new-smbservercertificatemapping) cmdlet.
- We recommend read-only domain controllers configured only with passwords of mobile users be made available to the file server.
- Users should have strong passwords or, ideally, be configured using a [passwordless strategy](/en-us/windows/security/identity-protection/hello-for-business/passwordless-strategy) with [Windows Hello for Business MFA](/en-us/windows/security/identity-protection/hello-for-business) or [smart cards](/en-us/windows/security/identity-protection/smart-cards/smart-card-windows-smart-card-technical-reference). Configure an account lockout policy for mobile users through [fine-grained password policy](../../identity/ad-ds/get-started/adac/introduction-to-active-directory-administrative-center-enhancements--level-100-#fine_grained_pswd_policy_mgmt) and you should deploy intrusion protection software to detect brute force or password spray attacks.

## More references

- [Storage at Microsoft blog](https://aka.ms/FileCab)
- [QUIC Working Group homepage](https://quicwg.org/)
- [Microsoft MsQuic GitHub homepage](https://github.com/microsoft/msquic)
- [QUIC Wikipedia](https://en.wikipedia.org/wiki/QUIC)
- [TLS 1.3 Working Group homepage](https://tlswg.org/)
- [Taking Transport Layer Security (TLS) to the next level with TLS 1.3](https://www.microsoft.com/security/blog/2020/08/20/taking-transport-layer-security-tls-to-the-next-level-with-tls-1-3/)