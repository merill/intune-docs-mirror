---
layout: Conceptual
title: Compliance settings views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/compliance-settings-views-configuration-manager
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
description: Information about the compliance of devices with regard to a number of configurations.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: dfacd4bd-2419-2b0a-4aa9-c8c245dc2081
document_version_independent_id: 531ff75e-ee1f-83df-088e-9b833f8e2549
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/compliance-settings-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/compliance-settings-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/compliance-settings-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 7571c182-7937-6ce2-a181-9d7d905656f1
---

# Compliance settings views - Configuration Manager | Microsoft Learn

The Configuration Manager compliance settings views contain information about the compliance of devices with regard to a number of configurations, such as whether the correct Windows operating system versions are installed and configured appropriately, whether all required applications are installed and configured correctly, whether optional applications are configured appropriately, and whether prohibited applications are installed. The compliance settings views contain information about the configuration baselines in the site, which configuration baselines store information about configuration items, software updates, bundles, drivers, and so on. Several of the status and status summarizer views contain status information for the configuration items and configuration item assignments.

The following sections provide detailed information about compliance settings views, compliance settings status views, and compliance settings status summarizer views.

## Compliance settings views

There are many compliance settings views, and it can sometimes be difficult to find the information that you need for your report SQL statement. The following are some of the key compliance settings views and columns:

- **CI\_ID** column � Commonly used to join compliance settings views
- **v\_ConfigurationItems** view - Used to retrieve information about the configuration items in the site.
- **v\_CategoryInfo** and **v\_LocalizedCIProperties** views - Often be used to retrieve additional information about the configuration items.
- **AssignmentID** column and the **v\_CIAssignment** view - Used to retrieve information about the configuration item deployments.
- **v\_CIAssignmentToCI** view - Can be used as the link between the **v\_ConfigurationItems** and **v\_CIAssignment** views.
- **v\_CIAssignmentTargetedMachines** view - can be used as the link between the **v\_CIAssignment** view and the views that contain resource information, such as the **v\_R\_System** view.

The compliance settings views are described in this section.

### v\_AssignmentTargetedCIs

Lists the assignment ID, **CI\_ID** and unique assignment ID for each deployed configuration item. This view can be joined to other views by using the **CI\_ID** and **AssignmentID** columns.

### v\_BaselineTargetedComputers

Lists the clients, by **ResourceID**, to which a configuration baseline has been deployed, by **CI\_ID**. This view displays only configuration baselines (**CI\_Type = 2**). This view can be joined to other views by using the **CI\_ID** and **ResourceID** columns.

### v\_Categories

Lists the configuration item category instances, by **CategoryInstanceID** and **CategoryInstance\_UniqueID**, category type name, date the category instance was last modified, source site, and the parent category. This view contains the same source data as the **v\_CategoryInstances** view, but it displays more columns. This view can be joined to other views by using the **CategoryInstanceID** and **ParentCategoryInstanceID** columns.

### v\_CategoryInfo

Lists the configuration item category instances, by **CategoryInstanceID** and **CategoryInstance\_UniqueID**, category type name, date the category instance was last modified, source site, parent category, category instance name, and locale ID. This view contains the same data as the **v\_Categories** view plus two additional columns from the **v\_LocalizedCategories\_SiteLoc** view. This view can be joined to other views by using the **CategoryInstanceID** and **ParentCategoryInstanceID** columns.

### v\_CategoryInstances

Lists the configuration item category instances, by category instance ID and category instance unique ID, category type name, date the category instance was last modified, source site, and parent category. This view contains the same source data as the **v\_Categories** view, but it displays fewer columns. This view can be joined to other views by using the **CategoryInstanceID** and **ParentCategoryInstanceID** columns.

### v\_CI\_ApplicablePlatforms

Lists the configuration items, by **CI\_ID** and **CI\_UniqueID** that have specific applicable platforms configured, including the operating system name, operating system maximum and minimum versions, and operating system platform. For example, a configuration item created in the Configuration Manager console that has **All Windows platforms** selected for the **Applicability** property will not be listed in this view, but the view will contain a record for each Windows platform for the configuration item when the **Specified Windows platforms** is selected. This view can be joined to other views by using the **CI\_ID** and **CI\_UniqueID** columns.

### v\_CI\_DriverHardwareIDs

