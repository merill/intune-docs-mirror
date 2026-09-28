---
layout: Conceptual
title: Publishing and the Active Directory schema - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/extend-the-active-directory-schema
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
description: Extend the Active Directory schema for Configuration Manager to simplify the process of deploying and configuring clients.
ms.date: 2021-01-21T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: f4417335-de0a-6a49-b1b4-5551199d8643
document_version_independent_id: 761507d4-99d2-991a-8baf-e0010d962d35
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/network/extend-the-active-directory-schema.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/network/extend-the-active-directory-schema
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/network/extend-the-active-directory-schema.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 51431af7-2c2c-2dcd-2bf2-42e4f2b59a64
---

# Publishing and the Active Directory schema - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When you extend the Active Directory schema for Configuration Manager, you introduce new structures to Active Directory. Configuration Manager sites use these new structures to publish key information in a secure location where clients can easily access it.

When you manage on-premises clients, you should extend the Active Directory schema for Configuration Manager. An extended schema can simplify the process of deploying and setting up clients. An extended schema also lets clients efficiently locate resources like content servers. Extending the schema is a one-time action for any forest.

If you're not familiar with the benefits of an extended schema for Configuration Manager, see [Schema extensions for Configuration Manager](schema-extensions).

When you don't use an extended schema, you can set up other methods like DNS to locate services and site system servers. These methods of service location require other configurations and aren't the preferred method for service location by clients. For more information, see [Understand how clients find site resources and services for Configuration Manager](../hierarchy/understand-how-clients-find-site-resources-and-services).

If your Active Directory schema was extended for Configuration Manager 2007 or System Center 2012 Configuration Manager, then you don't need to do more. The schema extensions are unchanged and are already in place.

## Step 1: Extend the schema

To extend the schema for Configuration Manager:

- Use an account that's a member of the **Schema Admins** security group.
- Sign in with that account to the schema master domain controller.

Then use one of the following options to add the new classes and attributes to the Active Directory schema.

### Option A: Use the extadsch.exe tool

This tool is in the **SMSSETUP\BIN\X64** folder on the Configuration Manager installation media.

1. Open a command line, and run **extadsch.exe**.

    Tip

    Run this tool from a command line to view feedback while it runs.
2. To verify that the schema extension was successful, review **extadsch.log** in the root of the system drive.

### Option B: Use the LDIF file

This file is in the **SMSSETUP\BIN\X64** folder on the Configuration Manager installation media.

1. Make a copy of the **ConfigMgr\_ad\_schema.ldf** file. Edit it in Notepad, and define the Active Directory root domain that you want to extend. Replace all instances of the text `DC=x` in the file with the full name of the domain to extend. For example, if the full name of the domain to extend is named **widgets.contoso.com**, change all instances of `DC=x` in the file to `DC=widgets, DC=contoso, DC=com`.
2. Use the **LDIFDE** command-line utility to import the contents of the **ConfigMgr\_ad\_schema.ldf** file to Active Directory Domain Services. For example, the following command-line imports the schema extensions, turns on verbose logging, and creates a log file in the temp directory:

    `ldifde -i -f ConfigMgr_ad_schema.ldf -v -j "%temp%"`

    For more information, see [Command-line reference: Ldifde](/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc731033%28v=ws.11%29).
3. To verify that the schema extension was successful, review the ldifde log file.

## Step 2: The System Management container

After you extend the schema, create a container named **System Management** in Active Directory Domain Services. Create this container once in each domain that has a Configuration site that will publish data to Active Directory. For each container, you need to grant permissions to the computer account of each site server that will publish data to that domain.

1. Use an account that has the **Create All Child Objects** permission on the **System** container in Active Directory Domain Services.
2. Run **ADSI Edit** (adsiedit.msc), and connect to the site server's domain.
3. Create the container:

    1. Expand the fully qualified domain name, and expand the distinguished name. Right-click **CN=System**, choose **New**, and then select **Object**.
    2. In the **Create Object** window, select **Container**, and then select **Next**.
    3. In the **Value** box, enter `System Management`, and then select **Next**.
4. Assign permissions:

    Note

    If you prefer, you can use other tools like the Active Directory Users and Computers administrative tool (dsa.msc) to add permissions to the container.

    1. Right-click **CN=System Management**, and select **Properties**.
    2. Switch to the **Security** tab. Select **Add**, and then add the site server's computer account with the **Full Control** permission.

        Add the computer account for each Configuration Manager site server in this domain. If you use [site server high availability](../../servers/deploy/configure/site-server-high-availability), make sure to include the computer account of the site server in passive mode.
    3. Select **Advanced**, select the site server's computer account, and then select **Edit**.
    4. In the **Apply onto** list, select **This object and all descendant objects**.
    5. Select **OK** to save the configuration.