---
title: REST API-wijzigingenlogboek voor Partnercentrum
description: Deze pagina bevat wijzigingen in de REST Api's van het Partner Center
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.topic: reference
ms.date: 12/15/2020
ms.openlocfilehash: b2c2cac36a8bd1bec7aa5bf6e5d1aa73b4779535
ms.sourcegitcommit: 717e483a6eec23607b4e31ddfaa3e2691f3043e6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104711845"
---
# <a name="december-2020-changes-to-partner-center-rest-apis"></a><span data-ttu-id="d557e-103">Wijzigingen van 2020 december voor het Partner Center REST-Api's</span><span class="sxs-lookup"><span data-stu-id="d557e-103">December 2020 changes to Partner Center REST APIs</span></span>

<span data-ttu-id="d557e-104">Schakel dit selectie vakje in als u de REST-Api's van het partner centrum wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="d557e-104">Check here for changes to Partner Center REST APIs.</span></span>

## <a name="enhancements-to-education-pricing-eligibility-apis"></a><span data-ttu-id="d557e-105">Verbeteringen van de geschiktheids-Api's voor onderwijs prijzen</span><span class="sxs-lookup"><span data-stu-id="d557e-105">Enhancements to education pricing Eligibility APIs</span></span>



### <a name="what-has-changed"></a><span data-ttu-id="d557e-106">Wat is er gewijzigd?</span><span class="sxs-lookup"><span data-stu-id="d557e-106">What has changed?</span></span>

<span data-ttu-id="d557e-107">Op dit moment heeft de partner centrum-API de mogelijkheid om de geschiktheid van het onderwijs klanten te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="d557e-107">Currently, the Partner Center API has GET and PUT qualifications to verify Education customers’ eligibility.</span></span> <span data-ttu-id="d557e-108">Er worden geen wijzigingen aangebracht in de kwalificatie-API ophalen.</span><span class="sxs-lookup"><span data-stu-id="d557e-108">There will be no changes to the GET Qualification API.</span></span> <span data-ttu-id="d557e-109">We hebben echter een retour Case toegevoegd aan de PUT-kwalificatie-API.</span><span class="sxs-lookup"><span data-stu-id="d557e-109">However, we’ve added a return case to the PUT Qualification API.</span></span>

- <span data-ttu-id="d557e-110">GET-wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="d557e-110">GET - doesn't change.</span></span> [<span data-ttu-id="d557e-111">Huidige API-artikel</span><span class="sxs-lookup"><span data-stu-id="d557e-111">Current API article</span></span>](./get-customer-qualification-synchronous.md)
- <span data-ttu-id="d557e-112">Er wordt een case met de waarde PUT toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="d557e-112">PUT - return case will be added.</span></span> [<span data-ttu-id="d557e-113">Huidige API-artikel</span><span class="sxs-lookup"><span data-stu-id="d557e-113">Current API article</span></span>](./update-customer-qualification-synchronous.md)

<span data-ttu-id="d557e-114">Deze Api's worden aan het einde van februari 2021 verwijderd en vervangen door nieuwe Api's, zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="d557e-114">These APIs will be retired at the end of February 2021, to be replaced by new APIs as described below.</span></span>

### <a name="scenarios-impacted"></a><span data-ttu-id="d557e-115">Getroffen scenario's:</span><span class="sxs-lookup"><span data-stu-id="d557e-115">Scenarios impacted:</span></span>

<span data-ttu-id="d557e-116">Klant geschiktheid voor onderwijs prijzen voor Select Sku's</span><span class="sxs-lookup"><span data-stu-id="d557e-116">Customer eligibility for education pricing on select SKUs</span></span>

### <a name="detail-descriptions"></a><span data-ttu-id="d557e-117">Gedetailleerde beschrijvingen</span><span class="sxs-lookup"><span data-stu-id="d557e-117">Detail descriptions</span></span>