Lists the configuration items, by **CI\_ID** and **CI\_UniqueID**, that have a configuration item type of **Driver** (CIType\_ID=6) and the associated hardware IDs that the driver supports. For example, a driver added in the **Drivers** node under the **Operating System Deployment** node in the Configuration Manager console will be listed in this view as well as the hardware IDs that it supports. The view can be joined to other views by using the **CI\_ID** and **CI\_UniqueID** columns.

### v\_CI\_DriverModels

Lists the configuration items, by **CI\_ID** and **CI\_UniqueID**, that have a configuration item type of **Driver** (CIType\_ID=6) and the supported model names and driver manufacturer. The supported models are listed in the **Applicability** section of the driver properties in the Configuration Manager console. The view can be joined to other views by using the **CI\_ID** and **CI\_UniqueID** columns.

### v\_CI\_DriversCIs

Lists the configuration items, by **CI\_ID** and **CI\_UniqueID**, that have a configuration item type of **Driver** (CIType\_ID=6), as well as the driver type, driver INF file, driver date, driver version, driver class, driver provider, whether the driver is signed (and if so, the driver signer), and whether the driver is boot critical. The view can be joined to other views by using the **CI\_ID** and **CI\_UniqueID** columns.

### v\_CIAssignment

Lists the configuration item deployments by **AssignmentID**, **Assignment\_UniqueID**, and **AssignmentName** that are active in the Configuration Manager hierarchy, including the deployment description, collection ID and name that is targeted by the deployment, start time, enforcement deadline, whether the deployment is an update deployment, and other details about the deployment. The view can be joined to other configuration items, software updates, and status views by using the **AssignmentID** and **Assignment\_UniqueID** columns, and it can be joined to collection views by using the **LocalCollectionID** and **CollectionID** columns.

### v\_CIAssignmentTargetedCollections

Lists the deployments, by **AssignmentID**, that are active in the Configuration Manager hierarchy and the associated target collection, by **LocalCollectionID**, **CollectionID**, and **CollectionName**. The view can be joined to other configuration items, software updates, and status views by using the **AssignmentID** column, and it can be joined to collection views by using the **LocalCollectionID** and **CollectionID** columns.

### v\_CIAssignmentTargetedMachines

Lists the deployments, by **AssignmentID**, that are active in the Configuration Manager hierarchy and the Configuration Manager clients, by **ResourceID**, that have been targeted for the assignment. The view can be joined to other views by using the **AssignmentID** and **ResourceID** columns.

### v\_CIAssignmentToCI

Lists the deployments, by **AssignmentID**, and the configuration items, by **CI\_ID**, that are in the deployment. For example, if the deployment is a software update deployment, the configuration item ID for each software update in the deployment will be listed. The view can be joined to other views by using the **AssignmentID** and **CI\_ID** columns.

### v\_CICategories

Lists the configuration items, by **CI\_ID**, and the configuration item category instances, by **CategoryInstanceID** and **CategoryInstance\_UniqueID**, in which they belong, as well as the category type name, date last modified, source site, and parent category instance ID. This view contains the same information as the **v\_CICategories\_All** view, except that it does not contain parent categories. The view can be joined to other views by using the **CI\_ID**, **CategoryInstanceID**, and **ParentCategoryInstanceID** columns.

### v\_CICategories\_All

Lists the configuration items, by **CI\_ID**, and the configuration item category instances, by **CategoryInstanceID** and **CategoryInstance\_UniqueID**, in which they belong, as well as the category type name, date last modified, source site, and parent category instance ID. This view contains the same information as the **v\_CICategories** view, except that it also contains parent categories. The view can be joined to other views by using the **CI\_ID**, **CategoryInstanceID**, and **ParentCategoryInstanceID** columns.

### v\_CICategoryInfo

Lists the configuration items, by **CI\_ID**, and the configuration item category instances, by **CategoryInstanceID** and **CategoryInstance\_UniqueID**, in which they belong, as well as the category type name, date the category instance was last modified, source site, parent category, category instance name, and locale ID. This view contains the same data as the **v\_CICategories** view plus two additional columns from the **v\_LocalizedCategories\_SiteLoc** view, and the same data as the **v\_CICategoryInfo\_All** view, except that it does not contain parent categories. The view can be joined to other views by using the **CI\_ID**, **CategoryInstanceID**, and ParentCategoryInstanceID columns.

### v\_CICategoryInfo\_All

