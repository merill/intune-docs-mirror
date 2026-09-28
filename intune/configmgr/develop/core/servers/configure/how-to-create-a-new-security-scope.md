---
layout: Conceptual
title: Create a New Security Scope - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-a-new-security-scope
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
description: Learn how to create a new security scope and that All security scopes are defined by the SMS_SecuredCategory Windows Management Instrumentation (WMI) class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: a13b9b48-16b7-b74b-3be7-f559d6a502cb
document_version_independent_id: c5b9de2b-54ab-dd2a-8ab0-a125a03dfa67
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-create-a-new-security-scope.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-create-a-new-security-scope
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-create-a-new-security-scope.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 79728fa6-5bcb-d5b3-9cdd-eb779c668cd7
---

# Create a New Security Scope - Configuration Manager | Microsoft Learn

Creating a security scope in Configuration Manager is simple. All security scopes are defined by the `SMS_SecuredCategory` Windows Management Instrumentation (WMI) class. Only two properties are required when you are creating a new security scope, the name and description.

### To create a new security scope

1. Set up a connection to the SMS Provider.
2. Create an instance of the `SMS_SecuredCategory` WMI class
3. Set the `CategoryName` and `CategoryDescription` properties.
4. Save the security scope.

## Example

The following example creates a new security scope:

```vbs
Sub CreateSecurityScope(connection, scopeName, scopeDescription)

    Dim scope

    ' Create a new security scope instance.
    Set scope = connection.Get("SMS_SecuredCategory").SpawnInstance_()

    ' Set the required properties.
    scope.CategoryName = scopeName    scope.CategoryDescription = scopeDescription

    ' Save the security scope.
    scope.Put_

End Sub
```

```c
public void CreateSecurityScope(WqlConnectionManager connection, string scopeName, string scopeDescription)
{
    // Create a new security scope instance.
    IResultObject secScope = connection.CreateInstance("SMS_SecuredCategory");

    // Set the required properties.
    secScope.Properties["CategoryName"].StringValue = scopeName;
    secScope.Properties["CategoryDescription"].StringValue = scopeDescription;

    // Save the security scope.
    secScope.Put();
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `scopeName` | `String` | The name of security scope. |
| `scopeDescription` | `String` | The description of security scope. |

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