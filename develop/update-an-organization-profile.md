---
title: Een organisatieprofiel bijwerken
description: Hiermee wordt het facturerings Profiel van een organisatie bijgewerkt.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ccf938fff285704f54d4717b2678e1419d857d8d
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767259"
---
# <a name="update-an-organization-profile"></a><span data-ttu-id="07573-103">Een organisatieprofiel bijwerken</span><span class="sxs-lookup"><span data-stu-id="07573-103">Update an organization profile</span></span>

<span data-ttu-id="07573-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="07573-104">**Applies To**</span></span>

- <span data-ttu-id="07573-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="07573-105">Partner Center</span></span>
- <span data-ttu-id="07573-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="07573-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="07573-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="07573-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="07573-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="07573-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="07573-109">Hiermee wordt het facturerings Profiel van een partner bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="07573-109">Updates a partner's billing profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="07573-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="07573-110">Prerequisites</span></span>

- <span data-ttu-id="07573-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="07573-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="07573-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="07573-112">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="07573-113">C\#</span><span class="sxs-lookup"><span data-stu-id="07573-113">C\#</span></span>

<span data-ttu-id="07573-114">Als u uw organisatie profiel wilt bijwerken, haalt u het profiel op en brengt u de gewenste wijzigingen aan.</span><span class="sxs-lookup"><span data-stu-id="07573-114">To update your organization profile, retrieve the profile and make any necessary changes.</span></span> <span data-ttu-id="07573-115">Vervolgens gebruikt u de verzameling **IAggregatePartner. Profiles** en roept u de eigenschap **OrganizationProfile** aan.</span><span class="sxs-lookup"><span data-stu-id="07573-115">Then, use your **IAggregatePartner.Profiles** collection and call the **OrganizationProfile** property.</span></span> <span data-ttu-id="07573-116">Roep ten slotte de methode **Update ()** aan.</span><span class="sxs-lookup"><span data-stu-id="07573-116">Finally, call the **Update()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

OrganizationProfile organizationProfile = partnerOperations.Profiles.OrganizationProfile.Get();

// Generating a random phone number to update in the organization profile
organizationProfile.DefaultAddress.PhoneNumber = ((long)(new Random().NextDouble() * 9000000000) + 1000000000).ToString(CultureInfo.InvariantCulture);

OrganizationProfile updatedOrganizationProfile = partnerOperations.Profiles.OrganizationProfile.Update(organizationProfile);
```

<span data-ttu-id="07573-117">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="07573-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="07573-118">**Project**: PartnerCenterSDK. FeaturesSamples- **klasse**: UpdateOrganizationProfile.cs</span><span class="sxs-lookup"><span data-stu-id="07573-118">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: UpdateOrganizationProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="07573-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="07573-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="07573-120">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="07573-120">Request syntax</span></span>

| <span data-ttu-id="07573-121">Methode</span><span class="sxs-lookup"><span data-stu-id="07573-121">Method</span></span>  | <span data-ttu-id="07573-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="07573-122">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="07573-123">**PUT**</span><span class="sxs-lookup"><span data-stu-id="07573-123">**PUT**</span></span> | <span data-ttu-id="07573-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/Profiles/Organization http/1.1</span><span class="sxs-lookup"><span data-stu-id="07573-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/organization HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="07573-125">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="07573-125">Request headers</span></span>

<span data-ttu-id="07573-126">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="07573-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="07573-127">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="07573-127">Request body</span></span>

<span data-ttu-id="07573-128">Geen.</span><span class="sxs-lookup"><span data-stu-id="07573-128">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="07573-129">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="07573-129">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/profiles/organization HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: fe76387b-9658-47d7-939d-0c70032ef589
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
Content-Length: 624
Expect: 100-continue

{
    "id":<id>,
    "companyName":"TEST_TEST_BugBash1",
    "defaultAddress":{
        "country":"US",
        "city":"Redmond",
        "state":"WA",
        "addressLine1":"Two Microsoft Way",
        "addressLine2":"",
        "postalCode":"98052",
        "firstName":"Test",
        "lastName":"Account",
        "phoneNumber":""
    },
    "tenantId":<tenantID>,
    "domain":"testtestbugbash1.onmicrosoft.com",
    "email":"test-partner@microsoft.com",
    "language":"es",
    "culture":"es-US",
    "links":{
        "self":{
            "uri":"/profiles/organization",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "etag":<etag>,
        "objectType":"OrganizationProfile"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="07573-130">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="07573-130">REST response</span></span>

<span data-ttu-id="07573-131">Als dit lukt, retourneert deze methode een **OrganizationProfile** -object in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="07573-131">If successful, this method returns an **OrganizationProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="07573-132">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="07573-132">Response success and error codes</span></span>

<span data-ttu-id="07573-133">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="07573-133">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="07573-134">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="07573-134">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="07573-135">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="07573-135">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="07573-136">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="07573-136">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 648
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
MS-RequestId: fe76387b-9658-47d7-939d-0c70032ef589
Date: Mon, 21 Mar 2016 05:48:41 GMT

{
    "id":<id>,
    "companyName":"TEST_TEST_BugBash1",
    "defaultAddress":{
        "country":"US",
        "city":"Redmond",
        "state":"WA",
        "addressLine1":"Two Microsoft Way",
        "addressLine2":"",
        "postalCode":"98052",
        "firstName":"Test",
        "lastName":"Account",
        "phoneNumber":""
    },
    "tenantId":<tenantID>,
    "domain":"testtestbugbash1.onmicrosoft.com",
    "email":"test-partner@microsoft.com",
    "language":"es",
    "culture":"es-US",
    "profileType":"OrganizationProfile",
    "links":{
        "self":{
            "uri":"/profiles/organization",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "etag":<etag>,
        "objectType":"OrganizationProfile"
    }
}
```