Lists the configuration items, by **CI\_ID**, and the configuration item category instances, by **CategoryInstanceID** and **CategoryInstance\_UniqueID**, in which they belong, as well as the category type name, date the category instance was last modified, source site, parent category, category instance name, and locale ID. This view contains the same data as the **v\_CICategories\_All** view plus two additional columns from the **v\_LocalizedCategories\_SiteLoc** view, and the same data as the **v\_CICategoryInfo** view, except that it also contains parent categories. The view can be joined to other views by using the **CI\_ID**, **CategoryInstanceID**, and **ParentCategoryInstanceID** columns.

### v\_CIContents

Lists the configuration items, by **CI\_ID**, that have associated content, which is listed by **ContentID**, and whether the content has been provisioned. For example, configuration items with the Software Updates (CIType\_ID = 1) have associated update files, and **Driver** configuration types (CIType\_ID = 6) have associated driver files. The view can be joined to other views by using the **CI\_ID** and **Content\_ID** columns.

### v\_CIContents\_All

Lists configuration items that have associated content, by **CI\_ID**, the configuration item ID for the configuration item in which the content is associated, the content ID, whether the content has been provisioned, and so on. The configuration item ID for a configuration item bundle is listed multiple times in the **CI\_ID** column, and the configuration item IDs for the configuration items that are part of the bundle are listed in the **ContentCI\_ID** column. For example, a configuration item that is not a bundle would have the same configuration item ID in the **CI\_ID** and **ContentCI\_ID** columns. A bundle configuration item would have one listing with the configuration item ID in the **CI\_ID** column and the same configuration item ID in the **ContentCI\_ID** columns, and then new listings would contain the configuration item ID for the bundle configuration item in the **CI\_ID** column and the configuration item ID for the bundled configuration items in the **ContentCI\_ID** column. The **ContentLevel** column represents how many times a configuration item ID is listed in the **ContentCI\_ID** column. The view can be joined to other views by using the **CI\_ID**, **ContentCI\_ID**, and **Content\_ID** columns.

### v\_CICurrentSettingsComplianceStatusDetail

Lists the configuration items, by **CI\_ID**, that are in a configuration baseline, that have been assigned to Configuration Manager clients, and are reporting a validation error or noncompliance. The information includes the NetBIOS name of the client, configuration item name, setting name, setting type, setting description, constraint name, constraint description, and validation rule. The view can be joined to other views by using the **CI\_ID** and **ResourceID** columns.

### v\_CIEULA\_LocalizedContent

Lists the configuration items, by **CI\_ID**, that have associated license terms, as well as the locale ID, the content unique ID for the license terms, the license terms text, and the source site. The view can be joined to other views by using the **CI\_ID** column.

### v\_CIRelation

Lists configuration items, by configuration item ID in the **FromCIID** column, the configuration items that are related to the first configuration item, by configuration item ID in the **TOCIID** column, and the type of relation. Configuration items with a bundle level of 1 are listed in the **ToCIID** column. For example, if the configuration item ID for an update bundle is listed in the **FromCIID** column and another update bundle is part of the first bundle, only the configuration item ID for the update bundle will be listed in the **ToCIID** column and not the software updates that are part of the second update bundle. The view can be joined to other views by using the **FromCIID**, **ToCIID**, and **RelationType** columns. The **FromCIID** column in this view contains the same information as the **CI\_ID** column, and the **ToCIID** column contains the same information as the **ReferencedCI\_ID** column in the **v\_CIRelation\_All** view.

Note

The configuration item relation types can be retrieved from the **v\_CIRelationTypes** view.

### v\_CIRelation\_All

Lists the relationships between configuration items, by **CI\_ID**, and other configuration items, by **ReferencedCI\_ID**, as well as how deep the relationship is between the configuration items, by level. The **CI\_ID** column lists the configuration item to which the configuration item in the **ReferencedCI\_ID** is related, such as a software updates bundle and associated software updates that are part of the bundle or a configuration baseline and the associated configuration items that are part of the baseline. Configuration items are also listed with a relationship to themselves, which is indicated by a value of 0. For example, the configuration item ID for an update bundle is listed in the **CI\_ID** column, the same configuration item ID is listed in the **ReferencedCI\_ID** column, and the Level is 0. In a different row, a configuration item ID for a different update bundle is listed in the **CI\_ID** column, the configuration item ID for the same software update that was part of the previous update bundle is listed in the **ReferencedCI\_ID** column because it is also part of this update bundle, and the Level is 1. In a different row, a configuration item ID for an update list is listed in the **CI\_ID** column, the configuration item ID for the same software update that was part of the previous update bundle is listed in the **ReferencedCI\_ID** column because it is also part of this update list, and the **Level** is 3. The view can be joined to other views by using the **CI\_ID** and **ReferencedCI\_ID** columns. The **CI\_ID** column in this view is the same as the FromCIID column, and the **ReferencedCI\_ID** column is the same as the **ToCIID** column in the **v\_CIRelation** and **v\_CIRelationEx** views.

