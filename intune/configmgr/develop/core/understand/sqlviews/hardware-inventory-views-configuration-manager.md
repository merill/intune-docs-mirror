---
layout: Conceptual
title: Hardware inventory views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/hardware-inventory-views-configuration-manager
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
description: Information about the computer hardware scanned on Configuration Manager client computers.
ms.date: 2019-06-03T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 931870af-92b6-3bd3-1928-94fe3d0ece9a
document_version_independent_id: bfa95bdb-ed33-d8c3-8ca8-f3ac740abb5d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/hardware-inventory-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/hardware-inventory-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/hardware-inventory-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a06d6f90-31c8-6a62-a34a-6897e9c88c48
---

# Hardware inventory views - Configuration Manager | Microsoft Learn

The hardware inventory views contain information about the computer hardware scanned on Configuration Manager client computers. Many hardware inventory views are created in Configuration Manager by default, and many more can be enabled or creating classes by using the hardware inventory classes dialog box, accessible from client settings. Because of this, it is likely that Configuration Manager sites collect different hardware inventory resulting in different hardware inventory views.

For more information about extending Configuration Manager hardware inventory, see [How to extend hardware inventory in Configuration Manager](../../../../core/clients/manage/inventory/extend-hardware-inventory).

## Hardware inventory schema views

The hardware inventory schema is important to understand when creating queries for Configuration Manager reports. Most of the client data within Configuration Manager is contained in one of the two hardware inventory schema views: **v\_GroupMap** and **v\_GroupAttributeMap**. The **v\_GroupMap** view contains a list of all the hardware inventory groups and the associated view for each of the groups. The **v\_GroupAttributeMap** view contains all of the attributes that are inventoried for each of the groups. Both views can be joined together by using the **GroupID** column and joined to the **v\_ResourceMap** discovery schema view by using the **ResourceType** column.

Because hardware inventory can be extended, one Configuration Manager site's SQL Server database might have different hardware inventory views and schema when compared to another site. The following query joins the **v\_GroupMap** and **v\_GroupAttributeMap** to generate the hardware inventory view schema, based on the specific settings for the site:

```sql
SELECT DISTINCT GM.DisplayName, GM.InvClassName,

  GM.InvHistoryClassName, GAM.AttributeName,

  GAM.ColumnName, GM.MIFClass

FROM v_GroupMap GM INNER JOIN v_GroupAttributeMap GAM

  ON GM.GroupID = GAM.GroupID
```

## Hardware inventory views

Most of the hardware inventory views start with the **v\_GS\_** view name followed by the name of the hardware component, such as CDROM (for example, **v\_GS\_CDROM**). As a general rule, each hardware inventory view has an associated inventory history view that starts with the **v\_HS\_** view name. The hardware inventory views can all be joined with other system data views by using the **ResourceID** column, which is demonstrated in Appendix A, in the topic [Sample queries for hardware inventory in Configuration Manager](sample-queries-hardware-inventory-configuration-manager). The standard hardware inventory views are described in this section.

Note

Not all of the items listed are collected by default when using Configuration Manager hardware inventory. For information about how to enable or disable hardware inventory classes, see the [How to extend hardware inventory in Configuration Manager](../../../../core/clients/manage/inventory/extend-hardware-inventory) topic in the Configuration Manager Documentation Library

### v\_InventoryClass

Lists the WMI classes that are collected by Configuration Manager hardware inventory by class ID. The view also shows the WMI namespace, the class name and the name of the class as it will be displayed in Resource Explorer. This view can be joined to other views by using the **ClassID** column.

### v\_InventoryClassProperty

Lists the properties collected from each inventory class by Configuration Manager hardware inventory. This view is unlikely to be joined to other views.

### v\_InventoryReport

Lists information about the last inventory taken by Configuration Manager. This can include hardware inventory, software inventory, and discovery. This view is unlikely to be joined to other views.

### v\_InventoryReportClass

Lists the inventory classes and properties used by Configuration Manager hardware inventory. This view is unlikely to be joined to other views.

