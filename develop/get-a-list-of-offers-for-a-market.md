---
title: Een lijst met aanbiedingen voor een markt ophalen
description: Hiermee wordt een verzameling opgehaald die alle aanbiedingen voor een specifieke markt bevat.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 3a004f6f8f8de8cd398d82c300793e4f196efaaa
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767297"
---
# <a name="get-a-list-of-offers-for-a-market"></a><span data-ttu-id="5486c-103">Een lijst met aanbiedingen voor een markt ophalen</span><span class="sxs-lookup"><span data-stu-id="5486c-103">Get a list of offers for a market</span></span>

<span data-ttu-id="5486c-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="5486c-104">**Applies To**</span></span>

- <span data-ttu-id="5486c-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="5486c-105">Partner Center</span></span>
- <span data-ttu-id="5486c-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="5486c-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="5486c-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="5486c-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="5486c-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="5486c-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="5486c-109">Hiermee wordt een verzameling opgehaald die alle aanbiedingen voor een specifieke markt bevat.</span><span class="sxs-lookup"><span data-stu-id="5486c-109">Gets a collection that contains all the offers for a specific market.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5486c-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="5486c-110">Prerequisites</span></span>

- <span data-ttu-id="5486c-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5486c-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5486c-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="5486c-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="5486c-113">C\#</span><span class="sxs-lookup"><span data-stu-id="5486c-113">C\#</span></span>

<span data-ttu-id="5486c-114">Als u een lijst met aanbiedingen op een bepaalde markt wilt ontvangen, gebruikt u uw **IAggregatePartner. offers** -verzameling, selecteert u de markt per land en roept u de methode **Get ()** of **Get async ()** aan.</span><span class="sxs-lookup"><span data-stu-id="5486c-114">To get a list of offers in a given market, use your **IAggregatePartner.Offers** collection, select the market by country, and call the **Get()** or **Get Async()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

ResourceCollection<Offer> offers = partnerOperations.Offers.ByCountry("US").Get();
```

<span data-ttu-id="5486c-115">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="5486c-115">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="5486c-116">**Project**: PartnerSDK. FeatureSample- **klasse**: offers.cs</span><span class="sxs-lookup"><span data-stu-id="5486c-116">**Project**: PartnerSDK.FeatureSample **Class**: Offers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="5486c-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="5486c-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5486c-118">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="5486c-118">Request syntax</span></span>

| <span data-ttu-id="5486c-119">Methode</span><span class="sxs-lookup"><span data-stu-id="5486c-119">Method</span></span>  | <span data-ttu-id="5486c-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="5486c-120">Request URI</span></span>                                                                          |
|---------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="5486c-121">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="5486c-121">**GET**</span></span> | <span data-ttu-id="5486c-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers? land = {land-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="5486c-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers?country={country-id} HTTP/1.1</span></span>   |

### <a name="uri-parameter"></a><span data-ttu-id="5486c-123">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="5486c-123">URI parameter</span></span>

<span data-ttu-id="5486c-124">Deze tabel bevat de vereiste query parameters voor het ophalen van de aanbiedingen.</span><span class="sxs-lookup"><span data-stu-id="5486c-124">This table lists the required query parameters to get the offers.</span></span>

| <span data-ttu-id="5486c-125">Naam</span><span class="sxs-lookup"><span data-stu-id="5486c-125">Name</span></span>           | <span data-ttu-id="5486c-126">Type</span><span class="sxs-lookup"><span data-stu-id="5486c-126">Type</span></span>       | <span data-ttu-id="5486c-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="5486c-127">Required</span></span> | <span data-ttu-id="5486c-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5486c-128">Description</span></span>            |
|----------------|------------|----------|------------------------|
| <span data-ttu-id="5486c-129">**land-id**</span><span class="sxs-lookup"><span data-stu-id="5486c-129">**country-id**</span></span> | <span data-ttu-id="5486c-130">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="5486c-130">**string**</span></span> | <span data-ttu-id="5486c-131">J</span><span class="sxs-lookup"><span data-stu-id="5486c-131">Y</span></span>        | <span data-ttu-id="5486c-132">De ID van het land/de regio.</span><span class="sxs-lookup"><span data-stu-id="5486c-132">The country/region ID.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="5486c-133">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="5486c-133">Request headers</span></span>

- <span data-ttu-id="5486c-134">Een **land instellingen-id** die is opgemaakt als een teken reeks is vereist.</span><span class="sxs-lookup"><span data-stu-id="5486c-134">A **locale-id** formatted as a string is required.</span></span>
<span data-ttu-id="5486c-135">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5486c-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5486c-136">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="5486c-136">Request body</span></span>

<span data-ttu-id="5486c-137">Geen.</span><span class="sxs-lookup"><span data-stu-id="5486c-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="5486c-138">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="5486c-138">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/offers?country=<country-id> HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
X-Locale: <locale-id>
```

## <a name="rest-response"></a><span data-ttu-id="5486c-139">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="5486c-139">REST response</span></span>

<span data-ttu-id="5486c-140">Als dit lukt, retourneert deze methode een verzameling van **aanbod** resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="5486c-140">If successful, this method returns a collection of **Offer** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5486c-141">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="5486c-141">Response success and error codes</span></span>

<span data-ttu-id="5486c-142">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="5486c-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5486c-143">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="5486c-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5486c-144">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="5486c-144">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="5486c-145">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="5486c-145">Response example</span></span>

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
