---
layout: Conceptual
title: SMS_Subscription Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_subscription-server-wmi-class
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
description: In Configuration Manager, the SMS_Subscription Windows Management Instrumentation class is an SMS Provider server class that represents email subscriptions.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3e2d586f-55ca-53a1-b342-e32215001688
document_version_independent_id: 17179a1a-62e6-d035-c837-3433e3ee27c0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_subscription-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_subscription-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_subscription-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 96ab9442-aa79-33e2-9356-c74f0acd4bc5
---

# SMS_Subscription Class - Configuration Manager | Microsoft Learn

The `SMS_Subscription` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents email subscriptions.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Subscription : SMS_BaseClass
{
    UInt32 AlertIDs[];
    String CreatedBy;
    DateTime DateCreated;
    DateTime DateLastModified;
    String EmailAddress;
    SMS_AlertEmailTemplate EmailTemplates[];
    UInt32 ID;
    String LastModifiedBy;
    UInt32 LocaleID;
    String Name;
    UInt32 Type;
};
```

## Methods

The following table lists the methods in the `SMS_Subscription` class.

| Method | Description |
| --- | --- |
| [GetAvailableLanguages Method in Class SMS_Subscription](getavailablelanguages-method-in-class-sms_subscription) | Gets the available languages. |
| [GetTestSmtpConnectionResult Method in Class SMS_Subscription](gettestsmtpconnectionresult-method-in-class-sms_subscription) | Gets the test SMTP connection result. |
| [TestSmtpConnection Method in Class SMS_Subscription](testsmtpconnection-method-in-class-sms_subscription) | Tests the SMTP connection. |

## Properties

`AlertIDs` Data type: `UInt32 Array`

Access type: Read/Write

Qualifiers: [lazy]

Alert IDs included in the subscription.

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, sizelimit("512")]

Name of the user who created the subscription.

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Date and time when the subscription was created.

`DateLastModified` Data type: `DateTime`

Access type: Read-only

Qualifiers: [not\_null, read]

Date and time when the subscription was last modified.

`EmailAddress` Data type: `String`

Access type: Read/Write

Qualifiers: none

Email addresses.

`EmailTemplates` Data type: `SMS_AlertEmailTemplate Array`

Access type: Read/Write

Qualifiers: [lazy]

Email template for alerts included in the subscription.

`ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Identifier of the subscription.

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: [not\_null, read, sizelimit("512")]

User who last modified the subscription. The string can contain up to 512 characters.

`LocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

LocaleID of this subscription.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: none

The name of the subscription.

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Type of subscription. Possible values are:

| Value | Type |
| --- | --- |
| 1 | Alert subscriptions. |

The default value is 1.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).