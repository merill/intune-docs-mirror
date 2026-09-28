---
layout: Conceptual
title: Set up checklist for CMG - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/set-up-checklist
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
description: Get an overview of the cloud management gateway (CMG) setup process and make sure you have all prerequisites ready to start.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: 08585d2d-c8d3-d732-5884-1a01069270ae
document_version_independent_id: 982da2bc-3015-cdad-cc51-a35cb1f9d19a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/cmg/set-up-checklist.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/cmg/set-up-checklist
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/cmg/set-up-checklist.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: b399c92e-9df8-207c-af12-f9a37839f083
---

# Set up checklist for CMG - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Before you deploy a cloud management gateway (CMG), use this article to understand the setup process. Also make sure you have all of the prerequisites ready to get started.

First, develop your design and plan for implementing a CMG in your environment. For more information, see [Plan for cloud management gateway](plan-cloud-management-gateway). Use that section of articles to determine your CMG design.

The overall CMG setup process is divided into the following five main parts:

1. *Get the CMG server authentication certificate*: The CMG uses HTTPS for secure client communication over the public internet. You can get a certificate from a public provider, or issue one from your public key infrastructure (PKI).
2. *Configure Microsoft Entra ID*: Configuration Manager requires app registrations in Microsoft Entra ID. You can let Configuration Manager create them, or an Azure administrator can pre-create the registrations.
3. *Configure client authentication*: Because clients communicate across the internet, Configuration Manager requires more security for this channel. You can use Microsoft Entra ID, PKI certificates, or token-based authentication from the site server.
4. *Set up the CMG*: This step also includes configuring the site, and adding the CMG connection point site system role.
5. *Configure clients to use the CMG*.

The other articles in this section step through each part of the process.

## Terminology

The following terms are used in the context of setting up a CMG. They're defined here for clarity.

- Microsoft Entra ID *tenant*: The directory of user accounts and app registrations. One tenant can have multiple subscriptions.
- Azure *subscription*: A subscription separates billing, resources, and services. It's associated with a single tenant.

    Tip

    For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](/en-us/microsoft-365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings).
- Azure *resource group*: A container that holds related resources for an Azure solution. The resource group includes those resources that you want to manage as a group. You decide which resources belong in a resource group based on what makes the most sense for your organization. For more information, see [Resource groups](/en-us/azure/azure-resource-manager/management/overview#resource-groups).
- CMG *service name*: The common name (CN) of the CMG server authentication certificate. Clients and the CMG connection point site system role communicate with this service name. For example, `GraniteFalls.Contoso.Com` or `GraniteFalls.WestUS.CloudApp.Azure.Com`.
- CMG *deployment name*: The first part of the service name plus the Azure location for the cloud service deployment. The cloud service manager component of the service connection point uses this name when it deploys the CMG in Azure. The deployment name is always in an Azure domain. The Azure location depends upon the deployment method, for example:

    - Virtual machine scale set: `GraniteFalls.WestUS.CloudApp.Azure.Com`
    - Classic deployment: `GraniteFalls.CloudApp.Net`

## Checklist

Use the following checklist to make sure you have the necessary information and prerequisites to create a CMG:

- The Azure environment to use. For example, the Azure Public Cloud or the Azure US Government Cloud.
- The Azure region for this CMG deployment.
- How many VM instances you need for scale and redundancy.
- A Microsoft Entra **[Application Developer](/en-us/entra/identity/role-based-access-control/permissions-reference#application-developer)**, **[Cloud Application Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)**, or **[Application Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)** role to register apps in Microsoft Entra ID.
- An Azure subscription **[Owner](/en-us/azure/role-based-access-control/built-in-roles#privileged)** role for when you create the CMG in Azure.
- At least one existing site system server on which you plan to add the **CMG connection point** role.
- Review the [internet access requirements](data-flow#internet-access-requirements) to make sure each required services can be reached.
- [Enable this optional feature](../../../servers/manage/optional-features).

You'll set up other prerequisite components during the next steps in the process.

## Automate with PowerShell

Optionally, you can automate aspects of the CMG setup using PowerShell. While some cmdlets were available in earlier versions, version 2010 includes new cmdlets and significant improvements to existing cmdlets.

For example, an Azure administrator first creates the two required apps in Microsoft Entra ID. Then you write a script that uses the following cmdlets to deploy a CMG:

1. **Import-CMAADServerApplication**: Create the Microsoft Entra server app definition in Configuration Manager.
2. **Import-CMAADClientApplication**: Create the Microsoft Entra client app definition in Configuration Manager.
3. Use **Get-CMAADApplication** to get the app objects, and then pass to **New-CMCloudManagementAzureService** to create the Azure service connection in Configuration Manager.
4. **New-CMCloudManagementGateway**: Create the CMG service in Azure.
5. **Add-CMCloudManagementGatewayConnectionPoint**: Create the CMG connection point site system.

You can use these cmdlets to automate the creation, configuration, and management of the CMG service and Microsoft Entra requirements.

Microsoft Entra app definitions in Configuration Manager:

- [Get-CMAADApplication](/en-us/powershell/module/configurationmanager/Get-CMAADApplication)
- [Import-CMAADClientApplication](/en-us/powershell/module/configurationmanager/Import-CMAADClientApplication)
- [Import-CMAADServerApplication](/en-us/powershell/module/configurationmanager/Import-CMAADServerApplication)

The **Cloud Management** Azure service in Configuration Manager:

- [New-CMCloudManagementAzureService](/en-us/powershell/module/configurationmanager/New-CMCloudManagementAzureService)
- [Set-CMCloudManagementAzureService](/en-us/powershell/module/configurationmanager/Set-CMCloudManagementAzureService)
- [Get-CMAzureService](/en-us/powershell/module/configurationmanager/Get-CMAzureService)
- [Remove-CMAzureService](/en-us/powershell/module/configurationmanager/Remove-CMAzureService)

The cloud management gateway service in Configuration Manager:

- [Get-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/Get-CMCloudManagementGateway)
- [New-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/New-CMCloudManagementGateway)
- [Remove-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/Remove-CMCloudManagementGateway)
- [Set-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/Set-CMCloudManagementGateway)
- [Start-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/Start-CMCloudManagementGateway)
- [Stop-CMCloudManagementGateway](/en-us/powershell/module/configurationmanager/Stop-CMCloudManagementGateway)

The CMG connection point site system role:

- [Add-CMCloudManagementGatewayConnectionPoint](/en-us/powershell/module/configurationmanager/Add-CMCloudManagementGatewayConnectionPoint)
- [Get-CMCloudManagementGatewayConnectionPoint](/en-us/powershell/module/configurationmanager/Get-CMCloudManagementGatewayConnectionPoint)
- [Remove-CMCloudManagementGatewayConnectionPoint](/en-us/powershell/module/configurationmanager/Remove-CMCloudManagementGatewayConnectionPoint)
- [Set-CMCloudManagementGatewayConnectionPoint](/en-us/powershell/module/configurationmanager/Set-CMCloudManagementGatewayConnectionPoint)