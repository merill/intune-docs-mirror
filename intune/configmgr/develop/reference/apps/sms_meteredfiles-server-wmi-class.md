---
layout: Conceptual
title: SMS_MeteredFiles Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_meteredfiles-server-wmi-class
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
description: Learn how to represent metered files and implement the matching between the meter rule and the file information in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0db140b9-5c47-35fb-4a4d-7543803c1672
document_version_independent_id: 3e67d053-be7e-cbac-2eac-e1134f253a49
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/apps/sms_meteredfiles-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/apps/sms_meteredfiles-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/apps/sms_meteredfiles-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bb273337-e48e-5426-4d84-04dec98b2c3a
---

# SMS_MeteredFiles Class - Configuration Manager | Microsoft Learn

The `SMS_MeteredFiles` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents metered files and implements the matching between the meter rule and the file information.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MeteredFiles : SMS_BaseClass
{
      Boolean ApplyToChildSites;
      String Comment;
      Boolean Enabled;
      String FileName;
      String FileVersion;
      UInt32 LanguageID;
      SInt64 MeteredFileID;
      String MeteredFileName;
      String MeteredFileVersion;
      UInt32 MeteredProductID;
      UInt32 MeteredProductLanguage;
      String OriginalFileName;
      String ProductName;
      UInt32 RuleID;
      String SecurityKey;
      String SiteCode;
      String SourceSite;
};
```

## Methods

The `SMS_MeteredFiles` class does not define any methods.

## Properties

`ApplyToChildSites` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the rule is applied to child sites.

`Comment` Data type: `String`

Access type: Read/Write

Qualifiers: None

Optional comment about the rule.

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the rule is enabled.

`FileName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the file. This property matches the file name specified in the metering rule.

`FileVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

Version of the file. This property matches the version specified in the metering rule.

`LanguageID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Locale of the file. This property matches the locale specified in the metering rule.

`MeteredFileID` Data type: `SInt64`

Access type: Read/Write

Qualifiers: [key]

ID of the file that the rule meters. More information about this file can be found by matching this property value to the `FileID` value in the [SMS_ProductFileInfo Server WMI Class](sms_productfileinfo-server-wmi-class) class.

`MeteredFileName` Data type: `String`

Access type: Read/Write

Qualifiers: None

The metered file name. This property value matches the `FileName` value or the `OriginalFileName` value, depending on which file matched the metered file.

`MeteredFileVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

Version of the file that the rule meters.

`MeteredProductID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

ID of the product that the rule meters.

`MeteredProductLanguage` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Locale of the product for the file that was metered.

`OriginalFileName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Original file name to match as specified in the rule.

`ProductName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the metering rule.

`RuleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

ID of the rule.

`SecurityKey` Data type: `String`

Access type: Read/Write

Qualifiers: None

Security key for the rule.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: None

Code of the site to which the rule is targeted.

`SourceSite` Data type: `String`

Access type: Read/Write

Qualifiers: None

Code of the site that created the rule.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

Software metering rules instruct the client agent to meter the running of certain applications. The data that the agent reports contains only information about the file that was metered, not the rules that caused it to be metered. This class is used to match the metering rules with metering data by combining information about each rule and its matching properties with files that the system knows about and the properties that were matched.

The matching done by this class works the same way as the matching on the client. Usage data reported in the summary classes can be matched to the metering rules by matching the `FileID` value in the summary data with the `MeteredFileID` value in this class. In a similar manner, software inventory can be matched to the rules that could meter the inventoried applications by matching the `MeteredFileID` value in this class to the `FileID` value in the [SMS_G_System_SoftwareFile Server WMI Class](../core/clients/manage/sms_g_system_softwarefile-server-wmi-class) class.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).