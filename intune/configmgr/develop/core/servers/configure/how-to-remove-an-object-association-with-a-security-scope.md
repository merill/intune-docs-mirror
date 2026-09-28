---
layout: Conceptual
title: Remove an Object Association with a Security Scope - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-remove-an-object-association-with-a-security-scope
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
description: Remove a security scope from an object by using an SMS_SecuredCategoryMembership class instance.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d00adaf0-7a80-7d47-062b-2f280c264fea
document_version_independent_id: a407bbd1-4152-b9a5-18a9-cc5a87d17992
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-remove-an-object-association-with-a-security-scope.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-remove-an-object-association-with-a-security-scope
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-remove-an-object-association-with-a-security-scope.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 12522981-24ff-e6f1-5b4d-9bedbc1595b2
---

# Remove an Object Association with a Security Scope - Configuration Manager | Microsoft Learn

Removing a security scope from an object instance is as simple as deleting the Windows Management Instrumentation (WMI)`SMS_SecuredCategoryMembership` class instance. However, object instances must have at least one security scope associated with them. The last object instance can never be removed. Every object is created with the `Default` security scope, and if all other security scopes are to be removed from an object instance, the `Default` should be added to it before removal.

Important

You must have administrative rights to the scope and the object you are removing it from. If you do not have the correct permissions, removing a scope from that object instance will fail. Removing the last scope from an object will be unsuccessful and will fail.

Tip

To remove multiple objects to a scope, use the [RemoveMemberships Method in Class SMS_SecuredCategoryMembership](../../../reference/core/servers/configure/removememberships-method-in-class-sms_securedcategorymembership).

### To remove a security scope from an object

1. Set up a connection to the SMS Provider.
2. Determine the object's key property identifier.
3. Determine the object type identifier.
4. Determine the scope identifier.
5. Find an instance of the `SMS_SecuredCategoryMembership` WMI class that matches the .
6. Delete the instance.

## Example

The following code example removes a scope identifier from a package:

```vbs
Sub RemoveObjectScope(connection, scopeId, objectKey, objectTypeId)

    Dim assignment

    ' Find the existing scope assignement that matches our parameters.
    Set assignment = connection.Get("SMS_SecuredCategoryMembership.CategoryID='" & scopeId & "',ObjectKey='" & objectKey & "',ObjectTypeId=" & objectTypeId)

    If (assignment Is Nothing) Then
        Err.Raise 1, "RemoveObjectScope", "Unable to find matching scope, object, and object type."
    Else
        assignment.Delete_
    End If
End Sub
```

```c
public void RemoveObjectScope(WqlConnectionManager connection, string scopeId, string objectKey, int objectTypeId)
{
    // Find the existing scope assignement that matches our parameters.
     IResultObject assignment = connection.GetInstance("SMS_SecuredCategoryMembership.CategoryID='" + scopeId + "',ObjectKey='" + objectKey + "',ObjectTypeID=" + objectTypeId.ToString());

   // Make sure we found the scope.
    if (assignment == null)
        throw new System.Exception("Unable to find matching scope, object, and object type.");
    else
        assignment.Delete();
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `scopeId` | `String` | The identifier of the security scope. |
| objectKey | `String` | The key property value of the object. |
| objectTypeId | `Integer` | The type identifier of the object referenced in the `objectKey` parameter. |

## Compiling the Code

The C# example requires:

### Namespaces

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider