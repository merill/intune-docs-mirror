---
layout: Conceptual
title: SMS_ProviderLocation Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_providerlocation-server-wmi-class
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
description: The SMS_ProviderLocation Windows Management Instrumentation (WMI) class, in Configuration Manager, identifies the location of the SMS Provider for a site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b194a4ed-91fc-9aa0-c56d-fece8c3670af
document_version_independent_id: 43c121a2-6af7-3d58-6d14-4005b3ee4900
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/sms_providerlocation-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/sms_providerlocation-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/sms_providerlocation-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9055c0b5-85dd-ab6f-9e2c-83409ca23ff2
---

# SMS_ProviderLocation Class - Configuration Manager | Microsoft Learn

The `SMS_ProviderLocation` Windows Management Instrumentation (WMI) class, in Configuration Manager, identifies the location of the SMS Provider for a site.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_ProviderLocation
{
     String Machine;
     String NamespacePath;
     Boolean ProviderForLocalSite;
     String SiteCode;
};
```

## Properties

`Machine` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the computer on which the SMS Provider resides.

`NamespacePath` Data type: `String`

Access type: Read/Write

Qualifiers: None

Full WMI path to the SMS Provider namespace.

`ProviderForLocalSite` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the SMS Provider is set as the local site server for the client.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: [key]

Site code of the site.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](class-and-property-qualifiers).

For information on using this class, see [How to Connect to an SMS Provider in Configuration Manager by Using WMI](../../core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).