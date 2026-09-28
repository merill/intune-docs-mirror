---
layout: Conceptual
title: Clear a PXE Advertisement for a Resource - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-clear-a-pxe-advertisement-for-a-configuration-manager-resource
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
description: To clear a PXE advertisement for a Configuration Manager resource, call the SMS_Collection object ClearLastNBSAdvForMachines method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: ccedaab2-d614-1c10-37a8-0b0f746e0535
document_version_independent_id: ea8bd992-cedc-a285-7b62-f5115b24f1c2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-clear-a-pxe-advertisement-for-a-configuration-manager-resource.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-clear-a-pxe-advertisement-for-a-configuration-manager-resource
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-clear-a-pxe-advertisement-for-a-configuration-manager-resource.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: ae34d3b4-bc46-b721-4db9-920c78e51129
---

# Clear a PXE Advertisement for a Resource - Configuration Manager | Microsoft Learn

To clear a PXE advertisement for a Configuration Manager resource, you call the [SMS_Collection](../reference/core/clients/collections/sms_collection-server-wmi-class) object [ClearLastNBSAdvForMachines](../reference/core/clients/collections/clearlastnbsadvformachines-method-in-class-sms_collection) method.

Clearing PXE advertisement is used to re-advertise a mandatory advertisement that is enabled for a PXE device or assigned to a collection. For information about clearing the PXE advertisement for a collection, see [How to Clear a PXE Advertisement For a Configuration Manager Collection](how-to-clear-a-pxe-advertisement-for-a-configuration-manager-collection).

Clearing a PXE advertisement forces the PXE server to re-evaluate the mandatory advertisement that a PXE device must execute on the next PXE boot. It is most often used when the last advertisement that was executed failed or when the advertisement must be re-run.

### To clear a PXE advertisement for a resource

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Create the `ClearLastNBSAdvForMachines` method resource identifier array for the method parameters.
3. Call the `ClearLastNBSAdvForMachines` method to clear the PXE advertisement for the resource.

## Example

The following example clears the PXE advertisement for the resource identified by the `resourceID` parameter.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub ClearPxeAdvertisementResource(connection,resourceID)

    On Error Resume Next

    Dim resources
    Dim InParams

    ' Set up the Resource array parameter.
    resources = Array(1)
    resources(0) = resourceID

    Set InParams = connection.Get("SMS_Collection").Methods_("ClearLastNBSAdvForMachines").InParameters.SpawnInstance_
    InParams.ResourceIDs = resources

    connection.ExecMethod "SMS_Collection","ClearLastNBSAdvForMachines", InParams

    if Err.number <> 0 Then
        WScript.Echo "Failed to clear PXE advertisement for resource: " & resourceID
        Exit Sub
    End If

End Sub

```

```c
public void ClearPxeAdvertisementResource(WqlConnectionManager connection, int resourceID)
{
    try
    {
        List<int> resourceIDs = new List<int>();
        Dictionary<string, object> inParams = new Dictionary<string, object>();

        resourceIDs.Add(resourceID);
        inParams.Add("ResourceIDs", resourceIDs.ToArray());

        IResultObject outParams = connection.ExecuteMethod("SMS_Collection","ClearLastNBSAdvForMachines",inParams);

        if (outParams == null || outParams["StatusCode"].IntegerValue != 0)
        {
            Console.WriteLine
                ("Failed to clear PXE advertisement for resource " + resourceID);
            return;
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to PXE advertisement " + e.Message);
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `resourceID` | - Managed: `Integer`- VBScript: `Integer` | The resource identifier. You can obtain this from the [SMS_Resource](../reference/core/clients/manage/sms_resource-server-wmi-class) class `ResourceId` property. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).