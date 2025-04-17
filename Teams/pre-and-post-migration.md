---
title: Helpful tips during a ACM migration
author: surbhigupta12
ms.author: surbhigupta
manager: prkosh
ms.topic: how-to
audience: admin
ms.service: msteams
ms.subservice: teams-apps
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - M365-collaboration
  - Tier1
search.appverid: MET150
ms.date: 02/10/2025
ms.reviewer: nguyenb
description: Tips and tricks for ACM migration.
f1.keywords:
- NOCSH
ms.localizationpriority: high
appliesto: 
  - Microsoft Teams
ms.custom: seo-marvel-apr2020
---

# Important tips and triks during ACM migration

> It is recommended customers follow these steps during self-serve migration to check pre- and post- ACM migration health.

## Pre-migration

### Summary

> App centric management simplifies the process of allowing apps for your users and groups. ACM migration involves preserving the users and apps allowed in your App permission policies; you can also add or exclude users.

> In summary, you will:

1. Export your app catalog and note your allowed apps.
1. Review your permission policies and note your allowed/blocked apps.
1. Identify the users allowed for each app through your permission policies.
1. Reassign those users in the App centric management.

#### Step 1: Export app catalog and your allowed apps

1. Start with the Manage Apps page. Export the full list of apps in the catalog as a CSV file, including each app’s allowed/blocked App status. The allow/block status determines whether the app is available to everyone or no one, respectively. This status is used in the following steps to narrow down your users. For more details, see [Export app catalog as CSV](https://learn.microsoft.com/en-us/microsoftteams/manage-apps#export-app-catalog-as-csv).
 
> :::image type="content" source="media/step1–export-app-catalog.png" alt-text="Screenshot showing the export App catalog.":::

#### Step 2: Review your permission policies and note your allowed/blocked apps

Review your permission policies. You are likely reading this document because you have more than 1 permission policy.

Retrieve list of permission policies 
UI
1. Navigate to Teams admin center > Manage apps > Permission policies 
1. Open each of the permission policies and note the apps allowed or blocked through each one. 

PS cmdlet
1. Run:  Get-CsTeamsAppPermissionPolicy Get-CsTeamsAppPermissionPolicy
2. Interpreting results: 

> :::image type="content" source="media/step2–interpret-results.png" alt-text="Screenshot showing the export App catalog.":::

Response legend:

* Allowed app list with a list of apps = list of apps allowed, all others are blocked.
* Allowed app list with empty list of apps = all apps are blocked.
* Blocked app list with empty list of apps = all apps allowed.
* Blocked app list with a list of apps = apps are blocked and all others are allowed.

In the example above, there are three policies in the tenant: Global, Test Policy, Test 2.

Global:
1. Microsoft apps (Default Catalog Apps): com.microsoft.teamspace.tab.vsts, cd2d8695-bdc9-4d8e-9620-cc963ed81f41, com.microsoft.teamspace.tab.planner, a6b63365-31a4-4f43-92ec-710b71557af9...(more) are allowed, the rest are blocked (Allowed app list)
1. Third party apps (Global Catalog Apps) 3 apps are allowed, the rest are blocked (Allowed App list) 
1. Private Catalog Apps (Custom Apps) - All allowed (Blocked app list is empty)

Retrieve allowed apps in each permission policy
PS cmdlet 
In the example above, not all default apps are shown in the response. To see all of them, you need to assign a variable to the result, example: 
$msftApps = Get-CsTeamsAppPermissionPolicy -Identity "Global" | Select-Object -ExpandProperty DefaultCatalogApps
$msftApps.id

Filter out blocked apps
So far we collected all apps that are allowed to somebody in the tenant. We need to know who the app is allowed for.

Merge it with export from Manage apps page and anything that is blocked in Manage apps will be blocked no matter what the policy assignment might return. 

### Step 3: Identify users allowed for each app 
Get list of users assigned to policy 
There is no Powershell command for it. But there is an alternative way in TAC before migration.

Go to TAC - https://admin.teams.microsoft.com/
Go to Manage Users page

> :::image type="content" source="media/step3-manage-users-page.png" alt-text="":::
>
> For timelines, see [Message Center post MC688930](https://admin.microsoft.com/Adminportal/Home#/MessageCenter/:/messages/MC688930) or [Microsoft 365 roadmap item 151829](https://www.microsoft.com/en-US/microsoft-365/roadmap?filters=&searchterms=151829).
>
> If you see policies on the [permission policies page](https://admin.teams.microsoft.com/policies/app-permission), continue to [use app permission policies](teams-app-permission-policies.md) or migrate to this feature on your own.

With the introduction of app centric management functionality, admins have two methods to control the access and availability of apps and copilot agents.

* Continue to [use permission policies](teams-app-permission-policies.md).
* Use the feature if already auto-migrated or [manually migrate to app centric management](#migrate-to-app-centric-management). It replaces app permission policies.

This functionality lets you specify which users and groups can use each app or a copilot agent and you can control it on a per-app basis.

Whatever method your use, you can manage access to apps for individual users, supported groups, or everyone in the organization. You have complete control over who can or can't add apps in your organization. You can also control the access to new apps that we publish to Teams app store.

## How is app centric management different than permission policy

Previously, when using permission policies, you determined access to apps using the following three settings:

* Org-wide app setting for third party apps: It applies at an org-level and controls if all third party apps are available for every user or not.
* App status: It applies at an app-level as allow or block and controls if it's available to any user or not.
* Permission policy: It applies at a user-level and controls if a specific user is allowed to use an app or not.

App centric management feature simplifies these settings. Each app contains its access definition using a list of users and groups that you assign to it. It lets you manage each app individually based on your user's needs and organization's compliance and risk posture.

When using this functionality, you determine access to apps using one of the following options for each app:

| New option | Who gets the app | How does it map with previous settings |
|------------|------------------|----------------------------------------|
| `Everyone` | Available to all org users, new users, and guests | Same effect as allowing an app and global (Org-wide default) app permission policy allowing all users to use it. |
| `Specific users or groups` | Only the users and groups that you select can use the app. The supported group types are security groups, Microsoft 365 groups, dynamic user membership groups, nested groups, and the distribution lists. | Same as using a custom app permission policy to restrict the use of app to selected users or groups. |
| `No one` | Not available to any user | Same as a blocked app. |

The method to allow users access to an app changes with this functionality. In the past, to allow access to a user, you'd add the app as an allowed app in a policy and assign that policy to the user. Using this functionality, you just modify the availability of an app to let selected users use it. Also, you don't have to create multiple policies for different combinations of apps and allowed users.

## Migrate to app centric management

> [!IMPORTANT]
> Starting from April 2025, tenants are automatically migrated to app centric management. After the migration, you won't have access to the migration wizard. However, until the migration is complete, you can use the wizard and have the option to complete the migration manually. If you've begun the wizard but have not completed it, your tenant can still be automatically migrated during the migration period. For more details about when your tenant can be auto-migrated, see [Message Center post MC688930](https://admin.microsoft.com/Adminportal/Home#/MessageCenter/:/messages/MC688930).

Previously, we automatically migrated organizations that weren't using any custom policies. Admins can now do an on-demand migration. Understand the difference between the two types of migration.

| Type of migration | Who does it   | Requirement                             | How is it done                        |
|-------------------|---------------|-----------------------------------------|---------------------------------------|
| Assisted          | Administrator | Org uses one or more custom policies    | Guided UI in admin center             |
| Automatic         | Microsoft     | Org uses only the default global policy | Automatic, without admin intervention |

To migrate your organization, follow these steps:

1. Log into Teams admin center and access Teams apps > [Permission policies](https://admin.teams.microsoft.com/policies/app-permission) page. Take inventory of the apps in the permission policies and identify the users and groups that the apps are allowed or blocked for. During the migration, you may have to manually edit the availability for some apps for the existing users and groups. For details, see step 5.

1. On the permission policies page, select **Get started**.

   :::image type="content" source="media/acm-start-prompt.png" alt-text="Screenshot showing the policy page with prompt to migrate to app centric management.":::

1. Select policies that you want to migrate and select **Next**. The page displays only those policies that are assigned to users or groups. Also, we migrate only those apps and their availability that are part of the policies that you choose to migrate. Apps in the unselected policies aren't part of the migration and can’t be migrated later. However, you can manually edit the availability for any app after the migration.

    :::image type="content" source="media/acm-migration-select-policies.png" alt-text="Screenshot showing the app centric management migration UI to select policies."  lightbox="media/acm-migration-select-policies-large.png":::

1. Verify the app availability for the users on the next page. In the following three tabs, it shows a list of apps from your Org-wide app settings and the app permission policies that you choose to migrate.

   * Available to everyone: List of apps allowed for everyone in your organization.
   * Available to specific users and groups: List of apps that are selectively allowed for at least one org user or a supported group.
   * Available to no one: List of apps that nobody in the org can use.

1. In each tab, you can modify the app availability to one of the [three app availability types](#how-is-app-centric-management-different-than-permission-policy), as necessary. Edit availability option appears in **Available to specific users and groups** tab if the app availability isn't clear and admin input is needed to proceed. Either the apps aren't present in the policies that you selected to migrate or selected policies contain conflicting availability. You must assign such apps to one of the availability types before you can proceed.

    :::image type="content" source="media/acm-migration-availability.png" alt-text="Screenshot showing three tabs during migration that help you review and modify the app availability." lightbox="media/acm-migration-availability.png":::

   > [!TIP]
   > If you see many apps in this tab, you likely have policies that have conflicting apps availability. For example, a policy that allows an app and another policy that blocks the same app. In such a scenario, we recommend that you uncheck the policy that leads to a conflict or you edit the availability in this tab.

1. You can validate the changes on a per-app or a per-user basis. Select a tab and type the name of the app or the user.

    :::image type="content" source="media/acm-verify-per-app.png" alt-text="Screenshot showing the option to verify available of for each user and users who receive a particular app."  lightbox="media/acm-verify-per-app-large.png":::

1. On the final review UI, you can see the apps, their availability, and the Org-wide app settings that apply after the migration. You can download this information as a CSV file to evaluate further. For example, you can use the inventory mapping from Step 1 to ensure that the app availability is as intended. Once assured, select **Start migration** and follow the prompts. Migration may take up to 24 hours to complete.

    :::image type="content" source="media/acm-migration-review.png" alt-text="Screenshot showing the last UI to review all settings."  lightbox="media/acm-migration-review-large.png":::

During migration, you can save a draft of the migration progress using the **Finish later** option. You can cancel the migration and delete the saved draft using the **Reset all changes** option.

> [!NOTE]
> While migrating, you can't make changes to app assignments. The existing UI gets disabled when you start the migration. If you aren't ready to proceed or want to make change to the exiting permission policies, open the migration wizard and select the Reset all changes option. You'll lose the progress and can restart the migration later.

After migration, your blocked apps continue to remain unavailable to users. The statuses of such apps show as `unblocked` now, but the apps are assigned to `No one` in the `Available to` column on the Manage apps page. It means that org user can't use the app, just as you intended before. Users can view the apps in store and [request access to apps](user-requests-approve-apps.md).

## Add or modify app availability for users

To allow users to add and use an app or a Copilot agent, you must assign users or groups to an app. To make any app or Copilot agent available in your organization, ensure the following:

* If your organization isn't migrated to unified app management, allow apps and Copilot agents in Teams admin center and under the **Integrated apps** page in [Microsoft 365 admin center](/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps).
* If your organization is migrated to unified app management, allow apps and Copilot agents in Teams admin center or under the **Integrated apps** page in [Microsoft 365 admin center](/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps).

For more information, see [manage apps that work across Teams, Outlook, and Microsoft 365 App](manage-apps-across-m365.md).

### Understand the auto-migration process

Auto-migration maintains the same access defined in app permission policies when there is no conflict between a user’s assigned policies. If a user belongs to policies that conflict with one allowing and another blocking the same app, Microsoft auto-migrates the app as allowed. After auto-migration, a security group is created for each set of users assigned to each app permission policy. These groups are assigned to each app they are allowed in their respective policy, maintaining their app access. You can manage these groups to customize the app centric management assignments, such as adding or removing users, or removing the group and replacing it with another.

> [!NOTE]
> It takes up to 24 hours for the availability changes to take effect. In rare cases, it may take up to six days for the changes to reflect in the client.

To make any app or Copilot agent available to your organization in Teams admin center, follow these steps:

1. Go to the [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page.

1. Search for the required app and select the app name to open its app details page.

1. Select the **Users and groups** tab.

1. Under **Select to manage who this app is installed for or available to in your organization**, select **Availability**.

1. Select **Edit availability**.

1. Select the required option from **Available to** menu. When assigning users or groups, search for the user or the group from the **Search for users or groups** menu. Select **Apply**.

    :::image type="content" source="media/acm-add-modify-access.png" alt-text="Screenshot shows how to define the app availability from the app details page." lightbox="media/acm-add-modify-access.png":::

1. To remove one or more users or groups from an app, select the rows and select **Remove**.

    :::image type="content" source="media/acm-remove-access.png" alt-text="Screenshot shows how to remove the existing availability of an app from the app details page." lightbox="media/acm-remove-access.png":::

## Default settings for app availability

In addition to defining the availability of an app, you can also control the default app availability of any new apps. You can control it for each type of app. For new organizations, the default setting is set to let users install apps by default. For existing organizations, [old settings are mapped to new access settings](#mapping-between-old-permission-policies-and-new-app-availability).

To change this default setting, access [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page, select **Actions** > **Org-wide app settings**, and modify the required settings.

The Org-wide app settings apply to:

* All the new apps made available in Teams app store.
* All the existing apps that you didn't actively manage, that is, you didn't change the availability of.

:::image type="content" source="media/acm-org-wide-app-settings.png" alt-text="Screenshot showing the org-wide app settings in an organization that uses app centric management feature.":::

The Org-wide app settings don’t apply to:

* All apps that have user assignment set to Specific users and groups and saved by you.
* All apps that were assigned to Everyone or to No one and saved individually.
* Any blocked apps.

Consider a scenario where you started using the feature and all apps were assigned to everyone. Now, you changed an app's availability to a specific group or some users. After you save this change, if you change the Org-wide app setting titled **Let users install and use available apps by default**, then this particular app continues to be assigned to the specific group or users. Your change to the org-wide app setting applies only to those apps for which you didn't change the availability. Further, if you again change the **Let users install and use available apps by default** setting, the availability of all other apps is again impacted, except the app that you actively managed.

## View apps in your organization

You can view all apps in the catalog and easily access the app availability from the [Manage apps](https://admin.teams.microsoft.com/policies/manage-apps) page. You can sort and filter using all three types of app availability. To know about the Microsoft-provided apps, see [list of Microsoft created apps](apps-in-teams.md#list-of-apps-created-by-microsoft).

:::image type="content" source="media/acm-app-filter.png" alt-text="Screenshot showing how to filter apps by combining various criteria such as app availability, app type, and app status.":::

### View all apps available to a specific user

On the **[Manage users](https://admin.teams.microsoft.com/users)** page, select a user to open the user details page, and select the **Apps** tab. The tab lists the apps that the user has access to. To easily locate the type of access for an app, you can search for the name of the app.

:::image type="content" source="media/acm-manage-user-apps-tab.png" alt-text="Screenshot showing how to view all the apps that a user has access to, from the Manage users page.":::

Each app displays the type of its availability, which indicates how the user is assigned to the app: through availability to everyone, direct availability to a user, or through a group. The list shows only those apps that are assigned to the user and that are allowed in the organization for use. Apps assigned to no one and app that are blocked in the organization don't appear in this list.

You can remove app availability for a user. Select an app that is directly assigned to the user and select **Remove**. You can’t remove availability for a user if the app is available to everyone or to a group.

## Mapping between old permission policies and new app availability

When your tenant's admin center receives this feature, the following updates are made to the app access. The access to apps doesn't change and the update only maps your existing permission policies to new availability.

| App permission policy and org settings earlier | Org-wide app settings while using this feature |
|------------------------------------------------|------------------------------------------------|
|  Global permission policy for Microsoft apps was `Allow all` or Global permission policy for Microsoft apps was `Block an app(s), allow all others`  |  `Allow users install available apps by default` for Microsoft apps is set to on |
|  Global permission policy for Microsoft apps was `Block all` or Global permission policy for Microsoft apps was `Allow app(s), Block all others` | `Allow users install available apps by default` for Microsoft apps is set to off |
|  Third party app setting in the Org-wide app settings was set to on; New third party app setting in the org-wide app setting was set to on; Global permission policy for third party apps was `Allow all`; or Global permission policy for third party apps was `Block an app(s), allow all others`  |  `Allow users install available apps by default` for third party apps is set to on |
|  third party app setting in the Org-wide app settings was set to off; New third party app setting in the org-wide app setting was set to off; Global permission policy for third party apps was `Block all`; or Global permission policy for third party apps was `Allow app(s), Block all others` | `Allow users install available apps by default` for third party apps is set to off |
| Third party app setting in the Org-wide app settings was set to on; New third party app setting in the org-wide app setting was set to off; Global permission policy for third party apps was `Block all`; or Global permission policy for third party apps was `Allow app(s), Block all others` | `Allow users install available apps by default for third party apps` is set to off |
|  Global permission policy for Custom apps was `Allow all` or Global permission policy for Custom apps was `Block an app(s), allow all others` | `Allow users install available apps by default` for custom apps is set to on |
|  Global permission policy for custom apps was `Block all` or Global permission policy for custom apps was `Allow app(s), Block all others` | `Allow users install available apps by default` for custom apps is set to off |

| App status earlier | Permission policy applied earlier | App availability when using this feature |
|--------------------|-----------------------------------|------------------------------------------|
| Blocked            | Blocked                           | No one can install                       |
| Blocked            | Allowed                           | No one can install                       |
| Allowed            | Blocked                           | No one can install                       |
| Allowed            | Allowed                           | Everyone                                 |

## Considerations and known limitations

* You can add up to 99 users or groups at a time to an app.

* When searching for users or groups to add, the UI displays only 20 results. If you don't find the expected results, refine your search query to use the exact name.

* After migration, your blocked apps continue to remain unavailable to users. The status of such apps is `unblocked` now but the apps are available to `No one` in the `Available to` column on the Manage apps page. It means that no org user can use the app as you intended before.

* After you switch to this feature, you can't access, edit, or use permission policies. Once your organization migrates, you can't revert the migration.

* You can't update app availability in bulk.

* Automatic migration details:
  
  * One security group is automatically created per custom app permission policy. All users assigned  to the app permission policy are assigned to the corresponding groups.

  * After the migration, an Entra Global or Groups administrator can view and manage the groups. We recommended assigning owners to each group.

  * There is no change in app availability for users during the automatic migration, except where an app is allowed in the global app permission policy but blocked in the custom app permission policy for specific users. The app becomes allowed for everyone.

## Related articles

* [Check the availability and state of app](/powershell/module/teams/get-m365teamsapp)
* [View all Teams apps in the app catalog](/powershell/module/teams/get-allm365teamsapps)
* [Updates the state of an app](/powershell/module/teams/update-m365teamsapp)
