---
layout: Conceptual
title: Configure the WSUS Settings - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-configure-the-wsus-settings
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
description: Windows Server Update Services (WSUS) component settings are configured in Configuration Manager by modifying the site control file.
locale: en-us
document_id: f26e9bd4-9374-81ed-4501-06e34eded33d
document_version_independent_id: 28fc9244-1ebc-90fa-152c-766f77abbbec
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/how-to-configure-the-wsus-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/how-to-configure-the-wsus-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/how-to-configure-the-wsus-settings.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: e6fe30a9-a5c5-27f0-464e-c889c865ccba
---

# Configure the WSUS Settings - Configuration Manager | Microsoft Learn

You configure the Windows Server Update Services (WSUS) component settings, in Configuration Manager, by modifying the site control file. For more information, see [Windows Server Update Services](/en-us/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus).

### To configure WSUS settings

1. Set up a connection to the SMS Provider.
2. Make a connection to the WSUS Configuration Manager component section of the site control file by using the [SMS_SCI_Component](../reference/core/servers/configure/sms_sci_component-server-wmi-class) class.
3. Loop through the array of available properties, making changes as needed.
4. Commit the property changes to the site control file.

## Example

The following example method configures various Windows Server Update Services (WSUS) component settings by using the [SMS_SCI_Component](../reference/core/servers/configure/sms_sci_component-server-wmi-class) class to connect to the site control file and change properties.

Note

For more information, see [Prepare for software updates management](../../sum/get-started/prepare-for-software-updates-management).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

Sub ConfigureWSUSSettings(swbemServices,         _
                          swbemContext,          _
                          siteCode,              _
                          newDefaultWSUSIISPort, _
                          newSSLDefaultWSUS,     _
                          newDefaultWSUSIISSSLPort)

    ' Load site control file and get the SMS_WSUS_CONFIGURATION_MANAGER component section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext

    Query = "SELECT * FROM SMS_SCI_Component " & _
            "WHERE ComponentName = 'SMS_WSUS_CONFIGURATION_MANAGER' " & _
            "AND SiteCode = '" & siteCode & "'"

    Set SCIComponentSet = swbemServices.ExecQuery(Query, ,wbemFlagForwardOnly Or wbemFlagReturnImmediately, swbemContext)

    ' Only one instance is returned from the query.
    For Each SCIComponent In SCIComponentSet

        ' Loop through the array of embedded SMS_EmbeddedProperty instances.
        For Each vProperty In SCIComponent.Props

            ' Display the WSUS server name.
            If vProperty.PropertyName = "DefaultWSUS" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName & " Server: " & vProperty.Value2
            End If

            ' Setting: DefaultWSUSIISPort.
            If vProperty.PropertyName = "DefaultWSUSIISPort" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value

                ' Modify the value.
                vProperty.Value = newDefaultWSUSIISPort
                wscript.echo "New value " & newDefaultWSUSIISPort
            End If

            ' Setting: SSLDefaultWSUS.
            If vProperty.PropertyName = "SSLDefaultWSUS" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value

                ' Modify the value.
                vProperty.Value = newSSLDefaultWSUS
                wscript.echo "New value " & newSSLDefaultWSUS
            End If

            ' Setting: DefaultWSUSIISSSLPort.
            If vProperty.PropertyName = "DefaultWSUSIISSSLPort" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value

                ' Modify the value.
                vProperty.Value = newDefaultWSUSIISSSLPort
                wscript.echo "New value " & newDefaultWSUSIISSSLPort
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

public void ConfigureWSUSSettings(WqlConnectionManager connection,
                                    string siteCode,
                                    string SUPServerName,
                                    string newDefaultWSUSIISPort,
                                    string newSSLDefaultWSUS,
                                    string newDefaultWSUSIISSSLPort)
{
    try
    {
        // Connect to SMS_WSUS_CONFIGURATION_MANAGER section of the site control file.
        IResultObject siteDefinition = connection.GetInstance(@"SMS_SCI_Component.FileType=2,ItemType='Component',SiteCode='" + siteCode + "',ItemName='SMS_WSUS_CONFIGURATION_MANAGER|" + SUPServerName + "'");
        foreach (KeyValuePair<string, IResultObject> kvp in siteDefinition.EmbeddedProperties)
        {
            // Temporary copy of the embedded properties.
            Dictionary<string, IResultObject> embeddedProperties = siteDefinition.EmbeddedProperties;

            // Display the WSUS server name.
            if (kvp.Value.PropertyList["PropertyName"] == "DefaultWSUS")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"] + " Server");
                Console.WriteLine("Server name: " + embeddedProperties["DefaultWSUS"]["Value2"].StringValue);
            }

            // Setting: DefaultWSUSIISPort.
            if (kvp.Value.PropertyList["PropertyName"] == "DefaultWSUSIISPort")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + embeddedProperties["DefaultWSUSIISPort"]["Value"].StringValue);

                // Change the value by using the newDefaultWSUSIISPort value passed that is in.
                embeddedProperties["DefaultWSUSIISPort"]["Value"].StringValue = newDefaultWSUSIISPort;
                Console.WriteLine("New value    : " + newDefaultWSUSIISPort);
            }

            // Setting: SSLDefaultWSUS.
            if (kvp.Value.PropertyList["PropertyName"] == "SSLDefaultWSUS")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + embeddedProperties["SSLDefaultWSUS"]["Value"].StringValue);

                // Change the value by using the newSSLDefaultWSUS value that is passed in.
                embeddedProperties["SSLDefaultWSUS"]["Value"].StringValue = newSSLDefaultWSUS;
                Console.WriteLine("New value    : " + newSSLDefaultWSUS);
            }

            // Setting: DefaultWSUSIISSSLPort.
            if (kvp.Value.PropertyList["PropertyName"] == "DefaultWSUSIISSSLPort")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + embeddedProperties["DefaultWSUSIISSSLPort"]["Value"].StringValue);

                // Change the value by using the newDefaultWSUSIISSSLPort value that is passed in.
                embeddedProperties["DefaultWSUSIISSSLPort"]["Value"].StringValue = newDefaultWSUSIISSSLPort;
                Console.WriteLine("New value    : " + newDefaultWSUSIISSSLPort);
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
| `SUPServerName` | - Managed: `String`- VBScript: `String` | The name of the software update point server. |
| `newDefaultWSUSIISPort` | - Managed: `String`- VBScript: `String` | The new default WSUS Internet Information Services (IIS) port. |
| `newSSLDefaultWSUS` | - Managed: `String`- VBScript: `String` | Determines whether to use Secure Sockets Layer (SSL). |
| `newDefaultWSUSIISSSLPort` | - Managed: `String`- VBScript: `String` | Identifies the default WSUS IIS SSL port. |

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