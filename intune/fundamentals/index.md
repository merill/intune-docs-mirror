---
layout: Landing
title: Fundamentals - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/
summary: Learn about Microsoft Intune architecture, licensing, setup, and shared infrastructure that supports all Intune workloads.
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: fundamentals
description: Get started with Microsoft Intune — architecture, licensing, tenant setup, RBAC, certificates, filters, and platform support.
ms.topic: landing-page
ms.date: 2026-05-04T00:00:00.0000000Z
locale: en-us
document_id: bba07af6-daaa-93e7-c5fd-6ef8851a67e4
document_version_independent_id: bba07af6-daaa-93e7-c5fd-6ef8851a67e4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/index.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: landing
toc_rel: ../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/index.yml
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 208d8ed2-70bc-65a4-9b2c-2ae7a8a51203
---

# Fundamentals

Learn about Microsoft Intune architecture, licensing, setup, and shared infrastructure that supports all Intune workloads.

## Get started

### Overview

- [What is Microsoft Intune?](what-is-intune)
- [Get started with Intune](get-started)
- [Try and evaluate Intune](try-overview)

### How-To Guide

- [Sign up for a free trial](free-trial-sign-up)
- [Sign up or sign in to Intune](account-sign-up)

### Tutorial

- [Walk through the admin center](tutorial-admin-center-walkthrough)

## Set up your tenant

### How-To Guide

- [Set the MDM authority](setup-mdm-authority)
- [Configure a custom domain name](configure-custom-domain)

### Quickstart

- [Create a user](tenant-administration/quickstart-create-user)
- [Create a group](tenant-administration/quickstart-create-group)

### Concept

- [Identity management](core-concepts#identities)

## Plan and deploy

### Concept

- [Planning guide](planning-guide)
- [Architecture overview](architecture)
- [Zero Trust with Intune](zero-trust)

### Deploy

- [Set up Intune (step 1)](deploy-setup-step-1)
- [Protect apps and data (step 2)](deploy-protect-apps-step-2)
- [Set up migration](setup-migration)

## Plans and licensing

### Overview

- [Microsoft Intune licensing](licensing)
- [Microsoft Intune advanced capabilities](advanced-capabilities)

### How-To Guide

- [Assign licenses to users](assign-licenses)
- [Unlicensed admins access](licensing#unlicensed-admin-access)

## Role-based access control

### Overview

- [RBAC overview](role-based-access-control/overview)

### How-To Guide

- [Configure multi admin approval](role-based-access-control/multi-admin-approval)
- [Create a custom role](role-based-access-control/create-custom-role)
- [Assign roles](role-based-access-control/assign-role)
- [Use scope tags](role-based-access-control/scope-tags)

### Reference

- [Built-in role permissions](role-based-access-control/ref-built-in-roles)

## Assignment filters

### Overview

- [Filters overview](filters/overview)

### Reference

- [Supported workloads](filters/ref-supported-workloads)
- [Device properties reference](filters/ref-device-properties)

### How-To Guide

- [Troubleshoot filters](filters/troubleshoot)

## Certificate infrastructure

### Overview

- [Certificate connectors overview](certificates/connector/overview)

### Concept

- [Certificate connectors](certificates/connector/certificate-connectors)
- [SCEP infrastructure](certificates/scep-infrastructure)

### How-To Guide

- [Connector prerequisites](certificates/connector/prerequisites)
- [Set up the certificate connector](certificates/connector/setup-connector)
- [Use third-party CAs with SCEP](certificates/third-party-ca-scep)

## Platform support and endpoints

### Reference

- [Supported operating systems](ref-supported-platforms)
- [AOSP supported devices](aosp-supported-devices)
- [Network endpoints](endpoints)
- [U.S. government endpoints](endpoints-us-government)

### Deploy

- [iOS/iPadOS platform guide](platform-guide-ios-ipados)
- [Android platform guide](platform-guide-android)
- [macOS platform guide](platform-guide-macos)