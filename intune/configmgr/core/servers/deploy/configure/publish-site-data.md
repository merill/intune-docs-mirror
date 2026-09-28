---
layout: Conceptual
title: Publish site data - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/publish-site-data
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
description: Learn how to publish Configuration Manager sites to Active Directory Domain Services.
ms.date: 2017-02-07T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 6cc5227b-c921-f039-68b5-834746d69f4d
document_version_independent_id: 4e7adac3-a54b-0502-801a-f52e37071f8e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/publish-site-data.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/publish-site-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/publish-site-data.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 96ff1d24-60eb-540a-a6fd-e9c509bd2107
---

# Publish site data - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

After you extend the Active Directory schema for Configuration Manager, you can publish Configuration Manager sites to Active Directory Domain Services (AD DS). This lets Active Directory computers securely retrieve site information from a trusted source. Although publishing site information to AD DS is not required for basic Configuration Manager functionality, it can reduce administrative overhead to do so.

- **When a site is configured to publish to AD DS**, Configuration Manager clients can automatically find management points through Active Directory publishing. They use an LDAP query to a global catalog server.
- **When a site does not publish to AD DS**, clients must have an alternative mechanism to locate their default management point.

For information about how clients find a management point, see [Understand how clients find site resources and services for Configuration Manager](../../../plan-design/hierarchy/understand-how-clients-find-site-resources-and-services).

## Configure sites to publish to AD DS

The following are the high-level steps:

- You must [extend the Active Directory schema for Configuration Manager](../../../plan-design/network/extend-the-active-directory-schema) in each forest where you will publish site data. Also ensure the **System Management** container is present.
- You must grant the computer account of each primary site that will publish data **full control** to the **System Management** container, and all of its child objects.

### To enable a Configuration Manager site to publish site information to Active Directory forest

1. In the Configuration Manager console, click **Administration**.
2. In the **Administration** workspace, expand **Site Configuration**, and click **Sites**. Select the site that you want to have publish its site data. Then on the **Home** tab, in the **Properties** group, click **Properties**.
3. On the **Publishing** tab of the site's properties, select the forests to which this site will publish site data.
4. Click **OK** to save the configuration.

### To set up Active Directory forests for publishing

1. In the Configuration Manager console, click **Administration**.
2. In the **Administration** workspace, expand **Hierarchy Configuration**, and click **Active Directory Forests**. If Active Directory Forest Discovery has previously run, you see each discovered forest in the results pane. The local forest and any trusted forests are discovered when Active Directory Forest Discovery runs. Only untrusted forests must be manually added.

    - To set up a previously discovered forest, select the forest in the results pane. Then on the **Home** tab, in the **Properties** group, click **Properties** to open the forest properties. Continue with step 3.
    - To set up a new forest that is not listed, on the **Home** tab, in the **Create** group, click **Add Forest** to open the **Add Forests** dialog box. Continue with step 3.
3. On the **General** tab, complete configurations for the forest that you want to discover, and specify the **Active Directory Forest Account**.

    Note

    Active Directory Forest Discovery requires a global account to discover and publish to untrusted forests. If you do not use the computer account of the site server, you can only select a global account.
4. If you plan to allow sites to publish site data to this forest, on the **Publishing** tab, complete configurations for publishing to this forest.

    Note

    If you enable sites to publish to a forest, you must extend the Active Directory schema of that forest for Configuration Manager. The Active Directory Forest Account must have Full Control permissions to the System container in that forest.
5. When you complete the configuration of this forest for use with Active Directory Forest Discovery, click **OK** to save the configuration.