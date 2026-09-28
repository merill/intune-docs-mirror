---
layout: Conceptual
title: Enable Unknown Computer Support for a PXE Service Point - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-enable-unknown-computer-support-for-a-pxe-service-point
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
description: Learn about how to set an operating system deployment response to PXE service requests from unknown computers.
locale: en-us
document_id: bf29d111-a4d9-1b31-5f0b-5d42dd120ee4
document_version_independent_id: f7f60d87-4339-02bf-1a4b-2b5257c8c8ba
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-enable-unknown-computer-support-for-a-pxe-service-point.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-enable-unknown-computer-support-for-a-pxe-service-point
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-enable-unknown-computer-support-for-a-pxe-service-point.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 3730111e-abad-caeb-4110-0832a709b6ad
---

# Enable Unknown Computer Support for a PXE Service Point - Configuration Manager | Microsoft Learn

In Configuration Manager, you set the operating system deployment PXE service point response to incoming PXE requests from unknown computers by setting the **SupportUnknownMachines** embedded property.

**SupportUnknownMachines** has the following possible values.

| Value | Description |
| --- | --- |
| 0 | The PXE service point does not respond to PXE requests from unknown computers. |
| 1 | The PXE service point responds to requests from unknown computers. |

### To set the PXE service point response to PXE requests from unknown computers

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Make a connection to the distribution point instance with PXE enabled.
3. Get the embedded properties.
4. Update the **SupportUnknownMachines** embedded property.
5. Commit the changes to the site control file.

## Example

The following example method sets the response for a PXE request based on the supplied `String` value (`allowResponse`).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```c
public void EnablePXE(WqlConnectionManager connection,                      string siteCode,                      string serverName,                      string allowResponse){    try    {        //Connect to distribution point instance.                        IResultObject siteRole = connection.GetInstance("SMS_SCI_SysResUse.FileType=2,ItemName=\"[\\\"Display=\\\\\\\\" + serverName + "\\\\\\\"]MSWNET:[\\\"SMS_SITE=" + siteCode + "\\\"]\\\\\\\\" + serverName + "\\\\,SMS Distribution Point\",ItemType=\"System Resource Usage\",SiteCode=" + "\"" + siteCode + "\"");        // Create temporary copy of the embedded properties.        Dictionary<string, IResultObject> embeddedProperties = siteRole.EmbeddedProperties;        // Enumerate through the embedded properties and makes changes as needed.        foreach (KeyValuePair<string, IResultObject> kvp in siteRole.EmbeddedProperties)        {            // Setting: SupportUnknownMachines            if (kvp.Value.PropertyList["PropertyName"] == "SupportUnknownMachines")            {                // Get current property value.                Console.WriteLine();                Console.WriteLine("Property: {0}", kvp.Value.PropertyList["PropertyName"]);                Console.WriteLine("Current value: {0}", kvp.Value.PropertyList["Value"]);                // Change value.                embeddedProperties["SupportUnknownMachines"]["Value"].StringValue = allowResponse;                Console.WriteLine("Setting the {0} value to {1}.", kvp.Value.PropertyList["PropertyName"], allowResponse);            }        }        // Store the settings that have changed.        siteRole.EmbeddedProperties = embeddedProperties;        // Save the settings.         siteRole.Put();    }    catch (SmsException ex)    {        Console.WriteLine();        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);    }}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `siteCode` | Managed: `String` | The Configuration Manager site code. |
| `serverName` | Managed: `String` | The server name. For example, `"SERVER1.DOMAIN1.COM"`. |
| `allowResponse` | Managed: `String` | The value to set whether the PXE service point will respond to unknown computers. - 0 - The PXE service point does not respond to PXE requests from unknown computers.- 1 - The PXE service point responds to requests from unknown computers. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).