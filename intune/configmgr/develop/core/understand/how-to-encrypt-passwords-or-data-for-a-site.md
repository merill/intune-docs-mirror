---
layout: Conceptual
title: Encrypt Passwords or Data for a Site - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-encrypt-passwords-or-data-for-a-site
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
description: Encrypt Passwords or Data for a Site. Using a new WMI method, the user accounts' passwords can be encrypted for a specific site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: e14ea64c-699c-d27a-1d10-5ac4f5b93b44
document_version_independent_id: 09b983af-4ace-9d09-be57-4368c456594f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-encrypt-passwords-or-data-for-a-site.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-encrypt-passwords-or-data-for-a-site
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-encrypt-passwords-or-data-for-a-site.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: ab3913d5-3512-50e0-1fce-b398993f70c9
---

# Encrypt Passwords or Data for a Site - Configuration Manager | Microsoft Learn

In Configuration Manager, user accounts connect to site systems and Active Directory to perform various tasks. Prior to System Center 2012 Configuration Manager, the Manage Site Accounts tool (MSAC) was used to manage these user accounts. The MSAC tool has been deprecated.

Using a new WMI method, these account passwords can be encrypted for a specific site. The following code snipped demonstrates how user account passwords can be encrypted for a specific site.

## To Encrypt Data for a Site

1. Connect to the Configuration Manager site.
2. Get the parameters for the [EncryptDataEx Method in Class SMS_Site](../../reference/core/servers/configure/encryptdataex-method-in-class-sms_site) method.
3. Add the data to be encrypted to the `Data` parameter.
4. Add the site code of the specific site for which the data should be encrypted to the `SiteCode` parameter.
5. Encrypt the data for the specified site by invoking the [EncryptDataEx Method in Class SMS_Site](../../reference/core/servers/configure/encryptdataex-method-in-class-sms_site).
6. In this case, the encrypted string is output as a test.

### Example

The following example encrypts data for a specific site.

```csharp
using System;
using System.Management;

namespace Encryption
{
    class Program
    {
        static void Main(string[] args)
        {
            // SMS_Site::EncryptDataEx is a class level method,
            // it will encrypt data for the site based on passed in site code.
            try
            {
                ManagementScope scope = new ManagementScope(@"root\sms\site_ABC");
                ManagementClass cls = new ManagementClass(scope.Path.Path, "SMS_Site", null);
                // Set up input parameters.
                ManagementBaseObject inParams = cls.GetMethodParameters("EncryptDataEx");
                inParams["Data"] = @"pass123";  // data to be encrypted
                inParams["SiteCode"] = @"ABC";  // encrypt the data for that specific site

                // Get the encrypted data.
                ManagementBaseObject outSiteParams = cls.InvokeMethod("EncryptDataEx", inParams, null);

                // print the encrypted data
                Console.WriteLine(outSiteParams["EncryptedData"].ToString());
            }
            catch (ManagementException e)
            {
                Console.WriteLine("Failed to execute method {0}", e.ToString());
            }
        }
    }
}

```

## Compiling the Code

The C# example requires:

### Namespaces

System

System.Management

### Assembly

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](about-configuration-manager-errors).