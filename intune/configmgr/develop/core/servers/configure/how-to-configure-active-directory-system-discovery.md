---
layout: Conceptual
title: Configure Active Directory System Discovery - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-configure-active-directory-system-discovery
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
description: In Configuration Manager, you configure the Active Directory System Discovery settings by modifying the necessary site control file settings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d7e498b6-bb50-89c6-bb1e-8e26251cfe09
document_version_independent_id: 3f669a7b-506f-b1f9-0214-85b1196a045e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-configure-active-directory-system-discovery.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-configure-active-directory-system-discovery
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-configure-active-directory-system-discovery.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: b3cd97fb-4a43-20f6-c07a-93bba5c9f0ec
---

# Configure Active Directory System Discovery - Configuration Manager | Microsoft Learn

You configure the Active Directory System Discovery settings, in Configuration Manager, by modifying the necessary site control file settings.

### To configure Active Directory System Discovery

1. Set up a connection to the SMS Provider.
2. Make a connection to the Active Directory System Discovery section of the site control file by using the `SMS_SCI_Component` class.
3. Loop through the array of available properties, making changes as needed.
4. Commit the changes to the site control file.

## Example

The following example sets the Active Directory System Discovery settings by using the `SMS_SCI_Component` class to connect to the site control file and change properties.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ConfigureADSystemDiscoverySettings(swbemServices,          _
                                      swbemContext,            _
                                      siteCode,                _
                                      serverName,              _
                                      newStartupSchedule,      _
                                      enableDisableDiscovery)

    ' Load site control file and get the SMS_AD_SYSTEM_DISCOVERY_AGENT section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext

    Query = "SELECT * FROM SMS_SCI_Component " &                         _
    "WHERE ItemName = 'SMS_AD_SYSTEM_DISCOVERY_AGENT|" & serverName & "' " &  _
    "AND SiteCode = '" & siteCode & "'"

    ' Get the SMS_AD_SYSTEM_DISCOVERY_AGENT properties.
    Set SCIComponentSet = swbemServices.ExecQuery(Query, ,wbemFlagForwardOnly Or wbemFlagReturnImmediately, swbemContext)

    ' Only one instance is returned from the query.
    For Each SCIComponent In SCIComponentSet

        ' Display the server name.
        wscript.echo "Server: " & SCIComponent.Name

        ' Loop through the array of embedded SMS_EmbeddedProperty instances.
        For Each vProperty In SCIComponent.Props

            ' Setting: Startup Schedule
            If vProperty.PropertyName = "Startup Schedule" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value1

                ' Modify the value.
                vProperty.Value1 = newStartupSchedule
                wscript.echo "New value " & newStartupSchedule
            End If

            ' Setting: SETTINGS
            If vProperty.PropertyName = "SETTINGS" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value1

                ' Modify the value.
                vProperty.Value1 = enableDisableDiscovery
                wscript.echo "New value " & enableDisableDiscovery
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

public void ConfigureADSystemDiscoverySettings(WqlConnectionManager connection,
                                               string siteCode,
                                               string serverName,
                                               string newStartupSchedule,
                                               string enableDisableDiscovery)
{
    try
    {
        // Connect to SMS_AD_SYSTEM_DISCOVERY_AGENT section of the site control file.
        IResultObject siteDefinition = connection.GetInstance(@"SMS_SCI_Component.FileType=2,ItemType='Component',SiteCode='" + siteCode + "',ItemName='SMS_AD_SYSTEM_DISCOVERY_AGENT|" + serverName + "'");

        // Create temporary copy of the embedded properties.
        Dictionary<string, IResultObject> embeddedProperties = siteDefinition.EmbeddedProperties;

        // Enumerate through the embedded properties and makes changes as needed.
        foreach (KeyValuePair<string, IResultObject> kvp in siteDefinition.EmbeddedProperties)
        {
            // Setting: Startup Schedule
            if (kvp.Value.PropertyList["PropertyName"] == "Startup Schedule")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + kvp.Value.PropertyList["Value1"]);

                // Change value using the newStartupSchedule value passed in.
                embeddedProperties["Startup Schedule"]["Value1"].StringValue = newStartupSchedule;
                Console.WriteLine("New value    : " + newStartupSchedule);
            }

            // Setting: SETTINGS
            if (kvp.Value.PropertyList["PropertyName"] == "SETTINGS")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + kvp.Value.PropertyList["Value1"]);

                // Change value using the newEnableHeartbeatDDR value passed in.
                embeddedProperties["SETTINGS"]["Value1"].StringValue = enableDisableDiscovery;
                Console.WriteLine("New value    : " + enableDisableDiscovery);
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
| `newStartupSchedule` | - Managed: `String`- VBScript: `String` | The new schedule. |
| `enableDisableDiscovery` | - Managed: `String`- VBScript: `String` | A value to enable or disable the discovery method. Disabled - INACTIVE Enabled - ACTIVE |

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