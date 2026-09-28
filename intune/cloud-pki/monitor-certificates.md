---
layout: Conceptual
title: Monitor issued PKI certificates with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/cloud-pki/monitor-certificates
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- certificates
ms.reviewer: wicale
ms.subservice: suite
description: Monitor reports for certificates issued via Microsoft Intune cloud PKI.
ms.date: 2024-12-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: c2ced377-aa8e-cf87-84b5-8be72858eb1a
document_version_independent_id: c2ced377-aa8e-cf87-84b5-8be72858eb1a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/cloud-pki/monitor-certificates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: cloud-pki/monitor-certificates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/cloud-pki/monitor-certificates.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 9ae511b8-80b4-f388-5f2a-d8fa10ba430c
---

# Monitor issued PKI certificates with Microsoft Intune - Microsoft Intune | Microsoft Learn

Monitor the certificates deployed to Intune-managed devices by the Microsoft Cloud PKI service. Every Microsoft Cloud PKI issuing CA has a dashboard that shows the number of deployed certificates, including:

- Active certificates
- Expired certificates
- Revoked certificates
- Total number of issued certificates

You can also view SCEP certificates issued by Cloud PKI.

This article describes how to monitor certificates, revoke certificates, and view SCEP certificate reports in the Microsoft Intune admin center.

## View issued certificates

To view issued certificates, go to **Devices** &gt; **Monitor**, and then select **Certificates**.

![Admin center Monitor page with Certificates option highlighted.](media/monitor-certificates/monitor-certificates-cloud-pki.png)

## Monitor Cloud PKI issuing CA

Each Cloud PKI issuing CA has a monitoring dashboard. Select **View all certificates** to view all issued certificates. Certificate report details should be available within 24 hours of the certificate being successfully issued to the device.

![Certificate count dashboard for Microsoft Cloud PKI in admin center.](media/monitor-certificates/intune-certificate-count-cloud-pki.png)

From here, you can also manually revoke an issued leaf certificate.

1. Select **View all certificates**.
2. Select the **Subject name** of the certificate you want to revoke.
3. On the certificate's details page, select **Revoke**.

Tip

When you manually revoke a certificate from a user or device that has an active SCEP certificate profile assignment, then on the next device check-in a new certificate request is made by the device. A certificate is also issued. If you don't want to reissue a certificate to the device, remove all SCEP policy assignments.

## View SCEP certificate profile report

Go to **Devices** &gt; **Manage devices** &gt; **Configuration**. Select the SCEP profile, and then select **Certificates**.

![SCEP certificate profile report in the admin center.](media/monitor-certificates/scep-certificate-profile.png)