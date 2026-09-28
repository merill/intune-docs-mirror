---
layout: Conceptual
title: Configure Remote Tools Settings - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/remote-control/how-to-configure-remote-tools-settings
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
description: Learn how to use the Remote Tools Client Agent settings by modifying the necessary site control file settings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: e7f2b6bb-b640-475f-f128-fa4df478053a
document_version_independent_id: eceb1800-20ea-8bda-fe20-94d40b8f8994
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/remote-control/how-to-configure-remote-tools-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/remote-control/how-to-configure-remote-tools-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/remote-control/how-to-configure-remote-tools-settings.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
platformId: 2f4c441b-b6f5-816d-c50e-13e8da8e764a
---

# Configure Remote Tools Settings - Configuration Manager | Microsoft Learn

In Configuration Manager, you set the Remote Tools Client Agent settings by modifying the necessary site control file settings.

### To configure Remote Tools settings

1. Set up a connection to the SMS Provider.
2. Make a connection to the Remote Tools Client Agent section of the site control file by using the `SMS_SCI_ClientComp` class.
3. Loop through the array of available properties, making changes as needed.
4. Commit the changes to the site control file.

## Example

The following example sets the Remote Tools Client Agent settings by using the `SMS_SCI_ClientComp` class to connect to the site control file and change properties.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ConfigureRemoteControlClientAgentSettings(swbemServices,            _  
                                              swbemContext,             _  
                                              siteCode,                 _  
                                              enableDisableClientAgent, _  
                                              newPermissionRequired,    _   
                                              newVisibleSignal,         _  
                                              newAudibleSignal)  

    ' Load the site control file and get the remote tools client agent section.  
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext  

    Query = "SELECT * FROM SMS_SCI_ClientComp " & _  
    "WHERE ClientComponentName = 'Remote Control' " & _  
    "AND SiteCode = '" & siteCode & "'"            

    Set SCIComponentSet = swbemServices.ExecQuery(Query, ,wbemFlagForwardOnly Or wbemFlagReturnImmediately, swbemContext)  

    ' Only one instance is returned from the query.  
    For Each SCIComponent In SCIComponentSet  

        ' Set the client agent by setting the Flags value to 0 or 1 using the enableDisableClientAgent variable.  
        wscript.echo " "  
        wscript.echo "Remote Control Agent"  
        wscript.echo "Current value " &  SCIComponent.Flags  

        ' Modify the value.                  
        SCIComponent.Flags = enableDisableClientAgent  
        wscript.echo "New value " & enableDisableClientAgent  

        ' Loop through the array of embedded SMS_EmbeddedProperty instances.  
        For Each vProperty In SCIComponent.Props  

            ' Setting: Permission Required  
            If vProperty.PropertyName = "Permission Required" Then  
                wscript.echo " "  
                wscript.echo vProperty.PropertyName  
                wscript.echo "Current value " &  vProperty.Value                 

                'Modify the value.  
                vProperty.Value = newPermissionRequired  
                wscript.echo "New value " & newPermissionRequired  
            End If  

            ' Setting: Visible Signal  
            If vProperty.PropertyName = "Visible Signal" Then  
                wscript.echo " "  
                wscript.echo vProperty.PropertyName  
                wscript.echo "Current value " &  vProperty.Value                 

                ' Modify the value.  
                vProperty.Value = newVisibleSignal  
                wscript.echo "New value " & newVisibleSignal  
            End If  

            ' Setting: Audible Signal  
            If vProperty.PropertyName = "Audible Signal" Then  
                wscript.echo " "  
                wscript.echo vProperty.PropertyName  
                wscript.echo "Current value " &  vProperty.Value                 

                ' Modify the value.  
                vProperty.Value = newAudibleSignal  
                wscript.echo "New value " & newAudibleSignal  
            End If  

        Next     

             ' Update the component in your copy of the site control file. Get the path  
             ' to the updated object, which could be used later to retrieve the instance.  
             Set SCICompPath = SCIComponent.Put_(wbemChangeFlagUpdateOnly, swbemContext)  
    Next  

    'Commit the change to the actual site control file.  
    Set InParams = swbemServices.Get("SMS_SiteControlFile").Methods_("CommitSCF").InParameters.SpawnInstance_  
    InParams.SiteCode = siteCode  
    swbemServices.ExecMethod "SMS_SiteControlFile", "CommitSCF", InParams, , swbemContext  

