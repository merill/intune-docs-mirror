---
layout: Conceptual
title: SMS_MigrationSourceSite Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/sms_migrationsourcesite-server-wmi-class
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
description: Learn how the SMS_MigrationSourceSite class is an SMS Provider server class, in Configuration Manager, that represents a site in the source hierarchy.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 3fbcb0f3-e25d-7db7-c14d-9568b6d041fe
document_version_independent_id: 9b87f2c6-29ed-a49b-8578-4ca7412ef17e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/migration/sms_migrationsourcesite-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/migration/sms_migrationsourcesite-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/migration/sms_migrationsourcesite-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: c57e6a22-738d-1283-9723-ebc0482a4c0e
---

# SMS_MigrationSourceSite Class - Configuration Manager | Microsoft Learn

The `SMS_MigrationSourceSite` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that represents a site in the source hierarchy.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_MigrationSourceSite : SMS_BaseClass
{
    String FQDN;
    Boolean IsCentral;
    Boolean IsConfigured;
    Boolean IsDecommissioned;
    Boolean IsDeleted;
    String ParentSiteCode;
    String ParentSiteServer;
    String SiteCode;
    UInt32 SiteID;
    UInt32 SiteType;
    String SourceSiteFQDN;
    String Version;
};
```

## Methods

The `SMS_MigrationSourceSite` class does not define any methods.

## Properties

`FQDN` Data type: `String`

Access type: Read-only

Qualifiers: none

FQDN of the source Site Server (deprecated).

`IsCentral` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if the source site is a central site.

`IsConfigured` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if the source site is configured.

`IsDecommissioned` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if the site has stopped gathering data.

`IsDeleted` Data type: `Boolean`

Access type: Read-only

Qualifiers: none

`true` if the source site is deleted.

`ParentSiteCode` Data type: `String`

Access type: Read-only

Qualifiers: none

The site code of the parent site of the source site.

`ParentSiteServer` Data type: `String`

Access type: Read-only

Qualifiers: none

The site server name of the parent site of the source site.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: none

The source site code.

`SiteID` Data type: `UInt32`

Access type: Read-only

Qualifiers: [key]

The source site ID.

`SiteType` Data type: `UInt32`

Access type: Read-only

Qualifiers: [enumeration]

See [SMS_SCI_SiteDefinition Server WMI Class](../servers/configure/sms_sci_sitedefinition-server-wmi-class).

`SourceSiteFQDN` Data type: `String`

Access type: Read-only

Qualifiers: none

The FQDN of the source site server.

`Version` Data type: `String`

Access type: Read-only

Qualifiers: none

The version of the source site.

This information applies to System Center 2012 Configuration Manager SP1 or later, and System Center 2012 R2 Configuration Manager or later.

## Remarks

All of the instances are gathered from the Configuration Manager database, except for the first one which is created when you specify the source hierarchy. Each instance carries basic information for the source site, such as the parent site code, the site type and the FQDN of the site.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../core/reqs/server-development-requirements).