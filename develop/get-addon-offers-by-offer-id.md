---
title: Invoegtoepassingen voor een aanbiedings-id ophalen
description: De invoeg toepassingen voor een aanbiedings-ID ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 9ee22712b323c7439a192ed2e5af8d5e7eaf92a3
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767349"
---
# <a name="get-add-ons-for-an-offer-id"></a><span data-ttu-id="c739b-103">Invoegtoepassingen voor een aanbiedings-id ophalen</span><span class="sxs-lookup"><span data-stu-id="c739b-103">Get add-ons for an offer ID</span></span>

<span data-ttu-id="c739b-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="c739b-104">**Applies To**</span></span>

- <span data-ttu-id="c739b-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="c739b-105">Partner Center</span></span>
- <span data-ttu-id="c739b-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="c739b-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="c739b-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="c739b-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="c739b-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c739b-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c739b-109">De invoeg toepassingen voor een aanbiedings-ID ophalen.</span><span class="sxs-lookup"><span data-stu-id="c739b-109">How to get the add-ons for an offer ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c739b-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c739b-110">Prerequisites</span></span>

- <span data-ttu-id="c739b-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c739b-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c739b-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="c739b-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="c739b-113">Een aanbiedings-ID.</span><span class="sxs-lookup"><span data-stu-id="c739b-113">An offer ID.</span></span> <span data-ttu-id="c739b-114">Als u de aanbiedings-ID niet hebt, raadpleegt u [een lijst met aanbiedingen voor een markt ophalen](get-a-list-of-offers-for-a-market.md).</span><span class="sxs-lookup"><span data-stu-id="c739b-114">If you don't have the offer ID, see [Get a list of offers for a market](get-a-list-of-offers-for-a-market.md).</span></span>

## <a name="c"></a><span data-ttu-id="c739b-115">C\#</span><span class="sxs-lookup"><span data-stu-id="c739b-115">C\#</span></span>

<span data-ttu-id="c739b-116">Als u de invoeg toepassingen voor een aanbieding op ID wilt ophalen, moet u eerst de methode [**IAggregatePartner. offers. ByCountry**](/dotnet/api/microsoft.store.partnercenter.genericoperations.icountryselector-1.bycountry) met de land code aanroepen om een interface te krijgen voor het aanbieden van bewerkingen op basis van het opgegeven land.</span><span class="sxs-lookup"><span data-stu-id="c739b-116">To get the add-ons for an offer by ID, first call the [**IAggregatePartner.Offers.ByCountry**](/dotnet/api/microsoft.store.partnercenter.genericoperations.icountryselector-1.bycountry) method with the country code to get an interface to offer operations based on the given country.</span></span> <span data-ttu-id="c739b-117">Vervolgens roept u de [**ByID**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.byid) -methode aan met de aanbiedings-id om de aanbieding te identificeren waarvan u de invoeg toepassingen wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="c739b-117">Then call the [**ByID**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.byid) method with the offer ID to identify the offer whose add-ons you want to retrieve.</span></span> <span data-ttu-id="c739b-118">Gebruik vervolgens de eigenschap [**Addons**](/dotnet/api/microsoft.store.partnercenter.offers.ioffer.addons) om een interface te verkrijgen voor het toevoegen van bewerkingen voor de huidige aanbieding.</span><span class="sxs-lookup"><span data-stu-id="c739b-118">Next, use the [**AddOns**](/dotnet/api/microsoft.store.partnercenter.offers.ioffer.addons) property to get an interface to add-on operations for the current offer.</span></span> <span data-ttu-id="c739b-119">Roep ten slotte de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.offers.iofferaddons.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.offers.iofferaddons.getasync) aan om een verzameling van alle invoeg toepassingen voor de opgegeven aanbieding op te halen.</span><span class="sxs-lookup"><span data-stu-id="c739b-119">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.offers.iofferaddons.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.offers.iofferaddons.getasync) method to get a collection of all the add-ons for the specified offer.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string offerId;
// string countryCode;