### v\_CustomInventoryReport

Lists details about hardware inventory collected from clients that have custom hardware inventory client settings deployed. This view can be joined to other views by using the **CollectionID** column.

### v\_Add\_Remove\_Programs

Lists information about the software installed on Configuration Manager clients that is registered in Add or Remove Programs or Programs and Features list. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_1394\_CONTROLLER

Lists details about 1394 controllers on clients. This includes the manufacturer, the install date and more. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_ACTIVESYNC\_CONNECTED\_DEVICE

Lists information about devices connected to Configuration Manager clients by using Exchange ActiveSync. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_ACTIVESYNC\_SERVICE

Lists information about the Exchange ActiveSync service on Configuration Manager clients, including the version and last synchronization time. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_ADD\_REMOVE\_PROGRAMS

Lists information about the software installed on Configuration Manager clients that is shown in the list of installed programs in Windows Control Panel. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_ADD\_REMOVE\_PROGRAMS\_64

Lists information about the 64-bit software installed on Configuration Manager client computers that is shown in the list of installed programs in Windows Control Panel. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_ADVANCED\_CLIENT\_SSL\_CONFIGURATIONS

Lists all Configuration Manager clients, by resource ID, and associated Secure Sockets Layer (SSL) information for the resource, if applicable. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_APPV\_CLIENT\_APPLICATION

Lists computers that have the App-V client application installed. The view can be joined with other views by using the **ResourceID** column.

### V\_GS\_APPV\_CLIENT\_PACKAGE

Lists computers that have the App-V client package installed. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_AUTOSTART\_SOFTWARE

