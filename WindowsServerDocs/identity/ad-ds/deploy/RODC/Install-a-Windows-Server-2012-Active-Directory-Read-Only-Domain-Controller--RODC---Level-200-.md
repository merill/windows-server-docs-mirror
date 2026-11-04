---
layout: Conceptual
title: Install a Windows Server 2012 Active Directory Read-Only Domain Controller (RODC) (Level 200) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/rodc/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-ds
ms.update-cycle: 1095-days
description: This article explains how to create a staged RODC account and then attach a server to that account during RODC installation. This article also explains how to install an RODC without performing a staged installation.
author: robinharwood
ms.author: roharwoo
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: install-set-up-deploy
ms.custom:
- inhenkel
- sfi-image-nochange
locale: en-us
document_id: 0d142b90-d894-06fb-f2c1-df809993cf87
document_version_independent_id: 4d9dcf50-9e2e-4bfc-a5e2-a5f946456ab0
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-ds/deploy/RODC/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-ds/deploy/rodc/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-ds/deploy/RODC/Install-a-Windows-Server-2012-Active-Directory-Read-Only-Domain-Controller--RODC---Level-200-.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e96e3e9c-4b2e-8135-618c-f4bcfae43ef5
---

# Install a Windows Server 2012 Active Directory Read-Only Domain Controller (RODC) (Level 200) | Microsoft Learn

This article explains how to create a staged RODC account and then attach a server to that account during RODC installation. This article also explains how to install an RODC without performing a staged installation.

## Stage RODC Workflow

A staged read only domain controller (RODC) installation works in two discrete phases:

1. Staging an unoccupied computer account
2. Attaching an RODC to that account during promotion

The following diagram illustrates the Active Directory Domain Services Read-Only Domain Controller staging process, where you create an empty RODC computer account in the domain using the Active Directory Administrative Center (Dsac.exe).

![Diagram showing the Active Directory Domain Services Read-Only Domain Controller staging process described above.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_stagedcreation.png)

## Stage RODC Windows PowerShell

| ADDSDeployment Cmdlet | Arguments (**Bold**arguments are required.*Italicized*arguments can be specified by using Windows PowerShell or the AD DS Configuration Wizard.) |
| --- | --- |
| Add-addsreadonlydomaincontrolleraccount | -SkipPreChecks<br>***-DomainControllerAccountName***<br><br>***-DomainName***<br><br>***-SiteName***<br><br>*-AllowPasswordReplicationAccountName*<br><br>***-Credential***<br><br>*-DelegatedAdministratorAccountName*<br><br>*-DenyPasswordReplicationAccountName*<br><br>*-NoGlobalCatalog*<br><br>*-InstallDNS*<br><br>-ReplicationSourceDC |

Note

The **-credential** argument is only required if you are not already logged on as a member of the Domain Admins group.

## Attach RODC Workflow

The diagram below illustrates the Active Directory Domain Services configuration process, where you already installed the AD DS role, you staged the RODC account, and started **Promote this Server to a Domain Controller** using Server Manager to create a new RODC in an existing domain, attaching it to the staged computer account.

![Diagram showing the Active Directory Domain Services configuration process described above.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_stageddeploy_beta1.png)

## Attach RODC Windows PowerShell

| ADDSDeployment Cmdlet | Arguments (**Bold**arguments are required.*Italicized*arguments can be specified by using Windows PowerShell or the AD DS Configuration Wizard.) |
| --- | --- |
| Install-AddsDomaincontroller | -SkipPreChecks<br>***-DomainName***<br><br>*-SafeModeAdministratorPassword*<br><br>*-ApplicationPartitionsToReplicate*<br><br>*-CreateDNSDelegation*<br><br>***-Credential***<br><br>-CriticalReplicationOnly<br><br>*-DatabasePath*<br><br>*-DNSDelegationCredential*<br><br>*-InstallationMediaPath*<br><br>*-LogPath*<br><br>-Norebootoncompletion<br><br>*-ReplicationSourceDC*<br><br>*-SystemKey*<br><br>*-SYSVOLPath*<br><br>***-UseExistingAccount*** |

Note

The **-credential** argument is only required if you are not already logged on as a member of the Domain Admins group.

## Staging

![Screenshot of the Active Directory Administrative Center showing the Pre-create a Read-only domain controller account option highlighted in the Tasks pane.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_precreaterodc.png)

You perform the staging operation of a read-only domain controller computer account by opening the Active Directory Administrative Center (**Dsac.exe**). Select the name of the domain in the navigation pane. Double-click **Domain Controllers** in the management list. Select **Pre-create a Read-only domain controller account** in the tasks pane.

For more information about the Active Directory Administrative Center, see [Advanced AD DS Management Using Active Directory Administrative Center (Level 200)](../../get-started/adac/advanced-ad-ds-management-using-active-directory-administrative-center--level-200-) and review [Active Directory Administrative Center: Getting Started](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd560651%28v=ws.10%29).

