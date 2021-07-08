---
title: Een MPN-id van een partner verifiëren
description: Leer hoe u de mpn-id (Microsoft Partner Network-id) van een partner kunt controleren door het MPN-profiel van de partner aan te vragen via C of de \# Partner Center REST API.
ms.date: 09/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6bd51850c7bc5a099a34f9c028a58e247c2600a3
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548818"
---
# <a name="verify-a-partner-mpn-id-via-c-or-the-partner-center-rest-api"></a><span data-ttu-id="b0f61-103">Controleer een MPN-id van een partner via C \# of de Partner Center REST API</span><span class="sxs-lookup"><span data-stu-id="b0f61-103">Verify a partner MPN ID via C\# or the Partner Center REST API</span></span>

<span data-ttu-id="b0f61-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b0f61-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b0f61-105">De ID van een partner controleren Microsoft Partner Network (MPN-id).</span><span class="sxs-lookup"><span data-stu-id="b0f61-105">How to verify a partner's Microsoft Partner Network identifier (MPN ID).</span></span>

<span data-ttu-id="b0f61-106">Met de hier weergegeven techniek wordt de id van de partner Microsoft Partner Network door het MPN-profiel van de partner aan te vragen bij het partnercentrum.</span><span class="sxs-lookup"><span data-stu-id="b0f61-106">The technique shown here verifies the partner's Microsoft Partner Network identifier by requesting the partner's MPN profile from partner center.</span></span> <span data-ttu-id="b0f61-107">De id wordt als geldig beschouwd als de aanvraag slaagt.</span><span class="sxs-lookup"><span data-stu-id="b0f61-107">The identifier is considered valid if the request succeeds.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b0f61-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b0f61-108">Prerequisites</span></span>

- <span data-ttu-id="b0f61-109">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b0f61-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b0f61-110">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="b0f61-110">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="b0f61-111">De MPN-id van de partner die moet worden geverifieerd.</span><span class="sxs-lookup"><span data-stu-id="b0f61-111">The partner MPN ID to verify.</span></span> <span data-ttu-id="b0f61-112">Als u deze waarde weglaten, haalt de aanvraag het MPN-profiel van de aangemelde partner op.</span><span class="sxs-lookup"><span data-stu-id="b0f61-112">If you omit this value, the request retrieves the MPN profile of the signed-in partner.</span></span>

## <a name="c"></a><span data-ttu-id="b0f61-113">C\#</span><span class="sxs-lookup"><span data-stu-id="b0f61-113">C\#</span></span>

<span data-ttu-id="b0f61-114">Als u de MPN-id van een partner wilt controleren, haalt u eerst een interface op voor verzamelingsbewerkingen van partnerprofielen van [**de eigenschap IAggregatePartner.Profiles.**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles)</span><span class="sxs-lookup"><span data-stu-id="b0f61-114">To verify a partner's MPN ID, first retrieve an interface to partner profile collection operations from the [**IAggregatePartner.Profiles**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles) property.</span></span> <span data-ttu-id="b0f61-115">Haal vervolgens een interface op voor MPN-profielbewerkingen van de [**eigenschap MpnProfile.**](/dotnet/api/microsoft.store.partnercenter.profiles.ipartnerprofilecollection.mpnprofile)</span><span class="sxs-lookup"><span data-stu-id="b0f61-115">Then get an interface to MPN profile operations from the [**MpnProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.ipartnerprofilecollection.mpnprofile) property.</span></span> <span data-ttu-id="b0f61-116">Roep ten slotte de [**methoden Get**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) met de MPN-id om het MPN-profiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="b0f61-116">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) methods with the MPN ID to retrieve the MPN profile.</span></span> <span data-ttu-id="b0f61-117">Als u de MPN-id weglaten uit de Get- of GetAsync-aanroep, probeert de aanvraag het MPN-profiel van de aangemelde partner op te halen.</span><span class="sxs-lookup"><span data-stu-id="b0f61-117">If you omit the MPN ID from the Get or GetAsync call, the request attempts to retrieve the MPN profile of the signed-in partner.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string partnerMpnId;

