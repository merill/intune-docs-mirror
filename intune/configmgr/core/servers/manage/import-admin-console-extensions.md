---
layout: Conceptual
title: Import admin console extensions for Configuration Manager - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/import-admin-console-extensions
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Learn about importing Configuration Manager console extensions
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 604c12a5-cd22-e792-5a56-9d6286464b5c
document_version_independent_id: 604c12a5-cd22-e792-5a56-9d6286464b5c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/import-admin-console-extensions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/import-admin-console-extensions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/import-admin-console-extensions.md
cmProducts: []
platformId: 7db4d4c7-b072-2b00-8fd7-3fc56047bea6
---

# Import admin console extensions for Configuration Manager - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Starting in Configuration Manager 2103, you can import console extensions to be used in your environment. These extensions show up under the **Console extensions** node. Importing and just having extensions in the console doesn't make them immediately available. An administrator still has to approve the extension for the site and enable notifications. Then console users can install the extension to their local console. For more information about managing and installing console extensions, see [Manage Configuration Manager console extensions](admin-console-extensions).

Based on the version of Configuration Manager you're running, different import options are available. Initially, only signed extensions could be imported through the administration service. Support for importing unsigned extensions was added later. Then a wizard that could import both signed and unsigned extensions for you without having to run a script was introduced in version 2111.

| Configuration Manager version | 2103 | 2107 | 2111 or later |
| --- | --- | --- | --- |
| Import a signed extension | Yes | Yes | Yes |
| Import an unsigned extension | No | Yes, when you allow unsigned | Yes, when you allow unsigned |
| Import from the [administration service](../../../develop/adminservice/usage) with a PowerShell script | Yes, signed extensions only | Yes | Yes |
| Import from the **Import Console Extension** wizard | No | No | Yes |

## How to import console extensions

To import console extensions, you'll follow four basic steps. Exactly how you can import will be determined by the version of Configuration Manager you're using and if the extension is signed or not. To import and install a hierarchy approved console extension, the high-level steps are:

1. Determine if you need to allow unsigned hierarchy approved console extensions (version 2107 and later).
2. Import the console extension using one of the following methods:
    - Import a signed console extension with a script (version 2103 and later)
    - Import an unsigned console extension with a script (version 2107 and later)
    - Use the **Import Console Extension** wizard (version 2111 and later)
3. Test the extension in a local console.
4. Enable notifications to allow console users to install the console extension.

## Allow unsigned console extensions for the hierarchy

(*Applies to Configuration Manager version 2107 or later*)

Starting in Configuration Manager version 2107, you can choose to allow unsigned hierarchy approved console extensions. It's a best practice to always used signed extensions to minimize security risks and to confirm the authenticity of a console extension. However, in some cases you may need to allow unsigned console extensions due to an unsigned internally developed extension, or for testing your own custom extension in a lab. To allow [import](import-admin-console-extensions#how-to-import-console-extensions) and install of unsigned hierarchy approved console extensions, you'll enable a hierarchy setting.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select **Sites**.
2. Select **Hierarchy Settings** from the ribbon.
3. On the **General** tab, enable the **Hierarchy approved console extensions can be unsigned** option.
4. Select **Ok** when done to close the **Hierarchy Settings Properties**.

Note

Currently, when an unsigned extension isn't enabled for user notification, in the **Console Extensions** node, the **Required** column remains blank instead of populating a value of **No**. 

## Import a signed console extension with a script

(*Applies to Configuration Manager version 2103 or later*)

When you have an extension packaged in a signed `.cab` file, you can import it into Configuration Manager. You'll do this by posting it through the [administration service](../../../develop/adminservice/usage) using a PowerShell script. Once the extension is inserted into the site, you can approve and install it locally from the **Console Extensions** node. To import, run the following PowerShell script after editing the `$adminServiceProvider` and `$cabFilePath`:

- `$adminServiceProvider` - The top-level SMSProvider server where the administration service is installed
- `$cabFilePath` - Path to the extension's signed `.cab` file

```powershell
$adminServiceProvider = "SMSProviderServer.contoso.com"
$cabFilePath = "C:\Testing\MyExtension.cab"
$adminServiceURL = "https://$adminServiceProvider/AdminService/v1/ConsoleExtensionMetadata/AdminService.UploadExtension"
$cabFileName = (Get-Item -Path $cabFilePath).Name
$Data = Get-Content $cabFilePath
$Bytes = [System.IO.File]::ReadAllBytes($cabFilePath)
$base64Content = [Convert]::ToBase64String($Bytes)

   $Headers = @{
       "Content-Type" = "Application/json"
   }

   $Body = @{
               CabFile = @{
                   FileName = $cabFileName
                   FileContent = $base64Content
               }
           } | ConvertTo-Json

   $result = Invoke-WebRequest -Method Post -Uri $adminServiceURL -Body $Body -Headers $Headers -UseDefaultCredentials

if ($result.StatusCode -eq 200) {Write-Host "$cabFileName was published successfully."}
else {Write-Host "$cabFileName publish failed. Review AdminService.log for more information."}
```

