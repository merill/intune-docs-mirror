---
layout: Conceptual
title: Create queries - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/create-queries
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
description: Discover how to create and import queries in Configuration Manager. Includes example queries and tips.
ms.date: 2021-04-27T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 24d681b3-cef8-b09b-68c5-0a76239a5a7f
document_version_independent_id: b49e8656-c979-6de2-8238-ac6321a0c545
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/create-queries.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/create-queries
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/create-queries.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 274e4cd6-1496-71d7-5ade-85296e3d40c6
---

# Create queries - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article describes how to create and import queries in Configuration Manager.

## Create a query

Use this procedure to create a query in Configuration Manager.

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, select **Queries**. On the **Home** tab, in the **Create** group, select **Create Query**.
3. On the **General** tab of the **Create Query Wizard**, specify a unique name and, optionally, a comment for the query.
4. If you want to import an existing query to use as a basis for the new query, select **Import Query Statement**. In the **Browse Query** dialog box, select a query that you want to import, and then select **OK**.
5. In the **Object Type** list, select the type of object that you want the query to return. This table describes some examples of the types of objects you can search for:

    | Object type | Description |
    | --- | --- |
    | **System Resource** | Use to search for typical system attributes, like the NetBIOS name of a device, the client version, the client IP address, and Active Directory Domain Services information. |
    | **User Resource** | Use to search for typical user information, like user names, user group names, and security group names. |
    | **Deployment** | Use to search for typical attributes of a deployment, like the deployment name, the schedule, and the collection that it was deployed to. |
6. Select **Edit Query Statement** to open the &lt;Query Name&gt; **Statement Properties** dialog box.
7. On the **General** tab of the &lt;Query Name&gt; **Statement Properties** dialog box, specify the attributes that the query returns and how they should be displayed. Select the **New** icon to add a new attribute. You can also select **Show Query Language** to enter or edit the query directly in WMI Query Language (WQL). For examples of WMI queries, see the Example WQL queries section in this article.

    - You can use the following reference documentation to help you construct your own WQL queries:
        - [WQL (SQL for WMI)](/en-us/windows/win32/wmisdk/wql-sql-for-wmi)
        - [WHERE Clause](/en-us/windows/win32/wmisdk/where-clause)
        - [WQL Operators](/en-us/windows/win32/wmisdk/wql-operators)
    - Starting in Configuration Manager 2010, you can preview the results when you're creating or editing a query for collection membership. In the **Query Statement Properties**, select the green triangle to show the **Query Results Preview** window. Select **Stop** if you want to stop a long running query.
8. On the **Criteria** tab of the &lt;Query Name&gt; **Statement Properties** dialog box, specify criteria that are used to refine the results of the query. For example, you could return only resources that have a site code of **XYZ**. You can configure multiple criteria for a query.

    Important

    If you create a query that contains no criteria, the query will return all devices in the **All Systems** collection.
9. On the **Joins** tab of the &lt;Query Name&gt; **Statement Properties** dialog box, you can combine data from two different attributes into your query results. Although Configuration Manager automatically creates query joins when you choose different attributes for your query result, the **Joins** tab provides more advanced options. Configuration Manager supports these attribute classes:

    | Join type | Description |
    | --- | --- |
    | Inner | Displays only matching results. Always used by joins that are created automatically. |
    | Left | Displays all results for the base attribute and only the matching results for the join attribute. |
    | Right | Displays all results for the join attribute and only the matching results for the base attribute. |
    | Full | Displays all results for both the base attribute and the join attribute. |

    For more information about how to use join operations, see the SQL Server documentation.
10. Select **OK** to close the &lt;Query Name&gt; **Statement Properties** dialog box.
11. On the **General** tab of the **Create Query Wizard**, specify that the results of the query aren't limited to the members of a collection, that they are limited to the members of a specified collection, or that a prompt for a collection appears each time the query is run.
12. Complete the wizard to create the query. The new query appears in the **Queries** node in the **Monitoring** workspace.

## Import a query

