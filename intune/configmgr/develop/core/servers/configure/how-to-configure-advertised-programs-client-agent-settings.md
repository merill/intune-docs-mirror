---
layout: Conceptual
title: Configure Advertised Programs Client Agent Settings - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-configure-advertised-programs-client-agent-settings
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
description: Learn how to configure software distribution advertised programs client agent settings in the site control file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 7e21478f-c1ba-dfd9-9987-1d721b393bfd
document_version_independent_id: 2b8720f5-6965-3616-9ef0-6e62ae215951
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-configure-advertised-programs-client-agent-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-configure-advertised-programs-client-agent-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-configure-advertised-programs-client-agent-settings.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
platformId: 5a03a5bc-bd2c-13c5-7e2f-15e156b0f711
---

# Configure Advertised Programs Client Agent Settings - Configuration Manager | Microsoft Learn

In Configuration Manager, the site control file maintains configuration for the configuration of the site. This topic shows how to configure software distribution advertised programs client agent settings in the site control file. For more information about reading from and writing to the site control file, see [About the site control file](../../understand/about-the-configuration-manager-site-control-file).

Caution

You should be experienced in managing a site's configuration before using the SMS Provider classes to modify the site configuration. You should use caution or avoid using the `SMS_SCI_FileDefinition` and `SMS_SCI_SiteDefinition` classes altogether. These classes manage the site control file itself. You can cause significant damage to a site by changing some configurable items.

