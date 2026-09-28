---
layout: Conceptual
title: Create a Deployment Template - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-create-a-deployment-template
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
description: Create a software updates deployment template in Configuration Manager by creating an instance of the SMS_Template class and populating the properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: fe5ebb5a-24eb-65c2-1eee-bf2b12ddfaf7
document_version_independent_id: 7f616fb1-328b-9002-c43d-82c21ca21b67
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/how-to-create-a-deployment-template.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/how-to-create-a-deployment-template
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/how-to-create-a-deployment-template.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2bb407c5-c939-4f7a-9174-27da19279675
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6eda2a8b-e231-4335-b766-c055ea6025a6
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f5e15ef3-cdd7-43cb-8164-d36d8a1c1acf
---

# Create a Deployment Template - Configuration Manager | Microsoft Learn

You create a software updates deployment template, in Configuration Manager, by creating an instance of the `SMS_Template` class and populating the properties.

### To create a deployment template

1. Set up a connection to the SMS Provider.
2. Create the new template object by using the `SMS_Template` class.
3. Populate the new template properties.
4. Save the new template and properties.

## Example

The following example method shows how to create a software updates deployment template by using the `SMS_Template` class and class properties.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

Note

In the following code examples, the template settings are passed into the method by using a string variable called deploymentTemplateSettings. The template settings are stored in an XML structure.

VB Template Setting Example (one long string):

```xml
deploymentTemplateSettings = "<TemplateDescription xmlns:xsi=""http://www.w3.org/2001/XMLSchema-instance"" xmlns:xsd=""http://www.w3.org/2001/XMLSchema""> <CollectionId>SMS00001</CollectionId> <IncludeSub>true</IncludeSub> <AttendedInstall>true</AttendedInstall> <UTC>true</UTC> <Duration>2</Duration> <DurationUnits>Weeks</DurationUnits> <SuppressServers>Unchecked</SuppressServers> <SuppressWorkstations>Unchecked</SuppressWorkstations> <AllowRestart>false</AllowRestart> <Deploy2003>true</Deploy2003> <CollectImmediately>false</CollectImmediately> <LocalDPOption>DownloadAndInstall</LocalDPOption> <RemoteDPOption>DownloadAndInstall</RemoteDPOption> <DisableMomAlert>false</DisableMomAlert> <GenerateMomAlert>false</GenerateMomAlert> <UseRemoteDP>false</UseRemoteDP> <UseUnprotectedDP>false</UseUnprotectedDP> </TemplateDescription>"
```

C# Template Setting Example (the same template settings and still passed as a string, but the XML structure is more obvious):

```xml
string deploymentTemplateSettings =
  @"<TemplateDescription xmlns:xsi=""http://www.w3.org/2001/XMLSchema-instance"" xmlns:xsd=""http://www.w3.org/2001/XMLSchema"">
  <CollectionId>SMS00001</CollectionId>
  <IncludeSub>true</IncludeSub>
  <AttendedInstall>true</AttendedInstall>
  <UTC>true</UTC>
  <Duration>2</Duration>
  <DurationUnits>Weeks</DurationUnits>
  <SuppressServers>Unchecked</SuppressServers>
  <SuppressWorkstations>Unchecked</SuppressWorkstations>
  <AllowRestart>false</AllowRestart>
  <Deploy2003>true</Deploy2003>
  <CollectImmediately>false</CollectImmediately>
  <LocalDPOption>DownloadAndInstall</LocalDPOption>
  <RemoteDPOption>DownloadAndInstall</RemoteDPOption>
  <DisableMomAlert>false</DisableMomAlert>
  <GenerateMomAlert>false</GenerateMomAlert>
  <UseRemoteDP>false</UseRemoteDP>
  <UseUnprotectedDP>false</UseUnprotectedDP>
  </TemplateDescription>";
```

