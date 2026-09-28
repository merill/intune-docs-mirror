---
layout: Conceptual
title: SMS_SupportedPlatforms Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_supportedplatforms-server-wmi-class
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
description: Learn how to represent the platforms that Configuration Manager supports using the SMS_SupportedPlatforms.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2125351f-00ee-c6f0-d4b0-f08168dd67ba
document_version_independent_id: 6e6247a1-a816-28d4-f9ce-c8b02221b327
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_supportedplatforms-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_supportedplatforms-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_supportedplatforms-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 98158f49-f36c-6898-162b-d862d840ac33
---

# SMS_SupportedPlatforms Class - Configuration Manager | Microsoft Learn

The `SMS_SupportedPlatforms` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the platforms (operating system, architecture, and versions) that Configuration Manager supports.

## Syntax

```
Class SMS_SupportedPlatforms : SMS_BaseClass
{
      String CI_UniqueID;
      String Condition;
      String DisplayText;
      Boolean IsSupported;
      String OSMaxVersion;
      String OSMinVersion;
      String OSName;
      String OSPlatform;
      String ResourceDll;
      UInt32 StringId;
};
```

## Methods

The following table lists the methods in the `SMS_SupportedPlatforms` class.

| Method | Description |
| --- | --- |
| [Enable Method in Class SMS_SupportedPlatforms](enable-method-in-class-sms_supportedplatforms) | Enables or disables the platforms. |

## Properties

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: none

The unique ID of the Configuration Item that defines the platform rules.

`Condition` Data type: `String`

Access type: Read/Write

Qualifiers: None

The XML data that specifies the WQL that the client uses to check the supported platforms.

`DisplayText` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the platform that humans can read. It is used if the resource string does not exist.

`IsSupported` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true`, if the platform is supported as client operating system.

`OSMaxVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [key, Not\_null]

Highest version number for the platform. A version of 99.99.9999.9999 denotes all future versions.

`OSMinVersion` Data type: `String`

Access type: Read/Write

Qualifiers: [key, Not\_null]

Lowest version number for the platform. A version of 0.00.0000.0 denotes all previous versions.

`OSName` Data type: `String`

Access type: Read/Write

Qualifiers: [key, Not\_null]

Name of the operating system for the platform, for example, "Win NT".

`OSPlatform` Data type: `String`

Access type: Read/Write

Qualifiers: [key, Not\_null]

Name of the computer architecture for the platform, for example, I386.

`ResourceDll` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the resource DLL containing the localized name of the platform.

`StringId` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

String ID in the resource DLL containing the localized name of the platform.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

This class is populated when Configuration Manager is installed. Your application cannot add, update, or delete instances of this class by using WMI. However, new instances are added to the class when a package definition file is processed that contains a platform that is not identified by a class instance.

Your application uses the information contained in this class to populate `SMS_OS_Details` objects. For more information, see the `SupportedOperatingSystems` property of [SMS_Program Server WMI Class](sms_program-server-wmi-class).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).