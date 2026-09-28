---
layout: Conceptual
title: Configure Heartbeat Discovery - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-configure-heartbeat-discovery
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
description: Learn how to configure the Heartbeat Discovery settings by modifying the necessary site control file settings in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 3b205d75-e474-ddd3-a3de-7fc1d0cfa369
document_version_independent_id: 43e5e1af-f79e-d310-7d20-4e940cebacca
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-configure-heartbeat-discovery.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-configure-heartbeat-discovery
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-configure-heartbeat-discovery.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
platformId: 776e0502-18cf-cb75-948b-48a1509dc220
---

# Configure Heartbeat Discovery - Configuration Manager | Microsoft Learn

In Configuration Manager, you configure the Heartbeat Discovery settings by modifying the necessary site control file settings.

### To configure Heartbeat Discovery

1. Set up a connection to the SMS Provider.
2. Make a connection to the Heartbeat Discovery section of the site control file by using the `SMS_SCI_Component` class.
3. Loop through the array of available properties, making changes as needed.
4. Commit the changes to the site control file.

## Example

The following example sets the Heartbeat Discovery settings by using the `SMS_SCI_Component` class to connect to the site control file and change properties.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ConfigureHeartbeatDiscoverySettings1(swbemServices,                       _
                                         swbemContext,                        _
                                         siteCode,                            _
                                         serverName,                          _
                                         newHeartbeatSiteControlFileSchedule)

    ' Load site control file and get the SMS_SITE_CONTROL_MANAGER section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext

    Query = "SELECT * FROM SMS_SCI_Component " &                         _
    "WHERE ItemName = 'SMS_SITE_CONTROL_MANAGER|" & serverName & "' " &  _
    "AND SiteCode = '" & siteCode & "'"

    ' Get the SMS Software Update Point properties.
    Set SCIComponentSet = swbemServices.ExecQuery(Query, ,wbemFlagForwardOnly Or wbemFlagReturnImmediately, swbemContext)

    ' Only one instance is returned from the query.
    For Each SCIComponent In SCIComponentSet

        ' Display the server name.
        wscript.echo "Server: " & SCIComponent.Name

        ' Loop through the array of embedded SMS_EmbeddedProperty instances.
        For Each vProperty In SCIComponent.Props

            ' Setting: Heartbeat Site Control File Schedule.
            If vProperty.PropertyName = "Heartbeat Site Control File Schedule" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value1

                'Modify the value.
                vProperty.Value1 = newHeartbeatSiteControlFileSchedule
                wscript.echo "New value " & newHeartbeatSiteControlFileSchedule
            End If

         Next

         ' Update the component in your copy of the site control file. Get the path
         ' to the updated object, which could be used later to retrieve the instance.
          Set SCICompPath = SCIComponent.Put_(wbemChangeFlagUpdateOnly, swbemContext)

    Next

    ' Commit the change to the actual site control file.
    Set InParams = swbemServices.Get("SMS_SiteControlFile").Methods_("CommitSCF").InParameters.SpawnInstance_
    InParams.SiteCode = siteCode
    swbemServices.ExecMethod "SMS_SiteControlFile", "CommitSCF", InParams, , swbemContext

End Sub

' SEPARATE EXAMPLE TO ENABLE HEARTBEAT DISCOVERY ON THE CLIENT
Sub ConfigureHeartbeatDiscoverySettings2(swbemServices,                       _
                                         swbemContext,                        _
                                         siteCode,                            _
                                         enableDisableHeartbeatDDR)

    ' Load site control file and get the SMS_SCI_ClientConfig section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext

    Query = "SELECT * FROM SMS_SCI_ClientConfig " &   _
    "WHERE ItemName  = 'Client Properties'" & _
    "AND SiteCode = '" & siteCode & "'"

     Set SCIComponentSet = swbemServices.ExecQuery(Query, ,wbemFlagForwardOnly Or wbemFlagReturnImmediately, swbemContext)

    ' Only one instance is returned from the query.
    For Each SCIComponent In SCIComponentSet

        'Loop through the array of embedded SMS_EmbeddedProperty instances.
        For Each vProperty In SCIComponent.Props

            ' Setting: Enable Heartbeat DDR
            If vProperty.PropertyName = "Enable Heartbeat DDR" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value

                'Modify the value.
                vProperty.Value = enableDisableHeartbeatDDR
                wscript.echo "New value " & enableDisableHeartbeatDDR
            End If

        Next

        ' Update the component in your copy of the site control file. Get the path
        ' to the updated object, which could be used later to retrieve the instance.
        Set SCICompPath = SCIComponent.Put_(wbemChangeFlagUpdateOnly, swbemContext)

    Next

    ' Commit the change to the actual site control file.
    Set InParams = swbemServices.Get("SMS_SiteControlFile").Methods_("CommitSCF").InParameters.SpawnInstance_
    InParams.SiteCode = siteCode
    swbemServices.ExecMethod "SMS_SiteControlFile", "CommitSCF", InParams, , swbemContext

