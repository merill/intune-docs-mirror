---
layout: Conceptual
title: ImportMachineEntryToMultipleCollections method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/importmachineentrytomultiplecollections-method-in-class-sms_site
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
description: ImportMachineEntryToMultipleCollections method
ms.date: 2019-04-03T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 80287a2c-a627-4732-749c-a7f6d7d12351
document_version_independent_id: b72d78cc-92ad-0826-a672-3472a9fd532d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/importmachineentrytomultiplecollections-method-in-class-sms_site.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/importmachineentrytomultiplecollections-method-in-class-sms_site
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/importmachineentrytomultiplecollections-method-in-class-sms_site.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: c33d871b-bb82-cc69-1de7-d3319c10629e
---

# ImportMachineEntryToMultipleCollections method - Configuration Manager | Microsoft Learn

The `ImportMachineEntryToMultipleCollections` WMI class method in Configuration Manager imports computer information and one or more optional collections.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 ImportMachineEntryToMultipleCollections
{
    [IN]    String NetbiosName
    [IN]    String SMBIOSGUID
    [IN]    String MACAddress
    [IN]    Boolean OverwriteExistingRecord
    [IN]    String FQDN
    [IN]    String AdminPassword
    [IN]    Boolean AddToCollection
    [IN]    SMS_CollectionRule CollectionRule
    [IN]    String[] CollectionIds
    [IN]    String WTGUniqueKey
    [OUT]   Boolean MachineExists
    [OUT]   UInt32 ResourceID
    [OUT]   String SMSUniqueIdentifier
};
```

### Parameters

#### `NetbiosName`

Data type: `String`

Qualifiers: [id("0"), in]

The NetBIOS name for the computer.

#### `SMBIOSGUID`

Data type: `String`

Qualifiers: [id("1"), in]

The GUID for the system management BIOS (SMBIOS).

#### `MACAddress`

Data type: `String`

Qualifiers: [id("2"), in]

The MAC address must be for a network adapter that has a driver in Windows PE. The MAC address must be in colon format. For example, 00:00:00:00:00:00. Other formats prevent the client from receiving policy.

#### `OverwriteExistingRecord`

Data type: `Boolean`

Qualifiers: [id("3"), in]

`true` to overwrite the existing record.

#### `FQDN`

Data type: `String`

Qualifiers: [id("4"), in, optional]

Fully qualified domain name of this computer.

#### `AdminPassword`

Data type: `String`

Qualifiers: [id("7"), in, optional]

The changed password of the MEBx password that can occur during out of band provisioning.

#### `AddToCollection`

Data type: `Boolean`

Qualifiers: [id("8"), in, optional]

`true` to add the computer to a collection.

#### `CollectionRule`

Data type: `SMS_CollectionRule`

Qualifiers: [id("9"), in, optional]

Adds the collection rule to a specified collection. The default value is NULL.

#### `CollectionIds`

Data type: `String[]`

Qualifiers: [id("10"), in, optional]

The collection identifier(s) for the collection(s) that the computer is added to. The default value is empty.

#### `WTGUniqueKey`

Data type: `String`

Qualifiers: [id("11"), in, optional]

For a Windows To Go deployment, this is the USB unique key that is used to identify the client, instead of the SMBIOS and MAC address.

#### `MachineExists`

Data type: `Boolean`

Qualifiers: [id("12"), out]

`true` if the computer exists.

#### `ResourceID`

Data type: `UInt32`

Qualifiers: [id("13"), out]

Resource identifier for the computer.

#### `SMSUniqueIdentifier`

Data type: `String`

Qualifiers: [id("14"), out]

Unique identifier of Configuration Manager.

## Runtime requirements

For more information, see [Configuration Manager server runtime requirements](../../../../core/reqs/server-runtime-requirements).

## Development requirements

For more information, see [Configuration Manager server development requirements](../../../../core/reqs/server-development-requirements).