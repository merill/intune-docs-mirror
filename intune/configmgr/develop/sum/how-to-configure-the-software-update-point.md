---
layout: Conceptual
title: Configure the Software Update Point - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-configure-the-software-update-point
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
description: You configure the software update point, in Configuration Manager, by modifying the site control file settings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 8c26dfc5-8c0f-ee94-3ce9-523fcb536003
document_version_independent_id: c6fa800f-4673-5732-9da0-1b58dcae4ff9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/how-to-configure-the-software-update-point.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/how-to-configure-the-software-update-point
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/how-to-configure-the-software-update-point.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
platformId: 4ad6e88b-e6aa-d783-7d12-c435551a0652
---

# Configure the Software Update Point - Configuration Manager | Microsoft Learn

You configure the software update point, in Configuration Manager, by modifying the site control file settings.

### To configure a software update point

1. Set up a connection to the SMS Provider.
2. Make a connection to the software update point resources section of the site control file by using the [SMS_SCI_SysResUse](../reference/core/servers/configure/sms_sci_sysresuse-server-wmi-class) class.
3. Loop through the array of available properties, making changes as needed.
4. Commit the property changes to the site control file.

## Example

The following example method configures various software update point settings by using the `SMS_SCI_SysResUse` class to connect to the site control file and change the software update point properties.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

Sub ConfigureSoftwareUpdatePoint(swbemServices,          _
                                 swbemContext,           _
                                 siteCode,               _
                                 newUseProxy,            _
                                 newProxyName,           _
                                 newProxyServerPort,     _
                                 newAnonymousProxyAccess)

    ' Load site control file and get software update point section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext

    Query = "SELECT * FROM SMS_SCI_SysResUse " & _
            "WHERE RoleName = 'SMS Software Update Point' " & _
            "AND SiteCode = '" & siteCode & "'"

    Set SCIComponentSet = swbemServices.ExecQuery(Query, ,wbemFlagForwardOnly Or wbemFlagReturnImmediately, swbemContext)

    ' Only one instance is returned from the query.
    For Each SCIComponent In SCIComponentSet

         ' Display the SUP server name.
         wscript.echo "SUP Server: " & SCIComponent.NetworkOSPath

        ' Loop through the array of embedded SMS_EmbeddedProperty instances.
        For Each vProperty In SCIComponent.Props

            ' Setting: UseProxy.
            If vProperty.PropertyName = "UseProxy" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value

                ' Modify the value.
                vProperty.Value = newUseProxy
                wscript.echo "New value " & newUseProxy
            End If

            ' Setting: ProxyName.
            If vProperty.PropertyName = "ProxyName" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value2

                ' Modify the value.
                vProperty.Value2 = newProxyName
                wscript.echo "New value " & newProxyName
            End If

            ' Setting: ProxyServerPort.
            If vProperty.PropertyName = "ProxyServerPort" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value

                ' Modify the value.
                vProperty.Value = newProxyServerPort
                wscript.echo "New value " & newProxyServerPort
            End If

            ' Setting: AnonymousProxyAccess.
            If vProperty.PropertyName = "AnonymousProxyAccess" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value

                ' Modify the value.
                vProperty.Value = newAnonymousProxyAccess
                wscript.echo "New value " & newAnonymousProxyAccess
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

public void ConfigureSoftwareUpdatePoint(WqlConnectionManager connection,
                                    string siteCode,
                                    string SUPServerName,
                                    string newUseProxy,
                                    string newProxyName,
                                    string newProxyServerPort,
                                    string newAnonymousProxyAccess)
{
    try
    {

        IResultObject siteDefinition = connection.GetInstance("SMS_SCI_SysResUse.FileType=2,ItemName='[\"Display=\\\\" + SUPServerName + "\\\"]MSWNET:[\"SMS_SITE=" + siteCode + "\"]\\\\" + SUPServerName + "\\,SMS Software Update Point',ItemType='System Resource Usage',SiteCode='" + siteCode + "'");

        foreach (KeyValuePair<string, IResultObject> kvp in siteDefinition.EmbeddedProperties)
        {
            // Temporary copy of the embedded properties.
            Dictionary<string, IResultObject> embeddedProperties = siteDefinition.EmbeddedProperties;

            // Setting: UseProxy.
            if (kvp.Value.PropertyList["PropertyName"] == "UseProxy")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + embeddedProperties["UseProxy"]["Value"].StringValue);

                // Change the value by using the newUseProxy value that is passed in.
                embeddedProperties["UseProxy"]["Value"].StringValue = newUseProxy;
                Console.WriteLine("New value    : " + newUseProxy);
            }

            // Setting: ProxyName.
            if (kvp.Value.PropertyList["PropertyName"] == "ProxyName")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + embeddedProperties["ProxyName"]["Value2"].StringValue);

                // Change the value by using the newProxyName value that is passed in.
                embeddedProperties["ProxyName"]["Value2"].StringValue = newProxyName;
                Console.WriteLine("New value    : " + newProxyName);
            }

            // Setting: ProxyServerPort.
            if (kvp.Value.PropertyList["PropertyName"] == "ProxyServerPort")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + embeddedProperties["ProxyServerPort"]["Value"].StringValue);

                // Change the value by using the newProxyServerPort value that is passed in.
                embeddedProperties["ProxyServerPort"]["Value"].StringValue = newProxyServerPort;
                Console.WriteLine("New value    : " + newProxyServerPort);
            }

            // Setting: AnonymousProxyAccess.
            if (kvp.Value.PropertyList["PropertyName"] == "AnonymousProxyAccess")
            {
                Console.WriteLine();
                Console.WriteLine(kvp.Value.PropertyList["PropertyName"]);
                Console.WriteLine("Current value: " + embeddedProperties["AnonymousProxyAccess"]["Value"].StringValue);

                // Change the value by using the newAnonymousProxyAccess value that is passed in.
                embeddedProperties["AnonymousProxyAccess"]["Value"].StringValue = newAnonymousProxyAccess;
                Console.WriteLine("New value    : " + newAnonymousProxyAccess);
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
| `SUPServerName` | - Managed: `String` | The name of the software update point server. |
| `newUseProxy` | - Managed: `String`- VBScript: `String` | Determines whether to use a proxy server. Possible values: "0" = `false` "1" = `true` |
| `newProxyName` | - Managed: `String`- VBScript: `String` | The proxy server name. |
| `newProxyServerPort` | - Managed: `String`- VBScript: `String` | The proxy server port. |
| `newAnonymousProxyAccess` | - Managed: `String`- VBScript: `String` | Determines whether to use credentials to connect to the proxy server. If this value is set to true, then the account used to connect needs to be set in the Configuration Manager 2007 Administrator Console. Possible values: "0" = `true` "1" = `false` |

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