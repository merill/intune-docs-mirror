---
layout: Conceptual
title: Updates and Servicing - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/updates
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
description: Learn about the in-console service method called Updates and Servicing that makes it easy to locate and install recommended updates.
ms.date: 2026-10-22T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: f1bc3f2a-edf6-24e0-4f45-86dc75717572
document_version_independent_id: 2789eb96-6e74-71c0-9c57-65be3d7d802c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/updates.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: 8cf6ccca-5d1d-2c98-820d-94311742041e
---

# Updates and Servicing - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager uses an in-console service method called *Updates and Servicing*. This in-console method makes it easy to find and install recommended updates for your Configuration Manager infrastructure. In-console servicing is supplemented by out-of-band updates such as hotfixes. The out-of-band updates are intended for customers who need to resolve issues that might be specific to their environment.

Tip

The terms *upgrade*, *update*, and *install* are used to describe three separate concepts in Configuration Manager. For more information, see [About upgrade, update, and install](../../understand/upgrade-update-install).

## Baseline and update versions

Use the latest baseline version when you install a new site in a new hierarchy.

- After you upgrade to Configuration Manager current branch, don't use baseline versions to stay current. Instead, use [in-console updates](install-in-console-updates) to update to the newest version.
- Periodically, Microsoft releases another baseline version. When you use the latest baseline version to install a new hierarchy, you avoid installing an outdated or unsupported version of Configuration Manager, followed by another update to your infrastructure.

After you install a baseline version, later versions of Configuration Manager are available as in-console updates. Use these updates to update your infrastructure to the latest version of Configuration Manager.

- You install in-console updates to update the version of your top-level site.
- Updates you install at the central administration site (CAS) automatically install at child primary sites. Control this timing by using a service window at the primary site. For more information, see [Service Windows](service-windows).
- Manually update secondary sites to a new update version from within the console.

When you install an update, the update stores installation files for that version on the site server in a folder named **CD.Latest**. For more information about these files, see [The CD.Latest folder](the-cd.latest-folder).

- Use the files in the **CD.Latest** folder during site recovery. Also, when your hierarchy no longer runs a baseline version, use these files to install other sites.
- You can't use installation files from **CD.Latest** to install the first site of a new hierarchy.

### Version details

Some updates for Configuration Manager are available as both an in-console update version for existing infrastructure, and as a new baseline version.

#### Supported versions

The following supported versions^`*`^, of Configuration Manager are currently available as a baseline, an update, or both:

| Version | Availability date | [Support end date](current-branch-versions-supported) | Baseline | In-console update |
| --- | --- | --- | --- | --- |
| [**2609**](../../plan-design/changes/whats-new-version-2609) (5.00.9152.1000) | September 28, 2026 | March 28, 2028 | Yes | Yes |
| [**2603**](../../plan-design/changes/whats-new-in-version-2603) (5.00.9146.1000) | May 5, 2026 | November 5, 2027 | No | Yes |
| [**2509**](../../plan-design/changes/whats-new-in-version-2509) (5.00.9141) | November 12, 2025 | May 12, 2027 | Yes | Yes |

Note

The **Availability date** in this table is when the early update ring was released. Baseline media are available on the VLSC soon after the update is globally available.

##### Note 1: How to get baseline media

The baseline media is available as part of the following releases on the [Volume License Service Center](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx) (VLSC):

- `Microsoft Configmgr (current branch)`
- `System Center Datacenter`
- `System Center Standard`

For example, search the VLSC for `Microsoft Configmgr (current branch)`. Find the baseline media in the list of files, and download it for that release.

Note