var offerAddOns = partnerOperations.Offers.ByCountry(countryCode).ById(offerId).AddOns.Get();
```

<span data-ttu-id="c739b-120">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="c739b-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="c739b-121">**Project**: Partner Center SDK-voor beelden **klasse**: GetOffer.cs</span><span class="sxs-lookup"><span data-stu-id="c739b-121">**Project**: Partner Center SDK Samples **Class**: GetOffer.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="c739b-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c739b-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c739b-123">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c739b-123">Request syntax</span></span>

| <span data-ttu-id="c739b-124">Methode</span><span class="sxs-lookup"><span data-stu-id="c739b-124">Method</span></span>  | <span data-ttu-id="c739b-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c739b-125">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c739b-126">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="c739b-126">**GET**</span></span> | <span data-ttu-id="c739b-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers/{offer-id}/addons? land = {land nummer} http/1.1</span><span class="sxs-lookup"><span data-stu-id="c739b-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers/{offer-id}/addons?country={country-code} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="c739b-128">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="c739b-128">URI parameters</span></span>

<span data-ttu-id="c739b-129">Gebruik de volgende para meters om de aanbieding-ID en land code op te geven.</span><span class="sxs-lookup"><span data-stu-id="c739b-129">Use the following parameters to provide the offer ID and country code.</span></span>

| <span data-ttu-id="c739b-130">Naam</span><span class="sxs-lookup"><span data-stu-id="c739b-130">Name</span></span>         | <span data-ttu-id="c739b-131">Type</span><span class="sxs-lookup"><span data-stu-id="c739b-131">Type</span></span>       | <span data-ttu-id="c739b-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="c739b-132">Required</span></span> | <span data-ttu-id="c739b-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c739b-133">Description</span></span>                       |
|--------------|------------|----------|-----------------------------------|
| <span data-ttu-id="c739b-134">**aanbieding-ID**</span><span class="sxs-lookup"><span data-stu-id="c739b-134">**offer-id**</span></span> | <span data-ttu-id="c739b-135">**guid**</span><span class="sxs-lookup"><span data-stu-id="c739b-135">**guid**</span></span>   | <span data-ttu-id="c739b-136">J</span><span class="sxs-lookup"><span data-stu-id="c739b-136">Y</span></span>        | <span data-ttu-id="c739b-137">Een GUID die de aanbieding aanduidt.</span><span class="sxs-lookup"><span data-stu-id="c739b-137">A GUID that identifies the offer.</span></span> |
| <span data-ttu-id="c739b-138">**regio**</span><span class="sxs-lookup"><span data-stu-id="c739b-138">**country**</span></span>  | <span data-ttu-id="c739b-139">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="c739b-139">**string**</span></span> | <span data-ttu-id="c739b-140">J</span><span class="sxs-lookup"><span data-stu-id="c739b-140">Y</span></span>        | <span data-ttu-id="c739b-141">De land code (bijvoorbeeld `US` ).</span><span class="sxs-lookup"><span data-stu-id="c739b-141">The country code (for example `US`).</span></span>       |

### <a name="request-headers"></a><span data-ttu-id="c739b-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c739b-142">Request headers</span></span>

<span data-ttu-id="c739b-143">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c739b-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c739b-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c739b-144">Request body</span></span>

<span data-ttu-id="c739b-145">Geen.</span><span class="sxs-lookup"><span data-stu-id="c739b-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c739b-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c739b-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/offers/195416C1-3447-423A-B37B-EE59A99A19C4/addons?country=us HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c15e829e-ecc7-42c2-8a4b-5e6961f4e3f8
MS-CorrelationId: 26d2b3b1-c76a-4aeb-8298-1654c91d9eb8
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="c739b-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c739b-147">REST response</span></span>

<span data-ttu-id="c739b-148">Als dit lukt, retourneert deze methode een verzameling [aanbiedings](offer-resources.md) objecten in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="c739b-148">If successful, this method returns a collection of [Offer](offer-resources.md) objects in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c739b-149">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="c739b-149">Response success and error codes</span></span>

<span data-ttu-id="c739b-150">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="c739b-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c739b-151">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c739b-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c739b-152">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="c739b-152">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c739b-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="c739b-153">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 3137
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 26d2b3b1-c76a-4aeb-8298-1654c91d9eb8
MS-RequestId: c15e829e-ecc7-42c2-8a4b-5e6961f4e3f8
MS-CV: P8xjUcSeY0ithZ9S.0
MS-ServerId: 202010406
Date: Wed, 01 Feb 2017 22:37:58 GMT

{
    "totalCount": 2,
    "items": [{
            "id": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "name": "Exchange Online Archiving for Exchange Online",
            "description": "A personal e-mail archive for users who have mailboxes on Exchange Server 2010 or later.",
            "minimumQuantity": 1,
            "maximumQuantity": 10000000,
            "rank": 200,
            "uri": "/3c95518e-8c37-41e3-9627-0ca339200f53/Offers/2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "locale": "en-US",
            "country": "US",
            "category": {
                "id": "",
                "name": "",
                "rank": 0,
                "locale": "en-us",
                "country": "US",
                "attributes": {
                    "objectType": "OfferCategory"
                }
            },
            "prerequisiteOffers": ["35A36B80-270A-44BF-9290-00545D350866", "6FBAD345-B7DE-42A6-B6AB-79B363D0B371", "91FD106F-4B2C-4938-95AC-F54F74E9A239", "195416C1-3447-423A-B37B-EE59A99A19C4", "22A70120-4078-4926-9592-39ED91CB9C01", "2A727AE4-F201-497D-A9D6-C6A892DF4A87", "BD938F12-058F-4927-BBA3-AE36B1D2501C", "031C9E47-4802-4248-838E-778FB1D2CC05", "B2016E73-D9AD-4758-B8B8-D5C001BDF411", "AA98032C-5403-472F-B24F-F6654846B15D"],
            "isAddOn": true,
            "isAvailableForPurchase": true,
            "billing": "license",
            "isAutoRenewable": true,
            "salesGroupId": "1",
            "product": {
                "id": "EE02FD1B-340E-4A4B-B355-4A514E4C8943",
                "name": "Exchange Online Archiving for Exchange Online",
                "unit": "Licenses"
            },
            "unitType": "Licenses",
            "links": {
                "learnMore": {
                    "uri": "http://g.microsoftonline.com/0BXPS00en-us/1302",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/offers/2828BE95-46BA-4F91-B2FD-0BEF192ECF60?country=US",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Offer"
            }
        }, {
            "id": "45320EC9-9B8E-49D0-B900-F14141A0ABD1",
            "name": "Microsoft MyAnalytics",
            "description": "Microsoft MyAnalytics provides insights about time and relationships to help individuals and teams achieve more at work.",
            "minimumQuantity": 1,
            "maximumQuantity": 10000000,
            "rank": 232,
            "uri": "/3c95518e-8c37-41e3-9627-0ca339200f53/Offers/45320EC9-9B8E-49D0-B900-F14141A0ABD1",
            "locale": "en-US",
            "country": "US",
            "category": {
                "id": "",
                "name": "",
                "rank": 0,
                "locale": "en-us",
                "country": "US",
                "attributes": {
                    "objectType": "OfferCategory"
                }
            },
            "prerequisiteOffers": ["195416C1-3447-423A-B37B-EE59A99A19C4", "2F707C7C-2433-49A5-A437-9CA7CF40D3EB", "91FD106F-4B2C-4938-95AC-F54F74E9A239", "796B6B5F-613C-4E24-A17C-EBA730D49C02", "8909E28E-5832-42F4-9886-B0A5545F3645", "2B3B8D2D-10AA-4BE4-B5FD-7F2FEB0C3091"],
            "isAddOn": true,
            "isAvailableForPurchase": true,
            "billing": "license",
            "isAutoRenewable": true,
            "salesGroupId": "1",
            "product": {
                "id": "90A8F363-DA30-4ECD-90A7-D3A6B203486D",
                "name": "Microsoft MyAnalytics",
                "unit": "Licenses"
            },
            "unitType": "Licenses",
            "links": {
                "learnMore": {
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/offers/45320EC9-9B8E-49D0-B900-F14141A0ABD1?country=US",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Offer"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
