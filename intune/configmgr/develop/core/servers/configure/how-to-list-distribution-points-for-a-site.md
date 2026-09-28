---
layout: Conceptual
title: List Distribution Points for a Site - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-list-distribution-points-for-a-site
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
description: How to assign a distribution point to a package by using the SMS_DistributionPoint Server WMI Class and class properties in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: ba45d4ce-01f6-9f0d-6973-107e23e80ab9
document_version_independent_id: 0056d79f-f4a4-f6cf-97dc-582ade757986
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-list-distribution-points-for-a-site.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-list-distribution-points-for-a-site
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-list-distribution-points-for-a-site.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: e21522be-71dd-7d09-6fb5-395ddf3a8466
---

# List Distribution Points for a Site - Configuration Manager | Microsoft Learn

The following example shows how to assign a distribution point to a package by using the [SMS_DistributionPoint Server WMI Class](../../../reference/core/servers/configure/sms_distributionpoint-server-wmi-class) class and class properties in Configuration Manager.

You only need to assign a distribution point to a package if the package contains source files. The package is not advertised until the program source files have been propagated to a distribution point share. You can use the default distribution point share, or you can specify a share to use. You can also specify more than one distribution point to use to distribute your package source files, although the following example does not demonstrate that.

Note

To identify branch distribution points, check the [IsPeerDP](../../../reference/core/servers/configure/sms_distributionpoint-server-wmi-class) property of the specific [SMS_DistributionPoint](../../../reference/core/servers/configure/sms_distributionpoint-server-wmi-class) class instance. If the IsPeerDP property is true, then the distribution point is a branch distribution point.

### To list distribution points for a site

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Run a query, which populates a variable with a collection of distribution point objects.
3. Enumerate through the collection of and list the distribution points returned by the query.

## Example

The following example method lists distribution points for a site.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub ListDistributionPointsForSite(connection, siteCode)

    ' This query selects all distribution points for a site based on the provided site code.
    Query = "SELECT * FROM SMS_SystemResourceList WHERE RoleName='SMS Distribution Point' AND SiteCode='" & siteCode & "'"

    ' Run query, which populates listOfResources with a collection of objects.
    Set ListOfResources = connection.ExecQuery(query, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

    ' Output header for list of distribution points.
    Wscript.Echo "List of distribution points for site: " & siteCode
    Wscript.Echo "--------------------------------------------"

    ' Enumerate through the collection of objects returned by the query.
    For Each resource In listOfResources
        ' Output the server name for each distribution point.
        Wscript.Echo resource.ServerName
    Next

End Sub
```

```c
public void ListDistributionPointsForSite(WqlConnectionManager connection, string siteCode)
{
    try
    {
        // This query selects all distribution points for a site based on the provided site code.
        string query = "SELECT * FROM SMS_SystemResourceList WHERE RoleName='SMS Distribution Point' AND SiteCode='" + siteCode + "'";

        // Run query, which populates 'listOfResources' with a collection of objects.
        IResultObject listOfResources = connection.QueryProcessor.ExecuteQuery(query);

        // Output header for list of distribution points.
        Console.WriteLine("List of distribution points for site: " + siteCode);
        Console.WriteLine("--------------------------------------------");

        // Enumerate through the collection of objects returned by the query.
        foreach (IResultObject resource in listOfResources)
        {
            // Output the server name for each distribution point.
            Console.WriteLine(resource["ServerName"].StringValue);
        }
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to list distribution points. Error: " + ex.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection``swebemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `siteCode` | - Managed: `String`- VBScript: `String` | The site code for the site that supports the distribution points. |

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