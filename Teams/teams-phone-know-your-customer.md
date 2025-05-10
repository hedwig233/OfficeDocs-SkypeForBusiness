---
title: "Teams Phone Know Your Customer overview"
author: sfrancis206
ms.author: scottfrancis
manager: pamgreen
ms.reviewer: garciadaniel
ms.date: 05/09/2025
ms.topic: conceptual
ms.assetid: 6b61cb3c-361c-48a8-a9ef-d81bddde27bb
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-calling
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: Medium
f1.keywords:
- CSH
ms.custom: 
  - Calling Plans
  - seo-marvel-apr2020
description: Learn how Microsoft supports validation of your business with PSTN operators through the Know Your Customer process.
---

# Validate your business identity with PSTN operators using Know Your Customer

**APPLIES TO:** ![Image of a checkmark for yes](/office/media/icons/success-teams.png)Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, and Direct Routing

This article provides an overview of the Know Your Customer value and process, and a guide for setting it up in your Teams admin center.

Know Your Customer, also known as **KYC** is a PSTN industry practice that allows PSTN operators to validate the identity of their customer before providing communication services. It's a way to identify your business so that PSTN operators can help prevent your business from carrying illegal traffic, receiving nuisance calls, and more. KYC is designed to help prevent fraud and ensure national security, and therefore it's a PSTN operator investment into your risk management strategy.

In some countries and regions, KYC is a prerequisite for allowing customers to acquire or port telephone numbers. National Regulatory Authorities in different countries and regions set the rules for the information needed from users or businesses to get, transfer, or activate phone numbers for calling and messaging services.

Microsoft supports the KYC process by storing your KYC profile in your tenant.

Having your KYC profile stored in Teams expedites PSTN service requests and increases request approvals for PSTN services.

## Setting up KYC in your Teams admin center

To get your business verified, submit your business KYC information via the Teams admin center. A summary of the steps follows.

- In the Teams Admin Center, go to ***Voice*** > ***Service configuration*** > ***Know-Your-Customer*** and select ***Add KYC information***.

- Step 1: Verify email address

- Step 2: Provide business information

- Step 3: Upload supporting documents

- Submit

### Step 1: Verify email address

Provide an email address for the business contact responsible for verification.

No free or generic email addresses are accepted.

A one-time code is sent. Submit the received code to confirm the email address. Status change notifications are sent to this email address.

### Step 2: Provide Business information

In the Business information section of the KYC form, provide details of your company, as denoted in its country/region. 

Ensure all information provided matches the supporting documents requested in the next step.

|Form field |Description |
|:-----|:-----|
|Company name |Enter your company's official name as it's legally registered in your country or region. |
|Tax ID or Business Registration number |Enter the Tax ID of your company, respective to the country/region of your company's headquarters. <br><br>**United States**--US companies (and companies with a US EIN), enter your Tax ID's nine-digit EIN. <br>**Canada**–-For companies based in Canada, enter your nine-digit Canadian Business Number (BN) issued by the CRA, Corporation/Incorporation Number, or Registry ID. <br>**Any other country/region**--Provide the Tax ID or Business Registration number. |
|Business address |Enter the address to match the address where your company is headquartered. |

### Step 3: Upload Supporting Documents

Submit documents that are up to 12 months old. A Registry extract copy should contain both the Company Name and the Tax ID/Business Registration Number. Other supporting documents are optional but recommended.

### Submit

After filling out all the applicable fields, select **Submit**.

Your KYC Status indicates *Submitted* and its information can no longer be modified without Microsoft Support intervention.

Status change notifications are sent to the email address provided. The Service Level Agreement for KYC approval or rejection is three days maximum.

Once your KYC is approved, move on to [Getting numbers with Microsoft Calling Plan](manage-phone-numbers-landing-page.md).

## KYC status definitions

KYC submittal status and status definitions are listed in the following table.

|Status |Description |
|:-----|:-----|
|Draft |The customer started a KYC request process but hasn't submitted it for vetting. |
|Submitted |The customer submitted the KYC request for the vetting process. Automated and manual checks by Microsoft are in progress. |
|Pending Customer Update |Microsoft determined additional information from the customer is required to approve the KYC request. Customer action required. |
|Approved |Microsoft successfully validated the KYC request. Customer is now able to acquire or port telephone numbers. |
|Denied |Microsoft determined the KYC request didn't pass the vetting process. No further action allowed. |

## Related articles

[Setting up Teams Phone](setting-up-your-phone-system.md)

[PSTN connectivity options](pstn-connectivity.md)

[Microsoft Teams Calling Plans](calling-plans-for-office-365.md)