If you have experience creating read-only domain controllers, you'll discover that the installation wizard has the same graphical interface as seen when using the older Active Directory Users and Computers snap-in from Windows Server 2008 and uses the same code, which includes exporting the configuration in the unattend file format used by the obsolete dcpromo.

Windows Server 2012 introduces a new ADDSDeployment cmdlet to stage RODC computer accounts, but the wizard doesn't use the cmdlet for its operation. The following sections display the equivalent cmdlet and arguments in order to make the information associated with each easier to understand.

The **Pre-create a Read-only domain controller account** link in the Active Directory Administrative Center's task pane is equivalent to the ADDSDeployment Windows PowerShell cmdlet:

```
Add-addsreadonlydomaincontrolleraccount

```

### Welcome

![Screenshot of the Welcome page of the Azure Directory Domain Services Installation Wizard showing the Use advanced mode installation option selected.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_welcomestage1.png)

The **Welcome to the Active Directory Domain Services Installation Wizard** dialog has one option named **Use advanced mode installation**. Select this option and select **Next** to show password replication policy options. Clear this option to use the default values for password replication policy options (this is discussed in further detail later in this section).

### Network Credentials

![Screenshot of the Network Credentials page of the Azure Directory Domain Services Installation Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage1creds.png)

The domain name option in the **Network Credentials** dialog displays the domain targeted by the Active Directory Administrative Center by default. Your current credentials are used by default. If they don't include membership in the Domain Admins group, select **Alternate Credentials**, and select **Set** to provide the wizard with a user name and password that is a member of Domain Admins.

The equivalent ADDSDeployment Windows PowerShell argument is:

```
-credential <pscredential>
```

Keep in mind that the staging system is a direct port from Windows Server 2008 R2 and doesn't provide the new Adprep functionality. If you plan to deploy staged RODC accounts, you must either first deploy an unstaged RODC in that domain so that the automatic rodcprep operation runs, or manually run adprep.exe /rodcprep first.

Otherwise, you'll receive error. You won't be able to install a read-only domain controller in this domain because adprep /rodcprep wasn't yet run.

![Screenshot of the warning message of the Azure Directory Domain Services Installation Wizard stating that adprep /rodcprep was not yet run.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_rodcprepnotrunerror.png)

### Specify the Computer Name

![Screenshot of the Specify the Computer Name page of the Azure Directory Domain Services Installation Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage1compname.png)

The **Specify the Computer Name** dialog requires you to enter the single-label **Computer name** of a domain controller that doesn't exist. The domain controller you configure and attach to this account later must have the same name, or the promotion operation won't detect the staged account.

The equivalent ADDSDeployment Windows PowerShell argument is:

```
-domaincontrolleraccountname <string>
```

### Select a Site

![Screenshot of the Select a Site page of the Azure Directory Domain Services Installation Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage1site.png)

The **Select a Site** dialog shows a list of Active Directory sites for the current forest. The staged read-only domain controller operation requires you to select a single site from the list. The RODC uses this information to create its NTDS Settings object in the Configuration partition and join itself to the correct site when it starts for the first time after being deployed.

The equivalent ADDSDeployment Windows PowerShell argument is:

```
-sitename <string>
```

### Additional Domain Controller Options

![Screenshot of the Specify the Domain Controller Options page of the Azure Directory Domain Services Installation Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage1dcoptions.png)

The **Additional Domain Controller Options** dialog enables you to specify that a domain controller include running as a **DNS Server** and a **Global Catalog**. Microsoft recommends that read-only domain controllers provide DNS and GC services, so both are installed by default; one intention of the RODC role is branch office scenarios where the wide area network may not be available and without those DNS and global catalog services, computers in the branch won't be able to use AD DS resources and functionality.

The **Read-only domain controller (RODC)** option is pre-selected and cannot be disabled. The equivalent ADDSDeployment Windows PowerShell arguments are:

```
-installdns <string>
-NoGlobalCatalog <{$true | $false}>

```

Note

By default, the **-NoGlobalCatalog** value is $false, which means the domain controller will be a global catalog server if the argument is not specified.

### Specify the Password Replication Policy

![Screenshot of the Specify the Password Replication policy page of the Azure Directory Domain Services Installation Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage1prp.png)

The **Specify the Password Replication Policy** dialog enables you to modify the default list of accounts that are allowed to cache their passwords on this read-only domain controller. Accounts in the list configured with **Deny** or that are not in the list (implicit) don't cache their password. Accounts that aren't allowed to cache passwords on the RODC and can't connect and authenticate to a writable domain controller can't access resources or functionality provided by Active Directory.

Important

The wizard shows this dialog only if you select the **Use Advanced Mode Installation** check box on the welcome screen. If you clear this check box, then the wizard uses following default groups and values:

- Administrators - Deny
- Server Operators - Deny
- Backup Operators - Deny
- Account Operators - Deny
- Denied RODC Password Replication Group - Deny
- Allowed RODC Password Replication Group - Allow

The equivalent ADDSDeployment Windows PowerShell arguments are:

```
-allowpasswordreplicationaccountname <string []>
-denypasswordreplicationaccountname <string []>
```

![Screenshot of the Add Groups, Users and Computers dialog box.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage1prpallow.png)

