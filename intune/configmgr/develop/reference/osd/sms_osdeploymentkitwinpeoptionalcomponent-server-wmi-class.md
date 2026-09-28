---
layout: Conceptual
title: SMS_OSDeploymentKitWinPEOptionalComponent Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_osdeploymentkitwinpeoptionalcomponent-server-wmi-class
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
description: In Configuration Manager, the SMS_OSDeploymentKitWinPEOptionalComponent WMI class is an SMS Provider server class that Maps Assessment and Deployment Kit versions to supported optional components.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ec24ae97-d86d-e6d9-5d03-8b230bc67ccb
document_version_independent_id: 4110df40-a49f-b2d1-0047-edda76f5f9ac
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_osdeploymentkitwinpeoptionalcomponent-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_osdeploymentkitwinpeoptionalcomponent-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_osdeploymentkitwinpeoptionalcomponent-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 739db148-8e7d-a2d7-5d6b-00ac2a6e2942
---

# SMS_OSDeploymentKitWinPEOptionalComponent Class - Configuration Manager | Microsoft Learn

The `SMS_OSDeploymentKitWinPEOptionalComponent` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that Maps Assessment and Deployment Kit (ADK) versions to supported optional components.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_OSDeploymentKitWinPEOptionalComponent : SMS_WinPEOptionalComponentInfo
{
    String Architecture;
    String DependentComponentNames[];
    UInt32 DependentIds[];
    String DeploymentKitVersion;
    Boolean IsRequired;
    UInt32 LanguageID;
    String Name;
    String RelativePath;
    UInt64 Size;
    UInt32 UniqueID;
};

```

## Methods

The `SMS_OSDeploymentKitWinPEOptionalComponent` class does not define any methods.

## Properties

`Architecture` Data type: `String`

Access type: Read

Qualifiers: none

See [SMS_WinPEOptionalComponentInfo Server WMI Class](sms_winpeoptionalcomponentinfo-server-wmi-class).

`DependentComponentNames` Data type: `String Array`

Access type: Read

Qualifiers: none

See [SMS_WinPEOptionalComponentInfo Server WMI Class](sms_winpeoptionalcomponentinfo-server-wmi-class).

`DependentIds` Data type: `UInt32 Array`

Access type: Read

Qualifiers: none

See [SMS_WinPEOptionalComponentInfo Server WMI Class](sms_winpeoptionalcomponentinfo-server-wmi-class)&gt;.

`DeploymentKitVersion` Data type: `String`

Access type: Read

Qualifiers: [not\_null]

The version of the deployment kit with which this property is associated.

`IsRequired` Data type: `Boolean`

Access type: Read

Qualifiers: none

See [SMS_WinPEOptionalComponentInfo Server WMI Class](sms_winpeoptionalcomponentinfo-server-wmi-class).

`LanguageID` Data type: `Unit32`

Access type: Read

Qualifiers: [key]

See [SMS_WinPEOptionalComponentInfo Server WMI Class](sms_winpeoptionalcomponentinfo-server-wmi-class).

`Name` Data type: `String`

Access type: Read

Qualifiers: none

See [SMS_WinPEOptionalComponentInfo Server WMI Class](sms_winpeoptionalcomponentinfo-server-wmi-class).

`RelativePath` Data type: `String`

Access type: Read

Qualifiers: none

See [SMS_WinPEOptionalComponentInfo Server WMI Class](sms_winpeoptionalcomponentinfo-server-wmi-class).

`Size` Data type: `UInt34`

Access type: Read

Qualifiers: none

See [SMS_WinPEOptionalComponentInfo Server WMI Class](sms_winpeoptionalcomponentinfo-server-wmi-class).

`UniqueID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

See [SMS_WinPEOptionalComponentInfo Server WMI Class](sms_winpeoptionalcomponentinfo-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).