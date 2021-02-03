---
title: Prijzen voor Microsoft Azure Partner Shared Services ophalen
description: Hoe u een Azure-tarief kaart krijgt met de prijzen voor de gedeelde services van Microsoft Azure partner.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: cd396c35b6b89de4d0f092ba4da738a2ed0ac633
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767563"
---
# <a name="get-prices-for-microsoft-azure-partner-shared-services"></a><span data-ttu-id="faec3-103">Prijzen voor Microsoft Azure Partner Shared Services ophalen</span><span class="sxs-lookup"><span data-stu-id="faec3-103">Get prices for Microsoft Azure Partner Shared Services</span></span>

<span data-ttu-id="faec3-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="faec3-104">**Applies To**</span></span>

- <span data-ttu-id="faec3-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="faec3-105">Partner Center</span></span>
- <span data-ttu-id="faec3-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="faec3-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="faec3-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="faec3-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="faec3-108">Hoe u een [Azure-tarief kaart](azure-rate-card-resources.md) krijgt met de prijzen voor de gedeelde Services van Microsoft Azure partner.</span><span class="sxs-lookup"><span data-stu-id="faec3-108">How to get an [Azure Rate Card](azure-rate-card-resources.md) with prices for Microsoft Azure Partner Shared Services.</span></span>

<span data-ttu-id="faec3-109">De prijzen zijn afhankelijk van de markt en valuta en deze API houdt rekening met de locatie.</span><span class="sxs-lookup"><span data-stu-id="faec3-109">Prices differ by market and currency, and this API takes location into consideration.</span></span> <span data-ttu-id="faec3-110">De API maakt standaard gebruik van uw partner Profiel instellingen in partner centrum en uw browser taal, en deze instellingen zijn aanpasbaar.</span><span class="sxs-lookup"><span data-stu-id="faec3-110">By default, the API uses your partner profile settings in Partner Center and your browser language, and those settings are customizable.</span></span> <span data-ttu-id="faec3-111">De locatie van het bewustzijn is vooral relevant als u de verkoop op meerdere markten beheert vanuit één gecentraliseerd kantoor.</span><span class="sxs-lookup"><span data-stu-id="faec3-111">The location awareness is especially relevant if you manage sales in multiple markets from a single, centralized office.</span></span>

## <a name="example-code"></a><span data-ttu-id="faec3-112">Voorbeeld code</span><span class="sxs-lookup"><span data-stu-id="faec3-112">Example Code</span></span>

## <a name="c"></a><span data-ttu-id="faec3-113">C\#</span><span class="sxs-lookup"><span data-stu-id="faec3-113">C\#</span></span>

<span data-ttu-id="faec3-114">Als u de Azure-tarief kaart wilt ophalen, roept u de methode [**IAzureRateCard. GetShared**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.getshared) aan om een [**AzureRateCard**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) -resource te retour neren die de Azure-prijzen bevat.</span><span class="sxs-lookup"><span data-stu-id="faec3-114">To obtain the Azure Rate Card, call the [**IAzureRateCard.GetShared**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.getshared) method to return an [**AzureRateCard**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) resource that contains the Azure prices.</span></span>

```csharp
// IAggregatePartner partnerOperations;

var azureRateCard = partner.RateCards.Azure.GetShared();
```

## <a name="java"></a><span data-ttu-id="faec3-115">Java</span><span class="sxs-lookup"><span data-stu-id="faec3-115">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="faec3-116">Als u de Azure-tarief kaart wilt ophalen, roept u de functie **IAzureRateCard. getShared** aan om de tarief kaart gegevens te retour neren die de Azure-prijzen bevatten.</span><span class="sxs-lookup"><span data-stu-id="faec3-116">To obtain the Azure Rate Card, call the **IAzureRateCard.getShared** function to return rate card details that contains the Azure prices.</span></span>

```java
// IAggregatePartner partnerOperations;

AzureRateCard azureRateCard = partner.getRateCards().getAzure().getShared();
```

## <a name="powershell"></a><span data-ttu-id="faec3-117">PowerShell</span><span class="sxs-lookup"><span data-stu-id="faec3-117">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="faec3-118">Als u de Azure-kaart wilt ophalen, voert u de opdracht [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) uit en geeft u de para meter **SharedServices** op om de tarief kaart gegevens te retour neren die de Azure-prijzen bevatten.</span><span class="sxs-lookup"><span data-stu-id="faec3-118">To obtain the Azure Card, execute the [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) command and specify the **SharedServices** parameter to return rate card details that contains the Azure prices.</span></span>

```powershell
Get-PartnerAzureRateCard -SharedServices
```