### Delegation of RODC Installation and Administration

![Screenshot of the Delegation of RODC Installation and Administration page of the Azure Directory Domain Services Installation Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage1delegateadmin.png)

The **Delegation of RODC Installation and Administration** dialog enables you to configure a user or group containing users who are allowed to attach the server to the RODC computer account. Select **Set** to browse the domain for a user or group. The user or group specified in this dialog gains local administrative permissions to the RODC. The specified user or members of the specified group can perform operations on the RODC with privileges equivalent to the computer's Administrators group. They aren't\* members of the Domain Admins or domain built-in Administrators groups.

Use this option to delegate branch office administration without granting the branch administrator membership to the Domain Admins group. Delegating RODC administration isn't required.

The equivalent ADDSDeployment Windows PowerShell argument is:

```
-delegatedadministratoraccountname <string>
```

### Summary

![Screenshot of the Summary page of the Azure Directory Domain Services Installation Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage1summary.png)

The **Summary** dialog enables you to confirm your settings. This is the last opportunity to stop the installation before the wizard creates the staged account. Select **Next** when you're ready to create the staged RODC computer account. Select **Export Settings** to save an answer file in the obsolete dcpromo unattend file format.

### Creation

![Screenshot of the progress page of the Azure Directory Domain Services Installation Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage1installprogress.png)

The **Active Directory Domain Services Installation Wizard** creates the staged read-only domain controller in Active Directory. You can't cancel this operation after it starts.

![Screenshot of the last page of the Azure Directory Domain Services Installation Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage1complete.png)

Use the following cmdlet to stage a read-only domain controller computer account using the ADDSDeployment Windows PowerShell module:

```
Add-addsreadonlydomaincontrolleraccount

```

