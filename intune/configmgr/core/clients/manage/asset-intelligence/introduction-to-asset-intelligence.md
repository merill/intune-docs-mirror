---
layout: Conceptual
title: Asset intelligence introduction - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence
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
description: Use asset intelligence in Configuration Manager to inventory and manage software license usage throughout your enterprise.
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 80828b1b-4dd1-5f44-cdd2-0b7ae7be26c7
document_version_independent_id: d2d0e2d6-33f7-4739-d42f-b85a562bb454
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/691e3042-55ad-4ce1-b5e9-649b1cc47b5c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b7d11190-096c-4ddb-87db-63764f603aac
platformId: be6a7777-730d-86bc-3352-af89296ca4cb
---

# Asset intelligence introduction - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in November 2021, this feature of Configuration Manager is [deprecated](../../../plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). For more information, see [Asset intelligence deprecation](deprecation).

This deprecation plan doesn't include the [product lifecycle dashboard](product-lifecycle-dashboard).

Inventory and manage software license usage throughout your enterprise by using the asset intelligence catalog. Asset intelligence adds hardware inventory classes to improve the breadth of information that Configuration Manager collects. This information includes the hardware and software titles used in your environment. Over 60 reports present this information in an easy-to-use format. Many of these reports link to more specific reports. Query for general information and drill down to more detailed information.

Add custom information to the asset intelligence catalog. For example, custom software categories, software families, software labels, and hardware requirements. To dynamically update the asset intelligence catalog with the most current information available, connect it to the Microsoft Cloud.

Use asset intelligence to help reconcile your enterprise software license usage. Import software license information into the Configuration Manager site database to view it against what software is being used.

## Asset intelligence catalog

The asset intelligence catalog is a set of database tables stored in the site database. These tables include categorization and identification information for over 300,000 software titles and versions. They also help manage hardware requirements for specific software titles.

Asset intelligence provides software license information for software titles that are being used, both of Microsoft and of non-Microsoft software. A predefined set of hardware requirements for software titles is available in the asset intelligence catalog, and you can create new user-defined hardware requirement information to meet custom requirements. You can also customize information in the asset intelligence catalog, and you can upload software title information to the Microsoft cloud for categorization.

Asset intelligence catalog updates that include newly released software are available for download periodically to perform bulk catalog updates. It can also be dynamically updated by using the asset intelligence synchronization point.

### Software categories

Asset intelligence software categories are used to widely categorize inventoried software titles and as high-level groupings of more specific software families. For example, a software category could be energy companies, and a software family within that software category could be oil and gas or hydroelectric. Many software categories are predefined in the asset intelligence catalog. You can create user-defined categories to additionally define inventoried software. The validation state for all predefined software categories is always **Validated**. Custom software category information added to the asset intelligence catalog is **User Defined**.

For more information about how to manage software categories, see [Configuring asset intelligence](configuring-asset-intelligence).

Note

Predefined software category information stored in the asset intelligence catalog is read-only. You can't change or delete it. Administrative users can add, modify, or delete user-defined software categories.

### Software families

Asset intelligence software families are used to define inventoried software titles within software categories. Many software families are predefined in the asset intelligence catalog. You can create user-defined categories to additionally define inventoried software. The validation state for all predefined software families is always **Validated**. Custom software family information added to the asset intelligence catalog is **User-Defined**.

For more information about how to manage software families, see [Configuring asset intelligence](configuring-asset-intelligence).

Note

Predefined software family information is read-only and can't be changed. Administrative users can add, modify, or delete user-defined software families.

### Software labels

Asset intelligence custom software labels let you create filters to group software titles and to view them in asset intelligence reports. Use software labels to create user-defined groups of software titles that share a common attribute. For example, you could create a software label called Shareware, associate it with inventoried shareware titles, and run a report to display all software titles with that label. There are no predefined labels. The validation state for software labels is always **User Defined**.

For more information about how to manage software labels, see [Configuring asset intelligence](configuring-asset-intelligence).

### Hardware requirements

Use the hardware requirements information to verify that computers meet the hardware requirements for software titles before they're targeted for software deployments. Manage hardware requirements for software titles in the **Assets and Compliance** workspace in the **Hardware Requirements** node under the **Asset Intelligence** node.

Many hardware requirements are predefined in the asset intelligence catalog. Create new user-defined hardware requirement information to meet custom requirements. The validation state for all predefined hardware requirements is always **Validated**. User-defined hardware requirements information added to the asset intelligence catalog is **User Defined**.

