---
layout: Conceptual
title: Site Configuration Server WMI Classes - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes
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
description: The site configuration server WMI classes in Configuration Manager relate to an installation that consists of one or more computers running the Configuration Manager components.
ms.date: 2017-03-13T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: efb926db-adc6-1fc9-23f0-8eb7a9b21388
document_version_independent_id: 3ff43894-5a76-4680-b2b8-bdb831615fdc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes.md
cmProducts: []
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/81a11282-2f1c-4a63-95c5-6e6f262fea55
platformId: 53b50c4f-5211-e500-572e-207e2d6aaf01
---

# Site Configuration Server WMI Classes - Configuration Manager | Microsoft Learn

This section contains detailed reference information about the site configuration server WMI classes in Configuration Manager. These classes include classes that relate to an installation of Configuration Manager that consists of one or more computers running the Configuration Manager components.

You can configure the components of a site at any time to enhance the management of your site. Configuration information is contained in the install map and the site control file.

When you install Configuration Manager, it creates an install map that describes the initial configuration of the installed features for the server, client, and Configuration Manager console. The install map configuration data is read-only and uses the following classes:

- [SMS_SiteInstallMap Server WMI Class](sms_siteinstallmap-server-wmi-class)
- [SMS_SiteInstallItemBase Server WMI Class](sms_siteinstallitembase-server-wmi-class)
- [SMS_SiteInstallItem Server WMI Class](sms_siteinstallitem-server-wmi-class)
- [SMS_SystemResourceList Server WMI Class](sms_systemresourcelist-server-wmi-class)

Classes that are derived from `SMS_SiteInstallItem` use the naming convention `SMS_SII_*`**.** Classes that are derived from `SMS_SiteInstallItemBase` use the naming convention `SMS_SIIB_*`.

The site control file describes the current configuration of the site and its components. Use the following classes to manage the site control file and the site configuration data:

- [SMS_SiteControlFile Server WMI Class](sms_sitecontrolfile-server-wmi-class)
- [SMS_SiteControlItem Server WMI Class](sms_sitecontrolitem-server-wmi-class)

Classes that are derived from `SMS_SiteControlItem` use the naming convention `SMS_SCI_*`. Use these classes to access and modify the configuration items that are contained in the site control file. For information about managing the site control file and changing component configuration, see [About the site control file](../../../../core/understand/about-the-configuration-manager-site-control-file).