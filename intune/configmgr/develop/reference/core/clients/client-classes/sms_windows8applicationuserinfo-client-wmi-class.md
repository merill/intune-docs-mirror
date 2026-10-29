---
layout: Conceptual
title: SMS_Windows8ApplicationUserInfo Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_windows8applicationuserinfo-client-wmi-class
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
description: Learn how to define user information of an application in Configuration Manager with SMS_Windows8ApplicationUserInfo.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ee369abc-112d-763c-84bf-a621be125b22
document_version_independent_id: fcaf776f-a128-c562-df53-06a318ed2b88
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/sms_windows8applicationuserinfo-client-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/sms_windows8applicationuserinfo-client-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/sms_windows8applicationuserinfo-client-wmi-class.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/fcc3cd4a-59ea-47a2-9cc1-784142a5a25d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/d7a55faf-a992-4e27-aa3a-eadc9830e778
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 63f77794-f3ff-d77c-feab-3ca8d03ccadb
---

# SMS_Windows8ApplicationUserInfo Class - Configuration Manager | Microsoft Learn

In Configuration Manager, the `SMS_Windows8ApplicationUserInfo` class is a client Windows Management Instrumentation (WMI) class that defines user information of an application.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_Windows8ApplicationUserInfo
{
      String FullName;
      String InstallState;
      String UserAccountName;
      String UserSecurityId;
};
```

## Methods

The `SMS_Windows8ApplicationUserInfo` class does not define any methods.

## Properties

`FullName` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

Full name of the user.

`InstallState` Data type: `String`

Access type: Read-only

Qualifiers: [read]

Installation state of the package. Possible values are:

| Value | Description |
| --- | --- |
| NotInstalled | The package has not been installed. |
| Staged | The package has been downloaded. |
| Installed | The package is ready for use. |

`UserAccountName` Data type: `String`

Access type: Read-only

Qualifiers: [read]

User account name.

`UserSecurityId` Data type: `String`

Access type: Read-only

Qualifiers: [key, read]

User security identifier.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).