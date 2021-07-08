---
title: De regels voor adresopmaak per markt ophalen
description: Haal de verwachte adresindeling op op basis van de ISO-code voor de markt.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d5233d059ea6e71c28df36b2242659c28c5dd857
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549039"
---
# <a name="get-address-formatting-rules-by-market"></a><span data-ttu-id="dfffb-103">De regels voor adresopmaak per markt ophalen</span><span class="sxs-lookup"><span data-stu-id="dfffb-103">Get address formatting rules by market</span></span>

<span data-ttu-id="dfffb-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="dfffb-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>


<span data-ttu-id="dfffb-105">Haal de verwachte adresindeling op op basis van de ISO-code voor de markt.</span><span class="sxs-lookup"><span data-stu-id="dfffb-105">Get the expected address format based on the iso code for the market.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dfffb-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="dfffb-106">Prerequisites</span></span>

- <span data-ttu-id="dfffb-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="dfffb-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="dfffb-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="dfffb-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="dfffb-109">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="dfffb-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="dfffb-110">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="dfffb-110">Request syntax</span></span>

| <span data-ttu-id="dfffb-111">Methode</span><span class="sxs-lookup"><span data-stu-id="dfffb-111">Method</span></span>  | <span data-ttu-id="dfffb-112">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="dfffb-112">Request URI</span></span>                                                                                 |
|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="dfffb-113">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="dfffb-113">**GET**</span></span> | <span data-ttu-id="dfffb-114">[*{baseURL}*](partner-center-rest-urls.md)/v1/countryvalidationrules/{isocode-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="dfffb-114">[*{baseURL}*](partner-center-rest-urls.md)/v1/countryvalidationrules/{isocode-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="dfffb-115">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="dfffb-115">URI parameter</span></span>

| <span data-ttu-id="dfffb-116">Naam</span><span class="sxs-lookup"><span data-stu-id="dfffb-116">Name</span></span>           | <span data-ttu-id="dfffb-117">Type</span><span class="sxs-lookup"><span data-stu-id="dfffb-117">Type</span></span>       | <span data-ttu-id="dfffb-118">Vereist</span><span class="sxs-lookup"><span data-stu-id="dfffb-118">Required</span></span> | <span data-ttu-id="dfffb-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dfffb-119">Description</span></span>                         |
|----------------|------------|----------|-------------------------------------|
| <span data-ttu-id="dfffb-120">**isocode-id**</span><span class="sxs-lookup"><span data-stu-id="dfffb-120">**isocode-id**</span></span> | <span data-ttu-id="dfffb-121">**tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="dfffb-121">**string**</span></span> | <span data-ttu-id="dfffb-122">J</span><span class="sxs-lookup"><span data-stu-id="dfffb-122">Y</span></span>        | <span data-ttu-id="dfffb-123">De ISO-landcode van twee tekens.</span><span class="sxs-lookup"><span data-stu-id="dfffb-123">The two-character ISO country code.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="dfffb-124">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="dfffb-124">Request headers</span></span>

<span data-ttu-id="dfffb-125">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="dfffb-125">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="dfffb-126">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="dfffb-126">Request body</span></span>

<span data-ttu-id="dfffb-127">Geen.</span><span class="sxs-lookup"><span data-stu-id="dfffb-127">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="dfffb-128">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="dfffb-128">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/countryvalidationrules/{isocode-id} HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 124b0e41-a093-4fec-b871-3eeb45fd734b
MS-CorrelationId: 5cfd634d-b936-47af-87f0-0f0217425dcc
```

## <a name="rest-response"></a><span data-ttu-id="dfffb-129">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="dfffb-129">REST response</span></span>

<span data-ttu-id="dfffb-130">Als dit lukt, retourneert deze methode een **CountryInformation-object** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="dfffb-130">If successful, this method returns a **CountryInformation** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="dfffb-131">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="dfffb-131">Response success and error codes</span></span>

<span data-ttu-id="dfffb-132">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="dfffb-132">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="dfffb-133">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="dfffb-133">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="dfffb-134">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="dfffb-134">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="dfffb-135">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="dfffb-135">Response example</span></span>

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
