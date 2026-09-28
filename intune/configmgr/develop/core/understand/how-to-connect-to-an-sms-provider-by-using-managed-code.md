---
layout: Conceptual
title: Connect to an SMS Provider by Using Managed Code - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code
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
description: To connect to an SMS Provider, use WqlConnectionManager.Connect.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 4c5243b5-0c7f-fc7c-4760-cd47c4782d25
document_version_independent_id: a7dc24b4-39bb-8c5e-73aa-f336a4c24ee0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 239d65aa-a844-e182-40dd-e64cfc966afe
---

# Connect to an SMS Provider by Using Managed Code - Configuration Manager | Microsoft Learn

To connect to an SMS Provider, use **WqlConnectionManager.Connect**. After it's connected, **WqlConnectionManager.Connect** has methods to query, create, delete, and otherwise use Configuration Manager Windows Management Instrumentation (WMI) objects.

Note

**WqlConnectionManager.Connect** is a WMI-specific derivation of [ConnectionManagerBase](/en-us/previous-versions/system-center/developer/cc147366%28v=msdn.10%29).

If you're connecting to a local SMS Provider, you don't supply user credentials. If you're connecting to a remote SMS Provider, you don't need to supply user credentials if the current user/computer context has permissions on the remote SMS Provider.

If you don't have access privileges on the remote SMS Provider, or if you want to use a different user account, then you must supply user credentials for a user account that has access privileges.

**WQLConnectionManager.Connection** requires a [SmsNamedValuesDictionary](/en-us/previous-versions/system-center/developer/cc147435%28v=msdn.10%29) object. This can be used to store cached information such as the computer name.

It's pre-populated with many values that can be used in your application.

| Value | Description. |
| --- | --- |
| ProviderLocation | The provider location. For example, \\&lt;ComputerName&gt;\ROOT\sms:SMS\_ProviderLocation.SiteCode="XXX". |
| ProviderMachineName | The provider computer. For example, \\ComputerName. |
| Connection | The connection path. For example, \\ComputerName\root\sms\site\_XXX. |
| ConnectedSiteCode | The site code for the Configuration Manager site that the connection is connected to. For example, XXX. |
| ServerName | The computer name, for example, COMPUTERNAME. |
| SiteName | The Configuration Manager site code. For example, Central Site. |
| ConnectedServerVersion | The version for the connected server. For example, 4.00.5830.0000 |
| BuildNumber | The Configuration Manager installation build number. For example, 5830. |

Note

The [SmsNamedValuesDictionary](/en-us/previous-versions/system-center/developer/cc147435%28v=msdn.10%29) object is not the context qualifier information passed to the provider. For more information, see [How to Add a Configuration Manager Context Qualifier by Using Managed Code](how-to-add-a-configuration-manager-context-qualifier-by-using-managed-code).

### To connect to the SMS Provider

1. Create a [SmsNamedValuesDictionaryObject](/en-us/previous-versions/system-center/developer/cc147435%28v=msdn.10%29).
2. Create an instance of the **WqlConnectionManager** class and call the *[Connect]* method passing the server name, and if the server name is remote, the user name and password.
3. Use the **WqlConnectionManager** object to connect to the provider.

## Example

The following example method connects to the SMS Provider on a local or remote computer. If `servername` is remote, the method uses the supplied user name and password to connect to the remote computer. If you want to use the current user context, for the remote connection, change the code so that it doesn't pass the user name and password. If the connection is successful, a **WqlConnectionManager** object is returned.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```
public WqlConnectionManager Connect(string serverName, string userName, string userPassword)
{
    try
    {
        SmsNamedValuesDictionary namedValues = new SmsNamedValuesDictionary();
        WqlConnectionManager connection = new WqlConnectionManager(namedValues);

        if (System.Net.Dns.GetHostName().ToUpper() == serverName.ToUpper())
        {
            // Connect to local computer.
            connection.Connect(serverName);
        }
        else
        {
            // Connect to remote computer.
            connection.Connect(serverName, userName, userPassword);
        }

        return connection;
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to Connect. Error: " + e.Message);
        return null;
    }
    catch (UnauthorizedAccessException e)
    {
        Console.WriteLine("Failed to authenticate. Error:" + e.Message);
        return null;
    }
}

```

## Compiling the Code

### Namespaces

System

System.Collections.Generic

System.ComponentModel

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

Microsoft.ManagementConsole

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

Microsoft.ManagementConsole

## Robust Programming

The Configuration Manager exceptions that can be raised are [SmsConnectionException](/en-us/previous-versions/system-center/developer/cc147431%28v=msdn.10%29) and [SmsQueryException](/en-us/previous-versions/system-center/developer/cc147436%28v=msdn.10%29). These can be caught together with [SmsException](/en-us/previous-versions/system-center/developer/cc147433%28v=msdn.10%29).

## .NET Framework Security

[UnauthorizedAccessException](/en-us/dotnet/api/system.unauthorizedaccessexception) is raised when the wrong credentials are passed to **WqlConnectionManager.Connect**.