## Import an unsigned console extension with a script

(*Applies to Configuration Manager version 2107 or later*)

Starting in Configuration Manager version 2107, you can choose to allow unsigned hierarchy approved console extensions. It's a best practice to always used signed extensions to minimize security risks and to confirm the authenticity of a console extension. However, in some cases you may need to allow unsigned console extensions due to an unsigned internally developed extension, or for testing your own custom extension in a lab.

When you have the `.cab` file for an extension, you can test it in a Configuration Manager lab environment. You'll do this by posting it through the [administration service](../../../develop/adminservice/usage). Once the extension is inserted into the site, you can approve it and install it locally from the **Console Extensions** node. To import, run the following PowerShell script after editing the `$adminServiceProvider` and `$cabFilePath`:

- `$adminServiceProvider` - The top-level SMSProvider server where the administration service is installed
- `$cabFilePath` - Path to the extension's `.cab` file

```powershell
$adminServiceProvider = "SMSProviderServer.contoso.com"
$cabFilePath = "C:\Testing\MyExtension.cab"
$adminServiceURL = "https://$adminServiceProvider/AdminService/v1/ConsoleExtensionMetadata/AdminService.UploadExtension"
$cabFileName = (Get-Item -Path $cabFilePath).Name
$Data = Get-Content $cabFilePath
$Bytes = [System.IO.File]::ReadAllBytes($cabFilePath)
$base64Content = [Convert]::ToBase64String($Bytes)
$Headers = @{
    "Content-Type" = "Application/json"
}
$Body = @{
            CabFile = @{
                FileName = $cabFileName
                FileContent = $base64Content
            }
            AllowUnsigned = $true
        } | ConvertTo-Json
$result = Invoke-WebRequest -Method Post -Uri $adminServiceURL -Body $Body -Headers $Headers -UseDefaultCredentials
if ($result.StatusCode -eq 200) {Write-Host "$cabFileName was published successfully."}
else {Write-Host "$cabFileName publish failed. Review AdminService.log for more information."}
```

Note

Currently, when an unsigned extension isn't enabled for user notification, in the **Console Extensions** node, the **Required** column remains blank instead of populating a value of **No**. 

## Import console extensions wizard

(*Applies to Configuration Manager version 2111 or later*)

Starting in version 2111, you can use the **Import Console Extension** wizard to import [console extensions](admin-console-extensions) that are managed for the hierarchy. You no longer need to use a PowerShell script to import a signed or unsigned console extension. To import a console extension using the wizard:

1. From the **Administration** workspace, expand **Updates and Servicing**, then select the **Console Extensions** node.
2. Select **Import Console Extension** from either the ribbon or the right-click menu.
3. When the wizard launches, select **Browse** and navigate to the extension's cab file.
4. If needed, select the option for **Allow extension to be unsigned**.
5. Select **Next** to review the import summary, then complete the wizard to import the extension.

Note

To import unsigned extensions, the **Hierarchy approved console extensions can be unsigned** option needs to be enabled in the **Hierarchy Settings**. For more information, see Allow unsigned hierarchy approved console extensions.

## Install and test an extension on a local console

1. Change the [security scope](../../understand/fundamentals-of-role-based-administration#security-scopes) for the extension. Changing the security scope is recommended for initial testing of an extension.

    1. Go to the **Console Extensions** node under **Administration** &gt; **Overview** &gt; **Updates and Servicing**.
    2. Select the extension, then select **Set Security Scopes** from the ribbon.
    3. Remove the **Default** security scope and add a scope that only contains one or two admins for initial testing.
    4. Choose **OK** to save the security scope for the extension.
2. Approve the extension by selecting **Approve Installation** from the ribbon or right-click menu.

    - If the extension isn't approved, you won't be able to install it or enable in-console notifications for it.
    - If you restart your console at this point, a notification about the available extension won't occur since you haven't enabled the option yet.
3. Install the extension on the local console by choosing **Install**.
4. Once the extension is installed, verify it displays and you can use it from the local console.

## Enable user notifications for extension installation

1. If needed, modify the security scopes for the extension to allow access by more admins. These admins will be targeted with the in-console notification for installing the extension.
2. Select **Enable Notifications**.
3. Launch a Configuration Manager console that doesn't have the extension installed. Ideally, use a test account that you gave access to when you modified the security scope.
4. Verify that the notification for the extension occurs and that you can install the extension.