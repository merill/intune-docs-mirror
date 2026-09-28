---
layout: Conceptual
title: SMS_ClientDeploymentFailureBucket Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/deploy/sms_clientdeploymentfailurebucket-server-wmi-class
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
description: Learn how to represent a client deployment failure bucket used to get the total number of clients with the same failed state message ID.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 53393847-8e5b-b2b6-db48-5be50371613d
document_version_independent_id: 77eb1f7c-8fae-3f39-a35d-73062af59880
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/deploy/sms_clientdeploymentfailurebucket-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/deploy/sms_clientdeploymentfailurebucket-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/deploy/sms_clientdeploymentfailurebucket-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b77d71c2-e51c-7c6b-c7e0-d59c415d7129
---

# SMS_ClientDeploymentFailureBucket Class - Configuration Manager | Microsoft Learn

The `SMS_ClientDeploymentFailureBucket` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a client deployment failure bucket that is used to get the total number of clients with the same failed state message ID.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientDeploymentFailureBucket: SMS_BaseClass
{
    UInt32 ClientCount;
    String CollectionID;
    UInt32 LastMessageStateID;
};

```

## Methods

The `SMS_ClientDeploymentFailureBucket` class does not define any methods.

## Properties

`ClientCount` Data type: `UInt32`

Access type: Read

Qualifiers: none

The total number of clients with the specified LastMessageStateID.

`CollectionID` Data type: `String`

Access type: Read

Qualifiers: none

The ID of the collection of which the clients are members.

`LastMessageStateID` Data type: `UInt32`

Access type: Read

Qualifiers: [key]

The ID of the last client deployment state message.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read (read-only)

    For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).