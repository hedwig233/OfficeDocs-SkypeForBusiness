---
title: Admins- Manage custom dictionaries Microsoft Teams meetings and events
ms.author: wlibebe
author: wlibebe
ms.reviewer: fei.zuo
manager: pamgreen
ms.date: 5/19/2025
audience: Admin
ms.topic: how-to
ms.subservice: meetings
ms.service: msteams
ms.localizationpriority: medium
ms.collection: 
- m365initiative-meetings
- m365copilot
- magic-ai-copilot
description: Learn about how to upload and manage a Copilot custom dictionary.
---

# Admins- Manage custom dictionaries Microsoft Teams meetings and events

## Overview

> [!IMPORTANT]
> This feature is currently in Teams Public preview.
>
> Features in preview might not be complete and could undergo changes before becoming available in the public release. They're provided for evaluation and exploration purposes only.

Organizations often use their own special terms, acronyms, and jargon, like product names, department-specific language, and industry-specific terms. The AI models powering Teams transcription are trained using general datasets that might not recognize these specialized terms. When you import a custom dictionary, the model dynamically adapts during meetings and performs post-correction once the meeting ends, ensuring accurate transcription of these specialized terms.

As an admin, you can upload a custom dictionary in the Microsoft 365 admin center to improve the quality of transcription. Once you upload a dictionary, it enhances the recognition of all entities throughout the meeting. This improvement enhances the meeting transcript and benefits the AI quality for Copilot and Recap.

## Prerequisites

### Admin

As an admin, you must meet the following requirements to upload custom dictionaries:

- You must have the AI administrator role. To learn more about admin roles, see [About admin roles in the Microsoft 365 admin center](/microsoft-365/admin/add-users/about-admin-roles).

### Your users

Users in your organization must meet the following requirements to use custom dictionaries:

- An eligible *Microsoft 365* base license.
  - For the list of eligible base licenses, see [Understand licensing requirements for Microsoft 365 Copilot](/copilot/microsoft-365/microsoft-365-copilot-licensing).
- An eligible *Microsoft Teams* license.
  - Teams licenses might be included in your *Microsoft 365* subscription, or you might need to purchase a separate Teams license if you have *Microsoft 365 (no Teams)* licenses.
- A *Microsoft 365 Copilot* license.
  - For information on how to acquire *Microsoft 365 Copilot* licenses, see [Where can I get Microsoft Copilot?](https://support.microsoft.com/topic/where-can-i-get-microsoft-copilot-40a622db-6d25-4266-b008-4bbcb55cf52f).
- Be a Microsoft Teams Public preview participant.
  - For information on how to access Teams Public preview features, see [Microsoft Teams Public preview](/microsoftteams/public-preview-doc-updates).

## Understand custom dictionaries

The custom dictionary captures organization-specific terminology to enhance the transcript and AI model's understanding of entities. It is configured at the tenant level and must be manually uploaded and managed by the admin. Group or user specific dictionaries are not included in this scope. The aim is to provide admins with an easy way to maintain a straightforward dictionary. All tenant meetings with a Copilot license will benefit from these terms when mentioned, without any adverse effects if they are not. 

> [!NOTE]  
> The custom dictionary will enhance transcription for meetings organized or initiated by users with a Microsoft 365 Copilot license.

As an admin, you're the only one who can create and update the custom dictionary with new internal terms. Uploading a new dictionary replaces the existing one in the same language. Your users can't add terms to the dictionary; they must ask you to upload an updated dictionary with new internal terms.

### Dictionary content

The dictionary is presented in a flat list format, with optional fields for recording the "Sounds like" and "Long form of the term," and a comments section to provide more context. This assists IT administrators in managing and collecting entries from internal systems or product groups effectively. Each custom dictionary includes the following columns:

|Column | Definition |
|:-----|:-----|
|Term *(required)*| The display form of the term or phrase. This field is required to validate an entry. **This field is required**.|
|Sounds like|A column to record how the word was pronounced in a meeting. This field is optional.|
|Long form of the term *(for acronyms)*| A column to clarify potential acronyms or abbreviations. This field is optional. |
|Definition and context |A column to provide more context or definition of the term. This field is optional.|

> [!NOTE]  
> Currently, the custom dictionary only enhances the meeting transcript. The 'Long form of the term' and 'Definition and context' will be applied in future AI enhancements for Intelligent Recap and Copilot responses.

### Dictionary sample

The following are examples of dictionary entries. The first column, **Term**, is the most important and should be mapped to your expected format from the transcription output.

| Term *(required)* | Sounds like | Long form of the term *(for acronyms)* | Definition and context |
|:-----|:-----|:-----|:-----|
|TAC| Tee-Ay-Cee| Teams Admin Center| Admin portal managing Teams|
|TAT| Tee-Ay-Tee| Turn Around time| Metric the support team uses and must meet|
|Viva Glint| Vee-Vah-Glint | |  Part of Microsoft Viva|

> [!TIP]
> The **Term** column is required, while all other columns are optional.

### Dictionary file format and language

You should compile the dictionary in a CSV plain-text format with UTF-8 encoding and comma-delimited format. We recommend the Excel output format option "CSV UTF-8 (comma delimited)." Each dictionary can contain up to 500 terms/entries. You can upload one dictionary per language, which is applied to the target Teams transcription language(region) setting as described in the following table.

| Custom dictionary Language | Teams transcription Language |
|:-----|:-----|
|English|English (United States)|
|English  |English (United Kingdom)|
|English  |English (Australia)|
|English  |English (Canada)|
|English  |English (India)|
|Spanish  |Spanish (Spain)|
|Spanish  |Spanish (Mexico)|
|Japanese  |Japanese (Japan)|
|French  |French (France)|
|French  |French (Canada)|
|German  |German (Germany)|
|Portuguese  |Portuguese (Brazil)|
|Italian  |Italian (Italy)|
|Chinese (Simplified) |Chinese (Simplified, China)|

## Upload a custom dictionary

### Navigate through the Microsoft 365 admin center

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com).
2. From the left navigation panel, select **Copilot**, and go to the **Settings**.
3. Select **Copilot custom dictionary** and select on it to see the flyout view from the right for custom dictionary management.
4. Select **Upload Dictionary** to go to the uploading sub view.

