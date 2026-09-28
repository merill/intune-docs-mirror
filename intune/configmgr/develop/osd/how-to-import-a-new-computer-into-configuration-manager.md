---
layout: Conceptual
title: Import a New Computer - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-import-a-new-computer-into-configuration-manager
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
description: Add a new computer directly to the Configuration Manager database by calling the ImportMachineEntry Method in Class SMS_Site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 0742d35e-41ca-bc45-c092-ba8fe342b4fe
document_version_independent_id: 4d008e46-ec8c-d623-eac8-b925747d4ab3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-import-a-new-computer-into-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-import-a-new-computer-into-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-import-a-new-computer-into-configuration-manager.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b711225c-4e25-135d-948f-1bfcffec8819
---

# Import a New Computer - Configuration Manager | Microsoft Learn

You add a new computer directly to the Configuration Manager database by calling the [ImportMachineEntry Method in Class SMS_Site](../reference/core/servers/configure/importmachineentry-method-in-class-sms_site). This can be used to deploy operating systems to computers that have not yet been discovered automatically by Configuration Manager.

Tip

You can also use the [Import-CMComputerInformation](/en-us/powershell/module/configurationmanager/import-cmcomputerinformation) PowerShell cmdlet.

You must provide the following information:

- NETBIOS computer name
- MAC address
- SMBIOS GUID

Note

The MAC address must be for a network adapter that has a driver in Windows PE. The MAC address must be in colon format. For example, `00:00:00:00:00:00`. Other formats will prevent the client from receiving policy.

You should add a newly imported computer to a collection. This allows you to immediately create advertisements for deploying operating systems to the computer.

You can associate a new computer with a reference computer. For more information, see [How to Create an Association Between Two Computers in Configuration Manager](how-to-create-an-association-between-two-computers-in-configuration-manager).

### To add a new computer

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Call the [ImportMachineEntry Method in Class SMS_Site](../reference/core/servers/configure/importmachineentry-method-in-class-sms_site).
3. Add the resource identifier you get from ImportMachineEntry to a collection.

## Example

The following example method adds a new computer to Configuration Manager. The [ImportMachineEntry Method in Class SMS_Site](../reference/core/servers/configure/importmachineentry-method-in-class-sms_site) is used to import the computer. Then, the computer is added to a custom collection. "All Systems" collection.

Important

In previous version of this example, the computer was added to the "All Systems" collection. It is no longer possible to modify the built-in collections, use a custom collection instead.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub AddNewComputer (connection, netBiosName, smBiosGuid, macAddress)

    Dim inParams
    Dim outParams
    Dim siteClass
    Dim collection
    Dim collectionRule

    If (IsNull(smBiosGuid) = True) And (IsNull(macAddress) = True) Then
        WScript.Echo "smBiosGuid or macAddress must be defined"
        Exit Sub
    End If

    If IsNull(macAddress) = False Then
        macAddress = Replace(macAddress,"-",":")
    End If

    ' Obtain an InParameters object specific
    ' to the method.

    Set siteClass = connection.Get("SMS_Site")
    Set inParams = siteClass.Methods_("ImportMachineEntry"). _
        inParameters.SpawnInstance_()

    ' Add the input parameters.
    inParams.Properties_.Item("MACAddress") =  macAddress
    inParams.Properties_.Item("NetbiosName") =  netBiosName
    inParams.Properties_.Item("OverwriteExistingRecord") =  False
    inParams.Properties_.Item("SMBIOSGUID") =  smBiosGuid

    ' Add the computer.
    Set outParams = connection.ExecMethod("SMS_Site", "ImportMachineEntry", inParams)

   ' Add the computer to the all systems collection.
   set collection = connection.Get("SMS_Collection.CollectionID='ABC0000A'")

   set collectionRule=connection.Get("SMS_CollectionRuleDirect").SpawnInstance_

   collectionRule.ResourceClassName="SMS_R_System"
   collectionRule.ResourceID= outParams.ResourceID

   collection.AddMembershipRule collectionRule

End Sub
```

```c
public int AddNewComputer(
    WqlConnectionManager connection,
    string netBiosName,
    string smBiosGuid,
    string macAddress)
{
    try
    {
        if (smBiosGuid == null && macAddress == null)
        {
            throw new ArgumentNullException("smBiosGuid or macAddress must be defined");
        }

        // Reformat macAddress to : separator.
        if (string.IsNullOrEmpty(macAddress) == false)
        {
            macAddress = macAddress.Replace("-", ":");
        }

        // Create the computer.
        Dictionary<string, object> inParams = new Dictionary<string, object>();
        inParams.Add("NetbiosName", netBiosName);
        inParams.Add("SMBIOSGUID", smBiosGuid);
        inParams.Add("MACAddress", macAddress);
        inParams.Add("OverwriteExistingRecord", false);

        IResultObject outParams = connection.ExecuteMethod(
            "SMS_Site",
            "ImportMachineEntry",
            inParams);

        // Add to All System collection.
        IResultObject collection = connection.GetInstance("SMS_Collection.collectionId='ABC0000A'");
        IResultObject collectionRule = connection.CreateEmbeddedObjectInstance("SMS_CollectionRuleDirect");
        collectionRule["ResourceClassName"].StringValue = "SMS_R_System";
        collectionRule["ResourceID"].IntegerValue = outParams["ResourceID"].IntegerValue;

        Dictionary<string, object> inParams2 = new Dictionary<string, object>();
        inParams2.Add("collectionRule", collectionRule);

        collection.ExecuteMethod("AddMembershipRule", inParams2);

        return outParams["ResourceID"].IntegerValue;
    }
    catch (SmsException e)
    {
        Console.WriteLine("failed to add the computer" + e.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | - A valid connection to the SMS Provider. |
| `netBiosName` | - Managed: `String`- VBScript: `String` | - The computer NETBIOS name. |
| `smBiosGuid` | - Managed: `String`- VBScript: `String` | The SMBIOS GUID for the computer. |
| `MacAddress` | - Managed: `String`- VBScript: `String` | The MAC address for the computer in the following format: `00:00:00:00:00:00`. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).