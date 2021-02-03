---
title: Een aanbieding ophalen op basis van id
description: Hiermee wordt een aanbiedings bron opgehaald die overeenkomt met de ID van de aanbieding.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: brentserbus
ms.author: brserbus
ms.openlocfilehash: 9448276e817affb823eddabbcab8757c79615fbd
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767564"
---
# <a name="get-an-offer-by-id"></a><span data-ttu-id="78d48-103">Een aanbieding ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="78d48-103">Get an offer by ID</span></span>

<span data-ttu-id="78d48-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="78d48-104">**Applies To**</span></span>

- <span data-ttu-id="78d48-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="78d48-105">Partner Center</span></span>
- <span data-ttu-id="78d48-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="78d48-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="78d48-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="78d48-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="78d48-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="78d48-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="78d48-109">Hiermee wordt een **aanbiedings** bron opgehaald die overeenkomt met de id van de aanbieding.</span><span class="sxs-lookup"><span data-stu-id="78d48-109">Gets an **Offer** resource that matches the offer ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="78d48-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="78d48-110">Prerequisites</span></span>

- <span data-ttu-id="78d48-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="78d48-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="78d48-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="78d48-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="78d48-113">Een aanbiedings-ID.</span><span class="sxs-lookup"><span data-stu-id="78d48-113">An offer ID.</span></span>

## <a name="c"></a><span data-ttu-id="78d48-114">C\#</span><span class="sxs-lookup"><span data-stu-id="78d48-114">C\#</span></span>

<span data-ttu-id="78d48-115">Als u een specifieke aanbieding op ID wilt zoeken, gebruikt u uw **IAggregatePartner. offers** -verzameling, stelt u het land in met een aanroep van **ByCountry ()** en roept u vervolgens de methode [**ByID ()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="78d48-115">To find a specific offer by ID, use your **IAggregatePartner.Offers** collection, establish the country with a call to **ByCountry()**, and then call the [**ByID()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.byid) method.</span></span> <span data-ttu-id="78d48-116">Roep vervolgens de methode [**Get ()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.get) of [**Get async () aan**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.getasync) .</span><span class="sxs-lookup"><span data-stu-id="78d48-116">Then, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.get) or [**Get Async()**](/dotnet/api/microsoft.store.partnercenter.offers.ioffercollection.getasync) method.</span></span>

```csharp
// IAggretagePartner partnerOperations;
// string countryCode;
// string offerId;

// retrieve the offer
var offer = partnerOperations.Offers.ByCountry(countryCode).ById(offerId).Get();
```

<span data-ttu-id="78d48-117">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="78d48-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="78d48-118">**Project**: PartnerSDK. FeatureSample- **klasse**: GetOffer.cs</span><span class="sxs-lookup"><span data-stu-id="78d48-118">**Project**: PartnerSDK.FeatureSample **Class**: GetOffer.cs</span></span>

## <a name="java"></a><span data-ttu-id="78d48-119">Java</span><span class="sxs-lookup"><span data-stu-id="78d48-119">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="78d48-120">Als u een specifieke aanbieding op ID wilt zoeken, gebruikt u de functie **IAggregatePartner. getOffers** , stelt u het land in met een aanroep van de functie **byCountry ()** en roept u vervolgens de functie **byID ()** aan.</span><span class="sxs-lookup"><span data-stu-id="78d48-120">To find a specific offer by ID, use your **IAggregatePartner.getOffers** function, establish the country with a call to the **byCountry()** function, and then call the **byID()** function.</span></span> <span data-ttu-id="78d48-121">Roep vervolgens de functie **Get () aan** .</span><span class="sxs-lookup"><span data-stu-id="78d48-121">Then call the **get()** function.</span></span>

```java
// IAggretagePartner partnerOperations;
// String countryCode;
// String offerId;

// Retrieve the offer
Offer offer = partnerOperations.getOffers().byCountry(countryCode).byId(offerId).get();
```

