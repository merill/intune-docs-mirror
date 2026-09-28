---
layout: Conceptual
title: How to Define the Create Application Wizard XML File - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-define-the-create-application-wizard-xml-file
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
description: How to create a custom deployment technology XML File for the Create Application Wizard/.
locale: en-us
document_id: 89f44c6d-0a82-8477-f06b-14a80ed81e5a
document_version_independent_id: df615a16-9fb2-2679-0ca1-8b6fb206e85d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-define-the-create-application-wizard-xml-file.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-define-the-create-application-wizard-xml-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-define-the-create-application-wizard-xml-file.md
cmProducts: []
platformId: 99174b83-7b52-9ac6-69e8-bd1f4cf8dbfb
---

# How to Define the Create Application Wizard XML File - Configuration Manager | Microsoft Learn

To define the custom deployment technology XML file, create an XML file based on the `https://schemas.microsoft.com/SystemsManagementServer/2005/03/ConsoleFramework` schema. The XML file for the Create Application Wizard should be named, CreateApp\_&lt;*TechnologyID*&gt;.xml.

### To define the create application wizard XML file

1. Create a Create Application Wizard XML file.

    The following example from the RDP sample project shows how to define the Create Application Wizard XML file. Wizards aren't extensible for the UI. However, by creating this custom deployment technology XML, the contents of the wizard now include the ability to create an RDP deployment type.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <SmsFormData xmlns="https://schemas.microsoft.com/SystemsManagementServer/2005/03/ConsoleFramework" FormatVersion="1">
      <Form Id="{FD19DEC6-81ED-447B-9D88-3AAD7DE499F1}" CustomData="CreateApp" FormType="PropertySheet" ForceRefresh="true">
        <Pages>
          <Page Assembly="AdminUI.DeploymentType.Rdp.dll" Namespace="RdpTechnology.AdminConsole" VendorId="Partner Company Name" Id="{6802BC91-30EF-49A5-80F6-D4902CD5181C}" Type="RdpDeploymentTechnologyPageControl" />
        </Pages>
      </Form>
    </SmsFormData>
    ```