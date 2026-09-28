---
layout: Conceptual
title: Download software updates - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/download-software-updates
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
description: Use the Download Software Updates Wizard to download software updates and distribute them to distribution points so they are ready to deploy to clients.
ms.date: 2023-03-20T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: software-updates
ms.collection: tier3
locale: en-us
document_id: 542b47c2-652c-ac9e-5486-431fe1df775c
document_version_independent_id: e957e8b7-2fc4-cb8d-58f9-000427a238e1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/deploy-use/download-software-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/deploy-use/download-software-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/deploy-use/download-software-updates.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: 5db79b56-669c-aea5-4f5e-bef5f56582a8
---

# Download software updates - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

There are several methods available to you for downloading software updates in Configuration Manager. When you create an automatic deployment rule (ADR) or manually deploy software updates, the software updates are downloaded to the content library on the site server. Then, the software updates are copied to the content library on the distribution points that are associated with the configured deployment package. If you want to download the software updates before you deploy them, you can use the Download Updates Wizard. Doing this will enable you to verify that the software updates are available on distribution points before you deploy the software updates to client computers.

Note

- Starting March 28, 2023, on-premises Windows 11, version 22H2 devices will receive quality updates via the Unified Update Platform (UUP). On-premises update management with Unified Update Platform (UUP) requires an additional 10 GB of space per Windows version and processor architecture for each version. For more information, see the [UUP considerations](/en-us/windows-server/administration/windows-server-update-services/plan/plan-your-wsus-deployment#uup-considerations) section
- For information about monitoring content status, see the [Content status monitoring](monitor-software-updates#BKMK_ContentStatus).

Use the following procedure to download software updates by using the Download Software Updates Wizard.

#### To download software updates

1. In the Configuration Manager console, go to the **Software Library** workspace, and select the **Software Updates** node.
2. Choose the software update to download by using one of the following methods:

    - Select one or more software update groups from the **Software Update Groups** node. Then click **Download** in the ribbon.
    - Select one or more software updates from **All Software Updates** node. Then click **Download** in the ribbon.

        Note

        In the **All Software Updates** node, Configuration Manager displays only software updates with a **Critical** and **Security** classification that have been released in the last 30 days.

        Tip

        Click **Add Criteria** to filter the software updates that are displayed in the **All Software Updates** node. Save search criteria that you often use, and then manage saved searches on the **Search** tab.
3. On the **Deployment Package** page of the Download Software Updates Wizard, configure the following settings:

    - **Select deployment package**: Choose this setting to select an existing deployment package for the software updates that are in the deployment.

        Note

        Software updates that the site has already downloaded to the selected deployment package won't be downloaded again.
    - **Create a new deployment package**: Select this setting to create a new deployment package for the software updates in the deployment. Configure the following settings:

        - **Name**: Specifies the name of the deployment package. The package must have a unique name that briefly describes the package content. It's limited to 50 characters.
        - **Description**: Specify a description that provides information about the deployment package. The optional description is limited to 127 characters.
        - **Package source**: Specifies the location of the software update source files. Type a network path for the source location, for example, `\\server\sharename\path`, or click **Browse** to find the network location. Create the shared folder for the deployment package source files before you proceed to the next page.

            - You can't use the specified location as the source of another software deployment package.
            - You can change the package source location in the deployment package properties after Configuration Manager creates the deployment package. If you do, first copy the content from the original package source to the new package source location.
            - The computer account of the SMS Provider and the user that's running the wizard to download the software updates must both have **Write** permissions to the download location. Restrict access to the download location. This restriction reduces the risk of attackers tampering with the software update source files.
        - **Enable binary differential replication**: Enable this setting to minimize network traffic between sites. Binary differential replication (BDR) only updates the content that has changed in the package, instead of updating the entire package contents. For more information, see [Binary differential replication](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management#binary-differential-replication).
4. On the **Distribution Points** page, specify the distribution points or distribution point groups to host the software update files. For more information about distribution points, see [Distribution point configurations](../../core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_configs). This page is available only when you create a new software update deployment package.
5. The **Distribution Settings** page is available only when you create a new software update deployment package. Specify the following settings:

    - **Distribution priority**: Use this setting to specify the distribution priority for the deployment package. The distribution priority applies when the deployment package is sent to distribution points at child sites. Deployment packages are sent in priority order: high, medium, or low. Packages with identical priorities are sent in the order in which they were created. If there's no backlog, the package processes immediately regardless of its priority. By default, the site sends packages with **Medium** priority.
    - **Enable for on-demand distribution**: Use this setting to enable on-demand content distribution to distribution points configured for this feature and in the client's current boundary group. When you enable this setting, the management point creates a trigger for the distribution manager to distribute the content to all such distribution points when a client requests the content for the package and the content isn't available. For more information, see [On-demand content distribution](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management#on-demand-content-distribution).
    - **Prestaged distribution point settings**: Use this setting to specify how you want to distribute content to prestaged distribution points. Choose one of the following options:

        - **Automatically download content when packages are assigned to distribution points**: Use this setting to ignore the prestage settings and distribute content to the distribution point.
        - **Download only content changes to the distribution point**: Use this setting to prestage the initial content to the distribution point, and then distribute content changes to the distribution point.
        - **Manually copy the content in this package to the distribution point**: Use this setting to always prestage content on the distribution point. This option is the default.

        For more information about prestaging content to distribution points, see [Use Prestaged content](../../core/servers/deploy/configure/deploy-and-manage-content#bkmk_prestage).
6. On the **Download Location** page, specify the location that Configuration Manager uses to download the software update source files. Use one of the following options:

    - **Download software updates from the Internet**: Select this setting to download the software updates from the location on the internet. This option is the default.
    - **Download software updates from a location on my network**: Select this setting to download the software updates from a local directory or shared folder. This setting is useful when the computer that runs the wizard doesn't have internet access. Any computer with internet access can preliminarily download the software updates. Then store them in a location on the local network that's accessible from the computer that runs the wizard.
7. On the **Language Selection** page, select the languages for which the site downloads the selected software updates. The site only downloads these updates if they're available in the selected languages. Software updates that aren't language-specific are always downloaded. By default, the wizard selects the languages that you've configured in the software update point properties. At least one language must be selected before proceeding to the next page. When you select only languages that a software update doesn't support, the download fails for the update.
8. On the **Summary** page, verify the settings that you selected in the wizard, and then click **Next** to download the software updates.
9. On the **Completion** page, verify that the software updates were successfully downloaded, and then click **Close**.