See [Stage RODC Windows PowerShell](install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-#BKMK_StagePS) for required and optional arguments.

Because **Add-addsreadonlydomaincontrolleraccount** only has one action with two phases (prerequisite checking and installation), the following screenshots show the installation phase with the minimum required arguments.

![Screenshot of the PowerShell window showing the full Add-addsreadonlydomaincontrolleraccount cmdlet.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_psaddrodc.png)

![Screenshot of the PowerShell window showing the result of the Add-addsreadonlydomaincontrolleraccount cmdlet.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_psaddrodcvalidating.png)

The stage RODC operation creates the RODC computer account in Active Directory. The Active Directory Administrative Center shows the **Domain Controller Type** as an **Unoccupied Domain Controller Account**. This domain controller types indicates that staged RODC account is ready for a server to attach to it as a read only domain controller.

![Screenshot of the Active Directory Administrative Center showing Unoccupied Domain Controller Account highlighted.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_unoccupied.png)

Important

The Active Directory Administrative Center is no longer required to attach a server to a read-only domain controller computer account. Use Server Manager and the Active Directory Domain Services Configuration Wizard or the ADDSDeployment Windows PowerShell module cmdlet **Install-AddsDomainController** to attach a new RODC to its staged account. The steps are similar to adding a new writable domain controller to an existing domain, with the exception that the staged RODC computer account contains configuration options decided at the time you staged the RODC computer account.

## Attaching

### Deployment Configuration

![Screenshot of the Deployment Configuration page of the Active Directory Domain Services Configuration Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_rodcdeployconfig.png)

Server Manager begins every domain controller promotion with the **Deployment Configuration** page. The remaining options and required fields change on this page and subsequent pages, depending on which deployment operation you select.

To add a read-only domain controller to an existing domain, select **Add a domain controller to an existing domain** and select the **Select** button to **Specify the domain information for this domain**. Server Manager automatically prompts you for valid credentials, or you can select **Change**.

Attaching an RODC requires membership in the Domain Admins groups in Windows Server 2012. The Active Directory Domain Services Configuration Wizard prompts you later if your current credentials don't have adequate permissions or group memberships.

The **Deployment Configuration** ADDSDeployment Windows PowerShell cmdlet and arguments are:

```
Install-AddsDomainController
-domainname <string>
-credential <pscredential>
```

### Domain Controller Options

![Screenshot of the Domain Controller Options page of the Active Directory Domain Services Configuration Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage2dcoptions.png)

The **Domain Controller Options** page shows the domain controller options for the new domain controller. When this page loads, the Active Directory Domain Services Configuration Wizard sends an LDAP query to an existing domain controller to check for unoccupied accounts. If the query finds an unoccupied domain controller computer account that shares the same name as the current computer, then the wizard displays an informational message at the top of the page that reads **A Pre-created RODC account that matches the name of the target server exists in the directory. Choose whether to use this existing RODC account or reinstall this domain controller**. The wizard uses the **Use existing RODC account** as the default configuration.

Important

You can use the **Reinstall this domain controller** option when a domain controller has suffered a physical problem and cannot return to functionality. This saves time when configuring the replacement domain controller, by leaving the domain controller computer account and object metadata in Active Directory. Install the new computer with the *same name*, and promote it as a domain controller in the domain. The **Reinstall this domain controller** option is unavailable if you removed the domain controller object's metadata from Active Directory (metadata cleanup).

You can't configure domain controller options when you're attaching a server to an RODC computer account. You configure domain controller options when you create the staged RODC computer account.

The specified **Directory Services Restore Mode Password** must adhere to the password policy applied to the server. Always choose a strong, complex password or preferably, a passphrase.

The **Domain Controller Options** ADDSDeployment Windows PowerShell arguments are:

```
-UseExistingAccount <{$true | $false}>
-SafeModeAdministratorPassword <secure string>
```

Important

The site name must already exist when provided as an argument to **-sitename**. The **install-AddsDomainController** cmdlet does not create site names. You can use cmdlet **new-adreplicationsite** to create new sites.

The **Install-ADDSDomainController** arguments follow the same defaults as Server Manager if not specified.

The **SafeModeAdministratorPassword** argument's operation is special:

- If *not specified* as an argument, the cmdlet prompts you to enter and confirm a masked password. This is the preferred usage when running the cmdlet interactively.

    For example, to create a new RODC in the corp.contoso.com and be prompted to enter and confirm a masked password:

    ```
    Install-ADDSDomainController -DomainName corp.contoso.com -credential (get-credential)
    ```
- If specified *with a value*, the value must be a secure string. This isn't the preferred usage when running the cmdlet interactively.

For example, you can manually prompt for a password by using the **Read-Host** cmdlet to prompt the user for a secure string:

```
-safemodeadministratorpassword (read-host -prompt Password: -assecurestring)

```

Warning

As the previous option does not confirm the password, use extreme caution: the password is not visible.

You can also provide a secure string as a converted clear-text variable, although this is highly discouraged.

```
-safemodeadministratorpassword (convertto-securestring Password1 -asplaintext -force)
```

Finally, you could store the obfuscated password in a file, and then reuse it later, without the clear text password ever appearing. For example:

```
$file = c:\pw.txt
$pw = read-host -prompt Password: -assecurestring
$pw | ConvertFrom-SecureString | Set-Content $file

-safemodeadministratorpassword (Get-Content $File | ConvertTo-SecureString)

```

Warning

Providing or storing a clear or obfuscated text password is not recommended. Anyone running this command in a script or looking over your shoulder knows the DSRM password of that domain controller. Anyone with access to the file could reverse that obfuscated password. With that knowledge, they can logon to a DC started in DSRM and eventually impersonate the domain controller itself, elevating their privileges to the highest level in an AD forest. An additional set of steps using **System.Security.Cryptography** to encrypt the text file data is advisable but out of scope. The best practice is to totally avoid password storage.

### Additional Options

![Screenshot of the Additional Options page of the Active Directory Domain Services Configuration Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage2additionaloptions.png)

The **Additional Options** page provides configuration options to name a domain controller as the replication source, or you can use any domain controller as the replication source.

You can also choose to install the domain controller using backed up media using the Install from media (IFM) option. The **Install from media** checkbox provides a browse option once selected and you must select **Verify** to ensure the provided path is valid media.

Guidelines for the IFM source:

- Media used by the IFM option is created with Windows Server Backup or Ntdsutil.exe from another existing Windows Server Domain Controller with the same operating system version only. For example, you can't use a Windows Server 2008 R2 or previous operating system to create media for a Windows Server 2012 domain controller.
- The IFM source data should be from a writable Domain Controller. While a source from RODC will technically work to create a new RODC, there are false positive replication warnings that the IFM source RODC isn't replicating.

For more information about changes in IFM, see [Ntdsutil.exe Install from Media Changes](../simplified-administration-appendix#BKMK_IFM). If using media protected with a SYSKEY, Server Manager prompts for the image's password during verification.

![Screenshot of the Command Prompt window showing the results of running ntdsutil.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stagedifm.png)

The **Additional Options** ADDSDeployment cmdlet arguments are:

```
-replicationsourcedc <string>
-installationmediapath <string>
-systemkey <secure string>
```

### Paths

![Screenshot of the Paths page of the Active Directory Domain Services Configuration Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage2paths.png)

The **Paths** page enables you to override the default folder locations of the AD DS database, the database transaction logs, and the SYSVOL share. The default locations are always in subdirectories of %systemroot%. The **Paths** ADDSDeployment cmdlet arguments are:

```
-databasepath <string>
-logpath <string>
-sysvolpath <string>
```

### Review Options and View Script

![Screenshot of the Review Options page of the Active Directory Domain Services Configuration Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage2reviewoptions.png)

The **Review Options** page enables you to validate your settings and ensure that they meet your requirements before you start the installation. This isn't the last opportunity to stop the installation using Server Manager. This page simply enables you to review and confirm your settings before continuing the configuration. The **Review Options** page in Server Manager also offers an optional **View Script** button to create a Unicode text file that contains the current ADDSDeployment configuration as a single Windows PowerShell script. This enables you to use the Server Manager graphical interface as a Windows PowerShell deployment studio. Use the Active Directory Domain Services Configuration Wizard to configure options, export the configuration, and then cancel the wizard. This process creates a valid and syntactically correct sample for further modification or direct use. For example:

```
#
# Windows PowerShell Script for AD DS Deployment
#

Import-Module ADDSDeployment
Install-ADDSDomainController `
-Credential (Get-Credential) `
-CriticalReplicationOnly:$false `
-DatabasePath C:\Windows\NTDS `
-DomainName corp.contoso.com `
-LogPath C:\Windows\NTDS `
-SYSVOLPath C:\Windows\SYSVOL `
-UseExistingAccount:$true `
-Norebootoncompletion:$false
-Force:$true

```

Note

Server Manager generally fills in all arguments with values when promoting and does not rely on defaults (as they may change between future versions of Windows or service packs). The one exception to this is the **-safemodeadministratorpassword** argument. To force a confirmation prompt omit the value when running cmdlet interactively

Use the optional **Whatif** argument with the **Install-ADDSDomainController** cmdlet to review configuration information. This enables you to see the explicit and implicit values of the arguments for a cmdlet.

![Screenshot of the PowerShell window showing the results of the Install-ADDSDomainController cmdlet.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage2whatif.png)

### Prerequisites Check

![Screenshot of the Prerequisites Check page of the Active Directory Domain Services Configuration Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage2prereqcheck.png)

The **Prerequisites Check** is a new feature in AD DS domain configuration. This new phase validates that the server configuration is capable of supporting a new AD DS forest.

When installing a new forest root domain, the Server Manager Active Directory Domain Services Configuration Wizard invokes a series of serialized modular tests. These tests alert you with suggested repair options. You can run the tests as many times as required. The domain controller installation process can't continue until all prerequisite tests pass.

The **Prerequisites Check** also surfaces relevant information such as security changes that affect older operating systems. For more information about the prerequisite checks, see [Prerequisite Checking](../../manage/ad-ds-simplified-administration#BKMK_PrerequisiteChecking).

You can't bypass the **Prerequisite Check** when using Server Manager, but you can skip the process when using the AD DS Deployment cmdlet using the following argument:

```
-skipprechecks

```

Warning

Microsoft discourages skipping the prerequisite check as it can lead to a partial domain controller promotion or damaged AD DS forest.

Select **Install** to begin the domain controller promotion process. This is last opportunity to cancel the installation. You can't cancel the promotion process once it begins. The computer will reboot automatically at the end of promotion, regardless of the promotion results.

### Installation

![Screenshot of the Installation page of the Active Directory Domain Services Configuration Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_stage2installation.png)

When the Installation page displays, the domain controller configuration begins and can't be halted or canceled. Detailed operations display on this page and are written to logs:

- %systemroot%\debug\dcpromo.log
- %systemroot%\debug\dcpromoui.log

To install a new Active Directory forest using the ADDSDeployment module, use the following cmdlet:

```
Install-addsdomaincontroller

```

See [Attach RODC Windows PowerShell](install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-#BKMK_AttachPS) for required and optional arguments.

The **Install-addsdomaincontroller** cmdlet only has two phases (prerequisite checking and installation). The two figures below show the installation phase with the minimum required arguments of **-domainname**, **-useexistingaccount**, and **-credential**. Note how, just like Server Manager, **Install-ADDSDomainController** reminds you that promotion will reboot the server automatically:

![Screenshot of the PowerShell window showing the result of the Install-addsdomaincontroller cmdlet.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_psstage2.png)

![Screenshot of the PowerShell window showing the progress of the validation and installation.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_psstage2complete.png)

To accept the reboot prompt automatically, use the **-force** or **-confirm:$false** arguments with any ADDSDeployment Windows PowerShell cmdlet. To prevent the server from automatically rebooting at the end of promotion, use the **-norebootoncompletion** argument.

Warning

Overriding the reboot is discouraged. The domain controller must reboot to function correctly.

### Results

![Screenshot of the Results page of the Active Directory Domain Services Configuration Wizard.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_forestsignoff.png)

The **Results** page shows the success or failure of the promotion and any important administrative information. The domain controller will automatically reboot after 10 seconds.

## RODC without Staging Workflow

The following diagram illustrates the Active Directory Domain Services configuration process, when you previously installed the AD DS role and you have started the Active Directory Domain Services Configuration Wizard using Server Manager to create a new nonstaged read-only domain controller in an existing Windows Server 2012 domain.

![Diagram showing the Active Directory Domain Services Read-Only Domain Controller process, as described above, without the staging workflow.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_rodcdeploy.png)

## RODC without Staging Windows PowerShell

| ADDSDeployment Cmdlet | Arguments (**Bold**arguments are required.*Italicized*arguments can be specified by using Windows PowerShell or the AD DS Configuration Wizard.) |
| --- | --- |
| Install-AddsDomainController | -SkipPreChecks<br>***-DomainName***<br><br>*-SafeModeAdministratorPassword*<br><br>***-SiteName***<br><br>*-ApplicationPartitionsToReplicate*<br><br>*-CreateDNSDelegation*<br><br>***-Credential***<br><br>*-CriticalReplicationOnly*<br><br>*-DatabasePath*<br><br>*-DNSDelegationCredential*<br><br>-DNSOnNetwork<br><br>*-InstallationMediaPath*<br><br>*-InstallDNS*<br><br>*-LogPath*<br><br>-MoveInfrastructureOperationMasterRoleIfNecessary<br><br>*-NoGlobalCatalog*<br><br>-Norebootoncompletion<br><br>*-ReplicationSourceDC*<br><br>-SkipAutoConfigureDNS<br><br>*-SystemKey*<br><br>*-SYSVOLPath*<br><br>*-AllowPasswordReplicationAccountName*<br><br>*-DelegatedAdministratorAccountName*<br><br>*-DenyPasswordReplicationAccountName*<br><br>***-ReadOnlyReplica*** |

Note

The **-credential** argument is only required if you are not already logged on as a member of the Domain Admins group.

## RODC without Staging Deployment

### Deployment Configuration

![Screenshot of the Deployment Configuration page of the Active Directory Domain Services Configuration Wizard when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_rodcdeployconfig.png)

Server Manager begins every domain controller promotion with the **Deployment Configuration** page. The remaining options and required fields change on this page and subsequent pages, depending on which deployment operation you select.

To add an unstaged read-only domain controller to an existing Windows Server 2012 domain, select **Add a domain controller to an existing domain** and select the **Select** button to **Specify the domain information for this domain**. Server Manager automatically prompts you for valid credentials, or you can select **Change**.

Attaching an RODC requires membership in the Domain Admins groups in Windows Server 2012. The Active Directory Domain Services Configuration Wizard prompts you later if your current credentials don't have adequate permissions or group memberships.

The **Deployment Configuration** ADDSDeployment Windows PowerShell cmdlet and arguments are:

```
Install-AddsDomainController
-domainname <string>
-credential <pscredential>
```

### Domain Controller Options

![Screenshot of the Domain Controller Options page of the Active Directory Domain Services Configuration Wizard when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_rodcdcoptions.png)

The **Domain Controller Options** page specifies the domain controller capabilities for the new domain controller. The configurable domain controller capabilities are **DNS server**, **Global Catalog**, and **Read-only domain controller**. Microsoft recommends that all domain controllers provide DNS and GC services for high availability in distributed environments. GC is always selected by default and DNS server is selected by default if the current domain hosts DNS already on its DCs based on Start of Authority query.

The **Domain Controller Options** page also enables you to choose the appropriate Active Directory logical **site name** from the forest configuration. By default, it selects the site with the most correct subnet. If there's only one site, it selects that site automatically.

Important

If the server does not belong to an Active Directory subnet and there is more than one Active Directory site, nothing is selected and the **Next** button is unavailable until you choose a site from the list.

The specified **Directory Services Restore Mode Password** must adhere to the password policy applied to the server. Always choose a strong, complex password or preferably, a passphrase.The **Domain Controller Options** ADDSDeployment Windows PowerShell arguments are:

```
-UseExistingAccount <{$true | $false}>
-SafeModeAdministratorPassword <secure string>
```

Important

The site name must already exist when provided as an argument to **-sitename**. The **install-AddsDomainController** cmdlet does not create site names. You can use cmdlet **new-adreplicationsite** to create new sites.

The **Install-ADDSDomainController** arguments follow the same defaults as Server Manager if not specified.

The **SafeModeAdministratorPassword** argument's operation is special:

- If *not specified* as an argument, the cmdlet prompts you to enter and confirm a masked password. This is the preferred usage when running the cmdlet interactively.

    For example, to create a new RODC in the corp.contoso.com and be prompted to enter and confirm a masked password:

    ```
    Install-ADDSDomainController -DomainName corp.contoso.com -credential (get-credential)
    ```
- If specified *with a value*, the value must be a secure string. This isn't the preferred usage when running the cmdlet interactively.

For example, you can manually prompt for a password by using the **Read-Host** cmdlet to prompt the user for a secure string:

```
-safemodeadministratorpassword (read-host -prompt Password: -assecurestring)

```

Warning

As the previous option does not confirm the password, use extreme caution: the password is not visible.

You can also provide a secure string as a converted clear-text variable, although this is highly discouraged.

```
-safemodeadministratorpassword (convertto-securestring Password1 -asplaintext -force)
```

Finally, you could store the obfuscated password in a file, and then reuse it later, without the clear text password ever appearing. For example:

```
$file = c:\pw.txt
$pw = read-host -prompt Password: -assecurestring
$pw | ConvertFrom-SecureString | Set-Content $file

-safemodeadministratorpassword (Get-Content $File | ConvertTo-SecureString)

```

Warning

Providing or storing a clear or obfuscated text password is not recommended. Anyone running this command in a script or looking over your shoulder knows the DSRM password of that domain controller. Anyone with access to the file could reverse that obfuscated password. With that knowledge, they can logon to a DC started in DSRM and eventually impersonate the domain controller itself, elevating their privileges to the highest level in an AD forest. An additional set of steps using **System.Security.Cryptography** to encrypt the text file data is advisable but out of scope. The best practice is to totally avoid password storage.

### RODC Options

![Screenshot of the RODC Options page of the Active Directory Domain Services Configuration Wizard when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_rodcoptions.png)

The **RODC Options** page enables you to modify the settings:

- Delegated Administrator Account
- Accounts that are allowed to replicate passwords to the RODC
- Accounts that are denied from replicating passwords to the RODC

Delegated administrator accounts gain local administrative permissions to the RODC. These users can operate with privileges equivalent to the local computer's Administrators group. They aren't members of the Domain Admins or the domain built-in Administrators groups. This option is useful for delegating branch office administration without giving out domain administrative permissions. Configuring delegation of administration isn't required.

The equivalent ADDSDeployment Windows PowerShell argument is:

```
-delegatedadministratoraccountname <string>
```

Accounts that aren't allowed to cache passwords on the RODC and can't connect and authenticate to a writable domain controller can't access resources or functionality provided by Active Directory.

Important

If not modified, the default groups and settings are used:

- Administrators - Deny
- Server Operators - Deny
- Backup Operators - Deny
- Account Operators - Deny
- Denied RODC Password Replication Group - Deny
- Allowed RODC Password Replication Group - Allow

The equivalent ADDSDeployment Windows PowerShell arguments are:

```
-allowpasswordreplicationaccountname <string []>
-denypasswordreplicationaccountname <string []>
```

![Screenshot of the Select User, Computer, Service Account dialog box.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_selectdeladmin.png)

### Additional Options

![Screenshot of the Additional Options page of the Active Directory Domain Services Configuration Wizard when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_rodcadditionaloptions.png)

The **Additional Options** page provides configuration options to name a domain controller as the replication source, or you can use any domain controller as the replication source.

You can also choose to install the domain controller using backed up media using the Install from media (IFM) option. The **Install from media** checkbox provides a browse option once selected and you must select **Verify** to ensure the provided path is valid media.

Guidelines for the IFM source:

- Media used by the IFM option is created with Windows Server Backup or Ntdsutil.exe from another existing Windows Server Domain Controller with the same operating system version only. For example, you can't use a Windows Server 2008 R2 or previous operating system to create media for a Windows Server 2012 domain controller.
- The IFM source data should be from a writable Domain Controller. While a source from RODC will technically work to create a new RODC, there are false positive replication warnings that the IFM source RODC isn't replicating.

For more information about changes in IFM, see [Ntdsutil.exe Install from Media Changes](../simplified-administration-appendix#BKMK_IFM). If using media protected with a SYSKEY, Server Manager prompts for the image's password during verification.

![Screenshot of the Command Prompt window showing the results of running ntdsutil when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_psifm.png)

The Additional Options ADDSDeployment cmdlet arguments are:

```
-replicationsourcedc <string>
-installationmediapath <string>
-systemkey <secure string>
```

### Paths

![Screenshot of the Paths page of the Active Directory Domain Services Configuration Wizard when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_rodcpaths.png)

The **Paths** page enables you to override the default folder locations of the AD DS database, the database transaction logs, and the SYSVOL share. The default locations are always in subdirectories of %systemroot%. The **Paths** ADDSDeployment cmdlet arguments are:

```
-databasepath <string>
-logpath <string>
-sysvolpath <string>
```

### Preparation Options

![Screenshot of the Preparation Options page of the Active Directory Domain Services Configuration Wizard when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_rodcprepoptions.png)

The **Preparation Options** page alerts you that the AD DS configuration includes extending the Schema (forestprep) and updating the domain (domainprep). You only see this page when the forest or domain hasn't been prepared by previous Windows Server 2012 domain controller installation or from manually running Adprep.exe. For example, the Active Directory Domain Services Configuration Wizard suppresses this page if you add a new replica domain controller to an existing Windows Server 2012 forest root domain.

Extending the Schema and updating the domain don't occur when you select **Next**. These events occur only during the installation phase. This page simply brings awareness about the events that will occur later in the installation.

This page also validates that the current user credentials are members of the Schema Admin and Enterprise Admins groups, as you need membership in these groups to extend the schema or prepare a domain. Select **Change** to provide the adequate user credentials if the page informs you that the current credentials don't provide sufficient permissions.

The Additional Options ADDSDeployment cmdlet argument is:

```
-adprepcredential <pscredential>
```

Important

As with previous versions of Windows Server, Windows Server 2012's automated domain preparation does not run GPPREP. Run **adprep.exe /gpprep** manually for all domains that were not previously prepared for Windows Server 2003, Windows Server 2008, or Windows Server 2008 R2. You should run GPPrep only once in the history of a domain, not with every upgrade. Adprep.exe does not run /gpprep automatically because its operation can cause all files and folders in the SYSVOL folder to re-replicate on all domain controllers.

Automatic RODCPrep runs when you promote the first un-staged RODC in a domain. It does not occur when you promote the first writeable Windows Server 2012 domain controller. You can also still manually run **adprep.exe /rodcprep** if you plan to deploy read-only domain controllers.

### Review Options and View Script

![Screenshot of the Review Options page of the Active Directory Domain Services Configuration Wizard when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_rodcreviewoptions.png)

The **Review Options** page enables you to validate your settings and ensure that they meet your requirements before you start the installation. This isn't the last opportunity to stop the installation using Server Manager. This page simply enables you to review and confirm your settings before continuing the configuration.

The **Review Options** page in Server Manager also offers an optional **View Script** button to create a Unicode text file that contains the current ADDSDeployment configuration as a single Windows PowerShell script. This enables you to use the Server Manager graphical interface as a Windows PowerShell deployment studio. Use the Active Directory Domain Services Configuration Wizard to configure options, export the configuration, and then cancel the wizard. This process creates a valid and syntactically correct sample for further modification or direct use. For example:

```
#
# Windows PowerShell Script for AD DS Deployment
#

Import-Module ADDSDeployment
Install-ADDSDomainController `
-AllowPasswordReplicationAccountName @(CORP\Allowed RODC Password Replication Group, CORP\Chicago RODC Admins, CORP\Chicago RODC Users and Computers) `
-Credential (Get-Credential) `
-CriticalReplicationOnly:$false `
-DatabasePath C:\Windows\NTDS `
-DelegatedAdministratorAccountName CORP\Chicago RODC Admins `
-DenyPasswordReplicationAccountName @(BUILTIN\Administrators, BUILTIN\Server Operators, BUILTIN\Backup Operators, BUILTIN\Account Operators, CORP\Denied RODC Password Replication Group) `
-DomainName corp.contoso.com `
-InstallDNS:$true `
-LogPath C:\Windows\NTDS `
-ReadOnlyReplica:$true `
-SiteName Default-First-Site-Name `
-SYSVOLPath C:\Windows\SYSVOL
-Force:$true

```

Note

Server Manager generally fills in all arguments with values when promoting and does not rely on defaults (as they may change between future versions of Windows or service packs). The one exception to this is the **-safemodeadministratorpassword** argument. To force a confirmation prompt, omit the value when running cmdlet interactively.

Use the optional Whatif argument with the Install-ADDSDomainController cmdlet to review configuration information. This enables you to see the explicit and implicit values of the arguments for a cmdlet.

![Screenshot of the PowerShell window showing the results of the Install-ADDSDomainController cmdlet when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_rodcwhatif.png)

### Prerequisites Check

![Screenshot of the Prerequisites Check page of the Active Directory Domain Services Configuration Wizard when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_rodcprereqcheck.png)

The **Prerequisites Check** is a new feature in AD DS domain configuration. This new phase validates that the server configuration is capable of supporting a new AD DS forest.

When installing a new forest root domain, the Server Manager Active Directory Domain Services Configuration Wizard invokes a series of serialized modular tests. These tests alert you with suggested repair options. You can run the tests as many times as required. The domain controller process can't continue until all prerequisite tests pass.

The **Prerequisites Check** also surfaces relevant information such as security changes that affect older operating systems.

You can't bypass the **Prerequisite Check** when using Server Manager, but you can skip the process when using the AD DS Deployment cmdlet using the following argument:

```
-skipprechecks

```

Select **Install** to begin the domain controller promotion process. This is last opportunity to cancel the installation. You can't cancel the promotion process once it begins. The computer will reboot automatically at the end of promotion, regardless of the promotion results.

### Installation

![Screenshot of the Installation page of the Active Directory Domain Services Configuration Wizard when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_rodcinstallation.png)

When the **Installation** page displays, the domain controller configuration begins and can't be halted or canceled. Detailed operations display on this page and are written to logs:

- %systemroot%\debug\dcpromo.log
- %systemroot%\debug\dcpromoui.log

To install a new Active Directory forest using the ADDSDeployment module, use the following cmdlet:

```
Install-addsdomaincontroller

```

See the **ADDSDeployment Cmdlet** table at the beginning of this section for required and optional arguments.

The **Install-addsdomaincontroller** cmdlet only has two phases (prerequisite checking and installation). The two figures below show the installation phase with the minimum required arguments of **-domainname**, **-readonlyreplica**, **-sitename**, and **-credential**. Note how, just like Server Manager, **Install-ADDSDomainController** reminds you that promotion will reboot the server automatically:

![Screenshot of the PowerShell window showing the result of the Install-addsdomaincontroller cmdlet when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_psinstallrodc.png)

![Screenshot of the PowerShell window showing the progress of the validation and installation when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_psinstallrodcprogress.png)

To accept the reboot prompt automatically, use the **-force** or **-confirm:$false** arguments with any ADDSDeployment Windows PowerShell cmdlet. To prevent the server from automatically rebooting at the end of promotion, use the **-norebootoncompletion** argument.

Warning

Overriding the reboot is not recommended. The domain controller must reboot to function correctly. If you log off the domain controller, you cannot log back on interactively until you restart it.

### Results

![Screenshot of the Results page of the Active Directory Domain Services Configuration Wizard when there is no staging deployment.](media/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-/adds_smi_tr_rodcsignoff.png)

The **Results** page shows the success or failure of the promotion and any important administrative information. The domain controller will automatically reboot after 10 seconds.