---
layout: Conceptual
title: Send Schedule Tool - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/support/send-schedule-tool
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
description: Use the Send Schedule Tool to trigger a schedule on a Configuration Manager client.
ms.date: 2018-07-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: de0250a8-ce9b-c8ef-a24a-0239b64fe0bc
document_version_independent_id: f9c57002-1f23-7d85-3d24-a4b545ce350e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/support/send-schedule-tool.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/support/send-schedule-tool
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/support/send-schedule-tool.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: ad3d7749-493b-cb00-ac2e-d712369c9305
---

# Send Schedule Tool - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Send Schedule Tool is one of the [Configuration Manager tools](tools). Use it to trigger a schedule on a client or trigger the evaluation of a specified configuration baseline. It works for the local computer or targeting a remote client.

For example, use the tool to trigger an inventory schedule or compliance evaluation. If a number of Configuration Manager clients haven't recently reported inventory or compliance status, run the tool to initiate the necessary schedule on each client.

## Usage

Run **SendSchedule.exe** as an administrator.

`SendSchedule /L [Computer Name]``SendSchedule "<Message GUID | DCM UID>" [Computer Name]`

After you trigger a message (GUID), see **SMSClientMethodProvider.log**. For more information about available message GUIDs, see Message IDs.

After you trigger the evaluation of a configuration baseline (DCM UID), see **DCMAgent.log**.

## Command-line options

### Option: `/L`

List all Message GUID or DCM UID available for sending. Display the meaningful name of messages in the data table for each one. If the computer name is absent, it uses the local computer. If you specify a message without a machine name, then it sends the message to the local machine.

## Examples

#### List the available messages on the local machine

`SendSchedule /L`

#### List the available messages on the client MyPC:

`SendSchedule /L MyPC`

#### Trigger hardware inventory on the local machine

`SendSchedule {00000000-0000-0000-0000-000000000001}`

#### Trigger hardware inventory on MyPC:

`SendSchedule {00000000-0000-0000-0000-000000000001} MyPC`

#### Trigger the evaluation of a specific configuration baseline on MyPC:

`SendSchedule ScopeId_611E8382-C064-4B62-B0DE-EFFB52AE8994/Baseline_36722778-69dd-4423-9632-b61148b2b67e MyPC`

## Message IDs

| Message ID | Display Name |
| --- | --- |
| {00000000-0000-0000-0000-000000000001} | Hardware Inventory |
| {00000000-0000-0000-0000-000000000002} | Software Inventory |
| {00000000-0000-0000-0000-000000000003} | Discovery Inventory |
| {00000000-0000-0000-0000-000000000010} | File Collection |
| {00000000-0000-0000-0000-000000000011} | IDMIF Collection |
| {00000000-0000-0000-0000-000000000021} | Request Machine Assignments |
| {00000000-0000-0000-0000-000000000022} | Evaluate Machine Policies |
| {00000000-0000-0000-0000-000000000023} | Refresh Default MP Task |
| {00000000-0000-0000-0000-000000000024} | LS (Location Service) Refresh Locations Task |
| {00000000-0000-0000-0000-000000000025} | LS Timeout Refresh Task |
| {00000000-0000-0000-0000-000000000026} | Policy Agent Request Assignment (User) |
| {00000000-0000-0000-0000-000000000027} | Policy Agent Evaluate Assignment (User) |
| {00000000-0000-0000-0000-000000000031} | Software Metering Generating Usage Report |
| {00000000-0000-0000-0000-000000000032} | Source Update Message |
| {00000000-0000-0000-0000-000000000037} | Clearing proxy settings cache |
| {00000000-0000-0000-0000-000000000040} | Machine Policy Agent Cleanup |
| {00000000-0000-0000-0000-000000000041} | User Policy Agent Cleanup |
| {00000000-0000-0000-0000-000000000042} | Policy Agent Validate Machine Policy / Assignment |
| {00000000-0000-0000-0000-000000000043} | Policy Agent Validate User Policy / Assignment |
| {00000000-0000-0000-0000-000000000051} | Retrying/Refreshing certificates in AD on MP |
| {00000000-0000-0000-0000-000000000061} | Peer DP Status reporting |
| {00000000-0000-0000-0000-000000000062} | Peer DP Pending package check schedule |
| {00000000-0000-0000-0000-000000000063} | SUM Updates install schedule |
| {00000000-0000-0000-0000-000000000101} | Hardware Inventory Collection Cycle |
| {00000000-0000-0000-0000-000000000102} | Software Inventory Collection Cycle |
| {00000000-0000-0000-0000-000000000103} | Discovery Data Collection Cycle |
| {00000000-0000-0000-0000-000000000104} | File Collection Cycle |
| {00000000-0000-0000-0000-000000000105} | IDMIF Collection Cycle |
| {00000000-0000-0000-0000-000000000106} | Software Metering Usage Report Cycle |
| {00000000-0000-0000-0000-000000000107} | Windows Installer Source List Update Cycle |
| {00000000-0000-0000-0000-000000000108} | Software Updates Policy Action Software Updates Assignments Evaluation Cycle |
| {00000000-0000-0000-0000-000000000109} | PDP Maintenance Policy Branch Distribution Point Maintenance Task |
| {00000000-0000-0000-0000-000000000110} | DCM policy |
| {00000000-0000-0000-0000-000000000111} | Send Unsent State Message |
| {00000000-0000-0000-0000-000000000112} | State System policy cache cleanout |
| {00000000-0000-0000-0000-000000000113} | Update source policy |
| {00000000-0000-0000-0000-000000000114} | Update Store Policy |
| {00000000-0000-0000-0000-000000000115} | State system policy bulk send high |
| {00000000-0000-0000-0000-000000000116} | State system policy bulk send low |
| {00000000-0000-0000-0000-000000000121} | Application manager policy action |
| {00000000-0000-0000-0000-000000000122} | Application manager user policy action |
| {00000000-0000-0000-0000-000000000123} | Application manager global evaluation action |
| {00000000-0000-0000-0000-000000000131} | Power management start summarizer |
| {00000000-0000-0000-0000-000000000221} | Endpoint deployment reevaluate |
| {00000000-0000-0000-0000-000000000222} | Endpoint AM policy reevaluate |
| {00000000-0000-0000-0000-000000000223} | External event detection |