For more information about how to manage hardware requirements, see [Configuring asset intelligence](configuring-asset-intelligence).

Note

The hardware requirements displayed in the Configuration Manager console are retrieved from the asset intelligence catalog. They aren't based on inventoried software title information from clients.

Hardware requirement information isn't updated as part of the synchronization process with Microsoft.

You can create user-defined hardware requirements for inventoried software that doesn't have associated hardware requirements.

By default, the following information is displayed for each listed hardware requirement:

- **Software Title**: The software title associated with the hardware requirement
- **Minimum CPU (MHz)**: The minimum processor speed in megahertz (MHz) required by the software title
- **Minimum RAM (KB)**: The minimum RAM in kilobytes (KB) required by the software title
- **Minimum Disk Space (KB)**: The minimum free hard disk space in KB required by the software title
- **Minimum Disk Size (KB)**: The minimum hard disk size in KB required by the software title
- **Validation State**: The validation state for the hardware requirement

Predefined hardware requirements stored in the asset intelligence catalog are read-only and can't be deleted. Administrative users can add, modify, or delete user-defined hardware requirements for software titles that aren't stored in the asset intelligence catalog.

## Inventoried software titles

To view inventoried software title information in the Configuration Manager console, go to the **Assets and Compliance** workspace, expand the **Asset Intelligence** node, and select the **Inventoried Software** node. The hardware inventory agent collects the inventoried software information from Configuration Manager clients based on the software titles stored in the asset intelligence catalog.

Note

The hardware inventory agent collects inventory based on the asset intelligence hardware inventory reporting classes that you enable. For more information about how to enable the reporting classes, see [Configuring asset intelligence](configuring-asset-intelligence).

By default, the following information is displayed for each inventoried software title:

- **Name**: The name of the inventoried software title
- **Vendor**: The name of the vendor that developed the inventoried software title
- **Version**: The product version of the inventoried software title
- **Category**: The software category that's currently assigned to the inventoried software title
- **Family**: The software family that's currently assigned to the inventoried software title
- **Label** [**1**, **2**, and **3**]: The custom labels associated with the software title. Inventoried software titles can have up to three custom labels associated with them.
- **Count**: The number of Configuration Manager clients that have inventoried the software title
- **State**: The validation state for the inventoried software title

Note

You can change the categorization information for inventoried software only at the top-level site in your hierarchy. This information includes product name, vendor, software category, and software family. After you modify the categorization information for predefined software, the validation state for the software changes from **Validated** to **User Defined**.

## Asset intelligence synchronization point

The asset intelligence synchronization point is a Configuration Manager site system role. It's used to connect to the Microsoft cloud on TCP port 443 to manage dynamic catalog information updates. Install this site role only on the top-level site of the hierarchy. Configure all asset intelligence catalog customization by using a Configuration Manager console connected to the top-level site.

While you configure all updates at the top-level site, catalog information is replicated to other sites in the hierarchy. The site role lets you request on-demand catalog synchronization with Microsoft, or schedule automatic catalog synchronization. In addition to downloading new catalog information, the asset intelligence synchronization point can upload custom software title information to Microsoft for categorization. Microsoft treats all uploaded software titles as public information. Make sure that your custom software titles don't include confidential or proprietary information.

After you submit an uncategorized software title, Microsoft doesn't review it until there are at least four categorization requests from customers for the same software title. Then Microsoft researchers identify, categorize, and make the software title categorization information available to all customers who are using the online service. Software titles that represent the most requests for categorization receive the highest priority to categorize. Custom software and line-of-business applications are unlikely to receive a category. Don't send these software titles to Microsoft for categorization.

An asset intelligence synchronization point is required to connect to the Microsoft cloud. For information about how to install the role, see [Configuring asset intelligence](configuring-asset-intelligence).

## Asset intelligence home page

The **Asset Intelligence** node in the **Assets and Compliance** workspace is the home page for asset intelligence in Configuration Manager.

Starting in version 2609, the **Catalog Synchronization** and **Inventoried Software Status** sections are removed. The home page displays deprecation information and links to the [product lifecycle dashboard](product-lifecycle-dashboard) and [Asset Intelligence client WMI classes](../../../../develop/reference/core/clients/client-classes/asset-intelligence-client-wmi-classes).

### Version 2603 and earlier

