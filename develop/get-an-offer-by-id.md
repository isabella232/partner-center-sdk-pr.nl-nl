---
title: Een aanbieding ophalen op basis van id
description: Haalt een aanbiedingsresource op die overeenkomt met de aanbiedings-id.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: brentserbus
ms.author: brserbus
ms.openlocfilehash: f759cbdeefb4f550c41b41de40e9979e72e4ddeb
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760637"
---
# <a name="get-an-offer-by-id"></a><span data-ttu-id="cb47c-103">Een aanbieding ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="cb47c-103">Get an offer by ID</span></span>

<span data-ttu-id="cb47c-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="cb47c-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="cb47c-105">Haalt een **aanbiedingsresource** op die overeenkomt met de aanbiedings-id.</span><span class="sxs-lookup"><span data-stu-id="cb47c-105">Gets an **Offer** resource that matches the offer ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cb47c-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cb47c-106">Prerequisites</span></span>

- <span data-ttu-id="cb47c-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cb47c-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cb47c-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="cb47c-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="cb47c-109">Een aanbiedings-id.</span><span class="sxs-lookup"><span data-stu-id="cb47c-109">An offer ID.</span></span>

## <a name="c"></a><span data-ttu-id="cb47c-110">C\#</span><span class="sxs-lookup"><span data-stu-id="cb47c-110">C\#</span></span>

