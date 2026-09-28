---
layout: Conceptual
title: Enumerate Administrative Assignments - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-enumerate-the-administrative-assignments-for-a-user-or-security-group
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
description: In Configuration Manager, the administrative assignments for a user or security group are defined by the roles and security scopes assigned to that user or security group.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: b1659e50-b647-eb06-29a6-cab2b2523131
document_version_independent_id: 9dc8b2fb-e53f-f916-b3cc-d04d850353f7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-enumerate-the-administrative-assignments-for-a-user-or-security-group.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-enumerate-the-administrative-assignments-for-a-user-or-security-group
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-enumerate-the-administrative-assignments-for-a-user-or-security-group.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 907c2229-9b5b-f721-9121-550983b5d2bf
---

# Enumerate Administrative Assignments - Configuration Manager | Microsoft Learn

The administrative assignments for a user or security group are defined by the roles and security scopes assigned to that user or security group. The Windows Management Instrumentation (WMI) `SMS_Admin` class contains all the administrators defined in Configuration Manager. The security roles for an admin are in the `SMS_Admin.Roles` property and the security scopes for an admin are in the `SMS_Admin.Categories` property. Both of these properties expose an array of strings which correspond to the identifier of the role or security scope. Both properties are also marked as `lazy` and are read-only.

Important

`Lazy` properties are never retrieved with the class instance if the class instance was loaded from a query. The object must be directly accessed from WMI. Generally the WMI provider will supply a `Get` method that will accept a query path to the object.

To determine whether an administrator references a user account or a security group, check the `SMS_Admin.AccountType` property. This property value will be one or zero. Zero means that the account is a user, and one means the account is a security group.

### To read the roles and security scopes of an administrator

1. Set up a connection to the SMS Provider.
2. Get an instance to a `SMS_Admin` WMI class that matches the desired administrator by using their identifier.
3. Read the `Roles` and `Categories` properties.

## Example

The following example pulls an admin directly from WMI and displays the role and security scope identifiers:

```vbs
Sub PrintAdminScopesAndRoles(connection, adminId)
    Dim admin
    Dim item
    On Error Resume Next
    set admin = Nothing
    Set admin = connection.Get("SMS_Admin.AdminID=" & CStr(adminId))
    On Error Goto 0
    If (Not admin Is Nothing) Then
        WScript.Echo "Reading Admin: " + admin.LogonName
        WScript.Echo ""
        WScript.Echo " == Roles (" + CStr(UBound(admin.Roles) + 1) + ") =="
        For Each item In admin.Roles
            WScript.Echo " = " + item
        Next
        WScript.Echo ""
        WScript.Echo " == Security Scopes (" + CStr(UBound(admin.Categories) + 1) + ") =="
        For Each item In admin.Categories
            WScript.Echo " = " + item
        Next
    Else
        WScript.Echo "Admin with id " + CStr(adminId) + " not found."
    End If
End Sub

```

```c
public void PrintAdminScopesAndRoles(WqlConnectionManager connection, int adminId)
{
    IResultObject admin = null;
    try
    {
        admin = connection.GetInstance("SMS_Admin.AdminID=" + adminId.ToString());
    }
    catch (Exception) { }
    if (admin != null)
    {
        Console.WriteLine("Reading Admin: " + admin["LogonName"].StringValue);
        Console.WriteLine("");
        Console.WriteLine(String.Format("== Roles ({0}) ==", admin["Roles"].StringArrayValue.Length.ToString()));
        foreach (var item in admin["Roles"].StringArrayValue)            Console.WriteLine("= " + item);
            Console.WriteLine("");
            Console.WriteLine(String.Format("== Security Scopes ({0}) ==", admin["Categories"].StringArrayValue.Length.ToString()));
        foreach (var item in admin["Categories"].StringArrayValue)
            Console.WriteLine("= " + item);
    }
    else
        Console.WriteLine("Admin with id " + adminId.ToString() + " not found.");
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `adminId` | `Integer` | The admin identifier. |

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