---
title: Ondersteuningsprofiel ophalen
description: Hiermee wordt een object opgehaald dat het ondersteunings Profiel van een gebruiker vertegenwoordigt.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b8b0fa533aaba74418985ea02cbb13bd722cede2
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767530"
---
# <a name="get-support-profile"></a><span data-ttu-id="0aad3-103">Ondersteuningsprofiel ophalen</span><span class="sxs-lookup"><span data-stu-id="0aad3-103">Get support profile</span></span>

<span data-ttu-id="0aad3-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="0aad3-104">**Applies To**</span></span>

- <span data-ttu-id="0aad3-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="0aad3-105">Partner Center</span></span>
- <span data-ttu-id="0aad3-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="0aad3-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="0aad3-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="0aad3-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="0aad3-108">Hiermee wordt een object opgehaald dat het ondersteunings Profiel van een gebruiker vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="0aad3-108">Gets an object representing a user's support profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0aad3-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0aad3-109">Prerequisites</span></span>

- <span data-ttu-id="0aad3-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0aad3-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="0aad3-111">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="0aad3-111">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="0aad3-112">C\#</span><span class="sxs-lookup"><span data-stu-id="0aad3-112">C\#</span></span>

<span data-ttu-id="0aad3-113">Gebruik uw **IAggregatePartner. Profiles** -verzameling om uw ondersteunings profiel te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="0aad3-113">To get your support profile, use your **IAggregatePartner.Profiles** collection.</span></span> <span data-ttu-id="0aad3-114">Roep de eigenschap [**SupportProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) aan, gevolgd door de methoden [**Get ()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.getasync) .</span><span class="sxs-lookup"><span data-stu-id="0aad3-114">Call the [**SupportProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

SupportProfile supportProfile = partnerOperations.Profiles.SupportProfile.Get();
```

<span data-ttu-id="0aad3-115">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="0aad3-115">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="0aad3-116">**Project**: PartnerCenterSDK. FeaturesSamples- **klasse**: GetSupportProfile.cs</span><span class="sxs-lookup"><span data-stu-id="0aad3-116">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetSupportProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="0aad3-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="0aad3-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0aad3-118">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="0aad3-118">Request syntax</span></span>

| <span data-ttu-id="0aad3-119">Methode</span><span class="sxs-lookup"><span data-stu-id="0aad3-119">Method</span></span>  | <span data-ttu-id="0aad3-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="0aad3-120">Request URI</span></span>                                                              |
|---------|--------------------------------------------------------------------------|
| <span data-ttu-id="0aad3-121">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="0aad3-121">**GET**</span></span> | <span data-ttu-id="0aad3-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/Profiles/support http/1.1</span><span class="sxs-lookup"><span data-stu-id="0aad3-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/support HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="0aad3-123">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="0aad3-123">Request headers</span></span>

<span data-ttu-id="0aad3-124">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="0aad3-124">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="0aad3-125">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="0aad3-125">Request body</span></span>

<span data-ttu-id="0aad3-126">Geen.</span><span class="sxs-lookup"><span data-stu-id="0aad3-126">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="0aad3-127">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="0aad3-127">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/support HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 07029132-385d-416f-a9a6-df5e9e4c78d3
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
```

## <a name="rest-response"></a><span data-ttu-id="0aad3-128">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="0aad3-128">REST response</span></span>

<span data-ttu-id="0aad3-129">Als dit lukt, retourneert deze methode een **SupportProfile** -object in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="0aad3-129">If successful, this method returns a **SupportProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0aad3-130">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="0aad3-130">Response success and error codes</span></span>

<span data-ttu-id="0aad3-131">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="0aad3-131">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0aad3-132">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="0aad3-132">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0aad3-133">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="0aad3-133">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="0aad3-134">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="0aad3-134">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 502
Content-Type: application/json
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
MS-RequestId: 07029132-385d-416f-a9a6-df5e9e4c78d3
Date: Wed, 25 Nov 2015 07:16:17 GMT

{
    "email": "email@sample.com",
    "telephone": "4255555555",
    "website": "www.microsoft.com",
    "profileType": "support_profile",
    "links": {
        "self": {
            "uri": "/v1/profiles/support",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "PartnerSupportProfile"
    }
}
```
