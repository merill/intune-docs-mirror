---
layout: Conceptual
title: Check if a User Has Permissions for an Object - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-check-if-a-user-has-permissions-for-an-object
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
description: In Configuration Manager, you can check for object permissions using the UserHasPermissions Method in Class SMS_RbacSecuredObject.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: eecd1ada-136e-0187-58e3-0db3119f9262
document_version_independent_id: 07d52d35-c525-b0c2-be8b-09bde78e2747
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-check-if-a-user-has-permissions-for-an-object.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-check-if-a-user-has-permissions-for-an-object
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-check-if-a-user-has-permissions-for-an-object.md
cmProducts: []
platformId: f16219ef-b1bd-e772-744b-9950648252fd
---

# Check if a User Has Permissions for an Object - Configuration Manager | Microsoft Learn

In Configuration Manager, you can check for object permissions using the [UserHasPermissions Method in Class SMS_RbacSecuredObject](../../../reference/core/servers/configure/userhaspermissions-method-in-class-sms_rbacsecuredobject).

### To check if a user has permissions for an object

1. Create a dictionary object to pass object name and permissions to check for to the [UserHasPermissions Method in Class SMS_RbacSecuredObject](../../../reference/core/servers/configure/userhaspermissions-method-in-class-sms_rbacsecuredobject).
2. Call the [UserHasPermissions Method in Class SMS_RbacSecuredObject](../../../reference/core/servers/configure/userhaspermissions-method-in-class-sms_rbacsecuredobject), passing in the dictionary object.
3. The method returns `true`, if the user has the permissions.

## Example

The following example checks to see if the user has the indicated permissions:

```c
public static bool UserHasPermissions(ConnectionManagerBase connectionManager, string objectName, int permissions, out int currentPermissions)
{
    if (connectionManager == null)
    {
        throw new ArgumentNullException("connectionManager");
    }
    if (string.IsNullOrEmpty(objectName) == true)
    {
        throw new ArgumentException("The parameter 'objectName' cannot be null or an empty string", "objectName");
    }
    IResultObject outParams = null;
    try
    {
        Dictionary<string, object> inParams = new Dictionary<string, object>();
        inParams["ObjectPath"] = objectName;
        inParams["Permissions"] = permissions;
        outParams = connectionManager.ExecuteMethod("SMS_RbacSecuredObject", "UserHasPermissions", inParams);
       if (outParams != null)
       {
            currentPermissions = outParams["Permissions"].IntegerValue;
            return outParams["ReturnValue"].BooleanValue;
       }
    }
    finally
    {
        if (outParams != null)
        {
            outParams.Dispose();
        }
    }
    currentPermissions = 0;
    return false;
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connectionManager` | - Managed: `connectionManager` | A valid connection to the SMS Provider. |
| `objectName` | `String` | Name of the object. |
| permissions | Integer | The permissions. |
| currentPermissions | Integer | The current permissions. |

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