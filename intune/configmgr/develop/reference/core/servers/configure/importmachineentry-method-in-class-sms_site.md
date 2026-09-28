---
layout: Conceptual
title: ImportMachineEntry Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/importmachineentry-method-in-class-sms_site
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
description: Learn how to import computer information using ImportMachineEntry class method in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6ee03bba-61e1-1f0d-8b58-3d21a4f67a28
document_version_independent_id: 7c43b439-1002-30a8-7c2f-4f57e4bb9d42
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/importmachineentry-method-in-class-sms_site.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/importmachineentry-method-in-class-sms_site
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/importmachineentry-method-in-class-sms_site.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 955e966a-1621-7a82-565d-34088b90a321
---

# ImportMachineEntry Method - Configuration Manager | Microsoft Learn

The `ImportMachineEntry` Windows Management Instrumentation (WMI) class method in Configuration Manager that imports computer information.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
uint32 ImportMachineEntry
{
    [IN]    String NetbiosName
    [IN]    String SMBIOSGUID
    [IN]    String MACAddress
    [IN]    Boolean OverwriteExistingRecord
    [IN]    String FQDN
    [IN]    String AdminPassword
    [IN]    Boolean AddToCollection
    [IN]    SMS_CollectionRule CollectionRule
    [IN]    String CollectionId
    [IN]    String WTGUniqueKey
    [OUT]   Boolean MachineExists
    [OUT]   UInt32 ResourceID
    [OUT]   String SMSUniqueIdentifier
};
```

## Parameters

`NetbiosName` Data type: `String`

Qualifiers: [id("0"), in]

The NetBIOS name for the computer.

`SMBIOSGUID` Data type: `String`

Qualifiers: [id("1"), in]

The GUID for the system management BIOS (SMBIOS).

`MACAddress` Data type: `String`

Qualifiers: [id("2"), in]

The media access controller (MAC) address. The MAC address must be for a network adapter that has a driver in Windows PE. The MAC address must be in colon format. For example, 00:00:00:00:00:00. Other formats prevent the client from receiving policy.

`OverwriteExistingRecord` Data type: `Boolean`

Qualifiers: [id("3"), in]

`true` to overwrite the existing record.

`FQDN` Data type: `String`

Qualifiers: [id("4"), in, optional]

Fully qualified domain name of this computer.

`AdminPassword` Data type: `String`

Qualifiers: [id("7"), in, optional]

The changed password of the MEBx password that can occur during out of band provisioning.

`AddToCollection` Data type: `Boolean`

Qualifiers: [id("8"), in, optional]

`true` to add the computer to a collection.

`CollectionRule` Data type: `SMS_CollectionRule`

Qualifiers: [id("9"), in, optional]

Adds the collection rule to a specified collection. The default value is NULL.

`CollectionId` Data type: `String`

Qualifiers: [id("10"), in, optional]

The collection identifier for the collection that the computer is added to. The default value is empty.

`WTGUniqueKey` Data type: `String`

Qualifiers: [id("11"), in, optional]

For a Windows To Go deployment, this is the USB unique key that is used to identify the client, instead of the SMBIOS and MAC address.

`MachineExists` Data type: `Boolean`

Qualifiers: [id("12"), out]

`true` if the computer exists.

`ResourceID` Data type: `UInt32`

Qualifiers: [id("13"), out]

Resource identifier for the computer.

`SMSUniqueIdentifier` Data type: `String`

Qualifiers: [id("14"), out]

Unique identifier of Configuration Manager.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).