Note

The configuration item relation types can be retrieved from the **v\_CIRelationTypes** view.

### v\_CIRelationEx

Lists the relationships between configuration items, by **FromCIID**, **TOCIID**, **RelationType**, and **RelationDepth**. The **FromCIID** column is the configuration item to which the configuration item in the ToCIID is related, such as a software updates bundle and associated software updates that are part of the bundle or a configuration baseline and the associated configuration items that are part of the baseline. The **RelationType** column indicates the type of relationship between the configuration items, and the **RelationDepth** column indicates how deep the relationship is for a configuration item listed in the **ToCIID** column. This view does not display configuration items with a **RelationDepth** of 0, which is the relationship of the configuration item to itself. For example, if the configuration item ID for an update bundle is listed in the **FromCIID** column and the configuration item ID for a software update that is part of the bundle is listed in the **ToCIID** column. The **RelationType** in this case is 1 (Bundled), and the **RelationDepth** is 1. In the next row, a configuration item ID for an update bundle that also contains the previous update is listed in the **FromCIID** column, the same configuration item ID for the update is listed in the **FromCIID** column, the **RelationType** is still 1, and the **RelationDepth** is now 2. In the next row, a configuration item ID for an update list that contains the same update is listed in the **FromCIID** column, the same configuration ID for the update is listed in the **FromCIID** column, the **RelationType** is still 1, and the **RelationDepth** is now 3. The view can be joined to other views by using the **FromCIID**, ToCIID, and **RelationType** columns. The **FromCIID** column in this view contains the same information as the **CI\_ID** column, and the **ToCIID** column contains the same information as the **ReferencedCI\_ID** column in the **v\_CIRelation\_All** view.

Note

The configuration item relation types can be retrieved from the **v\_CIRelationTypes** view.

### v\_CIRelationTypeMapping

Lists the configuration item elements, such as configuration baselines and software updates, the relation type value, and a description for the relation type. The view can be joined to other compliance settings views by using the **RelationType** column.

### v\_CIRelationTypes

Lists the relation type values, a description for the relation type, and whether the relation type is recursive. The view can be joined to other compliance settings views by using the **RelationType** column.

### v\_CITargetedCollections

Lists configuration items, by **CI\_ID**, and the collection that the configuration item targets, by **LocalCollectionID**, **CollectionID**, and **CollectionName**. The view can be joined to other compliance settings views by using the **CI\_ID**, **LocalCollectionID**, and **CollectionID** columns.

### v\_CITargetedMachines

Lists configuration items, by **CI\_ID**, and the Configuration Manager clients that the configuration item targets, by **ResourceID**. The view can be joined to other views by using the **CI\_ID** and **ResourceID** columns.

### v\_CITypes

Lists the configuration item types, by **CIType\_ID**, and the type name. For example, software updates have a **CIType\_ID** of 1, configuration baselines have a **CIType\_ID** of 2, and so on. The view can be joined to other views by using the **CIType\_ID** column, but it is more likely that this view will be used as a reference when filtering configuration item data retrieved from configuration item views in the report SQL statement.

### v\_CIValidationSeverity

Lists the possible configuration item validation severities, by severity, and a description, such as **Informational**, **Warning**, and **Error**. It is unlikely that this view will be joined to other views, but it can be used as a reference when filtering configuration item data retrieved from configuration item views in the report SQL statement.

### v\_ConfigurationItems

Lists the configuration items in the Configuration Manager site hierarchy, by **CI\_ID** and **CI\_UniqueID**, and details about the configuration item such as configuration item type ID, configuration item version, date the configuration item was created and last modified, whether it is part of a bundle, whether it is a hidden configuration item, whether it has been deployed, whether it is enabled, the source site for the configuration item, and so on. When creating SQL statements for the desired configuration management, software updates, and operating system deployment features, this view will most often be joined to other views when creating the report SQL statement. The view can be joined to other views by using the **CI\_ID**, **CI\_UniqueID**, **ModelName**, **SDMPackage\_ID**, and **CIType\_ID** columns.

### v\_LocalizedCategories

