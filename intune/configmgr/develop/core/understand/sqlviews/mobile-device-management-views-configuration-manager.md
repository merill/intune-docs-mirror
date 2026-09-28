---
layout: Conceptual
title: Mobile device management views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/mobile-device-management-views-configuration-manager
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
description: Information about the mobile device configuration items and configuration packages.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6bf65ab0-09a4-bf05-1ba1-46a8f956aa37
document_version_independent_id: 9463aaa6-fa39-cd92-692f-f9ef860f4d93
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/mobile-device-management-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/mobile-device-management-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/mobile-device-management-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/390894b2-8646-4f7e-b8cd-2209156272a9
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12b23b77-ab37-4318-a036-4f6690586386
platformId: 0a763fea-67de-d033-8b0c-2007edebb632
---

# Mobile device management views - Configuration Manager | Microsoft Learn

Mobile device management views in Configuration Manager contain information about the mobile device configuration items and configuration packages. The mobile device management status views provide client deployment and client health state information, and the mobile device management hardware inventory views contain information about the inventory collected from mobile device.

The following sections provide detailed information about mobile device management views, mobile device management status views, and mobile device management hardware inventory views.

## Mobile device management status views

The mobile device management status views contain information about the mobile device deployment and client health states. For more information about status views, see [Status and alert views in Configuration Manager](status-alert-views-configuration-manager). The status views that contain mobile devices information are described in this section.

### v\_DeviceClientDeploymentState

Lists all Configuration Manager mobile device clients, by device client ID, NetBIOS name, and device ID, and the last device deployment state reported, as well as the assigned site code, device client version, and so on. The view is also listed and described in the [Client deployment views in Configuration Manager](client-deployment-views-configuration-manager) topic. The view can be joined to other views by using the **DeviceClientID**, **DeviceNetBiosName**, and **DeviceDeploymentState** columns. The **DeviceDeploymentState** column contains the state ID for topic type 800. The **DeviceClientID** column contains the same information as the **SMS\_Unique\_Identifier0** column in the **v\_R\_System** view. The Configuration Manager states are listed in the **v\_StateNames** view.

### v\_DeviceClientHealthState

Lists all Configuration Manager mobile device clients, by device client ID, NetBIOS name, and device ID, and the health state of the device, as well as the assigned site code, owner name, and so on. The view is also listed and described in the [Client status views in Configuration Manager](client-status-views-configuration-manager) topic. The view can be joined to other views by using the **DeviceClientID**, **DeviceNetBiosName**, **HealthType**, and **HealthState** columns. The **DeviceClientID** column in this view contains the same information as the **SMS\_Unique\_Identifier0** column in the **v\_R\_System** view. The **HealthType** column in this view contains the same information as the **TopicType** column in the **v\_StateNames** view and the **HealthState** column in this view contains the same information as the **StateID** column in the **v\_StateNames** status view. Client health state messages have a state type from 1000 to 1004. The Configuration Manager states are listed in the **v\_StateNames** view.

### v\_DeviceClientUpdateState

Lists information about client updates applied to the mobile device client. The view can be joined to other views by using the **DeviceClientID**, **DeviceNetBiosName**, and **DeviceDeploymentState** columns. The **DeviceDeploymentState** column contains the state ID for topic type 800. The **DeviceClientID** column contains the same information as the **SMS\_Unique\_Identifier0** column in the **v\_R\_System** view. The Configuration Manager states are listed in the **v\_StateNames** view.

### v\_RBAC\_WinRTSideLoadingKeys

Lists information about the configured sideloading keys for Windows RT including a description, the maximum number of activations allowed, the type of key and more. It is unlikely that this view will be joined to other views.

## Mobile device management views

The mobile device management views contain information about the status of mobile devices in your hierarchy and contain the information described in this section.

### v\_DM\_RetireRecords

Lists information about devices that have been retired from management. The view can be joined with other views by using the **DeviceName** column.

### v\_DM\_WipeRecords

Lists information about devices that have been wiped by Configuration Manager. The view can be joined with other views by using the **DeviceName** column.

## Mobile device management hardware inventory views

The mobile device management hardware inventory views contain information about mobile devices that is retrieved as part of hardware inventory. For more information about hardware inventory views, see [Hardware inventory views in Configuration Manager](hardware-inventory-views-configuration-manager). The hardware inventory views that contain mobile device information are described in this section.

### v\_GS\_DEVICE\_CERTIFICATES

Lists information about the certificates on devices, including the revision ID, issuer, where it is located in the certificate store, the subject, the dates the certificate is valid, and so on. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_COMPUTERSYSTEM

Lists information about the Configuration Manager devices, including the manufacturer, model, phone number, processor, and more. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_DISPLAY

Lists information about the displays found on Configuration Manager devices including the display resolution, number of colors and more. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_MEMORY

Lists information about the memory found on Configuration Manager devices. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_OS\_INFORMATION

Lists information about the operating system found on Configuration Manager devices. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_POWER

Lists information about power settings and the battery on Configuration Manager devices. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_CLIENT

Lists information about the device client on Configuration Manager managed devices. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_CLIENTAGENTVERSION

Lists information about the client version installed on Configuration Manager managed client devices. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_EMAIL

Lists information about the email settings on a device. This includes the email address, domain, synchronization server and more. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_ENCRYPTION

Lists information about the encryption settings on devices including for email, phone memory and external storage devices. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_BLUETOOTH

Lists information about whether Bluetooth is enabled on device clients. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_CAMERA

Lists information about the camera on mobile devices including whether it is enabled. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_EXCHANGE

Lists Microsoft Exchange settings for mobile devices, such as the maximum size of file attachment, when email is sent, synchronization settings and more. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_INFO

Lists general information about mobile devices including the manufacturer and model, the operating system and more. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_INSTALLEDAPPLICATIONS

Lists the name and version of all applications installed on the device. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_IRDA

Lists information about the IRDA (infra-red) port on devices and whether it is enabled. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_MEMORY\_ADDRESS

Lists the memory address ranges found on the device. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_PASSWORD

Lists information about the password settings on mobile devices, such as the maximum incorrect passwords that can be entered before the device is wiped, when the password expires, and more. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_POLICY

Lists information about policies assigned to devices. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_WINDOWSSECURITYPOLICY

Lists information about the Windows Security policy assigned to Windows Mobile devices. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_WLAN

Lists information about network settings on mobile devices, including whether the network is enabled. This view can be joined with other views by using the **ResourceID** column.

## Exchange ActiveSync views

### v\_EAS\_Organization

Lists information about the Exchange Server and the organization that manage mobile devices. It is unlikely that this view will be joined to other views.

### v\_EAS\_Property

Lists information about all devices that are managed by Exchange ActiveSync. This includes the device ID, name, domain, the operating system of the device and more. This view can be joined to other views by using the **DeviceID** column.

### v\_DeviceJailBrokenStatus

Lists, by **ItemKey**, devices and whether they have been jailbroken. It is unlikely that this view will be joined to other views.