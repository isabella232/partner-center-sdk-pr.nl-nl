---
title: Het wettelijke bedrijfsprofiel van een partner ophalen
description: Meer informatie over het gebruik van API's om uw juridische bedrijfsprofiel op te halen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ba0654e364674bc2db129a0904d411c6fb67cbb9
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549056"
---
# <a name="get-the-partner-legal-business-profile"></a><span data-ttu-id="22765-103">Het wettelijke bedrijfsprofiel van een partner ophalen</span><span class="sxs-lookup"><span data-stu-id="22765-103">Get the partner legal business profile</span></span>

<span data-ttu-id="22765-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="22765-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="22765-105">Het juridische bedrijfsprofiel van een partner op te halen.</span><span class="sxs-lookup"><span data-stu-id="22765-105">How to get a partner's legal business profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22765-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="22765-106">Prerequisites</span></span>

- <span data-ttu-id="22765-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="22765-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="22765-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="22765-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="22765-109">C\#</span><span class="sxs-lookup"><span data-stu-id="22765-109">C\#</span></span>

<span data-ttu-id="22765-110">Als u het juridische bedrijfsprofiel van de partner wilt ophalen, moet u eerst een interface ophalen voor de verzameling partnerprofielbewerkingen van de **eigenschap IAggregatePartner.Profiles.**</span><span class="sxs-lookup"><span data-stu-id="22765-110">To get the partner legal business profile, first get an interface to the collection of partner profile operations from the **IAggregatePartner.Profiles** property.</span></span> <span data-ttu-id="22765-111">Haal vervolgens de waarde van de eigenschap **LegalBusinessProfile** op om een interface op te halen voor juridische bedrijfsprofielbewerkingen.</span><span class="sxs-lookup"><span data-stu-id="22765-111">Then, get the value of the **LegalBusinessProfile** property to retrieve an interface to legal business profile operations.</span></span> <span data-ttu-id="22765-112">Roep ten slotte de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.get) of [**getAsync aan**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.getasync) om het profiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="22765-112">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.get) or the [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.getasync) method to retrieve the profile.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var billingProfile = partnerOperations.Profiles.LegalBusinessProfile.Get();
```

<span data-ttu-id="22765-113">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="22765-113">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="22765-114">**Project**: Partnercentrum-SDK Samples **Class**: GetLegalBusinessProfile.cs</span><span class="sxs-lookup"><span data-stu-id="22765-114">**Project**: Partner Center SDK Samples **Class**: GetLegalBusinessProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="22765-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="22765-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="22765-116">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="22765-116">Request syntax</span></span>

| <span data-ttu-id="22765-117">Methode</span><span class="sxs-lookup"><span data-stu-id="22765-117">Method</span></span>  | <span data-ttu-id="22765-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="22765-118">Request URI</span></span>                                                                    |
|---------|--------------------------------------------------------------------------------|
| <span data-ttu-id="22765-119">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="22765-119">**GET**</span></span> | <span data-ttu-id="22765-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/legalbusiness HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="22765-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/legalbusiness HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="22765-121">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="22765-121">Request headers</span></span>

<span data-ttu-id="22765-122">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="22765-122">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="22765-123">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="22765-123">Request body</span></span>

<span data-ttu-id="22765-124">Geen.</span><span class="sxs-lookup"><span data-stu-id="22765-124">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="22765-125">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="22765-125">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="22765-126">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="22765-126">REST response</span></span>

<span data-ttu-id="22765-127">Als dit lukt, retourneert deze methode **een LegalBusinessProfile-object** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="22765-127">If successful, this method returns a **LegalBusinessProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="22765-128">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="22765-128">Response success and error codes</span></span>

<span data-ttu-id="22765-129">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="22765-129">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="22765-130">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="22765-130">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="22765-131">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="22765-131">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="22765-132">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="22765-132">Response example</span></span>

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
