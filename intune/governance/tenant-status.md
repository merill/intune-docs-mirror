---
layout: Conceptual
title: About the Microsoft Intune tenant status page - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/governance/tenant-status
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- help-support
description: The Intune tenant status page displays details about your tenant and the status of connectors you've configured, and messages intended for tenants and about the Intune service health.
ms.date: 2025-02-24T00:00:00.0000000Z
ms.topic: concept-article
ms.reviewer: crisk
locale: en-us
document_id: 5839b142-4dc3-7b60-e8a6-14247e940144
document_version_independent_id: 5839b142-4dc3-7b60-e8a6-14247e940144
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/governance/tenant-status.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: governance/tenant-status
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/governance/tenant-status.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/c4c18c0c-090d-4c28-a4be-9e6214a0c4fb
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/b22d517c-92cf-4ee3-8dca-36c6cd062217
platformId: df9ca91e-acab-3d02-c01e-d1975922a3ce
---

# About the Microsoft Intune tenant status page - Microsoft Intune | Microsoft Learn

The Microsoft Intune tenant status page is a centralized hub where you can view important details about your tenant. Details include:

- Your tenant name and location
- Service release versions
- Licensed users and enrolled devices

You can also view the status of the Intune connectors you've configured, and health messages for the Intune service and general messages for Tenants.

Tip

A tenant is an instance of Microsoft Entra ID. Your subscription to Intune is hosted by a Microsoft Entra tenant. For more information, see [Set up a tenant](/en-us/entra/identity-platform/quickstart-create-new-tenant) in the Microsoft Entra documentation.

## Prerequisites

To access the Tenant administration page, you need to have the following Intune permissions: `Organization.Read`, `ManagedDevice.Read`, and `ManagedApp.Read`. These permissions are granted to the **Intune Read Only Operator** RBAC built-in role.

You can create a custom role that contains those permissions (recommended for least-permission). Or, you can use the **Intune Administrator** Microsoft Entra role. Use of Entra Identity Management (PIM) roles is supported when elevated prior to viewing the tenant status page.

## Access the tenant status page

To view the dashboard, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). Go to **Tenant administration** &gt; **Tenant Status**.

The page is divided into three tabs.

## Tenant details tab

Tenant details provide at-a-glance information about your tenant. View details like your tenant name and location, your MDM Authority, and your tenants service release number. The service release number is a link that opens [What's new in Intune](../whats-new/). In *What's new*, you can read about the latest features and updates to the Intune service.

On this tab, you'll also find basic information about your available licenses and how many are assigned to users. Licenses for devices aren't shown.

Important

Note that *Total licensed users* refers to all users which have one license containing an Intune SKU, if the Intune SKU is enable or disable they still count as a licensed user.

## Connector status tab

Connector status is a one-stop location to review the status of all available connectors for Intune.

Connectors are:

- **Connections you configure to external services**. For example, the *Apple Volume Purchase Program* service or the *Windows Autopilot* service. Status for this type of connector is based on the last successful synchronization time.
- **Certificates or credentials that are required to connect to an external unmanaged service**, like *Apple Push Notification Services* (APNS) certificates. Status for this type of connector is based on the expiry timestamp of the certificate or credential.

When you open the *Connector status* tab, any unhealthy connectors display at the top of the list. Next are connectors with warnings, and then the list of healthy connectors. Connectors you haven't yet configured appear last as *Not Enabled*.

When there's more than a single connector of any one type, the status is a summary for all of those same connectors. The least healthy status of any single connector is used as the health for the group.

Important

Some connectors can report a status of *Healthy* or *Connected* but might not be functioning correctly. If you encounter issues with a specific connector, review any applicable connector logs or open a case with [support](../fundamentals/it-pro-support/get-support-admin-center) to investigate further.

**Connector status:**

- **Unhealthy:**
    - The certificate or credential has expired
    - The last synchronization was three or more days ago
- **Warning:**
    - The certificate or credential will expire within seven days
    - The last synchronization was more than one day ago
- **Healthy:**
    - The certificate or credential won't expire within the next seven days
    - The last synchronization was less than one day ago

When you select a connector from the list, the portal presents the portal page that is relevant to that connector. From the connectors page, you can view the status for previously configured connectors. You can also select options to add or create a new connector of that type.

For example, if you select the **VPP Expiry Date** connector, the **iOS Volume-Purchased Program Tokens** page opens. On this page you can view more details about that connector, create a new configuration, or edit and fix issues with an existing one.

## Service health and message center tab

The Service health and message center page is where you can view details about the Intune *Service health*, *Issues in your environment that require action*, and *Message center* posts that can provide information about updates and planned changes.

You can only set up your communication preferences for Intune Message center through the Microsoft 365 admin center. To do so, sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/) and go to **Health** &gt; **Service health**. Select **Customize**, and then open the **Email** tab. On the *Email* tab, select the checkbox for **Send me email notifications about service health**, and then configure the additional preferences to meet your requirements.

### Service health

View details for active incidents and advisories in the Microsoft Intune admin center. Only incidents that affect your tenant are shown. This information is also available in on the Service health page of the [Microsoft 365 admin center](https://admin.microsoft.com).

When you select an incident, the incident details are presented directly in the Tenant Status page. To view past advisories and incidents, select **See past Incidents/Advisories**. The Microsoft 365 admin center opens and you can then view advisories and incidents from the last 30 days for your tenant.

To view information for *Service health*, your account must have the **Service support administrator** role in Microsoft Entra ID or the Microsoft 365 admin center. To assign these permissions, sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) with [Privileged Role Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator) permissions. Select **Users &gt; Active Users**, and then select the account that requires access. Select **Edit** for Roles, select *Service support administrator*, and then **Save** your edit to assign the permissions.

### Issues in your environment that require action

The **Issues in your environment that require action** section displays messages that are sent to alert tenant administrators about issues that might require action to resolve.

To view information for *Issues in your environment that require action*, your account must have the **Service support administrator** role in Microsoft Entra ID or the Microsoft 365 admin center. To assign these permissions, sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) with [Privileged Role Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#privileged-role-administrator) permissions. Select **Users &gt; Active Users**, and then select the account that requires access. Select **Edit** for Roles, select *Service support administrator*, and then **Save** your edit to assign the permissions.

### Intune Message center

View informational communications from the Intune service team without having to navigate to the Office Message Center. Communications include messages about changes that have recently happened to the Intune service, or that are on the way for your tenant.

By default, the 10 most recent and active messages display. To view older messages, select **See past Messages** to open the *Message center* in the Microsoft 365 admin center.

To view information for Intune News, your account must have the **Service support administrator** role in Microsoft Entra ID, or the **Message Center reader** role in the Microsoft 365 admin center. To assign this permission, sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) with administrator permissions. Select **Users &gt; Active Users**, and then select the account that requires access. Select **Edit** for *Roles*, select *Teams Communications Administrator*, and then **Save** your edit to assign the permissions.