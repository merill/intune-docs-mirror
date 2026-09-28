---
layout: Conceptual
title: Set the Response Delay for a PXE Service Point - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-set-the-response-delay-for-a-pxe-service-point
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
description: In Configuration Manager, you set the operating system deployment PXE service point response delay by updating the ResponseDelay embedded property.
locale: en-us
document_id: 3d980247-3723-ec44-5e93-1bc310f53003
document_version_independent_id: da55b878-9488-fa67-1671-819788ff77e8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-set-the-response-delay-for-a-pxe-service-point.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-set-the-response-delay-for-a-pxe-service-point
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-set-the-response-delay-for-a-pxe-service-point.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: ad709539-1baa-78e0-36d7-e7a76f55836d
---

# Set the Response Delay for a PXE Service Point - Configuration Manager | Microsoft Learn

In Configuration Manager, you set the operating system deployment PXE service point response delay by updating the *ResponseDelay* embedded property. *ResponseDelay* specifies how long the delay should be for this PXE service point before it responds to computer requests when multiple PXE service points are used. By default, the Configuration Manager PXE service point will respond immediately to the network PXE requests.

The delay is provided by the PXE client, and it shows the time that has passed since the client started the PXE boot process (seconds elapsed since client began address acquisition or renewal process). A client sends requests to the server at intervals of 0 (default), 4, 8, 16, or 32 seconds.

### To set the response delay for a PXE service point

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Make a connection to the distribution point instance with PXE enabled.
3. Get the embedded properties.
4. Update the *ResponseDelay* embedded property.
5. Commit the changes to the site control file.

## Example

The following example method sets the response delay for a PXE service point.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```c
public void SetResponseDelay(WqlConnectionManager connection,                                  string siteCode,                                  string serverName,                                  int delay){    try    {        //Connect to distribution point instance.                        IResultObject siteRole = connection.GetInstance("SMS_SCI_SysResUse.FileType=2,ItemName=\"[\\\"Display=\\\\\\\\" + serverName + "\\\\\\\"]MSWNET:[\\\"SMS_SITE=" + siteCode + "\\\"]\\\\\\\\" + serverName + "\\\\,SMS Distribution Point\",ItemType=\"System Resource Usage\",SiteCode=" + "\"" + siteCode + "\"");        // Create temporary copy of the embedded properties.        Dictionary<string, IResultObject> embeddedProperties = siteRole.EmbeddedProperties;        // Enumerate through the embedded properties and makes changes as needed.        foreach (KeyValuePair<string, IResultObject> kvp in siteRole.EmbeddedProperties)        {            // Setting: ResponseDelay            if (kvp.Value.PropertyList["PropertyName"] == "ResponseDelay")            {                // Get current property value.                Console.WriteLine();                Console.WriteLine("Property: {0}", kvp.Value.PropertyList["PropertyName"]);                Console.WriteLine("Current value: {0}", kvp.Value.PropertyList["Value"]);                // Change value.                embeddedProperties["ResponseDelay"]["Value"].IntegerValue = delay;                Console.WriteLine("Setting the {0} value to {1}.", kvp.Value.PropertyList["PropertyName"], delay);            }        }        // Store the settings that have changed.        siteRole.EmbeddedProperties = embeddedProperties;        // Save the settings.         siteRole.Put();    }    catch (SmsException ex)    {        Console.WriteLine();        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);    }}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `siteCode` | Managed: `String` | The Configuration Manager site code. |
| `serverName` | Managed: `String` | The server name. For example, `"SERVER1.DOMAIN1.COM"`. |
| delay | Managed: `Integer` | The delay, in seconds. |

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