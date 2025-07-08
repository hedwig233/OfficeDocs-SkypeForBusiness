---
title: Manage caller ID for users
ms.author: scottfrancis
author: sfrancis206
manager: pamgreen
ms.reviewer: roykuntz
ms.date: 03/27/2025
ms.topic: how-to
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-calling
audience: Admin
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
f1.keywords:
- CSH
ms.custom: ms.teamsadmincenter.voice.callinglineid.overview
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to manage caller ID in Microsoft Teams to change or block the caller ID of Teams users in your organization.
---

# Manage caller ID for users

This article is for administrators and IT professionals who support Teams end user calling experiences for inbound and outbound caller ID.

Caller ID consists of two user-facing pieces of information:

- **Calling line ID (CLID)** - The phone number of the calling party, relayed to the Public Switched Telephone Network (PSTN) and offered to the called party.
- **Calling party name (CNAM)** - The name of the calling party, relayed to the PSTN, and offered to the called party.

The caller ID behavior for both inbound and outbound calls depends on the account's assigned Teams caller ID policy and calling policy, your organization's contact hygiene, and PSTN operators.

## Inbound caller ID behavior

In the operation of processing an inbound PSTN call, Teams looks up the number of the inbound caller's calling Line ID in the contacts configured in your organization.

Teams references your organization's Outlook and Entra ID contacts and your end-user's People contacts.

- Only "*Mobile phone*" and "*Work (Business) phone*" contact fields are searched
- Teams looks up and matches with contact numbers that are in E.164 standard format</br>(they must start with a "+")

If there *is* a match between the calling line ID and a contact, Teams substitutes the PSTN caller ID info with the matched contact's name. If there isn't a match, then the caller ID displays what's provided by the PSTN call.

The hierarchy for which source provides the presented caller ID to an end user is as follows, in order:

- The called Teams user's People contacts
- Contacts in Outlook and Entra ID
- The inbound PSTN call's calling party name
- The inbound PSTN call's calling line ID

> [!NOTE]
> Given that two Teams users can each customize the names in their People contacts differently for the same people, it's possible that a caller ID to the first Teams user could appear different than the caller ID to the second Teams user from the same caller.

### Spam calls

PSTN service providers do their best to block instances of robocalls, phone scams, and unwanted calls (collectively known as spam calls).

Service providers aren't always successful in blocking all spam calls; some spam calls manage to get through.

If Teams detects a call is possibly spam, it sends the caller ID as "*Spam likely*".

Changing the caller ID of a call to "*Spam likely*" is a setting that can be turned off in the user's calling policy. For more information, see [Configure spam filtering for calls in Microsoft Teams](configure-call-spam-filtering.md).

### Block inbound PSTN caller ID

If you have a requirement to prevent a set of Teams users from seeing the caller ID of inbound PSTN calls, you can assign a Teams *Caller ID* policy to the users where the setting "**Block incoming caller ID**" is turned **On**.

When this setting is turned on, the incoming PSTN caller is shown as coming from ***Anonymous***.

The **Block incoming caller ID** setting is an administrative setting and isn't available for end users to turn on or off in their user settings page.

