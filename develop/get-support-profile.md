---
title: Ondersteuningsprofiel ophalen
description: Haalt een -object op dat het ondersteuningsprofiel van een gebruiker vertegenwoordigt.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b112ccbbff731795c21f95845a08be9e9dfb6775
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548631"
---
# <a name="get-support-profile"></a><span data-ttu-id="c1fbb-103">Ondersteuningsprofiel ophalen</span><span class="sxs-lookup"><span data-stu-id="c1fbb-103">Get support profile</span></span>

<span data-ttu-id="c1fbb-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c1fbb-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c1fbb-105">Haalt een -object op dat het ondersteuningsprofiel van een gebruiker vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c1fbb-105">Gets an object representing a user's support profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c1fbb-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c1fbb-106">Prerequisites</span></span>

- <span data-ttu-id="c1fbb-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c1fbb-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c1fbb-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="c1fbb-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="c1fbb-109">C\#</span><span class="sxs-lookup"><span data-stu-id="c1fbb-109">C\#</span></span>

<span data-ttu-id="c1fbb-110">Gebruik de verzameling **IAggregatePartner.Profiles** om uw ondersteuningsprofiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="c1fbb-110">To get your support profile, use your **IAggregatePartner.Profiles** collection.</span></span> <span data-ttu-id="c1fbb-111">Roep de [**eigenschap SupportProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) aan, gevolgd door de [**methoden Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.get) of [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.getasync)</span><span class="sxs-lookup"><span data-stu-id="c1fbb-111">Call the [**SupportProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

SupportProfile supportProfile = partnerOperations.Profiles.SupportProfile.Get();
```

<span data-ttu-id="c1fbb-112">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="c1fbb-112">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="c1fbb-113">**Project:** PartnerCenterSDK.FeaturesSamples-klasse: GetSupportProfile.cs </span><span class="sxs-lookup"><span data-stu-id="c1fbb-113">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetSupportProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="c1fbb-114">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c1fbb-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c1fbb-115">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="c1fbb-115">Request syntax</span></span>

| <span data-ttu-id="c1fbb-116">Methode</span><span class="sxs-lookup"><span data-stu-id="c1fbb-116">Method</span></span>  | <span data-ttu-id="c1fbb-117">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c1fbb-117">Request URI</span></span>                                                              |
|---------|--------------------------------------------------------------------------|
| <span data-ttu-id="c1fbb-118">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="c1fbb-118">**GET**</span></span> | <span data-ttu-id="c1fbb-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/support HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c1fbb-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/support HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c1fbb-120">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c1fbb-120">Request headers</span></span>

<span data-ttu-id="c1fbb-121">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="c1fbb-121">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c1fbb-122">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c1fbb-122">Request body</span></span>

<span data-ttu-id="c1fbb-123">Geen.</span><span class="sxs-lookup"><span data-stu-id="c1fbb-123">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c1fbb-124">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c1fbb-124">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/support HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 07029132-385d-416f-a9a6-df5e9e4c78d3
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
```

## <a name="rest-response"></a><span data-ttu-id="c1fbb-125">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c1fbb-125">REST response</span></span>

<span data-ttu-id="c1fbb-126">Als dit lukt, retourneert deze methode een **SupportProfile-object** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="c1fbb-126">If successful, this method returns a **SupportProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c1fbb-127">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="c1fbb-127">Response success and error codes</span></span>

<span data-ttu-id="c1fbb-128">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="c1fbb-128">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c1fbb-129">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c1fbb-129">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c1fbb-130">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="c1fbb-130">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c1fbb-131">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="c1fbb-131">Response example</span></span>

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