Lists the configuration item category instances in the Configuration Manager site hierarchy, by **CategoryInstanceID** and **CategoryInstanceName**, and the locale for the category instance. Category instances consist of languages, update categories, products, product families, custom categories for desired configuration management, and so on. The view can be joined to other views by using the **CategoryInstanceID** column.

### v\_LocalizedCategories\_SiteLoc

Lists the configuration item category instances for the local Configuration Manager site, by **CategoryInstanceID** and **CategoryInstanceName**, the locale that the category instance is for, and the localized category instance name, which is the locale and category instance name combined. Category instances consist of languages, update categories, products, product families, custom categories for desired configuration management, and so on. The view can be joined to other views by using the **CategoryInstanceID** column.

### v\_LocalizedCIProperties

Lists the configuration items in the Configuration Manager site hierarchy, by **CI\_ID**, that contain localized properties, such as the display name, description, and informative URL for a software update. The view can be joined to other views by using the **CI\_ID** column.

### v\_LocalizedCIProperties\_SiteLoc

Lists the configuration items for the local Configuration Manager site, by **CI\_ID**, that contain localized properties, such as the localized properties for a software update. The information includes the locale ID, display name, description, and configuration item informative URL. The view can be joined to other views by using the **CI\_ID** column.

### v\_SDMErrorCategories

Lists the SDM error categories, by **Category**, and the description for the error. It is unlikely that this view will be joined to other views.

### v\_SDMLocalizedData\_SiteLoc

Lists the SDM packages, by **ModelName**, the SDM package version, the **localeID** for the data in the SDM package, and the localized data in XML format. The view can be joined to other views by using the **ModelName** column.

### v\_SMSConfigurationItems

This view can be joined to other views by using the **CI\_ID** and **ModelID** columns.

### v\_CIRules

Lists all rules that have been created in the Configuration Manager site. Includes the rule name, ID, and description. This view can be joined to other views by using the **CI\_ID** column.

### v\_CIRulesAll

Lists all configuration item rules that are currently being used in the Configuration Manager site. This view can be joined to other views by using the **CI\_ID** column.

### v\_CISettingReferences

Lists all settings that are currently deployed in the Configuration Manager site. This view can be joined to other views by using the **CI\_ID** column.

### v\_CISettings

Lists all available settings that can be used in the Configuration Manager site. This view can be joined to other views by using the **CI\_ID** column.

### v\_CIToContent

Lists, by **CI\_ID**, any content packages that are associated with a configuration item. This view can be joined to other views by using the **CI\_ID** and **Content\_UniqueID** columns.

### v\_CIComplianceStatusErrorDetail

Lists, by **CI\_ID**, information about the last compliance message returned by clients that evaluated the configuration item for compliance. This includes the time the last message was received and information about settings contained in the configuration item. This view can be joined to other views by using the **CI\_ID** column.

### v\_CIComplianceStatusReificationDetail

Lists, by model ID instances where Configuration Manager remediated settings on client devices. This includes the settings ID and the value of the setting before and after it was remediated. This view can be joined to other views by using the **ModelID** column.

### v\_CIConfigPointTypes

Lists the different system configuration point types by type and name. It is unlikely that this view will be joined to other views.

### v\_CIConflictCode

Lists the various error codes and descriptions that might be returned when configuration data contains conflicting settings. It is unlikely that this view will be joined to other views.

### v\_CIContentPackage

Lists each configuration item together with the ID of any associated packages. This view can be joined to other views by using the **CI\_ID**, or **PkgID** columns.

### v\_SMS\_CIRelation

Lists, by **FromCIID**, the relationships between configuration items. It is unlikely that this view will be joined to other views.

### v\_SMSCICurrentComplianceStatus

Lists compliance information for each configuration item that has been deployed. This includes whether the configuration item is applicable, it's version, the last time it reported about compliance, and more. This view can be joined to other views by using the **CI\_CurrentComplianceStatusID** column.

### v\_CI\_CurrentErrorDetails

Lists, by record ID, the configuration items that have generated an error when they were evaluated for compliance. This includes the error type, information about the setting, and the error code. This view can be joined to other views by using the **CI\_ID** column.

### v\_CIAppDependenceRelations

Lists information about the application dependencies that are currently active in deployment types. It is unlikely that this view will be joined to other views.

### v\_CIAssignmentToGroup

No description.

### v\_CIComplianceStatusComplianceDetail

Lists, by CI\_ID, deployed configuration items, and the compliance status of each setting in the configuration item. This view can be joined to other views by using the **CI\_ID** column.

### v\_CIComplianceStatusConflictsDetail

