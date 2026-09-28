---
layout: Conceptual
title: Import a MOF File to Extend Inventory - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/inventory/how-to-import-a-mof-file-to-extend-inventory
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
description: Learn how to import a MOF file to extend inventory, in Configuration Manager, by using the ImportInventoryReport method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: fa7bc8bf-50e1-1e30-80fd-a7282b9e9a38
document_version_independent_id: aee8e6a4-3aa7-7e5d-7beb-2af49a419929
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/inventory/how-to-import-a-mof-file-to-extend-inventory.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/inventory/how-to-import-a-mof-file-to-extend-inventory
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/inventory/how-to-import-a-mof-file-to-extend-inventory.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: c21ec14f-0dd3-3c29-8a9e-e5a37f298ded
---

# Import a MOF File to Extend Inventory - Configuration Manager | Microsoft Learn

You import a MOF file to extend inventory, in Configuration Manager, by using the `ImportInventoryReport` method.

### To import MOF file to extend hardware inventory

1. Connect to the site server namespace (root\sms\site\_&lt;site code&gt;).
2. Get the [SMS_InventoryReport](../../../reference/core/clients/manage/sms_inventoryreport-server-wmi-class) class.
3. Invoke the [ImportInventoryReport](../../../reference/core/clients/manage/importinventoryreport-method-in-class-sms_inventoryreport) method, passing in the *InventoryReportID*, *ImportType*, and *MofBuffer* parameters.

## Example

The following example imports a MOF file to extend inventory using the ImportInventoryReport method.

```c

public class ImportInventory{            public const string HardwareInventoryReportID = "{00000000-0000-0000-0000-000000000001}";    static void Main(string[] args)    {        if (args != null && args.Length >= 2)        {            string fileName = args[0];            string siteCode = args[1];            ImportInventoryReport(siteCode, fileName);        }        else        {            Console.WriteLine("Usage: InventoryImportExample <MofFileName> <site code>");        }        Console.WriteLine("Press any key to exit");        Console.ReadLine();    }    public static void ImportInventoryReport(string siteCode, string fileName,         string inventoryReportID = HardwareInventoryReportID,         InventoryImportType importOption = InventoryImportType.BothClassAndReport)    {        if (File.Exists(fileName)==false)        {            throw new FileNotFoundException("MOF file not found", fileName);        }        string mofToImport = File.ReadAllText(fileName);        // Get the SMS_InventoryReport class.        try        {            string scope = string.Format(@"root\sms\site_{0}",siteCode);            ManagementClass cls = new ManagementClass(scope, "SMS_InventoryReport", null);            ManagementBaseObject inParams = cls.GetMethodParameters("ImportInventoryReport");            inParams["InventoryReportID"] = inventoryReportID;            inParams["ImportType"] = (uint)importOption;            inParams["MofBuffer"] = mofToImport;            ManagementBaseObject retVal = cls.InvokeMethod("ImportInventoryReport", inParams, null);            // Get current site code.            uint resultCode = (uint)retVal["StatusCode"];            if (resultCode == 0)            {                Console.WriteLine("ImportInventoryReport for file {0} succeed ", fileName);            }            else            {                Console.WriteLine("ImportInventoryReport for file {0} failed with error code:{1} ", fileName,resultCode);            }        }        catch (ManagementException e)        {            Console.WriteLine("Failed to execute method ImportInventoryReport for file {0}: {1}", fileName, e.ToString());        }    }    public enum InventoryImportType    {        ClassOnly = 1,         ReportOnly = 2,         BothClassAndReport = 3    }}  

```

```wmimof
An example MOF file.================================[ SMS_Report (TRUE),  SMS_Group_Name ("User Account"),  SMS_Class_ID ("MICROSOFT|USER_ACCOUNT|1.0"),  Namespace ("root\\\\cimv2") ]class Win32_UserAccount : SMS_Class_Template{    [ SMS_Report (TRUE), key ]    String     Domain;    [ SMS_Report (TRUE), key ]    String     Name;    [ SMS_Report (TRUE) ]    UInt32     AccountType;    [ SMS_Report (TRUE) ]    String     Caption;    [ SMS_Report (TRUE) ]    String     Description;    [ SMS_Report (TRUE) ]    Boolean     Disabled;    [ SMS_Report (TRUE) ]    String     FullName;    [ SMS_Report (TRUE) ]    DateTime     InstallDate;    [ SMS_Report (TRUE) ]    Boolean     LocalAccount;    [ SMS_Report (TRUE) ]    Boolean     Lockout;    [ SMS_Report (TRUE) ]    Boolean     PasswordChangeable;    [ SMS_Report (TRUE) ]    Boolean     PasswordExpires;    [ SMS_Report (TRUE) ]    Boolean     PasswordRequired;    [ SMS_Report (TRUE) ]    String     SID;    [ SMS_Report (TRUE) ]    UInt8     SIDType;    [ SMS_Report (TRUE) ]    String     Status;};  
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `siteCode` | - Managed: `String` | The site code. |
| `fileName` | - Managed: `String` | The name of the MOF file to import. |
| `inventoryReportID` | - Managed: `String` | Inventory report identifier. |
| `importOption` | - Managed: `String` | Import type. Possible values are: - 1 – Class Only- 2 – Report Only- 3 – Both Class and Report |
| `mofToImport` | - Managed: `String` | The MOF content that contains the inventory class or report to import. This is the same format as the Configuration Manager 2007 sms\_def.mof file, or the file format that you export from inventory client settings. |

## Compiling the Code

This C# example requires:

### Assembly

System.Management

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../../servers/configure/role-based-administration).