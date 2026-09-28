---
layout: Conceptual
title: How to Define the Create Deployment Type Wizard XML File - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-define-the-create-deployment-type-wizard-xml-file
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
description: To define the custom create deployment type wizard XML file, create an XML file based on the schema.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: dfa797dd-eed0-8549-243b-0948d5cff1cd
document_version_independent_id: 2d2fd9c5-5fb9-08af-2ce4-605c3b233fe5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-define-the-create-deployment-type-wizard-xml-file.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-define-the-create-deployment-type-wizard-xml-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-define-the-create-deployment-type-wizard-xml-file.md
cmProducts: []
platformId: 03650b27-1ffa-9bda-e48f-7021532c6102
---

# How to Define the Create Deployment Type Wizard XML File - Configuration Manager | Microsoft Learn

To define the custom create deployment type wizard XML file, create an XML file based on the `https://schemas.microsoft.com/SystemsManagementServer/2005/03/ConsoleFramework` schema. The XML file for the Create Application Wizard should be named CreateDeploymentWizard\_&lt;*TechnologyID*&gt;.xml.

### To define the create deployment type wizard XML file

1. Create a Create Deployment Type Wizard XML file.

    The following example from the RDP sample project demonstrates how to define the Deployment Type Wizard XML file.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <SmsFormData xmlns="https://schemas.microsoft.com/SystemsManagementServer/2005/03/ConsoleFramework" FormatVersion="1">
      <Form Id="{FD19DEC6-81ED-447B-9D88-3AAD7DE499F1}" CustomData="CreateDT" FormType="PropertySheet" ForceRefresh="true">
        <Pages>
          <Page Assembly="AdminUI.DeploymentType.Rdp.dll" Namespace="RdpTechnology.AdminConsole" VendorId="Partner Company Name" Id="{6802BC91-30EF-49A5-80F6-D4902CD5181C}" Type="RdpDeploymentTechnologyPageControl" />
        </Pages>
      </Form>
    </SmsFormData>
    ```