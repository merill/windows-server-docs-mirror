---
layout: Conceptual
title: Advanced customization of AD FS sign-in pages | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/operations/advanced-customization-of-ad-fs-sign-in-pages
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.service: windows-server
ms.subservice: ad-fs
ms.update-cycle: 1095-days
ms.author: justinha
author: Justinha
description: Learn how to make advanced customizations of the Active Directory Federation Services (ADFS) sign-in pages in Windows Server.
ms.date: 2025-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 110e65f0-76bd-55d7-51b3-58149c8e0eb7
document_version_independent_id: 1184ab13-6803-236d-cc17-b08896cf1695
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/identity/ad-fs/operations/Advanced-Customization-of-AD-FS-Sign-in-Pages.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: identity/ad-fs/operations/advanced-customization-of-ad-fs-sign-in-pages
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/identity/ad-fs/operations/Advanced-Customization-of-AD-FS-Sign-in-Pages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 571fa04f-7d4c-06c6-a45d-6fa970b2f830
---

# Advanced customization of AD FS sign-in pages | Microsoft Learn

Active Directory Federation Services (AD FS) in Windows Server 2012 R2 and later supports customization of the user sign-in experience. For most scenarios, you can use the built-in Windows PowerShell cmdlets to configure the AD FS sign-in pages. The recommended approach is to use the built-in Windows PowerShell commands for customization whenever possible. For more information, see [AD-FS user sign-in customization](ad-fs-user-sign-in-customization).

Sometimes, you might need to provide a sign-in experience that can't be enabled by using the PowerShell commands that come with AD FS. You can configure the sign-in experience by adding custom code to the **onload.js** file provided with AD FS. The file code is executed on all AD FS pages.

## Considerations

Before you start customizing AD FS sign-in pages, review the following important considerations.

Important

Any customization change that impacts redirect flows or modifies protocol parameters used by AD FS isn't supported.

- The onload.js file is executed on all AD FS pages, including form-based sign-in pages, home realm discovery pages, and so on. Always ensure your custom code executes only as intended and not unexpectedly.
- AD FS comes with a built-in web theme called **default**. You can't modify the onload.js content that creates the default web theme. To update the onload.js file, create and use a custom web theme for AD FS sign-in pages. For more information, see [AD-FS user sign-in customization](ad-fs-user-sign-in-customization).
- The original onload.js file for the default web theme also contains code to handle page rendering for different form factors. The recommended customization approach is to append your custom logic code to the existing onload.js file. Don't modify the original onload.js file content.
- When you reference HTML elements, always check for the existence of the element prior to acting on the element. This step provides robustness and ensures custom logic isn't executed on pages that don't contain this element. To identify existing HTML elements, view the HTML source on the AD FS sign-in pages.
- It's recommended to validate your customizations in an alternate environment and run tests prior to moving your customizations onto production AD FS servers. This step reduces the chances of exposing end users to customizations prior to validation.

## Customization steps

The following sections provide the steps to customize the onload.js file content for AD FS sign-in pages.

### Create custom web theme

To add your custom logic to the onload.js file, the first step is to create a custom web theme. A quick method is to export the Default web theme and then use the original code as the basis for your customizations.

Run the following cmdlet to create a custom web theme by duplicating the default web theme:

```powershell
New-AdfsWebTheme –Name custom –SourceName default
```

### Generate onload.js file

The next step is to export your custom web theme so you have an onload.js file that you can update.

Run the following cmdlet to export your custom web theme and generate an onload.js file:

```powershell
Export-AdfsWebTheme –Name default –DirectoryPath c:\theme
```

The onload.js file is placed in the **script** folder in the directory specified in the cmdlet. In the example, the specified folder is `c:\theme`.

### Add customizations

Now you're ready to modify the onload.js content and add custom logic code for your scenarios. As mentioned, be sure to add your custom code to the end of the onload.js file.

See the following Examples section for code snippets that demonstrate common customizations.

### Change target onload.js file

After you add your customizations, you need to update the AD FS web theme to use your onload.js file rather than the original onload.js file.

Run the following cmdlet to set your onload.js file as the target for web theme definitions:

- **For AD FS on Windows Server 2016 and later**:

    ```powershell
    Set-AdfsWebTheme -TargetName custom -OnLoadScriptPath "c:\theme\script\onload.js"
    ```
- **For AD FS on Windows Server 2012 R2**:

    ```powershell
    Set-AdfsWebTheme -TargetName custom -AdditionalFileResource @{Uri='/adfs/portal/script/onload.js';path="c:\theme\script\onload.js"}
    ```

### Apply customizations to AD FS

The last step is to apply your customizations to the AD FS sign-in pages.

Run the following cmdlet to update AD FS with your customizations:

```powershell
Set-AdfsWebConfig -ActiveThemeName custom
```

## Examples

The following examples provide custom code that you can add to the onload.js file to configure AD FS sign-in pages.

Note

Always append custom code to the end of the onload.js file.

### Change sign-in page title string

The AD FS form-based sign-in page displays a title above the user input fields. The default title value is "Sign in with your organizational account."

Replace the default string value with a custom string by adding the following code to the onload.js file. In the code, set the value of the `loginMessage.innerHTML` parameter to the custom string to use for the title.

```javascript
// Sample code to change page title string

// Check if loginMessage element is present
var loginMessage = document.getElementById('loginMessage');
if (loginMessage)
{
       // If loginMessage element is present, change title to custom value
       loginMessage.innerHTML = 'Custom title string value';
}
```

### Accept SAM account name sign in

The AD FS form-based sign-in page supports two sign in methods by default:

- `userPrincipalName": A user principal name (UPN), such as `user@contoso.com`.
- `samAccountName`: A domain qualified Security Account Manager (SAM) account name, such as `contoso\user` or `contoso.com\user`.

Consider a scenario where all users are in the same domain and the users know only their SAM account name. You can update the sign-page to allow the users to sign in by using their SAM account name only.

Enable sign in from SAM accounts only by adding the following code to the onload.js file. In the code, set the value of the `userNameValue` parameter to the desired domain.

```javascript
// Sample code to enable user login from SAM account name only

if (typeof Login != 'undefined'){

    Login.submitLoginRequest = function () {
    
    var u = new InputUtil();
    var e = new LoginErrors();
    var userName = document.getElementById(Login.userNameInput);
    var password = document.getElementById(Login.passwordInput);

    // Update login method with desired domain value
    if (userName.value && !userName.value.match('[@\\\\]'))
    {
        var userNameValue = 'contoso.com\\' + userName.value;
        document.forms['loginForm'].UserName.value = userNameValue;
    }
    
    // Check for user name errors
    if (!userName.value) {
       u.setError(userName, e.userNameFormatError);
       return false;
    }

    // Check for password errors
    if (!password.value)
    {
        u.setError(password, e.passwordEmpty);
        return false;
    }

    // Update the form page 
    document.forms['loginForm'].submit();
    return false;
    };

}
```

## Related links

- [AD FS user sign-in customization](ad-fs-user-sign-in-customization)