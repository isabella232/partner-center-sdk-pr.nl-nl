---
title: Koppelingen voor factuurramingen ophalen
description: U kunt een verzameling ramings koppelingen ophalen voor de details van het regel item van de query-afstemming.
ms.date: 09/24/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.assetid: ''
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 10801cdb1f9d4f50a1f8fc86c2d0eaf8610ed68c
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767267"
---
# <a name="get-invoice-estimate-links"></a><span data-ttu-id="ac70f-103">Koppelingen voor factuurramingen ophalen</span><span class="sxs-lookup"><span data-stu-id="ac70f-103">Get invoice estimate links</span></span>

<span data-ttu-id="ac70f-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="ac70f-104">**Applies to:**</span></span>

- <span data-ttu-id="ac70f-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="ac70f-105">Partner Center</span></span>
- <span data-ttu-id="ac70f-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="ac70f-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="ac70f-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="ac70f-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="ac70f-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="ac70f-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="ac70f-109">U kunt schattings koppelingen verkrijgen om de details van de query voor niet-gefactureerde reconciliatie regel items te controleren.</span><span class="sxs-lookup"><span data-stu-id="ac70f-109">You can get estimate links to help query details for unbilled reconciliation line items.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ac70f-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ac70f-110">Prerequisites</span></span>

- <span data-ttu-id="ac70f-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ac70f-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ac70f-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="ac70f-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="ac70f-113">Een factuur-ID.</span><span class="sxs-lookup"><span data-stu-id="ac70f-113">An invoice identifier.</span></span> <span data-ttu-id="ac70f-114">Hiermee wordt de factuur aangegeven waarvoor de regel items moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ac70f-114">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="ac70f-115">C\#</span><span class="sxs-lookup"><span data-stu-id="ac70f-115">C\#</span></span>

<span data-ttu-id="ac70f-116">De volgende voorbeeld code laat zien hoe u de ramings koppelingen kunt ophalen om niet-gefactureerde regel items voor een bepaalde valuta op te vragen.</span><span class="sxs-lookup"><span data-stu-id="ac70f-116">The following example code shows how you can get the estimate links to query unbilled line items for a given currency.</span></span> <span data-ttu-id="ac70f-117">Het antwoord bevat de ramings koppelingen voor elke periode (bijvoorbeeld de huidige en vorige maand).</span><span class="sxs-lookup"><span data-stu-id="ac70f-117">The response contains the estimate links for each period (for example, the current and previous month).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string curencyCode;

 // all the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
 IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// read estimate links for currencycode
