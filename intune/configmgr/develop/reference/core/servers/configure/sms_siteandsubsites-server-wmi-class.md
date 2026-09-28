---
layout: Conceptual
title: SMS_SiteAndSubsites Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteandsubsites-server-wmi-class
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
description: The SMS_SiteAndSubsites WMI class reads the current site and child site information.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 5f60ecab-52f2-5f28-f50a-728f741a97a4
document_version_independent_id: 191ee563-2912-af8e-ad8e-34daa9096faa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/sms_siteandsubsites-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/sms_siteandsubsites-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/sms_siteandsubsites-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 13393331-37da-9cff-e9ec-9ed935e93db3
---

# SMS_SiteAndSubsites Class - Configuration Manager | Microsoft Learn

The `SMS_SiteAndSubsites` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that reads the current site and child site information.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_SiteAndSubsites : SMS_BaseClass
{
    String ServerName;
    String SiteCode;
    String SiteName;
    String Version;
};
```

## Methods

The `SMS_SiteAndSubsites` class does not define any methods.

## Properties

`ServerName` Data type: `String`

Access type: Read

Qualifiers: [none]

The server name of the site Configuration Manager is installed on.

`SiteCode` Data type: `String`

Access type: Read

Qualifiers: [key, sizelimit("3")]

The three letter site code for the site.

`SiteName` Data type: `String`

Access type: Read

Qualifiers: [none]

The name of the site.

`Version` Data type: `String`

Access type: Read

Qualifiers: [none]

The Configuration Manager version of the current site.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).