### To configure client agent settings

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Make a connection to the software distribution client component section of the site control file by using the [SMS_SCI_ClientComp](../../../reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class.
3. Loop through the array of available properties, making changes as needed.
4. Commit the property changes to the site control file.

## Example

The following example queries for specific items in the software distribution client component section of the site control file, and modifies those specific client agent settings.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ConfigureClientAgentSettings(swbemServices, swbemContext, siteToChange, enableDisableSWDClientAgent, enableDisableRequestUserPolicy, setPolicyRefreshInterval, enableDisableVisibleSignalOnAvailable, enableDisableAudibleSignalonAvailable,enableDisableCountdownSignal,setCountdownMinutes, enableDisableShowIcon)

    ' Load site control file and get SWD client component section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteToChange & """", "Refresh", , , swbemContext
    Set objSWbemInst = swbemServices.Get("SMS_SCI_ClientComp.Filetype=1,Itemtype='Client Component',Sitecode='" & siteToChange & "',ItemName='Software Distribution'", , swbemContext)

    ' Display SWD client agent settings before change.
    Wscript.Echo " "
    Wscript.Echo "Before Change"
    Wscript.Echo "-------------"

    Wscript.Echo " "
    Wscript.Echo objSWbemInst.ClientComponentName
    Wscript.Echo "Current value: " & objSWbemInst.Flags & " (0 = Disabled, 1 = Enabled)"
    Wscript.Echo " "
    objSWbemInst.Flags = enableDisableSWDClientAgent

    ' Enumerate though the property array, but display only the properties that we're specifically interested in.
    ' Note: A list of all properties could be generated by just using the following code:
    '     PropertyArray = objSwbemInst.props
    '     For i = 0 to ubound(PropertyArray)
    '        Wscript.Echo PropertyArray(i).PropertyName
    '        Wscript.Echo "Current value: " & PropertyArray(i).Value
    '     Next

    PropertyArray = objSwbemInst.props
    For i = 0 to ubound(PropertyArray)

        ' Client settings: Allow user targeted advertisement requests.
        If PropertyArray(i).PropertyName = "Request User Policy" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
            PropertyArray(i).Value = enableDisableRequestUserPolicy
        End If

        ' Client settings: Policy polling interval (minutes).
        If PropertyArray(i).PropertyName = "Policy Refresh Interval" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
            PropertyArray(i).Value = setPolicyRefreshInterval
        End If

        ' When new advertised programs are available: Display a notification message.
        If PropertyArray(i).PropertyName = "Visible Signal on Available" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
            PropertyArray(i).Value = enableDisableVisibleSignalOnAvailable
        End If

        ' When new advertised programs are available: Play a sound.
        If PropertyArray(i).PropertyName = "Audible Signal on Available" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
            PropertyArray(i).Value = enableDisableAudibleSignalonAvailable
        End If

        ' When a scheduled program is about to run: Provide a countdown.
        If PropertyArray(i).PropertyName = "Countdown Signal" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
            PropertyArray(i).Value = enableDisableCountdownSignal
        End If

        ' Countdown length (minutes).
        If PropertyArray(i).PropertyName = "Countdown Minutes" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
            PropertyArray(i).Value = setCountdownMinutes
        End If

        ' Show advertised program notification icons in the notification area.
        If PropertyArray(i).PropertyName = "Show Icon" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
            PropertyArray(i).Value = enableDisableShowIcon
        End If
    Next

    ' Save new client agent settings.
    objSWbemInst.Put_ , swbemContext
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteToChange & """", "Commit", , , swbemContext

    ' Refresh in-memory copy of the site control file and get the SWD client component section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteToChange & """", "Refresh", , , swbemContext
    Set objSWbemInst = swbemServices.Get("SMS_SCI_ClientComp.Filetype=1,Itemtype='Client Component',Sitecode='" & siteToChange & "',ItemName='Software Distribution'", , swbemContext)

    ' Display SWD client agent settings after change.

    Wscript.Echo " "
    Wscript.Echo "After Change"
    Wscript.Echo "------------"

    Wscript.Echo " "
    Wscript.Echo objSWbemInst.ClientComponentName
    Wscript.Echo "Current value: " & objSWbemInst.Flags & " (0 = Disabled, 1 = Enabled)"
    Wscript.Echo " "

    PropertyArray = objSwbemInst.props
    For i = 0 to ubound(PropertyArray)

        ' Client settings: Allow user targeted advertisement requests.
        If PropertyArray(i).PropertyName = "Request User Policy" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
        End If

        ' Client settings: Policy polling interval (minutes).
        If PropertyArray(i).PropertyName = "Policy Refresh Interval" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
        End If

        ' When new advertised programs are available: Display a notification message.
        If PropertyArray(i).PropertyName = "Visible Signal on Available" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
        End If

        ' When new advertised programs are available: Play a sound.
        If PropertyArray(i).PropertyName = "Audible Signal on Available" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
        End If

        ' When a scheduled program is about to run: Provide a countdown.
        If PropertyArray(i).PropertyName = "Countdown Signal" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
        End If

        ' Countdown length (minutes).
        If PropertyArray(i).PropertyName = "Countdown Minutes" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
        End If

        ' Show advertised program notification icons in the notification area.
        If PropertyArray(i).PropertyName = "Show Icon" Then
            Wscript.Echo PropertyArray(i).PropertyName
            Wscript.Echo "Current value: " & PropertyArray(i).Value
            Wscript.Echo " "
        End If
    Next

End Sub
```

```c
public void ConfigureSWDClientAgentSettings(WqlConnectionManager connection, string siteCode, string enableDisableSWDClientAgent, string enableDisableRequestUserPolicy, string setPolicyRefreshInterval, string enableDisableVisibleSignalOnAvailable, string enableDisableAudibleSignalonAvailable, string enableDisableCountdownSignal, string setCountdownMinutes, string enableDisableShowIcon)
{
try
{
    IResultObject siteDefinition = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Software Distribution'");

    Console.WriteLine();
    Console.WriteLine("Before Change");
    Console.WriteLine("-------------");

    // Enable software distribution to clients.
    // Set SWD client agent by setting flags value to  0 or 1 using the EnableDisableSWDClientAgent variable.
    Console.WriteLine("Software Distribution Client Agent");
    Console.WriteLine("Current value: " + siteDefinition["Flags"].StringValue + " (0 = Disabled, 1 = Enabled)");
    siteDefinition["Flags"].StringValue = enableDisableSWDClientAgent;

    foreach (KeyValuePair<string, IResultObject> kvp in siteDefinition.EmbeddedProperties)
    {
        Dictionary<string, IResultObject> embeddedProperties = siteDefinition.EmbeddedProperties; // temp copy

        // Client settings: Allow user targeted advertisement requests.
        if (kvp.Value.PropertyList["PropertyName"] == "Request User Policy")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Request User Policy"]["Value"].StringValue);
            embeddedProperties["Request User Policy"]["Value"].StringValue = enableDisableRequestUserPolicy;
        }

        // Client settings: Policy polling interval (minutes).
        if (kvp.Value.PropertyList["PropertyName"] == "Policy Refresh Interval")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Policy Refresh Interval"]["Value"].StringValue);
            embeddedProperties["Policy Refresh Interval"]["Value"].StringValue = setPolicyRefreshInterval;
        }

        // When new advertised programs are available: Display a notification message.
        if (kvp.Value.PropertyList["PropertyName"] == "Visible Signal on Available")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Visible Signal on Available"]["Value"].StringValue);
            embeddedProperties["Visible Signal on Available"]["Value"].StringValue = enableDisableVisibleSignalOnAvailable;
        }

        // When new advertised programs are available: Play a sound.
        if (kvp.Value.PropertyList["PropertyName"] == "Audible Signal on Available")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Audible Signal on Available"]["Value"].StringValue);
            embeddedProperties["Audible Signal on Available"]["Value"].StringValue = enableDisableAudibleSignalonAvailable;
        }

        // When a scheduled program is about to run: Provide a countdown.
        if (kvp.Value.PropertyList["PropertyName"] == "Countdown Signal")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Countdown Signal"]["Value"].StringValue);
            embeddedProperties["Countdown Signal"]["Value"].StringValue = enableDisableCountdownSignal;
        }

        // Countdown length (minutes).
        if (kvp.Value.PropertyList["PropertyName"] == "Countdown Minutes")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Countdown Minutes"]["Value"].StringValue);
            embeddedProperties["Countdown Minutes"]["Value"].StringValue = setCountdownMinutes;
        }

        // Show advertised program notification icons in the notification area.
        if (kvp.Value.PropertyList["PropertyName"] == "Show Icon")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Show Icon"]["Value"].StringValue);
            embeddedProperties["Show Icon"]["Value"].StringValue = enableDisableShowIcon;
        }

        // Store the settings that have changed.
        siteDefinition.EmbeddedProperties = embeddedProperties;
    }

    // Save the settings.
    siteDefinition.Put();

    // Verify change by reconnecting and getting the value again.
    IResultObject siteDefinition2 = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Software Distribution'");

    Console.WriteLine();
    Console.WriteLine("After Change");
    Console.WriteLine("-------------");

    // Enable software distribution to clients.
    Console.WriteLine("Software Distribution Client Agent");
    Console.WriteLine("Current value: " + siteDefinition2["Flags"].StringValue + " (0 = Disabled, 1 = Enabled)");

    foreach (KeyValuePair<string, IResultObject> kvp in siteDefinition2.EmbeddedProperties)
    {
        Dictionary<string, IResultObject> embeddedProperties = siteDefinition2.EmbeddedProperties; // temp copy

        // Client settings: Allow user targeted advertisement requests.
        if (kvp.Value.PropertyList["PropertyName"] == "Request User Policy")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Request User Policy"]["Value"].StringValue);
        }

        // Client settings: Policy polling interval (minutes).
        if (kvp.Value.PropertyList["PropertyName"] == "Policy Refresh Interval")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Policy Refresh Interval"]["Value"].StringValue);
        }

        // When new advertised programs are available: Display a notification message.
        if (kvp.Value.PropertyList["PropertyName"] == "Visible Signal on Available")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Visible Signal on Available"]["Value"].StringValue);
        }

        // When new advertised programs are available: Play a sound.
        if (kvp.Value.PropertyList["PropertyName"] == "Audible Signal on Available")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Audible Signal on Available"]["Value"].StringValue);
        }

        // When a scheduled program is about to run: Provide a countdown.
        if (kvp.Value.PropertyList["PropertyName"] == "Countdown Signal")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Countdown Signal"]["Value"].StringValue);
        }

        // Countdown length (minutes).
        if (kvp.Value.PropertyList["PropertyName"] == "Countdown Minutes")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Countdown Minutes"]["Value"].StringValue);
        }

        // Show advertised program notification icons in the notification area.
        if (kvp.Value.PropertyList["PropertyName"] == "Show Icon")
        {
            Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
            Console.WriteLine("Current value: " + embeddedProperties["Show Icon"]["Value"].StringValue);
        }
    }

    Console.WriteLine(" ");
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
| `siteCode``siteToChange` | - Managed: `String`- VBScript: `String` | The site code. |
| `enableDisableSWDClientAgent` | - Managed: `String`- VBScript: `String` | Flag to enable or disable the client agent. |
| `setPolicyRefreshInterval` | - Managed: `String`- VBScript: `String` | Policy polling interval, in minutes. |
| `enableDisableRequestUserPolicy` | - Managed: `String`- VBScript: `String` | Flag to enable or disable targeted advertisement requests. |
| `enableDisableVisibleSignalOnAvailable` | - Managed: `String`- VBScript: `String` | Flag to enable or disable display of a notification when new advertised programs are available. |
| `enableDisableAudibleSignalonAvailable` | - Managed: `String`- VBScript: `String` | Flag to enable or disable an audible notification when new advertised programs are available. |
| `enableDisableCountdownSignal` | - Managed: `String`- VBScript: `String` | Flag to enable or disable a countdown when a scheduled program is about to run. |
| `setCountdownMinutes` | - Managed: `String`- VBScript: `String` | Countdown length, in minutes. |
| `enableDisableShowIcon` | - Managed: `String`- VBScript: `String` | Flag to enable or disable the display of advertised program notification icons in the notification area. |

## Compiling the Code

The C# example requires:

### Namespaces

System

System.Collections.Generic

System.ComponentModel

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](role-based-administration).