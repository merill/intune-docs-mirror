---
layout: Conceptual
title: SMS_CMSiteConfiguration Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_cmsiteconfiguration-server-wmi-class
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
description: Learn how to retrieve the site's monitored configuration status, such as the SQL Server port, SQL Server Service Broker port, and SQL Server Firewall port.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: aaf90bf4-9015-4372-50fe-4cdd50970611
document_version_independent_id: 12964cd1-56cc-f044-60b9-182b16b78b9c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_cmsiteconfiguration-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_cmsiteconfiguration-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_cmsiteconfiguration-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: ae20780c-c7ae-87d7-09aa-c362a302c65b
---

# SMS_CMSiteConfiguration Class - Configuration Manager | Microsoft Learn

The `SMS_CMSiteConfiguration` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that returns the site's monitored configuration status, such as the SQL Server port, SQL Server Service Broker port, and SQL Server Firewall port.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_CMSiteConfiguration : SMS_BaseClass
{
    String Configuration;
    DateTime LastEvaluatingTime;
    UInt32 MessageID;
    String Param1;
    String Param2;
    String Param3;
    String Param4;
    String Param5;
    String Param6;
    UInt32 RoleID;
    String RoleName;
    String SiteCode;
    UInt32 State;
};
```

## Methods

The `SMS_CMSiteConfiguration` class does not define any methods.

## Properties

`Configuration` Data type: `String`

Access type: Read-only

Qualifiers: none

Configuration.

`LastEvaluatingTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: none

Last evaluation time.

`MessageID` Data type: `UInt32`

Access type: Read-only

Qualifiers: none

Message identifier.

`Param1` Data type: `String`

Access type: Read-only

Qualifiers: none

Parameter 1.

`Param2` Data type: `String`

Access type: Read-only

Qualifiers: none

Parameter 2.

`Param3` Data type: `String`

Access type: Read-only

Qualifiers: none

Parameter 3.

`Param4` Data type: `String`

Access type: Read-only

Qualifiers: none

Parameter 4.

`Param5` Data type: `String`

Access type: Read-only

Qualifiers: none

Parameter 5.

`Param6` Data type: `String`

Access type: Read-only

Qualifiers: none

Parameter 6.

`RoleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key]

Role identifier.

`RoleName` Data type: `String`

Access type: Read-only

Qualifiers: none

Role name.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: [key]

Site code.

`State` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration]

State.

| Value | State |
| --- | --- |
| 0 | Valid |
| 1 | Failed without Remediation |
| 2 | Failed with remediaton |
| 99 | Unknown |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).