---
layout: Conceptual
title: Set the Restore-Only Mode for a State Migration Point - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-set-the-restore-only-mode-for-a-state-migration-point
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
description: In Configuration Manager, you configure the operating system deployment state migration point to reject new requests to store user data by setting the SMPQuiesceState embedded property.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: bb295ad1-33c6-1076-fa92-3c419cab0f19
document_version_independent_id: 7ca6a8a5-af95-6511-336a-a6e11d920dba
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-set-the-restore-only-mode-for-a-state-migration-point.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-set-the-restore-only-mode-for-a-state-migration-point
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-set-the-restore-only-mode-for-a-state-migration-point.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 07a4e946-0cdf-7c04-548c-faa661e3beb6
---

# Set the Restore-Only Mode for a State Migration Point - Configuration Manager | Microsoft Learn

In Configuration Manager, you configure the operating system deployment state migration point to reject new requests to store user data by setting the **SMPQuiesceState** embedded property.

**SMPQuiesceState** has two possible values.

| Value | Definition |
| --- | --- |
| 0 | Restore-only mode is turned off. |
| 1 | Restore-only mode is turned on. |

### To set the restore only mode for a state migration point

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Make a connection to the state migration point resources section of the site control file.
3. Get the embedded properties.
4. Update **SMPQuiesceState**.
5. Commit the changes to the site control file.

## Example

The following example method sets the restore-only mode based on supplied value.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub SetRestoreOnlyMode(connection,          _
                       context,           _
                       siteCode,               _
                       enableRestoreOnlyMode)

    ' Load site control file and get SMS State Migration Point section.
    connection.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , context

    Query = "SELECT * FROM SMS_SCI_SysResUse " & _
            "WHERE RoleName = 'SMS State Migration Point' " & _
            "AND SiteCode = '" & siteCode & "'"

    Set SCIComponentSet = connection.ExecQuery(Query, , , context)

    ' Only one instance is returned from the query.
    For Each SCIComponent In SCIComponentSet

         ' Display state migration point server name.
         wscript.echo "SMS State Migration Point Server: " & SCIComponent.NetworkOSPath

        ' Loop through the array of embedded property instances.
        For Each vProperty In SCIComponent.Props

            ' Setting: SMPQuiesceState
            If vProperty.PropertyName = "SMPQuiesceState" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value

                ' Modify the value.
                vProperty.Value = enableRestoreOnlyMode
                wscript.echo "New value " & enableRestoreOnlyMode
            End If

        Next

             ' Update the component in your copy of the site control file. Get the path
             ' to the updated object, which could be used later to retrieve the instance.
             Set SCICompPath = SCIComponent.Put_( , context)
    Next

    ' Commit the change to the actual site control file.
    Set InParams = connection.Get("SMS_SiteControlFile").Methods_("CommitSCF").InParameters.SpawnInstance_
    InParams.SiteCode = siteCode
    connection.ExecMethod "SMS_SiteControlFile", "CommitSCF", InParams, , context
End Sub
```

```c
public void SetRestoreOnlyMode(
    WqlConnectionManager connection,
    string server,
    string siteCode,
    bool enableRestoreOnlyMode)
{
    try
    {
        // Get the site control file.
        IResultObject ro = connection.GetInstance("SMS_SCI_SysResUse.FileType=2,ItemName='[\"Display=\\\\" + server + "\\\"]MSWNET:[\"SMS_SITE=" + siteCode + "\"]\\\\" + server + "\\,SMS State Migration Point',ItemType='System Resource Usage',SiteCode='" + siteCode + "'");

        // Get the embedded properties.
        Dictionary<string, IResultObject> embeddedProperties = ro.EmbeddedProperties;

        // Set the restore only mode.
        embeddedProperties["SMPQuiesceState"]["Value"].BooleanValue = enableRestoreOnlyMode;

        ro.EmbeddedProperties = embeddedProperties;

        // Commmit the changes.
        ro.Put();
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to set restore only mode" + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `context (VBScript)` | - VBScript: `SWbemContext` | A valid context object. For more information, see [How to Add a Configuration Manager Context Qualifier by Using WMI](../core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi). |
| `server` | - Managed: `String`- VBScript: `String` | The Configuration Manager server that the state migration point is running on. |
| `siteCode` | - Managed: `String`- VBScript: `String` | The Configuration Manager site code. |
| `enableRestoreOnlyMode` | - Managed: `Boolean`- VBScript: `Integer` | Sets the restore only mode. - Managed: `true` turns restore only mode on; otherwise `false`.- VBScript: `1` turns restore mode on; otherwise `0`. |

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