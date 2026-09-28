---
layout: Conceptual
title: Data Protection for Windows MAM - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/protection/enable-mam-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- Windows
ms.subservice: apps
description: Enable protected MAM access to org data using Windows MAM.
ms.date: 2025-10-02T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: demerson
locale: en-us
document_id: 137fd7e3-c5e2-9086-e1be-63f6fc4e702c
document_version_independent_id: 137fd7e3-c5e2-9086-e1be-63f6fc4e702c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/protection/enable-mam-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/protection/enable-mam-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/protection/enable-mam-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/691e3042-55ad-4ce1-b5e9-649b1cc47b5c
- https://authoring-docs-microsoft.poolparty.biz/devrel/8e3fdb08-a059-4277-98f6-c0e21e940707
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b7d11190-096c-4ddb-87db-63764f603aac
- https://authoring-docs-microsoft.poolparty.biz/devrel/88291526-9c74-4f87-878c-de0a82134421
platformId: bfed05b9-8ab3-908c-d78f-f27f061d04b1
---

# Data Protection for Windows MAM - Microsoft Intune | Microsoft Learn

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

You can enable protected Mobile Application Management (MAM) access to org data on personal Windows devices. This capability uses the following functionality:

- Intune Application Configuration Policies (ACP) to customize the org user experience
- Intune app protection policies to secure org data and ensure the client device is healthy
- Windows Security app client threat defense integrated with Intune APP to detect local health threats on personal Windows devices
- Application Protection Conditional Access to ensure the device is protected and healthy before granting protected service access via Microsoft Entra ID

## Before you begin

- Intune Mobile Application Management (MAM) for Windows is available for [supported Windows versions](../../fundamentals/ref-supported-platforms). This includes the supporting changes for Microsoft Edge (Stable and Extended Stable releases for Windows) and Windows Security app. App Protection Conditional Access is generally available.
- Windows MAM is supported in government cloud environments. For related information, see [Deploying apps using Intune on the GCC High and DoD Environments](../deployment/deploy-gcc-dod).

    For more information about MAM, see [Mobile Application Management (MAM) basics](../overview#mobile-application-management-mam-basics).
- The Mobile Threat Defense (MTD) Connector for the Windows Security Center (WSC) component is only supported on Windows 11 version 22631 (23H2) or later.

## Overview

Both end-users and organizations need to have protected organizational access from personal devices. Organizations need to ensure that corporate data is protected on personal, unmanaged devices. As an Intune admin, you have the responsibility to determine how members (end-users) of your organization access corporate resources in a protected way from an unmanaged device. You need to ensure when accessing organizational data, that the unmanaged devices are healthy, the applications adhere to your organization data's protection policies, and that the end-user's unmanaged assets on their device aren't impacted by your organization's policies.

As the Intune admin, you need to have the following app management functionality:

- Ability to deploy app protection policies to apps/users protected by the Intune APP SDK, including the following:
    - Data protection settings
    - Health Checks (aka Conditional Launch) settings
- Ability to require app protection policies via Conditional Access
- Ability to perform additional client health verification via Windows Security center by doing the following:
    - Designating Windows Security Center risk level for allowing end users to access corporate resources
    - Setting up tenant-based connector to Microsoft Intune for Windows Security Center
- Ability to deploy a selective wipe command to protected applications

Members of your organization (end-users) expect to have the following functionality for their accounts:

- Ability to log in to Microsoft Entra ID to access sites protected by Conditional Access
- Ability to verify health status of the client device, in the case where a device is considered unhealthy
- Ability to have access revoked to resources when a device remains unhealthy
- Ability to be informed, with clear remediation steps, when access is controlled by an administrator policy

Note

For information related to Microsoft Entra ID, see [Require an app protection policy on Windows devices](/en-us/azure/active-directory/conditional-access/how-to-app-protection-policy-windows).

## Conditional Access Compliance

Preventing data loss is a part of protecting your organizational data. Data loss prevention (DLP) is only effective if your org data cannot be accessed from any unprotected system or device. App Protection Conditional Access uses Conditional Access (CA) to ensure app protection policies are supported and enforced in a client application before allowing access to protected resources (such as org data). App Protection Conditional Access will allow end-users with personal Windows devices to use app protection policies managed applications, including Microsoft Edge, to access Microsoft Entra resources without fully managing their personal device.

This MAM service syncs compliance state per user, per app, and per device to the Microsoft Entra CA service. This includes the threat information received from the Mobile Threat Defense (MTD) vendors starting with Windows Security Center.

Note

This MAM service uses the same Conditional Access compliance workflow that is used to [manage Microsoft Edge on iOS and Android devices](../configuration/configure-edge-ios-android).

When a change is detected, the MAM service updates the device compliance state immediately. The service also includes MTD health state as part of the compliance state.

Note

The MAM service evaluates the MTD state in the service. This is done independently from the MAM client and client platform.

The MAM Client communicates the client heath state (or health metadata) to the MAM Service upon check-in. The health state includes any failure of APP Health Checks for **Block** or **Wipe** conditions. In addition, Microsoft Entra ID guides end-users through remediation steps when they attempt to access a blocked CA resource.

### Conditional Access Compliance

Organizations can use Microsoft Entra Conditional Access policies to ensure that users can only access work or school content using policy managed applications on Windows. To do this, you'll need a Conditional Access policy that targets all potential users. Follow the steps in [Require an app protection policy on Windows devices](/en-us/azure/active-directory/conditional-access/how-to-app-protection-policy-windows), which allows Microsoft Edge for Windows, but blocks other web browsers from connecting to Microsoft 365 endpoints.

With Conditional Access, you can also target on-premises sites that you have exposed to external users via the Microsoft Entra application proxy.

For more information, see [Using Microsoft Entra application proxy to publish on-premises apps for remote users](/en-us/entra/identity/app-proxy/overview-what-is-app-proxy)

## Threat Defense Health

The health status of a personal owned device is verified before allowing access to your org data. MAM threat detection can be connected with Windows Security Center. Windows Security Center provides a client device health assessment to Intune APP via a service-to-service connector. This assessment supports gating of the flow and access to org data on personal unmanaged devices.

The health state includes the following details:

- User, app, and device identifiers
- A predefined health state
- The time of last health state update

The health state is only sent for MAM enrolled users. End users may stop sending data by signing out of their org account in protected applications. Administrators may stop sending data by removing the Windows Security Connector from Microsoft Intune.

For related information, see [create an MTD app protection policy for Windows](../../device-security/mobile-threat-defense/create-app-protection-policy#to-create-an-mtd-app-protection-policy-for-windows).

## Create Intune app protection policies

App protection policies define which apps are allowed and the actions they can take with your organization's data. The choices available in app protection policies enable organizations to tailor the protection to their specific needs. For some, it may not be obvious which policy settings are required to implement a complete scenario.

As an admin, you can configure how data is protected through app protection policies. This configuration applies to the native Windows application interaction with the data. App protection policy settings are segmented into three categories:

- **Data Protection** - These settings control how data can move into and out of an org context (account, document, location, services) for the user.

- **Health Checks** (Conditional Launch) - These settings controls the device conditions required to access org data and the remediation action(s) if the conditions aren't met.

To help organizations prioritize client endpoint hardening, Microsoft has introduced taxonomy for its app protection policies data protection framework for mobile app management.

To see the specific recommendations for each configuration level and the minimum apps that must be protected, review [Data protection framework using app protection policies](data-protection-framework).

For more information on the available settings, see [Windows app protection policy settings](ref-settings-windows).