End Sub

```

```c

public void ConfigureHeartbeatDiscoverySettings(WqlConnectionManager connection,
                                                string siteCode,
                                                string serverName,
                                                string newHeartbeatSiteControlFileSchedule,
                                                string newEnableDisableHeartbeatDDR)
{

    try
    {
    // Change the Heartbeat Site Control File Schedule value.

        // Connect to SMS_SITE_CONTROL_MANAGER section of the site control file.
         IResultObject siteDefinition = connection.GetInstance(@"SMS_SCI_Component.FileType=2,ItemType='Component',SiteCode='" + siteCode + "',ItemName='SMS_SITE_CONTROL_MANAGER|" + serverName + "'");

        // Temporary copy of the embedded properties.
        Dictionary<string, IResultObject> embeddedProperties = siteDefinition.EmbeddedProperties;

        foreach (KeyValuePair<string, IResultObject> kvp in siteDefinition.EmbeddedProperties)
        {
            // Property: Heartbeat Site Control File Schedule
            if (kvp.Value.PropertyList["PropertyName"] == "Heartbeat Site Control File Schedule")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + embeddedProperties["Heartbeat Site Control File Schedule"]["Value1"].StringValue);

                embeddedProperties["Heartbeat Site Control File Schedule"]["Value1"].StringValue = newHeartbeatSiteControlFileSchedule;
                Console.WriteLine("New value    : " + newHeartbeatSiteControlFileSchedule);
            }
        }

        // Store the settings that have changed.
        siteDefinition.EmbeddedProperties = embeddedProperties;

        // Save the settings.
        siteDefinition.Put();

    }
    catch (SmsException ex)
    {
        Console.WriteLine();
        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);
    }

    try
    {
    // Change the Enable Heartbeat DDR value.

        // Connect to SMS_SCI_ClientConfig section of the site control file.
    IResultObject siteDefinition = connection.GetInstance(@"SMS_SCI_ClientConfig.FileType=2,ItemType='Client Configuration',SiteCode='" + siteCode + "',ItemName='Client Properties'");

        // Create temporary working copy of embedded properties.
        Dictionary<string, IResultObject> embeddedProperties = siteDefinition.EmbeddedProperties;

        foreach (KeyValuePair<string, IResultObject> kvp in siteDefinition.EmbeddedProperties)
        {
            // Setting: Enable Heartbeat DDR
            if (kvp.Value.PropertyList["PropertyName"] == "Enable Heartbeat DDR")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + kvp.Value.PropertyList["Value"]);

                // Change value using the newEnableDisableHeartbeatDDR value passed in.
                embeddedProperties["Enable Heartbeat DDR"]["Value"].StringValue = newEnableDisableHeartbeatDDR;
                Console.WriteLine("New value    : " + newEnableDisableHeartbeatDDR);
            }
        }

        // Store the settings that have changed.
        siteDefinition.EmbeddedProperties = embeddedProperties;

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
| `serverName` | - Managed: `String`- VBScript: `String` | The server name. |
| `newHeartbeatSiteControlFileSchedule` | - Managed: `String`- VBScript: `String` | The schedule defining how often the client will produce heartbeat data discovery records (DDRs). |
| - `newEnableDisableHeartbeatDDR`- `enableDisableHeartbeatDDR` | - Managed: `String`- VBScript: `String` | A value to enable or disable the heartbeat DDR. Disabled - 0 Enabled - 1 |

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

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](role-based-administration).