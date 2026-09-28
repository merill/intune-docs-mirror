---
layout: Conceptual
title: Endpoint protection views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/endpoint-protection-views-configuration-manager
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
description: Information about the status of Endpoint Protection clients and malware activity in your Configuration Manager site.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6c070dac-6049-f858-7924-2cbb14d9cb28
document_version_independent_id: 7fa3b26f-8f9a-9c0f-6f4a-db99750c98b5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/endpoint-protection-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/endpoint-protection-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/endpoint-protection-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 7c03a839-58ff-5a4a-c5dc-b34ca0f3d66c
---

# Endpoint protection views - Configuration Manager | Microsoft Learn

The Configuration�Manager�Endpoint�Protection views provide information about the status of Endpoint Protection clients and malware activity in your Configuration Manager site.

The following sections provide detailed information about the Endpoint Protection views.

## Endpoint protection views

The Endpoint Protection views are described in this section.

### v\_AM\_NormalizedDetectionHistory

No description.

### v\_OverallThreatActivity

This view lists each collection in the Configuration Manager site, by collection ID. For each collection, information such as the number of infected computers, the computers that require a restart and information about any malware that was recently removed are listed. This view can be joined to other views by using the **CollectionID** column.

### v\_OverallThreatActivity\_History

This view lists each collection in the Configuration Manager site, by collection ID. For each collection, historical information such as the number of infected computers, the computers that require a restart and information about any malware that was recently removed are listed. This view can be joined to other views by using the **CollectionID** column.

### v\_EndpointProtectionCollections

Contains the collection ID and collection name of all collections that have the option **View this collection in the Endpoint Protection dashboard** checked on the **Alerts** tab of the *collection name*�**Properties** dialog box. This view can be joined to other views by using the **CollectionID** and **CollectionName** columns.

### v\_EndpointProtectionHealthStatus

Lists the collections protected by Endpoint Protection with information about the number of clients in each collection, clients that are considered at risk, clients that haven't been installed yet, clients that aren't supported and more. This view can be joined to other views by using the **CollectionID** column.

### v\_EndpointProtectionHealthStatus\_History

Lists historical information about the collections protected by Endpoint Protection with information about the number of clients in each collection, clients that are considered at risk, clients that haven't been installed yet, clients that aren't supported and more. This view can be joined to other views by using the **CollectionID** column.

### v\_GS\_AntimalwareHealthStatus

Lists information about the antimalware client installed on each Configuration Manager client computer, including whether the antimalware and antivirus components are enabled, the last scan time and date, the antimalware engine version, and more. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_AntimalwareInfectionStatus

Lists information about the status of clients protected by Endpoint Protection, such as the status of the computer, whether it's pending a full scan or a restart, whether manual steps are required to resolve a malware infection, and more. This view can be joined to other views by using the **ResourceID** column.

### v\_EndpointProtectionStatus

Provides an overall summary of the status of Endpoint Protection clients for each computer, sorted by resource ID. This includes whether the client is protected, whether it's considered at risk, whether it supports Endpoint Protection, whether it requires a restart, and more. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_Threats

Lists threats discovered on clients, sorted by resource ID. This view can be joined to other views by using the **ResourceID** column.

### v\_TopThreatsDetected

Lists, by collection ID, the top malware threats found on client computers. Includes the threat name, the number of computers in the collection that are affected, and more. This view can be joined to other views by using the **CollectionID** column.

### v\_ThreatSummary

Lists the possible descriptions of each malware threat that can be detected by Endpoint Protection. It's unlikely that this view will be joined to other views.

### v\_ThreatSeverities

Lists the threat severities, by severity ID that can be displayed in the Endpoint Protection dashboard to indicate the severity of discovered malware. It's unlikely that this view will be joined to other views.

### v\_ThreatDefaultActions

Lists the default actions, by default action ID that can be taken when malware is discovered on client computers. It's unlikely that this view will be joined to other views.

### v\_ThreatCategories

Lists the available threat categories, by category ID, that malware can be sorted into, such as trojans and spyware. It's unlikely that this view will be joined to other views.

### v\_ThreatCatalog

Lists all known threats, by threat ID. Includes the name, severity, and summary for the threat, together with the action that Endpoint Protection will take if the threat is discovered on client computers. This view can be joined to other views by using the **ThreatID**, **SeverityID**, **CategoryID** and **DefaultActionID** columns.

### v\_GS\_EPDeploymentState

Lists, by resource ID, the current state of the Endpoint Protection client deployment to computers. Includes the last status sent by the client, the state of the deployment, and any errors that have been generated. This view can be joined to other views by using the **ResourceID** column.

### v\_CurrentThreatOutbreak

Lists, by resource ID, the malware threats that have been detected on client computers. This includes the threat ID, the threat name, when the threat was first detected and when it was last detected. This view can be joined to other views by using the **ResourceID** column.