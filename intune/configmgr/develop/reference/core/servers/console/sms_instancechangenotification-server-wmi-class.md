---
layout: Conceptual
title: SMS_InstanceChangeNotification Class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/sms_instancechangenotification-server-wmi-class
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
description: Learn how to notify the administrator console that an alert has changed its status with SMS_InstanceChangeNotification class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 43603551-9917-8eed-609a-aecf54092164
document_version_independent_id: effbacc2-9b65-80c6-6872-46b600bd7084
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/console/sms_instancechangenotification-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/console/sms_instancechangenotification-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/console/sms_instancechangenotification-server-wmi-class.md
cmProducts: []
platformId: f84bb15f-d74b-c3df-328c-b54a3ab828a5
---

# SMS_InstanceChangeNotification Class - Configuration Manager | Microsoft Learn

The `SMS_InstanceChangeNotification` WMI class is an SMS Provider server class, in Configuration Manager, that notifies the administrator console that an alert has changed its status.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_InstanceChangeNotification : SMS_BaseClass
{
   String Action;
   String ClassName;
   ref:SMS_BaseClass InstancePath;
   UInt8[] SECURITY_DESCRIPTOR;
   UInt64 TIME_CREATED;
};
```

## Methods

The `SMS_InstanceChangeNotification` class does not define any methods.

## Properties

`Action` Data type: `String`

Access type: Read/Write

Qualifiers: None

The action that caused the change notification.

| Possible values |
| --- |
| Insert |
| Update |
| Delete |

`ClassName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the class that caused the change notification. For example, for an alert, the name of the class is SMS\_Alert.

`InstancePath` Data type: `ref:SMS_BaseClass`

Access type: Read/Write

Qualifiers: None

The instance path of the object that caused the change notification.

`SECURITY_DESCRIPTOR` Data type: `UInt8[]`

Access type: Read/Write

Qualifiers: None

For internal use only.

`TIME_CREATED` Data type: `UInt64`

Access type: Read/Write

Qualifiers: None

For internal use only.

## Remarks

This class allows alert tiles to be updated with the most recent status information.

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers that are included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../../../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../../../core/reqs/server-development-requirements).