Use this procedure to import a query into Configuration Manager. For information about how to export queries, see [How to manage queries](manage-queries).

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, select **Queries**. On the **Home** tab, in the **Create** group, select **Import Objects**.
3. On the **MOF File Name** page of the **Import Objects Wizard**, select **Browse** to select the Managed Object Format (MOF) file that contains the query that you want to import.
4. Review the information about the query to be imported and then complete the wizard. The new query appears on the **Queries** node in the **Monitoring** workspace.

## Example WQL queries

This section contains example WQL queries that you can use in your hierarchy or modify for other purposes. To use these queries, select **Show Query Language** in the **Query Statement Properties** dialog box. Then copy and paste the query into the **Query Statement** field.

Tip

Use the wildcard character `%` to signify any string of characters. For example, `%Visio%` returns Microsoft Office Visio 2010.

### Computers that run Windows 10

Use the following query to return the NetBIOS name and operating system version of all computers that run Windows 10.

```WQL
select SMS_R_System.NetbiosName,
SMS_R_System.OperatingSystemNameandVersion from
SMS_R_System where
SMS_R_System.OperatingSystemNameandVersion like "%Workstation 10%"
```

### Computers with a specific software package installed

Use the following query to return the NetBIOS name and software package name of all computers that have a specific software package installed. This example returns all computers with a version of Microsoft Visio installed. Replace `Microsoft%Visio%` with the software package that you want to query for.

Tip

This query searches for the software package by using the names that are displayed in the programs list in Windows Control Panel.

```WQL
select SMS_R_System.NetbiosName,
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName from
SMS_R_System inner join SMS_G_System_ADD_REMOVE_PROGRAMS on
SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceId =
SMS_R_System.ResourceId where
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "Microsoft%Visio%"
```

### Computers in a specific Active Directory Domain Services organizational unit

Use the following query to return the NetBIOS name and organizational unit (OU) name of all computers in a specified OU. Replace the text `OU Name` with the name of the OU that you want to query for.

```WQL
select SMS_R_System.NetbiosName,
SMS_R_System.SystemOUName from
SMS_R_System where
SMS_R_System.SystemOUName = "OU Name"
```

### Computers with a specific NetBIOS name

Use the following query to return the NetBIOS name of all computers that begin with a specific string of characters. In this example, the query returns all computers with a NetBIOS name that begins with `ABC`.

```WQL
select SMS_R_System.NetbiosName from
SMS_R_System where SMS_R_System.NetbiosName like "ABC%"
```

### Devices of a specific type

Device types are stored in the Configuration Manager database under the resource class **sms\_r\_system** and the attribute name **AgentEdition**. Use this query to retrieve only the devices that match the agent edition of the device type that you specify:

```WQL
Select SMS_R_System.ClientEdition from SMS_R_System where SMS_R_System.ClientEdition = <Device ID>
```

Use one of these values for &lt;Device ID&gt;:

| Device type | Value of AgentEdition |
| --- | --- |
| Windows desktop or laptop computer | 0 |
| Windows ARM-based device (running Windows RT) | 1 |
| Windows Mobile 6.5 | 2 |
| Nokia Symbian | 3 |
| Windows Phone | 4 |
| Mac computer | 5 |
| Windows Embedded | 7 |
| Intel system on a chip | 12 |
| Microsoft HoloLens (MDM) | 15 |
| Microsoft Surface Hub (MDM) | 16 |

Note

Values that aren't listed in this table are associated with devices that are no longer supported.

For example, if you want to return only Mac computers, use this query:

```WQL
Select SMS_R_System.ClientEdition from SMS_R_System where SMS_R_System.ClientEdition = 5
```

### Devices that are co-managed

```WQL
select SMS_R_SYSTEM.ResourceID, SMS_R_SYSTEM.ResourceType, SMS_R_SYSTEM.Name,
SMS_R_SYSTEM.SMSUniqueIdentifier, SMS_R_SYSTEM.ResourceDomainORWorkgroup, SMS_R_SYSTEM.Client
from SMS_R_System
inner join SMS_Client_ComanagementState on SMS_Client_ComanagementState.ResourceId = SMS_R_System.ResourceId
where SMS_Client_ComanagementState.ComgmtPolicyPresent = 1 AND SMS_Client_ComanagementState.MDMEnrolled = 1 AND MDMProvisioned = 1
```