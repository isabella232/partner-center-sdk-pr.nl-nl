---
title: Een MPN-id van een partner verifiëren
description: Lees hoe u de Microsoft Partner Network-ID van een partner (MPN-ID) kunt controleren door het MPN-Profiel van de partner via C \# of het Partner Center-rest API aan te vragen.
ms.date: 09/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6ef7bcb35274a6bcbaddbe0553ca0cb4dc1b2f9c
ms.sourcegitcommit: 8a5c37376a29e29fe0002a980082d4acc6b91131
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/11/2020
ms.locfileid: "97767574"
---
# <a name="verify-a-partner-mpn-id-via-c-or-the-partner-center-rest-api"></a><span data-ttu-id="139c0-103">Een partner MPN-ID verifiëren via C \# of het Partner Center rest API</span><span class="sxs-lookup"><span data-stu-id="139c0-103">Verify a partner MPN ID via C\# or the Partner Center REST API</span></span>

<span data-ttu-id="139c0-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="139c0-104">**Applies To**</span></span>

- <span data-ttu-id="139c0-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="139c0-105">Partner Center</span></span>
- <span data-ttu-id="139c0-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="139c0-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="139c0-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="139c0-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="139c0-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="139c0-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="139c0-109">De Microsoft Partner Network-ID van een partner controleren (MPN-ID).</span><span class="sxs-lookup"><span data-stu-id="139c0-109">How to verify a partner's Microsoft Partner Network identifier (MPN ID).</span></span>

<span data-ttu-id="139c0-110">De hier weer gegeven methode verifieert de Microsoft Partner Network-ID van de partner door het MPN-Profiel van de partner aan te vragen bij het partner centrum.</span><span class="sxs-lookup"><span data-stu-id="139c0-110">The technique shown here verifies the partner's Microsoft Partner Network identifier by requesting the partner's MPN profile from partner center.</span></span> <span data-ttu-id="139c0-111">De id wordt als geldig beschouwd als de aanvraag slaagt.</span><span class="sxs-lookup"><span data-stu-id="139c0-111">The identifier is considered valid if the request succeeds.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="139c0-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="139c0-112">Prerequisites</span></span>

- <span data-ttu-id="139c0-113">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="139c0-113">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="139c0-114">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="139c0-114">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="139c0-115">De MPN-ID van de partner die moet worden geverifieerd.</span><span class="sxs-lookup"><span data-stu-id="139c0-115">The partner MPN ID to verify.</span></span> <span data-ttu-id="139c0-116">Als u deze waarde weglaat, wordt door de aanvraag het MPN-Profiel van de aangemelde partner opgehaald.</span><span class="sxs-lookup"><span data-stu-id="139c0-116">If you omit this value, the request retrieves the MPN profile of the signed-in partner.</span></span>

## <a name="c"></a><span data-ttu-id="139c0-117">C\#</span><span class="sxs-lookup"><span data-stu-id="139c0-117">C\#</span></span>

<span data-ttu-id="139c0-118">Als u de MPN-ID van een partner wilt verifiëren, moet u eerst een interface voor het verzamelen van partner profielen ophalen uit de eigenschap [**IAggregatePartner. Profiles**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles) .</span><span class="sxs-lookup"><span data-stu-id="139c0-118">To verify a partner's MPN ID, first retrieve an interface to partner profile collection operations from the [**IAggregatePartner.Profiles**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles) property.</span></span> <span data-ttu-id="139c0-119">Vervolgens krijgt u een interface voor het MPN van profiel bewerkingen van de eigenschap [**MpnProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.ipartnerprofilecollection.mpnprofile) .</span><span class="sxs-lookup"><span data-stu-id="139c0-119">Then get an interface to MPN profile operations from the [**MpnProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.ipartnerprofilecollection.mpnprofile) property.</span></span> <span data-ttu-id="139c0-120">Roep ten slotte de methoden [**Get**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) aan met de MPN-ID om het MPN-profiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="139c0-120">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) methods with the MPN ID to retrieve the MPN profile.</span></span> <span data-ttu-id="139c0-121">Als u de MPN-ID van de aanroep Get of GetAsync weglaat, probeert de aanvraag het MPN-Profiel van de aangemelde partner op te halen.</span><span class="sxs-lookup"><span data-stu-id="139c0-121">If you omit the MPN ID from the Get or GetAsync call, the request attempts to retrieve the MPN profile of the signed-in partner.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string partnerMpnId;