```vbs

Sub CreateSUMDeploymentTemplate(connection,              _
                                 newTemplateName,         _
                                 newTemplateDescription,  _
                                 newTemplateSettings,     _
                                 newTemplateType)

    ' Create the new Template object.
    Set newSUMTemplate = connection.Get("SMS_Template").SpawnInstance_

    ' Populate the SMS_Template properties.
    ' Note: The template name (newTemplateName) must be unique.
    newSUMTemplate.Name = newTemplateName
    newSUMTemplate.Description = newTemplateDescription
    newSUMTemplate.Data = newTemplateSettings
    newSUMTemplate.Type = newTemplateType

    ' Save the new template and properties.
    newSUMTemplate.Put_

    ' Output the new template name.
    Wscript.Echo "Created new template: " & newTemplateName

 End Sub

```

```c

public void CreateSUMDeploymentTemplate(WqlConnectionManager connection,
                                        string newTemplateName,
                                        string newTemplateDescription,
                                        string newTemplateSettings,
                                        int newTemplateType)
{
    try
    {
        // Create the template object.
        IResultObject newSUMTemplate = connection.CreateInstance("SMS_Template");

        // Populate the new template properties.
        // Note: The template name (newTemplateName) must be unique.
        newSUMTemplate["Name"].StringValue = newTemplateName;
        newSUMTemplate["Description"].StringValue = newTemplateDescription;
        newSUMTemplate["Data"].StringValue = newTemplateSettings;
        newSUMTemplate["Type"].IntegerValue = newTemplateType;

        // Save the new template and the new template properties.
        newSUMTemplate.Put();

        // Output the new template name.
        Console.WriteLine("Created template: " + newTemplateName);
    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed to create template. Error: " + ex.Message);
        throw;
    }
}

```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `newTemplateName` | - Managed: `String`- VBScript: `String` | The new template name. The template name must be unique. |
| `newTemplateDescription` | - Managed: `String`- VBScript: `String` | The description for the new template. |
| `newTemplateSettings` | - Managed: `String`- VBScript: `String` | The new template settings. The settings are in an XML structure, stored as a string.<br>- **CollectionId**The collection for the software update deployment.<br>    - A valid collection ID.<br>- **IncludeSub**Include members of subcollections.<br>    - `true`<br>    - `false`<br>- **AttendedInstall**Display software update notifications on clients (false will suppress notifications).<br>    - `true`<br>    - `false`<br>- **UTC**Use Coordinated Universal Time (UTC) instead of client local time.<br>    - `true`<br>    - `false`<br>- **Duration**Duration of the deployment.<br>    - 1-24 (hours)<br>    - 1-365 (days)<br>    - 1-4 (weeks)<br>    - 1-12 (months)<br>- **DurationUnits**Duration units.<br>    - hours<br>    - days<br>    - weeks<br>    - months<br>- **SuppressServers**Suppress the system restart on servers.<br>    - Checked<br>    - Unchecked<br>- **SuppressWorkstations**Suppress the system restart on workstations.<br>    - Checked<br>    - Unchecked<br>- **AllowRestart**Allow system restart outside of maintenance windows (for both servers and workstations).<br>    - `true`<br>    - `false`<br>- **Deploy2003**Deploy software updates to SMS 2003 clients.<br>    - `true`<br>    - `false`<br>- **CollectImmediately** (SMS 2003 client specific)Collect hardware inventory immediately after installing software updates.<br>    - `true`<br>    - `false`<br>- **LocalDPOption** (SMS 2003 client specific)Specify whether to download the update source files before running the installation when a distribution point is available locally.<br>    - DownloadAndInstall<br>    - InstallFromDP<br>- **RemoteDPOption** (SMS 2003 client specific)Specify whether to download the update source files before running the installation when no distribution point is available locally.<br>    - DownloadAndInstall<br>    - InstallFromDP<br>- **DisableMomAlert**Disable Operations Manager alerts while software updates run.<br>    - `true`<br>    - `false`<br>- **GenerateMomAlert**Generate Operations Manager alert when a software update installation fails.<br>    - `true`<br>    - `false`<br>- **UseRemoteDP**Download software updates from use a remote distribution point (even when a client is connected within a slow or unreliable network boundary).<br>    - `true`<br>    - `false`<br>- **UseUnprotectedDP**Download software updates from a unprotected distribution point (when updates are not available from any protected distribution point).<br>    - `true`<br>    - `false` |
| `newTemplateType` | - Managed: `Integer`- VBScript: `Integer` | The new template type. Currently the only possible value is: - `0` (SUM\_DEPLOYMENT) |

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