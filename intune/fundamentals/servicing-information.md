---
layout: Conceptual
title: Microsoft Intune servicing information and details - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/servicing-information
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Learn more about the frequency of the Microsoft Intune service updates, the release cadence, and how to check your tenant release version.
ms.date: 2025-04-10T00:00:00.0000000Z
ms.topic: overview
ms.reviewer: acabello
locale: en-us
document_id: 1573f093-f9da-6b1b-5847-c61e0b3d997b
document_version_independent_id: 1573f093-f9da-6b1b-5847-c61e0b3d997b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/servicing-information.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/servicing-information
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/servicing-information.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: e7ba9f43-efc3-35d1-dba2-d705b191c671
---

# Microsoft Intune servicing information and details - Microsoft Intune | Microsoft Learn

New feature releases for Intune typically have a six to eight week cadence, from planning to release. This cadence is called a sprint. Intune releases use a `YYMM` naming convention. For example, 2502 is the February 2025 release.

This article provides information about the frequency of the Microsoft Intune service updates, the release cadence, and how to check your tenant release version.

## How updates are released

The monthly release process involves many different environments and is deployed to multiple Azure services. After the release is deployed to Azure, the release updates are deployed to the Intune admin center, which makes the release features available for you to use.

An internal environment called Self Host is the first environment to receive the release. Self Host is used only by the Intune engineering teams. After Self Host, the service release is deployed to the Microsoft tenant that manages many devices. Once the release is validated that there are no key issues with the service release, the release begins deploying to customer environments in a phased approach. Once all tenants are successfully updated, the Microsoft Intune admin center is updated. This phased approach helps identify issues before they affect the service or our customers.

Updating Intune client applications is a different process. For devices that meet the prerequisites, the Intune management extension (IME) is installed automatically when certain features are assigned to a user or device. See [Intune management agent for macOS](../app-management/deployment/management-agent-macos), [Add, assign, & monitor a Win32 app](../app-management/deployment/add-win32#prerequisites), and [Add PowerShell scripts to Windows devices](../device-management/tools/run-powershell-scripts-windows) for details. The IMEs are frequently updated alongside with our monthly releases. After a tenant is successfully updated, devices with the IME installed download the new version of the IME as they check-in on their regular schedule, resulting in a phased deployment of the updates within a tenant. The IME download sized is around 10Mb.

For Company Portal app, Microsoft is subject to the release requirements and processes of the Apple App Store, Google Play, and sometimes mobile carriers. It isn't always possible to align the Intune release updates with updates to the Company Portal app.

### How can I tell if a service update is complete for my tenant?

To check the release version of your tenant, use the following steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** &gt; **Tenant status**. Your tenant's name, location, MDM authority, account status, and service release number are shown.

In the following example, the tenant has the 2311 (November 2023) service release:

[![In the Intune admin center, select tenant administration and then tenant status to see the service release version.](media/servicing-information/intune-admin-center-tenant-status.png)](media/servicing-information/intune-admin-center-tenant-status.png#lightbox)

## Keep current with release features

Microsoft updates Intune frequently to keep up with operating system updates and mobile app releases. Keeping up to date about releases and changes is an important part of your Intune deployment. Intune provides several ways to stay current about latest updates:

- **[What's new in Intune](../whats-new/)**: Learn what's new in a Microsoft Intune release. When a feature is released, some information about that feature is added to this article. It also includes an overview of the current release, any notices, information about earlier releases, and other information.

    Content is published at the end of the current sprint, which is when the UI updates start deploying to the Microsoft Intune admin center.
- **[In development for Microsoft Intune](../whats-new/in-development)**: Learn more about what features are in development for Microsoft Intune. This article is updated regularly with upcoming features and changes.
- **[Microsoft 365 Message center](/en-us/microsoft-365/admin/manage/message-center)**: When the service update finishes deploying, a message is posted in the **Message center**. Or, you can view the same messages in the Message center at `admin.microsoft.com`. Service APIs pull only the Microsoft Intune messages from Microsoft 365 into the Microsoft Intune admin center.
- **[Microsoft Intune tenant status](../governance/tenant-status)**: This message center is a centralized hub where you can view current information and communications about the Intune service and your tenant status.

    To see the hub, use the following steps:

    1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
    2. Go to **Tenant administration** &gt; **Tenant status** &gt; **Service health and message center**.
    3. Under **Message center**, select any message to read it.
- **[Microsoft 365 Admin mobile app](/en-us/microsoft-365/admin/admin-overview/admin-mobile-app)**: Receive service notifications on your mobile device.
- **Social media**: Get the latest announcements on X at `@IntuneSuppTeam`.

For more information from the Intune support team and the broader Intune community, see the following blogs:

- [Microsoft Intune Blog](https://aka.ms/IntuneBlog)
- [Intune Customer Success Blog](https://aka.ms/IntuneCustomerSuccess)
- [Staying up to date on Intune new features, service changes, and service health](https://aka.ms/MEMServiceChangeBlog)
- [Tips and tricks for managing Intune](https://aka.ms/mem-tipsandtricks-blog)

Note

Monitor Intune service health in the [Microsoft 365 admin center](https://admin.microsoft.com) under **Service Health**.

## Advance notice for service changes

| Type of change | Notice |
| --- | --- |
| End-user experience changes | 7–30 days |
| **Plan for Change** notices that require admin action | About 30 days, with an **Act By** date when applicable |
| Deprecations | Up to 90 days where possible (less when a third party announces the change) |
| Service retirement | 12 months |

For post-incident actions, Microsoft emails service administrators using the email address in your [Microsoft 365 communication preferences](/en-us/microsoft-365/admin/manage/change-address-contact-and-more).

## Intune service configurations and experimentation

Intune uses Experimentation and Configuration Service (ECS) to request and receive service configuration payloads that help maintain service reliability, security, compliance, and customer experience. These payloads can include service configurations, controlled feature rollouts, and experimentation data.

Important

Disabling communication with required Microsoft cloud services can affect Microsoft's ability to deliver critical service updates, reliability improvements, security mitigations, and feature enablement for Intune-managed devices.

### Configurations

Configurations are payloads meant to ensure service health and reliability, security, and privacy compliance, and are intended to have the same value for all the users (based on platforms and channels). Configuration updates can be deployed rapidly to maintain service quality and respond to emerging issues

### Controlled feature rollout

Controlled feature rollout (CFR) is a procedure for slowly increasing the size of the user group that receives a feature. By distributing a new feature to a randomly selected subset of the user population, it's possible to compare user feedback to an equally sized control group without the feature to measure the impact of the feature. This approach helps reduce deploymnet risk, identify potential issues early, validate feature performance at scale and improve overall service quality. During a controlled rollout, some organizations might see a feature before others, even when they are running the same supported platform and service version

### Experiments

Currently, Intune doesn't do any experimental testing. Development is carried out via the controlled feature rollout process. If this changes, an announcement will be posted in the Message Center.

## Privacy and personal data in Intune

You should understand how Intune collects, stores, retains, processes, secures, shares, audits, and exports personal data. Microsoft Intune doesn't use any personal data collected as part of providing the service for profiling, advertising, or marketing purposes.

The following resources can help you understand privacy and personal data in Intune:

- [Privacy and personal data in Intune](../privacy/)
- [Optional diagnostic data from Intune Client apps](../privacy/data-handling/optional-diagnostic-data)
- [Data collection in Intune](../privacy/data-handling/data-collection)
- [Data storage and processing in Intune](../privacy/data-handling/data-storage-processing)
- [Audit, export, or delete personal data in Intune](../privacy/personal-data/manage-data-requests)