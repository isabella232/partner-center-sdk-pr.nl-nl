---
title: Het wettelijke bedrijfsprofiel van een partner ophalen
description: Het juridische zakelijke profiel van een partner ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 5d7055dd0a6586e16b078109db4252250561eb29
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767543"
---
# <a name="get-the-partner-legal-business-profile"></a><span data-ttu-id="9f625-103">Het wettelijke bedrijfsprofiel van een partner ophalen</span><span class="sxs-lookup"><span data-stu-id="9f625-103">Get the partner legal business profile</span></span>

<span data-ttu-id="9f625-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="9f625-104">**Applies To**</span></span>

- <span data-ttu-id="9f625-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="9f625-105">Partner Center</span></span>
- <span data-ttu-id="9f625-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="9f625-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="9f625-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="9f625-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="9f625-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="9f625-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="9f625-109">Het juridische zakelijke profiel van een partner ophalen.</span><span class="sxs-lookup"><span data-stu-id="9f625-109">How to get a partner's legal business profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9f625-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9f625-110">Prerequisites</span></span>

- <span data-ttu-id="9f625-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9f625-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9f625-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="9f625-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="9f625-113">C\#</span><span class="sxs-lookup"><span data-stu-id="9f625-113">C\#</span></span>

<span data-ttu-id="9f625-114">Als u het partner juridisch Business-profiel wilt ophalen, moet u eerst een interface ophalen voor de verzameling van partner profiel bewerkingen van de eigenschap **IAggregatePartner. Profiles** .</span><span class="sxs-lookup"><span data-stu-id="9f625-114">To get the partner legal business profile, first get an interface to the collection of partner profile operations from the **IAggregatePartner.Profiles** property.</span></span> <span data-ttu-id="9f625-115">Haal vervolgens de waarde van de eigenschap **LegalBusinessProfile** op om een interface op te halen voor juridische bedrijfs profiel bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="9f625-115">Then, get the value of the **LegalBusinessProfile** property to retrieve an interface to legal business profile operations.</span></span> <span data-ttu-id="9f625-116">Roep ten slotte de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.getasync) aan om het profiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="9f625-116">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.get) or the [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.getasync) method to retrieve the profile.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var billingProfile = partnerOperations.Profiles.LegalBusinessProfile.Get();
```

<span data-ttu-id="9f625-117">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="9f625-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="9f625-118">**Project**: Partner Center SDK-voor beelden **klasse**: GetLegalBusinessProfile.cs</span><span class="sxs-lookup"><span data-stu-id="9f625-118">**Project**: Partner Center SDK Samples **Class**: GetLegalBusinessProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="9f625-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="9f625-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9f625-120">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9f625-120">Request syntax</span></span>

| <span data-ttu-id="9f625-121">Methode</span><span class="sxs-lookup"><span data-stu-id="9f625-121">Method</span></span>  | <span data-ttu-id="9f625-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="9f625-122">Request URI</span></span>                                                                    |
|---------|--------------------------------------------------------------------------------|
| <span data-ttu-id="9f625-123">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="9f625-123">**GET**</span></span> | <span data-ttu-id="9f625-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/Profiles/legalbusiness http/1.1</span><span class="sxs-lookup"><span data-stu-id="9f625-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/legalbusiness HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9f625-125">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="9f625-125">Request headers</span></span>

<span data-ttu-id="9f625-126">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="9f625-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9f625-127">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="9f625-127">Request body</span></span>

<span data-ttu-id="9f625-128">Geen.</span><span class="sxs-lookup"><span data-stu-id="9f625-128">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="9f625-129">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9f625-129">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/legalbusiness?vettingVersion=Current HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 7391249f-cba0-467c-b026-7b3a60196422
MS-CorrelationId: 98a091a0-67db-4eeb-ae0d-7e8b2e39c1d2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="9f625-130">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="9f625-130">REST response</span></span>

<span data-ttu-id="9f625-131">Als dit lukt, retourneert deze methode een **LegalBusinessProfile** -object in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="9f625-131">If successful, this method returns a **LegalBusinessProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9f625-132">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="9f625-132">Response success and error codes</span></span>

<span data-ttu-id="9f625-133">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="9f625-133">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9f625-134">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="9f625-134">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9f625-135">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="9f625-135">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9f625-136">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="9f625-136">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1151
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 98a091a0-67db-4eeb-ae0d-7e8b2e39c1d2
MS-RequestId: 7391249f-cba0-467c-b026-7b3a60196422
MS-CV: MEgCpJUoGUeXG+4a.0
MS-ServerId: 030011719
Date: Tue, 21 Mar 2017 17:29:52 GMT

{
    "companyName": "Lucerne Publishing",
    "address": {
        "country": "US",
        "city": "Buffalo",
        "state": "NY",
        "addressLine1": "123 Main Street",
        "addressLine2": "",
        "postalCode": "98052",
        "firstName": "Gena",
        "lastName": "Soto",
        "phoneNumber": "4255550100"
    },
    "primaryContact": {
        "firstName": "Gena",
        "lastName": "Soto",
        "email": "gena@lucernepublishing.com",
        "phoneNumber": "4255550100"
    },
    "companyApproverAddress": {
        "country": "US",
        "city": "Buffalo",
        "state": "NY",
        "addressLine1": "123 Main Street",
        "addressLine2": "",
        "postalCode": "98052"
    },
    "companyApproverEmail": "gena@lucernepublishing.com",
    "vettingStatus": "authorized",
    "vettingSubStatus": "none",
    "profileType": "LegalBusinessProfile",
    "links": {
        "self": {
            "uri": "/profiles/legalbusiness",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "LegalBusinessProfile"
    }
}
```
