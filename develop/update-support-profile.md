---
title: Ondersteuningsprofiel bijwerken
description: Hiermee werkt u het ondersteunings Profiel van een gebruiker bij.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 605c509eeb18f301144fec6287c9611d5a5acfe2
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767459"
---
# <a name="update-support-profile"></a><span data-ttu-id="1309d-103">Ondersteuningsprofiel bijwerken</span><span class="sxs-lookup"><span data-stu-id="1309d-103">Update support profile</span></span>

<span data-ttu-id="1309d-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="1309d-104">**Applies To**</span></span>

- <span data-ttu-id="1309d-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="1309d-105">Partner Center</span></span>
- <span data-ttu-id="1309d-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="1309d-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="1309d-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="1309d-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="1309d-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="1309d-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="1309d-109">Hiermee werkt u het ondersteunings Profiel van een gebruiker bij.</span><span class="sxs-lookup"><span data-stu-id="1309d-109">Updates a user's support profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1309d-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1309d-110">Prerequisites</span></span>

- <span data-ttu-id="1309d-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1309d-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1309d-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="1309d-112">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="1309d-113">C\#</span><span class="sxs-lookup"><span data-stu-id="1309d-113">C\#</span></span>

<span data-ttu-id="1309d-114">Als u uw ondersteunings profiel wilt bijwerken, moet u eerst [uw ondersteunings profiel ophalen](get-support-profile.md) en de gewenste wijzigingen aanbrengen.</span><span class="sxs-lookup"><span data-stu-id="1309d-114">To update your support profile, first [get your support profile](get-support-profile.md) and make any changes you wish.</span></span> <span data-ttu-id="1309d-115">Gebruik vervolgens uw verzameling [**IPartnerOperations. Profiles**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles) .</span><span class="sxs-lookup"><span data-stu-id="1309d-115">Then, use your [**IPartnerOperations.Profiles**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles) collection.</span></span> <span data-ttu-id="1309d-116">Roep de eigenschap [**SupportProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) aan, gevolgd door de methode [**Update ()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.update) of [**UpdateAsync ()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.updateasync) .</span><span class="sxs-lookup"><span data-stu-id="1309d-116">Call the [**SupportProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) property, followed by the [**Update()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.update) or [**UpdateAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.updateasync) method.</span></span>

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

<span data-ttu-id="1309d-117">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="1309d-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="1309d-118">**Project**: PartnerCenterSDK. FeaturesSamples- **klasse**: UpdateSupportProfile.cs</span><span class="sxs-lookup"><span data-stu-id="1309d-118">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: UpdateSupportProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="1309d-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="1309d-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1309d-120">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1309d-120">Request syntax</span></span>

| <span data-ttu-id="1309d-121">Methode</span><span class="sxs-lookup"><span data-stu-id="1309d-121">Method</span></span>  | <span data-ttu-id="1309d-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="1309d-122">Request URI</span></span>                                                                     |
|---------|---------------------------------------------------------------------------------|
| <span data-ttu-id="1309d-123">**PUT**</span><span class="sxs-lookup"><span data-stu-id="1309d-123">**PUT**</span></span> | <span data-ttu-id="1309d-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/Profiles/supportprofile http/1.1</span><span class="sxs-lookup"><span data-stu-id="1309d-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/supportprofile HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="1309d-125">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="1309d-125">Request headers</span></span>

<span data-ttu-id="1309d-126">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="1309d-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1309d-127">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="1309d-127">Request body</span></span>

<span data-ttu-id="1309d-128">De volledige ondersteunings profiel resource.</span><span class="sxs-lookup"><span data-stu-id="1309d-128">The full support profile resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="1309d-129">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1309d-129">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="1309d-130">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="1309d-130">REST response</span></span>

<span data-ttu-id="1309d-131">Als dit lukt, retourneert deze methode bijgewerkte **SupportProfile** -object eigenschappen in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="1309d-131">If successful, this method returns updated **SupportProfile** object properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1309d-132">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="1309d-132">Response success and error codes</span></span>

<span data-ttu-id="1309d-133">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="1309d-133">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1309d-134">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="1309d-134">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1309d-135">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="1309d-135">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="1309d-136">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="1309d-136">Response example</span></span>

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
