---
layout: Conceptual
title: Enable or Disable a Software Metering Rule - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-enable-or-disable-a-software-metering-rule
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
description: Enable or disable a software metering rule, in Configuration Manager, by loading an instance of the software metering rule.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: ebc2ff5c-ab26-a061-7e37-95684564b52c
document_version_independent_id: 8ed08f63-bbdf-28f7-dd30-0d0d18c270b7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-enable-or-disable-a-software-metering-rule.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-enable-or-disable-a-software-metering-rule
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-enable-or-disable-a-software-metering-rule.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: fbdd2267-750e-0d90-97af-4aba46355cc1
---

# Enable or Disable a Software Metering Rule - Configuration Manager | Microsoft Learn

You enable or disable a software metering rule, in Configuration Manager, by loading the instance of the software metering rule that is identified by the software metering rule ID and then setting the Enabled value.

### To enable or disable a software metering rule

1. Set up a connection to the SMS Provider.
2. Load the software metering rule object by using the [SMS_MeteredProductRule](../reference/apps/sms_meteredproductrule-server-wmi-class) class and a known software metering rule ID.
3. Set the *Enabled* property to `true` or `false`.

## Example

The following example method shows how to enable or disable a software metering rule by loading the instance of the software metering rule that is identified by the software metering rule ID and setting the *Enabled* property.

Important

The rule ID corresponds to the value that is stored in the property *RuleID*. The Configuration Manager console displays a **Rule ID** column, which actually corresponds to the value that is stored in the property *SecurityID*.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

' Enable or disable a software metering rule.
 Sub EnableDisableSoftwareMeteringRule(connection,          _
                                      existingSWMRuleID,    _
                                      enableDisableSWMRule)

    ' Get an existing software metering rule to enable or disable.
    Set existingSWMRule = connection.Get("SMS_MeteredProductRule.RuleID='" & existingSWMRuleID & "'")

    ' Get file name for output.
    fileName = existingSWMRule.FileName

    ' Enable or disable the rule.
    existingSWMRule.Enabled = enableDisableSWMRule

    ' Save the new rule and properties.
    existingSWMRule.Put_

    ' Output a success message.
    Wscript.Echo "SWM rule ID:    " & existingSWMRuleID
    Wscript.Echo "Rule name:      " & fileName
    Wscript.Echo "Set enabled to: " & enableDisableSWMRule

 End Sub
```

```c

public void EnableDisableSoftwareMeteringRule(WqlConnectionManager connection,
                                              string existingSWMRuleID,
                                              bool enableDisableSWMRule)
{
    try
    {
        // Get the specific software metering rule to enable or disable.
        IResultObject existingSWMRule = connection.GetInstance(@"SMS_MeteredProductRule.RuleID='" + existingSWMRuleID + "'");

        // Get rule name for output message.
        string productName = existingSWMRule["ProductName"].StringValue;

        // Set the software metering rule.
        existingSWMRule["Enabled"].BooleanValue = enableDisableSWMRule;

        // Save changes.
        existingSWMRule.Put();

        // Output a success message.
        Console.WriteLine("SWM rule ID: " + existingSWMRuleID);
        Console.WriteLine("Rule name: " + productName);
        Console.WriteLine("Set enabled to: " + enableDisableSWMRule);
    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed to modify software metering rule. Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingSWMRuleID` | - Managed: `String`- VBScript: `String` | Identifies a specific software metering rule. In this case, identifies the specific software metering rule that will be enabled or disabled. |
| `enableDisableSWMRule` | - Managed: `Boolean`- VBScript: `Boolean` | Enables or disables the software metering rule.`true` - Enabled`false` - Disabled |

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