## <a name="rest-request"></a><span data-ttu-id="faec3-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="faec3-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="faec3-120">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="faec3-120">Request syntax</span></span>

| <span data-ttu-id="faec3-121">Methode</span><span class="sxs-lookup"><span data-stu-id="faec3-121">Method</span></span>  | <span data-ttu-id="faec3-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="faec3-122">Request URI</span></span>                                                               |
|---------|---------------------------------------------------------------------------|
| <span data-ttu-id="faec3-123">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="faec3-123">**GET**</span></span> | <span data-ttu-id="faec3-124">*{baseURL}*/v1/ratecards/Azure-Shared? Currency = {currency} &regio = {Region}</span><span class="sxs-lookup"><span data-stu-id="faec3-124">*{baseURL}*/v1/ratecards/azure-shared?currency={currency}&region={region}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="faec3-125">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="faec3-125">URI parameters</span></span>

| <span data-ttu-id="faec3-126">Naam</span><span class="sxs-lookup"><span data-stu-id="faec3-126">Name</span></span>     | <span data-ttu-id="faec3-127">Type</span><span class="sxs-lookup"><span data-stu-id="faec3-127">Type</span></span>   | <span data-ttu-id="faec3-128">Vereist</span><span class="sxs-lookup"><span data-stu-id="faec3-128">Required</span></span> | <span data-ttu-id="faec3-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="faec3-129">Description</span></span>                                                                                                                                                                               |
|----------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="faec3-130">currency</span><span class="sxs-lookup"><span data-stu-id="faec3-130">currency</span></span> | <span data-ttu-id="faec3-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="faec3-131">string</span></span> | <span data-ttu-id="faec3-132">No</span><span class="sxs-lookup"><span data-stu-id="faec3-132">No</span></span>       | <span data-ttu-id="faec3-133">Optionele ISO-code van drie letters voor de valuta waarin de resource tarieven worden gegeven (bijvoorbeeld `EUR` ).</span><span class="sxs-lookup"><span data-stu-id="faec3-133">Optional three letter ISO code for the currency in which the resource rates will be provided (for example `EUR`).</span></span> <span data-ttu-id="faec3-134">De standaard waarde is de valuta die is gekoppeld aan de markt in het Partner profiel.</span><span class="sxs-lookup"><span data-stu-id="faec3-134">The default is the currency associated with the market in the partner profile.</span></span> |
| <span data-ttu-id="faec3-135">regio</span><span class="sxs-lookup"><span data-stu-id="faec3-135">region</span></span>   | <span data-ttu-id="faec3-136">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="faec3-136">string</span></span> | <span data-ttu-id="faec3-137">No</span><span class="sxs-lookup"><span data-stu-id="faec3-137">No</span></span>       | <span data-ttu-id="faec3-138">Optionele ISO-land/regio code van twee letters waarmee de markt wordt aangegeven waar de aanbieding wordt gekocht (bijvoorbeeld `FR` ).</span><span class="sxs-lookup"><span data-stu-id="faec3-138">Optional two-letter ISO country/region code that indicates the market where the offer is purchased (for example `FR`).</span></span> <span data-ttu-id="faec3-139">De standaard waarde is de land/regio code die is ingesteld in het Partner profiel.</span><span class="sxs-lookup"><span data-stu-id="faec3-139">The default is the country/region code set in the partner profile.</span></span>        |

<span data-ttu-id="faec3-140">Als de optionele X-locale header is opgenomen in de aanvraag, bepaalt de waarde ervan de taal die wordt gebruikt voor de details in het antwoord.</span><span class="sxs-lookup"><span data-stu-id="faec3-140">If the optional X-Locale header is included in the request, its value determines the language used for the details in the response.</span></span>

### <a name="request-headers"></a><span data-ttu-id="faec3-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="faec3-141">Request headers</span></span>

<span data-ttu-id="faec3-142">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="faec3-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="faec3-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="faec3-143">Request body</span></span>

<span data-ttu-id="faec3-144">Geen.</span><span class="sxs-lookup"><span data-stu-id="faec3-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="faec3-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="faec3-145">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="faec3-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="faec3-146">REST response</span></span>

<span data-ttu-id="faec3-147">Als de aanvraag is voltooid, wordt een [Azure-tarieven](azure-rate-card-resources.md) resource geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="faec3-147">If the request is successful, it returns an [Azure Rate Card](azure-rate-card-resources.md) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="faec3-148">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="faec3-148">Response success and error codes</span></span>

<span data-ttu-id="faec3-149">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="faec3-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="faec3-150">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="faec3-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="faec3-151">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="faec3-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="faec3-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="faec3-152">Response example</span></span>

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
