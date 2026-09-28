---
layout: Conceptual
title: Create a Schedule Token - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-create-a-schedule-token
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
description: Create a schedule token in Configuration Manager by creating and populating an instance of the appropriate SMS_ST_ schedule token class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 41d63cf7-9e5a-5e70-8689-2cc386d2b09c
document_version_independent_id: 60e1e42a-2c9b-11f2-1dc0-25d372f7c459
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-create-a-schedule-token.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-create-a-schedule-token
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-create-a-schedule-token.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cd86e3fe-7a71-3943-833d-c8c92523695b
---

# Create a Schedule Token - Configuration Manager | Microsoft Learn

You create a schedule token, in Configuration Manager, by creating and populating an instance of the appropriate `SMS_ST_` schedule token class. `SMS_ST` schedule classes are child classes of the `SMS_ScheduleToken` class and handle the scheduling of events with differing frequencies such as daily, weekly and monthly.

The [SMS_ScheduleMethods](../../reference/core/servers/configure/sms_schedulemethods-server-wmi-class) Windows Management Instrumentation (WMI) class, and the corresponding [ReadFromString](../../reference/core/servers/configure/readfromstring-method-in-class-sms_schedulemethods) and [WriteToString](../../reference/core/servers/configure/writetostring-method-in-class-sms_schedulemethods) methods are used to decode and encode schedule tokens into and from an interval string. The interval strings can then be used to set schedule properties when defining or modifying objects. An example of this can be seen in the [How to Create a Maintenance Window for a Collection](../servers/configure/how-to-create-a-maintenance-window-for-a-collection) topic where the `ServiceWindowSchedules` property is configured.

### To create a schedule token and convert it to an interval string

1. Create a schedule token object by using one of the [SMS_ScheduleToken](../../reference/core/servers/configure/sms_scheduletoken-server-wmi-class) child classes. This example uses the [SMS_ST_RecurInterval](../../reference/core/servers/configure/sms_st_recurinterval-server-wmi-class) class.
2. Populate the properties of the new schedule token object.
3. Convert the schedule token object to an interval string by using the `SMS_ScheduleMethods` class and `WriteToString` method.
4. Use the interval string to populate an object's schedule properties, as needed.

## Example

The following example method shows how to create a schedule token by creating and populating an instance of the `SMS_ST_RecurInterval` schedule token class. In addition, the example shows how to convert the schedule to an interval string by using the `SMS_ScheduleMethods` class and `WriteToString` method.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs

Sub CreateDailyRecurringScheduleString(connection,   _
                                       hourDuration, _
                                       daySpan,      _
                                       startTime,    _
                                       isGmt)

    ' Create a new recurring interval schedule object.
    ' Note: There are several types of schedule classes available, each defines a different type of schedule.
    Set recurInterval = connection.Get("SMS_ST_RecurInterval").SpawnInstance_

    ' Populate the schedule properties.
    recurInterval.DayDuration = 0
    recurInterval.HourDuration = hourDuration
    recurInterval.MinuteDuration = 0
    recurInterval.DaySpan = daySpan
    recurInterval.HourSpan = 0
    recurInterval.MinuteSpan = 0
    recurInterval.StartTime = startTime
    recurInterval.IsGMT = isGmt

    ' Call WriteToString method to decode the schedule token.
    ' Note: The initial parameter of the WriteToString method requires an array.
    Set clsScheduleMethod = connection.Get("SMS_ScheduleMethods")
    clsScheduleMethod.WriteToString Array(recurInterval), scheduleString

    ' Output schedule token as an interval string.
    WScript.Echo "Schedule Token Interval String: " & scheduleString

End Sub
```

```c

public void CreateDailyRecurringScheduleToken(WqlConnectionManager connection,
                                              int hourDuration,
                                              int daySpan,
                                              string startTime,
                                              bool isGmt)
{
    try
    {
        // Create a new recurring interval schedule object.
        // Note: There are several types of schedule classes available, each defines a different type of schedule.
        IResultObject recurInterval = connection.CreateEmbeddedObjectInstance("SMS_ST_RecurInterval");

        // Populate the schedule properties.
        recurInterval["DayDuration"].IntegerValue = 0;
        recurInterval["HourDuration"].IntegerValue = hourDuration;
        recurInterval["MinuteDuration"].IntegerValue = 0;
        recurInterval["DaySpan"].IntegerValue = daySpan;
        recurInterval["HourSpan"].IntegerValue = 0;
        recurInterval["MinuteSpan"].IntegerValue = 0;
        recurInterval["StartTime"].StringValue = startTime;
        recurInterval["IsGMT"].BooleanValue = isGmt;

        // Creating array to use as a parameters for the WriteToString method.
        List<IResultObject> scheduleTokens = new List<IResultObject>();
        scheduleTokens.Add(recurInterval);

        // Creating dictionary object to pass parameters to the WriteToString method.
        Dictionary<string, object> inParams = new Dictionary<string, object>();
        inParams["TokenData"] = scheduleTokens;

        // Initialize the outParams object.
        IResultObject outParams = null;

        // Call WriteToString method to decode the schedule token.
        outParams = connection.ExecuteMethod("SMS_ScheduleMethods", "WriteToString", inParams);

        // Output schedule token as an interval string.
        // Note: The return value for this method is always 0, so this check is just best practice.
        if (outParams["ReturnValue"].IntegerValue == 0)
        {
            Console.WriteLine("Schedule Token Interval String: " + outParams["StringData"].StringValue);
        }
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `hourDuration` | - Managed: `Integer`- VBScript: `Integer` | Number of hours during which the scheduled action occurs. Allowable values are in the range 0-23. The default value is 0, indicating no duration. |
| `daySpan` | - Managed: `Integer`- VBScript: `Integer` | Number of days spanning schedule intervals. Allowable values are in the range 0-31. The default value is 0. |
| `startTime` | - Managed: `String` (DateTime)- VBScript: `String` (DateTime) | Date and time when the scheduled action takes place. The default value is "19700201000000.000000+\*\*\*". This is the format in which (WMI) CIM DATETIME values are stored. |
| `isGmt` | - Managed: `Boolean`- VBScript: `Boolean` | `true` if the time is in Coordinated Universal Time (UTC). The default value is `false`, for local time. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managmentprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../servers/configure/role-based-administration).