---
layout: Conceptual
title: Check if a User Has Permissions for a Resource - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-check-if-a-user-has-permissions-for-a-resource
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
description: Check whether a user has permission for a resource using the GetCollectionsWithResourcePermissions method in the SMS_RbacSecuredObject class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 7301dabf-8d6b-65a4-32a1-7e14278729be
document_version_independent_id: 61e1e75a-867a-ffbb-f312-84a1107f7a81
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-check-if-a-user-has-permissions-for-a-resource.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-check-if-a-user-has-permissions-for-a-resource
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-check-if-a-user-has-permissions-for-a-resource.md
cmProducts: []
platformId: a12e10e3-9bfc-d9fb-d566-fc1547486cd2
---

# Check if a User Has Permissions for a Resource - Configuration Manager | Microsoft Learn

In Configuration Manager, you can check whether a user has permission for a resource using the `GetCollectionsWithResourcePermissions` method in the `SMS_RbacSecuredObject` class.

### To check if a user has permissions for a resource

1. Create a dictionary object to pass object name and permissions to check for to the [GetCollectionsWithResourcePermissions Method in Class SMS_RbacSecuredObject](../../../reference/core/servers/configure/getcollectionswithresourcepermissions-method-in-class-sms_rbacsecuredobject).
2. Call the [GetCollectionsWithResourcePermissions Method in Class SMS_RbacSecuredObject](../../../reference/core/servers/configure/getcollectionswithresourcepermissions-method-in-class-sms_rbacsecuredobject), passing in the dictionary object.
3. The method returns `true`, if the user has the permissions.

## Example

The following example checks to see if the user has resource permissions.

```c
public bool CheckUserPermissions(ConnectionManagerBase connectionManager, string resourceID)
{
    bool result = false;
    int iId = 0;
    IResultObject outParams = null;
    if (int.TryParse(resourceID, out iId) == false)
    {
        throw new ArgumentException("Invalid resource ID");
    }
    //ControlAMT permissions.
    int controlAMT = 0x1000000;
    try
    {
        Dictionary<string, object> inParams = new Dictionary<string, object>();
        inParams["Permissions"] = controlAMT;
        inParams["ResourceID"] = iId;
        outParams = connectionManager.ExecuteMethod("SMS_RbacSecuredObject", "GetCollectionsWithResourcePermissions", inParams);
        if (outParams != null)
        {
            //If the return value equals 0 and the array is not empty, the user has the resource permissions.
            if (outParams["ReturnValue"].IntegerValue == 0 && outParams["CollectionIDs"].StringArrayValue.Length != 0)
            {
                result = true;
            }
        }
    }
    finally
    {
        if (outParams != null)
        {
             outParams.Dispose();
        }
    }
    return result;
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `connectionManager` | A valid connection to the SMS Provider. |
| `resourceID` | `String` | Unique ID, supplied by Configuration Manager, for the resource. |

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