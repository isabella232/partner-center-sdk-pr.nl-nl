---
title: Een lijst met aanbiedingen voor een markt ophalen
description: Haalt een verzameling op die alle aanbiedingen voor een specifieke markt bevat.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 6f4fd821879545db4e781fe3202c8ee11f167615
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874241"
---
# <a name="get-a-list-of-offers-for-a-market"></a><span data-ttu-id="6f6c7-103">Een lijst met aanbiedingen voor een markt ophalen</span><span class="sxs-lookup"><span data-stu-id="6f6c7-103">Get a list of offers for a market</span></span>

<span data-ttu-id="6f6c7-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6f6c7-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6f6c7-105">Haalt een verzameling op die alle aanbiedingen voor een specifieke markt bevat.</span><span class="sxs-lookup"><span data-stu-id="6f6c7-105">Gets a collection that contains all the offers for a specific market.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6f6c7-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6f6c7-106">Prerequisites</span></span>

- <span data-ttu-id="6f6c7-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6f6c7-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6f6c7-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="6f6c7-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="6f6c7-109">C\#</span><span class="sxs-lookup"><span data-stu-id="6f6c7-109">C\#</span></span>

<span data-ttu-id="6f6c7-110">Als u een lijst met aanbiedingen op een bepaalde markt wilt ophalen, gebruikt u de verzameling **IAggregatePartner.Offers,** selecteert u de markt per land en roept u de methode **Get()** of **Get Async()** aan.</span><span class="sxs-lookup"><span data-stu-id="6f6c7-110">To get a list of offers in a given market, use your **IAggregatePartner.Offers** collection, select the market by country, and call the **Get()** or **Get Async()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

ResourceCollection<Offer> offers = partnerOperations.Offers.ByCountry("US").Get();
```

<span data-ttu-id="6f6c7-111">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="6f6c7-111">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="6f6c7-112">**Project:** PartnerSDK.FeatureSample-klasse: Offers.cs </span><span class="sxs-lookup"><span data-stu-id="6f6c7-112">**Project**: PartnerSDK.FeatureSample **Class**: Offers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="6f6c7-113">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="6f6c7-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6f6c7-114">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="6f6c7-114">Request syntax</span></span>

| <span data-ttu-id="6f6c7-115">Methode</span><span class="sxs-lookup"><span data-stu-id="6f6c7-115">Method</span></span>  | <span data-ttu-id="6f6c7-116">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="6f6c7-116">Request URI</span></span>                                                                          |
|---------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="6f6c7-117">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="6f6c7-117">**GET**</span></span> | <span data-ttu-id="6f6c7-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers?country={country-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6f6c7-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers?country={country-id} HTTP/1.1</span></span>   |

### <a name="uri-parameter"></a><span data-ttu-id="6f6c7-119">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="6f6c7-119">URI parameter</span></span>

<span data-ttu-id="6f6c7-120">Deze tabel bevat de vereiste queryparameters om de aanbiedingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="6f6c7-120">This table lists the required query parameters to get the offers.</span></span>

| <span data-ttu-id="6f6c7-121">Naam</span><span class="sxs-lookup"><span data-stu-id="6f6c7-121">Name</span></span>           | <span data-ttu-id="6f6c7-122">Type</span><span class="sxs-lookup"><span data-stu-id="6f6c7-122">Type</span></span>       | <span data-ttu-id="6f6c7-123">Vereist</span><span class="sxs-lookup"><span data-stu-id="6f6c7-123">Required</span></span> | <span data-ttu-id="6f6c7-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6f6c7-124">Description</span></span>            |
|----------------|------------|----------|------------------------|
| <span data-ttu-id="6f6c7-125">**country-id**</span><span class="sxs-lookup"><span data-stu-id="6f6c7-125">**country-id**</span></span> | <span data-ttu-id="6f6c7-126">**tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="6f6c7-126">**string**</span></span> | <span data-ttu-id="6f6c7-127">J</span><span class="sxs-lookup"><span data-stu-id="6f6c7-127">Y</span></span>        | <span data-ttu-id="6f6c7-128">De land-/regio-id.</span><span class="sxs-lookup"><span data-stu-id="6f6c7-128">The country/region ID.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="6f6c7-129">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="6f6c7-129">Request headers</span></span>

- <span data-ttu-id="6f6c7-130">Er **is een locale-id** vereist die is opgemaakt als een tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="6f6c7-130">A **locale-id** formatted as a string is required.</span></span>
<span data-ttu-id="6f6c7-131">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="6f6c7-131">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6f6c7-132">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="6f6c7-132">Request body</span></span>

<span data-ttu-id="6f6c7-133">Geen.</span><span class="sxs-lookup"><span data-stu-id="6f6c7-133">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6f6c7-134">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6f6c7-134">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/offers?country=<country-id> HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
X-Locale: <locale-id>
```

## <a name="rest-response"></a><span data-ttu-id="6f6c7-135">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="6f6c7-135">REST response</span></span>

<span data-ttu-id="6f6c7-136">Als dit lukt, retourneert deze methode een verzameling **aanbiedingsresources** in de antwoordbody.</span><span class="sxs-lookup"><span data-stu-id="6f6c7-136">If successful, this method returns a collection of **Offer** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6f6c7-137">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="6f6c7-137">Response success and error codes</span></span>

<span data-ttu-id="6f6c7-138">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="6f6c7-138">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6f6c7-139">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="6f6c7-139">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6f6c7-140">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="6f6c7-140">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6f6c7-141">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="6f6c7-141">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 26584
Content-Type: application/json
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
Date: Mon, 23 Nov 2015 23:20:44 GMT

{
    "totalCount":12,"items":[{
        "id":"E60E0348-1710-484B-992A-32B294D4CDE1",
        "name":"Azure Rights Management Premium (Government Pricing)",
        "description":"Microsoft Azure Rights Management Premium helps you protect confidential documents and email with strong encryption.
                       Control the use of your information by specifying who can view, edit, print, save and share your data.
                       Simple to use and integrated with Microsoft Office, SharePoint and Exchange.",
        "minimumQuantity":1,
        "maximumQuantity":10000000,
        "rank":5,
        "uri":"/3c95518e-8c37-41e3-9627-0ca339200f53/Offers/E60E0348-1710-484B-992A-32B294D4CDE1",
        "locale":"EN-US",
        "country":"US",
        "category":{
            "id":"Government_Key",
            "name":"Government",
            "rank":40,
            "locale":"en-us",
            "country":"US",
            "attributes":{
                "objectType":"OfferCategory"
            }
        },
        "prerequisiteOffers":[],
        "isAddOn":false,
        "isAvailableForPurchase":true,
        "billing":"license",
        "isAutoRenewable":true,
        "product":{
            "id":"c52ea49f-fe5d-4e95-93ba-1de91d380f89",
            "name":"Azure Rights Management Premium",
            "unit":"Licenses"
        },
        "unitType":"Licenses",
        "links":{
            "learnMore":{
                "uri":"http://g.microsoftonline.com/0BXPS00en/0000",
                "method":"GET",
                "headers":[]
            },
            "self":{
                "uri":"/offers/E60E0348-1710-484B-992A-32B294D4CDE1",
                "method":"GET",
                "headers":[]
            }
        },
        "attributes":{
            "objectType":"Offer"
        }
    },
    "links":{
        "self":{
            "uri":"/v1/offers?country={country-id}",
            "method":"GET",
            "headers":[]
        },
        "previous":{
            "uri":"/v1/offers?country={country-id}",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "objectType":"Collection"
    }
}
```
