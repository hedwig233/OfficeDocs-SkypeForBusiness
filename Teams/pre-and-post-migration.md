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
There is no Powershell command for it. But there is an alternative way in TAC **before migration**.

Go to TAC - https://admin.teams.microsoft.com/
Go to Manage Users page

> :::image type="content" source="media/step3-manage-users-page.png" alt-text="":::

Click on filter of the Manage users table on right side top button.

> :::image type="content" source="media/step3-manage-users-page-filter.png" alt-text="":::

Select the policy name for which you need the user assignments and click apply.

> :::image type="content" source="media/step3-manage-users-page-filter-applied.png" alt-text="":::

That will show all the users assigned to the policy filtered.

> :::image type="content" source="media/step3-manage-users-page-filter-applied-results.png" alt-text="":::


Optionally export the user list to CSV.

> :::image type="content" source="media/step3-manage-users-page-export-csv.png" alt-text="":::


## Post migration

After migrating to ACM, customers can validate against their pre-migration posture using the same steps. Follow the instructions defined in this section to gather your previous permission policies and compare them to your ACM settings: Review your permission policies and note your allowed/blocked apps.

## Bulk App Management

1. Create Distribution Lists and Add Members: You can use the New-DistributionGroup and Add-DistributionGroupMember cmdlets to create distribution lists and add members. For example:

New-DistributionGroup -Name "DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins" -PrimarySmtpAddress "DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com"
Add-DistributionGroupMember -Identity "DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins" -Member "user1@man-es.com"

1. Assign All Applications to a Distribution List: To assign all applications to the distribution list DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com, you can use the Update-M365TeamsApp cmdlet. Here is an example to assign all apps at once:
$apps = Get-AllM365TeamsApps
foreach ($app in $apps) {
    Update-M365TeamsApp -Id $app.Id -AppAssignmentType UsersAndGroups -Groups "DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com"
}

1. Modify Availability of Specific Apps to Everyone: To modify the availability of 53 apps to Everyone, you can use the Update-M365TeamsApp cmdlet with the AppAssignmentType parameter set to Everyone. For example:
$appIds = @("appId1", "appId2", "appId3", ...) # List of 53 app IDs
foreach ($appId in $appIds) {
    Update-M365TeamsApp -Id $appId -AppAssignmentType Everyone
}

1.	Allow Microsoft Apps to Multiple Distribution Lists: To allow all Microsoft apps to the distribution lists DTDEAUG_MSTeamsAppPolicy_ITTestMSPVA@man-es.com and DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com, you can use the Update-M365TeamsApp cmdlet. For example:
$msApps = Get-AllM365TeamsApps | Where-Object { $_.Publisher -eq "Microsoft" }
foreach ($app in $msApps) {
    Update-M365TeamsApp -Id $app.Id -AppAssignmentType UsersAndGroups -Groups "DTDEAUG_MSTeamsAppPolicy_ITTestMSPVA@man-es.com","DTDEAUG_MSTeamsAppPolicy_M365TeamsAdmins@man-es.com"
}
1.	Here's an example of what the list.csv file might look like:
AppId,DistributionList
appId1,DTDEAUG_MSTeamsAppPolicy_Group1@man-es.com
appId2,DTDEAUG_MSTeamsAppPolicy_Group2@man-es.com
appId3,DTDEAUG_MSTeamsAppPolicy_Group3@man-es.com
...
You can then use the following PowerShell script to read the CSV file and assign the applications to the specified distribution lists:
$csv = Import-Csv -Path "C:\path\to\list.csv"
foreach ($row in $csv) {	
    Update-M365TeamsApp -Id $row.AppId -AppAssignmentType UsersAndGroups -Groups $row.DistributionList
}
This script will loop through each row in the CSV file and assign the applications to the corresponding distribution lists.

Another example 

1. Made required changes to Teams Admin Center Configuration Updates
1. Applied all available apps to Teams Admin Distribution Group for smooth management.  

PowerShell Command Used:
 
Import-Csv .\AppList1.csv | %{Update-M365TeamsApp -Id $_.AppId  -AppAssignmentType UsersAndGroups -Groups $_.GroupID -OperationType Add}
 
3. Assigned all Microsoft apps to a designated custom policy group to keep all Microsoft apps organized and managed under a specific policy for targeted user group. 

** PowerShell Command Used:
 
Import-Csv .\AppList2.csv | %{Update-M365TeamsApp -Id $_.AppId  -AppAssignmentType UsersAndGroups -Groups $_.GroupID -OperationType Add}

4. Mapped specific apps to their respective custom policy groups for making access control more effective.  
  PowerShell Command Used:
 
Import-Csv .\AppList3.csv | %{Update-M365TeamsApp -Id $_.AppId  -AppAssignmentType UsersAndGroups -Groups $_.GroupID -OperationType Add}
 
5. Updated Global Policy to make selected apps accessible to all users across the organization.  
  PowerShell Command Used:
 
gc '.\GlobalApps.txt' | %{Update-M365TeamsApp -Id $_ -AppAssignmentType Everyone}
 

## Related articles

* [Check the availability and state of app](/powershell/module/teams/get-m365teamsapp)
* [View all Teams apps in the app catalog](/powershell/module/teams/get-allm365teamsapps)
* [Updates the state of an app](/powershell/module/teams/update-m365teamsapp)
