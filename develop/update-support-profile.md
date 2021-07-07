---
title: Ondersteuningsprofiel bijwerken
description: Werkt het ondersteuningsprofiel van een gebruiker bij.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 143328c5501f525d52911eead805d420f79b78ff
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530341"
---
# <a name="update-support-profile"></a><span data-ttu-id="ddbda-103">Ondersteuningsprofiel bijwerken</span><span class="sxs-lookup"><span data-stu-id="ddbda-103">Update support profile</span></span>

<span data-ttu-id="ddbda-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="ddbda-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="ddbda-105">Werkt het ondersteuningsprofiel van een gebruiker bij.</span><span class="sxs-lookup"><span data-stu-id="ddbda-105">Updates a user's support profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ddbda-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ddbda-106">Prerequisites</span></span>

- <span data-ttu-id="ddbda-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ddbda-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ddbda-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="ddbda-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="ddbda-109">C\#</span><span class="sxs-lookup"><span data-stu-id="ddbda-109">C\#</span></span>

<span data-ttu-id="ddbda-110">Als u uw ondersteuningsprofiel wilt bijwerken, [moet u eerst uw ondersteuningsprofiel op](get-support-profile.md) halen en eventuele wijzigingen aanbrengen.</span><span class="sxs-lookup"><span data-stu-id="ddbda-110">To update your support profile, first [get your support profile](get-support-profile.md) and make any changes you wish.</span></span> <span data-ttu-id="ddbda-111">Gebruik vervolgens de [**verzameling IPartnerOperations.Profiles.**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles)</span><span class="sxs-lookup"><span data-stu-id="ddbda-111">Then, use your [**IPartnerOperations.Profiles**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles) collection.</span></span> <span data-ttu-id="ddbda-112">Roep de [**eigenschap SupportProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) aan, gevolgd door de [**methode Update()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.update) of [**UpdateAsync().**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.updateasync)</span><span class="sxs-lookup"><span data-stu-id="ddbda-112">Call the [**SupportProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) property, followed by the [**Update()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.update) or [**UpdateAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.updateasync) method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

// updated profile
SupportProfile newSupportProfile = new SupportProfile
{
   Email = supportProfile.Email,
   Website = supportProfile.Website,
   Telephone = new Random().Next(10000000, 99999999).ToString(CultureInfo.InvariantCulture)
};

SupportProfile updatedSupportProfile = partnerOperations.Profiles.SupportProfile.Update(newSupportProfile);
```

<span data-ttu-id="ddbda-113">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="ddbda-113">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="ddbda-114">**Project:** PartnerCenterSDK.FeaturesSamples-klasse: UpdateSupportProfile.cs </span><span class="sxs-lookup"><span data-stu-id="ddbda-114">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: UpdateSupportProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="ddbda-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="ddbda-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ddbda-116">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="ddbda-116">Request syntax</span></span>

| <span data-ttu-id="ddbda-117">Methode</span><span class="sxs-lookup"><span data-stu-id="ddbda-117">Method</span></span>  | <span data-ttu-id="ddbda-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="ddbda-118">Request URI</span></span>                                                                     |
|---------|---------------------------------------------------------------------------------|
| <span data-ttu-id="ddbda-119">**PUT**</span><span class="sxs-lookup"><span data-stu-id="ddbda-119">**PUT**</span></span> | <span data-ttu-id="ddbda-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/supportprofile HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ddbda-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/supportprofile HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ddbda-121">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ddbda-121">Request headers</span></span>

<span data-ttu-id="ddbda-122">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="ddbda-122">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ddbda-123">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="ddbda-123">Request body</span></span>

<span data-ttu-id="ddbda-124">De volledige ondersteuningsprofielresource.</span><span class="sxs-lookup"><span data-stu-id="ddbda-124">The full support profile resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="ddbda-125">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ddbda-125">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/profiles/supportprofile HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 603f3cd9-01b8-48f2-b65d-855a246f5bfd
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
Content-Type: application/json
Content-Length: 167
Expect: 100-continue

{
    "Email": "email@sample.com",
    "Telephone": "4255555555",
    "Website": "www.microsoft.com",
    "ProfileType": "support_profile",
    "Attributes": {
        "ObjectType": "PartnerSupportProfile"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="ddbda-126">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="ddbda-126">REST response</span></span>

<span data-ttu-id="ddbda-127">Als dit lukt, retourneert deze methode **bijgewerkte SupportProfile-objecteigenschappen** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="ddbda-127">If successful, this method returns updated **SupportProfile** object properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ddbda-128">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="ddbda-128">Response success and error codes</span></span>

<span data-ttu-id="ddbda-129">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="ddbda-129">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ddbda-130">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="ddbda-130">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ddbda-131">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="ddbda-131">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ddbda-132">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="ddbda-132">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 502
Content-Type: application/json
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
MS-RequestId: 603f3cd9-01b8-48f2-b65d-855a246f5bfd
Date: Wed, 25 Nov 2015 07:16:18 GMT

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