For more information, see [configure caller ID policies](#configure-caller-id-policies).

### Blocking inbound PSTN calls

To block inbound PSTN calls at a tenant level, see [Block inbound calls](block-inbound-calls.md).

To block inbound PSTN calls for an end-user, see [Manage your call settings in Microsoft Teams](https://support.microsoft.com/office/manage-your-call-settings-in-microsoft-teams-456cb611-3477-496f-b31a-6ab752a7595f).

- Teams only checks for blocking numbers (at the tenant and user level) that are in E.164 standard format</br>(they must start with a "+")

## Outbound caller ID behavior

The outbound caller ID that your Teams Phone users send with outbound PSTN calls depends on the settings in their assigned *caller ID policy*.

### Outbound calling line ID

The user's outbound *caller ID policy* can be configured to send one of the following caller ID options:

- The telephone number assigned to the user, which is the default.

- Anonymous, which removes the presentation of the user’s calling line ID and calling party name.

- A substitute phone number, which can be one of the following numbers:

  - An Operator Connect or Direct Routing number that is assigned to a resource account used by a Teams Auto attendant or Call queue.

  - A Microsoft Calling Plan service and toll-free number *in your Calling Plan telephone number inventory* and assigned to a resource account used by a Teams Auto attendant or Call queue.

> [!IMPORTANT]
> Emergency calls always send the ***user's*** **Calling line ID** to a public-safety answering point (PSAP). For more information on emergency calls, see [Plan and manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

When calling on behalf of another account, the caller ID for the user is replaced by the caller ID configured for the account that is used to place the call. Examples of calling on behalf of another account include the following.

- Calling on behalf of a delegator
- Calling on behalf of a Call Queue
- Shared calling

You can't assign the following types of phone numbers for the outbound caller ID:

- Any Calling Plan or Operator Connect phone numbers in your inventory where the usage type is classified as **User**.

- Any Direct Routing on-premises telephone number that is assigned to a user.

- Any Skype for Business Server on-premises telephone number.

For Direct Routing, the phone number substitution and the CNAM are sent in the `From` Session Information Protocol (SIP) header. If the corresponding [OnlinePstnGateway](/powershell/module/teams/set-csonlinepstngateway) policy is configured with `-ForwardPai $true`, the P-Asserted-Identity (PAI) SIP header contains the real calling user.

For more information, see [Configure caller ID policies](#configure-caller-id-policies).

### Outbound calling party name

If you're replacing the caller ID with either the user's number or a resource account's number, then configuring a calling party name is supported.

Using a company's name for the calling party name is common. For example, when a Teams Phone user makes a call, you can change their outbound caller ID to display your organization's main phone number and company name instead of the user's phone number.

  - The calling party name can have a maximum of 200 characters, but downstream systems might support fewer characters.
  
  - The calling party name is sent on outbound Teams calls where the caller ID is configured with the user's phone number or resource account's phone number, and when the caller is a Teams user.

> [!NOTE]
> While Microsoft supports calling party name display for outbound calls, there's still a *dependency on PSTN operators to deliver the CNAM information to the called party*. For more information, see [More about Calling Line ID and Calling Party Name](more-about-calling-line-ID-and-calling-party-name.md).

### End user control that overrides the caller ID policy

Using the caller ID policy, you can allow users to **Override the caller ID policy**.

Turning on the setting that allows end users to control their caller ID gives them the ability to hide--or expose--their phone number for calls.

This setting (parameter *-EnableUserOverride*) has precedence over other settings in the [Caller ID policy](/powershell/module/teams/set-cscallinglineidentity) policy.

For example, where an assigned policy has the caller ID replaced with **resource account**, **Override the caller ID policy** is turned on, and the setting is turned on by the respective user in their client settings, the outbound caller ID is blocked and Anonymous is used.

Inversely, where an assigned policy has the caller ID replaced with **Anonymous**, **Override the caller ID policy** is turned on, and the setting is turned off by the respective user in their client settings, the outbound caller ID is sent with the user's assigned telephone number.

## Configure caller ID policies

Settings for both inbound *and* outbound caller ID are configurable in the Teams caller id policy. A list of the available caller ID settings follows.

|Setting|Default|Description|
|-------|--------|---------|
|Block incoming caller ID|Off|This setting blocks a user from receiving caller ID on any incoming PSTN calls.|
|Override the caller ID policy|Off|This setting allows users to override the settings in the policy that decide whether or not they display their number to the callee. By turning on this setting, users can choose whether to display their caller ID.</br></br>Your end users can set their caller ID to Anonymous by going to **Settings** > **Calls**, and then under **Caller ID**, select **Hide my phone number and profile information for all calls**. It takes a few minutes for this setting change to reflect on new calls.|
|Calling Party Name|(empty)|This setting sends a CNAM on outbound PSTN calls.|
|Replace the caller ID with|User's number|By default, the policy sends the user's telephone number for their caller ID.</br>This setting supports replacing a user's caller ID with another phone number. </br>**Anonymous** - This setting blocks the outgoing calling line ID and calling party name from being sent with a user's outgoing PSTN call and displays the caller id as coming from *Anonymous*.</br>**Resource Account** - This setting lets you choose a resource account's assigned number to use as the caller ID. You can set the calling ID number to any Calling Plan, Operator Connect, or Direct Routing phone number assigned to a resource account used by an Auto attendant or a Call queue.|

With all caller ID settings turned off, the Teams user's phone number is visible when that user makes a call to the PSTN. Likewise, when a PSTN caller makes a call to a Teams user, the PSTN caller's phone number is visible.

You can configure caller ID policies by using the [Teams admin center](#use-the-teams-admin-center) or by using [PowerShell](#use-powershell).

### Use the Teams admin center

You manage caller ID policies by going to **Voice** > **Caller ID policies** in the Microsoft Teams admin center. You can use the global (Org-wide default) policy or create and assign custom policies. Users in your organization automatically get the global policy unless you create and assign a custom policy.

For more information on each policy, see [configure caller ID policies](#configure-caller-id-policies).

#### Create a custom caller ID policy

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies.**

2. Select **Add**.

3. Enter a name and description for the policy.

4. Turn on or off **Block incoming caller ID** and **Override the caller ID policy**.

5. Enter a **Calling Party Name**.

6. Under **Replace the caller ID with**, set which caller ID is displayed for users by selecting one of the following:

      - **User's number:** Display the user's number.

      - **Anonymous:** Display the caller ID as Anonymous.

      - **Resource account:** Set a resource account associated with an Auto Attendant or Call Queue.

        If you choose **Resource account**, you're prompted to specify a resource account for the next field, called **Replace the caller ID with this resource account**. Only resource accounts with an assigned phone number are displayed. If you just assigned a phone number to the resource account, it might take a few minutes before the resource account is available for selection.

7. Select **Save**.

#### Assign a custom caller ID policy to users

[!INCLUDE [assign-policy](includes/assign-policy.md)]

#### Edit a caller ID policy

You can edit the global policy or any custom policies that you create.

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Caller ID policies**.

2. Select the policy by clicking to the left of the policy name, and then select **Edit**.

3. Change the settings that you want, and then select **Save**.

### Use PowerShell

You can manage caller ID policies by using the following PowerShell cmdlets in Teams PowerShell module 2.3.1 or later:

- [New-CsCallingLineIdentity](/powershell/module/teams/new-cscallinglineidentity)
- [Set-CsCallingLineIdentity](/powershell/module/teams/set-cscallinglineidentity)
- [Remove-CsCallingLineIdentity](/powershell/module/teams/remove-cscallinglineidentity)
- [Get-CsCallingLineIdentity](/powershell/module/teams/get-cscallinglineidentity)
- [Grant-CsCallingLineIdentity](/powershell/module/teams/grant-cscallinglineidentity)

#### New custom caller ID policy

The following example creates a new caller ID policy that sets the caller ID (*-CallingIDSubstitute*) to the phone number of the specified resource account, and sets the Calling party name (*-CompanyName*) to Contoso.

```PowerShell
$ObjId = (Get-CsOnlineApplicationInstance -Identity dkcq@contoso.com).ObjectId
```

```PowerShell
New-CsCallingLineIdentity -Identity DKCQ -CallingIDSubstitute Resource -EnableUserOverride $false -ResourceAccount $ObjId -CompanyName "Contoso"
```

The next example creates a new caller ID policy that sets the caller ID to Anonymous:

```PowerShell
New-CsCallingLineIdentity -Identity Anonymous -Description "anonymous policy" -CallingIDSubstitute Anonymous -EnableUserOverride $false
```

#### Change a caller ID policy

The following example modifies the UKAA caller ID policy to set a new description:

```PowerShell
Set-CsCallingLineIdentity -Identity "UKAA" -Description "UK Main office"
```

#### Remove a caller ID policy

The following example removes the UKAA caller ID policy:

```PowerShell
Remove-CsCallingLineIdentity -Identity "UKAA"
```

#### Grant a caller ID policy

The following example grants the Anonymous caller ID policy to Amos Marble:

```PowerShell
Grant-CsCallingLineIdentity -Identity "amos.marble@contoso.com" -PolicyName "Anonymous"
```

> [!NOTE]
> The use of CallingIDSubstitute = Service has been deprecated. You're no longer able to create new caller ID policies using CallingIDSubstitute = Service. Existing caller ID policies with CallingIDSubstitute = Service aren't being honored. Use CallingIDSubstitute = Resource instead. For more information, see [Set-CsCallingLineIdentity](/powershell/module/teams/Set-CsCallingLineIdentity).

## Related articles

- [Teams policies reference - Caller ID](settings-policies-reference.md#caller-id-policies)
- [More about Calling Line ID and Calling Party Name](more-about-calling-line-ID-and-calling-party-name.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Set-CsCallingLineIdentity](/powershell/module/teams/set-cscallinglineidentity)
