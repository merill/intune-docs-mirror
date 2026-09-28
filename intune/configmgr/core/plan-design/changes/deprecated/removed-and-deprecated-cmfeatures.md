---
layout: Conceptual
title: Deprecated features - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures
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
description: Learn about the features that Configuration Manager no longer supports.
ms.subservice: core-infra
ms.topic: article
ms.date: 2024-12-04T00:00:00.0000000Z
ms.collection: tier3
locale: en-us
document_id: 02d90277-801f-f70c-63e5-2e295c99fe47
document_version_independent_id: c1f01406-2d58-c491-74a4-33ee30b3d316
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://authoring-docs-microsoft.poolparty.biz/devrel/6ab06385-661e-4214-8870-bbe4071c960d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://authoring-docs-microsoft.poolparty.biz/devrel/131ba09e-4280-4ae7-8622-1f9f1c0daad1
platformId: 3656e636-9d35-478e-5ce9-d14da45267b2
---

# Deprecated features - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article lists the features that are deprecated or removed from support for Configuration Manager. Deprecated features will be removed in a future update. These future changes might affect your use of Configuration Manager.

This information is subject to change with future releases. It might not include each deprecated Configuration Manager feature.

## Deprecated features

The following features are deprecated. You can still use them now, but Microsoft plans to end support in the future.

