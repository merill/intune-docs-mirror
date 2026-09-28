---
layout: Conceptual
title: Extend and Migrate an on-premises site to Microsoft Azure - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/support/azure-migration-tool
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
description: Learn about how to use the migration tool to programmatically create Azure virtual machines for Configuration Manager.
ms.date: 2021-01-27T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 188939d5-071a-d370-43d9-1299f30388f5
document_version_independent_id: 4d094e0d-2d5d-a599-4721-c4c7c16273c3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/support/azure-migration-tool.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/support/azure-migration-tool
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/support/azure-migration-tool.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/20ed8455-bc18-4537-87a4-83784e7b2a39
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/9a7f703b-30bb-4d62-9eb4-97213f571849
platformId: 025c89b0-9712-d3d4-8feb-93a09ae60e45
---

# Extend and Migrate an on-premises site to Microsoft Azure - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Starting in version 1910, this tool helps you to programmatically create Azure virtual machines (VMs) for Configuration Manager.  It can install with default settings site roles like a passive site server, management points, and distribution points. Once you validate the new roles, use them as additional site systems for high availability. You can also remove the on-premises site system role and only keep the Azure VM role.

## Prerequisites

- An Azure subscription
- Starting in version 2010, it supports environments with virtual networks other than ExpressRoute. In version 2006 and earlier, it requires an Azure virtual network with ExpressRoute gateway.
- Starting in version 2010, you can use the tool in a hierarchy or a standalone primary site. In version 2006 and earlier, it only works with a standalone primary site.
- Starting in version 2010, it supports a site with a collocated site database. In version 2006 and earlier, it requires the database to be on a remote SQL Server.
- Your user account needs to be a Configuration Manager **Full Administrator** and have administrator rights on the primary site server.
- To add a site server in passive mode, the site server must meet the [high availability requirements](../servers/deploy/configure/site-server-high-availability#prerequisites). For example, it requires a [remote content library](../plan-design/hierarchy/remote-content-library).

### Required Azure permissions

You'll need the following permissions in Azure when you run the tool:

- Microsoft.Resources/subscriptions/resourceGroups/read
- Microsoft.Resources/subscriptions/resourceGroups/write
- Microsoft.Resources/deployments/read
- Microsoft.Resources/deployments/write
- Microsoft.Resources/deployments/validate/action
- Microsoft.Compute/virtualMachines/extensions/read
- Microsoft.Compute/virtualMachines/extensions/write
- Microsoft.Compute/virtualMachines/read
- Microsoft.Compute/virtualMachines/write
- Microsoft.Network/virtualNetworks/read
- Microsoft.Network/virtualNetworks/subnets/read
- Microsoft.Network/virtualNetworks/subnets/join/action
- Microsoft.Network/networkInterfaces/read
- Microsoft.Network/networkInterfaces/write
- Microsoft.Network/networkInterfaces/join/action
- Microsoft.Network/networkSecurityGroups/write
- Microsoft.Network/networkSecurityGroups/read
- Microsoft.Network/networkSecurityGroups/join/action
- Microsoft.Storage/storageAccounts/write
- Microsoft.Storage/storageAccounts/read
- Microsoft.Storage/storageAccounts/listkeys/action
- Microsoft.Storage/storageAccounts/listServiceSas/action
- Microsoft.Storage/storageAccounts/blobServices/containers/write
- Microsoft.Storage/storageAccounts/blobServices/containers/read
- Microsoft.KeyVault/vaults/deploy/action
- Microsoft.KeyVault/vaults/read

For more information about permissions and assigning roles, see [Add or remove Azure role assignments using the Azure portal](/en-us/azure/role-based-access-control/role-assignments-portal).

### Virtual network support

Starting in version 2010, to support other virtual networks other than ExpressRoute, make the following configurations:

- In the configuration of the virtual network, go to the **DNS servers** settings. Add a **Custom** DNS server with the IP address of a domain controller.
- On the site server where you'll run the tool, set the following registry value: `HKCU\Software\Microsoft\ConfigMgr10\ExtendToAzure, SkipVNetCheck = 1`

## Run the tool

1. Sign on to the site server and run the following tool in the Configuration Manager installation directory: `Cd.Latest\SMSSETUP\TOOLS\ExtendMigrateToAzure\ExtendMigrateToAzure.exe`
2. Review the information on the **General** tab, and then switch to the **Azure Information** tab.
3. On the **Azure Information** tab, choose your **Azure environment**, and then **Sign in**.

    Tip

    You may need to add `https://*.microsoft.com` to your trusted websites list to correctly sign in.

    [![Azure Information tab in the Extend and Migrate tool](media/3556022-azure-information-tab.png)](media/3556022-azure-information-tab.png#lightbox)
4. After you sign in, select your **Subscription ID** and **Virtual network**.

    Note

    In version 2006 and earlier, the tool only lists networks with an ExpressRoute gateway.

## Site server high availability

1. On the **Site Server High Availability** tab, select **Check** to evaluate your site's readiness.

    If any of the checks fail, select **More detail** to determine how to remediate the problem. For more information about these prerequisites, see [Site server high availability](../servers/deploy/configure/site-server-high-availability#prerequisites).
2. If you want to extend or migrate your site server to Azure, select **Create a site server in Azure**. Then fill in the following fields:

    | Name | Description |
    | --- | --- |
    | **Subscription** | Read only. Shows the subscription name and ID. |
    | **Resource group** | Lists available resource groups. If you need to create a new resource group, use the [Azure portal](https://portal.azure.com), and then rerun this tool. |
    | **Location** | Read only. Determined by your virtual network's location |
    | **VM Size** | Choose a size to fit your workload. Microsoft recommends the **Standard\_DS3\_v2**. |
    | **Operating system** | Read only. The tool uses Windows Server 2019. |
    | **Disk type** | Read only. The tool uses Premium SSD for best performance. |
    | **Virtual network** | Read only. |
    | **Subnet** | Select the subnet to use. If you need to create a new subnet, use the [Azure portal](https://portal.azure.com). |
    | **Machine name** | Enter the name of the passive site server VM in Azure. It's the same name shown in the [Azure portal](https://portal.azure.com). |
    | **Local admin username** | Enter the name of the local administrative user that the Azure VM creates before it joins the domain. |
    | **Local admin password** | The password of the local administrative user. To protect the password during Azure deployment, store the password as a secret in [Azure Key Vault](/en-us/azure/key-vault/key-vault-overview). Then, use the reference here. If needed, create a new one from the [Azure portal](https://portal.azure.com). |
    | **Domain FQDN** | The fully qualified domain name for the Active Directory domain to join. By default, the tool gets this value from your current machine. |
    | **Domain username** | The name of the domain user allowed to join the domain. By default, the tool uses the name of the currently signed in user. |
    | **Domain password** | The password of the domain user to join the domain. The tool verifies it after you select **Start**. To protect the password during Azure deployment, store the password as a secret in [Azure Key Vault](/en-us/azure/key-vault/key-vault-overview). Then, use the reference here. If needed, create a new one from the [Azure portal](https://portal.azure.com). |
    | **Domain DNS IP** | Used for joining the domain. By default, the tool uses the current DNS from your current machine. |
    | **Type** | Read only. It shows *Passive Site Server* as the type. |

    Important

    By default the virtual machines are set to **No** for **Use existing Windows Server license**. If you want to utilize your on-premises Windows Server licenses with Software Assurance, configure this setting in the [Azure portal](https://portal.azure.com) after the virtual machines are provisioned. For more information, see [Azure Hybrid Benefit for Windows Server](/en-us/windows-server/get-started/azure-hybrid-benefit).
3. To start provisioning the Azure VM, select **Start**. To monitor the deployment status, switch to the **Deployments in Azure** tab in the tool. To get the latest status, select **Refresh deployment status**.

    Tip

    You can also use the [Azure portal](https://portal.azure.com) to check the status, find errors, and determine potential fixes.
4. When the deployment finishes, go to your SQL Servers, and grant permissions for the new Azure VM. For more information, see [Site server high availability - Prerequisites](../servers/deploy/configure/site-server-high-availability#prerequisites).
5. To add the Azure VM as a site server in passive mode, select **Add site server in passive mode**.
6. Once the site adds the site server in passive mode, the **Site Server High Availability** tab shows the status.

    [![Passive site server added to Site Server High Availability tab in Azure migration tool](media/3556022-site-server-passive-mode.png)](media/3556022-site-server-passive-mode.png#lightbox)
7. Next, switch to the Deployments in Azure tab to finish the deployment.

## Site database

The tool doesn't currently have any tasks to migrate the database from on-premises to Azure. You can choose to move the database from an on-premises SQL Server to an Azure SQL Server VM. The tool lists the following articles on the **Site Database** tab to help:

- [Backup and restore the database](../servers/manage/backup-and-recovery)
- [Configure a SQL Server Always On availability group and allow the data to replicate](../servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#changes-for-site-backup)
- [Migrate a SQL Server database to an Azure SQL Server VM](/en-us/azure/azure-sql/virtual-machines/windows/migrate-to-vm-from-sql-server)

## Site system roles

1. Switch to the **Site System Roles** tab. To provision a new site system role with the default settings, select **Create new**. You can provision roles such as the management point, distribution point, and software update point. Not all roles are currently available in the tool.

    [![Site System Roles tab in the Extend and Migrate tool](media/3556022-site-system-roles-tab.png)](media/3556022-site-system-roles-tab.png#lightbox)
2. In the provisioning window, fill in the fields to provision the site role's VM in Azure. These details are similar to the above list for the site server.
3. To start provisioning the Azure VM, select **Start**. To monitor the deployment status, switch to the **Deployments in Azure** tab in the tool. To get the latest status, select **Refresh deployment status**.

    Tip

    You can also use the [Azure portal](https://portal.azure.com) to check the status, find errors, and determine potential fixes.
4. Repeat this process to add more site system roles.
5. Next, go to the Deployments in Azure tab to finish the deployment.
6. When the deployment finishes, go to the Configuration Manager console to make additional changes to the site role.

## Deployments in Azure

1. Once Azure creates the VM, switch to the **Deployments in Azure** tab in the tool. Select **Deploy** to configure the role with the default settings.
2. Select **Run** to start the PowerShell script.

    [![Deploy site roles by running the generated PowerShell script](media/3556022-run-powershell-script-deployment.png)](media/3556022-run-powershell-script-deployment.png#lightbox)
3. Repeat this process to configure more roles.

## Add site roles to an existing VM

Starting in Configuration Manager version 2002, the tool supports provisioning multiple site system roles on a single Azure VM. You can add site system roles after the initial Azure VM deployment has completed. To add a new role to an existing VM, do the following steps:

1. On the **Deployments in Azure** tab, select on a virtual machine deployment that has a **Completed** status.
2. Select **Create new** to add an additional role to the virtual machine.