Lists information about the applications on Configuration Manager clients that start automatically with the operating system found through Asset Intelligence. The view is also listed and described in the [Asset intelligence views in Configuration Manager](asset-intelligence-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_BASEBOARD

Lists information about the motherboard on Configuration Manager client computers. This includes the serial number of the motherboard, a description and more. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_BATTERY

Returns details about any computer that contains a battery, such as a notebook computer. Includes information about the type of battery, any errors it has reported, when it was installed, and more. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_BOOT\_CONFIGURATION

Lists information about the folders and resources Windows uses to start on client computers, such as the startup folder, the location of Windows, the boot partition and more. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_BROWSER\_HELPER\_OBJECT

Lists information about the browser objects found on Configuration Manager clients through Asset Intelligence. While some browser helper objects are beneficial, malware might be delivered is in the form of browser helper objects. The view is also listed and described in the [Asset intelligence views in Configuration Manager](asset-intelligence-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_CCM\_RECENTLY\_USED\_APPS

Lists information about the applications found on Configuration Manager clients, through software metering, that were recently run. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_CDROM

Lists information about CDROM devices found on Configuration Manager clients. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_COMPUTER\_SYSTEM

Lists information about the Configuration Manager clients, including domain, computer name, Configuration Manager roles, status, system type, and more. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_COMPUTER\_SYSTEM\_PRODUCT

Lists general information about inventoried client devices including the manufacturer and model. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_DESKTOP

Lists information about the desktop settings on client computers including the icon size, wallpaper settings, fonts and more. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DESKTOP\_MONITOR

Lists information about the desktop monitors found on Configuration Manager client computers. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_CERTIFICATES

Lists information about the certificates on devices, including the revision ID, issuer, where it is located in the certificate store, the subject, the dates the certificate is valid, and so on. The view is also listed and described in the [Mobile device management views in Configuration Manager](mobile-device-management-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_COMPUTERSYSTEM

Lists information about the Configuration Manager devices, including the device ID, number of processors, platform type, processor type, and so on. The view is also listed and described in the [Mobile device management views in Configuration Manager](mobile-device-management-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_DISPLAY

Lists information about the displays found on Configuration Manager devices. The view is also listed and described in the [Mobile device management views in Configuration Manager](mobile-device-management-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_MEMORY

Lists information about the memory found on Configuration Manager devices. The view is also listed and described in the [Mobile device management views in Configuration Manager](mobile-device-management-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_OSINFORMATION

Lists information about the operating system found on Configuration Manager devices. The view is also listed and described in the [Mobile device management views in Configuration Manager](mobile-device-management-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DEVICE\_POWER

Lists information about power settings and the battery on Configuration Manager devices. The view is also listed and described in the [Mobile device management views in Configuration Manager](mobile-device-management-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DISK

Lists information about the disk drives found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_DMA\_CHANNEL

Lists information about the Direct Memory Access (DMA) channels found on client computers. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_EMBEDDED\_DEVICE\_INFO

Lists information about Windows Embedded devices, including the model name of the device. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_ENCRYPTABLE\_VOLUME

Lists the encryptable disk volumes found on Windows computers. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_ENVIRONMENT

Lists details about the Windows environment variables found on client computers. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_FOLDER\_REDIRECTION\_HEALTH

Lists information about the status of folder redirection on Windows computers. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_IDE\_CONTROLLER

Lists information about the IDE controllers found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_INSTALLED\_EXECUTABLE

Lists information about the installed executable files (files with the extension .exe) on Configuration Manager clients found through Asset Intelligence. The view is also listed and described in the [Asset intelligence views in Configuration Manager](asset-intelligence-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_INSTALLED\_SOFTWARE

Lists information about the installed software applications on Configuration Manager clients found through Asset Intelligence. The view is also listed and described in the [Asset intelligence views in Configuration Manager](asset-intelligence-views-configuration-manager) topic.

The view can be joined with other views by using the **ResourceID** column and with Asset Intelligence views by using the **SoftwareCode0** and **SoftwarePropertiesHash0** columns.

### v\_GS\_INSTALLED\_SOFTWARE\_CATEGORIZED

Lists information about the installed software applications on Configuration Manager clients found through Asset Intelligence. This view contains the information in the **v\_GS\_INSTALLED\_SOFTWARE** view and joins several other tables to provide additional details about the installed software. The view is also listed and described in the [Asset intelligence views in Configuration Manager](asset-intelligence-views-configuration-manager) topic.

The view can be joined with other views by using the **ResourceID** column and with Asset Intelligence views by using the **SoftwareCode0**, **SoftwarePropertiesHash0**, **FamilyID**, **CategoryID**, and **SoftwareID** columns.

### v\_GS\_INSTALLED\_SOFTWARE\_MS

Lists information about the installed Microsoft software applications on Configuration Manager clients found through Asset Intelligence. The view is also listed and described in the [Asset intelligence views in Configuration Manager](asset-intelligence-views-configuration-manager) topic.

The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_IRQ

List information about Interrupt Requests (IRQ's) found on client computers. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_KEYBOARD\_DEVICE

Lists information about keyboards found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_LOGICAL\_DISK

Lists information about the logical disks found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_MODEM\_DEVICE

Lists information about modems found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_MOTHERBOARD\_DEVICE

Lists information about the motherboard found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_NETWORK\_ADAPTER

Lists information about the network adapters found on Configuration Manager clients, including adapter type, description, MAC address, manufacturer, service name, and so on. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_NETWORK\_ADAPTER\_CONFIGURATION

Lists information about the configuration for network adapters found on Configuration Manager clients, including default IP gateway, whether DHCP is enabled, the DHCP server, DNS domain, IP address, IP subnet, and so on. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_NETWORK\_CLIENT

Lists information about the network clients found on Configuration Manager clients, including description, manufacturer, name, status, and more. The view can be joined with other views by using the **ResourceID** column.

### V\_GS\_NETWORK\_LOGIN\_PROFILE

Lists information about the login profiles found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_NT\_EVENTLOG\_FILE

Lists detailed information about the Windows Event Logs found on client computers. This includes file names, paths, maximum and current sizes, and more.

The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_OPERATING\_SYSTEM

Lists information about the operating system found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### V\_GS\_OS\_RECOVERY\_CONFIGURATION

Lists information about the actions that Windows clients take when they experience an unrecoverable error. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PAGE\_FILE\_SETTING

List information about the paging file on Windows computers. This includes the initial size and the maximum size for the page file. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PARALLEL\_PORT

Lists information about parallel ports found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PARTITION

Lists information about disk partitions found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PC\_BIOS

Lists information about the BIOS found on Configuration Manager clients. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PCMCIA\_CONTROLLER

Lists information about the type, capabilities and status of any PCMCIA controllers inventoried on client computers. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PHYSICAL\_MEMORY

Lists information about the physical memory installed in devices. Includes the capacity, manufacturer, description and more. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PORT

Lists information about the ports on each client computer. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PORTABLE\_BATTERY

Lists information about the battery on portable computers, including its status, type, voltage and expected life. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_POWER\_SUPPLY

Lists information about the power supply used by the Configuration Manager client device. This includes information about remaining charge, reported errors, power management capabilities and more. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_POINTING\_DEVICE

Lists information about the pointing devices connected to Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PNP\_DEVICE\_DRIVER

Lists information about the device drivers found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PRINT\_JOB

Lists, by resource ID, information about jobs that are in the printer queue of client computers. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PRINTER\_CONFIGURATION

Lists information about the configuration of printers attached to a device, including the printer name, whether it has double-sided (duplex) capabilities, its driver version and more. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PRINTER\_DEVICE

Lists information about the print devices attached to clients, including the model, print capabilities and current status at the time the inventory was ran. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PROCESS

Lists information about the Windows processes that were running on client computers at the time they ran hardware inventory. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PROCESSOR

Lists information about the processors found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column and to the **v\_LU\_CPU** asset intelligence view by using the **CPUHash0** column.

### v\_GS\_PROTECTED\_VOLUME\_INFO

Lists information about protected disk volumes found on client computers. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_PROTOCOL

Lists detailed information about the network protocols used by client computers. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_QUICK\_FIX\_ENGINEERING

Lists information about Windows hotfixes installed on client computers. Includes the name of the hotfix, who installed it and when, a description of the hotfix, and more. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_REGISTRY

Lists information about the registry on client computers such as its current size and its maximum size. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_SCSI\_CONTROLLER

Lists information about the SCSI controllers found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SERVER\_FEATURE

Lists the server features that are installed on Windows Server computers. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SERIAL\_PORT

Lists information about the type, capabilities and status of serial ports inventoried on client computers. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SERIAL\_PORT\_CONFIGURATION

Lists information about the serial ports on clients. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_SERVICE

Lists information about the Windows services found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SHARE

Lists information about shared folders found on client computers. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SMS\_ADVANCED\_CLIENT\_STATE

Lists information about the name and version of Configuration Manager client components found on clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SOFTWARE\_LICENSING\_PRODUCT

Lists software licensing product information for Windows Configuration Manager clients found through Asset Intelligence. The view is also listed and described in the [Asset intelligence views in Configuration Manager](asset-intelligence-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SOFTWARE\_LICENSING\_SERVICE

Lists software licensing service information for Windows Configuration Manager clients found through Asset Intelligence. The view is also listed and described in the [Asset intelligence views in Configuration Manager](asset-intelligence-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SOFTWARE\_SHORTCUT

Lists software shortcut information for Configuration Manager clients found through Asset Intelligence. The view is also listed and described in the [Asset intelligence views in Configuration Manager](asset-intelligence-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SOUND\_DEVICE

Lists information about the sound devices found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SYSTEM

Lists information about the active Configuration Manager clients, including domain, name, system role, system type, and more. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SYSTEM\_ACCOUNT

Lists information about the system accounts on Windows computers. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SYSTEM\_CONSOLE\_USAGE

Lists all system console usage information for Configuration Manager clients found through Asset Intelligence by polling the Windows System Security Event Log. The view is also listed and described in the [Asset intelligence views in Configuration Manager](asset-intelligence-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SYSTEM\_CONSOLE\_USAGE\_MAXGROUP

Lists all system console usage information for Configuration Manager clients found through Asset Intelligence by polling the Windows System Security Event Log. This view contains a subset of information from the **v\_GS\_SYSTEM\_CONSOLE\_USAGE** view. The view is also listed and described in the [Asset intelligence views in Configuration Manager](asset-intelligence-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SYSTEM\_CONSOLE\_USER

Lists all system console user information for Configuration Manager clients found through Asset Intelligence by polling the Windows System Security Event Log. The view is also listed and described in the [Asset intelligence views in Configuration Manager](asset-intelligence-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SYSTEM\_DEVICES

Lists information about the system devices found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### V\_GS\_SYSTEM\_DRIVER

Lists information about the drivers found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SYSTEM\_ENCLOSURE

Lists information about the system enclosure found on Configuration Manager clients, including chassis types, serial number, SMBIOS asset tag, and so on. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SYSTEM\_ENCLOSURE\_UNIQUE

Lists information about the unique system enclosures found on Configuration Manager clients, including serial number, SMBIOS asset tag, and so on. This view contains a subset of information from the **v\_GS\_SYSTEM\_ENCLOSURE** view. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SYSTEMBOOTDATA

Lists information about the computer boot times. This includes BIOS duration, boot duration, event log start, group policy duration, system start time and update duration.

The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_TAPE\_DRIVE

Lists information about the tape drives found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_TIME\_ZONE

Lists information about the time zone settings on clients. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_TPM

Lists information about the Trusted Platform Model (TPM) chip when it is found on client computers. This view can be joined with other views by using the **ResourceID** column.

### v\_GS\_TS\_ISSUED\_LICENSE

Lists information about issued Terminal Services licenses. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_TS\_LICENSE\_KEY\_PACK

Lists information about Terminal Services key packs found on client computers. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_USB\_CONTROLLER

Lists information about the USB controllers found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_USB\_DEVICE

Lists information about the USB devices found on Configuration Manager clients through Asset Intelligence. The view is also listed and described in the [Asset intelligence views in Configuration Manager](asset-intelligence-views-configuration-manager) topic. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_USER\_PROFILE

Lists information about user profiles found on client computers including the path to the profile, roaming preferences and more. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_VIDEO\_CONTROLLER

Lists information about the video controllers found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_VIRTUAL\_APPLICATION\_PACKAGES

Lists virtual application package information found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_VIRTUAL\_APPLICATIONS

Lists information about virtual applications found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_VIRTUAL\_MACHINE

Lists information about the virtual machines found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### V\_GS\_WEBAPP\_APPLICATION

Lists information about Web applications found on clients. This includes the name and URL to the application. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_WINDOWS8\_APPLICATION

Lists the installed modern Windows applications found on client computers. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_WINDOWS8\_APPLICATION\_USER\_INFO

Lists user account information for the modern Windows applications found on client computers. This view can be joined to other views by using the **ResourceID** column.

### v\_GS\_WINDOWSUPDATEAGENTVERSION

Lists information about the Windows Update Agent found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_WORKSTATION\_STATUS

Lists workstation status information for Configuration Manager clients, including last hardware scan, default locale ID, time zone offset, and so on. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_WRITE\_FILTER\_STATE

Lists information about whether the write filter is enabled on Windows Embedded devices. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_X86\_PC\_MEMORY

Lists information about the memory found on Configuration Manager clients. The view can be joined with other views by using the **ResourceID** column.

### v\_Network\_DATA\_Serialized

Lists information about the network item found on Configuration Manager clients, and organized by **ResourceID** and then by **GroupID**. The **GroupID** column starts at 1 for the first network item for a client and increments by 1 for each additional network item. The view lists the IP address for the default gateway, the IP address for the DHCP server, DNS domain, IP address, MAC address, and so on. The view can be joined with other views by using the **ResourceID** column.

### v\_SystemInventoryChanges

Lists information about the inventory changes on Configuration Manager clients, including name, MIF class, time stamp, change type, and more. The view can be joined with other views by using the **ResourceID** column.