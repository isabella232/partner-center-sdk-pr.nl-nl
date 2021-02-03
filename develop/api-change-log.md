---
title: REST API-wijzigingenlogboek voor Partnercentrum
description: Deze pagina bevat wijzigingen in de REST Api's van het Partner Center
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.topic: reference
ms.date: 12/15/2020
ms.openlocfilehash: 79359414276a1259117a8f506bbfae4441cdcbed
ms.sourcegitcommit: f8ca3a14a763013fefafd3262d0a740881d1d7b1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/17/2020
ms.locfileid: "97768685"
---
# <a name="december-2020-changes-to-partner-center-rest-apis"></a><span data-ttu-id="25036-103">Wijzigingen van 2020 december voor het Partner Center REST-Api's</span><span class="sxs-lookup"><span data-stu-id="25036-103">December 2020 changes to Partner Center REST APIs</span></span>

<span data-ttu-id="25036-104">Schakel dit selectie vakje in als u de REST-Api's van het partner centrum wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="25036-104">Check here for changes to Partner Center REST APIs.</span></span>

## <a name="enhancements-to-education-pricing-eligibility-apis"></a><span data-ttu-id="25036-105">Verbeteringen van de geschiktheids-Api's voor onderwijs prijzen</span><span class="sxs-lookup"><span data-stu-id="25036-105">Enhancements to education pricing Eligibility APIs</span></span>



### <a name="what-has-changed"></a><span data-ttu-id="25036-106">Wat is er gewijzigd?</span><span class="sxs-lookup"><span data-stu-id="25036-106">What has changed?</span></span>

<span data-ttu-id="25036-107">Op dit moment heeft de partner centrum-API de mogelijkheid om de geschiktheid van het onderwijs klanten te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="25036-107">Currently, the Partner Center API has GET and PUT qualifications to verify Education customers’ eligibility.</span></span> <span data-ttu-id="25036-108">Er worden geen wijzigingen aangebracht in de kwalificatie-API ophalen.</span><span class="sxs-lookup"><span data-stu-id="25036-108">There will be no changes to the GET Qualification API.</span></span> <span data-ttu-id="25036-109">We hebben echter een retour Case toegevoegd aan de PUT-kwalificatie-API.</span><span class="sxs-lookup"><span data-stu-id="25036-109">However, we’ve added a return case to the PUT Qualification API.</span></span>

- <span data-ttu-id="25036-110">GET-wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="25036-110">GET - doesn't change.</span></span> [<span data-ttu-id="25036-111">Huidige API-artikel</span><span class="sxs-lookup"><span data-stu-id="25036-111">Current API article</span></span>](get-a-customer-s-qualification.md)
- <span data-ttu-id="25036-112">Er wordt een case met de waarde PUT toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="25036-112">PUT - return case will be added.</span></span> [<span data-ttu-id="25036-113">Huidige API-artikel</span><span class="sxs-lookup"><span data-stu-id="25036-113">Current API article</span></span>](update-a-customer-s-qualification.md)

<span data-ttu-id="25036-114">Deze Api's worden aan het einde van februari 2021 verwijderd en vervangen door nieuwe Api's, zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="25036-114">These APIs will be retired at the end of February 2021, to be replaced by new APIs as described below.</span></span>

### <a name="scenarios-impacted"></a><span data-ttu-id="25036-115">Getroffen scenario's:</span><span class="sxs-lookup"><span data-stu-id="25036-115">Scenarios impacted:</span></span>

<span data-ttu-id="25036-116">Klant geschiktheid voor onderwijs prijzen voor Select Sku's</span><span class="sxs-lookup"><span data-stu-id="25036-116">Customer eligibility for education pricing on select SKUs</span></span>

### <a name="detail-descriptions"></a><span data-ttu-id="25036-117">Gedetailleerde beschrijvingen</span><span class="sxs-lookup"><span data-stu-id="25036-117">Detail descriptions</span></span>

