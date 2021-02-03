---
title: Prijzen voor Microsoft Azure ophalen
description: Hoe u een Azure-tarief kaart krijgt met real-time prijzen voor een Azure-aanbieding. Prijzen voor Azure zijn vaak dynamisch en worden gewijzigd.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0716f0428b13604105b435a2ce8287a8b4609fea
ms.sourcegitcommit: 64c498d3571f2287305968890578bc7396779621
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/19/2020
ms.locfileid: "97768690"
---
# <a name="get-prices-for-microsoft-azure"></a><span data-ttu-id="fda94-104">Prijzen voor Microsoft Azure ophalen</span><span class="sxs-lookup"><span data-stu-id="fda94-104">Get prices for Microsoft Azure</span></span>

<span data-ttu-id="fda94-105">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="fda94-105">**Applies To**</span></span>

- <span data-ttu-id="fda94-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="fda94-106">Partner Center</span></span>
- <span data-ttu-id="fda94-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="fda94-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="fda94-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="fda94-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="fda94-109">Hoe u een [Azure-tarief kaart](azure-rate-card-resources.md) krijgt met real-time prijzen voor een Azure-aanbieding.</span><span class="sxs-lookup"><span data-stu-id="fda94-109">How to get an [Azure Rate Card](azure-rate-card-resources.md) with real-time prices for an Azure offer.</span></span> <span data-ttu-id="fda94-110">Prijzen voor Azure zijn vaak dynamisch en worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="fda94-110">Azure pricing is quite dynamic and changes frequently.</span></span>

