---
layout: Conceptual
title: Set the PXE Service Point Response for a Specific Network Interface - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-set-the-pxe-service-point-response-for-a-specific-network-interface
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
description: In Configuration Manager, you set the operating system deployment to respond to a specific set of network addresses by adding the required media access control (MAC) addresses to the BindExcept embedded property list.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 0d7b4335-c3d2-75fd-ab25-649446a61c32
document_version_independent_id: 099d7caa-017d-09e0-eae9-f0d034f77ee9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-set-the-pxe-service-point-response-for-a-specific-network-interface.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-set-the-pxe-service-point-response-for-a-specific-network-interface
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-set-the-pxe-service-point-response-for-a-specific-network-interface.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 45f96f2c-f9d0-4aa4-724d-4f4eef61b570
---

# Set the PXE Service Point Response for a Specific Network Interface - Configuration Manager | Microsoft Learn

In Configuration Manager, you set the operating system deployment to respond to a specific set of network addresses by adding the required media access control (MAC) addresses to the `BindExcept` embedded property list. You must also set the `BindPolicy` embedded property to 1. This specifies that PXE requests are accepted on specified network address only. For more information about setting `BindPolicy`, see [How to Set the PXE Service Point Response to All Network Interfaces](how-to-set-the-pxe-service-point-response-to-all-network-interfaces).

### To set the response for a specific network interface

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Make a connection to the PXE service point resources section of the site control file.
3. Get the `BindExcept` embedded property list.
4. Add the MAC addresses to the `BindExcept` embedded property list.
5. Commit the changes to the site control file.

## Example

The following example method adds a supplied MAC address to the list of MAC address that are responded to.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```c
public void SetNetworkInterface(WqlConnectionManager connection,                                string siteCode,                                string serverName,                                string macAddress){    try    {        //Connect to distribution point instance.                        IResultObject siteRole = connection.GetInstance("SMS_SCI_SysResUse.FileType=2,ItemName=\"[\\\"Display=\\\\\\\\" + serverName + "\\\\\\\"]MSWNET:[\\\"SMS_SITE=" + siteCode + "\\\"]\\\\\\\\" + serverName + "\\\\,SMS Distribution Point\",ItemType=\"System Resource Usage\",SiteCode=" + "\"" + siteCode + "\"");        // Create temporary copy of the embedded properties.        Dictionary<string, IResultObject> embeddedPropertyLists = siteRole.EmbeddedPropertyLists;        // Get current mac addresses.        string[] macAddresses = embeddedPropertyLists["BindExcept"]["Values"].StringArrayValue;        //Convert to list.        List<string> addressList = new List<string>();        foreach (string address in macAddresses)        {            addressList.Add(address);        }        // Add the new mac address to the list.        addressList.Add(macAddress);        // Add the new mac address to the list.        embeddedPropertyLists["BindExcept"]["Values"].StringArrayValue = addressList.ToArray();        siteRole.EmbeddedPropertyLists = embeddedPropertyLists;        // Save the settings.         siteRole.Put();    }    catch (SmsException ex)    {        Console.WriteLine();        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);    }}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `serverName` | - Managed: `String` | The Configuration Manager server. |
| `siteCode` | - Managed: `String` | The Configuration Manager site code. |
| `macAddress` | - Managed: `String` | The MAC address to be added in the following format: 00:11:22:33:44:55 |

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