In version 2603 and earlier, the home page displays a summary dashboard view for asset intelligence catalog information.

Note

The **Asset Intelligence** home page doesn't automatically update while you're viewing it.

The **Asset Intelligence** home page includes the following sections:

- **Catalog Synchronization**: Information about whether asset intelligence is enabled and the current status of the asset intelligence synchronization point.

    Note

    The home page only displays this section when you install an asset intelligence synchronization point.

    The section also provides the following information:

    - Synchronization schedule
    - If you've imported a customer license statement
    - The last status update
    - The time for the next scheduled update
    - The number of changes after you installed the asset intelligence synchronization point
- **Inventoried Software Status**: The count and percentage of inventoried software, software categories, and software families that are identified by Microsoft, identified by an administrator, pending online identification, or unidentified and not pending. The information displayed in table format shows the count for each, and the information displayed in the chart shows the percentage for each.

## Asset intelligence reports

Important

Starting in version 2609, Asset Intelligence reports are removed from the **Monitoring &gt; Reporting &gt; Reports** node. The report descriptions in this section apply to version 2603 and earlier.

The asset intelligence reports are located in the Configuration Manager console, in the **Monitoring** workspace, in the **Asset intelligence** folder under the **Reporting** node. The reports provide information about hardware, license management, and software. For more information about reports in Configuration Manager, see [Introduction to reporting](../../../servers/manage/introduction-to-reporting).

Note

The accuracy of the quantity of installed software titles and license information displayed in asset intelligence reports might vary from the actual number of software titles installed or licenses that are used in the environment. This variation is because of the complex dependencies and limitations involved in inventorying software license information for software titles that are installed in enterprise environments. Don't use asset intelligence reports as the sole source for determining purchased software license compliance.

### Hardware reports

Asset intelligence hardware reports provide information about hardware assets in the organization. By using hardware inventory information such as speed, memory, and peripheral devices, asset intelligence hardware reports can present information about USB devices, about hardware that must be upgraded, and even about computers that aren't ready for a specific software upgrade.

Note

Some user data in asset intelligence hardware reports is collected from the Windows security event log. For better report accuracy, clear this log when you reassign a computer to a new user.

### License management reports

Asset intelligence license management reports provide data about licenses that are being used. The **License Ledger** report lists installed Microsoft applications in a format congruent with a Microsoft License Statement (MLS). This format provides a convenient method of matching acquired licenses with used licenses. Other license management reports provide information about computers acting as servers that run the key management service (KMS) for Windows activation statistics.

Important

Several of the asset intelligence license management reports present information about the function of KMS, a method of administering volume licensing. If you haven't implemented a KMS server, some reports might not return any data.

### Software reports

Asset intelligence software reports provide information about software families, categories, and specific software titles that are installed on computers in the organization. The software reports present information such as browser helper objects and software that starts automatically. These reports can be used to identify adware, spyware, and other malware. You can also use them to identify software redundancy to help streamline software acquisition and support.

### Software identification tag reports

Asset intelligence software identification tag reports provide information about software that includes a software identification tag compliant with ISO/IEC 19770-2. The software identification tags provide authoritative information used to identify installed software. When you enable the **SMS\_SoftwareTag** hardware inventory reporting class, Configuration Manager collects information about the software with software identification tags.

The following reports provide information about the software:

- **Software 14A - Search for software identification tag enabled software**: The count of installed software with a software identification tag enabled
- **Software 14B - Computers with specific software identification tag enabled software installed**: All computers that have installed software with a specific software identification tag enabled
- **Software 14C - Installed software identification tag enabled software on a specific computer**: All installed software with a specific software identification tag enabled on a specific computer

### Reporting limitations

Asset intelligence reports can provide large amounts of information about installed software titles and acquired software licenses that are being used. Don't use this information as the only source for determining acquired software license compliance.

#### Example dependencies

The accuracy of the quantity displayed in the asset intelligence reports for installed software titles and license information can vary from the actual amounts currently used. This variation is caused by the complex dependencies involved in inventorying software license information for software titles in use in enterprise environments. The following examples show the dependencies involved in inventorying installed software in the enterprise by using asset intelligence that might affect the accuracy of asset intelligence reports:

