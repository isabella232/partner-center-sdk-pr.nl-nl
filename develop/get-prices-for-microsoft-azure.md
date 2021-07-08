---
title: Prijzen voor Microsoft Azure ophalen
description: Een Azure-tariefkaart met realtime prijzen voor een Azure-aanbieding krijgen. Azure-prijzen zijn zeer dynamisch en veranderen regelmatig.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4f66ab19ef3723fbaa27acff941cf48683a7c25c
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548784"
---
# <a name="get-prices-for-microsoft-azure"></a><span data-ttu-id="6ffe2-104">Prijzen voor Microsoft Azure ophalen</span><span class="sxs-lookup"><span data-stu-id="6ffe2-104">Get prices for Microsoft Azure</span></span>

<span data-ttu-id="6ffe2-105">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6ffe2-105">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6ffe2-106">Een [Azure-tariefkaart met](azure-rate-card-resources.md) realtime prijzen voor een Azure-aanbieding krijgen.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-106">How to get an [Azure Rate Card](azure-rate-card-resources.md) with real-time prices for an Azure offer.</span></span> <span data-ttu-id="6ffe2-107">Azure-prijzen zijn zeer dynamisch en veranderen regelmatig.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-107">Azure pricing is quite dynamic and changes frequently.</span></span>

<span data-ttu-id="6ffe2-108">Als u het gebruik wilt bijhouden en uw maandelijkse factuur en de facturen voor afzonderlijke klanten wilt voorspellen, kunt u deze Azure Rate Card-query combineren om prijzen voor Microsoft Azure op te halen met een aanvraag om de gebruiksrecords van een klant voor Azure op te [halen.](get-a-customer-s-utilization-record-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="6ffe2-108">To track usage and help predict your monthly bill and the bills for individual customers, you can combine this Azure Rate Card query to get prices for Microsoft Azure with a request to [Get a customer's utilization records for Azure](get-a-customer-s-utilization-record-for-azure.md).</span></span>

<span data-ttu-id="6ffe2-109">De prijzen verschillen per markt en valuta en deze API houdt rekening met de locatie.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-109">Prices differ by market and currency, and this API takes location into consideration.</span></span> <span data-ttu-id="6ffe2-110">De API maakt standaard gebruik van uw partnerprofielinstellingen in Partner Center en uw browsertaal. Deze instellingen kunnen worden aangepast.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-110">By default, the API uses your partner profile settings in Partner Center and your browser language, and those settings are customizable.</span></span> <span data-ttu-id="6ffe2-111">De locatiebewustheid is vooral relevant als u de verkoop in meerdere markten beheert vanuit één gecentraliseerd kantoor.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-111">The location awareness is especially relevant if you manage sales in multiple markets from a single, centralized office.</span></span> <span data-ttu-id="6ffe2-112">Zie [URI-parameters voor meer informatie.](#uri-parameters)</span><span class="sxs-lookup"><span data-stu-id="6ffe2-112">For more information, see [URI parameters](#uri-parameters).</span></span>

## <a name="c"></a><span data-ttu-id="6ffe2-113">C\#</span><span class="sxs-lookup"><span data-stu-id="6ffe2-113">C\#</span></span>

<span data-ttu-id="6ffe2-114">Als u de Azure-tariefkaart wilt verkrijgen, roept u de methode [**IAzureRateCard.Get**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.get) aan om een [**AzureRateCard-resource**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) te retourneren die de Azure-prijzen bevat.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-114">To obtain the Azure Rate Card, call the [**IAzureRateCard.Get**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.get) method to return an [**AzureRateCard**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) resource that contains the Azure prices.</span></span>

```csharp
// IAggregatePartner partnerOperations;

var azureRateCard = partner.RateCards.Azure.Get();
```

<span data-ttu-id="6ffe2-115">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="6ffe2-115">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="6ffe2-116">**Project**: Partnercentrum-SDK Samples **Class**: GetAzureRateCard.cs</span><span class="sxs-lookup"><span data-stu-id="6ffe2-116">**Project**: Partner Center SDK Samples **Class**: GetAzureRateCard.cs</span></span>

## <a name="java"></a><span data-ttu-id="6ffe2-117">Java</span><span class="sxs-lookup"><span data-stu-id="6ffe2-117">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="6ffe2-118">Als u de Azure-tariefkaart wilt verkrijgen, roept u de **functie IAzureRateCard.get** aan om tariefkaartgegevens te retourneren die de Azure-prijzen bevatten.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-118">To obtain the Azure Rate Card, call the **IAzureRateCard.get** function to return rate card details that contains the Azure prices.</span></span>

```java
// IAggregatePartner partnerOperations;

AzureRateCard azureRateCard = partner.getRateCards().getAzure().get();
```

## <a name="powershell"></a><span data-ttu-id="6ffe2-119">PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ffe2-119">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="6ffe2-120">Als u de Azure-kaart wilt verkrijgen, voert u [**de opdracht Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) uit om tariefkaartgegevens te retourneren die de Azure-prijzen bevatten.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-120">To obtain the Azure Card, execute the [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) command to return rate card details that contains the Azure prices.</span></span>

```powershell
Get-PartnerAzureRateCard
```

## <a name="rest-request"></a><span data-ttu-id="6ffe2-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="6ffe2-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6ffe2-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="6ffe2-122">Request syntax</span></span>

| <span data-ttu-id="6ffe2-123">Methode</span><span class="sxs-lookup"><span data-stu-id="6ffe2-123">Method</span></span>  | <span data-ttu-id="6ffe2-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="6ffe2-124">Request URI</span></span>                                                        |
|---------|--------------------------------------------------------------------|
| <span data-ttu-id="6ffe2-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="6ffe2-125">**GET**</span></span> | <span data-ttu-id="6ffe2-126">*{baseURL}*/v1/ratecards/azure?currency={currency}&region={region}</span><span class="sxs-lookup"><span data-stu-id="6ffe2-126">*{baseURL}*/v1/ratecards/azure?currency={currency}&region={region}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="6ffe2-127">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="6ffe2-127">URI parameters</span></span>

| <span data-ttu-id="6ffe2-128">Naam</span><span class="sxs-lookup"><span data-stu-id="6ffe2-128">Name</span></span>     | <span data-ttu-id="6ffe2-129">Type</span><span class="sxs-lookup"><span data-stu-id="6ffe2-129">Type</span></span>   | <span data-ttu-id="6ffe2-130">Vereist</span><span class="sxs-lookup"><span data-stu-id="6ffe2-130">Required</span></span> | <span data-ttu-id="6ffe2-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6ffe2-131">Description</span></span>                                                                                                                                                                               |
|----------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6ffe2-132">currency</span><span class="sxs-lookup"><span data-stu-id="6ffe2-132">currency</span></span> | <span data-ttu-id="6ffe2-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6ffe2-133">string</span></span> | <span data-ttu-id="6ffe2-134">No</span><span class="sxs-lookup"><span data-stu-id="6ffe2-134">No</span></span>       | <span data-ttu-id="6ffe2-135">Optionele ISO-code van drie letters voor de valuta waarin de resourcetarieven worden opgegeven (bijvoorbeeld `EUR` ).</span><span class="sxs-lookup"><span data-stu-id="6ffe2-135">Optional three letter ISO code for the currency in which the resource rates will be provided (for example `EUR`).</span></span> <span data-ttu-id="6ffe2-136">De standaardwaarde is `USD`.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-136">The default is `USD`.</span></span> |
| <span data-ttu-id="6ffe2-137">regio</span><span class="sxs-lookup"><span data-stu-id="6ffe2-137">region</span></span>   | <span data-ttu-id="6ffe2-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6ffe2-138">string</span></span> | <span data-ttu-id="6ffe2-139">No</span><span class="sxs-lookup"><span data-stu-id="6ffe2-139">No</span></span>       | <span data-ttu-id="6ffe2-140">Optionele iso-land-/regiocode van twee letters die de markt aangeeft waarop de aanbieding is gekocht (bijvoorbeeld `FR` ).</span><span class="sxs-lookup"><span data-stu-id="6ffe2-140">Optional two-letter ISO country/region code that indicates the market where the offer is purchased (for example `FR`).</span></span> <span data-ttu-id="6ffe2-141">De standaardwaarde is `US`.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-141">The default is `US`.</span></span>        |

<span data-ttu-id="6ffe2-142">U kunt de optionele X-Locale-header [opnemen](headers.md#rest-request-headers) in uw aanvraag.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-142">You can include the optional X-Locale [header](headers.md#rest-request-headers) in your request.</span></span> <span data-ttu-id="6ffe2-143">Als u de X-Locale-header niet op neemt, wordt de standaardwaarde ('en-US') gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-143">If you don't include the X-Locale header, the default value ("en-US") is used.</span></span>

- <span data-ttu-id="6ffe2-144">Als u valuta- en regioparameters in uw aanvraag op geeft, wordt de waarde van X-Locale gebruikt om de taal van het antwoord te bepalen.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-144">If you provide currency and region parameters in your request, the value of X-Locale is used to determine the response's language.</span></span>

- <span data-ttu-id="6ffe2-145">Als u geen regio- en valutaparameters in uw aanvraag op geeft, wordt de waarde van X-Locale gebruikt om de regio, valuta en taal van het antwoord te bepalen.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-145">If you don't provide region and currency parameters in your request, the value of X-Locale is used to determine the response's region, currency, and language.</span></span>

### <a name="request-header"></a><span data-ttu-id="6ffe2-146">Aanvraagheader</span><span class="sxs-lookup"><span data-stu-id="6ffe2-146">Request header</span></span>

<span data-ttu-id="6ffe2-147">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="6ffe2-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6ffe2-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="6ffe2-148">Request body</span></span>

<span data-ttu-id="6ffe2-149">Geen.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6ffe2-150">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6ffe2-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/ratecards/azure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 07ced227-3f32-4eeb-8062-f0bef849a9bc
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="6ffe2-151">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="6ffe2-151">REST response</span></span>

<span data-ttu-id="6ffe2-152">Als de aanvraag is geslaagd, wordt een [Azure Rate Card-resource](azure-rate-card-resources.md) retourneert.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-152">If the request is successful, it returns an [Azure Rate Card](azure-rate-card-resources.md) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6ffe2-153">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="6ffe2-153">Response success and error codes</span></span>

<span data-ttu-id="6ffe2-154">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6ffe2-155">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="6ffe2-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6ffe2-156">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="6ffe2-156">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6ffe2-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="6ffe2-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1545508
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57b25659-fc00-4215-87e7-2b09bac6845d
MS-RequestId: 870118d0-adbb-41a3-82d2-a3d45ade3c73
MS-CV: CYBB8PXMsEukJBIn.0
MS-ServerId: 201021413
Date: Wed, 01 Feb 2017 00:13:45 GMT

{
    "locale": "en",
    "currency": "USD",
    "isTaxIncluded": false,
    "meters": [{
            "id": "4b836326-7e19-46e6-8bce-1b19bb6cd91e",
            "name": "Unlimited Data - 1 Gbps",
            "rates": {
                "0": 7395.0
            },
            "tags": [],
            "category": "Networking",
            "subcategory": "ExpressRoute",
            "region": "Zone 2",
            "unit": "Connections",
            "includedQuantity": 0.0,
            "effectiveDate": "2015-09-01T00:00:00Z"
        }, {
            "id": "1e8f6d9f-8b40-4c97-80cc-cff87a290a93",
            "name": "Compute Hours",
            "rates": {
                "0": 3.9729
            },
            "tags": [],
            "category": "Cloud Services",
            "subcategory": "Standard_L16 Cloud Services",
            "region": "AU East",
            "unit": "1 Hour",
            "includedQuantity": 0.0,
            "effectiveDate": "2016-09-01T00:00:00Z"
        }, {
            "id": "7a2639ce-ae47-4413-9837-6b4f4b78be3d",
            "name": "Compute Hours",
            "rates": {
                "0": 0.1122
            },
            "tags": [],
            "category": "Virtual Machines",
            "subcategory": "Standard_D1_v2 VM (Windows)",
            "region": "BR South",
            "unit": "Hours",
            "includedQuantity": 0.0,
            "effectiveDate": "2017-01-01T00:00:00Z"
        }
    ],
    "offerTerms": [{
            "name": "Overage discount",
            "discount": 0.15,
            "excludedMeterIds": ["53cc0061-0fe2-4249-bf62-e1008c811f5c", "c82dbd27-c978-43a7-ad41-525a90d8962b"],
            "effectiveDate": "2014-01-01T00:00:00"
        }
    ],
    "attributes": {
        "objectType": "AzureRateCard"
    }
}
```