## <a name="powershell"></a><span data-ttu-id="78d48-122">PowerShell</span><span class="sxs-lookup"><span data-stu-id="78d48-122">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="78d48-123">Als u een specifieke aanbieding op ID wilt zoeken, voert u de opdracht [**Get-PartnerOffer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOffer.md) uit en geeft u de para meters **CountryCode** en **OfferId** op.</span><span class="sxs-lookup"><span data-stu-id="78d48-123">To find a specific offer by ID, execute the [**Get-PartnerOffer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOffer.md) command, and specify the **CountryCode** and **OfferId** parameters.</span></span>

```powershell
# $countryCode
# $offerId

Get-PartnerOffer -Country $countryCode -OfferId $offerId
```

## <a name="rest-request"></a><span data-ttu-id="78d48-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="78d48-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="78d48-125">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="78d48-125">Request syntax</span></span>

| <span data-ttu-id="78d48-126">Methode</span><span class="sxs-lookup"><span data-stu-id="78d48-126">Method</span></span>  | <span data-ttu-id="78d48-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="78d48-127">Request URI</span></span>                                                                                    |
|---------|------------------------------------------------------------------------------------------------|
| <span data-ttu-id="78d48-128">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="78d48-128">**GET**</span></span> | <span data-ttu-id="78d48-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers/{offer-id}? land = {land-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="78d48-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/offers/{offer-id}?country={country-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="78d48-130">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="78d48-130">URI parameter</span></span>

| <span data-ttu-id="78d48-131">Naam</span><span class="sxs-lookup"><span data-stu-id="78d48-131">Name</span></span>           | <span data-ttu-id="78d48-132">Type</span><span class="sxs-lookup"><span data-stu-id="78d48-132">Type</span></span>       | <span data-ttu-id="78d48-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="78d48-133">Required</span></span> | <span data-ttu-id="78d48-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="78d48-134">Description</span></span>                           |
|----------------|------------|----------|---------------------------------------|
| <span data-ttu-id="78d48-135">**aanbieding-ID**</span><span class="sxs-lookup"><span data-stu-id="78d48-135">**offer-id**</span></span>   | <span data-ttu-id="78d48-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="78d48-136">**guid**</span></span>   | <span data-ttu-id="78d48-137">J</span><span class="sxs-lookup"><span data-stu-id="78d48-137">Y</span></span>        | <span data-ttu-id="78d48-138">Een GUID die overeenkomt met de aanbieding.</span><span class="sxs-lookup"><span data-stu-id="78d48-138">A GUID that corresponds to the offer.</span></span> |
| <span data-ttu-id="78d48-139">**land-id**</span><span class="sxs-lookup"><span data-stu-id="78d48-139">**country-id**</span></span> | <span data-ttu-id="78d48-140">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="78d48-140">**string**</span></span> | <span data-ttu-id="78d48-141">J</span><span class="sxs-lookup"><span data-stu-id="78d48-141">Y</span></span>        | <span data-ttu-id="78d48-142">De ID van het land/de regio.</span><span class="sxs-lookup"><span data-stu-id="78d48-142">The country/region ID.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="78d48-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="78d48-143">Request headers</span></span>

- <span data-ttu-id="78d48-144">Een **land instellingen-id** die is opgemaakt als een teken reeks is vereist.</span><span class="sxs-lookup"><span data-stu-id="78d48-144">A **locale-id** formatted as a string is required.</span></span>
<span data-ttu-id="78d48-145">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="78d48-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="78d48-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="78d48-146">Request body</span></span>

<span data-ttu-id="78d48-147">Geen.</span><span class="sxs-lookup"><span data-stu-id="78d48-147">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="78d48-148">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="78d48-148">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/offers/<offer-id>?country=<country-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
X-Locale: <locale-id>
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="78d48-149">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="78d48-149">REST response</span></span>

<span data-ttu-id="78d48-150">Als dit lukt, retourneert deze methode een resource voor de **aanbieding** in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="78d48-150">If successful, this method returns an **Offer** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="78d48-151">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="78d48-151">Response success and error codes</span></span>

<span data-ttu-id="78d48-152">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="78d48-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="78d48-153">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="78d48-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="78d48-154">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="78d48-154">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="78d48-155">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="78d48-155">Response example</span></span>

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
