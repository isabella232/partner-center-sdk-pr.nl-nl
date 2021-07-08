---
title: Prijzen voor Microsoft Azure Partner Shared Services ophalen
description: Een Azure-tariefkaart met prijzen voor Microsoft Azure Partner Shared Services.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0008d7474f7e57bbbd765afdf2487ee279848ac3
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548801"
---
# <a name="get-prices-for-microsoft-azure-partner-shared-services"></a><span data-ttu-id="fdefd-103">Prijzen voor Microsoft Azure Partner Shared Services ophalen</span><span class="sxs-lookup"><span data-stu-id="fdefd-103">Get prices for Microsoft Azure Partner Shared Services</span></span>

<span data-ttu-id="fdefd-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="fdefd-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="fdefd-105">Een Azure-tariefkaart [met prijzen voor](azure-rate-card-resources.md) Microsoft Azure Partner Shared Services.</span><span class="sxs-lookup"><span data-stu-id="fdefd-105">How to get an [Azure Rate Card](azure-rate-card-resources.md) with prices for Microsoft Azure Partner Shared Services.</span></span>

<span data-ttu-id="fdefd-106">De prijzen verschillen per markt en valuta en deze API houdt rekening met de locatie.</span><span class="sxs-lookup"><span data-stu-id="fdefd-106">Prices differ by market and currency, and this API takes location into consideration.</span></span> <span data-ttu-id="fdefd-107">De API maakt standaard gebruik van uw partnerprofielinstellingen in Partner Center en uw browsertaal. Deze instellingen kunnen worden aangepast.</span><span class="sxs-lookup"><span data-stu-id="fdefd-107">By default, the API uses your partner profile settings in Partner Center and your browser language, and those settings are customizable.</span></span> <span data-ttu-id="fdefd-108">De locatiebewustheid is vooral relevant als u de verkoop in meerdere markten beheert vanuit één gecentraliseerd kantoor.</span><span class="sxs-lookup"><span data-stu-id="fdefd-108">The location awareness is especially relevant if you manage sales in multiple markets from a single, centralized office.</span></span>

## <a name="example-code"></a><span data-ttu-id="fdefd-109">Voorbeeldcode</span><span class="sxs-lookup"><span data-stu-id="fdefd-109">Example Code</span></span>

## <a name="c"></a><span data-ttu-id="fdefd-110">C\#</span><span class="sxs-lookup"><span data-stu-id="fdefd-110">C\#</span></span>

<span data-ttu-id="fdefd-111">Als u de Azure-tariefkaart wilt verkrijgen, roept u de methode [**IAzureRateCard.GetShared**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.getshared) aan om een [**AzureRateCard-resource**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) te retourneren die de Azure-prijzen bevat.</span><span class="sxs-lookup"><span data-stu-id="fdefd-111">To obtain the Azure Rate Card, call the [**IAzureRateCard.GetShared**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.getshared) method to return an [**AzureRateCard**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) resource that contains the Azure prices.</span></span>

```csharp
// IAggregatePartner partnerOperations;

var azureRateCard = partner.RateCards.Azure.GetShared();
```

## <a name="java"></a><span data-ttu-id="fdefd-112">Java</span><span class="sxs-lookup"><span data-stu-id="fdefd-112">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="fdefd-113">Als u de Azure-tariefkaart wilt verkrijgen, roept u de functie **IAzureRateCard.getShared** aan om details van de tariefkaart te retourneren die de Azure-prijzen bevatten.</span><span class="sxs-lookup"><span data-stu-id="fdefd-113">To obtain the Azure Rate Card, call the **IAzureRateCard.getShared** function to return rate card details that contains the Azure prices.</span></span>

```java
// IAggregatePartner partnerOperations;

AzureRateCard azureRateCard = partner.getRateCards().getAzure().getShared();
```

## <a name="powershell"></a><span data-ttu-id="fdefd-114">PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdefd-114">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="fdefd-115">Als u de Azure-kaart wilt verkrijgen, voert u de opdracht [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) uit en geeft u de parameter **SharedServices** op om tariefkaartgegevens te retourneren die de Azure-prijzen bevatten.</span><span class="sxs-lookup"><span data-stu-id="fdefd-115">To obtain the Azure Card, execute the [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) command and specify the **SharedServices** parameter to return rate card details that contains the Azure prices.</span></span>

```powershell
Get-PartnerAzureRateCard -SharedServices
```

## <a name="rest-request"></a><span data-ttu-id="fdefd-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fdefd-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fdefd-117">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="fdefd-117">Request syntax</span></span>