- **Client hardware inventory dependencies**: Asset intelligence installed software reports are based on data collected from Configuration Manager clients by extending hardware inventory to enable asset intelligence reporting. Because of this dependency on hardware inventory reporting, asset intelligence reports reflect data only from clients that successfully complete hardware inventory processes with the required asset intelligence WMI reporting classes enabled. Because Configuration Manager clients perform hardware inventory processes on a schedule defined by the administrative user, a delay might occur in data reporting that affects the accuracy of asset intelligence reports.

    For example, an inventoried licensed software title might be uninstalled after the client finishes a successful hardware inventory cycle. Asset intelligence reports display the software title as installed until the client's next scheduled hardware inventory reporting cycle.
- **Software packaging dependencies**: Asset intelligence reports are based on installed software title data collected by using standard Configuration Manager client hardware inventory processes. Some software title data might not be collected correctly. Examples that could cause inaccurate asset intelligence reporting:

    - Software installations that don't comply with standard installation processes
    - Software installations that were changed before installation

#### Legal limitations

The information displayed in asset intelligence reports is subject to many limitations. The information displayed in them doesn't represent legal, accounting, or other professional advice. The information provided by asset intelligence reports is for information only. Don't use it as the only source of information for determining software license usage compliance.

The following limitations are examples of using asset intelligence that might affect the accuracy of the reports:

- **Microsoft license usage quantity limitations**:

    - The quantity of acquired Microsoft software licenses is based on information that administrators supply. Closely review it to make sure that the correct number of software licenses is provided.
    - The reported quantity of Microsoft software licenses includes information only about Microsoft software licenses acquired through volume licensing programs. It doesn't reflect information for software licenses acquired through retail, OEM, or other software license sales channels.
    - Software licenses acquired in the last 45 days might not be included in the quantity of Microsoft software licenses reported because of software reseller reporting requirements and schedules.
    - Software license transfers from company mergers or acquisitions might not be reflected in Microsoft software license quantities.
    - Nonstandard terms and conditions in a Microsoft Volume Licensing (MVLS) agreement might affect the number of software licenses reported. They might require additional review by a Microsoft representative.
- **Installed software title quantity limitations**: Configuration Manager clients must successfully complete hardware inventory reporting cycles for the asset intelligence reports to accurately report the quantity of installed software titles. There might be a delay between the installation or uninstallation of a licensed software title after a successful hardware inventory reporting cycle. This action may not be reflected in asset intelligence reports run before the client reports its next scheduled hardware inventory.
- **License reconciliation limitations**: The reconciliation of the quantity of installed software titles to the quantity of acquired software licenses is calculated by using a comparison of the license quantity specified by the administrator and the quantity of installed software titles collected from Configuration Manager client hardware inventories based on the schedule set by the administrator. This comparison doesn't represent a final Microsoft conclusion of the license positions. The actual license position depends on the specific software title license and usage rights granted by the license terms.

## Asset intelligence validation states

Asset intelligence validation states represent the source and current validation status of asset intelligence catalog information. The following table shows possible asset intelligence validation states and administrator actions that can cause them.

| State | Definition | Administrator action | Comment |
| --- | --- | --- | --- |
| **Validated** | Microsoft researchers defined the catalog item | None | Best state |
| **User Defined** | Microsoft researchers haven't defined the catalog item | Customize the local catalog information | This state is displayed in asset intelligence reports |
| **Pending** | Microsoft researchers haven't defined the catalog item, but you submitted the item to Microsoft for categorization | No further action after requesting categorization | Catalog item remains in this state until Microsoft researchers categorize the item, and you synchronize your asset intelligence catalog |
| **Updateable** | A user-defined catalog item has been categorized differently by Microsoft during catalog synchronization. | Use the **Resolve Conflict** action to decide whether to use the new categorization information or the previous user-defined value. For more information about how to resolve conflicts, see [Operations for asset intelligence](operations-for-asset-intelligence). | After you resolve a categorization conflict, the item isn't validated as conflicting again unless later categorization updates introduce new information about the item. |
| **Uncategorized** | Catalog item hasn't been defined by Microsoft researchers, the item hasn't been submitted to Microsoft for categorization, and the administrator hasn't assigned a user-defined categorization value. | Request categorization or customize your local catalog information. For more information, see [Operations for asset intelligence](operations-for-asset-intelligence). | None |

Note

Catalog items that you submit to Microsoft for categorization have a validation state of **Pending** on a central administration site, but continue to be displayed with a validation state of **Uncategorized** on child primary sites.

For examples of when a validation state might transition from one state to another, see [Example validation state transitions for asset intelligence](example-validation-state-transitions-for-asset-intelligence).