### Create the custom dictionary with a CSV file

5. Select the option to download the **CSV template with header only** from the portal.
6. Open the template with Excel, open with UTF-8 and comma-delimited format.
7. Fill in your custom terms in the **Term *(required)*** column as a flat list.
8. *(optional)* Fill in additional information in the **Sounds like**, **Long form of the term *(for acronyms)***, and **Definition and context** columns.
9. Save the file as CSV UTF-8 (Comma delimited) (.csv).

### Upload your custom dictionary

10. Return to the uploading view and select your CSV file in the **Upload CSV file with terms** field.
11. Select the target language for this dictionary, then select **Upload**.

> [!NOTE]  
> The language you select must match the intended language for transcription.

12. After the loading page, a message appears at the top of the view, indicating if the upload was successful. If successful, your dictionary appears in the dictionary list in the management view.
13. Wait for up to 24 hours for the dictionary to become available for Teams meetings in your organization.

## Optimize your custom dictionary

To optimize your custom dictionary, follow these best practices:

- Include frequently mentioned terminology, acronyms, product names, project codes, team names, and industry-specific language relevant to your meetings.
- Allowed symbols in term- Don't include punctuation in the **Term** column and use fewer symbols. Symbols allowed in the middle of terms are: **-'/&·ㆍ**.
- Localize dictionaries- To create dictionaries in the corresponding languages, you should collect custom terms from each local group. For example, in the Japanese dictionary, some terms might remain in their English Latin form, while others might have local variants. Include all these terms in the Japanese custom dictionary to benefit meetings where Japanese is the primary language.
- Break down multi-word names- For names with multiple words, consider splitting them into individual parts. For example, instead of "Copilot in Power Platform and Dynamics 365," create separate entries for "Copilot," "Power Platform," and "Dynamics 365."
- Use Copilot for extra fields- Use Copilot to generate entries for **Sounds like**, **Long form of the term *(for acronyms)***, and **Definition and context**, then review and modify the entries as needed.
- Avoid short words: Avoid using short terms like "AB."
- Avoid numeric terms: Avoid including terms that are purely numeric like "123."
- Avoid repeated chars: Avoid using terms with repeated chars like "AAA."

## Data safety

- Custom dictionary should be restricted to tenant-specific terms that are relevant to the tenant's needs and must not contain any confidential, sensitive, or personal information.
- Custom dictionary data is used solely within your organization for meetings. Nobody else accesses the data and it isn't included in any AI model training.

## Supported scenarios

### Supported

Custom Dictionary enhances entity recognition for Teams transcription in the following scenarios:

- Scheduled meetings
- Town halls
- Webinars

### Not supported

Custom Dictionary isn't supported in the following scenarios:

- Group and 1:1 calls

## Related articles

- [Admins- Manage transcription and captions for Teams meetings](meeting-transcription-captions.md)
- [Manage Microsoft 365 Copilot in Teams meetings and events](copilot-teams-transcription.md)
- [Intelligent recap for Teams calls and meetings](intelligent-recap-calls-meetings.md)
