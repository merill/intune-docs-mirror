---
layout: Conceptual
title: Configure the Default Compliance Evaluation Schedule - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/how-to-configure-the-default-compliance-evaluation-schedule
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
description: In Configuration Manager, the site control file maintains configuration for the configuration of the site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: e63f6bc2-3463-ee74-de8b-86041947ad61
document_version_independent_id: 44f1ef66-369d-fd64-da0c-519bfc9fde3c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/compliance/how-to-configure-the-default-compliance-evaluation-schedule.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/compliance/how-to-configure-the-default-compliance-evaluation-schedule
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/compliance/how-to-configure-the-default-compliance-evaluation-schedule.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: d33db3d6-9ebe-ba4b-aba9-ea3bb9480e87
---

# Configure the Default Compliance Evaluation Schedule - Configuration Manager | Microsoft Learn

In Configuration Manager, the site control file maintains configuration for the configuration of the site. These code samples query for the specific site control file item Configuration Management Agent, and change the EvaluationSchedule value to set the client agent evaluation schedule.

### To configure the Default Compliance Evaluation Schedule

1. Set up a connection to the SMS Provider.
2. Make a connection to the Desired Configuration Management Client Agent section of the site control file by using the [SMS_SCI_ClientComp](../reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class.
3. Loop through the array of available properties, making changes as needed.
4. Commit the changes to the site control file.

## Example

The following code example shows how to change the default compliance evaluation schedule for the configuration management client agent.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

Sub ChangeDCMAgentEvaluationSchedule(swbemServices,    _
                                     swbemContext,     _
                                     siteCode,         _
                                     newAgentSchedule)

    ' The evaluation schedule is defined by a string stored in a schedule token format.
    ' Detailed information on the schedule token format can be found in the class SMS_ScheduleToken reference material.

    ' Load site control file and get DCM client component section.
swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext
Set swbemInst = swbemServices.Get("SMS_SCI_ClientComp.Filetype=1,Itemtype='Client Component',Sitecode='" & siteCode & "',ItemName='Configuration Management Agent'", , swbemContext)

    ' Loop through the array of embedded SMS_EmbeddedProperty instances for the
    ' Number of Retries PropertyName. Get its value and display it.
    For Each vProperty In swbemInst.Props

        If vProperty.PropertyName = "EvaluationSchedule" Then

            ' Display DCM client agent evaluation schedule before change.
            Wscript.Echo " "
            Wscript.Echo "Evaluation Schedule - Before Change"
            Wscript.Echo "-----------------------------------"
            Wscript.Echo vProperty.Value2

            ' Set DCM client agent evaluation schedule using the newAgentSchedule variable.
            vProperty.Value2 = newAgentSchedule

            ' Save new client agent settings
            swbemInst.Put_ , swbemContext
            swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Commit", , , swbemContext

        End If
    Next

    ' Refresh in-memory copy of the site control file and get the DCM client component section.
swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext
Set swbemInst = Nothing

Set swbemInst = swbemServices.Get("SMS_SCI_ClientComp.Filetype=1,Itemtype='Client Component',Sitecode='" & siteCode & "',ItemName='Configuration Management Agent'", , swbemContext)

    For Each vProperty In swbemInst.Props

        If vProperty.PropertyName = "EvaluationSchedule" Then

            ' Sisplay DCM client agent evaluation schedule before change.
            Wscript.Echo " "
            Wscript.Echo "Evaluation Schedule - After Change"
            Wscript.Echo "----------------------------------"
            Wscript.Echo vProperty.Value2

        End If
    Next

End Sub

```

```c

public void ChangeDCMAgentEvaluationSchedule(WqlConnectionManager connection,
                                             string siteCode,
                                             string newAgentSchedule)
{

    // The evaluation schedule is defined by a string stored in a schedule token format.
    // Detailed information on the schedule token format can be found in the class SMS_ScheduleToken reference material.

    try
    {
        IResultObject siteDefinition = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Configuration Management Agent'");

        if (siteDefinition.EmbeddedProperties.ContainsKey("EvaluationSchedule"))
        {
            Dictionary<string, IResultObject> WorkingEmbeddedProperties = siteDefinition.EmbeddedProperties; //get temporary copy

            // Display DCM client agent settings before change.
            Console.WriteLine();
            Console.WriteLine("DCM Client Agent Schedule - Before Change");
            Console.WriteLine("-----------------------------------------");
            Console.WriteLine("Schedule in token format: " + WorkingEmbeddedProperties["EvaluationSchedule"]["Value2"].StringValue);

            // Set DCM client agent setting to new value.
            WorkingEmbeddedProperties["EvaluationSchedule"]["Value2"].StringValue = newAgentSchedule;
            siteDefinition.EmbeddedProperties = WorkingEmbeddedProperties;

            // Save the settings.
            siteDefinition.Put();

            // Verify change by reconnecting and getting the value again.
            Dictionary<string, IResultObject> WorkingEmbeddedProperties2 = siteDefinition.EmbeddedProperties; //Get temporary copy for change verification.

            // Display DCM client agent settings after change.
            Console.WriteLine();
            Console.WriteLine("DCM Client Agent Schedule - After Change");
            Console.WriteLine("-----------------------------------------");
            Console.WriteLine("Schedule in token format: " + WorkingEmbeddedProperties2["EvaluationSchedule"]["Value2"].StringValue);

        }
    }

    catch (SmsException eX)
    {
        Console.WriteLine("Failed. Error: " + eX.InnerException.Message);
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
| `newAgentSchedule` | - Managed: `String`- VBScript: `String` | The new schedule in string format. For more information, see [About schedules](../core/understand/about-configuration-manager-schedules). |

## Compiling the Code

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

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).