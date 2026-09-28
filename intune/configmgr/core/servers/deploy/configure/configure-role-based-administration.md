---
layout: Conceptual
title: Configure role-based administration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/configure-role-based-administration
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
description: Combine security roles, security scopes, and assigned collections to define the administrative scope for each administrative user.
ms.date: 2025-07-17T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 8298c96c-4449-7066-a2a7-2623f8be8016
document_version_independent_id: d43800ff-eae7-1c77-5972-efc027d304d9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/configure-role-based-administration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/configure-role-based-administration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/configure-role-based-administration.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d1a90773-57ab-325b-32bf-1466e5aff764
---

# Configure role-based administration - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

In Configuration Manager, role-based administration combines security roles, security scopes, and assigned collections to define the administrative scope for each administrative user. An administrative scope includes the objects that an administrative user can view in the Configuration Manager console and the tasks related to those objects that they have permission to do.

If you're not yet familiar with these concepts, see [Fundamentals of role-based administration](../../../understand/fundamentals-of-role-based-administration).

Use the information in this article to create and configure role-based administration and related security settings.

Note

The procedures in this article assume that your administrative user is in a security role with the required permissions. For example, the **Full Administrator** or **Security administrator** roles.

Tip

Use the [Role-based administration and auditing tool](../../../support/rbaviewer) to help with the following actions:

- Model permissions for a new role that you want to create.
- Audit all existing administrative users, collections, and security scopes.
- Audit a specific user

## Create custom security roles

