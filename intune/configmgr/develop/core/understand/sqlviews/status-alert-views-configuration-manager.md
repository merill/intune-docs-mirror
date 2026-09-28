---
layout: Conceptual
title: Status and alert views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/status-alert-views-configuration-manager
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
description: Information about Configuration Manager component behavior and data flow.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a08fa8c4-e4c9-97a1-db9d-355fb3382fae
document_version_independent_id: 00885e99-5a6b-518f-d184-9e7dbcaf4584
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/status-alert-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/status-alert-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/status-alert-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1ae5c491-970a-4062-8301-6336e69f9026
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/86a4b315-a9f1-4577-b985-6fb0e0e67420
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/f2c3e52e-3667-4e8a-bf11-20b9eaccdc8c
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/96ac410d-d052-4707-8007-df31dd0fe041
platformId: eef5fc32-316e-79c2-f496-24d0b334ea37
---

# Status and alert views - Configuration Manager | Microsoft Learn

Configuration�Manager status messages report information about Configuration Manager component behavior and data flow and are categorized by severity and type. State messages are sent by Configuration Manager clients to site systems based on important changes of state, providing a snapshot of the state of a process at a specific time. Status summarizers produce summaries of the status and state messages and provide a snapshot of the status and health of site systems, components, software updates compliance, and so on.

Status message instances consist of properties that are stored in the database, which are represented primarily by the **v\_StatusMessage** view, and message strings stored in dynamic-link library (DLL) files. When you view a message by using the Configuration Manager console, **Status Message Viewer**, and the **Status Message Details** page in **Report Viewer**, Configuration Manager creates the instance of status messages by combining the various parts.

The following sections provide detailed information about status message views, state message views, and status summarizer views.

## Status message views

The status views are described in this section.

### v\_AdvertisementStatusInformation

Lists all deployment status message IDs, the message state, and the message name, such as succeeded, expired, failed, and retrying. The view is also listed and described in the [Application Management Views in Configuration Manager](application-management-views-configuration-manager) topic. The view can be joined to other advertisement status views by using the **MessageID** column.

### v\_ClientAdvertisementStatus

Lists all package and program deployments with the associated status for system resources that have been targeted. The view is also listed and described in the [Application Management Views in Configuration Manager](application-management-views-configuration-manager) topic. The view can be joined to other views by using the **AdvertisementID**, **ResourceID**, and **LastStatusMessageID** columns.

### v\_ClientMessageStatistics

Lists all Configuration Manager clients, by resource ID, the last time the client sent and processed a status message, and the last time a resynchronization was issued and completed on the client. This view can be joined to other views by using the **ResourceID** column.

### v\_DCMClientStatusInformation

Lists all possible compliance settings client states. The view is also listed and described in the [Compliance Settings Views in Configuration Manager](compliance-settings-views-configuration-manager) topic. It is unlikely that this view will be joined to other views.

### v\_PackageStatus

Lists the status for all deployments, as well as the package server location, last update time, and so on. The view is also listed and described in the [Application Management Views in Configuration Manager](application-management-views-configuration-manager) topic. The view can be joined to other views by using the **PackageID** column.

### v\_PeerDPStatusInfo

Lists the peer distribution point states and associated state names. It is unlikely that this view will be joined to other views.

### v\_ServerMessageStatistics

Lists the site system servers, the associated site code, when the last heartbeat occurred, and how long the heartbeat took to process. The view is also listed and described in the [Site Administration Views in Configuration Manager](site-admin-views-configuration-manager) topic. The view can be joined to other views by using the **ServerName** column.

### v\_StatMsgAttributes

Lists the attributes for all status messages (for example, package ID, collection ID, user name, object GUID, and so on). The view can be joined to the **v\_StatusMessage** and **v\_StatMsgInsStrings** views by using the **RecordID** column.

### v\_StatMsgInsStrings

Lists the status insertion strings for all status messages. The view can be joined to the **v\_StatusMessage** and **v\_StatMsgAttributes** views by using the **RecordID** column.

### v\_StatMsgModuleNames

