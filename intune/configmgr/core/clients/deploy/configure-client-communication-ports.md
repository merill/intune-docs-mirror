---
layout: Conceptual
title: Configure client communication ports - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/configure-client-communication-ports
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
description: Set client communication ports in Configuration Manager.
ms.date: 2021-04-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 12bbced5-03e9-6ae1-5054-5f894460c3bd
document_version_independent_id: 3379f329-92b2-5b37-e5b2-1e977e027989
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/configure-client-communication-ports.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/configure-client-communication-ports
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/configure-client-communication-ports.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: b7e0fbc3-ceff-92e4-657a-9a057f0f45f3
---

# Configure client communication ports - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can change the request port numbers that Configuration Manager clients use to communicate with site systems that use HTTP and HTTPS for communication. Although HTTP or HTTPS is more likely to be already configured for firewalls, client notification that uses HTTP or HTTPS requires more CPU usage and memory on the management point computer than if you use a custom port number. You can also specify the site port number to use if you wake up clients by using traditional wake-up packets.

When you specify HTTP and HTTPS request ports, you can specify both a default port number and an alternative port number. If communication fails with the default port, clients automatically try the alternative port. You can specify port settings for HTTP and HTTPS data communication.

The default values for client request ports are **80** for HTTP traffic and **443** for HTTPS traffic. Change them only if you don't want to use these default values. A typical scenario for using custom ports is when you use a custom website in IIS rather than the default website. If you change the default port numbers for the default website in IIS, and other applications also use the default website, they're likely to fail.

Important

Don't change the port numbers in Configuration Manager without understanding the consequences. For example:

- If you change the port numbers for the client request services as a site configuration, and existing clients aren't reconfigured to use the new port numbers, these clients will be unmanaged.
- Before you configure a non-default port number, make sure that firewalls and all intervening network devices support this configuration. If you will manage clients on the internet, and change the default HTTPS port number of 443, routers and firewalls on the internet might block this communication.

To make sure that clients don't become unmanaged after you change the request port numbers, configure clients to use the new request port numbers. When you change the request ports on a primary site, any attached secondary sites automatically inherit the same port configuration.

## How clients get the port configuration

When the Configuration Manager [site is published](../../servers/deploy/configure/publish-site-data) to Active Directory Domain Services, new and existing clients that can access this information will automatically be configured with their site port settings. You don't need to take further action.

Clients that can't access this information published to Active Directory include:

- Workgroup clients
- Clients from another Active Directory forest
- Clients that are configured for internet-only
- Clients that are currently on the internet.

If you change the default port numbers after you install these clients, reinstall them.

Install any new clients by using one of the following methods:

- Reinstall the clients by using the Client Push Installation Wizard. Client push installation automatically configures clients with the current site port configuration. For more information, see [How to install Configuration Manager clients with client push](deploy-clients-to-windows-computers#BKMK_ClientPush).
- Reinstall the clients by using CCMSetup.exe and the client.msi installation properties of **CCMHTTPPORT** and **CCMHTTPSPORT**. For more information, see [About client installation properties](about-client-installation-properties).
- Reinstall the clients by using a method that searches Active Directory Domain Services for Configuration Manager client installation properties. For more information, see [About client installation properties published to Active Directory Domain Services](about-client-installation-properties-published-to-active-directory-domain-services).

To reconfigure the port numbers for existing clients, you can also use the script **Portswitch.vbs**. Find this script on the installation media in the `SMSSETUP\Tools\PortConfiguration` folder.

Important

For existing and new clients that are currently on the internet, configure the non-default port numbers by using the CCMSetup.exe client.msi properties of **CCMHTTPPORT** and **CCMHTTPSPORT**.

After changing the request ports on the site, when you install new clients with the site-wide client push installation method, they're automatically configured with the current port numbers for the site.

## Configure ports for a site

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Sites** node.
2. Select the primary site to configure.
3. On the **Home** tab of the ribbon, select **Properties**.
4. Switch to the **Ports** tab.

    ![The Ports tab of the site's Properties window](media/site-properties-ports.png)
5. Select a service, and then select the Properties icon to open the **Port Detail** window.

    ![Site properties Port Detail window](media/port-detail.png)
6. Specify the port number and description for the item, and then select **OK**.
7. If you want to use the custom website **SMSWeb** for site systems that run IIS, select **Use custom web site**. For more information, see [Websites for site system servers](../../plan-design/network/websites-for-site-system-servers).
8. Select **OK** to save the configuration and close the site properties window.

Repeat this procedure for all primary sites in the hierarchy.