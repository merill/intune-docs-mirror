---
layout: Conceptual
title: Asset Intelligence Prerequisites - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/prerequisites-for-asset-intelligence
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
description: Get the prerequisites for Asset Intelligence in Configuration Manager.
ms.date: 2017-02-22T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 902a0ff8-df99-8a46-909d-9dde56638432
document_version_independent_id: bcaf3182-a841-faa5-f3e5-b0e938e8d434
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/asset-intelligence/prerequisites-for-asset-intelligence.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/asset-intelligence/prerequisites-for-asset-intelligence
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/asset-intelligence/prerequisites-for-asset-intelligence.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/691e3042-55ad-4ce1-b5e9-649b1cc47b5c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b7d11190-096c-4ddb-87db-63764f603aac
platformId: 47b5ff93-4477-5d87-8703-614f7b5e8826
---

# Asset Intelligence Prerequisites - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Asset Intelligence in Configuration Manager has external dependencies and dependencies within the product.

## Dependencies external to Configuration Manager

The following table provides the dependencies for Asset Intelligence that are external to Configuration Manager.

| Dependency | More Information |
| --- | --- |
| Auditing of Success Logon Events Prerequisites | Four Asset Intelligence reports display information gathered from the Windows Security event logs on client computers. If the Security event log settings are not configured to log all Success logon events, these reports contain no data even if the appropriate hardware inventory reporting class is enabled. The following Asset Intelligence reports depend on collected Windows Security event log information: - Hardware 03A - Primary Computer Users- Hardware 03B - Computers for a Specific Primary Console User- Hardware 04A - Shared (Multi-user) Computers- Hardware 05A - Console Users on a Specific Computer To enable the Hardware Inventory Client Agent to inventory the information required to support these reports, you must first modify the Windows Security event log settings on clients to log all Success logon events, and enable the **SMS\_SystemConsoleUser** hardware inventory reporting class. For more information about modifying Security event log settings to log all Success logon events, see [Enable auditing of success logon events](configuring-asset-intelligence#BKMK_EnableSuccessLogonEvents). |

Note

The **SMS\_SystemConsoleUser** hardware inventory reporting class retains successful logon event data for only the previous 90 days of the Security event log, regardless of the length of the log. If the Security event log has fewer than 90 days of data, the entire log is read.

## Dependencies Internal to Configuration Manager

The following table provides the dependencies for Asset Intelligence that are internal to Configuration Manager.

| Dependency | More Information |
| --- | --- |
| Client Agent Prerequisites | The Asset Intelligence reports depend on client information that is obtained through client hardware and software inventory reports. To obtain the information necessary for all Asset Intelligence reports, the following client agents must be enabled: - Hardware Inventory Client Agent- Software Metering Client Agent |
| Hardware Inventory Client Agent Dependencies | To collect inventory data required for some Asset Intelligence reports, the Hardware Inventory Client Agent must be enabled. In addition, some hardware inventory reporting classes that Asset Intelligence reports depend on must be enabled on primary site server computers. For information about enabling the Hardware Inventory Client Agent, see [How to extend hardware inventory](../inventory/extend-hardware-inventory). |
| Software Metering Client Agent Dependencies | A number of Asset Intelligence software reports depend on the Software Metering Client Agent for data. For information about enabling the Software Metering Client Agent, see [Monitor app usage with software metering](../../../../apps/deploy-use/monitor-app-usage-with-software-metering). The following Asset Intelligence reports depend on the Software Metering Client Agent to provide data: - Software 07A - Recently Used Executables by Number of Computers- Software 07B - Computers that Recently Used a Specified Executable- Software 07C - Recently Used Executables on a Specific Computer- Software 08A - Recently Used Executables by Number of Users- Software 08B - Users that Recently Used a Specified Executable- Software 08C - Recently Used Executables by a Specified User |
| Asset Intelligence Hardware Inventory Reporting Class Prerequisites | Asset Intelligence reports in Configuration Manager depend on specific hardware inventory reporting classes. Until the hardware inventory reporting classes are enabled and clients have reported hardware inventory based on these classes, the associated Asset Intelligence reports do not contain any data. You can enable the following hardware inventory reporting classes to support Asset Intelligence reporting requirements: - SMS\_SystemConsoleUsage^1^- SMS\_SystemConsoleUser^1^- SMS\_InstalledSoftware- SMS\_AutoStartSoftware- SMS\_BrowserHelperObject- Win32\_USBDevice- SMS\_InstalledExecutable- SMS\_SoftwareShortcut- SoftwareLicensingService- SoftwareLicensingProduct- SMS\_SoftwareTag^1^ By default, the **SMS\_SystemConsoleUsage** and **SMS\_SystemConsoleUser** Asset Intelligence hardware inventory reporting classes are enabled. You can edit the Asset Intelligence hardware inventory reporting classes in the Configuration Manager console, in the **Assets and Compliance** workspace, when you click the **Asset Intelligence** node. For more information, see the [Enable Asset Intelligence hardware inventory reporting classes](configuring-asset-intelligence#BKMK_EnableAssetIntelligence) section in the [Configuring Asset Intelligence](configuring-asset-intelligence) topic. |
| Reporting services point | The reporting services point site system role must be installed before software updates reports can be displayed. For more information about creating a reporting services point, see [Configuring reporting](../../../servers/manage/configuring-reporting). |