<span data-ttu-id="fda94-111">Om het gebruik bij te houden en te helpen uw maandelijkse factuur en de facturen voor afzonderlijke klanten te voors pellen, kunt u deze Azure Rate Card-query combi neren om prijzen voor Microsoft Azure op te halen met een aanvraag om [de gebruiks gegevens van een klant voor Azure te verkrijgen](get-a-customer-s-utilization-record-for-azure.md).</span><span class="sxs-lookup"><span data-stu-id="fda94-111">To track usage and help predict your monthly bill and the bills for individual customers, you can combine this Azure Rate Card query to get prices for Microsoft Azure with a request to [Get a customer's utilization records for Azure](get-a-customer-s-utilization-record-for-azure.md).</span></span>

<span data-ttu-id="fda94-112">De prijzen zijn afhankelijk van de markt en valuta en deze API houdt rekening met de locatie.</span><span class="sxs-lookup"><span data-stu-id="fda94-112">Prices differ by market and currency, and this API takes location into consideration.</span></span> <span data-ttu-id="fda94-113">De API maakt standaard gebruik van uw partner Profiel instellingen in partner centrum en uw browser taal, en deze instellingen zijn aanpasbaar.</span><span class="sxs-lookup"><span data-stu-id="fda94-113">By default, the API uses your partner profile settings in Partner Center and your browser language, and those settings are customizable.</span></span> <span data-ttu-id="fda94-114">De locatie van het bewustzijn is vooral relevant als u de verkoop op meerdere markten beheert vanuit één gecentraliseerd kantoor.</span><span class="sxs-lookup"><span data-stu-id="fda94-114">The location awareness is especially relevant if you manage sales in multiple markets from a single, centralized office.</span></span> <span data-ttu-id="fda94-115">Zie [URI-para meters](#uri-parameters)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fda94-115">For more information, see [URI parameters](#uri-parameters).</span></span>

## <a name="c"></a><span data-ttu-id="fda94-116">C\#</span><span class="sxs-lookup"><span data-stu-id="fda94-116">C\#</span></span>

<span data-ttu-id="fda94-117">Als u de Azure-tarief kaart wilt ophalen, roept u de [**IAzureRateCard. Get**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.get) -methode aan om een [**AzureRateCard**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) -resource te retour neren die de Azure-prijzen bevat.</span><span class="sxs-lookup"><span data-stu-id="fda94-117">To obtain the Azure Rate Card, call the [**IAzureRateCard.Get**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.get) method to return an [**AzureRateCard**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) resource that contains the Azure prices.</span></span>

```csharp
// IAggregatePartner partnerOperations;

var azureRateCard = partner.RateCards.Azure.Get();
```

<span data-ttu-id="fda94-118">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="fda94-118">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="fda94-119">**Project**: Partner Center SDK-voor beelden **klasse**: GetAzureRateCard.cs</span><span class="sxs-lookup"><span data-stu-id="fda94-119">**Project**: Partner Center SDK Samples **Class**: GetAzureRateCard.cs</span></span>

## <a name="java"></a><span data-ttu-id="fda94-120">Java</span><span class="sxs-lookup"><span data-stu-id="fda94-120">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="fda94-121">Als u de Azure-tarief kaart wilt ophalen, roept u de functie **IAzureRateCard. Get** aan om de tarief kaart gegevens te retour neren die de Azure-prijzen bevatten.</span><span class="sxs-lookup"><span data-stu-id="fda94-121">To obtain the Azure Rate Card, call the **IAzureRateCard.get** function to return rate card details that contains the Azure prices.</span></span>

```java
// IAggregatePartner partnerOperations;

AzureRateCard azureRateCard = partner.getRateCards().getAzure().get();
```

## <a name="powershell"></a><span data-ttu-id="fda94-122">PowerShell</span><span class="sxs-lookup"><span data-stu-id="fda94-122">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="fda94-123">Als u de Azure-kaart wilt ophalen, voert u de opdracht [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) uit om de tarief kaart gegevens te retour neren die de prijzen van Azure bevatten.</span><span class="sxs-lookup"><span data-stu-id="fda94-123">To obtain the Azure Card, execute the [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) command to return rate card details that contains the Azure prices.</span></span>

```powershell
Get-PartnerAzureRateCard
```

## <a name="rest-request"></a><span data-ttu-id="fda94-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fda94-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fda94-125">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fda94-125">Request syntax</span></span>

| <span data-ttu-id="fda94-126">Methode</span><span class="sxs-lookup"><span data-stu-id="fda94-126">Method</span></span>  | <span data-ttu-id="fda94-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fda94-127">Request URI</span></span>                                                        |
|---------|--------------------------------------------------------------------|
| <span data-ttu-id="fda94-128">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fda94-128">**GET**</span></span> | <span data-ttu-id="fda94-129">*{baseURL}*/v1/ratecards/Azure? Currency = {currency} &regio = {Region}</span><span class="sxs-lookup"><span data-stu-id="fda94-129">*{baseURL}*/v1/ratecards/azure?currency={currency}&region={region}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="fda94-130">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="fda94-130">URI parameters</span></span>

| <span data-ttu-id="fda94-131">Naam</span><span class="sxs-lookup"><span data-stu-id="fda94-131">Name</span></span>     | <span data-ttu-id="fda94-132">Type</span><span class="sxs-lookup"><span data-stu-id="fda94-132">Type</span></span>   | <span data-ttu-id="fda94-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="fda94-133">Required</span></span> | <span data-ttu-id="fda94-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fda94-134">Description</span></span>                                                                                                                                                                               |
|----------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fda94-135">currency</span><span class="sxs-lookup"><span data-stu-id="fda94-135">currency</span></span> | <span data-ttu-id="fda94-136">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fda94-136">string</span></span> | <span data-ttu-id="fda94-137">No</span><span class="sxs-lookup"><span data-stu-id="fda94-137">No</span></span>       | <span data-ttu-id="fda94-138">Optionele ISO-code van drie letters voor de valuta waarin de resource tarieven worden gegeven (bijvoorbeeld `EUR` ).</span><span class="sxs-lookup"><span data-stu-id="fda94-138">Optional three letter ISO code for the currency in which the resource rates will be provided (for example `EUR`).</span></span> <span data-ttu-id="fda94-139">De standaardwaarde is `USD`.</span><span class="sxs-lookup"><span data-stu-id="fda94-139">The default is `USD`.</span></span> |
| <span data-ttu-id="fda94-140">regio</span><span class="sxs-lookup"><span data-stu-id="fda94-140">region</span></span>   | <span data-ttu-id="fda94-141">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fda94-141">string</span></span> | <span data-ttu-id="fda94-142">No</span><span class="sxs-lookup"><span data-stu-id="fda94-142">No</span></span>       | <span data-ttu-id="fda94-143">Optionele ISO-land/regio code van twee letters waarmee de markt wordt aangegeven waar de aanbieding wordt gekocht (bijvoorbeeld `FR` ).</span><span class="sxs-lookup"><span data-stu-id="fda94-143">Optional two-letter ISO country/region code that indicates the market where the offer is purchased (for example `FR`).</span></span> <span data-ttu-id="fda94-144">De standaardwaarde is `US`.</span><span class="sxs-lookup"><span data-stu-id="fda94-144">The default is `US`.</span></span>        |

<span data-ttu-id="fda94-145">U kunt de optionele X-locale- [header](headers.md#rest-request-headers) in uw aanvraag toevoegen.</span><span class="sxs-lookup"><span data-stu-id="fda94-145">You can include the optional X-Locale [header](headers.md#rest-request-headers) in your request.</span></span> <span data-ttu-id="fda94-146">Als u de header X-locale niet opneemt, wordt de standaard waarde ("en-US") gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fda94-146">If you don't include the X-Locale header, the default value ("en-US") is used.</span></span>

- <span data-ttu-id="fda94-147">Als u in uw aanvraag valuta-en regio parameters opgeeft, wordt de waarde van de X-land instelling gebruikt om de taal van het antwoord te bepalen.</span><span class="sxs-lookup"><span data-stu-id="fda94-147">If you provide currency and region parameters in your request, the value of X-Locale is used to determine the response's language.</span></span>

- <span data-ttu-id="fda94-148">Als u geen regio-en valuta parameters in uw aanvraag opgeeft, wordt de waarde van de X-land instelling gebruikt om de regio, valuta en taal van het antwoord te bepalen.</span><span class="sxs-lookup"><span data-stu-id="fda94-148">If you don't provide region and currency parameters in your request, the value of X-Locale is used to determine the response's region, currency, and language.</span></span>

### <a name="request-header"></a><span data-ttu-id="fda94-149">Aanvraagheader</span><span class="sxs-lookup"><span data-stu-id="fda94-149">Request header</span></span>

<span data-ttu-id="fda94-150">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="fda94-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fda94-151">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="fda94-151">Request body</span></span>

<span data-ttu-id="fda94-152">Geen.</span><span class="sxs-lookup"><span data-stu-id="fda94-152">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="fda94-153">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fda94-153">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="fda94-154">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fda94-154">REST response</span></span>

<span data-ttu-id="fda94-155">Als de aanvraag is voltooid, wordt een [Azure-tarieven](azure-rate-card-resources.md) resource geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fda94-155">If the request is successful, it returns an [Azure Rate Card](azure-rate-card-resources.md) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fda94-156">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="fda94-156">Response success and error codes</span></span>

<span data-ttu-id="fda94-157">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="fda94-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fda94-158">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fda94-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fda94-159">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="fda94-159">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fda94-160">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fda94-160">Response example</span></span>

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
