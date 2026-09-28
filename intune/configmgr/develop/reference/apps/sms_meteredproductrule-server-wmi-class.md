---
layout: Conceptual
title: SMS_MeteredProductRule Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_meteredproductrule-server-wmi-class
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
description: The SMS_MeteredProductRule WMI class is an SMS Provider server class that represents the rules that describe which files to meter.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c7eb1092-1dd5-4a4e-d124-845b3a0003eb
document_version_independent_id: fa1cea76-ec58-0cda-4f46-9342ed980225
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_meteredproductrule-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_meteredproductrule-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_meteredproductrule-server-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5f54f099-ad96-412e-c4ae-2ce891fe74c9
---

# SMS_MeteredProductRule Class - Configuration Manager | Microsoft Learn

The `SMS_MeteredProductRule` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents the rules that describe which files to meter.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MeteredProductRule : SMS_BaseClass
{
      Boolean ApplyToChildSites;
      String Comment;
      Boolean Enabled;
      String FileName;
      String FileVersion;
      UInt32 LanguageID;
      DateTime LastUpdateTime;
      String OriginalFileName;
      String ProductName;
      UInt32 RuleID;
      String SecurityKey;
      String SiteCode;
      String SourceSite;
};
```

## Methods

The `SMS_MeteredProductRule` class does not define any methods.

## Properties

`ApplyToChildSites` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` (default) if the rule is applied to child sites.

`Comment` Data type: `String`

Access type: Read/Write

Qualifiers: None

Comment describing the rule.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the rule is enabled. Data is only collected by the client if the rule is enabled.

`FileName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the file to be metered. This property is used for matching.

`FileVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

Version of the file being metered. This property is used for matching and matches to the `FileVersion` property stored in the file version information. It can contain wildcards, such as \* (match multiple characters) and ? (match a single character). An empty `FileVersion` property only matches to those executable files that have no version.

`LanguageID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [Subtype("Locale Id")]

Language ID of the rule being metered. This property matches the `Language` property stored in the file version information. If it is set to 65535, it matches any language.

`LastUpdateTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Last time the rule definition was changed.

`OriginalFileName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Original file name. This property is used for matching and matches the `OriginalFileName` property stored in the file version information. Because `FileName` is the Resource Explorer name of the file and might be changed by users, `OriginalFileName` is used to ensure that the file is metered.

`ProductName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the product being metered. This is the display name of the rule and is not used in matching.

`RuleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

ID for the rule.

`SecurityKey` Data type: `String`

Access type: Read/Write

Qualifiers: None

Security key for the rule.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: None

Site code of the site on which the rule runs. The rule applies to clients of this site and to the clients of child sites if `ApplyToChildSites` is set to `true`.

`SourceSite` Data type: `String`

Access type: Read/Write

Qualifiers: None

Site where the rule was created.

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    Software metering rules instruct the Software Metering Agent which processes to monitor on the client. Your application creates a new rule by creating an instance of this class. The following properties of this class have to be provided:
- `ProductName`
- `FileName`
- `OriginalFileName`
- `FileVersion`
- `LanguageID`
- `SiteCode`
- `ApplyToChildSites`
- `Enabled`

    The `Comment` property is optional. `OriginalFileName` can be used instead of `FileName`, both can be supplied, or `FileName` only can be supplied. If either the `FileName` value or the `OriginalFileName` value matches the file, the file is metered.

    No other properties should be supplied.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).