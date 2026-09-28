---
layout: Conceptual
title: Planning client deployment to Windows Embedded devices - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices
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
description: Plan for client deployment to Windows Embedded devices in Configuration Manager.
ms.date: 2021-10-11T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 5e4547e2-e0f3-bff9-e374-35a7bec8419b
document_version_independent_id: 2dc9e200-e2ad-1605-bf2a-2e2364cd33b0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 5ad4d177-20a8-e4db-0d3a-98d6edba4fe9
---

# Planning client deployment to Windows Embedded devices - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

 If your Windows Embedded device does not include the Configuration Manager client, you can use any of the client installation methods if the device meets the required dependencies. If the embedded device supports write filters, you must disable these filters before you install the client, and then re-enable the filters again after the client is installed and assigned to a site.

Note that when you disable the filters, you should not disable the filter drivers. Typically these drivers are started automatically when the computer is started. Disabling the drivers will either prevent installation of the client, or interfere with write filter orchestration which will cause client operations to fail. These are the services associated with each write filter type that must remain running:

| Write Filter Type | Driver | Type | Description |
| --- | --- | --- | --- |
| EWF | ewf | Kernel | Implements sector-level I/O redirection on protected volumes. |
| FBWF | fbwf | File system | Implements file-level I/O redirection on protected volumes. |
| UWF | uwfreg | Kernel | UWF Registry Redirector |
| UWF | uwfs | File System | UWF File Redirector |
| UWF | uwfvol | Kernel | UWF Volume Manager |

Write filters control how the operating system on the embedded device is updated when you make changes, such as when you install software. When write filters are enabled, instead of making the changes directly to the operating system, these changes are redirected to a temporary overlay. If the changes are only written to the overlay, they are lost when the embedded device shuts downs. However, if the write filters are temporarily disabled, the changes can be made permanent so that you do not have to make the changes again (or reinstall software) every time that the embedded device restarts. However, temporarily disabling and then re-enabling the write filters requires one or more restarts, so that you typically want to control when this happens by configuring maintenance windows so that restarts occur outside business hours.

You can configure options to automatically disable and re-enable the write filters when you deploy software such as applications, task sequences, software updates, and the Endpoint Protection client. The exception is for configuration baselines with configuration items that use automatic remediation. In this scenario, the remediation always occurs in the overlay so that it is available only until the device is restarted. The remediation is applied again at the next evaluation cycle, but only to the overlay, which is cleared at restart. To force Configuration Manager to commit the remediation changes, you can deploy the configuration baseline and then another software deployment that supports committing the change as soon as possible.

If the write filters are disabled, you can install software on Windows Embedded devices by using Software Center. However, if the write filters are enabled, the installation fails and Configuration Manager displays an error message that you have insufficient permissions to install the application.

Warning

Even if you do not select the Configuration Manager options to commit the changes, the changes might be committed if another software installation or change is made that commits changes. In this scenario, the original changes will be committed in addition to the new changes.

When Configuration Manager disables the write filters to make changes permanent, only users who have local administrative rights can log on and use the embedded device. During this period, low-rights users are locked out and see a message that the computer is unavailable because it is being serviced. This helps protect the device while it is in a state where changes can be permanently applied, and this servicing mode lockout behavior is another reason to configure a maintenance window for a time when users will not log on to these devices.

Configuration Manager supports managing the following types of write filters:

- File-Based Write Filter (FBWF) - For more information, see [File-Based Write Filter](/en-us/previous-versions/windows/embedded/aa940926%28v=winembedded.5%29).
- Enhanced Write Filter (EWF) RAM - For more information, see [Enhanced Write Filter](/en-us/previous-versions/windows/embedded/ms912906%28v=winembedded.5%29).
- Unified Write Filter (UWF) - For more information, see [Unified Write Filter](/en-us/windows-hardware/customize/enterprise/unified-write-filter).

    Configuration Manager does not support write filter operations when the Windows Embedded device is in EWF RAM Reg mode.

Important

If you have the choice, use File-Based Write Filters (FBWF) with Configuration Manager for increased efficiency and higher scalability.

**For devices that use FBWF only:** Configure the following exceptions to persist client state and inventory data between device restarts:

- CCMINSTALLDIR\\*.sdf

    - CCMINSTALLDIR\ServiceData
    - HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\CCM\StateSystem

    Devices that run Windows Embedded 8.0 and later do not support exclusions that contain wildcard characters. On these devices, you must configure the following exclusions individually:
- All files in CCMINSTALLDIR with the extension .sdf, typically:

    - UserAffinityStore.sdf
    - InventoryStore.sdf
    - CcmStore.sdf
    - StateMessageStore.sdf
    - CertEnrollmentStore.sdf
    - CCMINSTALLDIR\ServiceData
    - HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\CCM\StateSystem

**For devices that use FBWF and UWF only:** When clients in a workgroup use certificates for authentication to management points, you must also exclude the private key to ensure the client continues to communicate with the management point. On these devices, configure the following exceptions:

- c:\Windows\System32\Microsoft\Protect
    - c:\ProgramData\Microsoft\Crypto
    - HKEY\_LOCAL\_MACHINE\Software\Microsoft\SystemCertificates\SMS\Certificates

Note

No additional exceptions are needed by the Configuration Manager client other than those documented in the above **Important** box. Adding additional Configuration Manager or WMI (WBEM) related exceptions may lead to failures of the Configuration Manager including devices getting stuck in servicing mode or devices experiencing reboot loops. Unneeded exceptions include the Configuration Manager client directory, the CCMcache directory, the CCMSetup directory, the Task Sequence cache directory, the WBEM directory, and Configuration Manager related registry keys.

For an example scenario to deploy and manage write-filter-enabled Windows Embedded devices in Configuration Manager see [Example scenario for deploying and managing Configuration Manager clients on Windows Embedded devices](../example-scenario-for-deploying-and-managing-clients-on-windows-embedded-devices).

For more information about how to build images for Windows Embedded devices and configure write filters, see your Windows Embedded documentation, or contact your OEM.

Note

When you select the applicable platforms for software deployments and configuration items, these display the Windows Embedded families rather than specific versions.