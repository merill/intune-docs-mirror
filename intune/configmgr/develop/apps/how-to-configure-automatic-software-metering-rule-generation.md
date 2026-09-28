---
layout: Conceptual
title: How to Configure Automatic Software Metering Rule Generation - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-configure-automatic-software-metering-rule-generation
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
description: You configure Automatic Software Metering Rule Generation settings, in Configuration Manager, by modifying the site control file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 10c06dbb-1ca9-53e2-810b-ef4a3101f12d
document_version_independent_id: bb0d2059-8f3e-9376-4503-0415825fd809
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-configure-automatic-software-metering-rule-generation.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-configure-automatic-software-metering-rule-generation
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-configure-automatic-software-metering-rule-generation.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
platformId: 6166bfe7-8f21-084c-f4ae-c2f971aed2be
---

# How to Configure Automatic Software Metering Rule Generation - Configuration Manager | Microsoft Learn

You configure Automatic Software Metering Rule Generation settings, in Configuration Manager, by modifying the site control file.

Important

This setting is shared across the whole hierarchy, and only can be configured on the CAS or a standalone primary site.

### To configure automatic software metering rule generation

1. Set up a connection to the SMS Provider.
2. Make a connection to the Software Metering Client Agent section of the site control file by using the [SMS_SCI_ClientComp](../reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class.
3. Loop through the array of available properties, making changes as needed.
4. Commit the property changes to the site control file.

## Example

The following example method configures various Software Metering Rule Generation settings by using the [SMS_SCI_ClientComp](../reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class to connect to the site control file and change properties.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

Sub ConfigureAutomaticSWMRuleGeneration(swbemServices,                  _
                                        swbemContext,                   _
                                        siteCode,                       _
                                        enableAutoCreateDisabledRule,   _
                                        newAutoCreatePercentage,        _
                                        newAutoCreateThreshold)

    ' Load site control file and get the SMS_SCI_ClientComp section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext

    Query = "SELECT * FROM SMS_SCI_ClientComp " &   _
    "WHERE ClientComponentName  = 'Software Metering Agent'" & _
    "AND SiteCode = '" & siteCode & "'"

     Set SCIComponentSet = swbemServices.ExecQuery(Query, ,wbemFlagForwardOnly Or wbemFlagReturnImmediately, swbemContext)

    ' Only one instance is returned from the query.
    For Each SCIComponent In SCIComponentSet

        'Loop through the array of embedded SMS_EmbeddedProperty instances.
        For Each vProperty In SCIComponent.Props

            ' Setting: Auto Create Disabled Rule
            If vProperty.PropertyName = "Auto Create Disabled Rule" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value

                'Modify the value.
                vProperty.Value = enableAutoCreateDisabledRule
                wscript.echo "New value " & enableAutoCreateDisabledRule
            End If

            ' Setting: Auto Create Percentage
            If vProperty.PropertyName = "Auto Create Percentage" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value

                ' Modify the value.
                vProperty.Value = newAutoCreatePercentage
                wscript.echo "New value " & newAutoCreatePercentage
            End If

            ' Setting: Auto Create Threshold
            If vProperty.PropertyName = "Auto Create Threshold" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value

                ' Modify the value.
                vProperty.Value = newAutoCreateThreshold
                wscript.echo "New value " & newAutoCreateThreshold
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

public void ConfigureAutomaticSWMRuleGeneration(WqlConnectionManager connection,
                                                string siteCode,
                                                string enableAutoCreateDisabledRule,
                                                string newAutoCreatePercentage,
                                                string newAutoCreateThreshold)
{
    try
    {
        IResultObject siteDefinition = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Software Metering Agent'");

        foreach (KeyValuePair<string, IResultObject> kvp in siteDefinition.EmbeddedProperties)
        {
            // Create temporary working copy of embedded properties.
            Dictionary<string, IResultObject> embeddedProperties = siteDefinition.EmbeddedProperties;

            //Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);

            // Setting: Auto Create Disabled Rule
            if (kvp.Value.PropertyList["PropertyName"] == "Auto Create Disabled Rule")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + embeddedProperties["Auto Create Disabled Rule"]["Value"].StringValue);

                // Change value using the enableAutoCreateDisabledRule value passed in.
                embeddedProperties["Auto Create Disabled Rule"]["Value"].StringValue = enableAutoCreateDisabledRule;
                Console.WriteLine("New value    : " + enableAutoCreateDisabledRule);
            }

            // Setting: Auto Create Percentage
            if (kvp.Value.PropertyList["PropertyName"] == "Auto Create Percentage")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + embeddedProperties["Auto Create Percentage"]["Value"].StringValue);

                // Change value using the newAutoCreatePercentage value passed in.
                embeddedProperties["Auto Create Percentage"]["Value"].StringValue = newAutoCreatePercentage;
                Console.WriteLine("New value    : " + newAutoCreatePercentage);
            }

            // Setting: Auto Create Threshold
            if (kvp.Value.PropertyList["PropertyName"] == "Auto Create Threshold")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + embeddedProperties["Auto Create Threshold"]["Value"].StringValue);

                // Change value using the newAutoCreateThreshold value passed in.
                embeddedProperties["Auto Create Threshold"]["Value"].StringValue = newAutoCreateThreshold;
                Console.WriteLine("New value    : " + newAutoCreateThreshold);
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
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `swbemContext` | - VBScript: `SWbemContext` | A valid context object. For more information, see [How to Add a Configuration Manager Context Qualifier by Using WMI](../core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi). |
| `siteCode` | - Managed: `String`- VBScript: `String` | The site code. |
| `enableAutoCreateDisabledRule` | - Managed: `String`- VBScript: `String` | Enables or disables Software Metering auto rule creation. - 0 - Disabled- 1 - Enabled |
| `newAutoCreatePercentage` | - Managed: `String`- VBScript: `String` | Sets the auto creation percentage. 0 - 100 |
| `newAutoCreateThreshold` | - Managed: `String`- VBScript: `String` | Sets the auto creation threshold. |

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

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).