<span data-ttu-id="25036-118">Er worden twee nieuwe GET-en POST-kwalificaties-Api's geïntroduceerd.</span><span class="sxs-lookup"><span data-stu-id="25036-118">Two new GET and POST Qualifications APIs will be introduced.</span></span> <span data-ttu-id="25036-119">De nieuwe Api's maken gebruik van **kwalificaties**, geen **Kwalificatie**.</span><span class="sxs-lookup"><span data-stu-id="25036-119">The new APIs will be using **Qualifications**, not **Qualification**.</span></span> <span data-ttu-id="25036-120">De Api's zijn beschikbaar voor testen in FY21 Q2.</span><span class="sxs-lookup"><span data-stu-id="25036-120">The APIs will be available for testing in FY21 Q2.</span></span>

#### <a name="get-qualifications"></a><span data-ttu-id="25036-121">Kwalificaties ophalen</span><span class="sxs-lookup"><span data-stu-id="25036-121">GET Qualifications</span></span>

```http
GET {customer_id}/qualifications
```

#### <a name="response-example"></a><span data-ttu-id="25036-122">Voorbeeldantwoord:</span><span class="sxs-lookup"><span data-stu-id="25036-122">Response example:</span></span>

```json
{
  "Qualification": "Education",
  "VettingStatus": "Denied",
  "VettingReason": "Not an education customer",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

#### <a name="response-fields"></a><span data-ttu-id="25036-123">Antwoord velden:</span><span class="sxs-lookup"><span data-stu-id="25036-123">Response fields:</span></span> 

- <span data-ttu-id="25036-124">VettingStatus waarden: goedgekeurd, geweigerd, inbeoordeling enz.</span><span class="sxs-lookup"><span data-stu-id="25036-124">VettingStatus values: Approved, Denied, InReview, etc.</span></span>

- <span data-ttu-id="25036-125">VettingReason waarden:</span><span class="sxs-lookup"><span data-stu-id="25036-125">VettingReason values:</span></span>
   - <span data-ttu-id="25036-126">Geen onderwijs klant</span><span class="sxs-lookup"><span data-stu-id="25036-126">Not an Education Customer</span></span>
   - <span data-ttu-id="25036-127">Geen onderwijs gebruiker meer</span><span class="sxs-lookup"><span data-stu-id="25036-127">No longer an Education Customer</span></span>
   - <span data-ttu-id="25036-128">Geen onderwijs klant-na beoordeling</span><span class="sxs-lookup"><span data-stu-id="25036-128">Not an Education Customer - After Review</span></span>
   - <span data-ttu-id="25036-129">Alleen een onderwijs gebruiker</span><span class="sxs-lookup"><span data-stu-id="25036-129">Restricted being an Education Customer</span></span>
   - <span data-ttu-id="25036-130">Geen academisch domein</span><span class="sxs-lookup"><span data-stu-id="25036-130">Not an Academic Domain</span></span>
   - <span data-ttu-id="25036-131">Geen beschik bare bibliotheek</span><span class="sxs-lookup"><span data-stu-id="25036-131">Not an eligible Library</span></span>
   - <span data-ttu-id="25036-132">Geen in aanmerking komend Museum</span><span class="sxs-lookup"><span data-stu-id="25036-132">Not an eligible Museum</span></span>
 
#### <a name="post-qualifications"></a><span data-ttu-id="25036-133">BERICHT kwalificaties</span><span class="sxs-lookup"><span data-stu-id="25036-133">POST Qualifications</span></span>

```http
POST {customer_id}/qualifications
    [
            "Qualification": "Education"
    ]
```

#### <a name="response-example"></a><span data-ttu-id="25036-134">Voorbeeldantwoord:</span><span class="sxs-lookup"><span data-stu-id="25036-134">Response example:</span></span>

```JSON
{
  "Qualification": "Education",
  "VettingStatus": "InReview",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

## <a name="next-steps"></a><span data-ttu-id="25036-135">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="25036-135">Next steps</span></span>

[<span data-ttu-id="25036-136">REST API-verwijzing voor Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="25036-136">Partner Center REST API reference</span></span>](partner-center-rest-api-reference.md)
