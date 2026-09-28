---
layout: Conceptual
title: Client health checks - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/client-health-checks
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
description: The checks that the Configuration Manager client runs regularly to keep healthy.
ms.date: 2022-04-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 159f77be-348d-9b30-0294-6c6ab0de9f26
document_version_independent_id: 159f77be-348d-9b30-0294-6c6ab0de9f26
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/client-health-checks.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/client-health-checks
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/client-health-checks.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9e68b910-f08e-7551-2ecd-8d7c339eed62
---

# Client health checks - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Configuration Manager client regularly runs the checks and remediations to keep healthy. For more information, see [How to monitor clients](monitor-clients).

## Client checks

### Verify that the client was installed correctly

If the client isn't correctly installed, start by troubleshooting client install. Review the ccmsetup.log. Often, remediation requires that you reinstall the client.

### Verify that client prerequisites are installed

Verify that the [client prerequisites](../deploy/prerequisites-for-deploying-clients-to-windows-computers) are installed. It reads the file ccmsetup.xml in the client installation folder to discover the prerequisites. By default: `C:\Windows\ccmsetup\ccmsetup.xml`

Most client prerequisites are available by default in Windows, or installed automatically by the Configuration Manager client. To remediate problems with prerequisites, you can try to install them manually, or reinstall the client.

### Verify that there is sufficient disk space

Verify that there is greater that 1% disk space remaining on C drive.

### Verify the client service

There are three checks for the **SMS Agent Host** client service (`CcmExec`):

- First, it verifies that the service exists. If it doesn't exist, you need to reinstall the client.
- Next, it verifies that the service startup type is automatic. To remediate a failure with this check, reset the service startup type to automatic. Check group policies to make sure something isn't automatically configuring the service startup type.
- Then it verifies that the client service is running. The remediation for this check is to start the client service. Then monitor it to make sure it keeps running. Review Windows event logs to see if there are any related activities that might be stopping the service. Review client logs to make sure it's not failing to start.

### Verify that client check has recently run

Verify that the client check scheduled task (`CcmEval`) has run at least one time in the past three days. You can manually run the scheduled task. Make sure that Windows can run scheduled tasks.

### Verify that the client database is healthy

The client uses a built-in version of SQL Server Compact Edition (CE) to locally store information. If this check fails, reinstall the Configuration Manager client to remediate.

### Verify WMI

There are several checks specific to WMI. The first three checks are for the **Windows Management Instrumentation** (WMI) service (`Winmgmt`).

- Verify that the service exists. WMI is a fundamental component of Windows. If this service doesn't exist, you may need to reinstall Windows.
- Verify that the service startup type is automatic. To remediate a failure with this check, reset the service startup type to automatic. Check group policies to make sure something isn't automatically configuring the service startup type.
- Verify that the service is running. The remediation for this check is to start the WMI service. Then monitor it to make sure it keeps running. Review Windows event logs to see if there are any related activities that might be stopping the service.

There are two other checks to test the overall health of WMI on the device:

- The WMI repository integrity test checks that Configuration Manager client entries exist in WMI. If this check fails, reinstall the Configuration Manager client.
- The WMI event sink test checks whether the Configuration Manager-related WMI event sink is lost. If this check fails, restart the client service.

### Verify the antimalware service

There are two checks for whatever antimalware service is registered with Windows:

- Verify that the antimalware service startup type is automatic. To remediate a failure with this check, reset the service startup type to automatic. Check group policies to make sure something isn't automatically configuring the service startup type.
- Verify that the antimalware service is running. The remediation for this check is to start the antimalware service. Then monitor it to make sure it keeps running. Review Windows event logs to see if there are any related activities that might be stopping the service.

If you're using Windows Defender, the Configuration Manager client also verifies the **Windows Defender Antivirus Network Inspection Service** (`WdNisSvc`). It checks to make sure the service startup type is manual.

### Verify Windows Update service

This check verifies that the **Windows Update** service (`wuauserv`) startup type is automatic or manual. To remediate a failure with this check, reset the service startup type to automatic. Check group policies to make sure something isn't automatically configuring the service startup type.

### Verify the policy platform

There are three checks for the **Microsoft Policy Platform** service (`lppsvc`):

- Verify that the service exists. The policy platform is one of the [prerequisite components that the Configuration Manager client automatically installs](../deploy/prerequisites-for-deploying-clients-to-windows-computers#components-automatically-downloaded-during-installation). If this service doesn't exist, reinstall the Configuration Manager client.
- Verify that the service startup type is manual. To remediate a failure with this check, reset the service startup type to manual. Check group policies to make sure something isn't automatically configuring the service startup type.
- Policy platform WMI integrity test. Repair the policy platform.

### Verify BITS service

There are two checks for the **Background Intelligent Transfer Service** (`BITS`):

- Verify that the service exists. BITS is a fundamental component of Windows. If this service doesn't exist, you may need to reinstall Windows.
- Verify that the service startup type is automatic or manual. To remediate a failure with this check, reset the service startup type to automatic. Check group policies to make sure something isn't automatically configuring the service startup type.

### Verify remote control

If you enable the [remote control agent in client settings](../deploy/about-client-settings#remote-tools), there are two checks for the **Configuration Manager Remote Control** service (`CmRcService`):

- Verify that the service type is automatic or manual. To remediate a failure with this check, reset the service startup type to automatic. Check group policies to make sure something isn't automatically configuring the service startup type.
- Verify that the service is running. The remediation for this check is to start the remote control service. Then monitor it to make sure it keeps running. Review Windows event logs to see if there are any related activities that might be stopping the service.

### Verify wake-up proxy

If you enable the [wake-up proxy in client settings](../deploy/about-client-settings#power-management), there are two checks for the **Configuration Manager Wake-up Proxy** service:

- Verify that the service startup type is automatic. To remediate a failure with this check, reset the service startup type to automatic. Check group policies to make sure something isn't automatically configuring the service startup type.
- Verify that the service is running. The remediation for this check is to start the wake-up proxy service. Then monitor it to make sure it keeps running. Review Windows event logs to see if there are any related activities that might be stopping the service.

## Most common check failures

The following checks have the most commonly reported failures. The numbers are included to provide scale between the checks.

- Verify CcmEval task has run in recent cycles (4,950)
- Verify client prerequisites (554)
- Verify Windows Update service startup type (399)
- Verify Configuration Manager Remote Control service status (345)
- Verify Configuration Manager Remote Control service startup type (294)
- Verify SMS Agent Host service status (249)
- Verify SQL Server CE database is healthy (157)
- Verify client WMI Provider (131)
- Verify client installation (120)
- WMI event sink test (93)