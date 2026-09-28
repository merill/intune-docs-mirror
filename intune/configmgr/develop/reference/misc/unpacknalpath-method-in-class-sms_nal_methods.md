---
layout: Conceptual
title: UnPackNALPath Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/unpacknalpath-method-in-class-sms_nal_methods
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
description: Decodes a network abstraction layer (NAL) path into its components.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: dea275c4-80d7-eb43-f411-c7bd62503ae7
document_version_independent_id: 5eb87b73-612a-474b-b874-2ddeacca5ecd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/misc/unpacknalpath-method-in-class-sms_nal_methods.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/misc/unpacknalpath-method-in-class-sms_nal_methods
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/misc/unpacknalpath-method-in-class-sms_nal_methods.md
cmProducts: []
platformId: ca93bea0-5b2b-369f-0a1e-cd449a457c91
---

# UnPackNALPath Method - Configuration Manager | Microsoft Learn

The `UnPackNALPath` method, in Configuration Manager, decodes a network abstraction layer (NAL) path into its components.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
SInt32 UnPackNALPath(
     String NALPath,
     String DisplayQualifiers[],
     String NALType,
     String NetworkOSPath,
     String NetworkConnectionQualifiers[]
);
```

#### Parameters

`NALPath` Data type: `String`

Qualifiers: [in]

NAL path to be decoded.

`DisplayQualifiers` Data type: `String` Array

Qualifiers: [out]

Qualifiers used by the Configuration Manager console. See the `DisplayQualifiers` property of [PackNALPath Method in Class SMS_NAL_Methods](packnalpath-method-in-class-sms_nal_methods).

`NALType` Data type: `String`

Qualifiers: [out]

The NAL type specified by the network operating system. See the `NALType` property of [PackNALPath Method in Class SMS_NAL_Methods](packnalpath-method-in-class-sms_nal_methods).

`NetworkOSPath` Data type: `String`

Qualifiers: [out]

Network operating system path. See the `NetworkOSPath` property of [PackNALPath Method in Class SMS_NAL_Methods](packnalpath-method-in-class-sms_nal_methods).

`NetworkConnectionQualifiers` Data type: `String` Array

Qualifiers: [out]

Configuration Manager component-specific qualifiers. See the `NetworkConnectionQualifiers` property of [PackNALPath Method in Class SMS_NAL_Methods](packnalpath-method-in-class-sms_nal_methods).

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](../../core/understand/about-configuration-manager-errors).

## Example Code

The following example decodes a NAL path.

```
Dim clsNALMethods As SWbemObject
Dim NALPath As String
Dim DisplayQuals() As Variant
Dim NALType As String
Dim NOSPath As String
Dim NOSQuals() As Variant
Dim instResources As SWbemObjectSet
Dim instResource As SWbemObject
Dim Query As String

Set clsNALMethods = Services.Get("SMS_NAL_Methods")

Query = "SELECT * FROM SMS_SystemResourceList " & _
        "WHERE RoleName=""SMS Distribution Point"" AND SiteCode=""<site code>"""
Set instResources = Services.ExecQuery(Query, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

For Each instResource In instResources
    NALPath = instResource.NALPath

    clsNALMethods.UnPackNALPath NALPath, DisplayQuals, NALType, NOSPath, NOSQuals
    MsgBox "Path = " & NALPath & vbCrLf & _
           "Display = " & DisplayQuals(0) & vbCrLf & _
           "Type = " & NALType & vbCrLf & _
           "NOSPath = " & NOSPath & vbCrLf & _
           "NOSQual = " & NOSQuals(0)
Next
```

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).