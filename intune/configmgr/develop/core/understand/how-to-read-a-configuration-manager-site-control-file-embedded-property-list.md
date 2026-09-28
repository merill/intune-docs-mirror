---
layout: Conceptual
title: Read a Site Control File Embedded Property List - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-site-control-file-embedded-property-list
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
description: Learn how to read a Configuration Manager site control embedded property list in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: cc9c515e-b1bb-153c-f7d7-cca12966aa84
document_version_independent_id: eef65c07-f84d-1e1c-8866-b95ec4074141
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-site-control-file-embedded-property-list.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-read-a-configuration-manager-site-control-file-embedded-property-list
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-site-control-file-embedded-property-list.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: dedddb67-1559-e396-205e-8edaf0d6fab2
---

# Read a Site Control File Embedded Property List - Configuration Manager | Microsoft Learn

In Configuration Manager, you read an embedded property list from a site control file resource by getting the [SMS_EmbeddedPropertyList](../../reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class) object for the embedded object from the resources *PropLists* property array.

An embedded property list has the following properties that you can set. For more information, see [SMS_EmbeddedPropertyList](../../reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class).

| Value | Description |
| --- | --- |
| PropertyListName | The embedded property name. |
| Values | An array of string values. Each array item represents a single property list item. |

Caution

Making changes to the site control file can cause irreparable damage to your Configuration Manager site.

### To read a site control file embedded property list

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](sms-provider-fundamentals).
2. Using the connection object from step one, get a site control file resource. For more information, see [About the Configuration Manager Site Control File](about-the-configuration-manager-site-control-file).
3. Get the `SMS_EmbeddedPropertyList` for the required embedded property list.
4. Access the property list values by using the `SMS_EmbeddedPropertyList` object *Values* property array.

## Example

The following example method populates the supplied `values` parameter with the *Values* array of the embedded property list `SMS_EmbeddedPropertyList` identified by the `propertyListName` parameter. `true` is returned if the embedded property list is found; otherwise, `false` is returned.

To view code that calls these functions, see [How to Read and Write to the Configuration Manager Site Control File by Using Managed Code](how-to-read-and-write-to-the-site-control-file-by-using-managed-code) or see [How to Read and Write to the Configuration Manager Site Control File by Using WMI](how-to-read-and-write-to-the-site-control-file-by-using-wmi).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs

Function GetScfEmbeddedPropertyList(resource,  _
        propertyListName,               _
        ByRef values)

    Dim scfPropertyList

    If IsNull(resource.PropLists) = True Then
        GetScfPropertyList = False
        Exit Function
    End If

    For each scfPropertyList in resource.PropLists
       if   scfPropertyList.PropertyListName = propertyListName Then
            ' Found property list, so return the values array.
            values = scfPropertyList.Values
            GetScfEmbeddedPropertyList = True
            Exit Function
        End If
     Next

     ' Did not find the property list.
     GetScfEmbeddedPropertyList = False
End Function

```

```c
public bool GetScfEmbeddedPropertyList(
    IResultObject resource,
    string propertyListName,
    out ArrayList values)
{
    values = new ArrayList();
    try
    {
        if (resource.EmbeddedPropertyLists.ContainsKey(propertyListName))
        {
            values.AddRange(resource.EmbeddedPropertyLists[propertyListName]["Values"].StringArrayValue);
            return true;
        }
    }
    catch(SmsException e)
    {
        Console.WriteLine("Couldn't get the embedded property list: " + e.Message);
    }
    return false;

}

```

The sample method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Resource` | - Managed: `IResultObject`- VBScript: [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) | The site control file resource that contains the embedded property. |
| `propertyListName` | - Managed: `String`- VBScript: `String` | The embedded property list to be read. |
| `Values` | - Managed: `String` array- VBScript: `String` array | The `SMS_EmbeddedProperty` class Values property. An array of string values. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

System.Collections

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../servers/configure/role-based-administration).