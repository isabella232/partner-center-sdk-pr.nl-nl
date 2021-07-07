---
title: Overeenkomstbronnen
description: De overeenkomstresource vertegenwoordigt een Microsoft Cloud-klantovereenkomst met details van de certificering die door de partner wordt geleverd.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 5fa196e711d9ff899b61ba20e75edd92749165e5
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025613"
---
# <a name="agreement-resources-representing-a-microsoft-cloud-customer-agreement"></a><span data-ttu-id="288b9-103">Overeenkomstbronnen die een Microsoft Cloud-klantovereenkomst vertegenwoordigen</span><span class="sxs-lookup"><span data-stu-id="288b9-103">Agreement resources representing a Microsoft cloud customer agreement</span></span>

<span data-ttu-id="288b9-104">**Van toepassing op**: Partner Center</span><span class="sxs-lookup"><span data-stu-id="288b9-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="288b9-105">**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="288b9-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="288b9-106">De **overeenkomstresource** wordt momenteel alleen ondersteund door Partner Center in de openbare Cloud van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="288b9-106">The **Agreement** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="288b9-107">De **overeenkomstresource** vertegenwoordigt een Microsoft Cloud-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="288b9-107">The **Agreement** resource represents a Microsoft cloud customer agreement.</span></span>

## <a name="agreement"></a><span data-ttu-id="288b9-108">Overeenkomst</span><span class="sxs-lookup"><span data-stu-id="288b9-108">Agreement</span></span>

<span data-ttu-id="288b9-109">De **overeenkomstresource** vertegenwoordigt de details van de certificering die door de partner wordt geleverd.</span><span class="sxs-lookup"><span data-stu-id="288b9-109">The **Agreement** resource represents the details of certification provided by the partner.</span></span>

| <span data-ttu-id="288b9-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="288b9-110">Property</span></span>       | <span data-ttu-id="288b9-111">Type</span><span class="sxs-lookup"><span data-stu-id="288b9-111">Type</span></span>   | <span data-ttu-id="288b9-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="288b9-112">Description</span></span>                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="288b9-113">userId</span><span class="sxs-lookup"><span data-stu-id="288b9-113">userId</span></span>         | <span data-ttu-id="288b9-114">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="288b9-114">string</span></span>                         | <span data-ttu-id="288b9-115">Object-id van de aangemelde gebruiker in de partner-tenant die namens de partnerorganisatie een bevestiging geeft.</span><span class="sxs-lookup"><span data-stu-id="288b9-115">Object identifier of the logged-in user in the partner tenant who is providing confirmation on behalf of the partner organization.</span></span> <span data-ttu-id="288b9-116">Wanneer u app+gebruikersverificatie gebruikt om een overeenkomstresource te maken, wordt Partner Center kenmerkwaarde **userId** automatisch afgeleid van het token App+Gebruiker.</span><span class="sxs-lookup"><span data-stu-id="288b9-116">When using App+User authentication to create an Agreement resource, Partner Center automatically derives the **userId** attribute value from the App+User token.</span></span>                                                                             |
| <span data-ttu-id="288b9-117">primaryContact</span><span class="sxs-lookup"><span data-stu-id="288b9-117">primaryContact</span></span> | [<span data-ttu-id="288b9-118">Contact</span><span class="sxs-lookup"><span data-stu-id="288b9-118">Contact</span></span>](./utility-resources.md#contact) | <span data-ttu-id="288b9-119">Informatie over de gebruiker van de klantorganisatie die de overeenkomst heeft geaccepteerd, waaronder:  **firstName,** **lastName,** **email** en **phoneNumber** (optioneel).</span><span class="sxs-lookup"><span data-stu-id="288b9-119">Information about the user from the customer organization that accepted the agreement, including:  **firstName**, **lastName**, **email**, and **phoneNumber** (optional).</span></span> |
| <span data-ttu-id="288b9-120">dateAgreed</span><span class="sxs-lookup"><span data-stu-id="288b9-120">dateAgreed</span></span>     | <span data-ttu-id="288b9-121">tekenreeks in UTC-datum/tijd-indeling</span><span class="sxs-lookup"><span data-stu-id="288b9-121">string in UTC date time format</span></span> | <span data-ttu-id="288b9-122">De datum waarop de klant de overeenkomst heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="288b9-122">The date when the customer accepted the agreement.</span></span>                                 |
| <span data-ttu-id="288b9-123">templateId</span><span class="sxs-lookup"><span data-stu-id="288b9-123">templateId</span></span>     |<span data-ttu-id="288b9-124">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="288b9-124">string</span></span>                          | <span data-ttu-id="288b9-125">De unieke id van de overeenkomst die de klant heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="288b9-125">Unique identifier of the agreement that the customer accepted.</span></span> |
| <span data-ttu-id="288b9-126">type</span><span class="sxs-lookup"><span data-stu-id="288b9-126">type</span></span>           |<span data-ttu-id="288b9-127">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="288b9-127">string</span></span>                          | <span data-ttu-id="288b9-128">Overeenkomsttype.</span><span class="sxs-lookup"><span data-stu-id="288b9-128">Agreement type.</span></span> <span data-ttu-id="288b9-129">Momenteel zijn de ondersteunde **waarden MicrosoftCloudAgreement** **en MicrosoftCustomerAgreement**.</span><span class="sxs-lookup"><span data-stu-id="288b9-129">Currently, supported values include **MicrosoftCloudAgreement** and **MicrosoftCustomerAgreement**.</span></span>|
| <span data-ttu-id="288b9-130">agreementLink</span><span class="sxs-lookup"><span data-stu-id="288b9-130">agreementLink</span></span>  | <span data-ttu-id="288b9-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="288b9-131">string</span></span>                         | <span data-ttu-id="288b9-132">URL voor de overeenkomstsjabloon.</span><span class="sxs-lookup"><span data-stu-id="288b9-132">URL for the agreement template.</span></span>                                                    |
