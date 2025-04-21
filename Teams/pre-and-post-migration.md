---
title: Best practices ACM migration
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

# Best practices during ACM migration

It is recommended that customers follow these steps during self-serve migration to check pre- and post- ACM migration health.

## Pre-migration

### Summary

App centric management simplifies the process of allowing apps for your users and groups. ACM migration involves preserving the users and apps allowed in your App permission policies; you can also add or exclude users.

> In summary, you will:

1. [Export your app catalog and note your allowed apps](#step-1-export-your-app-catalog-and-note-your-allowed-apps).
1. [Review your permission policies and note your allowed/blocked apps](#step-2-review-your-permission-policies-and-note-your-allowedblocked-apps).
1. [Identify the users allowed for each app through your permission policies.](#step-3-identify-users-allowed-for-each-app)
1. [Reassign those users in the App centric management](#get-a-list-of-users-assigned-to-a-policy).

#### Step 1: Export your app catalog and note your allowed apps

1. Start with the Manage Apps page. Export the full list of apps in the catalog as a CSV file, including each app’s allowed/blocked App status. The allow/block status determines whether the app is available to everyone or no one, respectively. This status is used in the following steps to narrow down your users. For more details, see [Export app catalog as CSV](https://learn.microsoft.com/microsoftteams/manage-apps#export-app-catalog-as-csv).
 
> :::image type="content" source="media/step1–export-app-catalog.png" alt-text="Screenshot showing the export App catalog.":::

#### Step 2: Review your permission policies and note your allowed/blocked apps

Review your permission policies. This section is intended for users who have multiple permission policies.

Steps to retrieve the permission policies list using UI:

1. Navigate to Teams admin center > Manage apps > Permission policies.
1. Open each permission policy and note which apps are allowed or blocked.

Steps to retrieve the permission policies list using PS cmdlet:

1. Run Get-CsTeamsAppPermissionPolicy(/powershell/module/teams/get-csteamsapppermissionpolicy?view=teams-ps &preserve-view=true).
2. Interpreting results:

> :::image type="content" source="media/step2–interpret-results.png" alt-text="Screenshot showing the interpret results.":::

Response legend:

* Allowed app list with a list of apps = List of apps allowed, all other apps are blocked.
* Allowed app list with an empty list of apps = All apps are blocked.
* Blocked app list with an empty list of apps = All apps are allowed.
* Blocked app list with a list of apps = Apps are blocked and all other apps are allowed.

In the above example, there are three policies in the tenant: Global, Test Policy, and Test 2.

Global:

1. Microsoft apps (Default Catalog Apps): com.microsoft.teamspace.tab.vsts, cd2d8695-bdc9-4d8e-9620-cc963ed81f41, com.microsoft.teamspace.tab.planner, a6b63365-31a4-4f43-92ec-710b71557af9...(more) are allowed, the rest are blocked (Allowed app list)
1. Third party apps (Global Catalog Apps) 3 apps are allowed, the rest are blocked (Allowed App list)
1. Private Catalog Apps (Custom Apps) - All allowed (Blocked app list is empty)

Retrieve allowed apps in each permission policy
PS cmdlet
In the example above, not all default apps are shown in the response. To see all the default apps, you need to assign a variable to the result.
For example: 
$msftApps = Get-CsTeamsAppPermissionPolicy -Identity "Global" | Select-Object -ExpandProperty DefaultCatalogApps
$msftApps.id

Filter out blocked apps
We have gathered information on all applications permitted within the tenant. It is now necessary to identify the individuals or groups for whom each application is authorized.

Merge it with export from Manage apps page and anything that is blocked in Manage apps will be blocked no matter what the policy assignment might return. 

### Step 3: Identify users allowed for each app 

#### Get a list of users assigned to a policy

There is no Powershell command to get a list of users assigned to a policy. You can use an alternative way in TAC  **before migration** to get the list of users.

1. Go to TAC - https://admin.teams.microsoft.com/
1. Go to **Manage Users** page.

> :::image type="content" source="media/step3-manage-users-page.png" alt-text="Screenshot showing manage users page.":::
1. Click the filter located at the top right of the Manage Users table.

> :::image type="content" source="media/step3-manage-users-page-filter.png" alt-text="Screenshot showing manage users page filter.":::

1. Select the policy name for which you need the user assignments and click **Apply**.

> :::image type="content" source="media/step3-manage-users-page-filter-applied.png" alt-text="Screenshot showing manage users page applied page.":::

All the users assigned to the policy filtered are shown.

> :::image type="content" source="media/step3-manage-users-page-filter-result.png" alt-text="Screenshot showing manage users page filter results.":::

1. You can also export the users list to CSV.

> :::image type="content" source="media/step3-manage-users-page-export-csv.png" alt-text="Screenshot showing export manage users page csv.":::

## Post migration

After migrating to ACM, customers can validate against the pre-migration posture using the same steps. Follow the instructions defined in this section to gather your previous permission policies and compare them to your ACM settings. Review your permission policies and note your allowed/blocked apps.

## Bulk app management

1. **Create Distribution Lists and Add Members**: You can use the `New-DistributionGroup` and `Add-DistributionGroupMember` cmdlets to create distribution lists and add members.

For example:
`New-DistributionGroup -Name "DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins" -PrimarySmtpAddress "DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com"`
`Add-DistributionGroupMember -Identity "DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins" -Member "user1@man-es.com"`

1. Assign all apps to a distribution list: To assign all apps to the distribution list DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com, you can use the `Update-M365TeamsApp` cmdlet. Here is an example to assign all apps together:

`$apps = Get-AllM365TeamsApps
foreach ($app in $apps) {
    Update-M365TeamsApp -Id $app.Id -AppAssignmentType UsersAndGroups -Groups "DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com"
}`

1. Modify availability of specific apps to everyone: To modify the availability of specific apps to everyone, you can use the `Update-M365TeamsApp` cmdlet with the `AppAssignmentType` parameter set to `Everyone`.

For example:
`$appIds = @("appId1", "appId2", "appId3", ...) # List of 53 app IDs
foreach ($appId in $appIds) {
    Update-M365TeamsApp -Id $appId -AppAssignmentType Everyone
}`

1. Allow Microsoft apps to multiple distribution lists: To allow all Microsoft apps to the distribution lists DTDEAUG_MSTeamsAppPolicy_ITTestMSPVA@man-es.com and DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com, you can use the `Update-M365TeamsApp` cmdlet.

For example:
$msApps = Get-AllM365TeamsApps | Where-Object { $_.Publisher -eq "Microsoft" }
foreach ($app in $msApps) {
    Update-M365TeamsApp -Id $app.Id -AppAssignmentType UsersAndGroups -Groups "DTDEAUG_MSTeamsAppPolicy_ITTestMSPVA@man-es.com","DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com"
}

1. Here's an example of the `list.csv` file:
AppId,DistributionList
appId1,DTDEAUG_MSTeamsAppPolicy_Group1@man-es.com
appId2,DTDEAUG_MSTeamsAppPolicy_Group2@man-es.com
appId3,DTDEAUG_MSTeamsAppPolicy_Group3@man-es.com
...

The following PowerShell script can be used to read the CSV file and assign the applications to the specified distribution lists:
`$csv = Import-Csv -Path "C:\path\to\list.csv"
foreach ($row in $csv) {
    Update-M365TeamsApp -Id $row.AppId -AppAssignmentType UsersAndGroups -Groups $row.DistributionList
}`

This PowerShell script loops through each row in the CSV file and assign the applications to the corresponding distribution lists.

Another example:

1. Made required changes to Teams Admin Center Configuration Updates.
1. Applied all available apps to Teams Admin Distribution Group for smooth management.  
PowerShell command used:
`Import-Csv .\AppList1.csv | %{Update-M365TeamsApp -Id $_.AppId  -AppAssignmentType UsersAndGroups -Groups $_.GroupID -OperationType Add}`

1. Assigned all Microsoft apps to a designated custom policy group to keep all Microsoft apps organized and managed under a specific policy for targeted user group.
PowerShell command used:
`Import-Csv .\AppList2.csv | %{Update-M365TeamsApp -Id $_.AppId  -AppAssignmentType UsersAndGroups -Groups $_.GroupID -OperationType Add}`

1. Mapped specific apps to their respective custom policy groups for making access control more effective.
PowerShell command used:
`Import-Csv .\AppList3.csv | %{Update-M365TeamsApp -Id $_.AppId  -AppAssignmentType UsersAndGroups -Groups $_.GroupID -OperationType Add}`

1. Update **Global Policy** to make selected apps accessible to all users across the organization.
PowerShell command used:
`gc '.\GlobalApps.txt' | %{Update-M365TeamsApp -Id $_ -AppAssignmentType Everyone}`

## Related articles

* [Check the availability and state of app](/powershell/module/teams/get-m365teamsapp)
* [View all Teams apps in the app catalog](/powershell/module/teams/get-allm365teamsapps)
* [Updates the state of an app](/powershell/module/teams/update-m365teamsapp)