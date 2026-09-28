---
layout: Conceptual
title: Configure discovery - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/configure-discovery-methods
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
description: Configure discovery methods to find resources to manage from your network, Active Directory, and Microsoft Entra ID.
ms.date: 2022-04-25T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
ms.custom: sfi-ga-nochange
locale: en-us
document_id: 09a88524-a2af-cdb2-630d-86177e245753
document_version_independent_id: b5590ca8-3ce9-c277-e8c3-9c78a69945c1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/configure-discovery-methods.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/configure-discovery-methods
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/configure-discovery-methods.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 0bfc300a-2a49-221a-3471-a32979746cce
---

# Configure discovery - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configure discovery methods to find resources to manage from your network, Active Directory, and Microsoft Entra ID. First enable and then configure each method that you want to use to search your environment. You can also disable a method by using the same procedure that you use to enable it. The only exceptions to this process are Heartbeat Discovery and Server Discovery:

- By default, **Heartbeat Discovery** is already enabled when you install a Configuration Manager primary site. It's configured to run on a basic schedule. Keep Heartbeat Discovery enabled. It makes sure that the discovery data records (DDRs) for devices are up to date. For more information about Heartbeat Discovery, see [About Heartbeat Discovery](about-discovery-methods#bkmk_aboutHeartbeat).
- **Server Discovery** is an automatic discovery method. It finds computers that you use as site systems. You can't configure or disable it.

## Active Directory Forest Discovery

To finish the configuration of Active Directory Forest Discovery, configure settings in the following locations of the Configuration Manager console:

- In the **Discovery Methods** node:

    - Enable this discovery method.
    - Set a polling schedule.
    - Select whether discovery automatically creates boundaries for the Active Directory sites and subnets that it discovers.
- In the **Active Directory Forests** node:

    - Add forests that you want to discover.
    - Enable discovery of Active Directory sites and subnets in that forest.
    - Configure settings that enable Configuration Manager sites to publish their site information to the forest.
    - Assign an account to use as the Active Directory Forest Account for each forest.

Use the following procedures to enable Active Directory Forest Discovery, and to configure individual forests for use with Active Directory Forest Discovery.

### Configure Active Directory Forest Discovery

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Hierarchy Configuration**, and select the **Discovery Methods** node.
2. Select the Active Directory Forest Discovery method for the site where you want to configure discovery.
3. On the **Home** tab of the ribbon, select **Properties**.
4. On the **General** tab of the properties, configure the following settings:

    - Enable the discovery method.
    - Specify options to create site boundaries for discovered locations.
    - Specify a schedule for when discovery runs.
5. Select **OK** to save the configuration.

### Configure a forest for Active Directory Forest Discovery

1. In the **Administration** workspace, expand **Hierarchy Configuration**, and select the **Active Directory Forests** node. If Active Directory Forest Discovery has previously run, you see each discovered forest in the results pane. When this discovery method runs, it discovers the local forest and any trusted forests. Manually add untrusted forests.

    - To configure a previously discovered forest, select the forest in the results pane. In the ribbon, select **Properties** to open the forest properties.
    - To configure a new forest that isn't listed, on the **Home** tab of the ribbon, in the **Create** group, select **Add Forest**. This action opens the **Add Forests** dialog box.
