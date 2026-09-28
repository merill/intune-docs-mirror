---
layout: Conceptual
title: Client installation properties in Active Directory - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services
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
description: Publish Configuration Manager client installation properties to Active Directory Domain Services.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: d90c1a45-2a29-c928-dd5c-81b8863b5f38
document_version_independent_id: 5bdb13ec-fe78-b3c7-8de4-46e0338de6a4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: ddc28ac6-633c-b3df-102a-36efbcf6b60a
---

# Client installation properties in Active Directory - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When you extend the Active Directory schema for Configuration Manager, and the site is published to Active Directory Domain Services, many client installation properties are published to Active Directory Domain Services. If a computer can locate these client installation properties, it can use them during Configuration Manager client deployment.

The advantages of using Active Directory Domain Services to publish client installation properties include the following:

- Software update point-based client installations and Group Policy client installations do not require setup parameters to be set up on each computer.
- Because this information is automatically generated, the risk of human error associated with manually entering installation properties is eliminated.

Note

For more information about how to extend the Active Directory schema for Configuration Manager, and how to publish a site, see [Schema extensions for Configuration Manager](../../plan-design/network/schema-extensions).

## Client installation properties published to Active Directory Domain Services

The following is a list of client installation properties. For more information about each item listed below, see [About client installation properties](about-client-installation-properties).

- The Configuration Manager site code.
- The site server signing certificate.
- The trusted root key.
- The client communication ports for HTTP and HTTPS.
- The fallback status point. If the site has multiple fallback status points, only the first one that was installed is published to Active Directory Domain Services.
- A setting to indicate that the client must communicate by using HTTPS only.
- Settings related to PKI certificates:

    - Whether to use a client PKI certificate.
    - The selection criteria for certificate selection. This may be required because the client has more than one valid PKI certificate that can be used for Configuration Manager.
    - A setting to determine which certificate to use if the client has multiple valid certificates after the certificate selection process.
    - The certificate issuers list that contains a list of trusted root CA certificates.
- Client.msi installation properties that are specified in the **Client** tab of the **Client Push Installation Properties** dialog box.

Client installation (CCMSetup) uses the properties that are published to Active Directory Domain Services only if no other properties are specified by using either of the following:

- The manual installation method (described later in this article)
- The Group Policy installation method (described later in this article)

Note

The client installation properties are used to install the client. These properties might be overwritten with new settings from its assigned site after the client is installed and has successfully been assigned to a Configuration Manager site.

Use the details in the following sections to determine which Configuration Manager client installation methods use Active Directory Domain Services to obtain client installation properties.

## Client push installation

Client push installation does not use Active Directory Domain Services to obtain installation properties.

Instead, you can specify client installation properties in the **Installation Properties** tab of the **Client Push Installation Properties** dialog box. These options and client-related site settings are stored in a file that the client reads during client installation.

Note

You do not have to specify any CCMSetup properties for client push installation, or the fallback status point, or the trusted root key in the **Installation Properties** tab. These settings are automatically supplied to clients when they are installed by using client push installation. In addition to Client.msi properties, CCMSetup supports the following parameters: /forcereboot, /skipprereq, /logon, /BITSPriority, /downloadtimeout, /forceinstall

Any properties that you specify in the **Installation Properties** tab are published to Active Directory Domain Services if the site is published to Active Directory Domain Services. These settings are read by client installations where CCMSetup is run with no installation properties.

## Software update point-based installation

The software update point-based installation method does not support the addition of installation properties to the CCMSetup command line.

If no command line properties have been provisioned on the client computer by using Group Policy, CCMSetup searches Active Directory Domain Services for installation properties.

## Group Policy installation

The Group Policy installation method does not support the addition of installation properties to the CCMSetup command line.

If no command line properties have been provisioned on the client computer, CCMSetup searches Active Directory Domain Services for installation properties.

## Manual installation

CCMSetup searches Active Directory Domain Services for installation properties under the following circumstances:

- No command line properties are specified after the CCMSetup.exe command.
- The computer has not been provisioned with installation properties by using Group Policy.

## Logon script installation

CCMSetup searches Active Directory Domain Services for installation properties under the following circumstances:

- No command line properties are specified after the CCMSetup.exe command.
- The computer has not been provisioned with installation properties by using Group Policy.

## Software distribution installation

CCMSetup searches Active Directory Domain Services for installation properties under the following circumstances:

- No command line properties are specified after the CCMSetup.exe command.
- The computer has not been provisioned with installation properties by using Group Policy.

## Installations for clients that cannot access Active Directory Domain Services

These client computers cannot read or access the published installation properties from Active Directory Domain Services.

These clients include:

- Workgroup computers.
- Clients that are assigned to a Configuration Manager site that is not published to Active Directory Domain Services.
- Clients that are installed when they are on the Internet.