var partnerProfile = partnerOperations.Profiles.MpnProfile.Get(partnerMpnId);
```

<span data-ttu-id="b0f61-118">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="b0f61-118">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="b0f61-119">**Project:** Partnercentrum-SDK Klasse **Samples:** VerifyPartnerMpnId.cs</span><span class="sxs-lookup"><span data-stu-id="b0f61-119">**Project**: Partner Center SDK Samples **Class**: VerifyPartnerMpnId.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="b0f61-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="b0f61-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b0f61-121">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="b0f61-121">Request syntax</span></span>

| <span data-ttu-id="b0f61-122">Methode</span><span class="sxs-lookup"><span data-stu-id="b0f61-122">Method</span></span>  | <span data-ttu-id="b0f61-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="b0f61-123">Request URI</span></span>                                                                         |
|---------|-------------------------------------------------------------------------------------|
| <span data-ttu-id="b0f61-124">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="b0f61-124">**GET**</span></span> | <span data-ttu-id="b0f61-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/mpn?mpnId={mpn-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b0f61-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/mpn?mpnId={mpn-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="b0f61-126">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="b0f61-126">URI parameter</span></span>

<span data-ttu-id="b0f61-127">Geef de volgende queryparameter op om de partner te identificeren.</span><span class="sxs-lookup"><span data-stu-id="b0f61-127">Provide the following query parameter to identify the partner.</span></span> <span data-ttu-id="b0f61-128">Als u deze queryparameter weglaten, retourneert de aanvraag het MPN-profiel van de aangemelde partner.</span><span class="sxs-lookup"><span data-stu-id="b0f61-128">If you omit this query parameter, the request returns the MPN profile of the signed-in partner.</span></span>

| <span data-ttu-id="b0f61-129">Naam</span><span class="sxs-lookup"><span data-stu-id="b0f61-129">Name</span></span>   | <span data-ttu-id="b0f61-130">Type</span><span class="sxs-lookup"><span data-stu-id="b0f61-130">Type</span></span> | <span data-ttu-id="b0f61-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="b0f61-131">Required</span></span> | <span data-ttu-id="b0f61-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b0f61-132">Description</span></span>                                                 |
|--------|------|----------|-------------------------------------------------------------|
| <span data-ttu-id="b0f61-133">mpn-id</span><span class="sxs-lookup"><span data-stu-id="b0f61-133">mpn-id</span></span> | <span data-ttu-id="b0f61-134">int</span><span class="sxs-lookup"><span data-stu-id="b0f61-134">int</span></span>  | <span data-ttu-id="b0f61-135">Nee</span><span class="sxs-lookup"><span data-stu-id="b0f61-135">No</span></span>       | <span data-ttu-id="b0f61-136">Een Microsoft Partner Network-id die de partner identificeert.</span><span class="sxs-lookup"><span data-stu-id="b0f61-136">A Microsoft Partner Network ID that identifies the partner.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="b0f61-137">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="b0f61-137">Request headers</span></span>

<span data-ttu-id="b0f61-138">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="b0f61-138">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b0f61-139">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="b0f61-139">Request body</span></span>

<span data-ttu-id="b0f61-140">Geen.</span><span class="sxs-lookup"><span data-stu-id="b0f61-140">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b0f61-141">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b0f61-141">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/mpn?mpnId=9999999 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 560df6b9-6e53-4954-aed7-133477ac1194
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="b0f61-142">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="b0f61-142">REST response</span></span>

<span data-ttu-id="b0f61-143">Als dit lukt, bevat de antwoord-body de [MpnProfile-resource](profile-resources.md#mpnprofile) voor de partner.</span><span class="sxs-lookup"><span data-stu-id="b0f61-143">If successful, the response body contains the [MpnProfile](profile-resources.md#mpnprofile) resource for the partner.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b0f61-144">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="b0f61-144">Response success and error codes</span></span>

<span data-ttu-id="b0f61-145">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="b0f61-145">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b0f61-146">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="b0f61-146">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b0f61-147">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="b0f61-147">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example-success"></a><span data-ttu-id="b0f61-148">Voorbeeld van antwoord (geslaagd)</span><span class="sxs-lookup"><span data-stu-id="b0f61-148">Response example (success)</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 159
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
MS-RequestId: e39e0ddf-3fd0-4b7e-bb4e-8aebe242d3ee
MS-CV: s2GvkNgZsUSadxQX.0
MS-ServerId: 030011719
Date: Thu, 13 Apr 2017 18:13:40 GMT

{
    "mpnId": "4391507",
    "profileType": "MpnProfile",
    "links": {
        "self": {
            "uri": "/profiles/mpn",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "MpnProfile"
    }
}
```

### <a name="response-example-failure"></a><span data-ttu-id="b0f61-149">Voorbeeld van een reactie (fout)</span><span class="sxs-lookup"><span data-stu-id="b0f61-149">Response example (failure)</span></span>

```http
HTTP/1.1 404 Not Found
Content-Length: 124
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
MS-RequestId: 560df6b9-6e53-4954-aed7-133477ac1194
MS-CV: sLRFZMWm+EKuL47u.0
MS-ServerId: 102030524
Date: Thu, 13 Apr 2017 18:26:51 GMT

{
    "code": 3000,
    "description": "Partner Organization with partner_id 9999999 could not be found",
    "data": [],
    "source": "PartnerFD"
}
```
