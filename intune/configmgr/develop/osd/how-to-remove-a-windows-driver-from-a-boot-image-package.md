---
layout: Conceptual
title: Remove a Windows Driver from a Boot Image Package - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-remove-a-windows-driver-from-a-boot-image-package
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
description: In Configuration Manager, you remove a Windows driver from an operating system deployment boot image package by removing it from the ReferencedDrivers property of the SMS_BootImagePackage Server WMI Class object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: fbfe1248-7283-bba1-81dc-563ff408f856
document_version_independent_id: 8085b347-4c90-56fb-9c5a-d5261fe2d9cb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-remove-a-windows-driver-from-a-boot-image-package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-remove-a-windows-driver-from-a-boot-image-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-remove-a-windows-driver-from-a-boot-image-package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0625c1de-e761-bf9e-f0c7-fbafc666c66c
---

# Remove a Windows Driver from a Boot Image Package - Configuration Manager | Microsoft Learn

In Configuration Manager, you remove a Windows driver from an operating system deployment boot image package by removing it from the `ReferencedDrivers` property of the [SMS_BootImagePackage Server WMI Class](../reference/osd/sms_bootimagepackage-server-wmi-class) object.

Note

The driver is not removed until the boot image package is refreshed and updated on the distribution points.

### To remove a Windows driver from a boot image package

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get the [SMS_BootImagePackage](../reference/osd/sms_bootimagepackage-server-wmi-class) object for the boot image package that contains the driver you want to remove.
3. Remove the driver from the `ReferencedDrivers` property. The driver is identified by its configuration item identifier represented by the `ID` property of the [SMS_Driver_Details Server WMI Class](../reference/osd/sms_driver_details-server-wmi-class) object. This identifier matches the `CI_ID` property of `SMS_Driver`.
4. Commit the `SMS_BootImagePackage` object changes.
5. Refresh the boot image package by calling `RefreshPkgSource`.

## Example

The following example method removes the Windows driver from the boot image package. The package is identified by its `PackageID` property and the driver is identified by its `CI_ID` property.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub RemoveDriverFromBootImagePackage(connection, driverId, packageId)
    Dim bootImagePackage
    Dim driver
    Dim driverDetails
    Dim newReferencedDrivers()
    Dim found
    Dim index

    ' Get the boot image package.
    Set bootImagePackage = connection.Get("SMS_BootImagePackage.PackageID='" & packageId &"'" )

    found = False
    index=0

    ' Copy the contents and leave out the driver.
    For Each driver In bootImagePackage.ReferencedDrivers
        If driver.ID = driverID Then
            found=True
        Else
           Set newReferencedDrivers(index)=driver
           index = index + 1
        End If
    Next

    ' Update the referenced drivers.
    If found=True Then
        ReDim preserve newReferencedDrivers(UBound(bootImagePackage.ReferencedDrivers)-1)
        bootImagePackage.ReferencedDrivers=newReferencedDrivers
        bootImagePackage.Put_
        bootImagePackage.RefreshPkgSource
   End If

End Sub
```

```c
public void RemoveDriverFromBootImagePackage(
    WqlConnectionManager connection,
    int driverId,
    string packageId)
{
    try
    {
        // Get the boot image package.
        IResultObject bootImagePackage = connection.GetInstance(@"SMS_BootImagePackage.packageId='" + packageId + "'");

        // Get the (SMS_Driver_Details) drivers referenced by the package.
        List<IResultObject> referencedDrivers = bootImagePackage.GetArrayItems("ReferencedDrivers");

        foreach (IResultObject ro in referencedDrivers)
        {
            if (ro["ID"].IntegerValue == driverId) // Remove the driver that matches driverId.
            {
                referencedDrivers.Remove(ro);
                break;
            }
        }

        bootImagePackage.SetArrayItems("ReferencedDrivers", referencedDrivers);

        // Commit the changes.
        bootImagePackage.Put();
        bootImagePackage.ExecuteMethod("RefreshPkgSource", null);
    }
    catch (SmsException e)
    {
        Console.WriteLine(e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `driverID` | - Managed: `Integer`- VBScript: `Integer` | The Windows driver identifier available in `SMS_Driver.CI_ID`. |
| `PackageID` | - Managed: `String`- VBScript: `String` | The boot image package identifier available in `SMS_BootImagePackage.PackageID`. |

## Compiling the Code

This C# example requires:

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