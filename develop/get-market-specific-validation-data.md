---
title: De regels voor adresopmaak per markt ophalen
description: Haal de verwachte adres notatie op op basis van de ISO-code voor de markt.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c755a38c11ed9803edb7777a0f661c1fbc5a6107
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767263"
---
# <a name="get-address-formatting-rules-by-market"></a><span data-ttu-id="b42a9-103">De regels voor adresopmaak per markt ophalen</span><span class="sxs-lookup"><span data-stu-id="b42a9-103">Get address formatting rules by market</span></span>

<span data-ttu-id="b42a9-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="b42a9-104">**Applies To**</span></span>

- <span data-ttu-id="b42a9-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="b42a9-105">Partner Center</span></span>
- <span data-ttu-id="b42a9-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="b42a9-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="b42a9-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="b42a9-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="b42a9-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b42a9-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b42a9-109">Haal de verwachte adres notatie op op basis van de ISO-code voor de markt.</span><span class="sxs-lookup"><span data-stu-id="b42a9-109">Get the expected address format based on the iso code for the market.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b42a9-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b42a9-110">Prerequisites</span></span>

- <span data-ttu-id="b42a9-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b42a9-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b42a9-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="b42a9-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="b42a9-113">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="b42a9-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b42a9-114">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b42a9-114">Request syntax</span></span>

| <span data-ttu-id="b42a9-115">Methode</span><span class="sxs-lookup"><span data-stu-id="b42a9-115">Method</span></span>  | <span data-ttu-id="b42a9-116">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="b42a9-116">Request URI</span></span>                                                                                 |
|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="b42a9-117">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="b42a9-117">**GET**</span></span> | <span data-ttu-id="b42a9-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/countryvalidationrules/{isocode-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="b42a9-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/countryvalidationrules/{isocode-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="b42a9-119">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="b42a9-119">URI parameter</span></span>

| <span data-ttu-id="b42a9-120">Naam</span><span class="sxs-lookup"><span data-stu-id="b42a9-120">Name</span></span>           | <span data-ttu-id="b42a9-121">Type</span><span class="sxs-lookup"><span data-stu-id="b42a9-121">Type</span></span>       | <span data-ttu-id="b42a9-122">Vereist</span><span class="sxs-lookup"><span data-stu-id="b42a9-122">Required</span></span> | <span data-ttu-id="b42a9-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b42a9-123">Description</span></span>                         |
|----------------|------------|----------|-------------------------------------|
| <span data-ttu-id="b42a9-124">**isocode-id**</span><span class="sxs-lookup"><span data-stu-id="b42a9-124">**isocode-id**</span></span> | <span data-ttu-id="b42a9-125">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="b42a9-125">**string**</span></span> | <span data-ttu-id="b42a9-126">J</span><span class="sxs-lookup"><span data-stu-id="b42a9-126">Y</span></span>        | <span data-ttu-id="b42a9-127">De ISO-land code van twee tekens.</span><span class="sxs-lookup"><span data-stu-id="b42a9-127">The two-character ISO country code.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="b42a9-128">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="b42a9-128">Request headers</span></span>

<span data-ttu-id="b42a9-129">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b42a9-129">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b42a9-130">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="b42a9-130">Request body</span></span>

<span data-ttu-id="b42a9-131">Geen.</span><span class="sxs-lookup"><span data-stu-id="b42a9-131">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b42a9-132">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b42a9-132">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/countryvalidationrules/{isocode-id} HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 124b0e41-a093-4fec-b871-3eeb45fd734b
MS-CorrelationId: 5cfd634d-b936-47af-87f0-0f0217425dcc
```

## <a name="rest-response"></a><span data-ttu-id="b42a9-133">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="b42a9-133">REST response</span></span>

<span data-ttu-id="b42a9-134">Als dit lukt, retourneert deze methode een **CountryInformation** -object in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="b42a9-134">If successful, this method returns a **CountryInformation** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b42a9-135">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="b42a9-135">Response success and error codes</span></span>

<span data-ttu-id="b42a9-136">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="b42a9-136">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b42a9-137">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="b42a9-137">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b42a9-138">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="b42a9-138">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b42a9-139">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="b42a9-139">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1856
Content-Type: application/json
MS-CorrelationId: 5cfd634d-b936-47af-87f0-0f0217425dcc
MS-RequestId: 124b0e41-a093-4fec-b871-3eeb45fd734b
Date: Wed, 25 Nov 2015 06:36:47 GMT

{
    "iso2Code": "US",
    "defaultCulture": "en-US",
    "isStateRequired": true,
    "states": {
        "value": ["AK","AL","AR", "AZ","CA","CO","CT","DC","DE","FL","GA","HI","IA","ID","IL","IN",
        "KS","KY","LA","MA","MD","ME","MI","MN","MO","MS","MT","NC","ND","NE","NH","NJ","NM","NV",
        "NY","OH","OK","OR","PA","RI","SC","SD","TN","TX","UT","VA","VT","WA","WI","WV","WY"]
    },
    "supportedLanguages": {
        "value": ["en",
        "es"]
    },
    "supportedCultures": {
        "value": ["en-US",
        "es-US"]
    },
    "isPostalCodeRequired": true,
    "postalCodeRegex": "^\\d{
        5
    }(-\\d{
        4
    })?$",
    "isCityRequired": true,
    "isVatIdSupported": false,
    "taxIdFormat": "US######",
    "taxIdSample": "US999965",
    "phoneNumberRegex": "^(1[\\-\\/\\.]?)?(\((\\d{3})\)|(\\d{3}))[\\-\\/\\.]?(\\d{3})[\\-\\/\\.]?(\\d{4})$",
    "isRegistrationNumberSupported": false,
    "isTaxIdSupported": true,
    "resellerAgreementRegion": "AOC",
    "geographicRegion": "NorthAndLatinAmerica",
    "countryCallingCodes": {
        "value": ["1"]
    },
    "attributes": {
        "objectType": "CountryInformation"
    }
}
```
