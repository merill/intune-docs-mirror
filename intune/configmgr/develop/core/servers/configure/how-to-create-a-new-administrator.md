---
layout: Conceptual
title: Create a New Administrator - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-a-new-administrator
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
description: Learn how administrative assignments for a user or security group are defined by the roles and security scopes assigned to that user or security group.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 588badbc-9a7f-d90e-ece4-cc54bca39840
document_version_independent_id: ccab3dd0-36c9-7134-5c5a-7ddc43a03d02
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-create-a-new-administrator.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-create-a-new-administrator
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-create-a-new-administrator.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 07823001-4c92-ea92-2ec6-b6c79cf5d48e
---

# Create a New Administrator - Configuration Manager | Microsoft Learn

The administrative assignments for a user or security group are defined by the roles and security scopes assigned to that user or security group. The Windows Management Instrumentation (WMI) `SMS_Admin` class contains all the administrators defined in Configuration Manager. The security roles for an admin are in the `SMS_Admin.Roles` property and the security scopes for an admin are in the `SMS_Admin.Categories` property. Both of these properties expose an array of strings which correspond to the identifier of the role or security scope. Both properties are also marked as `lazy` and are read-only.

Important

`Lazy` properties are never retrieved with the class instance if the class instance was loaded from a query. The object must be directly accessed from WMI. Generally the WMI provider will supply a `Get` method that will accept a query path to the object.

### To create a new administrator

1. Set up a connection to the SMS Provider.
2. Get an instance to a `SMS_Admin` WMI class that matches the desired administrator by using their identifier.
3. Add permissions, including category, role and secured scope.

    Important

    Category, role and secured scope are all required values.
4. Save the new administrator instance.

## Example

The following example pulls an admin directly from WMI and displays the role and security scope identifiers:

```c
public void CreateSMSAdmin(WqlConnectionManager connection, string distinguishedName, string categoryID, string roleID, int categoryTypeID)
 {
     // Create a new administrator instance.
     IResultObject newSMSAdmin = connection.CreateInstance("SMS_Admin");

     // Set the required properties.
     // One set of example values in comments.
    newSMSAdmin.Properties["DistinguishedName"].StringValue = distinguishedName; // "CN=<USERACCOUNT>,CN=Users,DC=<DOMAINNAME>,DC=COM"

    // Create new permissions list.
    List<IResultObject> permissionsObjectList = new List<IResultObject>();

    // Add permissions.
    IResultObject permissionObject = connection.CreateEmbeddedObjectInstance("SMS_APermission");
    permissionObject["CategoryID"].StringValue = categoryID;             // "SMS00004" (All Users and User Groups)
    permissionObject["RoleID"].StringValue = roleID;                     // "SMS000GR" (EndPoint Protection Manager)
    permissionObject["CategoryTypeID"].IntegerValue = categoryTypeID;    // 1          (Collection)
    permissionsObjectList.Add(permissionObject);

    // Add secured scope.
    IResultObject permissionObject2 = connection.CreateEmbeddedObjectInstance("SMS_APermission");
    permissionObject2["CategoryID"].StringValue = "SMS00UNA";             // "SMS00UNA" (Default)
    permissionObject2["RoleID"].StringValue = "SMS000GR";                 // "SMS000GR" (EndPoint Protection Manager)
    permissionObject2["CategoryTypeID"].IntegerValue = 29;                // 29         (Secured Scope)
    permissionsObjectList.Add(permissionObject2);

    // Save the permissions list to the new administrator instance.
     newSMSAdmin.SetArrayItems("Permissions", permissionsObjectList);

    // Save the new administrator instance.
     newSMSAdmin.Put();
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `distinguishedName` | - Managed: `String` | Like "CN=John Doe,OU=UserAccounts,DC=contoso,DC=com" |
| `categoryID` | - Managed: `String` | The RBA secured categories associated with this account. |
| `CategoryTypeID` | - Managed: `Integer` | The type of the category (collection or secured scope). |

## Compiling the Code

The C# example requires:

### Namespaces

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

System

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

mscorlib

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).