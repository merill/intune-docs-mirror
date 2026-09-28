---
layout: Conceptual
title: PackNALPath Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/packnalpath-method-in-class-sms_nal_methods
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
description: Encode a network abstraction layer (NAL) path from its components. A NAL path is an abstract representation of a network path or a user account.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d7d0cd00-a532-dd22-2c43-a97c1263071d
document_version_independent_id: 7023ba4c-db73-d35b-bad6-de7ceade2d86
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/packnalpath-method-in-class-sms_nal_methods.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/packnalpath-method-in-class-sms_nal_methods
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/packnalpath-method-in-class-sms_nal_methods.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 45702d28-0ffa-0540-0837-266a25994729
---

# PackNALPath Method - Configuration Manager | Microsoft Learn

The `PackNALPath` method, in Configuration Manager, encodes a network abstraction layer (NAL) path from its components. A NAL path is an abstract representation of a network path or a user account.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 PackNALPath(
     String DisplayQualifiers[],
     String NALType,
     String NetworkOSPath,
     String NetworkConnectionQualifiers[],
     String NALPath
);
```

#### Parameters

`DisplayQualifiers` Data type: `String` Array

Qualifiers: [in]

Qualifiers that are used by the Configuration Manager console. The possible values are: Display=&lt;path, group, or user&gt;. The value that you specify for the path must be the same as the value that you specify for `NetworkOSPath`. For path formats, see `NetworkOSPath` formats later in this topic.

`NALType` Data type: `String`

Qualifiers: [in]

The NAL type specified by the network operating system. Possible values are:

| Value | NAL type |
| --- | --- |
| GENERIC | All providers accept this account specification. Use this value only when you specify a user or group name. |
| MSWNET | Windows NT. |

`NetworkOSPath` Data type: `String`

Qualifiers: [in]

The network operating system path. Possible values are:

| Provider | NetworkOSPath |
| --- | --- |
| Windows NT user names | &lt;domain&gt;\&lt;user name&gt; |
| Windows NT group names | &lt;domain&gt;\group=&lt;group name&gt; |
| Generic group names | GROUP=&lt;group name&gt; |
| Windows NT (UNC) computer names | \\&lt;computer name&gt; |
| Windows NT (UNC) share names | \\&lt;computer name&gt;\&lt;share name&gt; |

`NetworkConnectionQualifiers` Data type: `String` Array

Qualifiers: [in]

Optional. Configuration Manager component-specific qualifiers. The possible values are: SMS\_SITE=&lt;site code&gt; [Preferred]. SMS\_SITE identifies the site to which the path belongs. Preferred is optional and identifies the path to use when multiple paths are specified.

`NALPath` Data type: `String`

Qualifiers: [out]

Encoded NAL path.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Example Code

The following example encodes a NAL path for an MSWNET network operating system.

```
Dim clsNALMethods As SWbemObject
Dim NALPath As String

Set clsNALMethods = Services.Get("SMS_NAL_Methods")
clsNALMethods.PackNALPath Array("Display=\\<server>"), "MSWNET", _
"\\<server>", Array("SMS_SITE=<site code>"), NALPath
```

## Remarks

Your application uses this method when creating a distribution point or defining system resources in the site control file programmatically. The method is not used to create a NAL path of an existing distribution point for an [SMS_DistributionPoint Server WMI Class](../core/servers/configure/sms_distributionpoint-server-wmi-class) object. To determine the NAL path for an existing distribution point, the application should query the [SMS_SystemResourceList Server WMI Class](../core/servers/configure/sms_systemresourcelist-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).