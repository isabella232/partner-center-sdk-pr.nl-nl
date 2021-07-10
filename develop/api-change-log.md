---
title: REST API-wijzigingenlogboek voor Partnercentrum
description: Deze pagina bevat wijzigingen in de Partner Center REST API's
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.topic: reference
ms.date: 12/15/2020
ms.openlocfilehash: d4f7f034a36a26b6219086ca952b189f7a313ef7
ms.sourcegitcommit: 51237e7e98d71a7e0590b4d6a4034b6409542126
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2021
ms.locfileid: "113571992"
---
# <a name="december-2020-changes-to-partner-center-rest-apis"></a><span data-ttu-id="572e0-103">Wijzigingen van december 2020 in Partner Center REST API's</span><span class="sxs-lookup"><span data-stu-id="572e0-103">December 2020 changes to Partner Center REST APIs</span></span>

<span data-ttu-id="572e0-104">Kijk hier voor wijzigingen in Partner Center REST API's.</span><span class="sxs-lookup"><span data-stu-id="572e0-104">Check here for changes to Partner Center REST APIs.</span></span>

## <a name="enhancements-to-education-pricing-eligibility-apis"></a><span data-ttu-id="572e0-105">Verbeteringen in de education pricing Eligibility API's</span><span class="sxs-lookup"><span data-stu-id="572e0-105">Enhancements to education pricing Eligibility APIs</span></span>



### <a name="what-has-changed"></a><span data-ttu-id="572e0-106">Wat is er veranderd?</span><span class="sxs-lookup"><span data-stu-id="572e0-106">What has changed?</span></span>

<span data-ttu-id="572e0-107">Momenteel heeft de Partner Center-API de kwalificaties GET en PUT om te controleren of Education-klanten in aanmerking komen.</span><span class="sxs-lookup"><span data-stu-id="572e0-107">Currently, the Partner Center API has GET and PUT qualifications to verify Education customers’ eligibility.</span></span> <span data-ttu-id="572e0-108">Er worden geen wijzigingen aangebracht in de GET Kwalificatie-API.</span><span class="sxs-lookup"><span data-stu-id="572e0-108">There will be no changes to the GET Qualification API.</span></span> <span data-ttu-id="572e0-109">We hebben echter een retourcase toegevoegd aan de PUT Kwalificatie-API.</span><span class="sxs-lookup"><span data-stu-id="572e0-109">However, we’ve added a return case to the PUT Qualification API.</span></span>

- <span data-ttu-id="572e0-110">GET: verandert niet.</span><span class="sxs-lookup"><span data-stu-id="572e0-110">GET - doesn't change.</span></span>
- <span data-ttu-id="572e0-111">PUT: retourcase wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="572e0-111">PUT - return case will be added.</span></span>

<span data-ttu-id="572e0-112">Deze API's worden eind februari 2021 uit gebruik genomen om te worden vervangen door nieuwe API's, zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="572e0-112">These APIs will be retired at the end of February 2021, to be replaced by new APIs as described below.</span></span>

### <a name="scenarios-impacted"></a><span data-ttu-id="572e0-113">Scenario's die worden beïnvloed:</span><span class="sxs-lookup"><span data-stu-id="572e0-113">Scenarios impacted:</span></span>

<span data-ttu-id="572e0-114">Klant in aanmerking komen voor onderwijsprijzen voor bepaalde SKU's</span><span class="sxs-lookup"><span data-stu-id="572e0-114">Customer eligibility for education pricing on select SKUs</span></span>

### <a name="detail-descriptions"></a><span data-ttu-id="572e0-115">Beschrijvingen van details</span><span class="sxs-lookup"><span data-stu-id="572e0-115">Detail descriptions</span></span>

