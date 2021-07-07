---
title: De geschiktheid voor abonnementsoverdracht van een klant ophalen
description: Een verzameling ophalen van de abonnementen van een klant die in aanmerking komen/in aanmerking komen voor overdracht.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: fe8af76d1e1456754dec79291ec0853fb253d108
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446289"
---
# <a name="get-a-customers-subscriptions-transfer-eligibility"></a><span data-ttu-id="3b44d-103">De geschiktheid voor abonnementsoverdracht van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="3b44d-103">Get a customer's subscriptions transfer eligibility</span></span>

<span data-ttu-id="3b44d-104">Een verzameling van de abonnementen van een klant ophalen die in aanmerking komen/niet in aanmerking komen voor overdracht.</span><span class="sxs-lookup"><span data-stu-id="3b44d-104">How to get a collection of a customer's subscriptions that are eligible/ineligible for transfer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3b44d-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3b44d-105">Prerequisites</span></span>

- <span data-ttu-id="3b44d-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3b44d-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="3b44d-107">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="3b44d-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="3b44d-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3b44d-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="3b44d-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="3b44d-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="3b44d-110">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="3b44d-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="3b44d-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="3b44d-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="3b44d-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="3b44d-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="3b44d-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3b44d-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="3b44d-114">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="3b44d-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3b44d-115">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="3b44d-115">Request syntax</span></span>

| <span data-ttu-id="3b44d-116">Methode</span><span class="sxs-lookup"><span data-stu-id="3b44d-116">Method</span></span>  | <span data-ttu-id="3b44d-117">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="3b44d-117">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3b44d-118">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="3b44d-118">**GET**</span></span> | <span data-ttu-id="3b44d-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/transferseligibility?transferType={transfer-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="3b44d-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/transferseligibility?transferType={transfer-type} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="3b44d-120">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="3b44d-120">URI parameter</span></span>

<span data-ttu-id="3b44d-121">Deze tabel bevat de vereiste queryparameter om alle abonnementen op te halen.</span><span class="sxs-lookup"><span data-stu-id="3b44d-121">This table lists the required query parameter to get all the subscriptions.</span></span>

| <span data-ttu-id="3b44d-122">Naam</span><span class="sxs-lookup"><span data-stu-id="3b44d-122">Name</span></span>               | <span data-ttu-id="3b44d-123">Type</span><span class="sxs-lookup"><span data-stu-id="3b44d-123">Type</span></span>   | <span data-ttu-id="3b44d-124">Vereist</span><span class="sxs-lookup"><span data-stu-id="3b44d-124">Required</span></span> | <span data-ttu-id="3b44d-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3b44d-125">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="3b44d-126">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="3b44d-126">customer-tenant-id</span></span> | <span data-ttu-id="3b44d-127">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3b44d-127">string</span></span> | <span data-ttu-id="3b44d-128">Ja</span><span class="sxs-lookup"><span data-stu-id="3b44d-128">Yes</span></span>      | <span data-ttu-id="3b44d-129">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="3b44d-129">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="3b44d-130">overdrachtstype</span><span class="sxs-lookup"><span data-stu-id="3b44d-130">transfer-type</span></span>      | <span data-ttu-id="3b44d-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3b44d-131">string</span></span> | <span data-ttu-id="3b44d-132">Ja</span><span class="sxs-lookup"><span data-stu-id="3b44d-132">Yes</span></span>      | <span data-ttu-id="3b44d-133">Het type overdracht dat is bedoeld.</span><span class="sxs-lookup"><span data-stu-id="3b44d-133">The type of transfer that is intended.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="3b44d-134">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="3b44d-134">Request headers</span></span>

<span data-ttu-id="3b44d-135">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="3b44d-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3b44d-136">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="3b44d-136">Request body</span></span>

<span data-ttu-id="3b44d-137">Geen.</span><span class="sxs-lookup"><span data-stu-id="3b44d-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="3b44d-138">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3b44d-138">Request example</span></span>

```http
GET /v1/customers/823c6c3f-9259-4d51-bae2-5dd06743177f/transferseligibility?transferType=directtoindirect HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 202b5e9a-ae82-4ab9-8a0a-f4e9e04eb14d
MS-CorrelationId: cd589c16-dc94-49ad-e529-125c258573d6
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="3b44d-139">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="3b44d-139">REST response</span></span>

<span data-ttu-id="3b44d-140">Als dit lukt, retourneert deze methode een verzameling [TransferEligibility-resources](transfer-eligibility-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="3b44d-140">If successful, this method returns a collection of [TransferEligibility](transfer-eligibility-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3b44d-141">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="3b44d-141">Response success and error codes</span></span>

<span data-ttu-id="3b44d-142">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="3b44d-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="3b44d-143">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="3b44d-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3b44d-144">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="3b44d-144">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="3b44d-145">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="3b44d-145">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 73754
Content-Type: application/json
MS-CorrelationId: cd589c16-dc94-49ad-e529-125c258573d6
MS-RequestId: 202b5e9a-ae82-4ab9-8a0a-f4e9e04eb14d
Date: Tue, 24 Mar 2020 23:43:25 GMT

[
  {
    "id": "548FA265-5F40-4765-9A6B-47826F72A4BF",
    "isEligible": false,
    "reason": "Subscription: 548FA265-5F40-4765-9A6B-47826F72A4BF is in state: Deleted"
  },
  {
    "id": "E2A3AEB3-70A7-42E3-930C-7519EEDDC45A",
    "isEligible": false,
    "reason": "Subscription: E2A3AEB3-70A7-42E3-930C-7519EEDDC45A is in state: Suspended"
  },
  {
    "id": "4B600A9A-DF56-4564-A75A-6CC6D2D0C9F9",
    "isEligible": false,
    "reason": "subscription is already part of another transfer request id : 31a06eac-c527-458a-a6b4-0de197a45996"
  },
  {
    "id": "D3350F46-AA29-4F6F-95A0-E3011988915C",
    "isEligible": true
  }
  {
    "id": "E82B2F4A-736A-4E2B-955C-C1A4C56C0171",
    "isEligible": true
  }
]
```
