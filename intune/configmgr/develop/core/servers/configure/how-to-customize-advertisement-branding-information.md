---
layout: Conceptual
title: Customize Advertisement Branding Information - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-customize-advertisement-branding-information
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
description: You set the software distribution branding information for the Configuration Manager client by changing the SWDBrandingSubTitle property of the client agent component section in the site control file.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 9acb2e88-aaa6-82ac-3f7e-ed3ebf0b485d
document_version_independent_id: 8b6b0a08-bac9-ddff-8151-93648c86b3b9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-customize-advertisement-branding-information.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-customize-advertisement-branding-information
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-customize-advertisement-branding-information.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: d38fff54-2828-74a1-2c79-553515546ed2
---

# Customize Advertisement Branding Information - Configuration Manager | Microsoft Learn

You set the software distribution branding information for the Configuration Manager client by changing the `SWDBrandingSubTitle` property of the client agent component section in the site control file.

### To customize advertisement branding information

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../../understand/sms-provider-fundamentals).
2. Get the Client Agent site control file `Client Component` object from [SMS_SCI_ClientComp Server WMI Class](../../../reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class).
3. Set the `SWDBrandingSubtitle` property to the value you want.
4. Commit the changes back to the site control file.

## Example

The following example method changes the software distribution branding text to the supplied value.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```vbs

Sub SetAdvertBranding(swbemServices,          _
                      swbemContext,           _
                      siteCode,               _
                      brandingText)

    ' Load the site control file and get the Client Agent section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext

    Query = "SELECT * FROM SMS_SCI_ClientComp " & _
            "WHERE ClientComponentName = 'Client Agent' " & _
            "AND SiteCode = '" & siteCode & "'"

    Set SCIComponentSet = swbemServices.ExecQuery(Query, ,wbemFlagForwardOnly Or wbemFlagReturnImmediately, swbemContext)

    ' Only one instance is returned from the query.
    For Each SCIComponent In SCIComponentSet

        ' Loop through the array of embedded SMS_EmbeddedProperty instances.
        For Each vProperty In SCIComponent.Props

            ' Setting: SWDBrandingSubTitle
            If vProperty.PropertyName = "SWDBrandingSubTitle" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value1

                ' Modify the value.
                vProperty.Value1 = brandingText
                wscript.echo "New value: " & brandingText
            End If

        Next

             ' Update the component in your copy of the site control file. Get the path
             ' to the updated object, which could be used later to retrieve the instance.
              Set SCICompPath = SCIComponent.Put_(wbemChangeFlagUpdateOnly, swbemContext)
    Next

    ' Commit the change to the actual site control file.
    Set InParams = swbemServices.Get("SMS_SiteControlFile").Methods_("CommitSCF").InParameters.SpawnInstance_
    InParams.SiteCode = siteCode
    swbemServices.ExecMethod "SMS_SiteControlFile", "CommitSCF", InParams, , swbemContext

End Sub
```

```c
public void SetAdvertBranding(WqlConnectionManager connection, string siteCode,  string brandingText)
{
    try
    {
        // Get the site control file client component section.
        IResultObject clientAgent = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Client Agent'");

        // Update the branding information.
        Dictionary<string, IResultObject> embeddedProperties = clientAgent.EmbeddedProperties;

        embeddedProperties["SWDBrandingSubTitle"]["Value1"].StringValue=brandingText;

        clientAgent.EmbeddedProperties = embeddedProperties;
        // Commit the change back to the site control file.
        clientAgent.Put();

    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to set branding text: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection``swbemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `swbemContext` | - VBScript: `SWbemContext` | A valid context object. For more information, see [How to Add a Configuration Manager Context Qualifier by Using WMI](../../understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi). |
| `siteCode` | - Managed: `String`- VBScript: `String` | The site code for the Configuration Manager site. |
| `brandingText` | - Managed: `String`- VBScript: `String` | The text used to update the branding text. |

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

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](role-based-administration).