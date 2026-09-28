---
layout: Conceptual
title: Create a New Security Role - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-a-new-security-role
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
description: Learn how the administrative assignments for a user or security group are defined by the roles and security scopes assigned to that user or security group.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 178601a0-496b-7a0c-8ef1-ed1e23c5b5b2
document_version_independent_id: 205cfb03-c631-7108-1258-84d0e28466c4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-create-a-new-security-role.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-create-a-new-security-role
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-create-a-new-security-role.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 31e18634-0dc0-e4d3-bcda-00e0e63abba5
---

# Create a New Security Role - Configuration Manager | Microsoft Learn

The administrative assignments for a user or security group are defined by the roles and security scopes assigned to that user or security group. The Windows Management Instrumentation (WMI)`SMS_Admin` class contains all the administrators defined in Configuration Manager. The security roles for an admin are in the `SMS_Admin.Roles` property and the security scopes for an admin are in the `SMS_Admin.Categories` property. Both of these properties expose an array of strings which correspond to the identifier of the role or security scope. Both properties are also marked as `lazy` and are read-only.

Important

`Lazy` properties are never retrieved with the class instance if the class instance was loaded from a query. The object must be directly accessed from WMI. Generally the WMI provider will supply a `Get` method that will accept a query path to the object.

### To create a new Security Role

1. Set up a connection to the SMS Provider.
2. Create an instance of the `SMS_Role` WMI class.
3. Set the required properties, including a new role name and the original security role to copy.
4. Get an instance of the original `SMS_Role` WMI class.
5. Copy the role permissions from the original security role to the new security role. This is similar to the Admin Console functionality when creating a new security role and not strictly required to create the security role.
6. Save the new security role.

## Example

The following example creates a new security role:

```c
public void CreateRole(WqlConnectionManager connection, string roleName, string originalRoleID)
{
    // Create a new security role instance.
    IResultObject newRole = connection.CreateInstance("SMS_Role");

    // Set the required properties.
    // Note: RoleDescription is not required, but convenient.
    newRole.Properties["RoleName"].StringValue = roleName;
    newRole.Properties["CopiedFromID"].StringValue = originalRoleID;
    newRole.Properties["RoleDescription"].StringValue = roleName + " Description";

    // Get the original role instance.
    IResultObject originalRole = connection.GetInstance(@"SMS_Role.RoleID='" + originalRoleID + "'");

    // Copy the original role permissions to the new security role.
    newRole.SetArrayItems("Operations", originalRole.GetArrayItems("Operations"));

    // Save the new security role.
    newRole.Put();
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |
| roleName | - Managed: `String` | A name for the new role. |
| `originalRoleID` | - Managed: `String` | The identifier of the original security role. |

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