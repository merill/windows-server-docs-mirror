---
layout: Conceptual
title: Configure Device-based Conditional Access on-premises | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/configure-device-based-conditional-access-on-premises
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: 'Learn more about: Configure on-premises Conditional Access using registered devices'
ms.date: 2025-03-18T00:00:00.0000000Z
ms.topic: how-to
ms.custom: sfi-image-nochange
locale: en-us
document_id: 74d09c81-d205-dbd0-ea6a-aaf469eadf5c
document_version_independent_id: 458db848-1b30-1115-8814-3a639a57c70b
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Configure-Device-Based-Conditional-Access-on-Premises.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/configure-device-based-conditional-access-on-premises
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Configure-Device-Based-Conditional-Access-on-Premises.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 3919c196-cc48-6645-72d9-813a7d497fe3
---

# Configure Device-based Conditional Access on-premises | Microsoft Learn

The following document guides you through installing and configuring on-premises conditional access with registered devices.

![conditional access](media/using-device-based-conditional-access-on-premises/adfs_itpro4.png)

## Infrastructure prerequisites

The following prerequisites are required.

| Requirement | Description |
| --- | --- |
| A Microsoft Entra subscription with Microsoft Entra ID P1 or P2 | To enable device write-back for on premises conditional access - [a free trial is fine](https://azure.microsoft.com/trial/get-started-active-directory/) |
| Intune subscription | only required for MDM integration for device compliance scenarios -[a free trial is fine](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&amp;dl=INTUNE_A&amp;ali=1#0) |
| Microsoft Entra Connect Sync | Get the latest version [here](https://www.microsoft.com/download/details.aspx?id=47594). |
| Windows Server 2016 | Build 10586 or newer for AD FS |
| Windows Server 2016 Active Directory schema | Schema level 85 or higher is required. |
| Windows Server 2016 domain controller | Only required for Hello For Business key-trust deployments. For more information, see [here](/en-us/windows/security/identity-protection/hello-for-business/hello-identity-verification). |
| Windows 10 client | Build 10586 or newer, joined to the above domain is required for Windows 10 Domain Join and Windows Hello for Business scenarios only |
| Microsoft Entra user account with Microsoft Entra ID P1 or P2 licenses assigned | For registering the device |

## Upgrade your Active Directory Schema

In order to use on-premises conditional access with registered devices, you must first upgrade your AD schema. The following conditions must be met:

- The schema should be version 85 or later
- Only required for the forest that AD FS is joined to

Note

If you installed Microsoft Entra Connect Sync prior to upgrading to the schema version (level 85 or greater) in Windows Server 2016, you'll need to re-run the Microsoft Entra Connect Sync installation and refresh the on-premises AD schema to ensure the synchronization rule for msDS-KeyCredentialLink is configured.

### Verify your schema level

To verify your schema level, do the following:

1. Use ADSIEdit.exe or LDP.exe and connect to the Schema Naming Context.
2. In ADSIEdit, right-click on "CN=Schema,CN=Configuration,DC=&lt;domain&gt;,DC=&lt;com&gt; and select properties. Replace domain and the com portions with your forest information.
3. Under the Attribute Editor locate the objectVersion attribute and it tells you, your version.

![ADSI Edit](media/configure-device-based-conditional-access-on-premises/adsiedit.png)

You may also use the following PowerShell cmdlet (replace the object with your schema-naming context information):

```powershell
Get-ADObject "cn=schema,cn=configuration,dc=domain,dc=local" -Property objectVersion

```

![PowerShell](media/configure-device-based-conditional-access-on-premises/pshell1.png)

For more information on upgrading, see [Upgrade Domain Controllers to Windows Server 2016](../../ad-ds/deploy/upgrade-domain-controllers).

## Enable Microsoft Entra Device Registration

To configure this scenario, you must configure the device registration capability in Microsoft Entra ID.

To do this, follow the steps under [Setting up Microsoft Entra join in your organization](/en-us/azure/active-directory/devices/device-management-azure-portal).

## Set up AD FS

1. Create a [new AD FS 2016 farm](../deployment/deploying-a-federation-server-farm).
2. Or [migrate](../deployment/upgrading-to-ad-fs-in-windows-server) a farm to AD FS 2016 from AD FS 2012 R2
3. Deploy [Microsoft Entra Connect Sync](../deployment/upgrading-to-ad-fs-in-windows-server) using the Custom path to connect AD FS to Microsoft Entra ID.

## Configure Device Write Back and Device Authentication

Note

If you ran Microsoft Entra Connect Sync using Express Settings, the correct AD objects have been created for you. However, in most AD FS scenarios, Microsoft Entra Connect Sync was run with Custom Settings to configure AD FS, so the below steps are necessary.

### Create AD objects for AD FS Device Authentication

If your AD FS farm isn't already configured for Device Authentication (you may see this in the AD FS Management console under Service -&gt; Device Registration), use the following steps to create the correct AD DS objects and configuration.

![Screenshot that shows the Device Registration Overview screen.](media/configure-device-based-conditional-access-on-premises/device1.png)

Note

The below commands require Active Directory administration tools, so if your federation server isn't also a domain controller, first install the tools using step 1 below. Otherwise you may skip step 1.

1. Run the **Add Roles & Features** wizard and select feature **Remote Server Administration Tools** -&gt; **Role Administration Tools** -&gt; **AD DS and AD LDS Tools** -&gt; Choose both the **Active Directory module for Windows PowerShell** and the **AD DS Tools**.

![Screenshot that highlights the Active Directory module for Windows PowerShell and the AD DS Tools options.](media/configure-device-based-conditional-access-on-premises/device2.png)

1. On your AD FS primary server, ensure you're logged in as AD DS user with Enterprise Admin (EA) privileges and open an elevated PowerShell prompt. Then, execute the following PowerShell commands:

`Import-module activedirectory``PS C:\> Initialize-ADDeviceRegistration -ServiceAccountName "<your service account>" ` 3. On the pop-up window hit Yes.

Note

If your AD FS service is configured to use a GMSA account, enter the account name in the format "domain\accountname$"

![Screenshot that shows how to use the listed PowerShell commands.](media/configure-device-based-conditional-access-on-premises/device3.png)

The above PSH creates the following objects:

- RegisteredDevices container under the AD domain partition
- Device Registration Service container and object under Configuration --&gt; Services --&gt; Device Registration Configuration
- Device Registration Service DKM container and object under Configuration --&gt; Services --&gt; Device Registration Configuration

![Screenshot that shows the progress of the objects being created.](media/configure-device-based-conditional-access-on-premises/device4.png)

1. Once this is done, you'll see a successful completion message.

![Screenshot that shows the successful completion message.](media/configure-device-based-conditional-access-on-premises/device5.png)

### Create Service Connection Point (SCP) in AD

If you plan to use Windows 10 domain join (with automatic registration to Microsoft Entra ID) as described here, execute the following commands to create a service connection point in AD DS

1. Open Windows PowerShell and execute the following:

`PS C:>Import-Module -Name "C:\Program Files\Microsoft Azure Active Directory Connect\AdPrep\AdSyncPrep.psm1" `

Note

If necessary, copy the AdSyncPrep.psm1 file from your Microsoft Entra Connect Sync server. This file is located in Program Files\Microsoft Entra Connect\AdPrep

![Screenshot that shows the path to the AdSyncPrep file.](media/configure-device-based-conditional-access-on-premises/device6.png)

1. Provide your Microsoft Entra Conditional Access Administrator credentials.

`PS C:>$aadAdminCred = Get-Credential`

![Screenshot that shows where to provide the Microsoft Entra Conditional Access Administrator credentials.](media/configure-device-based-conditional-access-on-premises/device7.png)

1. Run the following PowerShell command

`PS C:>Initialize-ADSyncDomainJoinedComputerSync -AdConnectorAccount [AD connector account name] -AzureADCredentials $aadAdminCred `

Where the [AD connector account name] is the name of the account you configured in Microsoft Entra Connect Sync when adding your on-premises AD DS directory.

The above commands enable Windows 10 clients to find the correct Microsoft Entra domain to join by creating the serviceConnectionpoint object in AD DS.

### Prepare AD for Device Write Back

To ensure AD DS objects and containers are in the correct state for write-back of devices from Microsoft Entra ID, do the following.

1. Open Windows PowerShell and execute the following:

`PS C:>Initialize-ADSyncDeviceWriteBack -DomainName <AD DS domain name> -AdConnectorAccount [AD connector account name] `

Where the [AD connector account name] is the name of the account you configured in Microsoft Entra Connect Sync when adding your on-premises AD DS directory in domain\accountname format

The above command creates the following objects for device write-back to AD DS, if they don't exist already, and allows access to the specified AD connector account name

- RegisteredDevices container in the AD domain partition
- Device Registration Service container and object under Configuration --&gt; Services --&gt; Device Registration Configuration

### Enable Device Write Back in Microsoft Entra Connect Sync

If you haven't done so before, enable device write-back in Microsoft Entra Connect Sync by running the wizard a second time and selecting **"Customize Synchronization Options"**, then checking the box for device write-back and selecting the forest in which you have run the above cmdlets

### Configure Device Authentication in AD FS

Using an elevated PowerShell command window, configure AD FS policy by executing the following command

`PS C:>Set-AdfsGlobalAuthenticationPolicy -DeviceAuthenticationEnabled $true -DeviceAuthenticationMethod All`

### Check your configuration

For your reference, below is a comprehensive list of the AD DS devices, containers, and permissions required for device write-back and authentication to work

- Object of type ms-DS-DeviceContainer at CN=RegisteredDevices,DC=&lt;domain&gt;

    - Read access to the AD FS service account
    - read/write access to the Microsoft Entra Connect Sync AD connector account
- Container CN=Device Registration Configuration,CN=Services,CN=Configuration,DC=&lt;domain&gt;
- Container Device Registration Service DKM under the above container

![Device Registration](media/configure-device-based-conditional-access-on-premises/device8.png)

- Object of type serviceConnectionpoint at CN=&lt;guid&gt;, CN=Device Registration
- Configuration,CN=Services,CN=Configuration,DC=&lt;domain&gt;
- read/write access to the specified AD connector account name on the new object
- Object of type msDS-DeviceRegistrationServiceContainer at CN=Device Registration Services,CN=Device Registration Configuration,CN=Services,CN=Configuration,DC=&ltdomain&gt;
- Object of type msDS-DeviceRegistrationService in the above container

### See it work

To evaluate the new claims and policies, first register a device. For example, Microsoft Entra join a Windows 10 computer using the Settings app under System -&gt; About, or set up Windows 10 domain join with automatic device registration following the additional steps [here](/en-us/azure/active-directory/devices/hybrid-azuread-join-plan). For information on joining Windows 10 mobile devices, see the document [here](/en-us/windows/client-management/mdm/mdm-enrollment-of-windows-devices).

For easiest evaluation, sign on to AD FS using a test application that shows a list of claims. You'll be able to see new claims including `isManaged`, `isCompliant`, and `trusttype`. If you enable Windows Hello for Business, you'll also see the `prt` claim.

## Configure Additional Scenarios

### Automatic Registration for Windows 10 Domain Joined computers

To enable automatic device registration for Windows 10 domain joined computers, follow steps 1 and 2 [here](/en-us/azure/active-directory/devices/hybrid-azuread-join-plan).

1. Ensure your service connection point in AD DS exists and has the proper permissions (we created this object above, but it doesn't hurt to double check).
2. Ensure AD FS is configured properly
3. Ensure your AD FS system has the correct endpoints enabled and claim rules configured
4. Configure the group policy settings required for automatic device registration of domain joined computers

### Windows Hello for Business

For information on enabling Windows 10 with Windows Hello for Business, see [Enable Windows Hello for Business in your organization.](/en-us/windows/security/identity-protection/hello-for-business/hello-identity-verification)

### Automatic MDM enrollment

To enable automatic MDM enrollment of registered devices follow the steps [here.](/en-us/windows/client-management/mdm/mdm-enrollment-of-windows-devices)

## Troubleshooting

1. If you get an error on `Initialize-ADDeviceRegistration` that complains about an object already existing in the wrong state, such as "The DRS service object has been found without all the required attributes", you may have executed Microsoft Entra Connect Sync PowerShell commands previously and have a partial configuration in AD DS. Try deleting manually the objects under **CN=Device Registration Configuration,CN=Services,CN=Configuration,DC=&lt;domain&gt;** and trying again.
2. For Windows 10 domain joined clients
3. To verify that device authentication is working, sign on to the domain joined client as a test user account. To trigger provisioning quickly, lock and unlock the desktop at least one time.
4. Instructions to check for STK key credential link on AD DS object (does sync still have to run twice?)
5. If you get an error upon trying to register a Windows computer that the device was already enrolled, but you're unable or have already unenrolled the device, you may have a fragment of device enrollment configuration in the registry. To investigate and remove this, use the following steps:
6. On the Windows computer, open Regedit and navigate to **HKLM\Software\Microsoft\Enrollments**
7. Under this key, there are subkeys in the GUID form. Navigate to the subkey that has ~17 values in it and has "EnrollmentType" of "6" [MDM joined] or "13" (Microsoft Entra joined)
8. Modify **EnrollmentType** to **0**
9. Try the device enrollment or registration again

### Related Articles

- [Securing access to Office 365 and other apps connected to Microsoft Entra ID](/en-us/azure/active-directory/conditional-access/overview)
- [Conditional access device policies for Office 365 services](/en-us/azure/active-directory/conditional-access/overview)
- [Setting up on-premises conditional access using Microsoft Entra Device Registration](/en-us/azure/active-directory/active-directory-device-registration-on-premises-setup)
- [Connect domain-joined devices to Microsoft Entra ID for Windows 10 experiences](/en-us/azure/active-directory/devices/hybrid-azuread-join-plan)