var estimateLinks = scopedPartnerOperations.Invoices.Estimates.Links.ByCurrency(curencyCode).Get();
```

<span data-ttu-id="ac70f-118">Voor een vergelijkbaar voor beeld raadpleegt u het volgende:</span><span class="sxs-lookup"><span data-stu-id="ac70f-118">For a similar example, see the following:</span></span>

- <span data-ttu-id="ac70f-119">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="ac70f-119">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="ac70f-120">Project: **Partner Center SDK** -voor beelden</span><span class="sxs-lookup"><span data-stu-id="ac70f-120">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="ac70f-121">Klasse: **GetEstimatesLinks.cs**</span><span class="sxs-lookup"><span data-stu-id="ac70f-121">Class: **GetEstimatesLinks.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="ac70f-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="ac70f-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ac70f-123">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ac70f-123">Request syntax</span></span>

| <span data-ttu-id="ac70f-124">Methode</span><span class="sxs-lookup"><span data-stu-id="ac70f-124">Method</span></span>  | <span data-ttu-id="ac70f-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="ac70f-125">Request URI</span></span>                                                                                                 |
|---------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ac70f-126">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ac70f-126">**GET**</span></span> | <span data-ttu-id="ac70f-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/estimates/links? CurrencyCode = {CURRENCYCODE} http/1.1</span><span class="sxs-lookup"><span data-stu-id="ac70f-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/estimates/links?currencycode={currencycode} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="ac70f-128">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="ac70f-128">URI parameters</span></span>

<span data-ttu-id="ac70f-129">Gebruik de volgende URI en query parameter bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="ac70f-129">Use the following URI and query parameter when creating the request.</span></span>

| <span data-ttu-id="ac70f-130">Naam</span><span class="sxs-lookup"><span data-stu-id="ac70f-130">Name</span></span>                   | <span data-ttu-id="ac70f-131">Type</span><span class="sxs-lookup"><span data-stu-id="ac70f-131">Type</span></span>   | <span data-ttu-id="ac70f-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="ac70f-132">Required</span></span> | <span data-ttu-id="ac70f-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ac70f-133">Description</span></span>                                                       |
|------------------------|--------|----------|-------------------------------------------------------------------|
| <span data-ttu-id="ac70f-134">currencyCode</span><span class="sxs-lookup"><span data-stu-id="ac70f-134">currencyCode</span></span>           | <span data-ttu-id="ac70f-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ac70f-135">string</span></span> | <span data-ttu-id="ac70f-136">Yes</span><span class="sxs-lookup"><span data-stu-id="ac70f-136">Yes</span></span>      | <span data-ttu-id="ac70f-137">De valuta code voor de niet-gefactureerde regel items.</span><span class="sxs-lookup"><span data-stu-id="ac70f-137">The currency code for the unbilled line items.</span></span>                    |

### <a name="request-headers"></a><span data-ttu-id="ac70f-138">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ac70f-138">Request headers</span></span>

<span data-ttu-id="ac70f-139">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="ac70f-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ac70f-140">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="ac70f-140">Request body</span></span>

<span data-ttu-id="ac70f-141">Geen.</span><span class="sxs-lookup"><span data-stu-id="ac70f-141">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="ac70f-142">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ac70f-142">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/estimates/links?currencycode=usd HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="ac70f-143">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="ac70f-143">REST response</span></span>

<span data-ttu-id="ac70f-144">Als dit lukt, bevat het antwoord de koppelingen om niet-gefactureerde ramingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="ac70f-144">If successful, the response contains the links to retrieve unbilled estimates.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ac70f-145">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="ac70f-145">Response success and error codes</span></span>

<span data-ttu-id="ac70f-146">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="ac70f-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ac70f-147">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="ac70f-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ac70f-148">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="ac70f-148">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ac70f-149">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="ac70f-149">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: 80EAA055-B5D3-4D88-BFE8-924A3F706462
MS-RequestId: 1b18689e-3fe3-4fdb-d09e-39d13941390b
X-Locale: en-US
X-SourceFiles: =?UTF-8?B?RDpcU291cmNlc1xSUEUuUGFydG5lci5TZXJ2aWNlLkJpbGxpbmdTZXJ2aWNlXHYxLjFcV2ViQXBpc1xCaWxsaW5nU2VydmljZS5WMi5XZWJcdjFcaW52b2ljZXNcZXN0aW1hdGVzXGxpbmtz?=
X-Powered-By: ASP.NET
Date: Thu, 14 Mar 2019 18:15:06 GMT
Content-Length: 1857

{
  "totalCount": 4,
  "items": [
    {
      "type": "daily_rated_usage",
      "title": "Daily rated usage unbilled",
      "description": "This invoice line items includes unbilled consumption based data only.",
      "period": "Current",
      "link": {
        "uri": "/invoices/unbilled/lineitems?provider=Marketplace&invoicelineitemtype=UsageLineItems&currencycode=USD&period=current&size=2000",
        "method": "GET",
        "headers": []
      }
    },
    {
      "type": "daily_rated_usage",
      "title": "Daily rated usage unbilled",
      "description": "This invoice line items includes unbilled consumption based data only.",
      "period": "Previous",
      "link": {
        "uri": "/invoices/unbilled/lineitems?provider=Marketplace&invoicelineitemtype=UsageLineItems&currencycode=USD&period=previous&size=2000",
        "method": "GET",
        "headers": []
      }
    },
    {
      "type": "non_consumption",
      "title": "Unbilled reconciliation line items",
      "description": "This includes reconciliation line items for unbilled data only.",
      "period": "Current",
      "link": {
        "uri": "/invoices/unbilled/lineitems?provider=all&invoicelineitemtype=billinglineitems&currencycode=USD&period=current&size=2000",
        "method": "GET",
        "headers": []
      }
    },
    {
      "type": "non_consumption",
      "title": "Unbilled reconciliation line items",
      "description": "This includes reconciliation line items for unbilled data only.",
      "period": "Previous",
      "link": {
        "uri": "/invoices/unbilled/lineitems?provider=all&invoicelineitemtype=billinglineitems&currencycode=USD&period=previous&size=2000",
        "method": "GET",
        "headers": []
      }
    }
  ],
  "attributes": {
    "objectType": "Collection"
 }
}
```
