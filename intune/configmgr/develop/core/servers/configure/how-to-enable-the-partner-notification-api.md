---
layout: Conceptual
title: Enable the Partner Notification API - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-enable-the-partner-notification-api
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
description: Partner Notification API allows third-party partners to use the Wake on LAN feature to receive a list of computers that need to be awoken based on advertisements for software distribution.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 1d47103c-3aa5-0870-127b-3028c60ca17f
document_version_independent_id: 97714cc7-f58d-402e-c3b1-62c85a7613f3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-enable-the-partner-notification-api.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-enable-the-partner-notification-api
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-enable-the-partner-notification-api.md
cmProducts: []
platformId: 2b6ffa3c-3bb0-7614-f48f-3de9c54bbf4d
---

# Enable the Partner Notification API - Configuration Manager | Microsoft Learn

The Partner Notification API allows third-party partners to use the Wake on LAN feature of Configuration Manager to receive a list of computers that need to be woken up based on advertisements for software distribution.

Before you can enable the Partner Notification API, you must configure Wake on LAN for each primary site for which you want to enable this feature. For more information about configuring Wake on LAN, see [How to configure Wake on LAN](../../../../core/clients/deploy/configure-wake-on-lan).

### To enable the Partner Notification API

1. Set the following registry keys on the computer for each primary site where you want to enable this feature:

    - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\COMPONENTS\SMS_WAKEONLAN_MANAGER\CreatePartnerNotification` Set the value to 1 to enable the Partner Notification API and create a partner notification file. This key is set to 0 by default.
    - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\COMPONENTS\SMS_WAKEONLAN_MANAGER\DeletePartnerNotificationOlderThanDays` Deletes partner notification files older than the indicated number of days. The default value is 3 days.

        The partner notification file is a .csv file that contains a list of computers, by their FQDN, that you can wake with your custom code.
2. Restart the SMS\_EXECUTIVE service on each computer where you updated the registry keys.
3. Create an advertisement by using the [SMS_Advertisement Server WMI Class](../../../reference/core/servers/configure/sms_advertisement-server-wmi-class). Set the `OfferType` value to 0 and the `AdvertFlags` value to 0x00400000. For more information about advertisements, see [How to Create an Advertisement](how-to-create-an-advertisement) and [How to Configure a Software Distribution Mandatory Advertisement for Wake On LAN](how-to-configure-a-mandatory-advertisement-for-wake-on-lan).
4. Use the `AssignedSchedule` and `AssignedScheduleEnabled` properties to set a schedule for your advertisement.

    When the advertisement deadline is met, and Configuration Manager attempts to wake the computers, a partner notification file is generated and stored in the following location: &lt;Configuration Manager Installation Directory&gt;\inboxes\WOLMGR.box\Partners. If the `OfferType` property in the advertisement is not set to 0, Configuration Manager will not try to wake up computers through Wake on LAN, thus notification files are not generated.
5. Use the list of computers in the partner notification file to wake the computers with your custom code.