End Sub  

```

```c

public void ConfigureRemoteControlClientAgentSettings(WqlConnectionManager connection,  
                                                      string siteCode,  
                                                      string enableDisableRemoteControlClientAgent,  
                                                      string newPermissionRequired,  
                                                      string newVisibleSignal,  
                                                      string newAudibleSignal)  
{  
    try  
    {  
        IResultObject siteDefinition = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Remote Control'");  

        // Setting: Enable Remote Control Client Agent  
        // Set Remote Control client agent by setting flags value to  0 or 1 using the EnableDisableRemoteControlClientAgent variable.   
        Console.WriteLine();  
        Console.WriteLine("Remote Control Client Agent");  
        Console.WriteLine("Current value: " + siteDefinition["Flags"].StringValue);  

        // Change value using the enableDisableRemoteControlClientAgent value passed in.   
        siteDefinition["Flags"].StringValue = enableDisableRemoteControlClientAgent;  
        Console.WriteLine("New value    : " + enableDisableRemoteControlClientAgent);  

        foreach (KeyValuePair<string, IResultObject> kvp in siteDefinition.EmbeddedProperties)  
        {  

            // Create temporary working copy of embedded properties.  
            Dictionary<string, IResultObject> embeddedProperties = siteDefinition.EmbeddedProperties;  

            // Setting: Permission Required.  
            if (kvp.Value.PropertyList["PropertyName"] == "Permission Required")  
            {  
                Console.WriteLine();  
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);  
                Console.WriteLine("Current value: " + embeddedProperties[kvp.Value.PropertyList["PropertyName"]]["Value"].StringValue);  

                // Change value using the newPermissionRequired value passed in.   
                embeddedProperties[kvp.Value.PropertyList["PropertyName"]]["Value"].StringValue = newPermissionRequired;  
                Console.WriteLine("New value    : " + newPermissionRequired);  
            }  

            // Setting: Visible Signal.  
            if (kvp.Value.PropertyList["PropertyName"] == "Visible Signal")  
            {  
                Console.WriteLine();  
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);  
                Console.WriteLine("Current value: " + embeddedProperties[kvp.Value.PropertyList["PropertyName"]]["Value"].StringValue);  

                // Change value using the newScanSchedule value passed in.   
                embeddedProperties[kvp.Value.PropertyList["PropertyName"]]["Value"].StringValue = newVisibleSignal;  
                Console.WriteLine("New value    : " + newVisibleSignal);  
            }  

            // Setting: Audible Signal.  
            if (kvp.Value.PropertyList["PropertyName"] == "Audible Signal")  
            {  
                Console.WriteLine();  
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);  
                Console.WriteLine("Current value: " + embeddedProperties[kvp.Value.PropertyList["PropertyName"]]["Value"].StringValue);  

                // Change value using the newAudibleSignal value passed in.   
                embeddedProperties[kvp.Value.PropertyList["PropertyName"]]["Value"].StringValue = newAudibleSignal;  
                Console.WriteLine("New value    : " + newAudibleSignal);  
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
| `connection``swbemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `swbemContext` | - VBScript: `SWbemContext` | A valid context object. For more information, see [How to Add a Configuration Manager Context Qualifier by Using WMI](../../understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi). |
| `siteCode` | - Managed: `String`- VBScript: `String` | The site code. |
| - Managed: `enableDisableRemoteControlClientAgent`- VBScript: `enableDisableClientAgent` | - Managed: `String`- VBScript: `String` | Determines whether the Remote Tools Client Agent is enabled or disabled. 0 - disabled 1 - enabled |
| `newPermissionRequired` | - Managed: `String`- VBScript: `String` | Determines whether permission is required to remote control. 0 - not required 1 - required |
| `newVisibleSignal` | - Managed: `String`- VBScript: `String` | Determines whether the visible signal is enabled or disabled. 0 - disabled 1 - enabled |
| `newAudibleSignal` | - Managed: `String`- VBScript: `String` | Determines whether the audible signal is enabled or disabled. 0 - disabled 1 - enabled |

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