Configuration Manager provides several [built-in security roles](../../../understand/fundamentals-of-role-based-administration#security-roles). You can't change the permissions of the built-in roles. If you require other roles, create a custom one. You might create a custom role to grant administrative users other permissions that they require and aren't included in a built-in role. By using a custom security role, you can assign them the least required permissions. A custom role can help you avoid assigning a security role that grants more permissions than they require.

### How to create custom security roles

In the Configuration Manager console, go to the **Administration** workspace. Expand **Security**, and then select the **Security Roles** node. Then use one of the following processes to create a new security role:

#### Create a new custom security role by copying a built-in role

1. Select an existing security role to use as the source for the new role.
2. On the **Home** tab of the ribbon, in the **Security Role** group, select **Copy**. This action creates a copy of the source security role.
3. In the Copy Security Role wizard, specify a **Name** for the new custom security role. The maximum length is 256 characters.
4. Optional but recommended, specify a **Description** to summarize the purpose of this custom security role. The maximum length is 512 characters.
5. Under **Permissions**, expand each object type to display the available permissions.
6. To change a permission, select the drop-down list, and choose either **Yes** or **No**.

Caution

When you configure a custom security role, only grant permissions that are required by the users assigned to this role. For example, the **Modify** permission for the **Security Roles** object allows assigned users to edit any accessible security role, even if they aren't assigned to that security role.
7. After you configure the permissions, select **OK** to save the new security role.

#### Import a security role that was exported from another Configuration Manager hierarchy

Important

Only import custom security role configuration files from a trusted source. When you export a custom security role, save it in a secure location. The XML files aren't digitally signed.

1. On the **Home** tab of the ribbon, in the **Create** group, choose **Import Security Role**.
2. Specify the XML file that contains the exported security role configuration. Select **Open** to complete the procedure and create the security role.
3. After you import a custom security role, open its **Properties**. View the permissions to confirm they include the least required permissions for this role. Change any permissions that aren't required in this environment.

Note

You can't export built-in security roles.

## Configure security roles

You can modify the permissions for a custom security role, but you can't modify the built-in security roles.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Security**, and then select the **Security Roles** node.
2. Select the custom security role that you want to modify or view.
3. On the **Home** tab of the ribbon, in the **Properties** group, select **Properties**.
4. On the **General** tab of the properties window, change the **Name** or **Description** if necessary.
5. On the **Administrative Users** tab, view the users that are associated with this role. To change the assignment, go to the properties of the administrative user.
6. On the **Permissions** tab, expand each object type to display the available permissions.
7. To change a permission, select the drop-down list, and then choose either **Yes** or **No**.

Caution

When you configure a custom security role, only grant permissions that are required by the users assigned to this role. For example, the **Modify** permission for the **Security Roles** object allows assigned users to edit any accessible security role, even if they aren't assigned to that security role.
8. When you're done, select **OK** to save the custom security role.

## Configure security scopes for an object

Manage security scopes from the securable object, not from the security scope. The only properties you can change on a custom security scope is the name and description. You can't modify the two built-in scopes. To change the name and description of a custom scope, you need the **Modify** permission for the **Security Scopes** object.

When you create a new object in Configuration Manager, it's associated with each security scope that's associated with the security roles of the account used to create the object. This behavior occurs when those security roles provide the **Create** permission or **Set Security Scope** permission. After you create an object, you can change the security scopes and assign it to multiple scopes.

For example, you're assigned a security role that grants you permission to create a new boundary group. That role is associated with the **Admins** security scope. When you create a new boundary group, you've no option to assign specific security scopes. The **Admins** security scope is automatically assigned to the new boundary group. After you save the new boundary group, you can edit the security scopes for the boundary group.

For more information on how to add a scope for a user, see Modify the administrative scope of an administrative user.

### How to create a custom security scope

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Security**, and then select the **Security Scopes** node.
2. On the **Home** tab of the ribbon, in the **Create** group, select **Create Security Scope**.
3. In the Create Security Scope window, specify a **Security scope name**. The maximum length is 256 characters.
4. Optional but recommended, specify a **Description** to summarize the purpose of this custom security scope. The maximum length is 512 characters.
5. Select or remove administrative user assignments. You can change these after you create the security scope.
6. To save the custom security scope, select **OK**.

### How to configure security scopes for an object

1. In the Configuration Manager console, select an object that supports being assigned to a security scope. For the list of supported objects, see [Fundamentals of role-based administration - Security scopes](../../../understand/fundamentals-of-role-based-administration#security-scopes).
2. On the **Home** tab of the ribbon, in the **Classify** group, select **Set Security Scopes**.

    For a folder, go to the **Folder** tab of the ribbon. In the **Actions** group, select **Set Security Scopes**.

    Note

    An item is searchable in folders outside of a user's security scope if that user shares a security scope with the person who created the object.
3. In the **Set Security Scopes** window, select or clear the security scopes for this object. Select at least one security scope.
4. Select **OK** to save the assigned security scopes.

## Configure collections to manage security

There are no procedures to configure collections for role-based administration. Collections don't have a role-based administration configuration. Instead, you assign collections to an administrative user. To determine the actions that an administrative user can do to a collection and its members, view the permissions for the **Collection** object type on the security role.

When an administrative user has permissions to a collection, they also have permissions to collections that are limited to that collection. For example, your organization uses a collection named **All Desktops**. There's also a collection named **All North America Desktops** that's limited to the **All Desktops** collection. If an administrative user has permissions to **All Desktops**, they have the same permissions to the **All North America Desktops** collection.

An administrative user can't use the **Delete** or **Modify** permissions on a collection that's directly assigned to them. They can use these permissions on the collections that are limited to that collection. In the previous example, the administrative user can delete or modify the **All North America Desktops** collection, but they can't delete or modify the **All Desktops** collection.

## Create a new administrative user

To grant individuals or members of a security group access to manage Configuration Manager, create an administrative user. Specify a Windows account of the user or user group. Assign each administrative user to at least one security role and one security scope. You can also assign collections to limit the administrative scope of the user or group.

Note

If the administrative user is a member of the **Protected Users** global security group, they can only run the console for 4 hours at a time. After 4 hours, their kerberos authorization expires and can't be renewed. The console automatically closes and any unsaved work in progress is lost.

Members of the **Protected Users** security group should monitor their time in the console and save or close any work in progress before 4 hours. After closing the console, re-launch it to continue working.

For more information regarding the **Protected Users** security group, see [Protected Users security group](/en-us/windows-server/security/credentials-protection-and-management/protected-users-security-group) and [Guidance about how to configure protected accounts](/en-us/windows-server/identity/ad-ds/manage/how-to-configure-protected-accounts).

### How to create a new administrative user

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Security**, and then select the **Administrative Users** node.
2. On the **Home** tab of the ribbon, in the **Create** group, select **Add User or Group**.
3. Select **Browse**, and then select the user account or group to use for this new administrative user in Configuration Manager.

    Note

    For console-based administration, you can only specify domain users or domain security groups as an administrative user.
4. For the **Associated security roles**, select **Add** to open a list of the available security roles. Select one or more security roles, and then select **OK**.
5. Choose one of the following options to define the securable object behavior for the new user:

    - **All instances of the objects that are related to the assigned security roles**: This option has the following behaviors:

        - Security scope: **All**
        - Collections: **All Systems** and **All Users and User Groups**
        - The security roles that you assign to the user define their access to objects.
        - New objects that this user creates are assigned to the **Default** security scope.
    - **Only the instances of objects that are assigned to the specified security scopes and collections**: This option has the following behaviors:

        - Security scope: **Default**
        - Collections: **All Systems** and **All Users and User Groups**
        - These defaults maybe different, as the actual security scopes and collections are limited to those that are associated with the account that you use to create the administrative user.
        - **Add** or **Remove** security scopes and collections to customize the administrative scope of this user.

    Important

    After you create the user, view its properties to select a third option, **Associate assigned security roles with specific security scopes and collections**. For more information, see Modify the administrative scope of an administrative user.
6. Select **OK** to close the window and create the administrative user.

## Modify the administrative scope of an administrative user

You can modify the administrative scope of an administrative user by adding or removing security roles, security scopes, and collections that are associated with the user. Each administrative user must be associated with at least one security role and one security scope. You might have to assign one or more collections to the administrative scope of the user. Most security roles interact with collections and don't function correctly without an assigned collection.

When you modify an administrative user, you can change the behavior for how securable objects are associated with the assigned security roles. The three behaviors that you can select are as follows:

- **All instances of the objects that are related to the assigned security roles**: This option associates the administrative user with the **All** scope, and the **All Systems** and **All Users and User Groups** collections. The security roles that are assigned to the user define access to objects.
- **Only the instances of objects that are assigned to the specified security scopes and collections**: This option associates the administrative user to the same security scopes and collections that are associated to the account you use to configure the administrative user. This option supports the addition or removal of security roles and collections to customize the administrative scope of the administrative user.
- **Associate assigned security roles with specific security scopes and collections**: This option lets you create specific associations between individual security roles and specific security scopes and collections for the user.

    Note

    This option is available only when you modify the properties of an administrative user.

The current configuration for the securable object behavior changes the process that you use to assign additional security roles. Use the following procedures that are based on the different options for securable objects to help you manage an administrative user.

Use the following procedure to view and manage the configuration for securable objects for an administrative user.

### To view and manage the securable object behavior for an administrative user

1. In the Configuration Manager console, choose **Administration**.
2. In the **Administration** workspace, expand **Security**, and then choose **Administrative Users**.
3. Select the administrative user that you want to modify.
4. On the **Home** tab, in the **Properties** group, choose **Properties**.
5. Choose the **Security Scopes** tab to view the current configuration for securable objects for this administrative user.
6. To modify the securable object behavior, select a new option for securable object behavior. After you change this configuration, see the appropriate procedure for further guidance to configure security scopes and collections, and security roles for this administrative user.
7. Choose **OK** to complete the procedure.

Use the following procedure to modify an administrative user that has the securable object behavior set to **All instances of the objects that are related to the assigned security roles**.

### For option: All instances of the objects that are related to the assigned security roles

1. In the Configuration Manager console, choose **Administration**.
2. In the **Administration** workspace, expand **Security**, and then choose **Administrative Users**.
3. Select the administrative user that you want to modify.
4. On the **Home** tab, in the **Properties** group, choose **Properties**.
5. Choose the **Security Scopes** tab to confirm that the administrative user is configured for **All instances of the objects that are related to the assigned security roles**.
6. To modify the assigned security roles, choose the **Security Roles** tab.

    - To assign additional security roles to this administrative user, choose **Add**, check the box for each additional security role that you want to assign, and then choose **OK**.
    - To remove security roles, select one or more security roles from the list, and then choose **Remove**.
7. To modify the securable object behavior, choose the **Security Scopes** tab and choose a new option for the securable object behavior. After you change this configuration, see the appropriate procedure for further guidance to configure security scopes and collections, and security roles for this administrative user.

    Note

    When the securable object behavior is set to **All instances of the objects that are related to the assigned security roles**, you can't add or remove specific security scopes and collections.
8. Choose **OK** to complete this procedure.

Use the following procedure to modify an administrative user that has the securable object behavior set to **Only the instances of objects that are assigned to the specified security scopes and collections**.

### For option: Only the instances of objects that are assigned to the specified security scopes and collections

1. In the Configuration Manager console, choose **Administration**.
2. In the **Administration** workspace, expand **Security**, and then choose **Administrative Users**.
3. Select the administrative user that you want to modify.
4. On the **Home** tab, in the **Properties** group, choose **Properties**.
5. Choose the **Security Scopes** tab to confirm that the user is configured for **Only the instances of objects that are assigned to the specified security scopes and collections**.
6. To modify the assigned security roles, choose the **Security Roles** tab.

    - To assign additional security roles to this user, choose **Add**, check the box for each additional security role that you want to assign, and then choose **OK**.
    - To remove security roles, select one or more security roles from the list, and then choose **Remove**.
7. To modify the security scopes and collections that are associated with security roles, choose the **Security Scopes** tab.

    - To associate new security scopes or collections with all security roles that are assigned to this administrative user, choose **Add** and select one of the four options. If you select **Security Scope** or **Collection**, check the box for one or more objects to complete that selection, and then choose **OK**.
    - To remove a security scope or collection, choose the object, and then choose **Remove**.
8. Choose **OK** to complete this procedure.

Use the following procedure to modify an administrative user that has the securable object behavior set to **Associate assigned security roles with specific security scopes and collections**.

### For option: Associate assigned security roles with specific security scopes and collections

1. In the Configuration Manager console, choose **Administration**.
2. In the **Administration** workspace, expand **Security**, and then choose **Administrative Users**.
3. Select the administrative user that you want to modify.
4. On the **Home** tab, in the **Properties** group, choose **Properties**.
5. Choose the **Security Scopes** tab to confirm that the administrative user is configured for **Associate assigned security roles with specific security scopes and collections**.
6. To modify the assigned security roles, choose the **Security Roles** tab.

    - To assign additional security roles to this administrative user, choose **Add**. On the **Add Security Role** dialog box, select one or more available security roles, choose **Add**, and select an object type to associate with the selected security roles. If you select **Security Scope** or **Collection**, check the box for one or more objects to complete that selection, and then choose **OK**.

        Note

        You must configure at least one security scope before the selected security roles can be assigned to the administrative user. When you select multiple security roles, each security scope and collection that you configure is associated with each of the selected security roles.
    - To remove security roles, select one or more security roles from the list, and then choose **Remove**.
7. To modify the security scopes and collections that are associated with a specific security role, choose the **Security Scopes** tab, select the security role, and then choose **Edit**.

    - To associate new objects with this security role, choose **Add**, and select an object type to associate with the selected security roles. If you select **Security Scope** or **Collection**, check the box for one or more objects to complete that selection, and then choose **OK**.

        Note

        You must configure at least one security scope.
    - To remove a security scope or collection that is associated with this security role, select the object, and then choose **Remove**.
    - When you have finished modifying the associated objects, choose **OK**.
8. Choose **OK** to complete this procedure.

Caution

When a security role grants administrative users the collection deployment permission, those administrative users can distribute objects from any security scope for which they have object **read** permissions, even if that security scope is associated with a different security role.

## Automate with Windows PowerShell

You can use the following PowerShell cmdlets to automate some of these tasks:

Manage administrative users:

- [Get-CMAdministrativeUser](/en-us/powershell/module/configurationmanager/Get-CMAdministrativeUser): Get an administrative user object.
- [New-CMAdministrativeUser](/en-us/powershell/module/configurationmanager/New-CMAdministrativeUser): Create a new administrative user.
- [New-CMAdministrativeUserPermission](/en-us/powershell/module/configurationmanager/New-CMAdministrativeUserPermission): Create a permissions object.
- [Remove-CMAdministrativeUser](/en-us/powershell/module/configurationmanager/Remove-CMAdministrativeUser): Remove an administrative user.

Manage roles and scopes on users:

- [Add-CMSecurityRoleToAdministrativeUser](/en-us/powershell/module/configurationmanager/Add-CMSecurityRoleToAdministrativeUser): Add a security role to a user or group.
- [Remove-CMSecurityRoleFromAdministrativeUser](/en-us/powershell/module/configurationmanager/Remove-CMSecurityRoleFromAdministrativeUser): Remove the association between a security role and an administrative user.
- [Add-CMSecurityScopeToAdministrativeUser](/en-us/powershell/module/configurationmanager/Add-CMSecurityScopeToAdministrativeUser): Add a security scope to a user or group.
- [Remove-CMSecurityScopeFromAdministrativeUser](/en-us/powershell/module/configurationmanager/remove-cmsecurityscopefromadministrativeuser): Remove the association between a security scope and an administrative user.

Manage security roles:

- [Copy-CMSecurityRole](/en-us/powershell/module/configurationmanager/Copy-CMSecurityRole): Create a custom security role.
- [Export-CMSecurityRole](/en-us/powershell/module/configurationmanager/Export-CMSecurityRole): Export a security role to an XML file.
- [Get-CMSecurityRole](/en-us/powershell/module/configurationmanager/Get-CMSecurityRole): Get a security role.
- [Import-CMSecurityRole](/en-us/powershell/module/configurationmanager/Import-CMSecurityRole): Import a security role from an XML file.
- [Remove-CMSecurityRole](/en-us/powershell/module/configurationmanager/Remove-CMSecurityRole): Remove custom security roles.
- [Set-CMSecurityRole](/en-us/powershell/module/configurationmanager/Set-CMSecurityRole): Change configuration settings of a security role.

Manage permissions on security roles:

- [Get-CMSecurityRolePermission](/en-us/powershell/module/configurationmanager/Get-CMSecurityRolePermission): Get the permissions for a security role.
- [Set-CMSecurityRolePermission](/en-us/powershell/module/configurationmanager/Set-CMSecurityRolePermission): Configure a security role with specific permissions.

Manage security scopes:

- [Get-CMSecurityScope](/en-us/powershell/module/configurationmanager/Get-CMSecurityScope): Get a security scope.
- [New-CMSecurityScope](/en-us/powershell/module/configurationmanager/New-CMSecurityScope): Create a security scope.
- [Remove-CMSecurityScope](/en-us/powershell/module/configurationmanager/Remove-CMSecurityScope): Remove a security scope.
- [Set-CMSecurityScope](/en-us/powershell/module/configurationmanager/Set-CMSecurityScope): Configure a security scope.

Manage object security scope:

- [Add-CMObjectSecurityScope](/en-us/powershell/module/configurationmanager/Add-CMObjectSecurityScope): Add a security scope to an object.
- [Get-CMObjectSecurityScope](/en-us/powershell/module/configurationmanager/Get-CMObjectSecurityScope): Get the security scope for a Configuration Manager object.
- [Remove-CMObjectSecurityScope](/en-us/powershell/module/configurationmanager/Remove-CMObjectSecurityScope): Remove a security scope from a Configuration Manager object.