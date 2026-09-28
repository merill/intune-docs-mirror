---
layout: Conceptual
title: SMS_ResourceMap Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_resourcemap-server-wmi-class
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
description: The SMS_ResourceMap Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that maps a resource type to its resource class name and display name.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ed4fbd3a-d9ee-a9e3-c38b-312222b34722
document_version_independent_id: 205fe929-2263-776e-0271-b44d1bd95fb3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/manage/sms_resourcemap-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/manage/sms_resourcemap-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/manage/sms_resourcemap-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 141fbee9-f05e-73ab-91a6-79a3acb9723e
---

# SMS_ResourceMap Class - Configuration Manager | Microsoft Learn

The `SMS_ResourceMap` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that maps a resource type to its resource class name and display name.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ResourceMap : SMS_BaseClass
{
     String DisplayName;
     String ResourceClassName;
     UInt32 ResourceType;
};
```

## Methods

The following table lists the methods in `SMS_ResourceMap`.

| Method | Description |
| --- | --- |
| [GetClassesWithData Method in Class SMS_ResourceMap](getclasseswithdata-method-in-class-sms_resourcemap) | Gets the names of the classes that have inventory data for a resource. |
| [Refresh Method in Class SMS_ResourceMap](refresh-method-in-class-sms_resourcemap) | Updates the resource and inventory class definitions. |

## Properties

`DisplayName` Data type: **String**

Access type: Read/Write

Qualifiers: None

Name displayed in the Configuration Manager console to represent the resource class name. For a list of the default resource display names, see the `ResourceType` property.

`ResourceClassName` Data type: **String**

Access type: Read/Write

Qualifiers: None

Class name of the resource. For a list of the default resource class names, see the `ResourceType` property.

`ResourceType` Data type: **UInt32**

Access type: Read/Write

Qualifiers: [key]

Type of resources on the site. Possible values are:

| Resource type | Display name | Class |
| --- | --- | --- |
| 3 | User Group | `SMS_R_UserGroup` |
| 4 | User | `SMS_R_User` |
| 5 | System | `SMS_R_System` |
| See the following Note | IP Network | `SMS_R_IPNetwork` |

Note

The IP network resource type might not have a resource type value of 6. Its value depends on when Network Discovery was initiated relative to the discovery of new architectures by the Discovery Data Manager. The resource type value is 6 if the Data Discovery Manager discovered a new architecture before network discovery was initiated.

## Remarks

Class qualifiers for this class include:

- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).