The search string might be different on other media sites. For example, on the [Visual Studio Subscriptions Portal](https://my.visualstudio.com/), search for `Microsoft Configuration Manager`.

Note

`*`**Supported Versions in Configuration Manager**: In the context of Configuration Manager, the term `supported` encompasses both *engineering* and *assisted technical support*. While no further engineering development will occur for the versions in question, users won't have access to phone or online assisted technical support for these versions. However, Technical Support will assist with upgrading to a supported version of Configuration Manager. Users will resume their regular assisted technical support once Configuration Manager is upgraded to a supported version.

#### Historical versions

The following table lists historical versions of Configuration Manager current branch that are out of support:

| Version | Availability date | Support end date | Baseline | In-console update |
| --- | --- | --- | --- | --- |
| **2503** (5.00.9135) | March 31, 2025 | September 30, 2026 | No | Yes |
| **2409** (5.00.9132) | December 4, 2024 | June 4, 2026 | No | Yes |
| **2403** (5.00.9128) | April 22, 2024 | October 22, 2025 | Yes | Yes |
| **2309** (5.00.9122) | October 9, 2023 | April 9, 2025 | No | Yes |
| **2303** (5.00.9106) | April 10, 2023 | October 10, 2024 | Yes | Yes |
| **2211** (5.00.9096) | December 5, 2022 | June 5, 2024 | No | Yes |
| **2207** (5.00.9088) | August 12, 2022 | February 12, 2024 | No | Yes |
| **2203** (5.00.9078) | April 6, 2022 | October 6, 2023 | Yes | Yes |
| **2111** (5.00.9068) | December 1, 2021 | June 1, 2023 | No | Yes |
| **2107** (5.00.9058) | August 2, 2021 | February 2, 2023 | No | Yes |
| **2103** (5.00.9049) | April 19, 2021 | October 19, 2022 | Yes | Yes |
| **2010** (5.00.9040) | November 30, 2020 | May 30, 2022 | No | Yes |
| **2006** (5.00.9012) | August 11, 2020 | February 11, 2022 | No | Yes |
| **2002** (5.00.8968) | April 1, 2020 | October 1, 2021 | Yes | Yes |
| **1910** (5.00.8913) | November 29, 2019 | May 29, 2021 | No | Yes |
| **1906** (5.00.8853) | July 26, 2019 | January 26, 2021 | No | Yes |
| **1902** (5.00.8790) | March 27, 2019 | September 27, 2020 | Yes | Yes |
| **1810** (5.00.8740) | November 27, 2018 | December 1, 2020 | No | Yes |
| **1806** (5.00.8692) | July 31, 2018 | January 31, 2020 | No | Yes |
| **1802** (5.00.8634) | March 22, 2018 | September 22, 2019 | Yes | Yes |
| **1710** (5.00.8577) | November 20, 2017 | May 20, 2019 | No | Yes |
| **1706** (5.00.8540) | July 31, 2017 | July 31, 2018 | No | Yes |
| **1702** (5.00.8498) | March 27, 2017 | March 27, 2018 | Yes | Yes |
| **1610** (5.00.8458) | November 18, 2016 | November 18, 2017 | No | Yes |
| **1606 with KB3186654** (5.00.8412.1307) | October 12, 2016 | October 12, 2017 | Yes | No |
| **1606** (5.00.8412.1000) | July 22, 2016 | July 22, 2017 | No | Yes |
| **1602** (5.00.8355) | March 11, 2016 | March 11, 2017 | No | Yes |
| **1511** (5.00.8325) | December 8, 2015 | December 8, 2016 | Yes | No |

#### How to check the version

To check the version of your Configuration Manager site, in the console, go to **About Configuration Manager** at the top-left corner of the console. This dialog displays the site and console versions.

Note

The console version is slightly different from the site version. The minor version of the console corresponds to the Configuration Manager release version. For example, in Configuration Manager version 2303 the initial site version is 5.0.9122.1000, and the initial console version is 5.9122.1082.1700. The build (1082) and revision (1700) numbers might change with future hotfixes.

## In-console updates and servicing

When you use a production-ready installation of Configuration Manager current branch, you can get most updates through the **Updates and Servicing** channel. This method identifies, downloads, and makes available the updates that apply to your current infrastructure version and configuration. It includes only updates that Microsoft recommends for all customers.

These updates include:

- New versions
- Updates that include new features for your current version
- Hotfixes for your version of Configuration Manager that all customers should install

    Note

    In-console hotfixes have supersedence relationships. For more information, see Supersedence for in-console hotfixes.

The in-console updates deliver increased stability and resolve common issues. They replace the update types seen for previous product versions such as service packs, cumulative updates, hotfixes that are applicable to all customers, and the extension for Microsoft Intune.

The in-console updates can apply to one or more of the following systems:

- Primary and CAS servers
- Site system roles and site system servers
- Instances of the SMS Provider
- Configuration Manager consoles
- Configuration Manager clients

Configuration Manager discovers new updates for you. Synchronize your Configuration Manager service connection point with the Microsoft cloud service, noting the following behaviors:

- When your service connection point is in online mode, your site synchronizes with Microsoft every day. It automatically identifies new updates that apply to your infrastructure. To download updates and redistributable files, the computer that hosts the service connection point site system role uses the **System** context to access the following internet locations: `go.microsoft.com` and `download.microsoft.com`. For more information about other locations used by the service connection point, see [Internet access requirements](../../plan-design/network/internet-endpoints#service-connection-point).
- When your service connection point is in offline mode, use the service connection tool to manually sync with the Microsoft cloud. For more information, see [Use the service connection tool](use-the-service-connection-tool).
- In-console updates replace the need to independently locate and install individual updates, service packs, and new features.
- Install only the in-console updates you choose. When installing some updates, you can select individual features to enable and use. For more information, see [Enable optional features from updates](optional-features).

When you install an in-console update, the following process occurs:

- It automatically runs a prerequisite check. You can also manually run this check before you start the installation.
- It installs at the top-level site in your environment. This site is the CAS if there's one. In a hierarchy, the update automatically installs at primary sites. Control when each primary site server is allowed to update by using [Service windows for site servers](service-windows).
- After a site server updates, all affected site system roles automatically update. These roles include instances of the SMS Provider. After the site installs the update, Configuration Manager consoles also prompt the console user to update the console.
- If an update includes the Configuration Manager client, you're offered the option to test the update in pre-production, or to apply the update to all clients immediately.
- After a primary site is updated, secondary sites don't automatically update. Instead, you must manually start the secondary site update.

Note

The Configuration Manager current branch, the long-term servicing branch, and the technical preview branch are different releases. Updates that apply for one branch aren't available as in-console updates for the other branches. For more information about available branches, see [Which branch of Configuration Manager should I use?](../../understand/which-branch-should-i-use)

### Supersedence for in-console hotfixes

In-console hotfixes have supersedence relationships. When Microsoft publishes a new Configuration Manager hotfix, the console doesn't display any hotfixes that this new hotfix supersedes. This new behavior helps you better determine which hotfixes to install.

### Supersedence example

Three hotfixes are available: Hotfix-A, Hotfix-B, and Hotfix-C. Hotfix-A is superseded by Hotfix-B, and Hotfix-B is superseded by Hotfix-C.

| Hotfix-A | Hotfix-B | Hotfix-C | In-console view |
| --- | --- | --- | --- |
| Not installed | Not installed | Not installed | Show all three hotfixes |
| Installed | Installed | Not installed | Hotfix-B shows as installedHotfix-C shows as ready to install |
| Not installed | Not installed | Installed | Hotfix-C shows as installed |

## Out-of-band hotfixes

Some hotfixes release with limited availability to address specific issues. Other hotfixes are applicable to all customers but can't install by using the in-console method. These fixes are delivered out-of-band and aren't discovered from the Microsoft cloud service.

Typically, when you want to fix or address a problem with your deployment of Configuration Manager, you can learn about out-of-band hotfixes from Microsoft customer support services, a Microsoft support knowledge base article, or [the Configuration Manager team blog](https://techcommunity.microsoft.com/t5/Configuration-Manager-Blog/bg-p/ConfigurationManagerBlog).

Use one of the following methods to manually install these fixes:

### Update Registration Tool

This tool manually imports the hotfix into your Configuration Manager console. Then, install the update as you would in-console updates that are discovered automatically.

Use this method for hotfixes that use the following file name structure: `<Product>-<product version>-<KB article ID>-ConfigMgr.Update.exe`

For more information, see [Use the update registration tool to import hotfixes](use-the-update-registration-tool-to-import-hotfixes).

### Hotfix Installer

Use this tool to manually install a hotfix that you can't install by using the in-console method.

Use this method for fixes that use the following file name structure: `<Product>-<product version>-<KB article ID>-<platform>-<language>.exe`

For more information, see [Use the hotfix installer to install updates](use-the-hotfix-installer-to-install-updates).