<span data-ttu-id="d557e-118">Er worden twee nieuwe GET-en POST-kwalificaties-Api's geïntroduceerd.</span><span class="sxs-lookup"><span data-stu-id="d557e-118">Two new GET and POST Qualifications APIs will be introduced.</span></span> <span data-ttu-id="d557e-119">De nieuwe Api's maken gebruik van **kwalificaties**, geen **Kwalificatie**.</span><span class="sxs-lookup"><span data-stu-id="d557e-119">The new APIs will be using **Qualifications**, not **Qualification**.</span></span> <span data-ttu-id="d557e-120">De Api's zijn beschikbaar voor testen in FY21 Q2.</span><span class="sxs-lookup"><span data-stu-id="d557e-120">The APIs will be available for testing in FY21 Q2.</span></span>

#### <a name="get-qualifications"></a><span data-ttu-id="d557e-121">Kwalificaties ophalen</span><span class="sxs-lookup"><span data-stu-id="d557e-121">GET Qualifications</span></span>

```http
GET {customer_id}/qualifications
```

#### <a name="response-example"></a><span data-ttu-id="d557e-122">Voorbeeldantwoord:</span><span class="sxs-lookup"><span data-stu-id="d557e-122">Response example:</span></span>

```json
{
  "Qualification": "Education",
  "VettingStatus": "Denied",
  "VettingReason": "Not an education customer",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

#### <a name="response-fields"></a><span data-ttu-id="d557e-123">Antwoord velden:</span><span class="sxs-lookup"><span data-stu-id="d557e-123">Response fields:</span></span> 

- <span data-ttu-id="d557e-124">VettingStatus waarden: goedgekeurd, geweigerd, inbeoordeling enz.</span><span class="sxs-lookup"><span data-stu-id="d557e-124">VettingStatus values: Approved, Denied, InReview, etc.</span></span>

- <span data-ttu-id="d557e-125">VettingReason waarden:</span><span class="sxs-lookup"><span data-stu-id="d557e-125">VettingReason values:</span></span>
   - <span data-ttu-id="d557e-126">Geen onderwijs klant</span><span class="sxs-lookup"><span data-stu-id="d557e-126">Not an Education Customer</span></span>
   - <span data-ttu-id="d557e-127">Geen onderwijs gebruiker meer</span><span class="sxs-lookup"><span data-stu-id="d557e-127">No longer an Education Customer</span></span>
   - <span data-ttu-id="d557e-128">Geen onderwijs klant-na beoordeling</span><span class="sxs-lookup"><span data-stu-id="d557e-128">Not an Education Customer - After Review</span></span>
   - <span data-ttu-id="d557e-129">Alleen een onderwijs gebruiker</span><span class="sxs-lookup"><span data-stu-id="d557e-129">Restricted being an Education Customer</span></span>
   - <span data-ttu-id="d557e-130">Geen academisch domein</span><span class="sxs-lookup"><span data-stu-id="d557e-130">Not an Academic Domain</span></span>
   - <span data-ttu-id="d557e-131">Geen beschik bare bibliotheek</span><span class="sxs-lookup"><span data-stu-id="d557e-131">Not an eligible Library</span></span>
   - <span data-ttu-id="d557e-132">Geen in aanmerking komend Museum</span><span class="sxs-lookup"><span data-stu-id="d557e-132">Not an eligible Museum</span></span>
 
#### <a name="post-qualifications"></a><span data-ttu-id="d557e-133">BERICHT kwalificaties</span><span class="sxs-lookup"><span data-stu-id="d557e-133">POST Qualifications</span></span>

```http
POST {customer_id}/qualifications
    [
            "Qualification": "Education"
    ]
```

#### <a name="response-example"></a><span data-ttu-id="d557e-134">Voorbeeldantwoord:</span><span class="sxs-lookup"><span data-stu-id="d557e-134">Response example:</span></span>

```JSON
{
  "Qualification": "Education",
  "VettingStatus": "InReview",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

## <a name="next-steps"></a><span data-ttu-id="d557e-135">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="d557e-135">Next steps</span></span>

[<span data-ttu-id="d557e-136">REST API-verwijzing voor Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="d557e-136">Partner Center REST API reference</span></span>](partner-center-rest-api-reference.md)