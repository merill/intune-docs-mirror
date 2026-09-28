---
layout: Conceptual
title: Disable a PXE Service Point Role - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-disable-a-pxe-service-point-role
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
description: You disable the PXE Service Point role, in Configuration Manager, by getting an instance of a specific distribution point and setting the IsPXE value to 0.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 2937683c-647a-2d0f-c3c0-f75ef145afc9
document_version_independent_id: 6a0cbc9f-5de6-453c-99b8-d148d7b53596
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-disable-a-pxe-service-point-role.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-disable-a-pxe-service-point-role
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-disable-a-pxe-service-point-role.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 4e8476ad-d265-6997-2fe7-ddf6183a5fd4
---

# Disable a PXE Service Point Role - Configuration Manager | Microsoft Learn

You disable the PXE Service Point role, in Configuration Manager, by getting an instance of a specific distribution point and setting the `IsPXE` value to `0`.

### To disable a PXE service point role

1. Set up a connection to the SMS Provider. For more information see, [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get an instance of a specific distribution point.
3. Set the `IsPXE` embedded property to `0`.
4. Save the distribution point instance.

## Example

The following example method disables the PXE service point.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```c
public void DisablePXE(WqlConnectionManager connection,                                        string siteCode,                                        string serverName){    try    {        //Connect to distribution point instance.                        IResultObject siteRole = connection.GetInstance("SMS_SCI_SysResUse.FileType=2,ItemName=\"[\\\"Display=\\\\\\\\" + serverName + "\\\\\\\"]MSWNET:[\\\"SMS_SITE=" + siteCode + "\\\"]\\\\\\\\" + serverName + "\\\\,SMS Distribution Point\",ItemType=\"System Resource Usage\",SiteCode=" + "\"" + siteCode + "\"");        // Create temporary copy of the embedded properties.        Dictionary<string, IResultObject> embeddedProperties = siteRole.EmbeddedProperties;        // Enumerate through the embedded properties and makes changes as needed.        foreach (KeyValuePair<string, IResultObject> kvp in siteRole.EmbeddedProperties)        {            // Setting: IsPXE            if (kvp.Value.PropertyList["PropertyName"] == "IsPXE")            {                // Get current property value.                Console.WriteLine();                Console.WriteLine("Property: {0}", kvp.Value.PropertyList["PropertyName"]);                Console.WriteLine("Current value: {0} (0 not enabled, 1 enabled)", kvp.Value.PropertyList["Value"]);                // Change value to disable PXE (1 enabled, 0 not enabled).                 embeddedProperties["IsPXE"]["Value"].StringValue = "0";                Console.WriteLine("Setting the {0} value to {1}.", kvp.Value.PropertyList["PropertyName"], "0");            }        }        // Store the settings that have changed.        siteRole.EmbeddedProperties = embeddedProperties;        // Save the settings.         siteRole.Put();    }    catch (SmsException ex)    {        Console.WriteLine();        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);    }}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `siteCode` | Managed: `String` | The Configuration Manager site code. |
| `serverName` | Managed: `String` | The server name. For example, `"SERVER1.DOMAIN1.COM"` |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

System.Globalization

System.Localization

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).