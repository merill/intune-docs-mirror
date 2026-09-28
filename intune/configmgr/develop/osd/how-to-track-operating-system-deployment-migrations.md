---
layout: Conceptual
title: Track OS Deployment Migrations - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-track-operating-system-deployment-migrations
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
description: The StoreCreationDate, StoreDeletionDate, and StoreReleaseDate properties can be used to identify the current state of the migration.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 6634bc43-716b-ab97-bc9f-39ce55086e79
document_version_independent_id: 0d4af33b-0582-3b16-44b6-925ece0dc0c1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-track-operating-system-deployment-migrations.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-track-operating-system-deployment-migrations
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-track-operating-system-deployment-migrations.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: f5efb667-4ba6-af3e-9b9a-e0985ba9e896
---

# Track OS Deployment Migrations - Configuration Manager | Microsoft Learn

You track Configuration Manager operating system migrations by inspecting the [SMS_StateMigration](../reference/osd/sms_statemigration-server-wmi-class) class.

The `StoreCreationDate`, `StoreDeletionDate`, and `StoreReleaseDate` properties can be used to identify the current state of the migration.

### To track state migrations

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get an instance of [SMS_StateMigration](../reference/osd/sms_statemigration-server-wmi-class).
3. Calculate the current migration state using the `StoreCreationDate`, `StoreDeletionDate`, and `StoreReleaseDate` properties.

## Example

The following example method enumerates through all migrations and determines whether they are in progress.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub MigrationState(connection)

    Dim migrations
    Dim migration
    Dim inProgress
    Dim zeroTime

    zeroTime = "00000000000000.000000+***"

    Set migrations = connection.ExecQuery( "Select * From SMS_StateMigration")

    For Each migration in Migrations
        inProgress=False

        If migration.StoreCreationDate<>zeroTime Then
            If migration.StoreReleaseDate = zeroTime Then
                inProgress=True
            Else If migration.StoreDeletionDate = zeroTime Then
                inProgress = True
            Else
                inProgress = false
            End If
        End If
        Else
            inProgress=False
        End If

        WScript.StdOut.Write "Migration " + migration.MigrationID
        If inProgress = True Then
            Wscript.Echo " is in progress"
        Else
            WScript.Echo " is not in progress"
        End If
    Next

End Sub
```

```c
public void MigrationState(WqlConnectionManager connection)
{
    try
    {
        IResultObject migrations =
            connection.QueryProcessor.ExecuteQuery("Select * from SMS_StateMigration");

        string zeroTime = "00000000000000.000000+***";

        foreach (IResultObject migration in migrations)
        {
            Boolean inProgress = false;

            if (migration["StoreCreationDate"].DateTimeValue.Equals(zeroTime) == false)
            {
                if (migration["StoreReleaseDate"].DateTimeValue.Equals(zeroTime) == true)
                {
                    inProgress = true;
                }
                else if (migration["StoreDeletionDate"].DateTimeValue.Equals(zeroTime) == true)
                {
                    inProgress = true;
                }
                else
                {
                    inProgress = false;
                }
            }
            else
            {
                inProgress = false;
            }

            Console.Write("Migration " + migration["MigrationID"].StringValue);
            if (inProgress)
            {
                Console.WriteLine(" is in progress");
            }
            else
            {
                Console.WriteLine(" is not in progress");
            }
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed while displaying migration state: " + e.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).