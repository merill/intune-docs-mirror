---
layout: Conceptual
title: Associate an Object with a Security Scope - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-associate-an-object-with-a-security-scope
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
description: To assign multiple objects to a scope, use the AddMemberships Method in Class SMS_SecuredCategoryMembership.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: f1ce31ba-6d2e-a1a2-90c7-415ae939f211
document_version_independent_id: 04026bf7-3365-8212-7cb5-2dbd3b3a797a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-associate-an-object-with-a-security-scope.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-associate-an-object-with-a-security-scope
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-associate-an-object-with-a-security-scope.md
cmProducts: []
platformId: 4aa3c118-d2a9-9350-451a-cdf70ddfc43f
---

# Associate an Object with a Security Scope - Configuration Manager | Microsoft Learn

Tip

To assign multiple objects to a scope, use the [AddMemberships Method in Class SMS_SecuredCategoryMembership](../../../reference/core/servers/configure/addmemberships-method-in-class-sms_securedcategorymembership).

### To assign an object a security scope

1. Set up a connection to the SMS Provider.
2. Determine the object's key property identifier.
3. Determine the object type identifier.
4. Create a new instance of the `SMS_SecuredCategoryMembership` WMI class, setting the scope identifier, object key, and object type values.
5. Save the `SMS_SecuredCategoryMembership` object instance.

## Example

The following code example assigns a scope identifier to a package:

```vbs
Sub AddObjectScope(connection, scopeId, objectKey, objectTypeId)

    Dim assignment

    ' Create a new instance of the scope assignment.
    Set assignment = connection.Get("SMS_SecuredCategoryMembership").SpawnInstance_()

    ' Configure the assignment
    assignment.CategoryID = scopeId
    assignment.ObjectKey = objectKey
    assignment.ObjectTypeID = objectTypeId

    ' Commit the assignment
    assignment.Put_

End Sub
```

```c
public void AddObjectScope(WqlConnectionManager connection, string scopeId, string objectKey, int objectTypeId)
{
    // Create a new instance of the scope assignment.
    IResultObject assignment = connection.CreateInstance("SMS_SecuredCategoryMembership");

    // Configure the assignment
    assignment.Properties["CategoryID"].StringValue = scopeId;
    assignment.Properties["ObjectKey"].StringValue = objectKey;
    assignment.Properties["ObjectTypeID"].IntegerValue = objectTypeId;

    // Commit the assignment
    assignment.Put();
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `scopeId` | `String` | The identifier of the security scope. |
| objectKey | `String` | The key property value of the object to assign a scope to. |
| objectTypeId | `Integer` | The type identifier of the object referenced in the `objectKey` parameter. |

## Compiling the Code

The C# example requires:

### Namespaces

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).