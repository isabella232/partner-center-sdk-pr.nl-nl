---
title: De geschiktheid voor abonnementsoverdracht van een klant ophalen
description: Een verzameling van de abonnementen van een klant ophalen die in aanmerking komen/ineligibile voor overdracht.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 43086a32fa0dbbdecf65aac167c687f26fc4c2c6
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767175"
---
# <a name="get-a-customers-subscriptions-transfer-eligibility"></a><span data-ttu-id="eaf6b-103">De geschiktheid voor abonnementsoverdracht van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="eaf6b-103">Get a customer's subscriptions transfer eligibility</span></span>

<span data-ttu-id="eaf6b-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="eaf6b-104">**Applies To**</span></span>

- <span data-ttu-id="eaf6b-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="eaf6b-105">Partner Center</span></span>

<span data-ttu-id="eaf6b-106">Een verzameling van de abonnementen van een klant ophalen die in aanmerking komen/niet in aanmerking komen voor overdracht.</span><span class="sxs-lookup"><span data-stu-id="eaf6b-106">How to get a collection of a customer's subscriptions that are eligible/ineligible for transfer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eaf6b-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="eaf6b-107">Prerequisites</span></span>

- <span data-ttu-id="eaf6b-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="eaf6b-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="eaf6b-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="eaf6b-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="eaf6b-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eaf6b-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="eaf6b-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="eaf6b-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="eaf6b-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="eaf6b-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="eaf6b-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="eaf6b-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="eaf6b-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="eaf6b-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="eaf6b-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eaf6b-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="eaf6b-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="eaf6b-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="eaf6b-117">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="eaf6b-117">Request syntax</span></span>

| <span data-ttu-id="eaf6b-118">Methode</span><span class="sxs-lookup"><span data-stu-id="eaf6b-118">Method</span></span>  | <span data-ttu-id="eaf6b-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="eaf6b-119">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="eaf6b-120">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="eaf6b-120">**GET**</span></span> | <span data-ttu-id="eaf6b-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/transferseligibility? transferType = {overdracht-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="eaf6b-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/transferseligibility?transferType={transfer-type} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="eaf6b-122">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="eaf6b-122">URI parameter</span></span>

<span data-ttu-id="eaf6b-123">Deze tabel bevat de vereiste query parameter om alle abonnementen op te halen.</span><span class="sxs-lookup"><span data-stu-id="eaf6b-123">This table lists the required query parameter to get all the subscriptions.</span></span>

| <span data-ttu-id="eaf6b-124">Naam</span><span class="sxs-lookup"><span data-stu-id="eaf6b-124">Name</span></span>               | <span data-ttu-id="eaf6b-125">Type</span><span class="sxs-lookup"><span data-stu-id="eaf6b-125">Type</span></span>   | <span data-ttu-id="eaf6b-126">Vereist</span><span class="sxs-lookup"><span data-stu-id="eaf6b-126">Required</span></span> | <span data-ttu-id="eaf6b-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="eaf6b-127">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="eaf6b-128">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="eaf6b-128">customer-tenant-id</span></span> | <span data-ttu-id="eaf6b-129">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="eaf6b-129">string</span></span> | <span data-ttu-id="eaf6b-130">Yes</span><span class="sxs-lookup"><span data-stu-id="eaf6b-130">Yes</span></span>      | <span data-ttu-id="eaf6b-131">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="eaf6b-131">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="eaf6b-132">overdracht-type</span><span class="sxs-lookup"><span data-stu-id="eaf6b-132">transfer-type</span></span>      | <span data-ttu-id="eaf6b-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="eaf6b-133">string</span></span> | <span data-ttu-id="eaf6b-134">Yes</span><span class="sxs-lookup"><span data-stu-id="eaf6b-134">Yes</span></span>      | <span data-ttu-id="eaf6b-135">Het type overdracht dat is bedoeld.</span><span class="sxs-lookup"><span data-stu-id="eaf6b-135">The type of transfer that is intended.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="eaf6b-136">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="eaf6b-136">Request headers</span></span>

<span data-ttu-id="eaf6b-137">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="eaf6b-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="eaf6b-138">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="eaf6b-138">Request body</span></span>

<span data-ttu-id="eaf6b-139">Geen.</span><span class="sxs-lookup"><span data-stu-id="eaf6b-139">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="eaf6b-140">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="eaf6b-140">Request example</span></span>

```http
GET /v1/customers/823c6c3f-9259-4d51-bae2-5dd06743177f/transferseligibility?transferType=directtoindirect HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 202b5e9a-ae82-4ab9-8a0a-f4e9e04eb14d
MS-CorrelationId: cd589c16-dc94-49ad-e529-125c258573d6
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="eaf6b-141">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="eaf6b-141">REST response</span></span>

<span data-ttu-id="eaf6b-142">Als dit lukt, retourneert deze methode een verzameling [TransferEligibility](transfer-eligibility-resources.md) -resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="eaf6b-142">If successful, this method returns a collection of [TransferEligibility](transfer-eligibility-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="eaf6b-143">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="eaf6b-143">Response success and error codes</span></span>

<span data-ttu-id="eaf6b-144">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="eaf6b-144">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="eaf6b-145">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="eaf6b-145">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="eaf6b-146">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="eaf6b-146">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="eaf6b-147">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="eaf6b-147">Response example</span></span>

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