| <span data-ttu-id="fdefd-118">Methode</span><span class="sxs-lookup"><span data-stu-id="fdefd-118">Method</span></span>  | <span data-ttu-id="fdefd-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fdefd-119">Request URI</span></span>                                                               |
|---------|---------------------------------------------------------------------------|
| <span data-ttu-id="fdefd-120">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fdefd-120">**GET**</span></span> | <span data-ttu-id="fdefd-121">*{baseURL}*/v1/ratecards/azure-shared?currency={currency}&region={region}</span><span class="sxs-lookup"><span data-stu-id="fdefd-121">*{baseURL}*/v1/ratecards/azure-shared?currency={currency}&region={region}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="fdefd-122">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="fdefd-122">URI parameters</span></span>

| <span data-ttu-id="fdefd-123">Naam</span><span class="sxs-lookup"><span data-stu-id="fdefd-123">Name</span></span>     | <span data-ttu-id="fdefd-124">Type</span><span class="sxs-lookup"><span data-stu-id="fdefd-124">Type</span></span>   | <span data-ttu-id="fdefd-125">Vereist</span><span class="sxs-lookup"><span data-stu-id="fdefd-125">Required</span></span> | <span data-ttu-id="fdefd-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fdefd-126">Description</span></span>                                                                                                                                                                               |
|----------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fdefd-127">currency</span><span class="sxs-lookup"><span data-stu-id="fdefd-127">currency</span></span> | <span data-ttu-id="fdefd-128">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdefd-128">string</span></span> | <span data-ttu-id="fdefd-129">No</span><span class="sxs-lookup"><span data-stu-id="fdefd-129">No</span></span>       | <span data-ttu-id="fdefd-130">Optionele ISO-code van drie letters voor de valuta waarin de resourcetarieven worden opgegeven (bijvoorbeeld `EUR` ).</span><span class="sxs-lookup"><span data-stu-id="fdefd-130">Optional three letter ISO code for the currency in which the resource rates will be provided (for example `EUR`).</span></span> <span data-ttu-id="fdefd-131">De standaardwaarde is de valuta die is gekoppeld aan de markt in het partnerprofiel.</span><span class="sxs-lookup"><span data-stu-id="fdefd-131">The default is the currency associated with the market in the partner profile.</span></span> |
| <span data-ttu-id="fdefd-132">regio</span><span class="sxs-lookup"><span data-stu-id="fdefd-132">region</span></span>   | <span data-ttu-id="fdefd-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdefd-133">string</span></span> | <span data-ttu-id="fdefd-134">No</span><span class="sxs-lookup"><span data-stu-id="fdefd-134">No</span></span>       | <span data-ttu-id="fdefd-135">Optionele iso-land-/regiocode van twee letters die de markt aangeeft waarop de aanbieding is gekocht (bijvoorbeeld `FR` ).</span><span class="sxs-lookup"><span data-stu-id="fdefd-135">Optional two-letter ISO country/region code that indicates the market where the offer is purchased (for example `FR`).</span></span> <span data-ttu-id="fdefd-136">De standaardwaarde is de land-/regiocode die is ingesteld in het partnerprofiel.</span><span class="sxs-lookup"><span data-stu-id="fdefd-136">The default is the country/region code set in the partner profile.</span></span>        |

<span data-ttu-id="fdefd-137">Als de optionele X-Locale-header is opgenomen in de aanvraag, bepaalt de waarde de taal die wordt gebruikt voor de details in het antwoord.</span><span class="sxs-lookup"><span data-stu-id="fdefd-137">If the optional X-Locale header is included in the request, its value determines the language used for the details in the response.</span></span>

### <a name="request-headers"></a><span data-ttu-id="fdefd-138">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="fdefd-138">Request headers</span></span>

<span data-ttu-id="fdefd-139">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="fdefd-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fdefd-140">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="fdefd-140">Request body</span></span>

<span data-ttu-id="fdefd-141">Geen.</span><span class="sxs-lookup"><span data-stu-id="fdefd-141">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="fdefd-142">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fdefd-142">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/ratecards/azure-shared HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 07ced227-3f32-4eeb-8062-f0bef849a9bc
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="fdefd-143">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fdefd-143">REST response</span></span>

<span data-ttu-id="fdefd-144">Als de aanvraag is geslaagd, wordt een [Azure Rate Card-resource](azure-rate-card-resources.md) retourneert.</span><span class="sxs-lookup"><span data-stu-id="fdefd-144">If the request is successful, it returns an [Azure Rate Card](azure-rate-card-resources.md) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fdefd-145">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="fdefd-145">Response success and error codes</span></span>

<span data-ttu-id="fdefd-146">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="fdefd-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fdefd-147">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fdefd-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fdefd-148">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="fdefd-148">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fdefd-149">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fdefd-149">Response example</span></span>

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
    "locale": "en-US",
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