Lists the status message module names with associated module DLL name. By default, Configuration Manager has the SMS Client, SMS Provider, and SMS Server module names. It is unlikely that this view will be joined to other views.

### v\_StatusMessage

Lists information about all status messages, including status message ID, time of status message, severity, site code, and so on. The view can be joined to the **v\_StatMsgAttributes** and **v\_StatMsgInsStrings** views by using the **RecordID** column, and to other views by using the **MachineName** column.

### v\_TaskExecutionStatus

Lists the status for operating system deployment task sequence steps, as well as the advertisement ID, resource ID, action name, and so on. The view is also listed and described in the [Operating System Deployment Views in Configuration Manager](operating-system-deployment-views-configuration-manager) topic. The view can be joined to other views by using the **AdvertisementID** and **ResourceID** columns.

### v\_WOLCommicationErrorStatus

Lists the Wake on LAN error status messages, as well as the time of the error, batch ID, object type, ID, and error code. The view is also listed and described in the [Wake On LAN Views in Configuration Manager](wake-lan-views-configuration-manager) topic. It is unlikely that this view will be joined to other views.

### v\_StatusMessagesAlerts

Lists, by record ID, recently generated alerts. This includes the severity of the alert, the alert text and more. This view can be joined to other views by using the **AlertSeverity**, **Name**, **TypeInstanceID** or **MachineName** columns.

## State views

The state views list the state messages sent by Configuration Manager clients to site systems and can generally be joined to system data, other state message views, deployment views, and more. The Configuration Manager states are listed in the **v\_StateNames** view. When creating reports by using state views, you will likely want to join the **v\_StateNames** view with another state view by using the **StateType** and **StateID** columns to retrieve the friendly names for the state and to use the **v\_StateNames** view to determine the criteria to filter the SQL statement. Each state message type has multiple state IDs, which start at 1 for each message type. When joining to a view that contains information for more than one state type, you will need to either join to the other view by using both the **StateType** and **StateID** columns or join to the other view by using the **StateID** column and filter the query with for the specific **StateType**. For example, if you join to another view by using the **StateID** column, you could filter the results by **StateType**=300.

### v\_AssignmentState\_Combined

Lists the last state message received from Configuration Manager client computers for assigned software update deployments, including the assignment ID (deployment ID), resource ID, state type, and so on. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **AssignmentID**, **ResourceID**, **StateType**, and **StateID** columns.

### v\_AssignmentStatePerTopic

Lists the last state message for each state type received from Configuration Manager client computers for assigned software update deployments, including assignment ID (deployment ID), resource ID, state type, and so on. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **AssignmentID**, **ResourceID**, **TopicType**, and **StateID** columns.

### v\_CIAssignmentStatus

Lists the enforcement and evaluation state messages received from Configuration Manager client computers for all assigned configuration items, including assigned software update deployments and assigned configuration baselines. The assignment ID, resource ID, the last enforcement state message ID, the last evaluation state message ID, and so on are provided. The view is also listed and described in the [Compliance Settings Views in Configuration Manager](compliance-settings-views-configuration-manager) topic. The view can be joined to other views by using the **AssignmentID**, **ResourceID**, **LastEnforcementMessageID**, and **LastEvaluationMessageID** columns. The **LastEnforcementMessageID** column provides the state ID for state messages with a topic type of 402. The **LastEvaluationMessageID** column provides the state ID for state messages with a topic type of 400.

### v\_CIComplianceHistory

