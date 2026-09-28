---
layout: Conceptual
title: Determine the Health of a Site - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-determine-the-health-of-a-configuration-manager-site
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
description: In Configuration Manager, you can determine the overall health or status of a site by inspecting the SMS_SummarizerSiteStatus object Status property.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 938d6d40-f652-9558-88b2-b19cfcf76c44
document_version_independent_id: de7b4916-0d9e-d302-7c39-2234707362f4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/manage/how-to-determine-the-health-of-a-configuration-manager-site.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/manage/how-to-determine-the-health-of-a-configuration-manager-site
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/manage/how-to-determine-the-health-of-a-configuration-manager-site.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: fe473f54-15d6-1ea2-1344-4cb574f74753
---

# Determine the Health of a Site - Configuration Manager | Microsoft Learn

You can determine the overall health or status of a site, in Configuration Manager, by inspecting the `SMS_SummarizerSiteStatus` object `Status` property. The `Status` property has three possible values:

| Value | Description |
| --- | --- |
| 0 | The site is healthy. |
| 1 | The site has warning conditions. |
| 2 | The site has error conditions. |

`SMS_SummarizerSiteStatus` is an example of a Configuration Manager summarizer. For more information, see [SMS_SummarizerSiteStatus server WMI class](../../../reference/core/servers/manage/sms_summarizersitestatus-server-wmi-class).

### To determine a site's health

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Get the `SMS_SummarizerSiteStatus` object by using the Configuration Manager site code.
3. Inspect the `SMS_SummarizerSiteStatus` object `Status` property to determine the site status

## Example

The following example determines the health of the site code supplied in the parameter `siteCode`.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs
Sub ShowSiteHealth(connection, siteCode)

    Dim siteHealth
    Dim health

    On Error Resume Next

    ' Get the site status summarizer.
    Set siteHealth = connection.Get("SMS_SummarizerSiteStatus.SiteCode='" & siteCode & "'")
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get site health"
        Exit Sub
    End If

    ' Display the site health.
    health="Health for site " + siteCode + " "

    Select Case siteHealth.Status
        Case 0
            heath = health + "is OK"
        Case 1
            health = health + "has warnings"
        Case 2
            health = health + "is critical"
        Case Else
            health = health + "is not known"
    End Select

    Wscript.Echo health
End Sub
```

```c
public void ShowSiteHealth(WqlConnectionManager connection, string siteCode)
{
    try
    {
        IResultObject siteHealth = connection.GetInstance(@"SMS_SummarizerSiteStatus.SiteCode='" + siteCode + "'");

        Console.Write("Health for site {0}", siteCode);
        switch (siteHealth["Status"].IntegerValue)
        {
            case 0:
                Console.WriteLine("is OK");
                break;
            case 1:
                Console.WriteLine("has warnings");
                break;
            case 2:
                Console.WriteLine("is critical");
                break;
            default:
                Console.WriteLine("is not known");
                break;
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to show site status: " + e.Message);
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: [WqlConnectionManager](../../understand/managed-sms-provider-fundamentals-in-configuration-manager#wqlconnectionmanager)- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals). |
| `siteCode` | - Managed: `String`- VBScript: `String` | A valid task Configuration Manager site code |

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