Lists details about conflicts that were found when configuration item settings and rules were evaluated for compliance. This includes the time of the last status, information about the settings and rules, and the conflict error code. This view can be joined to other views by using the **ResourceID** column.

### v\_CICurrentRuleDetail

Lists, by record ID, the current compliance status of configuration item rules. This view can be joined to other views by using the **RecordID** column.

### v\_CIErrorDetails

Lists information about configuration items that reported errors when they were evaluated for compliance. This includes information about the configuration item, its settings and rules, and details about the error that was generated. This view can be joined to other views by using the **CI\_ID** and **ResourceID** columns.

### v\_CI\_CurrentComplianceStatus

Lists, by **CI\_ID**, the currently deployed configuration items, and detailed information about their current compliance status. This view can be joined to other views by using the **CI\_ID** and **ResourceID** columns.

### v\_CIAssignmentStatusSummary

Lists details about the compliance status of currently deployed configuration data. This view can be joined to other views by using the **AssignmentID** column.

### v\_CIAssignmentSummary

Lists summary information for deployed configuration items, including the summarization time, success and failure statistics, requirements not met, and more. This view can be joined to other views by using the **AssignmentID** column.

## Compliance settings status views

The compliance settings status views contain information about the compliance, evaluation, and enforcement state of configuration items. For more information about the status views, see [Status and alert views in Configuration Manager](status-alert-views-configuration-manager). The status views that contain compliance settings information are described in this section.

### v\_CIAssignmentStatus

Lists the enforcement and evaluation state messages received from Configuration Manager client computers for all assigned configuration items, including assigned software update deployments and assigned configuration baselines. The assignment ID, resource ID, last enforcement state message ID, last evaluation state message ID, and so on are provided. The view can be joined to other views by using the **AssignmentID** and **ResourceID** columns.

### v\_CIComplianceHistory

Lists the configuration items, by **CI\_UniqueID** and **CI\_ID**, that are configuration baselines or a configuration item in a configuration baseline, have been assigned to a Configuration Manager client (listed by **ResourceID**), and it lists compliance information for the configuration item. The information includes the compliance start and end dates, whether the configuration item is applicable to the client, whether the client is compliant for the configuration item, and so on. The view can be joined to other views by using the **CI\_UniqueID**, **CI\_ID**, and **ResourceID** columns.

### v\_CIComplianceStatusDetail

Lists the configuration items, by **CI\_ID** and **CI\_UniqueID**, that are in a configuration baseline, have been assigned to a Configuration Manager client (listed by **ResourceID**), and have a state value of **Non-Compliant**. The view can be joined to other views by using the **CI\_ID**, **CI\_UniqueID**, **ResourceID**, and **ModelName** columns.

### v\_CICurrentComplianceStatus

Lists the compliance and enforcement states for configuration items, by configuration item ID, as well as the resource ID, whether the configuration item is applicable to the resource, and information related to the compliance and evaluation of the configuration item. The view can be joined to other views by using the **CI\_ID**, **ResourceID**, **CI\_UniqueID**, **ModelName**, **ComplianceState**, and **LastEnforcementMessageID** columns. The **ComplianceState** column provides the state ID for state messages with a topic type of 401. The **LastEnforcementMessageID** column provides the state ID for state messages with a state message topic type of 402.

### v\_DCMClientStatusInformation

Lists all possible compliance settings client states. It is unlikely that this view will be joined to other views.

## Compliance settings status summarizer views

The compliance settings status summarizer views provide summary information for configuration item deployments and configuration baselines. For more information about the status summarizer views, see [Status and alert views in Configuration Manager](status-alert-views-configuration-manager). The status summarizer views that contain compliance settings information are described in this section.

### v\_AssignmentSummaryPerTopic

Lists the deployments, by assignment ID, the type of deployment state message, the state ID for the type, the count of Configuration Manager client computers that are in the deployment state, and the total count of client computers that have been targeted for the deployment. The view can be joined to other views by using the **AssignmentID** column.

Note

There are three deployment states. A state type of 300 is deployment compliance, type 301 is deployment enforcement, and type 302 is deployment evaluation. You can find a list of the state IDs by looking in the **v\_StateNames** view.

### v\_CIComplianceSummary

Lists the compliance settings configuration baselines, by **CI\_ID**, and the count of Configuration Manager client devices that have been targeted, how many clients are compliant, how many have failed the compliance evaluation, how many are noncompliant, and more. The view can be joined to other views by using the **CI\_ID** and **CI\_UniqueID** columns.