var partnerProfile = partnerOperations.Profiles.MpnProfile.Get(partnerMpnId);
```

<span data-ttu-id="139c0-122">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="139c0-122">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="139c0-123">**Project**: Partner Center SDK-voor beelden **klasse**: VerifyPartnerMpnId.cs</span><span class="sxs-lookup"><span data-stu-id="139c0-123">**Project**: Partner Center SDK Samples **Class**: VerifyPartnerMpnId.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="139c0-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="139c0-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="139c0-125">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="139c0-125">Request syntax</span></span>

| <span data-ttu-id="139c0-126">Methode</span><span class="sxs-lookup"><span data-stu-id="139c0-126">Method</span></span>  | <span data-ttu-id="139c0-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="139c0-127">Request URI</span></span>                                                                         |
|---------|-------------------------------------------------------------------------------------|
| <span data-ttu-id="139c0-128">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="139c0-128">**GET**</span></span> | <span data-ttu-id="139c0-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/Profiles/MPN? mpnId = {MPN-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="139c0-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/mpn?mpnId={mpn-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="139c0-130">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="139c0-130">URI parameter</span></span>

<span data-ttu-id="139c0-131">Geef de volgende query parameter op om de partner te identificeren.</span><span class="sxs-lookup"><span data-stu-id="139c0-131">Provide the following query parameter to identify the partner.</span></span> <span data-ttu-id="139c0-132">Als u deze query parameter weglaat, retourneert de aanvraag het MPN-Profiel van de aangemelde partner.</span><span class="sxs-lookup"><span data-stu-id="139c0-132">If you omit this query parameter, the request returns the MPN profile of the signed-in partner.</span></span>

| <span data-ttu-id="139c0-133">Naam</span><span class="sxs-lookup"><span data-stu-id="139c0-133">Name</span></span>   | <span data-ttu-id="139c0-134">Type</span><span class="sxs-lookup"><span data-stu-id="139c0-134">Type</span></span> | <span data-ttu-id="139c0-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="139c0-135">Required</span></span> | <span data-ttu-id="139c0-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="139c0-136">Description</span></span>                                                 |
|--------|------|----------|-------------------------------------------------------------|
| <span data-ttu-id="139c0-137">MPN-id</span><span class="sxs-lookup"><span data-stu-id="139c0-137">mpn-id</span></span> | <span data-ttu-id="139c0-138">int</span><span class="sxs-lookup"><span data-stu-id="139c0-138">int</span></span>  | <span data-ttu-id="139c0-139">No</span><span class="sxs-lookup"><span data-stu-id="139c0-139">No</span></span>       | <span data-ttu-id="139c0-140">Een Microsoft Partner Network-ID waarmee de partner wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="139c0-140">A Microsoft Partner Network ID that identifies the partner.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="139c0-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="139c0-141">Request headers</span></span>

<span data-ttu-id="139c0-142">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="139c0-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="139c0-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="139c0-143">Request body</span></span>

<span data-ttu-id="139c0-144">Geen.</span><span class="sxs-lookup"><span data-stu-id="139c0-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="139c0-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="139c0-145">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="139c0-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="139c0-146">REST response</span></span>

<span data-ttu-id="139c0-147">Als dit lukt, bevat de antwoord tekst de [MpnProfile](profile-resources.md#mpnprofile) -resource voor de partner.</span><span class="sxs-lookup"><span data-stu-id="139c0-147">If successful, the response body contains the [MpnProfile](profile-resources.md#mpnprofile) resource for the partner.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="139c0-148">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="139c0-148">Response success and error codes</span></span>

<span data-ttu-id="139c0-149">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="139c0-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="139c0-150">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="139c0-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="139c0-151">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="139c0-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example-success"></a><span data-ttu-id="139c0-152">Voor beeld van antwoord (geslaagd)</span><span class="sxs-lookup"><span data-stu-id="139c0-152">Response example (success)</span></span>

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

### <a name="response-example-failure"></a><span data-ttu-id="139c0-153">Voor beeld van antwoord (fout)</span><span class="sxs-lookup"><span data-stu-id="139c0-153">Response example (failure)</span></span>

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
