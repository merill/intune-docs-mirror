---
layout: Conceptual
title: SMS_PendingReRegistrationOnSiteReAssignment Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_pendingreregistrationonsitereassignment-client-wmi-class
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
description: Learn how to represent a pending re-registration at the time of site reassignment in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 2c1b1640-864a-c20d-c8c8-77a5a66f4b77
document_version_independent_id: 8cdcc19e-361f-a6e5-91d4-5f357954d26e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_pendingreregistrationonsitereassignment-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_pendingreregistrationonsitereassignment-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_pendingreregistrationonsitereassignment-client-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7170f6af-2d70-11b4-d261-0745292addb4
---

# SMS_PendingReRegistrationOnSiteReAssignment Class - Configuration Manager | Microsoft Learn

Important

This class supports the Configuration Manager 2007 infrastructure and is not intended to be used directly from your code.

The `SMS_PendingReRegistrationOnSiteReAssignment` class is a client Windows Management Instrumentation (WMI) class, in Configuration Manager, that represents a pending re-registration at the time of site reassignment.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_PendingReRegistrationOnSiteReAssignment
{
      UInt32 Flags;
      String LastAssignedSite;
      String NewAssignedSite;
};
```

## Methods

The `SMS_PendingReRegistrationOnSiteReAssignment` class does not define any methods.

## Properties

`Flags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Flags defining options for the pending re-registration.

`LastAssignedSite` Data type: `String`

Access type: Read/Write

Qualifiers: None

The site code of the last site that was assigned.

`NewAssignedSite` Data type: `String`

Access type: Read/Write

Qualifiers: None

The site code of the new site being assigned.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).