<span data-ttu-id="572e0-116">Er worden twee nieuwe API's voor GET- en POST-kwalificaties geïntroduceerd.</span><span class="sxs-lookup"><span data-stu-id="572e0-116">Two new GET and POST Qualifications APIs will be introduced.</span></span> <span data-ttu-id="572e0-117">De nieuwe API's gebruiken **Kwalificaties,** niet **Kwalificatie.**</span><span class="sxs-lookup"><span data-stu-id="572e0-117">The new APIs will be using **Qualifications**, not **Qualification**.</span></span> <span data-ttu-id="572e0-118">De API's zijn beschikbaar voor testen in FY21 Q2.</span><span class="sxs-lookup"><span data-stu-id="572e0-118">The APIs will be available for testing in FY21 Q2.</span></span>

#### <a name="get-qualifications"></a><span data-ttu-id="572e0-119">GET Kwalificaties</span><span class="sxs-lookup"><span data-stu-id="572e0-119">GET Qualifications</span></span>

```http
GET {customer_id}/qualifications
```

#### <a name="response-example"></a><span data-ttu-id="572e0-120">Voorbeeldantwoord:</span><span class="sxs-lookup"><span data-stu-id="572e0-120">Response example:</span></span>

```json
{
  "Qualification": "Education",
  "VettingStatus": "Denied",
  "VettingReason": "Not an education customer",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

#### <a name="response-fields"></a><span data-ttu-id="572e0-121">Antwoordvelden:</span><span class="sxs-lookup"><span data-stu-id="572e0-121">Response fields:</span></span> 

- <span data-ttu-id="572e0-122">Waarden voor VettingStatus: Approved, Denied, InReview, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="572e0-122">VettingStatus values: Approved, Denied, InReview, etc.</span></span>

- <span data-ttu-id="572e0-123">VettingReason-waarden:</span><span class="sxs-lookup"><span data-stu-id="572e0-123">VettingReason values:</span></span>
   - <span data-ttu-id="572e0-124">Geen Education-klant</span><span class="sxs-lookup"><span data-stu-id="572e0-124">Not an Education Customer</span></span>
   - <span data-ttu-id="572e0-125">Geen Education-klant meer</span><span class="sxs-lookup"><span data-stu-id="572e0-125">No longer an Education Customer</span></span>
   - <span data-ttu-id="572e0-126">Geen education-klant - na beoordeling</span><span class="sxs-lookup"><span data-stu-id="572e0-126">Not an Education Customer - After Review</span></span>
   - <span data-ttu-id="572e0-127">Beperkte toegang tot onderwijsklant</span><span class="sxs-lookup"><span data-stu-id="572e0-127">Restricted being an Education Customer</span></span>
   - <span data-ttu-id="572e0-128">Geen academische domein</span><span class="sxs-lookup"><span data-stu-id="572e0-128">Not an Academic Domain</span></span>
   - <span data-ttu-id="572e0-129">Geen in aanmerking komende bibliotheek</span><span class="sxs-lookup"><span data-stu-id="572e0-129">Not an eligible Library</span></span>
   - <span data-ttu-id="572e0-130">Geen in aanmerking komende Moet</span><span class="sxs-lookup"><span data-stu-id="572e0-130">Not an eligible Museum</span></span>
 
#### <a name="post-qualifications"></a><span data-ttu-id="572e0-131">POST-kwalificaties</span><span class="sxs-lookup"><span data-stu-id="572e0-131">POST Qualifications</span></span>

```http
POST {customer_id}/qualifications
    [
            "Qualification": "Education"
    ]
```

#### <a name="response-example"></a><span data-ttu-id="572e0-132">Voorbeeldantwoord:</span><span class="sxs-lookup"><span data-stu-id="572e0-132">Response example:</span></span>

```JSON
{
  "Qualification": "Education",
  "VettingStatus": "InReview",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

## <a name="next-steps"></a><span data-ttu-id="572e0-133">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="572e0-133">Next steps</span></span>

[<span data-ttu-id="572e0-134">REST API-verwijzing voor Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="572e0-134">Partner Center REST API reference</span></span>](partner-center-rest-api-reference.md)
