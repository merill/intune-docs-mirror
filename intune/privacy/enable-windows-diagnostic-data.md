---
layout: Conceptual
title: Enable Windows diagnostic data and license verification - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/privacy/enable-windows-diagnostic-data
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
description: Learn how to enable Intune tenant settings to use Windows diagnostic data and verify Windows licenses required for dependent features.
ms.date: 2026-02-24T00:00:00.0000000Z
ms.topic: how-to
ms.collection:
- M365-identity-device-management
- privacy
- sub-data-privacy
locale: en-us
document_id: 197a6fc9-b929-3bfa-ff91-15fe111a4dac
document_version_independent_id: 197a6fc9-b929-3bfa-ff91-15fe111a4dac
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/privacy/enable-windows-diagnostic-data.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: privacy/enable-windows-diagnostic-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/privacy/enable-windows-diagnostic-data.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fb014418-9042-0434-9a98-d483db4c7c96
---

# Enable Windows diagnostic data and license verification - Microsoft Intune | Microsoft Learn

Some Microsoft Intune features require access to Windows diagnostic data or verification that the tenant owns eligible Windows licenses. Configure these requirements at the tenant level so dependent features can function correctly.

## Enable Windows diagnostic data

To allow Intune to access Windows diagnostic data collected from enrolled devices:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Tenant administration** &gt; **Connectors and tokens** &gt; **Windows data**.
2. Toggle **Enable features that require Windows diagnostic data in processor configuration** to **On**. The default is *Off*.

Note

There are multiple ways to enable Windows diagnostic data for a tenant. This toggle reflects only your configuration choice for **Intune features**.

Turning this setting **Off** disables Intune features that rely on this configuration, but it might not disable processor configuration that was enabled by other methods.

Features that require Windows diagnostic data include:

- [Compatibility reports for Windows updates](../device-updates/windows/monitor-compatibility)
- [Reports for expedite policies](../device-updates/windows/configure-expedite-policy#monitoring-and-reporting)
- Driver update policies with alerts for Windows driver update failures
- Expedited quality update policies with alerts for Windows expedited update failures
- Feature update policies with alerts for feature update failures

To learn more about this configuration, see [Enable Windows diagnostic data processor configuration](/en-us/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enable-windows-diagnostic-data-processor-configuration) in the Windows privacy documentation.

## Enable Windows license verification

Some Intune features require an attestation that your tenant owns eligible Windows licenses. This setting confirms tenant entitlement for those features; it does not validate or assign licenses to individual devices.

To attest ownership of the required Windows licenses:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Tenant administration**](https://intune.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/TenantAdminMenu) &gt; [**Connectors and tokens**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/TenantAdminMenu/%7E/connectorsAndTokens) &gt; [**Windows data**].
2. Toggle **I confirm that my tenant owns one of these licenses** to **On**. By default, it's *Off*.

Supported licenses:

- Windows Enterprise E3/E5 or Microsoft 365 F3/E3/E5
- Windows Education A3/A5 or Microsoft 365 A3/A5
- Windows Virtual Desktop Access E3/E5

Features that require license verification include:

- [Compatibility reports for Windows updates](../device-updates/windows/monitor-compatibility)
- [Remediations](../device-management/tools/deploy-remediations)