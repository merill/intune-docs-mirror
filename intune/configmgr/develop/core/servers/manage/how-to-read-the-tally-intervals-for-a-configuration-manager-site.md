---
layout: Conceptual
title: Read the Tally Intervals for a Site - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-read-the-tally-intervals-for-a-configuration-manager-site
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
description: In Configuration Manager, you can read the available tally intervals for a site by inspecting the site control file SMS_COMPONENT_STATUS_SUMMARIZER object Summary_Intervals embedded property list.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 6da02d4e-8d6d-2fa8-63f3-d9a2333fd6f7
document_version_independent_id: 0acc6d8d-2dcd-e47b-640b-d5ad9ceca9bc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/manage/how-to-read-the-tally-intervals-for-a-configuration-manager-site.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/manage/how-to-read-the-tally-intervals-for-a-configuration-manager-site
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/manage/how-to-read-the-tally-intervals-for-a-configuration-manager-site.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 7c0231d6-5d4a-3260-a09a-614781b519b3
---

# Read the Tally Intervals for a Site - Configuration Manager | Microsoft Learn

In Configuration Manager, you can read the available tally intervals for a site by inspecting the site control file `SMS_COMPONENT_STATUS_SUMMARIZER` object `Summary_Intervals` embedded property list.

You use tally intervals for querying component (`SMS_ComponentSummarizer`) and site detail (`SMS_SiteDetailSummarizer`) summarizer classes. For more information, see [About Configuration Manager Status Summarizers](about-configuration-manager-status-summarizers).

### To read the tally intervals for a site

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Perform a query for the site's SMS\_COMPONENT\_STATUS\_SUMMARIZER property lists
3. In the results from step two, search for the Summary\_Intervals embedded property list.
4. Display the contents of the embedded property list.

## Example

The following example method returns a [SMS_TaskSequence](../../../reference/osd/sms_tasksequence-server-wmi-class) object after importing it from the supplied XML.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs
Sub ShowSiteTallyIntervals(connection, siteCode)

    Dim SCIComponent              'SMS_SCI_Component class
    Dim SCIComponentSet         'Enumeration of SMS_SCI_Component
    Dim query
    Dim i
    Dim vProperty                     'Embedded property

    query = "SELECT PropLists FROM SMS_SCI_Component " & _
            "WHERE ComponentName = 'SMS_COMPONENT_STATUS_SUMMARIZER' " & _
            "AND SiteCode = '" + siteCode + "'"

    ' You do not need to get a copy of the site control file just to read it.
    Set SCIComponentSet = connection.ExecQuery(query)

    ' The query returns only one instance.
    For Each SCIComponent In SCIComponentSet
        For Each vProperty In SCIComponent.PropLists
            If vProperty.PropertyListName = "Summary_Intervals" Then
                For i = 0 To UBound(vProperty.Values)
                    WScript.Echo vProperty.Values(i)
                Next
            End If
        Next
    Next
 End Sub
```

```c
public void ShowSiteTallyIntervals(WqlConnectionManager connection, string siteCode)
{
    try
    {
        // Query for the site's site control file SMS_COMPONENT_STATUS_SUMMARIZER property lists.
        IResultObject query =
            connection.QueryProcessor.ExecuteQuery("SELECT PropLists FROM SMS_SCI_Component " +
            "WHERE ComponentName = 'SMS_COMPONENT_STATUS_SUMMARIZER' " +
            "AND SiteCode = '" + siteCode + "'");

        foreach (IResultObject r in query)
        {
            // Get the summary intervals and display them.
          if (r.EmbeddedPropertyLists.ContainsKey("Summary_Intervals"))
            {
                Console.WriteLine(r.EmbeddedPropertyLists["Summary_Intervals"]["PropertyListName"].StringValue);
                foreach (string value in r.EmbeddedPropertyLists["Summary_Intervals"]["Values"].StringArrayValue)
                {
                    Console.WriteLine(value);
                }
            }
            else
            {
                Console.WriteLine("Not found");
                return;
            }
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to tally intervals: " + e.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: [WqlConnectionManager](../../understand/managed-sms-provider-fundamentals-in-configuration-manager#wqlconnectionmanager)- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals). |
| `siteCode` | - Managed: `String`- VBScript: `String` | A valid Configuration Manager site code. |

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

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../configure/role-based-administration).