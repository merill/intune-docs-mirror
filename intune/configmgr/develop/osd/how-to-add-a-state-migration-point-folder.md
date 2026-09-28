---
layout: Conceptual
title: Add a State Migration Point Folder - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-state-migration-point-folder
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
description: Add an operating system deployment state migration point folder by adding the folder description to the Directories embedded property list.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 389297ef-332e-9283-2781-017a11159bbe
document_version_independent_id: a3b0aeba-c86a-0cbf-5792-03ae674a3ee4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-add-a-state-migration-point-folder.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-add-a-state-migration-point-folder
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-add-a-state-migration-point-folder.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: ef781a34-2965-66b5-57d9-f206cee49068
---

# Add a State Migration Point Folder - Configuration Manager | Microsoft Learn

In Configuration Manager, you add an operating system deployment state migration point folder by adding the folder description to the `Directories` embedded property list.

The folder description is a string that defines the following information.

| Value | Description |
| --- | --- |
| `Directory` | The name of the folder. |
| `MaxClients` | The maximum number of clients supported. |
| `MinDiskSpace` | The minimum disk space required. |
| `MinDiskSpaceUnit` | The minimum disk space units. 1 - MB 2 - GB 3 - Percentage |

### To add a state migration point folder

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Make a connection to the state migration point resources section of the site control file.
3. Get the `Directories` embedded properties list.
4. Update the `Directories` embedded property with new folder.
5. Commit the changes to the site control file.

## Example

The following example method adds a new folder to the state migration point.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub AddSmpFolder( connection, _
    context,              _
    directory,            _
     maxClients,          _
     minDiskSpace,        _
     minDiskSpaceUnit,    _
    siteCode)

    Dim InParams
    Dim smpSettings
    Dim found

     ' Format the directories string.
     smpSettings = "Directory=" + directory + ";MaxClients=" + _
     CStr(maxClients) + ";MinDiskSpace=" + CStr(minDiskSpace) + _
     ";MinDiskSpaceUnit=" + CStr(minDiskSpaceUnit) + ";"

     Set InParams = connection.Get("SMS_SiteControlFile").Methods_("RefreshSCF").InParameters.SpawnInstance_
InParams.SiteCode = siteCode
connection.ExecMethod "SMS_SiteControlFile", "RefreshSCF", InParams, , context

    Query = "SELECT * FROM SMS_SCI_SysResUse " & _
            "WHERE RoleName = 'SMS State Migration Point' " & _
            "AND SiteCode = '" & siteCode & "'"

    found = false

    Set SCIComponentSet = connection.ExecQuery(Query, , , context)

    For Each SCIComponent In SCIComponentSet
        For Each vProperty in SCIComponent.PropLists

            WScript.Echo vProperty.PropertyListName

            if   vProperty.PropertyListName = "Directories" Then

                Dim  directories
                Dim i

                found = true

                ' Resize the array to accommodate the new directory.
                ReDim  directories(UBound (vProperty.Values)+1)

                for i  = 0 to UBound(vProperty.Values)
                    directories(i) = vProperty.Values(i)
                Next

                directories(ubound (directories))= smpSettings
                vProperty.Values = directories

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
public void AddSmpFolder(
    WqlConnectionManager connection,
    string directory,
    int maxClients,
    int minDiskSpace,
    int minDiskSpaceUnit,
    string serverName,
    string siteCode)
{
    try
    {
        // Set up folder string.
        string smpSettings = "Directory=" +
            directory +
            ";MaxClients=" +
            maxClients.ToString(CultureInfo.InvariantCulture) +
            ";MinDiskSpace=" +
            minDiskSpace.ToString(CultureInfo.InvariantCulture) +
            ";MinDiskSpaceUnit=" +
            minDiskSpaceUnit.ToString(CultureInfo.InvariantCulture) +
            ";";

        // Get state migration point properties from site control file.
        IResultObject ro = connection.GetInstance(
            "SMS_SCI_SysResUse.FileType=2,ItemName='[\"Display=\\\\" +
            serverName +
            "\\\"]MSWNET:[\"SMS_SITE=" +
            siteCode + "\"]\\\\" +
            serverName +
            "\\,SMS State Migration Point',ItemType='System Resource Usage',SiteCode='" +
            siteCode +
            "'"
            );

        // Get directories.
        Dictionary<string, IResultObject> embeddedPropertyLists = ro.EmbeddedPropertyLists;

        string[] directories = embeddedPropertyLists["Directories"]["Values"].StringArrayValue; // Current directories.

        List<string> directoriesList = new List<string>(); // convert to list.
        foreach (string directoryName in directories)
        {
            directoriesList.Add(directoryName);
        }

        directoriesList.Add(smpSettings);

        // Update the embedded property list.
        embeddedPropertyLists["Directories"]["Values"].StringArrayValue = directoriesList.ToArray();

        ro.EmbeddedPropertyLists = embeddedPropertyLists;

        // Commit changes.
        ro.Put();
    }
    catch (SmsException e)
    {
        Console.WriteLine("failed to update SMP settings" + e.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `context (VBScript)` | - VBScript: `SWbemContext` | A valid context object. For more information, see [How to Add a Configuration Manager Context Qualifier by Using WMI](../core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi). |
| `directory` | - Managed: `String`- VBScript: `String` | The folder to be added. |
| `maxClients` | - Managed: `Integer`- VBScript: `Integer` | The maximum number of supported clients. |
| `minDiskSpace` | - Managed: `Integer`- VBScript: `Integer` | The minimum disk space. |
| `minDiskSpaceUnit` | - Managed: `Integer`- VBScript: `Integer` | The minimum disk space unit. |
| `serverName` | - Managed: `String`- VBScript: `String` | The Configuration Manager server that the state migration point is running on. |
| `siteCode` | - Managed: `String`- VBScript: `String` | The site code for the site that is running the state migration point site role. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

System.Globalization

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).