Lists the configuration items, by **CI\_UniqueID** and **CI\_ID**, that are configuration baselines or configuration items within a configuration baseline, that have been assigned to a Configuration Manager client, listed by **ResourceID**, and compliance information for the configuration item. The information includes the compliance start and end dates, whether the configuration item is applicable to the client, whether the client is compliant for the configuration item, and so on. The view is also listed and described in the [Compliance Settings Views in Configuration Manager](compliance-settings-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_UniqueID**, **CI\_ID**, and **ResourceID** columns.

### v\_CIComplianceStatusDetail

Lists the configuration items, by **CI\_ID** and **CI\_UniqueID**, that are in a configuration baseline, have been assigned to a Configuration Manager client, listed by **ResourceID**, and have a state value of **Non-Compliant**. The view is also listed and described in the [Compliance Settings Views in Configuration Manager](compliance-settings-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_ID**, **CI\_UniqueID**, **ResourceID**, and **ModelName** columns.

### v\_CICurrentComplianceStatus

Lists the compliance and enforcement states for configuration items, by configuration item ID, as well as the resource ID, whether the configuration item is applicable to the resource, and information related to the compliance and evaluation of the configuration item. The view is also listed and described in the [Compliance Settings Views in Configuration Manager](compliance-settings-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_ID**, **ResourceID**, **CI\_UniqueID**, **ModelName**, **ComplianceState**, and **LastEnforcementMessageID** columns. The **ComplianceState** column provides the state ID for state messages with a topic type of 401. The **LastEnforcementMessageID** column provides the state ID for state messages with a state message topic type of 402.

### v\_ClientDeploymentState

Lists all Configuration Manager clients, by SMSID, and the last client deployment state reported, as well as the fully qualified domain name (FQDN), NetBIOS name, assigned site code, client version, and so on. The view is also listed and described in the [Client Deployment Views in Configuration Manager](client-deployment-views-configuration-manager) topic. The view can be joined to other views by using the **SMSID**, **FQDN**, **NetBiosName**, and **LastMessageStateID** columns. The **LastMessageStateID** column contains the state ID for topic type 800. The Configuration Manager states are listed in the **v\_StateNames** view.

### v\_ClientHealthState

Lists all Configuration Manager clients, by SMSID, the last client health state reported for each state type, the fully qualified domain name (FQDN), NetBIOS name, assigned site code, health type, health state, health state name, and so on. The view is also listed and described in the [Client Status Views in Configuration Manager](client-status-views-configuration-manager) topic. The view can be joined to other views by using the **SMSID**, **FQDN**, **NetBiosName**, **HealthType**, and **HealthState** columns. The **HealthType** column contains the topic type and the **HealthState** column contains the state ID. Client health state messages have a state type from 1000 to 1004. The Configuration Manager states are listed in the **v\_StateNames** view.

### v\_DeviceClientDeploymentState

Lists all Configuration Manager mobile device clients, by device client ID, NetBIOS name, and device ID, and the last device deployment state reported, as well as the assigned site code, device client version, and so on. The view is also listed and described in the [Mobile Device Management Views in Configuration Manager](mobile-device-management-views-configuration-manager) and [Client Deployment Views in Configuration Manager](client-deployment-views-configuration-manager) topics. The view can be joined to other views by using the **DeviceClientID**, which contains the same information as the **SMS\_Unique\_Identifier0** column in the **v\_R\_System** view, **DeviceNetBiosName**, and DeviceDeploymentState columns. The **DeviceDeploymentState** column contains the state ID for topic type 800. The Configuration Manager states are listed in the **v\_StateNames** view.

### v\_DeviceClientHealthState

Lists all Configuration Manager mobile device clients, by device client ID, NetBIOS name, and device ID, and the health state of the device, as well as the assigned site code, owner name, and so on. The view is also listed and described in the [Mobile Device Management Views in Configuration Manager](mobile-device-management-views-configuration-manager) and [Client Status Views in Configuration Manager](client-status-views-configuration-manager) topics. The view can be joined to other views by using the **DeviceClientID**, which contains the same information as the **SMS\_Unique\_Identifier0** column in the **v\_R\_System** view, **DeviceNetBiosName**, **DeviceID**, **HealthType**, and **HealthState** columns. The **HealthType** column contains the topic type and the **HealthState** column contains the state ID. Client health state messages have a state type from 1000 to 1004. The Configuration Manager states are listed in the **v\_StateNames** view.

### v\_StateNames

Lists all states that can be reported by Configuration Manager clients by topic type, state ID, state name, and state description. Each state topic type defines a specific function, and each topic type contains multiple state IDs. The view can be joined to other views by using the **TopicType** and **StateID** columns.

### v\_Update\_ComplianceStatusAll

Lists the detection state for all software updates that have been scanned for compliance on Configuration Manager clients, as well as the resource ID of the client, last enforcement state ID, enforcement source, last status check time, and so on. The **v\_Update\_ComplianceStatusAll** view combines information from the **v\_Update\_ComplianceStatusReported** and **v\_UpdateComplianceStatus\_Unknown** views. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_ID**, **ResourceID**, **Status**, and **LastEnforcementMessageID** columns. The Status column provides the state ID for state messages with a topic type of 500. The **LastEnforcementMessageID** column provides the state ID for state messages with a topic type of 402.

### v\_Update\_ComplianceStatusReported

Lists the detection state for all software updates that have been scanned for compliance on Configuration Manager clients, as well as the resource ID of the client, last enforcement state ID, enforcement source, last status check time, and so on. The **v\_Update\_ComplianceStatusReported** view combines information from the **v\_UpdateComplianceStatus** and **v\_UpdateComplianceStatus\_NotApplicable** views. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_ID**, **ResourceID**, **Status**, and **LastEnforcementMessageID** columns. The **Status** column provides the state ID for state messages with a topic type of 500. The **LastEnforcementMessageID** column provides the state ID for state messages with a topic type of 402.

### v\_UpdateAssignmentStatus

Lists the software update deployment assignments, the system resources that have been targeted, the last compliance state for the deployment, the last enforcement state for the deployments, the last evaluation state for the deployment, and so on. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **AssignmentID**, ResourceID, **LastComplianceMessageID**, **LastEnforcementMessageID**, and **LastEvaluationMessageID** columns. The **LastComplianceMessageID** column provides the state ID for state messages with a topic type of 300. The **LastEnforcementMessageID** column provides the state ID for state messages with a topic type of 301. The **LastEvaluationMessageID** provides the state ID for state messages with a topic type of 302.

### v\_UpdateAssignmentStatus\_Live

Lists the software update deployment assignments, the system resources that have been targeted, the last compliance state for the deployment, the last enforcement state for the deployments, the last evaluation state for the deployment, and so on. The **v\_UpdateAssignmentStatus\_Live** view contains a subset of information from the **v\_UpdateAssignmentStatus** view. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **AssignmentID**, **ResourceID**, **LastComplianceMessageID**, **LastEnforcementMessageID**, and **LastEvaluationMessageID** columns. The **LastComplianceMessageID** column provides the state ID for state messages with a topic type of 300. The **LastEnforcementMessageID** column provides the state ID for state messages with a topic type of 301. The **LastEvaluationMessageID** provides the state ID for state messages with a topic type of 302.

### v\_UpdateComplianceStatus

Lists the detection state for all software updates that have been scanned for compliance on Configuration Manager clients, as well as the resource ID of the client, last enforcement state ID, enforcement source, last status check time, and so on. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_ID**, **ResourceID**, **Status**, and **LastEnforcementMessageID** columns. The **Status** column provides the state ID for state messages with a topic type of 500. The **LastEnforcementMessageID** column provides the state ID for state messages with a topic type of 402.

### v\_UpdateScanStatus

Lists the Configuration Manager client computers, by resource ID, that have scanned for software updates compliance and the last scan state, as well as the last scan time, last error code, last Windows Update Agent version, and so on. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **ResourceID**, **UpdateSource\_ID**, and **LastScanState** columns.

Note

The **LastScanState** column provides the state ID for state messages with a topic type of 501.

### v\_UpdateState\_Combined

Lists the detection state for software updates that are not required on Configuration Manager client computers and the enforcement state for software updates that are required on Configuration Manager client computers, as well as the state ID, state time, enforcement source, and so on. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_ID**, **ResourceID**, **StateType**, and **StateID** columns.

Note

A value of 402 in the **StateType** column is for enforcement state, and a value of 500 is for software update detection state.

## Status summarizer views

Status summarizers produce summaries from status messages, state messages, and other data in the Configuration Manager site database. Status summaries are produced in real time as the summarizers receive status and state messages from Configuration Manager components and clients. You can use status summarizers to view a snapshot of the status and health of the site systems, components, deployments, software updates compliance, client health, and so on.

Data in a status summary is classified as either a count or a state. A count is a tally of events that occurs over a specific period of time, such as the number of error status messages reported by a component since the beginning of the week. A state is the last known condition of something, such as the number of free bytes that is available for the Configuration Manager site database.

Each of the status summaries contains some state data. Only the component status and advertisement status summaries contain count data. The status summarizer views contain data such as the number of information, warning, and error messages for a site within a specified interval and the state of all components in a site at a specified interval.

Each of the status message summarizer views are listed and described in this section.

### v\_AssignmentEnforcementSummaryPerUpdateAndState

Lists the software update deployments, by assignment ID, the software updates in the deployment, by **CI\_ID**, the enforcement state name, the count of Configuration Manager client computers that are in the enforcement state, and the total count of client computers that have been targeted for the deployment. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **AssignmentID** and **CI\_ID** columns.

Note

The enforcement states listed in this view have a state type of 402.

### v\_AssignmentSummaryPerTopic

Lists the assignments, by assignment ID, the type of assignment state message, the state ID for the type, the count of Configuration Manager client computers that are in the assignment state, and the total count of client computers that have been targeted for the assignment. The view is also listed and described in the [Compliance Settings Views in Configuration Manager](compliance-settings-views-configuration-manager) topic. The view can be joined to other views by using the **AssignmentID** column.

Note

There are three deployment assignment states. State type of 300 is assignment compliance, type 301 is assignment enforcement, and type 302 is assignment evaluation. You can find a list of the state IDs by looking in the **v\_StateNames** view.

### v\_CH\_ClientSummary

Lists summarized client status information for all Configuration Manager client computers, such as last heartbeat discovery, last hardware and software inventory scan, last policy request, whether there are possible certificate issues, and so on. The view is also listed and described in the [Client Status Views in Configuration Manager](client-status-views-configuration-manager) topic. The view can be joined to other views by using the **MachineID**, **NetBiosName**, and **SiteCode** columns.

### v\_CH\_ClientSummaryHistory

Lists a summarization of the client status information for all Configuration Manager client computers, such as total number of clients, total number of clients that are active based on the last heartbeat discovery, hardware and software inventory scans, and so on. The view is also listed and described in the [Client Status Views in Configuration Manager](client-status-views-configuration-manager) topic. It is unlikely that this view will be joined to other views.

### v\_CIComplianceSummary

Lists the compliance settings configuration baselines, by **CI\_ID**, and the count of Configuration Manager client computers that have been targeted, how many clients are compliant, how many have failed the compliance evaluation, the count of client computers that are noncompliant, and so on. The view is also listed and described in the [Compliance Settings Views in Configuration Manager](compliance-settings-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_ID** and **CI\_UniqueID** columns.

### v\_ClientOfferSummary

Lists the standard package and program deployments, by **OfferID**, the count of Configuration Manager client computers that have been targeted, and the count of computers reporting not started, waiting, running, retrying, failed, and succeeded status for the deployment. The view is also listed and described in the [Application Management Views in Configuration Manager](application-management-views-configuration-manager) topic. The view can be joined to other views by using the **OfferID** and **PkgID** columns.

### v\_ComponentSummarizer

Lists summary status information for all Configuration Manager components for different intervals. The view also provides the site code, server name, component name, the count of information, warning, and error messages, and so on. The information in this view contains the same information that is displayed in the **Component Status** node of the Configuration Manager console, but the view contains information for all display intervals. The view is also listed and described in the [Site Administration Views in Configuration Manager](site-admin-views-configuration-manager) topic.

Note

The value in the **Status** column provides the current status for the component. A value of 0 indicates that the component is OK, a value of 1 indicates a warning state for the component, and a value of 2 indicates a critical state for the component.

The view can be joined to other views by using the **SiteCode**, **MachineName**, and **ComponentName** columns.

### v\_FileUsageSummary

Lists software metering summary status information for file usage by site. The view is also listed and described in the [Software Metering Views in Configuration Manager](software-metering-views-configuration-manager) topic. The view can be linked by using the **FileID** column.

### v\_FileUsageSummaryIntervals

Lists software metering summary interval information for file usage. The view is also listed and described in the [Software Metering Views in Configuration Manager](software-metering-views-configuration-manager) topic. It is unlikely that this view will be joined to other views.

### v\_INSTALLED\_SOFTWARE\_DATA\_Summary

Lists the count of the installed software applications on Configuration Manager clients found through Asset Intelligence. This view contains the same source information as the **v\_GS\_INSTALLED\_SOFTWARE** view, but provides summary information instead of listing the individual system resources. The view is also listed and described in the [Asset Intelligence Views in Configuration Manager](asset-intelligence-views-configuration-manager) topic. It is unlikely that this view will be joined to other views.

### v\_MonthlyUsageSummary

Lists the Configuration Manager client computers, by **ResourceID**, and the usage summary for metered files, as well as the logged-on user name, usage time, and time of last usage. The view is also listed and described in the [Software Metering Views in Configuration Manager](software-metering-views-configuration-manager) topic. The view can be joined to other views by using the **ResourceID**, **FileID**, and **MeteredUserID** columns.

### v\_PackageStatusDetailSumm

Lists all applications, task sequences, and packages and programs, by **PackageID**, the originating site code, package name, site name, source version, the date for the summary information, the targeted count for each package, and the count for installed, retrying, and failed status. The view is also listed and described in the [Application Management Views in Configuration Manager](application-management-views-configuration-manager) topic. The view can be joined to other views by using the **PackageID** column.

### v\_PackageStatusDistPointSumm

Lists all content packages, by **PackageID**, and the installation status for the package source files on all associated distribution points. The view also provides information such as the site code, path to the distribution point, path to source location, time of last copy, and so on. The view is also listed and described in the [Application Management Views in Configuration Manager](application-management-views-configuration-manager) topic. The view can be joined to other views by using the **PackageID** and **ServerNALPath** columns.

### v\_PackageStatusRootSummarizer

Lists all applications, task sequences, and packages and programs, by **PackageID**, the package name, source version, source date, the source site, size of the source files, the targeted count for each package, and the count for installed, retrying, and failed status. The view is also listed and described in the [Application Management Views in Configuration Manager](application-management-views-configuration-manager) topic. The view can be joined to other views by using the **PackageID** column.

### v\_SiteDetailSummarizer

Lists status summary information for all Configuration Manager sites, by **SiteCode**, for different intervals. The view also provides the site name, site version, interval, the count of information, warning, and error messages, and so on. The information in this view contains the same information that is displayed in the **Site Status** node of the Configuration Manager console, but the view contains information for all display intervals. The view is also listed and described in the [Site Administration Views in Configuration Manager](site-admin-views-configuration-manager) topic. The view can be joined to other views by using the **SiteCode** column.

Note

The value in the **Status** column provides the current status for the site. A value of 0 indicates that the site is OK, a value of 1 indicates a warning state for the site, and a value of 2 indicates a critical state for the site.

### v\_SiteSystemSummarizer

Lists status summary information for all Configuration Manager sites systems for different intervals. The view also provides the object location, the site role for the site system, total disk space, free disk space, and percentage of free disk space for the site system, the time of the last status reported, and whether the site system is available. The information in this view contains the same information that is displayed in the Site System Status node of the Configuration Manager console. The view is also listed and described in the [Site Administration Views in Configuration Manager](site-admin-views-configuration-manager) topic. The view can be joined to other views by using the **SiteCode** column.

### v\_SummarizationInterval

Lists the status summarization interval. It is unlikely that this view will be joined to other views.

### v\_SummarizerRootStatus

Lists the root summary status, which is the same status displayed on the **System Status** node of the Configuration Manager console. It is unlikely that this view will be joined to other views.

### v\_SummarizerSiteStatus

Lists the site summary status, which is the same status displayed for the &lt;*site code*&gt; - &lt;*site name*&gt; node of the Configuration Manager console. The view is also listed and described in the [Site Administration Views in Configuration Manager](site-admin-views-configuration-manager) topic. The view can be joined to other views by using the **SiteCode** column.

### v\_SummaryTasks

Lists the tasks, by name and command, used to summarize Configuration Manager information, as well as the run interval, last run duration, when the task last completed successfully, next start time, and so on. It is unlikely that this view will be joined to other views.

### v\_Update\_ComplianceSummary

Lists all software updates, by **CI\_ID**, the last time summarization was run, the total count of client computers, the count of client computers reporting unknown, not applicable, missing (required), and present (already installed) states, and so on. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_ID** column.

### v\_Update\_ComplianceSummary\_Live

Lists all software updates, by CI\_ID, the last time summarization was run, the total count of client computers, the count of client computers reporting unknown, not applicable, missing (required), and present (already installed) states, and so on. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_ID** column.

### v\_Update\_DeploymentSummary\_Live

Lists all software updates, by **CI\_ID**, in active software update deployments, listed by AssignmentID, and summarized state reported by targeted clients. The view includes the target collection ID and name; the time of the last summarization; the total number of client computers targeted; the count of client computers reporting unknown, not applicable, missing (required), and present (already installed) states; the number of clients that have installed the software update and failed to install the update; and so on. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_ID**, **AssignmentID**, and **CollectionID** columns.

### v\_UpdateDeploymentSummary

Lists all software updates, by **CI\_ID**, in software update deployments, listed by **AssignmentID**, and summarized state reported by targeted clients. The view includes the target collection ID and name; the time of the last summarization; the total number of client computers targeted; the count of client computers reporting unknown, not applicable, missing (required), and present (already installed) states; the number of clients that have installed the software update and failed to install the update; and so on. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_ID**, **AssignmentID**, and **CollectionID** columns.

Note

This view has been deprecated, no longer generates summary data, and may be removed in the future.

### v\_UpdateEnforcementSummaryPerCollection

Lists the summary state for all software updates that have been deployed. The view provides the software update, by **CI\_ID**, target collection, collection name, and summarized enforcement state reported by clients in the collection. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_ID** column.

### v\_UpdateSummaryPerCollection

Lists the summary state for all software updates and the compliance state per collection. The view includes the software update, by **CI\_ID**; target collection ID and name; the time of the last summarization; the total number of client computers targeted; the count of client computers reporting not applicable, missing (required), present (already installed), and unknown states; and so on. The view is also listed and described in the [Software Updates Views in Configuration Manager](software-updates-views-configuration-manager) topic. The view can be joined to other views by using the **CI\_ID** and **CollectionID** columns.

## Alert views

The alerts views are listed in this section.

### v\_Alert

Lists information about the events than can be generated by Configuration Manager. This includes the severity of the alert, when it was created, and who created it. This view can be joined to other views by using the **Name** and **Severity** columns.

### v\_AlertEvents

Lists information about the events that have been triggered on the Configuration Manager site. This view can be joined to other views by using the **AlertID** and EventMachineID columns.

### v\_AlertValidFeatureArea

Lists information about each product component, by feature area ID, that might generate alerts. It is unlikely that this view will be joined to other views.

### v\_AlertVariable\_G

Lists system information about variables that are assigned to alerts. It is unlikely that this view will be joined to other views.

### v\_SMS\_Alert

Lists information about the built-in, and user created alerts that might be displayed in the Configuration Manager console. It is unlikely that this view will be joined to other views.

### v\_Report\_StatusMessageDetail

Lists detailed information about status messages returned by each Configuration Manager component. This includes the record ID, the time of the status message, the component that generated the message, and more. This view can be joined to other views by using the **RecordID** column.

### v\_StateMessageStatistics

Lists information about the number of state messages returned for each topic type. It is unlikely that this view will be joined to other views.

### v\_StatMsgWithInsStrings

Lists detailed information about status messages returned by each Configuration Manager component. This includes the record ID, the time of the status message, the component that generated the message, and more. This view can be joined to other views by using the **RecordID** column.