<span data-ttu-id="cb47c-111">Als u een specifieke aanbieding wilt zoeken op id, gebruikt u de verzameling **IAggregatePartner.Offers,** brengt u het land tot stand met een aanroep naar **ByCountry()** en roept u vervolgens de [**methode ByID()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="cb47c-111">To find a specific offer by ID, use your **IAggregatePartner.Offers** collection, establish the country with a call to **ByCountry()**, and then call the [**ByID()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.byid) method.</span></span> <span data-ttu-id="cb47c-112">Roep vervolgens de [**methode Get()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.get) of [**Get Async()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="cb47c-112">Then, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.get) or [**Get Async()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.getasync) method.</span></span>

```csharp
// IAggretagePartner partnerOperations;
// string countryCode;
// string offerId;

// retrieve the offer
var offer = partnerOperations.Offers.ByCountry(countryCode).ById(offerId).Get();
```

<span data-ttu-id="cb47c-113">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="cb47c-113">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="cb47c-114">**Project:** PartnerSDK.FeatureSample-klasse: GetOffer.cs </span><span class="sxs-lookup"><span data-stu-id="cb47c-114">**Project**: PartnerSDK.FeatureSample **Class**: GetOffer.cs</span></span>

## <a name="java"></a><span data-ttu-id="cb47c-115">Java</span><span class="sxs-lookup"><span data-stu-id="cb47c-115">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="cb47c-116">Als u een specifieke aanbieding wilt zoeken op id, gebruikt u de functie **IAggregatePartner.getOffers,** stelt u het land in met een aanroep naar de functie **byCountry()** en roept u vervolgens de **functie byID()** aan.</span><span class="sxs-lookup"><span data-stu-id="cb47c-116">To find a specific offer by ID, use your **IAggregatePartner.getOffers** function, establish the country with a call to the **byCountry()** function, and then call the **byID()** function.</span></span> <span data-ttu-id="cb47c-117">Roep vervolgens de **functie get()** aan.</span><span class="sxs-lookup"><span data-stu-id="cb47c-117">Then call the **get()** function.</span></span>

```java
// IAggretagePartner partnerOperations;
// String countryCode;
// String offerId;

// Retrieve the offer
Offer offer = partnerOperations.getOffers().byCountry(countryCode).byId(offerId).get();
```

## <a name="powershell"></a><span data-ttu-id="cb47c-118">PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb47c-118">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="cb47c-119">Als u een specifieke aanbieding op id wilt vinden, voert u [**de opdracht Get-PartnerOffer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOffer.md) uit en geeft u de parameters **CountryCode** **en OfferId** op.</span><span class="sxs-lookup"><span data-stu-id="cb47c-119">To find a specific offer by ID, execute the [**Get-PartnerOffer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOffer.md) command, and specify the **CountryCode** and **OfferId** parameters.</span></span>

```powershell
# $countryCode
# $offerId

Get-PartnerOffer -Country $countryCode -OfferId $offerId
```

## <a name="rest-request"></a><span data-ttu-id="cb47c-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="cb47c-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cb47c-121">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="cb47c-121">Request syntax</span></span>

| <span data-ttu-id="cb47c-122">Methode</span><span class="sxs-lookup"><span data-stu-id="cb47c-122">Method</span></span>  | <span data-ttu-id="cb47c-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="cb47c-123">Request URI</span></span>                                                                                    |
|---------|------------------------------------------------------------------------------------------------|
| <span data-ttu-id="cb47c-124">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="cb47c-124">**GET**</span></span> | <span data-ttu-id="cb47c-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers/{offer-id}?country={country-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="cb47c-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers/{offer-id}?country={country-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="cb47c-126">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="cb47c-126">URI parameter</span></span>

| <span data-ttu-id="cb47c-127">Naam</span><span class="sxs-lookup"><span data-stu-id="cb47c-127">Name</span></span>           | <span data-ttu-id="cb47c-128">Type</span><span class="sxs-lookup"><span data-stu-id="cb47c-128">Type</span></span>       | <span data-ttu-id="cb47c-129">Vereist</span><span class="sxs-lookup"><span data-stu-id="cb47c-129">Required</span></span> | <span data-ttu-id="cb47c-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cb47c-130">Description</span></span>                           |
|----------------|------------|----------|---------------------------------------|
| <span data-ttu-id="cb47c-131">**offer-id**</span><span class="sxs-lookup"><span data-stu-id="cb47c-131">**offer-id**</span></span>   | <span data-ttu-id="cb47c-132">**guid**</span><span class="sxs-lookup"><span data-stu-id="cb47c-132">**guid**</span></span>   | <span data-ttu-id="cb47c-133">J</span><span class="sxs-lookup"><span data-stu-id="cb47c-133">Y</span></span>        | <span data-ttu-id="cb47c-134">Een GUID die overeenkomt met de aanbieding.</span><span class="sxs-lookup"><span data-stu-id="cb47c-134">A GUID that corresponds to the offer.</span></span> |
| <span data-ttu-id="cb47c-135">**country-id**</span><span class="sxs-lookup"><span data-stu-id="cb47c-135">**country-id**</span></span> | <span data-ttu-id="cb47c-136">**tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="cb47c-136">**string**</span></span> | <span data-ttu-id="cb47c-137">J</span><span class="sxs-lookup"><span data-stu-id="cb47c-137">Y</span></span>        | <span data-ttu-id="cb47c-138">De land-/regio-id.</span><span class="sxs-lookup"><span data-stu-id="cb47c-138">The country/region ID.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="cb47c-139">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="cb47c-139">Request headers</span></span>

- <span data-ttu-id="cb47c-140">Er **is een locale-id** vereist die is opgemaakt als een tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="cb47c-140">A **locale-id** formatted as a string is required.</span></span>
<span data-ttu-id="cb47c-141">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="cb47c-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cb47c-142">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="cb47c-142">Request body</span></span>

<span data-ttu-id="cb47c-143">Geen.</span><span class="sxs-lookup"><span data-stu-id="cb47c-143">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="cb47c-144">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cb47c-144">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/offers/<offer-id>?country=<country-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
X-Locale: <locale-id>
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="cb47c-145">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="cb47c-145">REST response</span></span>

<span data-ttu-id="cb47c-146">Als dit lukt, retourneert deze methode een **aanbiedingsresource** in de antwoordbody.</span><span class="sxs-lookup"><span data-stu-id="cb47c-146">If successful, this method returns an **Offer** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cb47c-147">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="cb47c-147">Response success and error codes</span></span>

<span data-ttu-id="cb47c-148">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="cb47c-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cb47c-149">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="cb47c-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="cb47c-150">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="cb47c-150">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="cb47c-151">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="cb47c-151">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1918
Content-Type: application/json
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
Date: Mon, 23 Nov 2015 23:13:01 GMT

{
    "id": "031C9E47-4802-4248-838E-778FB1D2CC05",
    "name": "Office 365 Business Premium",
    "description": "For businesses with 1 to 300 users that need the latest desktop version of Office,
                    plus anywhere access to email, filesharing, and online conferencing.",
    "minimumQuantity": 1,
    "maximumQuantity": 300,
    "rank": 56,
    "uri": "/3c95518e-8c37-41e3-9627-0ca339200f53/Offers/031C9E47-4802-4248-838E-778FB1D2CC05",
    "locale": "en-us",
    "country": "US",
    "category": {
        "id": "SmallBusiness_Key",
        "name": "Small Business",
        "rank": 30,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    },
    "prerequisiteOffers": [],
    "isAddOn": false,
    "isAvailableForPurchase": true,
    "billing": "license",
    "isAutoRenewable": true,
    "product": {
        "id": "f245ecc8-75af-4f8e-b61f-27d8114de5f3",
        "name": "Office 365 Business Premium",
        "unit": "Licenses"
    },
    "unitType": "Licenses",
    "links": {
        "learnMore": {
            "uri": "http: //g.microsoftonline.com/0BXPS00en/909",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Offer"
    }
}
```
