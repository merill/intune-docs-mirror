---
layout: Conceptual
title: Enable or Disable the Software Updates Client Agent - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-enable-or-disable-the-software-updates-client-agent
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
description: You enable or disable the Software Updates Client Agent, in Configuration Manager, by modifying the site control file settings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 3fcb1d33-389b-be0a-c2ae-fb489a3c6faa
document_version_independent_id: e149a623-9fb6-04d9-d0a7-d3324ddf80f1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/how-to-enable-or-disable-the-software-updates-client-agent.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/how-to-enable-or-disable-the-software-updates-client-agent
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/how-to-enable-or-disable-the-software-updates-client-agent.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
platformId: 2cb0b514-7931-cb86-3707-42ea3ac606ff
---

# Enable or Disable the Software Updates Client Agent - Configuration Manager | Microsoft Learn

You enable or disable the Software Updates Client Agent, in Configuration Manager, by modifying the site control file settings.

### To enable or disable the Software Updates Client Agent

1. Set up a connection to the SMS Provider.
2. Make a connection to the Software Updates Client Agent section of the site control file by using the [SMS_SCI_ClientComp](../reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class.
3. Loop through the array of available properties, making changes as needed.
4. Commit the changes to the site control file.

## Example

The following example method enables or disables the Software Updates Client Agent by using the [SMS_SCI_ClientComp](../reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class to connect to the site control file and change properties.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

Sub EnableDisableSUMClientAgent(swbemServices,     _
                                swbemContext,      _
                                enableDisableFlag, _
                                siteToChange )

    ' Load site control file and get software updates client component section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteToChange & """", "Refresh", , , swbemContext
    Set objSWbemInst = swbemServices.Get("SMS_SCI_ClientComp.Filetype=1,Itemtype='Client Component',Sitecode='" & siteToChange & "',ItemName='Software Updates'", , swbemContext)

    ' Display the Software Updates Client Agent settings before changing the properties.
    Wscript.Echo " "
    Wscript.Echo "Properties - Before Change"
    Wscript.Echo "---------------------------"
    Wscript.Echo objSWbemInst.ClientComponentName
    Wscript.Echo objSWbemInst.Flags & " (0 = Disabled, 1 = Enabled)"

    ' Set Software Updates Client Agent by setting Flags value to 0 or 1 by using the enableDisableFlag variable.
    objSWbemInst.Flags = enableDisableFlag

    ' Save new Software Updates Client Agent settings.
    objSWbemInst.Put_ , swbemContext
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteToChange & """", "Commit", , , swbemContext

    ' Refresh in-memory copy of the site control file and get the software updates client component section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteToChange & """", "Refresh", , , swbemContext
    Set objSWbemInst = swbemServices.Get("SMS_SCI_ClientComp.Filetype=1,Itemtype='Client Component',Sitecode='" & siteToChange & "',ItemName='Software Updates'", , swbemContext)

    ' Display the Software Updates Client Agent settings after changing the properties.
    Wscript.Echo " "
    Wscript.Echo "Properties - After Change"
    Wscript.Echo "---------------------------"
    Wscript.Echo objSWbemInst.ClientComponentName
    Wscript.Echo objSWbemInst.Flags & " (0 = Disabled, 1 = Enabled)"

End Sub

```

```c

public void EnableDisableSUMClientAgent(WqlConnectionManager connection,
                                        string enableDisableFlag,
                                        string siteCode)
{
    try
    {
        IResultObject siteDefinition = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Software Updates'");

        // Display Software Updates Client Agent settings before changing the properties.
        Console.WriteLine();
        Console.WriteLine("Properties - Before Change");
        Console.WriteLine("---------------------------");
        Console.WriteLine(siteDefinition["ClientComponentName"].StringValue);
        Console.WriteLine(siteDefinition["Flags"].StringValue + " (0 = Disabled, 1 = Enabled)");

        // Set Software Updates Client Agent by setting "Flags" value to 0 or 1 by using the enableDisableFlag variable.
        siteDefinition["Flags"].StringValue = enableDisableFlag;

        // Save the settings.
        siteDefinition.Put();

        // Verify the change by reconnecting and getting the value again.
        IResultObject siteDefinition2 = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Software Updates'");

        // Display Software Updates Client Agent settings after changing the properties.
        Console.WriteLine();
        Console.WriteLine("Properties - After Change");
        Console.WriteLine("--------------------------");
        Console.WriteLine(siteDefinition2["ClientComponentName"].StringValue);
        Console.WriteLine(siteDefinition2["Flags"].StringValue + " (0 = Disabled, 1 = Enabled)");
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
| `siteCode` | - Managed: `String` | The site code. |
| `siteToChange` | - VBScript: `String` | The site code. |
| `enableDisableFlag` | - Managed: `String`- VBScript: `String` | Determines whether the Software Updates Client Agent is enabled or disabled. 0 - Disabled 1 - Enabled |

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