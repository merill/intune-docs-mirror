---
layout: Conceptual
title: Configure Hardware Inventory Settings - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/inventory/how-to-configure-hardware-inventory-settings
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
description: Set the Hardware Inventory Client Agent settings by modifying the necessary site control file settings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 31aca8f9-0c3a-5871-5f52-78d0f1b0b363
document_version_independent_id: ea90988a-93a8-1c35-7e73-574d3b766898
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/inventory/how-to-configure-hardware-inventory-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/inventory/how-to-configure-hardware-inventory-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/inventory/how-to-configure-hardware-inventory-settings.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
platformId: 660379af-b31e-462e-ef21-e28ce3c30504
---

# Configure Hardware Inventory Settings - Configuration Manager | Microsoft Learn

You set the Hardware Inventory Client Agent settings, in Configuration Manager, by modifying the necessary site control file settings.

### To modify the Hardware Inventory Client Agent settings

1. Set up a connection to the SMS Provider.
2. Make a connection to the Hardware Inventory Client Agent section of the site control file by using the [SMS_SCI_ClientComp](../../../reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class.
3. Loop through the array of available properties, making changes as needed.
4. Commit the changes to the site control file.

## Example

The following example sets the Hardware Inventory Client Agent settings by using the [SMS_SCI_ClientComp](../../../reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class to connect to the site control file and change properties.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ConfigureHardwareInventoryClientAgentSettings(swbemServices,        _  
                                                  swbemContext,         _  
                                                  siteCode,             _  
                                                  newInventorySchedule, _  
                                                  newMIFSize,           _   
                                                  newMIFCollection)  

    ' Load site control file and get the SMS Software Update Point system resource section.  
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext  

    Query = "SELECT * FROM SMS_SCI_ClientComp " & _  
    "WHERE ClientComponentName = 'Hardware Inventory Agent' " & _  
    "AND SiteCode = '" & siteCode & "'"            

    Set SCIComponentSet = swbemServices.ExecQuery(Query, ,wbemFlagForwardOnly Or wbemFlagReturnImmediately, swbemContext)  

    ' Only one instance is returned from the query.  
    For Each SCIComponent In SCIComponentSet  

        ' Set the client agent by setting the Flags value to 0 or 1 using the enableDisableClientAgent variable.  
        wscript.echo " "  
        wscript.echo "Hardware Inventory Agent"  
        wscript.echo "Current value " &  SCIComponent.Flags  

        ' Modify the value.                  
        SCIComponent.Flags = enableDisableClientAgent  
        wscript.echo "New value " & enableDisableClientAgent  

        'Loop through the array of embedded SMS_EmbeddedProperty instances.  
        For Each vProperty In SCIComponent.Props  

            ' Setting: Inventory Schedule  
            If vProperty.PropertyName = "Inventory Schedule" Then  
                wscript.echo " "  
                wscript.echo vProperty.PropertyName  
                wscript.echo "Current value " &  vProperty.Value2                 

                'Modify the value.  
                vProperty.Value2 = newInventorySchedule  
                wscript.echo "New value " & newInventorySchedule  
            End If  

            ' Setting: Maximum 3rd Party MIF Size  
            If vProperty.PropertyName = "Maximum 3rd Party MIF Size" Then  
                wscript.echo " "  
                wscript.echo vProperty.PropertyName  
                wscript.echo "Current value " &  vProperty.Value                 

                ' Modify the value.  
                vProperty.Value = newMIFSize  
                wscript.echo "New value " & newMIFSize  
            End If  

            ' Setting: MIF Collection  
            If vProperty.PropertyName = "MIF Collection" Then  
                wscript.echo " "  
                wscript.echo vProperty.PropertyName  
                wscript.echo "Current value " &  vProperty.Value                 

                ' Modify the value.  
                vProperty.Value = newMIFCollection  
                wscript.echo "New value " & newMIFCollection  
            End If  

        Next     

        ' Update the component in your copy of the site control file. Get the path  
        'to the updated object, which could be used later to retrieve the instance.  
        Set SCICompPath = SCIComponent.Put_(wbemChangeFlagUpdateOnly, swbemContext)  

    Next  

    ' Commit the change to the actual site control file.  
    Set InParams = swbemServices.Get("SMS_SiteControlFile").Methods_("CommitSCF").InParameters.SpawnInstance_  
    InParams.SiteCode = siteCode  
    swbemServices.ExecMethod "SMS_SiteControlFile", "CommitSCF", InParams, , swbemContext  

End Sub  
```

```c

public void ConfigureHardwareInventoryClientAgentSettings(WqlConnectionManager connection,  
                                                    string siteCode,  
                                                    string enableDisableClientAgent,  
                                                    string newInventorySchedule,  
                                                    string newMIFSize,  
                                                    string newMIFCollection)  
{  
    try  
    {  
        IResultObject siteDefinition = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Hardware Inventory Agent'");  

        // Setting: Enable Client Agent  
        // Enable or disable the client agent by setting the Flags value to 0 or 1 using the enableDisableClientAgent variable.   
        Console.WriteLine();  
        Console.WriteLine("Hardware Inventory Client Agent");  
        Console.WriteLine("Current value: " + siteDefinition["Flags"].StringValue);  

        // Change value using the enableDisableClientAgent value passed in.   
        siteDefinition["Flags"].StringValue = enableDisableClientAgent;  
        Console.WriteLine("New value    : " + enableDisableClientAgent);  

        foreach (KeyValuePair<string, IResultObject> kvp in siteDefinition.EmbeddedProperties)  
        {  
            // Create temporary working copy of embedded properties.  
            Dictionary<string, IResultObject> embeddedProperties = siteDefinition.EmbeddedProperties;  

            // Setting: Inventory Schedule  
            if (kvp.Value.PropertyList["PropertyName"] == "Inventory Schedule")  
            {  
                Console.WriteLine();  
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);  
                Console.WriteLine("Current value: " + kvp.Value.PropertyList["PropertyName"]);  

                // Change value using the newInventorySchedule value passed in.   
                embeddedProperties["Inventory Schedule"]["Value2"].StringValue = newInventorySchedule;  
                Console.WriteLine("New value    : " + newInventorySchedule);  
            }  

            // Setting: Maximum 3rd Party MIF Size  
            if (kvp.Value.PropertyList["PropertyName"] == "Maximum 3rd Party MIF Size")  
            {  
                Console.WriteLine();  
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);  
                Console.WriteLine("Current value: " + kvp.Value.PropertyList["PropertyName"]);  

                // Change value using the newMIFSize value passed in.   
                embeddedProperties["Maximum 3rd Party MIF Size"]["Value"].StringValue = newMIFSize;  
                Console.WriteLine("New value    : " + newMIFSize);  
            }  

            // Setting: MIF Collection  
            if (kvp.Value.PropertyList["PropertyName"] == "MIF Collection")  
            {  
                Console.WriteLine();  
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);  
                Console.WriteLine("Current value: " + kvp.Value.PropertyList["PropertyName"]);  

                // Change value using the newMIFCollection value passed in.   
                embeddedProperties["MIF Collection"]["Value"].StringValue = newMIFCollection;  
                Console.WriteLine("New value    : " + newMIFCollection);  
            }  

            // Store the settings that have changed.  
            siteDefinition.EmbeddedProperties = embeddedProperties;  
        }  

        // Save the settings.   
        siteDefinition.Put();  

    }  

    catch (SmsException ex)  
    {  
        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);  
        throw;  
    }  

}  

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| - `connection`- `swbemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `swbemContext` | - VBScript: `SWbemContext` | A valid context object. For more information, see [How to Add a Configuration Manager Context Qualifier by Using WMI](../../understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi). |
| `siteCode` | - Managed: `String`- VBScript: `String` | The site code. |
| `enableDisableClientAgent` | - Managed: `String`- VBScript: `String` | A value to enable or disable the client agent. Disabled - 0 Enabled - 1 |
| `newInventorySchedule` | - Managed: `String`- VBScript: `String` | A value to set the inventory schedule. |
| `newMIFSize` | - Managed: `String`- VBScript: `String` | A value to set the maximum size of the hardware inventory MIF. Default is 512. |
| `newMIFCollection` | - Managed: `String`- VBScript: `String` | A value to enable or disable MIF collection. Collect: No (MIF) files - 0 NOIDMIF files - 4 IDMIF files - 8 Both NOIDMIF and IDMIF files - 12 |

## Compiling the Code

This C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../../servers/configure/role-based-administration).