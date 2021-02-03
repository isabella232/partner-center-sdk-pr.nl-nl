---
title: Overeenkomst bronnen
description: De overeenkomst resource vertegenwoordigt een micro soft Cloud-klant overeenkomst met details van certificering van de partner.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: d964b1c7c6d70814ef68e48f05611ecbb113c8fe
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2020
ms.locfileid: "97767601"
---
# <a name="agreement-resources-representing-a-microsoft-cloud-customer-agreement"></a><span data-ttu-id="fa8a1-103">Overeenkomst bronnen die een micro soft-Cloud klant overeenkomst vertegenwoordigen</span><span class="sxs-lookup"><span data-stu-id="fa8a1-103">Agreement resources representing a Microsoft cloud customer agreement</span></span>

<span data-ttu-id="fa8a1-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="fa8a1-104">**Applies to:**</span></span>

- <span data-ttu-id="fa8a1-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="fa8a1-105">Partner Center</span></span>

<span data-ttu-id="fa8a1-106">De bron van de **overeenkomst** wordt momenteel alleen ondersteund door het partner centrum in de open bare cloud van micro soft.</span><span class="sxs-lookup"><span data-stu-id="fa8a1-106">The **Agreement** resource is currently supported by Partner Center in the Microsoft public cloud only.</span></span> <span data-ttu-id="fa8a1-107">Het is niet van toepassing op:</span><span class="sxs-lookup"><span data-stu-id="fa8a1-107">It isn't applicable to:</span></span>

- <span data-ttu-id="fa8a1-108">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="fa8a1-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="fa8a1-109">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="fa8a1-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="fa8a1-110">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="fa8a1-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="fa8a1-111">De **overeenkomst** resource vertegenwoordigt een micro soft-Cloud-klant overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="fa8a1-111">The **Agreement** resource represents a Microsoft cloud customer agreement.</span></span>

## <a name="agreement"></a><span data-ttu-id="fa8a1-112">Overeenkomst</span><span class="sxs-lookup"><span data-stu-id="fa8a1-112">Agreement</span></span>

<span data-ttu-id="fa8a1-113">De **overeenkomst** resource bevat de details van de certificering die is verschaft door de partner.</span><span class="sxs-lookup"><span data-stu-id="fa8a1-113">The **Agreement** resource represents the details of certification provided by the partner.</span></span>

| <span data-ttu-id="fa8a1-114">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="fa8a1-114">Property</span></span>       | <span data-ttu-id="fa8a1-115">Type</span><span class="sxs-lookup"><span data-stu-id="fa8a1-115">Type</span></span>   | <span data-ttu-id="fa8a1-116">Description</span><span class="sxs-lookup"><span data-stu-id="fa8a1-116">Description</span></span>                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fa8a1-117">userId</span><span class="sxs-lookup"><span data-stu-id="fa8a1-117">userId</span></span>         | <span data-ttu-id="fa8a1-118">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fa8a1-118">string</span></span>                         | <span data-ttu-id="fa8a1-119">De object-id van de aangemelde gebruiker in de partner-Tenant die een bevestiging verstrekt namens de partner organisatie.</span><span class="sxs-lookup"><span data-stu-id="fa8a1-119">Object identifier of the logged-in user in the partner tenant who is providing confirmation on behalf of the partner organization.</span></span> <span data-ttu-id="fa8a1-120">Wanneer u app + gebruikers authenticatie gebruikt voor het maken van een overeenkomst resource, wordt in het partner centrum automatisch de kenmerk- **id** van het gebruikers token van de app + gebruiker afgeleid.</span><span class="sxs-lookup"><span data-stu-id="fa8a1-120">When using App+User authentication to create an Agreement resource, Partner Center automatically derives the **userId** attribute value from the App+User token.</span></span>                                                                             |
| <span data-ttu-id="fa8a1-121">primaryContact</span><span class="sxs-lookup"><span data-stu-id="fa8a1-121">primaryContact</span></span> | [<span data-ttu-id="fa8a1-122">Contact</span><span class="sxs-lookup"><span data-stu-id="fa8a1-122">Contact</span></span>](./utility-resources.md#contact) | <span data-ttu-id="fa8a1-123">Informatie over de gebruiker van de organisatie van de klant die de overeenkomst heeft geaccepteerd, waaronder:  **FirstName**, **LastName**, **email** en **phonenumber** (optioneel).</span><span class="sxs-lookup"><span data-stu-id="fa8a1-123">Information about the user from the customer organization that accepted the agreement, including:  **firstName**, **lastName**, **email**, and **phoneNumber** (optional).</span></span> |
| <span data-ttu-id="fa8a1-124">dateAgreed</span><span class="sxs-lookup"><span data-stu-id="fa8a1-124">dateAgreed</span></span>     | <span data-ttu-id="fa8a1-125">teken reeks in UTC-datum tijd notatie</span><span class="sxs-lookup"><span data-stu-id="fa8a1-125">string in UTC date time format</span></span> | <span data-ttu-id="fa8a1-126">De datum waarop de klant de overeenkomst heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="fa8a1-126">The date when the customer accepted the agreement.</span></span>                                 |
| <span data-ttu-id="fa8a1-127">Ontbrekende templateid</span><span class="sxs-lookup"><span data-stu-id="fa8a1-127">templateId</span></span>     |<span data-ttu-id="fa8a1-128">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fa8a1-128">string</span></span>                          | <span data-ttu-id="fa8a1-129">De unieke id van de overeenkomst die de klant heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="fa8a1-129">Unique identifier of the agreement that the customer accepted.</span></span> |
| <span data-ttu-id="fa8a1-130">type</span><span class="sxs-lookup"><span data-stu-id="fa8a1-130">type</span></span>           |<span data-ttu-id="fa8a1-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fa8a1-131">string</span></span>                          | <span data-ttu-id="fa8a1-132">Type overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="fa8a1-132">Agreement type.</span></span> <span data-ttu-id="fa8a1-133">Op dit moment worden de volgende waarden ondersteund: **MicrosoftCloudAgreement** en **MicrosoftCustomerAgreement**.</span><span class="sxs-lookup"><span data-stu-id="fa8a1-133">Currently, supported values include **MicrosoftCloudAgreement** and **MicrosoftCustomerAgreement**.</span></span>|
| <span data-ttu-id="fa8a1-134">agreementLink</span><span class="sxs-lookup"><span data-stu-id="fa8a1-134">agreementLink</span></span>  | <span data-ttu-id="fa8a1-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fa8a1-135">string</span></span>                         | <span data-ttu-id="fa8a1-136">URL voor de overeenkomst sjabloon.</span><span class="sxs-lookup"><span data-stu-id="fa8a1-136">URL for the agreement template.</span></span>                                                    |
