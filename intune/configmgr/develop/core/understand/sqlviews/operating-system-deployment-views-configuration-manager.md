---
layout: Conceptual
title: Operating system deployment views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/operating-system-deployment-views-configuration-manager
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
description: Information about boot image packages, computer association state migrations, and operating system image packages.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: a0b71cd1-bf44-eb3c-4a5e-50ca1e64d208
document_version_independent_id: fb9d58bf-87b7-0c52-8847-da354569f48f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/operating-system-deployment-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/operating-system-deployment-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/operating-system-deployment-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 90fa9550-65d7-a29d-dba9-a8a0aac56365
---

# Operating system deployment views - Configuration Manager | Microsoft Learn

The Configuration Manager operating system deployment views contain information about boot image packages, computer association state migrations, operating system image packages, task sequences, driver packages, and so on. There is also a status view that contains information about the status of task sequence steps.

The following sections provide detailed information about operating system deployment views and operating system deployment status views.

## Operating system deployment views

The operating system deployment views are described in this section.

### v\_BootImagePackage

Lists the boot image packages in the Configuration Manager site hierarchy, including package ID, package name, the path of the package source files, source site, priority, package flags, last refresh time, and more. The view can be joined to other views by using the **PackageID** column.

### v\_BootImagePackage\_References

Lists the boot image packages, by **pkgID**, the configuration item ID for the drivers that have been added to the boot image package, as well as the path to the driver source files. The view can be joined to the **v\_ConfigurationItems** view by using the **CI\_ID** column and other views by using the **PkgID** column, which contains the same package ID information as the **PackageID** column in other views.

### v\_DriverContentToPackage

Lists the driver packages, by package ID and package name, the configuration item IDs for the drivers contained in the package, and the content IDs for the drivers. The view can be joined to the **v\_ConfigurationItems** view by using the **CI\_ID** column, the **v\_Contents** view by using the **Content\_ID** column, and other views by using the **PkgID** column, which contains the same package ID Information as the **PackageID** column in other views.

### v\_DriverPackage

Lists the driver packages in the Configuration Manager site hierarchy, including package ID, package name, the path of the package source files, source site, priority, package flags, last refresh time, and more. The driver packages are created in the Driver Packages node of the Configuration Manager console. The view can be joined to other views by using the **PackageID** column.

### v\_ImagePackage

Lists the operating system image packages in the Configuration Manager site hierarchy, including package ID, package name, the path of the package source files, source site, priority, package flags, last refresh time, and more. The operating system image packages are created in the **Operating System Images** node of the Configuration Manager console. The view can be joined to other views by using the **PackageID** column.

### V\_LastPXEDeployment

Lists information about the last PXE deployment including the Mac address of the computer, the NetBIOS name and more. The view can be joined to other views by using the **MachineID** column.

### v\_MachineSettings

Lists the Configuration Manager clients, by **ResourceID**, that have operating system deployment computer settings, including the source site, locale, and the date the settings were last modified. The view can be joined to other views by using the **ResourceID** column.

### v\_StateMigration

Lists the computer associations, by **MigrationID**, that have been created in the **User State Migration** node of the Configuration Manager console. Computer associations organize the migration of user state and settings from a source computer to a destination computer. The view provides information about the migration type, source computer name, source client resource ID, last logged on user, restore computer name, restore client resource ID, and so on. The view can be joined to other views by using the **SourceClientResourceID** and **RestoreClientResourceID** columns.

### v\_TaskSequencePackage

Lists the task sequences in the Configuration Manager site hierarchy, including the task sequence package ID, package name, source site, priority, package flags, last refresh time, boot image package ID, and more. The **BootImageID** column contains the package ID for the boot image package defined in the task sequence. The task sequences are created in the **Task Sequences** node of the Configuration Manager console. The view can be joined to other views by using the **PackageID** and **BootImageID** columns. The **BootImageID** column contains the same package ID information as the **ReferencePackageID** column in the **v\_TaskSequenceReferencesInfo** view, and the same package ID information as the **PackageID** column in other views.

### v\_TaskSequencePackageReferences

Lists the packages in a task sequence that reference other packages. This view can be joined to other views by using the **PackageID** and **RefPackageID** columns.

### v\_TaskSequenceReferenceDps

Lists the task sequences, by Task sequence ID, which is the task sequence package ID, the boot image package ID, server NAL path (path to distribution point), site code, task sequence source version, and task sequence hash. The view can be joined to other views by using the **TaskSequenceID** and **PackageID** columns. The **TaskSequenceID** column in this view contains the same package ID information as the **PackageID** column in other views.

### v\_TaskSequenceReferencesInfo

Lists the task sequences, by Package ID, and the reference package ID for the associated boot image, as well as the reference name, reference version, and so on. The view can be joined to other views by using the **PackageID** and **RefPackageID** columns. The **RefPackageID** column contains the same package ID information as the **BootImageID** column in the **v\_TaskSequencePackage** view, and the same package ID information as the **PackageID** column in other views.

### v\_UserStateMigration

Lists the user accounts, by *Domain*\*Username*, that will be migrated as specified for the computer associations created in the **User State Migration** node of the Configuration Manager console. The locale ID, source client resource ID, and restore client resource ID are also listed. The view can be joined to other views by using the **SourceClientResourceID** and **RestoreClientResourceID** columns, which contain the same information as the **ResourceID** column in other views.

### v\_TaskSequenceAppReferenceDps

Lists, by task sequence ID, information about the content packages that are associated with task sequences. This view can be joined to other views by using the **PackageID** and **TaskSequenceID** columns.

### v\_TaskSequenceAppReferencesInfo

Lists, by package ID, the content packages that are referenced by a task sequence that installs an application. This view can be joined to other views by using the **PackageID** column.

## Operating system deployment status view

The operating system deployment status view contains status information for operating system deployment task sequence steps. For more information about the status views, see [Status and alert views in Configuration Manager](status-alert-views-configuration-manager). The status view that contains operating system deployment information is described in this section.

### v\_TaskExecutionStatus

Lists the status for operating system deployment task sequence steps, as well as the advertisement ID, resource ID, action name, and so on. The view can be joined to other views by using the **AdvertisementID** or **ResourceID** columns.