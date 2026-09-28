---
layout: Conceptual
title: SMS_StateMigration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_statemigration-server-wmi-class
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
description: An SMS Provider that contains all the state migration information for a specific computer association and exposes methods for managing an association.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: bf5ae22b-ff39-76af-8fce-3dc551f08678
document_version_independent_id: f773f098-f40b-0cb9-fb00-2c4688f7c9f2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_statemigration-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_statemigration-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_statemigration-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 10c38836-62b3-63d0-8fad-9746f46d051e
---

# SMS_StateMigration Class - Configuration Manager | Microsoft Learn

The `SMS_StateMigration` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that contains all the state migration information for a specific computer association and exposes methods for managing an association.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_StateMigration : SMS_BaseClass
{
   UInt32 MigrationBehavior;
   String MigrationID;
   UInt32 MigrationStatus;
   UInt32 MigrationType;
   UInt32 RestoreClientResourceID;
   String RestoreLastLogonUserDomain;
   String RestoreLastLogonUserName;
   String RestoreMACAddresses;
   String RestoreName;
   String SiteCode;
   UInt32 SourceClientResourceID;
   String SourceLastLogonUserDomain;
   String SourceLastLogonUserName;
   String SourceMACAddresses;
   String SourceName;
   DateTime StoreCreationDate;
   DateTime StoreDeletionDate;
   String StorePath;
   DateTime StoreReleaseDate;
   SMS_StateMigrationUserNames UserNames[];
};
```

## Methods

The following table shows the methods in `SMS_StateMigration`.

| Method | Description |
| --- | --- |
| [AddAssociation Method in Class SMS_StateMigration](addassociation-method-in-class-sms_statemigration) | Adds the association between two system resources. |
| [DeleteAssociation Method in Class SMS_StateMigration](deleteassociation-method-in-class-sms_statemigration) | Deletes the association between two system resources. |
| [GetEncryptDecryptKey Method in Class SMS_StateMigration](getencryptdecryptkey-method-in-class-sms_statemigration) | Retrieves the symmetric key that is used to encrypt and decrypt the user state. |
| [AddAssociationEx Method in Class SMS_StateMigration](addassociationex-method-in-class-sms_statemigration) | Adds the association with a specified migration behavior between two system resources. |

## Properties

`MigrationBehavior` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Migration behavior. Possible values are:

| Value | Migration behavior |
| --- | --- |
| 0 | CAPTUREANDRESTOREALL |
| 1 | CAPTUREALLRESTORESPECIFIED |
| 2 | CAPTUREANDRESTORESPECIFIED |

`MigrationID` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Unique migration ID. The default value is "".

`MigrationStatus` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration, read]

Migration status. Possible values are:

| Value | Migration status |
| --- | --- |
| 0 | NOTSTARTED |
| 1 | INPROGRESS |
| 2 | COMPLETED |

`MigrationType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [read]

The migration type used to store the user state. Possible values are:

| Value | Migration type |
| --- | --- |
| 1 | SIDEBYSIDE |
| 2 | INPLACE |

`RestoreClientResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Unique resource ID of the restore client.

`RestoreLastLogonUserDomain` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Last logon user domain of the user on the restore client.

`RestoreLastLogonUserName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Last logon user name on the restore client.

`RestoreMACAddresses` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Media access controller (MAC) addresses of the restore client.

`RestoreName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the restore client.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Site code.

`SourceClientResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: [key]

Unique ID of the source client.

`SourceLastLogonUserDomain` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Last logon user domain of the user on the source client.

`SourceLastLogonUserName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Last logon user name on the source client.

`SourceMACAddresses` Data type: `String`

Access type: Read-only

Qualifiers: [read]

MAC addresses of the source client.

`SourceName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Name of the source client.

`StoreCreationDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date and time when the state was saved. The default value is "00000000000000.000000+\*\*\*".

`StoreDeletionDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date and time when the state was deleted. The default value is "00000000000000.000000+\*\*\*".

`StorePath` Data type: `String`

Access type: Read-only

Qualifiers: [read]

The UNC path indicating the location of the state store.

`StoreReleaseDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: [read]

Date and time when the state was migrated. The default value is "00000000000000.000000+\*\*\*".

`UserNames` Data type: `SMS_StateMigrationUserNames` Array

Access type: Read-only

Qualifiers: [read, lazy]

[SMS_StateMigrationUserNames Server WMI Class](sms_statemigrationusernames-server-wmi-class) objects representing the user names to be migrated.

## Remarks

Class qualifiers for this class include:

- Secured

    For more information about both the class qualifiers and the property qualifiers that are included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

    This class represents state migration that is used in configuring sites for operating system deployment. State migration primarily affects resources, for example, memory, for the state migration point. During migration, user state and settings are copied from one computer to another as part of operating system deployment.

Note

The state migration point requires Internet Information Services (IIS) to be installed.

For an example of the use of this class, see How to Create an Association Between Two Computers in Configuration Manager.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).