2. On the **General** tab, finish configurations for the forest that you want to discover, and specify the **Active Directory Forest Account**. For more information on this account, see [Accounts](../../../plan-design/hierarchy/accounts#active-directory-forest-account).

    Note

    Active Directory Forest Discovery requires a global account to discover and publish to untrusted forests. If you don't use the computer account of the site server, you can only select a global account.
3. If you plan to let sites publish site data to this forest, on the **Publishing** tab, finish configurations for publishing to this forest.

    Note

    If you let sites publish to a forest, extend the Active Directory schema of that forest for Configuration Manager. The Active Directory Forest Account must have Full Control permissions to the System container in that forest.
4. Select **OK** to save the configuration.

## Active Directory discovery for computers, users, or groups

To configure discovery of computers, users, or groups, start with these common steps:

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Hierarchy Configuration**, and select the **Discovery Methods** node.
2. Select the method for the site where you want to configure discovery.
3. On the **Home** tab of the ribbon, select **Properties**.
4. On the **General** tab of the properties, select the checkbox to enable discovery. Or you can configure discovery now, and then return to enable discovery later.

Then use the information in the following sections to configure the specific discovery methods:

- Active Directory Group Discovery
- Active Directory System Discovery
- Active Directory User Discovery

Note

The information in this section doesn't apply to Active Directory Forest Discovery.

Although each of these discovery methods is independent of the others, they share similar options. For more information about these configuration options, see [Shared options for group, system, and user discovery](about-discovery-methods#bkmk_shared).

Warning

The Active Directory polling by each of these discovery methods can generate significant network traffic. Consider scheduling each discovery method to run at a time when this network traffic doesn't adversely affect business uses of your network.

### Configure Active Directory Group Discovery

1. On the **General** tab of the Active Directory Group Discovery Properties window, select **Add** to configure a discovery scope. Select either **Groups** or **Location**. Then finish the following configurations in the **Add Groups** or **Add Active Directory Location** dialog box:

    1. Specify a **Name** for this discovery scope.
    2. Specify an **Active Directory Domain** or **Location** to search:

        - If you chose **Groups**, specify one or more Active Directory groups to discover.
        - If you chose **Location**, specify an Active Directory container as a location to discover. You can also enable a recursive search of Active Directory child containers for this location.
    3. Specify the **Active Directory Group Discovery Account** that the site uses to search this discovery scope. For more information, see [Accounts](../../../plan-design/hierarchy/accounts#active-directory-group-discovery-account).
    4. Select **OK** to save the discovery scope configuration.
2. Repeat the previous steps for each other discovery scope that you want to define.
3. On the **Polling Schedule** tab, configure both the full discovery polling schedule and delta discovery.
4. On the **Options** tab, configure settings to filter out or exclude stale computer records from discovery. Also configure the discovery of the membership of distribution groups.

    Note

    By default, Active Directory Group Discovery discovers only the membership of security groups.
5. Select **OK** to save the configuration.

### Configure Active Directory System Discovery

1. On the **General** tab of the Active Directory System Discovery Properties window, select the **New** icon ![New icon](media/disc_new_icon.gif) to specify a new Active Directory container. In the **Active Directory Container** dialog box, finish the following configurations:

    1. Type or browse to a location for the **Path**. This value is a valid LDAP path to a container or organizational unit (OU). The site queries this path for resources. For example, `LDAP://CN=Computers,DC=contoso,DC=com`
    2. Specify options that change the search behavior:

        - **Discover objects within Active Directory groups**: The site also looks at the membership of groups in this path.
        - **Recursively search Active Directory child containers**: If you enable this option, the site searches any other containers or OUs within the above path. If you disable this option, the site only searches for resources in the specific path.

            Select subcontainers to exclude from this recursive search. This option helps to reduce the number of discovered objects. Select **Add** to choose the containers under the above path. In the Select New Container dialog box, select a child container to exclude. Select **OK** to close the Select New Container dialog box.

            Tip

            - The list of Active Directory containers in the Active Directory System Discovery Properties window includes a column **Has Exclusions**. When you select containers to exclude, this value is **Yes**.
            - Starting in version 2203, you can exclude subcontainers in untrusted domains for **Active Directory System Discovery** and **Active Directory User Discovery**.
    3. For each location, specify the account to use as the **Active Directory Discovery Account**. For more information, see [Accounts](../../../plan-design/hierarchy/accounts#active-directory-system-discovery-account).

        Tip

        For each specified location, you can configure a set of discovery options and a unique Active Directory Discovery Account.
    4. Select **OK** to save the Active Directory container configuration.
2. On the **Polling Schedule** tab, configure both the full discovery polling schedule and delta discovery.
3. On the **Active Directory Attributes** tab, configure other Active Directory attributes for computers that you want to discover. This tab lists the default object attributes.

    Tip

    For example, your organization uses the **Description** attribute on the computer account in Active Directory. Select **Custom**, and add `Description` as a custom attribute. After this discovery method runs, this attribute shows on the device Properties tab in the Configuration Manager console.
4. On the **Options** tab, configure settings to filter out or exclude stale computer records from discovery.
5. Select **OK** to save the configuration.

### Configure Active Directory User Discovery

1. On the **General** tab of the Active Directory User Discovery Properties window, select the **New** icon ![New icon](media/disc_new_icon.gif) to specify a new Active Directory container. In the **Active Directory Container** dialog box, finish the following configurations:

    1. Specify one or more locations to search.
    2. For each location, specify options that change the search behavior.
    3. For each location, specify the account to use as the **Active Directory Discovery Account**. For more information, see [Accounts](../../../plan-design/hierarchy/accounts#active-directory-user-discovery-account).

        Note

        For each specified location, you can configure a unique set of discovery options and a unique Active Directory Discovery Account.
    4. Select **OK** to save the Active Directory container configuration.
2. On the **Polling Schedule** tab, configure both the full discovery polling schedule and delta discovery.
3. On the **Active Directory Attributes** tab, configure other Active Directory attributes for computers that you want to discover. This tab lists the default object attributes.
4. Select **OK** to save the configuration.

#### Exclude organizational units (OU) from Active Directory User Discovery

Starting in version 2103, you can exclude OUs from Active Directory User Discovery. To exclude an OU:

1. From the Configuration Manager console, go to **Administration** &gt; **Hierarchy Configuration** &gt; **Discovery Methods**.
2. Select **Active Directory User Discovery** then select **Properties** from the ribbon.
3. On the **General** tab of the Active Directory User Discovery Properties window, select the **New** icon to specify a new Active Directory container or **Edit** to change an existing one.
4. In the **Active Directory Container** dialog box, locate the search option named **Select sub containers to be excluded from discovery**.
5. Select **Add** to add an exclusion or **Remove** to remove an existing exclusion.
6. Select **OK** to save the Active Directory container configuration.

Tip

Starting in version 2203, you can exclude subcontainers in untrusted domains for **Active Directory System Discovery** and **Active Directory User Discovery**.

## Microsoft Entra user Discovery

Microsoft Entra user Discovery isn't enabled or configured the same as other discovery methods. Configure it when you onboard the Configuration Manager site to Microsoft Entra ID.

For more information, see [Microsoft Entra user Discovery](about-discovery-methods#azureaddisc).

### Prerequisites for Microsoft Entra user Discovery

To enable and configure this discovery method, [Configure Azure Services](azure-services-wizard) for **Cloud Management**.

If you use Configuration Manager to *create* the Azure app, it configures the app with the necessary permissions.

If you create the app in Azure first, and then *import* it into Configuration Manager, you need to manually configure the app. This configuration includes granting the server app permission to read directory data.

1. Open the [Azure portal](https://portal.azure.com) as a user with *Global Administrator* permissions. Go to **Microsoft Entra ID**, and select **App registrations**. Switch to **All applications** if necessary.

    Important

    The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role and should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions. To learn more, see [Fundamentals of role-based administration for Configuration Manager](../../../understand/fundamentals-of-role-based-administration).
2. Select the target application.
3. In the **Manage** menu, select **API permissions**.

    1. On the **API permissions** panel, select **Add a permission**.
    2. In the **Request API permissions** panel, switch to **APIs my organization uses**.
    3. Search for and select the **Microsoft Graph** API.
    4. Select the **Application permissions** group. Expand **Directory**, and select **Directory.Read.All**.
    5. Select **Add permissions**.
4. On the **API permissions** panel, in the **Grant consent** section, select **Grant admin consent...**. Select **Yes**.

### Configure Microsoft Entra user Discovery

When configuring the **Cloud Management** Azure service:

- On the **Discovery** page of the wizard, select the option to **Enable Microsoft Entra user Discovery**.
- Select **Settings**.
- In the Microsoft Entra user Discovery Settings dialog box, configure a schedule for when discovery occurs. You can also enable delta discovery, which only checks for new or changed accounts in Microsoft Entra ID.

Note

If the user is a federated or synchronized identity, you must use Configuration Manager [Active Directory user discovery](about-discovery-methods#bkmk_aboutUser) as well as Microsoft Entra user discovery. For more information about hybrid identities, see [Define a hybrid identity adoption strategy](/en-us/azure/active-directory/active-directory-hybrid-identity-design-considerations-identity-adoption-strategy).

## Microsoft Entra user Group Discovery

You can discover user groups and members of those groups from Microsoft Entra ID. When the site finds users in Microsoft Entra groups that it hasn't previously discovered, it adds them as new user resources in Configuration Manager. A user group resource record is created when the group is a security group.

### Prerequisites for Microsoft Entra user Group Discovery

- Cloud Management [Azure service](azure-services-wizard)
- Permission to read and search Microsoft Entra groups

### Log files

Use the SMS\_AZUREAD\_DISCOVERY\_AGENT.log for troubleshooting. This log is also shared with Microsoft Entra user discovery. For more information, see [Log files](../../../plan-design/hierarchy/log-files#BKMK_ServerLogs).

### Enable Microsoft Entra user group discovery

To enable discovery on an existing **Cloud Management** Azure service:

1. Go to the **Administration** workspace, expand **Cloud Services**, then select the **Azure Services** node.
2. Select one of your Azure services, then select **Properties** in the ribbon.
3. In the **Discovery** tab, check the box to **Enable Microsoft Entra group Discovery**, then select **Settings**.
4. Select **Add** under the **Discovery Scopes**tab.
    - You can modify the **Polling Schedule** in the other tab.
5. Select one or more user groups. You can **Search**by name.
    - You'll be prompted to sign in to Azure when you select **Search** the first time.
6. Select **OK** when you finish selecting groups.
7. Once discovery finishes running, you can browse your Microsoft Entra user groups in the **Users** node.

To enable discovery when configuring a new **Cloud Management** Azure service:

- On the **Discovery** page of the wizard, select the option to **Enable Microsoft Entra group Discovery**.
- Select **Settings**.
- In the Microsoft Entra group Discovery Settings dialog box, configure your discovery scope and a schedule for when discovery occurs.

## Heartbeat Discovery

Configuration Manager enables the Heartbeat Discovery method when you install a primary site. If you want to use the default schedule of every seven days, there's nothing else to configure. Otherwise, you only have to configure the schedule for how often clients send the Heartbeat Discovery data record to a management point.

Note

If you enable both client push installation and the site maintenance task for **Clear Install Flag** at the same site, set the schedule of Heartbeat Discovery to be less than the **Client Rediscovery period** of the **Clear Install Flag** site maintenance task. By default, this task runs every 21 days. Heartbeat discovery should run more frequently than the task, or clients will unnecessarily reinstall. For more information about site maintenance tasks, see [Maintenance tasks](../../manage/maintenance-tasks).

### Configure the Heartbeat Discovery schedule

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Hierarchy Configuration**, and select the **Discovery Methods** node.
2. Select the **Heartbeat Discovery** method for the site where you want to configure Heartbeat Discovery.
3. On the **Home** tab of the ribbon, select **Properties**.
4. Configure the frequency with which clients submit a Heartbeat discovery data record. Then select **OK** to save the configuration.

## Network Discovery

Before you configure Network Discovery, understand the following topics:

- Available levels of Network Discovery
- Available Network Discovery options
- Limiting Network Discovery on the network

For more information, see [About Network Discovery](about-discovery-methods#bkmk_aboutNetwork).

The following sections provide information about common configurations for Network Discovery. You can configure one or more of these configurations for use during the same discovery run. If you use multiple configurations, plan for the interactions that can affect the discovery results.

For example, you discover all Simple Network Management Protocol (SNMP) devices that use a specific SNMP community name. For the same discovery run, you disable discovery on a specific subnet. When discovery runs, Network Discovery doesn't discover the SNMP devices with the specified community name on the subnet that you've disabled.

### Determine your network topology

You can use a topology-only discovery to map your network. This kind of discovery doesn't discover potential clients. The topology-only Network Discovery relies on SNMP.

When you're mapping your network topology, configure the **Maximum hops** on the **SNMP** tab in the **Network Discovery Properties** dialog box. Just a few hops can help control the network bandwidth that's used when discovery runs. As you discover more of your network, increase the number of hops to gain a better understanding of your network topology.

After you understand your network topology, configure the properties for Network Discovery. These properties help to discover potential clients and their operating systems. Also configure Network Discovery to limit the network segments that it can search.

For more information, see How to determine your network topology

### Network Discovery search options

Configuration Manager supports the following methods to search the network:

- Limit searches by using subnets
- Search a specific domain
- Limit searches by using SNMP community names
- Search a specific DHCP server

#### Limit searches by using subnets

You can configure Network Discovery to search specific subnets during a discovery run. By default, Network Discovery searches the subnet of the server that runs discovery. Any other subnets that you configure and enable apply only to SNMP and DHCP search options. When Network Discovery searches domains, it isn't limited by configurations for subnets.

If you specify one or more subnets on the **Subnets** tab in the **Network Discovery Properties** dialog box, it only searches the subnets that you mark as **Enabled**.

When you disable a subnet, the site excludes it from discovery, and the following conditions apply:

- SNMP-based queries don't run on the subnet.
- DHCP servers don't reply with a list of resources located on the subnet.
- Domain-based queries can discover resources that are located on the subnet.

#### Search a specific domain

You can configure Network Discovery to search a specific domain or set of domains during a discovery run. By default, Network Discovery searches the local domain of the server that runs discovery.

If you specify one or more domains on the **Domains** tab in the **Network Discovery Properties** dialog box, it only searches the domains that you mark as **Enabled**.

When you disable a domain, the site excludes it from discovery, and the following conditions apply:

- Network Discovery doesn't query domain controllers in that domain.
- SNMP-based queries can still run on subnets in the domain.
- DHCP servers can still reply with a list of resources located in the domain.

#### Limit searches by using SNMP community names

You configure Network Discovery to search a specific SNMP community or set of communities during a discovery run. By default, the method configures the **public** community name.

Network Discovery uses community names to gain access to routers that are SNMP devices. A router can supply Network Discovery with information about other routers and subnets that are linked to the first router.

Note

SNMP community names resemble passwords. Network Discovery can get information only from an SNMP device for which you've specified a community name. Each SNMP device can have its own community name, but often the same community name is shared among several devices. Additionally, most SNMP devices have a default community name of **public**. But some organizations delete the **public** community name from their devices as a security precaution.

If you include more than one SNMP community on the **SNMP** tab in the **Network Discovery Properties** dialog box, it searches them in the order in which they're shown. Make sure that the most frequently used names are at the top of the list. This configuration helps to minimize network traffic that the site generates when it tries to contact a device by using different names.

Note

Along with using the SNMP community name, you can specify the IP address or resolvable name of a specific SNMP device. You do this action on the **SNMP Devices** tab in the **Network Discovery Properties** dialog box.

#### Search a specific DHCP server

You can configure Network Discovery to use a specific DHCP server or multiple servers to discover DHCP clients during a discovery run.

Network Discovery searches each DHCP server that you specify on the **DHCP** tab in the **Network Discovery Properties** dialog box. If the server that's running discovery leases its IP address from a DHCP server, you can configure discovery to search that DHCP server. Enable this behavior with the option to **Include the DHCP server that the site server is configured to use**.

Note

To successfully configure a DHCP server in Network Discovery, your environment must support IPv4. You can't configure Network Discovery to use a DHCP server in a native IPv6 environment.

### How to configure Network Discovery

Use the following procedures to first discover only your network topology, and then to configure Network Discovery to discover potential clients by using one or more of the available Network Discovery options.

#### How to determine your network topology

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Hierarchy Configuration**, and select the **Discovery Methods** node.
2. Select the **Network Discovery** method for the site where you want to discover network resources.
3. On the **Home** tab of the ribbon, select **Properties**.

    - On the **General** tab, select the option to **Enable network discovery**. Then select **Topology** from the **Type of discovery** options.
    - On the **Subnets** tab, select the **Search local subnets** option.

        Tip

        If you know the specific subnets that constitute your network, deselect the **Search local subnets** checkbox. Then select the **New** icon ![New icon](media/disc_new_icon.gif), and add the specific subnets that you want to search. For large networks, search only one or two subnets at a time to minimize the use of network bandwidth.
    - On the **Domains** tab, select the option to **Search local domain**.
    - On the **SNMP** tab, select an option from the **Maximum hops** drop-down list. This option specifies how many router hops Network Discovery can take in mapping your topology.

        Tip

        When you first map your network topology, configure just a few router hops to minimize the use of network bandwidth.
4. On the **Schedule** tab, select the **New** icon ![New icon](media/disc_new_icon.gif), and set a schedule for running discovery. The **Duration** is the period of time that Network Discovery has to complete the search for resources. On smaller subnets, an hour may be enough, but searching across an enterprise network with multiple router hops will take longer. If Network Discovery runs out of time, a message is logged in **Netdisc.log**.

    Note

    You can't assign a different discovery configuration to separate Network Discovery schedules. Each time Network Discovery runs, it uses the current discovery configuration.
5. Select **OK** to accept the configurations. Network Discovery runs at the scheduled time.

#### How to configure Network Discovery

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Hierarchy Configuration**, and select the **Discovery Methods** node.
2. Select the **Network Discovery** method for the site where you want to discover network resources.
3. On the **Home** tab of the ribbon, select **Properties**.
4. On the **General** tab, select the option to **Enable network discovery**.

    - Select from the **Type of discovery** options the type of discovery that you want to run.
    - Enable the **Slow network** option for Configuration Manager to make automatic adjustments for low-bandwidth networks.
5. To configure discovery to search subnets, switch to the **Subnets** tab. Then configure one or more of the following options:

    - To run discovery on subnets that are local to the computer that runs discovery, enable the option to **Search local subnets**.
    - To search a specific subnet, make sure that the subnet is listed in **Subnets to search** and has a **Search** value of **Enabled**:

        1. If the subnet isn't listed, select the **New** icon ![New icon](media/disc_new_icon.gif). In the **New Subnet Assignment** dialog box, enter the **Subnet** and **Mask** information, and then select **OK**. By default, a new subnet is enabled for search.
        2. To change the **Search** value for a listed subnet, select it in the list. Then select the **Toggle** icon to switch the value between **Disabled** and **Enabled**.
6. To configure discovery to search domains, switch to the **Domains** tab. Then configure one or more of the following options:

    - To run discovery on the domain of the computer that runs discovery, enable the option to **Search local domain**.
    - To search a specific domain, make sure that the domain is listed in **Domains** and has a **Search** value of **Enabled**:

        1. If the domain isn't listed, select the **New** icon ![New icon](media/disc_new_icon.gif). In the **Domain Properties** dialog box, enter the **Domain** information, and then select **OK**. By default, a new domain is enabled for search.
        2. To change the **Search** value for a listed domain, select it in the list. Then select the **Toggle** icon to switch the value between **Disabled** and **Enabled**.
7. To configure discovery to search specific SNMP community names for SNMP devices, switch to the **SNMP** tab. Then configure one or more of the following options:

    - To add an SNMP community name to the list of **SNMP Community names**, select the **New** icon ![New icon](media/disc_new_icon.gif). In the **New SNMP Community Name** dialog box, specify the **Name** of the SNMP community, and then select **OK**.
    - To remove an SNMP community name, select the community name, and then select the **Delete** icon ![Delete icon](media/disc_delete_icon.gif).
    - To adjust the search order of SNMP community names, select a community name from the list. Then select the **Move Item Up** icon ![Move UP Icon](media/disc_moveup_icon.gif) or the **Move Item Down** icon ![Move Down Icon](media/disc_movedown_icon.gif). When discovery runs, community names are searched in a top-to-bottom order.
    - To configure the maximum number of router hops for use by SNMP searches, select the number of hops from the **Maximum hops** drop-down list.
8. To configure an SNMP device, switch to the **SNMP Devices** tab. If the device isn't listed, select the **New** icon ![New icon](media/disc_new_icon.gif). In the **New SNMP Device** dialog box, specify the IP address or device name of the SNMP device, and then select **OK**.

    Note

    If you specify a device name, Configuration Manager must be able to resolve the NetBIOS name to an IP address.
9. To configure discovery to query specific DHCP servers, switch to the **DHCP** tab. Then configure one or more of the following options:

    - To query the DHCP server on the computer that is running discovery, enable the option to **Always use the site server's DHCP server**.

        Note

        To use this option, the server must lease its IP address from a DHCP server and can't use a static IP address.
    - To query a specific DHCP server, select the **New** icon ![New icon](media/disc_new_icon.gif). In the **New DHCP Server** dialog box, specify the IP address or server name of the DHCP server, and then select **OK**.

        Note

        If you specify a server name, Configuration Manager must be able to resolve the NetBIOS name to an IP address.
10. To configure when discovery runs, switch to the **Schedule** tab. Then select the **New** icon ![New icon](media/disc_new_icon.gif) to set a schedule for running Network Discovery. You can configure multiple recurring schedules, and multiple schedules that have no recurrence.

    Note

    If the **Schedule** tab shows more than one schedule at the same time, Network Discovery runs for all schedules as it's configured at the time indicated in the schedule. This behavior is also true for recurring schedules.
11. Select **OK** to save your configurations.

### How to verify that Network Discovery has finished

The time that Network Discovery requires to finish can vary depending on one or more of the following factors:

- The size of your network
- The topology of your network
- The maximum number of hops that are configured to find routers in the network
- The type of discovery that is being run

Network Discovery doesn't create messages to alert you when it's finished. Use the following procedure to verify when discovery has finished:

1. In the Configuration Manager console, go to the **Monitoring** workspace. Expand **System Status**, and then select the **Status Message Queries** node.
2. Select the **All Status Messages** query.
3. On the **Home** tab of the ribbon, in the **Status Message Queries** group, select **Show Messages**.
4. In the All Status Messages window, select a value from the **Select date and time** drop-down list that includes how long ago the discovery started. Then select **OK** to open the **Configuration Manager Status Message Viewer**.

    Tip

    You can also use the **Specify date and time** option to select a given date and time that you ran discovery. This option is useful when you ran Network Discovery on a given date and want to retrieve messages from only that date.
5. To validate that Network Discovery has finished, search for a status message that has the following details:

    - Message ID: **502**
    - Component: **SMS\_NETWORK\_DISCOVERY**
    - Description: **This component stopped**

    If this status message isn't present, Network Discovery hasn't finished.
6. To validate when Network Discovery started, search for a status message that has the following details:

    - Message ID: **500**
    - Component: **SMS\_NETWORK\_DISCOVERY**
    - Description: **This component started**

    This information verifies that Network Discovery started. If this information isn't present, reschedule Network Discovery.