| Feature | Deprecation first announced | Planned end of support |
| --- | --- | --- |
| **Microsoft Connected Cache (MCC)** integration in Configuration Manager will be deprecated in a future release of Configuration Manager. After deprecation, no further feature development or updates will be provided for Microsoft Connected Cache within Configuration Manager. Customers should begin transitioning to the standalone version of Microsoft Connected Cache to continue receiving ongoing improvements and support. For more information, see [Microsoft Connected Cache](/en-us/windows/deployment/do/waas-microsoft-connected-cache). | June 2026 | TBD |
| The **MDT Integration with CM and Standalone** is no longer supported with Configuration Manager. Customers should remove MDT TS steps, followed by removing MDT integration, to avoid TS corruption and modification failures. More information on the MDT retirement [here](/en-us/troubleshoot/mem/configmgr/mdt/mdt-retirement). | Dec 2024 | The first release after Oct 10, 2025 |
| **Office 365 Client Management dashboard add-in support statement**. For more information, see [Office 365 Client Management dashboard](../../../../sum/deploy-use/office-365-dashboard). | April 2024 | The first release after April 1, 2025 |
| Windows Information Protection | July 2022 | TBD |
| The site system roles for on-premises MDM and macOS clients: **enrollment proxy point and enrollment point**. | January 2022 | Mar 31, 2024 |
| The **Microsoft Store for Business and Education**. For more information, see [Manage apps from the Microsoft Store for Business and Education with Configuration Manager](../../../../apps/deploy-use/manage-apps-from-the-windows-store-for-business). | November 2021 | The first release after March 1, 2023 |
| **Asset intelligence**. For more information, see [Asset intelligence deprecation](../../../clients/manage/asset-intelligence/deprecation). | November 2021 | The first release after November 1, 2022 |
| **On-premises MDM**. For more information, see [On-premises MDM in Configuration Manager](../../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure). | November 2021 | The first release after November 1, 2022 |
| Azure Active Directory (Azure AD) Graph API and Azure AD Authentication Library (ADAL), which is used by Configuration Manager for some cloud-attached scenarios. If you use cloud-attached features such as co-management, tenant attach, or Microsoft Entra discovery, starting June 30, 2022, these features may not work correctly in Configuration Manager version 2107 or earlier. Stay current with Configuration Manager to make sure these features continue to work. For more information, see [CMG FAQ](../../../clients/manage/cmg/cloud-management-gateway-faq#do-i-need-to-do-anything-with-the-deprecation-of-the-azure-ad-graph-api-and-azure-ad-authentication-library--adal--). | July 2021 | June 30, 2022 |
| The BitLocker management implementation for the [recovery service](../../../../protect/deploy-use/bitlocker/recovery-service) has changed. The legacy MBAM-based service is replaced by the messaging processing engine on the management point. | March 2021 | The first release after Mar 2025 |
| Older style of console extensions that haven't been approved in the **Console Extension** node, will no longer be supported. For more information about new console extensions, see [Manage console extensions](../../../servers/manage/admin-console-extensions). | April 2021 | TBD^Note 1^ |
| The implementation for sharing content from Azure has changed. Use a content-enabled cloud management gateway. Starting in version 2107, you can't create a traditional cloud distribution point. | February 2019 | The first release after October 5, 2022 |
| Cloud management gateway and cloud distribution point deployments with Azure Service Manager using a management certificate. For more information, see [Plan for CMG](../../../clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager). | November 2018 | The first release after October 5, 2022 |

### Note 1: Support removed TBD

The specific timeframe is to be determined (TBD). Microsoft recommends that you change to the new process or feature, but you can continue to use the deprecated process or feature for the near future.

## Unsupported and removed features

The following features are no longer supported. In some cases, they're no longer in the product.

| Feature | Deprecation first announced | Support removed |
| --- | --- | --- |
| [System Center Update Publisher (SCUP) and integration with ConfigMgr](../../../../sum/tools/updates-publisher) | October 2023 | Jan 31, 2024 |
| Sites that allow HTTP client communication. Configure the site for HTTPS or Enhanced HTTP. For more information, see [Enable the site for HTTPS-only or enhanced HTTP](../../../servers/deploy/install/list-of-prerequisite-checks#enable-site-system-roles-for-https-or-enhanced-http). | March 2021 | The first release after April 1, 2024 |
| Upgrade from any version of System Center 2012 Configuration Manager to current branch. For more information, see [Upgrade to Configuration Manager current branch](../../../servers/deploy/install/upgrade-to-configuration-manager) | April 2022 | Version 2303 |
| The Configuration Manager client for **macOS** and Mac client management. For more information, see [Supported clients: Mac computers](../../configs/supported-operating-systems-for-clients-and-devices#mac-computers). Migrate management of macOS devices to Microsoft Intune. For more information, see [Deployment guide: Manage macOS devices in Microsoft Intune](../../../../../fundamentals/platform-guide-macos). | January 2022 | December 31, 2022 |
| [Community hub service and integration with ConfigMgr](../../../servers/manage/community-hub) | October 2022 | The first release after March 1, 2023 |
| The geographical view in the **Site Hierarchy** node of the **Monitoring** workspace in the Configuration Manager console. | August 2020 | The first release after September 2023 |
| **Desktop Analytics**. For more information, see [Windows compatibility reports in Intune](https://go.microsoft.com/fwlink/?linkid=2212414). | November 2021 | November 30, 2022 |
| The ability to deploy a cloud management gateway (CMG) as a **cloud service (classic)**. All CMG deployments should use a [virtual machine scale set](../../../clients/manage/cmg/plan-cloud-management-gateway#virtual-machine-scale-sets). | September 2021 | Version 2203 |
| Cloud management gateway (CMG) as a **cloud service (classic)**. All CMG deployments should use a [virtual machine scale set](../../../clients/manage/cmg/plan-cloud-management-gateway#virtual-machine-scale-sets). |  | Version 2403 |
| The following compliance settings for **Company resource access**: [Certificate profiles](../../../../protect/deploy-use/introduction-to-certificate-profiles), [VPN profiles](../../../../protect/deploy-use/vpn-profiles), [Wi-Fi profiles](../../../../protect/deploy-use/create-wifi-profiles), [Windows Hello for Business settings](../../../../protect/deploy-use/windows-hello-for-business-settings), and email profiles. This deprecation includes the [co-management resource access workload](../../../../comanage/workloads#resource-access-policies). Use Microsoft Intune to [deploy resource access profiles](../../../../../device-configuration/overview). For more information, see [Frequently asked questions about resource access deprecation](../../../../protect/plan-design/resource-access-deprecation-faq). | March 2021 | Version 2203 |
| Desktop Analytics data for Windows 7, Windows 8, and earlier versions of Windows 10 that don't support the [Windows diagnostic data processor configuration](../../../../../device-updates/windows/monitor-compatibility). | July 2021 | January 31, 2022 |
| Third-party add-ons that use Microsoft .NET Framework version 4.6.1 or earlier, and rely on Configuration Manager libraries. Such add-ons need to use .NET 4.6.2 or later. For more information, see [External dependencies require .NET 4.6.2](../../../get-started/2021/technical-preview-2109#bkmk_dotnetsdk). | September 2021 | Version 2111 |
| [Log Analytics connector for Azure Monitor.](/en-us/azure/azure-monitor/platform/collect-sccm?context=%2fmem%2fconfigmgr%2fcore%2fcontext%2fcore-context) This feature is called the *OMS Connector* in the Azure Services node. | November 2020 | Version 2107 |
| Microsoft Edge legacy [browser profiles](../../../../compliance/deploy-use/browser-profiles). For more information, see [New Microsoft Edge to replace Microsoft Edge Legacy with April's Windows 10 Update Tuesday release](https://techcommunity.microsoft.com/t5/microsoft-365-blog/new-microsoft-edge-to-replace-microsoft-edge-legacy-with-april-s/ba-p/2114224) | March 2021 | April 2021 |
| The [collection evaluation viewer](../../../support/ceviewer), which was integrated in version 2010. | November 2020 | Version 2103 |
| Desktop Analytics tile and page for **Security Updates** | December 2020 | March 2021 |
| Desktop Analytics option to **View recent data** for device enrollment and security updates. For more information, see [Data latency](../../../../../device-updates/windows/monitor-compatibility). | May 2020 | July 2020 |
| Windows Analytics and Upgrade Readiness integration. For more information, see [KB 4521815: Windows Analytics retirement on January 31, 2020](https://support.microsoft.com/help/4521815/windows-analytics-retirement). | October 14, 2019 | January 31, 2020 |
| Device health attestation assessment for Conditional Access compliance policies  For more information, see [What happened to hybrid MDM](../../../../mdm/understand/what-happened-to-hybrid). | July 3, 2019 | Version 1910 |
| The Configuration Manager Company Portal app | May 21, 2019 | Version 1910 |
| The application catalog, including both site system roles: the application catalog website point and web service point. For more information, see [Remove the application catalog](../../../../apps/plan-design/plan-for-and-configure-application-management#remove-the-application-catalog). | May 21, 2019 | Version 1910 |
| Certificate-based authentication with Windows Hello for Business settings in Configuration ManagerFor more information, see [Windows Hello for Business settings](../../../../protect/deploy-use/windows-hello-for-business-settings). | December 2017 | Version 1910 |
| System Center Endpoint Protection for Mac and LinuxFor more information, see [End of support blog post](https://techcommunity.microsoft.com/t5/configuration-manager-blog/end-of-support-for-scep-for-mac-and-scep-for-linux-on-december/ba-p/286257). | October 2018 | December 31, 2018 |
| On-premises Conditional AccessFor more information, see [What happened to hybrid MDM](../../../../mdm/understand/what-happened-to-hybrid). | January 30, 2019 | September 1, 2019 |
| Hybrid mobile device management (MDM)For more information, see [What happened to hybrid MDM](../../../../mdm/understand/what-happened-to-hybrid).Starting with the 1902 Intune service release, expected at the end of February 2019, new customers can't create a new hybrid connection. | August 14, 2018 | September 1, 2019 |
| Security Content Automation Protocol (SCAP) extensions. | September 2018 | Version 1810 |
| The **Silverlight user experience** for the application catalog website point is no longer supported. Users should use the new Software Center. For more information, see [Configure Software Center](../../../../apps/plan-design/plan-for-software-center#configure-software-center). | August 11, 2017 | Version 1806 |
| The previous version of Software Center.For more information about the new Software Center, see [Plan for and configure application management](../../../../apps/plan-design/plan-for-software-center). | December 13, 2016 | Version 1802 |
| Management of Virtual Hard Disks (VHDs) with Configuration Manager. This deprecation includes removal of options to create a new VHD or manage a VHD using a task sequence, and the removal of the Virtual Hard Disks node from the Configuration Manager console. Existing VHDs are not deleted, but are no longer accessible from within the Configuration Manager console. | January 6, 2017 | Version 1710 |
| Task sequences:  - Convert Disk to Dynamic  - Install Deployment Tools | November 18, 2016 | Version 1710 |
| Upgrade Assessment ToolThe Upgrade Assessment Tool depends on both Configuration Manager and the Application Compatibility Toolkit (ACT) 6.x. The final version of ACT was shipped in the Windows 10 v1511 ADK. As there are no further updates to ACT, support for the Upgrade Assessment Tool is discontinued. Deprecation notice was added to the [download page for UAT](https://www.microsoft.com/software-download/windows10) on September 12, 2016. | September 12, 2016 | July 11, 2017 |
| Software update points with a network load balancing (NLB) cluster | February 27, 2016 | Version 1702 |
| Task sequences:  - OSDPreserveDriveLetter  During an operating system deployment, by default, Windows Setup now determines the best drive letter to use (typically C:). If you want to specify a different drive to use, you can change the location in the Apply Operating System task sequence step. Go to the **Select the location where you want to apply this operating system** setting. Select **Specific logical drive letter** and choose the drive that you want to use. | June 20, 2016 | Version 1606 |
| Network Access Protection (NAP) - as found in System Center 2012 Configuration Manager | July 10, 2015 | Version 1511 |
| Out of Band Management - as found in System Center 2012 Configuration Manager | October 16, 2015 | Version 1511 |
| System Center Configuration Manager Management Pack - for System Center Operations Manager is not available for download | October 16, 2015 | Version 1511 |

### WINS

Windows Internet Name Service (WINS) is a legacy computer name registration and resolution service. It's a deprecated service. You should replace WINS with Domain Name System (DNS). For more information, see [Windows Internet Name Service (WINS)](/en-us/windows-server/networking/technologies/wins/wins-top).

### Out of Band Management

With Configuration Manager, native support for AMT-based computers from within the Configuration Manager console has been removed.

- AMT-based computers remain fully managed when you use the [Intel SCS Add-on for Configuration Manager](https://www.intel.com/content/www/us/en/software/setup-configuration-software.html). The add-on provides you access to the latest capabilities to manage AMT, while removing limitations introduced until Configuration Manager could incorporate those changes.
- Out of Band Management in System Center 2012 Configuration Manager is not affected by this change.

### Network Access Protection

Configuration Manager has removed support for Network Access Protection. The feature has been deprecated in Windows Server 2012 R2, and is removed from Windows 10.

For network access protection alternatives, see the *Deprecated functionality* section of [Network Policy and Access Services Overview](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831683%28v=ws.11%29).