---
layout: Conceptual
title: SMS_CM_UpdatePackagesHistory Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cm_updatepackageshistory-server-wmi-class
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
description: The SMS_CM_UpdatePackagesHistory WMI class is used to get a list of all update packages.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bfed72fc-d853-a9b9-4b6c-7c3883eb6bfc
document_version_independent_id: 2c5e2d74-416e-b459-bd68-350e6c346fc0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/sum/sms_cm_updatepackageshistory-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/sum/sms_cm_updatepackageshistory-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/sum/sms_cm_updatepackageshistory-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b5e1000c-d9dd-0d80-c507-974ddead44c9
---

# SMS_CM_UpdatePackagesHistory Class - Configuration Manager | Microsoft Learn

The `SMS_CM_UpdatePackagesHistory` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that is used to get a list of all update packages.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CM_UpdatePackagesHistory: SMS_BaseClass
{
    String ClientVersion;
    DateTime DateCreated;
    DateTime DateReleased;
    String Description;
    String FullVersion;
    SInt32 Impact;
    DateTime LastUpdateTime;
    SInt32 LocaleID;
    String MaxCMVersion;
    String MinCMVersion;
    String MoreInfoLink;
    String Name;
    String PackageGuid;
    Sint32 PrereqFlag;
    String PrereqPackageName;
    SInt32 PrereqPackageState;
    SInt32 PublisherFlags;
    SInt32 State;
    SInt32 UpdateType;
    SInt32 WarningFlag;
};

```

## Methods

The `SMS_CM_UpdatePackagesHistory` class does not define any methods.

## Properties

`ClientVersion` Data type: `String`

Access type: Read

Qualifiers: none

The client version, if there is a client update in the package.

`DateCreated` Data type: `DateTime`

Access type: Read

Qualifiers: none

The date the update package was added to the site.

`DateReleased` Data type: `DateTime`

Access type: Read

Qualifiers: none

The date the update package was released.

`Description` Data type: `String`

Access type: Read

Qualifiers: none

A description of the update package.

`FullVersion` Data type: `String`

Access type: Read

Qualifiers: none

The full version.

`Impact` Data type: `SInt32`

Access type: Read

Qualifiers: none

Bit to indicate impact. Possible values are:

| Value | Description |
| --- | --- |
| 0x01 | Site server |
| 0x02 | Console |
| 0x04 | Client |
| 0x08 | New features |
| 0x10 | Bug fixes |

`LastUpdateTime` Data type: `DateTime`

Access type: Read

Qualifiers: none

The date and time that the state was last updated.

`LocaleID` Data type: `SInt32`

Access type: Read

Qualifiers: none

The locale ID for the localized data.

`MaxCMVersion` Data type: `String`

Access type: Read

Qualifiers: none

The maximum applicable version of Configuration Manager.

`MinCMVersion` Data type: `String`

Access type: Read

Qualifiers: none

The minimum applicable version of Configuration Manager.

`MoreInfoLink` Data type: `String`

Access type: Read

Qualifiers: none

Link to additional information about the update package.

`Name` Data type: `String`

Access type: Read

Qualifiers: none

The name of the update package.

`PackageGuid` Data type: `String`

Access type: Read

Qualifiers: [key]

A unique identifier for the package.

`PrereqFlag` Data type: `SInt32`

Access type: Read

Qualifiers: none

Flag for pre-requisites. Valid values are:

| Value | Description |
| --- | --- |
| 0x1 | Prereq only |
| 0x2 | CONTINUE\_ON\_PREREQ\_WARNING |

`PrereqPackageName` Data type: `String`

Access type: Read

Qualifiers: none

The name of the package that the current package depends on.

`PrereqPackageState` Data type: `SInt32`

Access type: Read

Qualifiers: none

The state of the package that the current package depends on.

`PublisherFlags` Data type: `SInt32`

Access type: Read

Qualifiers: none

0x2: update boot image package.

`State` Data type: `SInt32`

Access type: Read

Qualifiers: none

The overall state of the update package.

`UpdateType` Data type: `SInt32`

Access type: Read

Qualifiers: none

Package type. Possible values are:

| Value | Description |
| --- | --- |
| 0 | Regular Update |
| 1 | Weave |
| 2 | QFE |

`WarningFlag` Data type: `SInt32`

Access type: Read

Qualifiers: none

Warning flag. Possible values are:

| Value | Description |
| --- | --- |
| 0 | Bypass warning |
| 1 | Do not bypass warning |

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