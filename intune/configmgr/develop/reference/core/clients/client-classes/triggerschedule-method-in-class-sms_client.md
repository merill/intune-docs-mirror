---
layout: Conceptual
title: TriggerSchedule Method - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/triggerschedule-method-in-class-sms_client
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
description: Trigger the client to run a specific schedule.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f42fd6ba-cbcc-3295-4af8-33be2ceff64c
document_version_independent_id: a6d90def-202e-c480-258a-2c994f56c280
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/triggerschedule-method-in-class-sms_client.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/triggerschedule-method-in-class-sms_client
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/triggerschedule-method-in-class-sms_client.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 0181390f-19c3-b6cf-0eb4-a22d182913bc
---

# TriggerSchedule Method - Configuration Manager | Microsoft Learn

The `TriggerSchedule` method, in Configuration Manager, triggers the client to run the specified schedule.

The following syntax is simplified from Managed Object Format (MOF) code and defines the method.

## Syntax

```
UInt32 TriggerSchedule(
     String sScheduleID
);
```

#### Parameters

`sScheduleID` Data type: `String`

Qualifiers: [in]

GUID of the schedule to be triggered.

Complete GUID List:

| Schedule | GUID |
| --- | --- |
| Hardware Inventory | {00000000-0000-0000-0000-000000000001} |
| Software Inventory | {00000000-0000-0000-0000-000000000002} |
| Data Discovery Record | {00000000-0000-0000-0000-000000000003} |
| File Collection | {00000000-0000-0000-0000-000000000010} |
| IDMIF Collection | {00000000-0000-0000-0000-000000000011} |
| Client Machine Authentication | {00000000-0000-0000-0000-000000000012} |
| Machine Policy Assignments Request | {00000000-0000-0000-0000-000000000021} |
| Machine Policy Evaluation | {00000000-0000-0000-0000-000000000022} |
| Refresh Default MP Task | {00000000-0000-0000-0000-000000000023} |
| LS (Location Service) Refresh Locations Task | {00000000-0000-0000-0000-000000000024} |
| LS (Location Service) Timeout Refresh Task | {00000000-0000-0000-0000-000000000025} |
| Policy Agent Request Assignment (User) | {00000000-0000-0000-0000-000000000026} |
| Policy Agent Evaluate Assignment (User) | {00000000-0000-0000-0000-000000000027} |
| Software Metering Generating Usage Report | {00000000-0000-0000-0000-000000000031} |
| Source Update Message | {00000000-0000-0000-0000-000000000032} |
| Clearing proxy settings cache | {00000000-0000-0000-0000-000000000037} |
| Machine Policy Agent Cleanup | {00000000-0000-0000-0000-000000000040} |
| User Policy Agent Cleanup | {00000000-0000-0000-0000-000000000041} |
| Policy Agent Validate Machine Policy / Assignment | {00000000-0000-0000-0000-000000000042} |
| Policy Agent Validate User Policy / Assignment | {00000000-0000-0000-0000-000000000043} |
| Retrying/Refreshing certificates in AD on MP | {00000000-0000-0000-0000-000000000051} |
| Peer DP Status reporting | {00000000-0000-0000-0000-000000000061} |
| Peer DP Pending package check schedule | {00000000-0000-0000-0000-000000000062} |
| SUM Updates install schedule | {00000000-0000-0000-0000-000000000063} |
| Hardware Inventory Collection Cycle | {00000000-0000-0000-0000-000000000101} |
| Software Inventory Collection Cycle | {00000000-0000-0000-0000-000000000102} |
| Discovery Data Collection Cycle | {00000000-0000-0000-0000-000000000103} |
| File Collection Cycle | {00000000-0000-0000-0000-000000000104} |
| IDMIF Collection Cycle | {00000000-0000-0000-0000-000000000105} |
| Software Metering Usage Report Cycle | {00000000-0000-0000-0000-000000000106} |
| Windows Installer Source List Update Cycle | {00000000-0000-0000-0000-000000000107} |
| Software Updates Assignments Evaluation Cycle | {00000000-0000-0000-0000-000000000108} |
| Branch Distribution Point Maintenance Task | {00000000-0000-0000-0000-000000000109} |
| Send Unsent State Message | {00000000-0000-0000-0000-000000000111} |
| State System policy cache cleanout | {00000000-0000-0000-0000-000000000112} |
| Scan by Update Source | {00000000-0000-0000-0000-000000000113} |
| Update Store Policy | {00000000-0000-0000-0000-000000000114} |
| State system policy bulk send high | {00000000-0000-0000-0000-000000000115} |
| State system policy bulk send low | {00000000-0000-0000-0000-000000000116} |
| Application manager policy action | {00000000-0000-0000-0000-000000000121} |
| Application manager user policy action | {00000000-0000-0000-0000-000000000122} |
| Application manager global evaluation action | {00000000-0000-0000-0000-000000000123} |
| Power management start summarizer | {00000000-0000-0000-0000-000000000131} |
| Endpoint deployment reevaluate | {00000000-0000-0000-0000-000000000221} |
| Endpoint AM policy reevaluate | {00000000-0000-0000-0000-000000000222} |
| External event detection | {00000000-0000-0000-0000-000000000223} |

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).

## Examples

### Example 1: Trigger hardware inventory via PowerShell using the `WMICLASS` type accelerator

```powershell
([wmiclass]"root\ccm:SMS_Client").TriggerSchedule("{00000000-0000-0000-0000-000000000001}")
```

### Example 2: Trigger location service refresh task via PowerShell using the Invoke-CIMMethod method

```powershell
Invoke-CimMethod -Namespace 'root\CCM' -ClassName SMS_Client -MethodName TriggerSchedule -Arguments @{sScheduleID='{00000000-0000-0000-0000-000000000024}'}
```

### Example 3: Trigger Software Update Scan cache deletion and scan via Command Prompt using WMIC

```batchfile
%windir%\System32\wbem\WMIC.exe /namespace:\\root\ccm\invagt path inventoryActionStatus where InventoryActionID="{00000000-0000-0000-0000-000000000113}" DELETE /NOINTERACTIVE
%windir%\System32\wbem\WMIC.exe /namespace:\\root\ccm path sms_client CALL TriggerSchedule "{00000000-0000-0000-0000-000000000113}" /NOINTERACTIVE
```

Important

Windows Deprecated Features - [Update - January 2024]: Currently, WMIC is a Feature on Demand (FoD) that's preinstalled by default in Windows 11 22H2 and 23H2. In the future releases of Windows 11, 24H2+, the WMIC FoD will be disabled by default.