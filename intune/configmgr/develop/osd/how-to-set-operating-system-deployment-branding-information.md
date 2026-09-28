---
layout: Conceptual
title: Set Operating System Deployment Branding Information - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-set-operating-system-deployment-branding-information
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
description: Learn how to set operating system deployment branding information in the configuration manager by changing the property of the client agent component section.
locale: en-us
document_id: 45f1cc71-0369-6109-b9e3-f419ad3b7c0b
document_version_independent_id: 9f061ac5-9721-9713-09f8-aab769fbab6f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-set-operating-system-deployment-branding-information.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-set-operating-system-deployment-branding-information
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-set-operating-system-deployment-branding-information.md
cmProducts: []
platformId: 90f97a4f-6184-bce0-1642-546088aab162
---

# Set Operating System Deployment Branding Information - Configuration Manager | Microsoft Learn

You set the operating system deployment branding information for the Configuration Manager client by changing the `OSDBrandingSubtitle` property of the client agent component section in the site control file.

Note

`OSDBrandingSubtitle` is encoded with BASE64 encoding.

The branding information is displayed by the task sequence when it is run on the client.

### To set operating system deployment branding information

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals) .
2. Get the client agent site control file client component object from [SMS_SCI_ClientComp Server WMI Class](../reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class).
3. Set the `OSDBrandingSubtitle` property to the value you want.
4. Commit the changes back to the site control file.

## Example

The following example method changes the operating system deployment branding text to the supplied value.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub SetOsdBranding(connection,          _
                      context,          _
                      siteCode,               _
                      brandingText)

    ' Load the site control file and get the Client Agent section.
    connection.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , context

    Query = "SELECT * FROM SMS_SCI_ClientComp " & _
            "WHERE ClientComponentName = 'Client Agent' " & _
            "AND SiteCode = '" & siteCode & "'"

    Set SCIComponentSet = connection.ExecQuery(Query, ,wbemFlagForwardOnly Or wbemFlagReturnImmediately, context)

    ' Only one instance is returned from the query.
    For Each SCIComponent In SCIComponentSet

        ' Loop through the array of embedded SMS_EmbeddedProperty instances.
        For Each vProperty In SCIComponent.Props

            ' Setting: OSDBrandingSubTitle.
            If vProperty.PropertyName = "OSDBrandingSubTitle" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value1

                ' Modify the value.
                vProperty.Value1 = brandingText
                wscript.echo "New value: " & brandingText
            End If

        Next

             ' Update the component in your copy of the site control file. Get the path
             ' to the updated object, which can be used later to retrieve the instance.
              Set SCICompPath = SCIComponent.Put_(wbemChangeFlagUpdateOnly, context)
    Next

    ' Commit the change to the actual site control file.
    Set InParams = connection.Get("SMS_SiteControlFile").Methods_("CommitSCF").InParameters.SpawnInstance_
    InParams.SiteCode = siteCode
    connection.ExecMethod "SMS_SiteControlFile", "CommitSCF", InParams, , context

End Sub
```

```c
public void SetOsdBranding(
    WqlConnectionManager connection,
    string siteCode,
    string brandingText)
{
    try
    {
        // Get the site control file client component section.
        IResultObject clientAgent = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" +
            siteCode + "',ItemName='Client Agent'");

        // Update the branding information.
        Dictionary<string, IResultObject> embeddedProperties = clientAgent.EmbeddedProperties;

        embeddedProperties["OSDBrandingSubTitle"]["Value1"].StringValue = brandingText;

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
| `connection` | - Managed: `WqlConnectionManager`- VBScript: `SWbemServices` | A valid connection to the SMS Provider. |
| `context (VBScript)` | - VBScript: `SWbemContext` | A valid context qualifier object. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using WMI](../core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) |
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

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine