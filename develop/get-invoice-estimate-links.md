---
title: Koppelingen voor factuurramingen ophalen
description: U kunt een verzameling van schattingskoppelingen ophalen om de details van het query-afstemmingsregelitem op te vragen.
ms.date: 09/24/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.assetid: ''
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 719becd3fac5605c4ad48ab86d483ba7903d65d8
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549141"
---
# <a name="get-invoice-estimate-links"></a><span data-ttu-id="94623-103">Koppelingen voor factuurramingen ophalen</span><span class="sxs-lookup"><span data-stu-id="94623-103">Get invoice estimate links</span></span>

<span data-ttu-id="94623-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="94623-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="94623-105">U kunt schattingskoppelingen krijgen om gegevens op te vragen voor niet-gebilbileerde afstemmingslijnitems.</span><span class="sxs-lookup"><span data-stu-id="94623-105">You can get estimate links to help query details for unbilled reconciliation line items.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="94623-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="94623-106">Prerequisites</span></span>

- <span data-ttu-id="94623-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="94623-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="94623-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="94623-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="94623-109">Een factuur-id.</span><span class="sxs-lookup"><span data-stu-id="94623-109">An invoice identifier.</span></span> <span data-ttu-id="94623-110">Hiermee wordt de factuur geïdentificeerd waarvoor de regelitems moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="94623-110">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="94623-111">C\#</span><span class="sxs-lookup"><span data-stu-id="94623-111">C\#</span></span>

<span data-ttu-id="94623-112">De volgende voorbeeldcode laat zien hoe u de schattingskoppelingen kunt krijgen om niet-gebileerde regelitems voor een bepaalde valuta op te vragen.</span><span class="sxs-lookup"><span data-stu-id="94623-112">The following example code shows how you can get the estimate links to query unbilled line items for a given currency.</span></span> <span data-ttu-id="94623-113">Het antwoord bevat de schattingskoppelingen voor elke periode (bijvoorbeeld de huidige en vorige maand).</span><span class="sxs-lookup"><span data-stu-id="94623-113">The response contains the estimate links for each period (for example, the current and previous month).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string curencyCode;

 // all the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
 IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// read estimate links for currencycode
var estimateLinks = scopedPartnerOperations.Invoices.Estimates.Links.ByCurrency(curencyCode).Get();
```

<span data-ttu-id="94623-114">Zie het volgende voor een vergelijkbaar voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="94623-114">For a similar example, see the following:</span></span>

- <span data-ttu-id="94623-115">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="94623-115">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="94623-116">Project: **Partnercentrum-SDK Voorbeelden**</span><span class="sxs-lookup"><span data-stu-id="94623-116">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="94623-117">Klasse: **GetEstimatesLinks.cs**</span><span class="sxs-lookup"><span data-stu-id="94623-117">Class: **GetEstimatesLinks.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="94623-118">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="94623-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="94623-119">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="94623-119">Request syntax</span></span>

| <span data-ttu-id="94623-120">Methode</span><span class="sxs-lookup"><span data-stu-id="94623-120">Method</span></span>  | <span data-ttu-id="94623-121">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="94623-121">Request URI</span></span>                                                                                                 |
|---------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="94623-122">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="94623-122">**GET**</span></span> | <span data-ttu-id="94623-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/estimates/links?currencycode={currencycode} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="94623-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/estimates/links?currencycode={currencycode} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="94623-124">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="94623-124">URI parameters</span></span>

<span data-ttu-id="94623-125">Gebruik de volgende URI en queryparameter bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="94623-125">Use the following URI and query parameter when creating the request.</span></span>

| <span data-ttu-id="94623-126">Naam</span><span class="sxs-lookup"><span data-stu-id="94623-126">Name</span></span>                   | <span data-ttu-id="94623-127">Type</span><span class="sxs-lookup"><span data-stu-id="94623-127">Type</span></span>   | <span data-ttu-id="94623-128">Vereist</span><span class="sxs-lookup"><span data-stu-id="94623-128">Required</span></span> | <span data-ttu-id="94623-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="94623-129">Description</span></span>                                                       |
|------------------------|--------|----------|-------------------------------------------------------------------|
| <span data-ttu-id="94623-130">currencyCode</span><span class="sxs-lookup"><span data-stu-id="94623-130">currencyCode</span></span>           | <span data-ttu-id="94623-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="94623-131">string</span></span> | <span data-ttu-id="94623-132">Ja</span><span class="sxs-lookup"><span data-stu-id="94623-132">Yes</span></span>      | <span data-ttu-id="94623-133">De valutacode voor de niet-gebillede regelitems.</span><span class="sxs-lookup"><span data-stu-id="94623-133">The currency code for the unbilled line items.</span></span>                    |

### <a name="request-headers"></a><span data-ttu-id="94623-134">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="94623-134">Request headers</span></span>

<span data-ttu-id="94623-135">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="94623-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="94623-136">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="94623-136">Request body</span></span>

<span data-ttu-id="94623-137">Geen.</span><span class="sxs-lookup"><span data-stu-id="94623-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="94623-138">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="94623-138">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/estimates/links?currencycode=usd HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="94623-139">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="94623-139">REST response</span></span>

<span data-ttu-id="94623-140">Als dit lukt, bevat het antwoord de koppelingen voor het ophalen van niet-gebileerde schattingen.</span><span class="sxs-lookup"><span data-stu-id="94623-140">If successful, the response contains the links to retrieve unbilled estimates.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="94623-141">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="94623-141">Response success and error codes</span></span>

<span data-ttu-id="94623-142">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="94623-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="94623-143">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="94623-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="94623-144">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="94623-144">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="94623-145">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="94623-145">Response example</span></span>

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
