---
title: Een organisatieprofiel bijwerken
description: Werkt het factureringsprofiel van een organisatie bij.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0ef736a722cde16f95ed6dfdbdab278c98fcf738
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530052"
---
# <a name="update-an-organization-profile"></a><span data-ttu-id="b003e-103">Een organisatieprofiel bijwerken</span><span class="sxs-lookup"><span data-stu-id="b003e-103">Update an organization profile</span></span>

<span data-ttu-id="b003e-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b003e-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b003e-105">Werkt het factureringsprofiel van een partner bij.</span><span class="sxs-lookup"><span data-stu-id="b003e-105">Updates a partner's billing profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b003e-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b003e-106">Prerequisites</span></span>

- <span data-ttu-id="b003e-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b003e-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b003e-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="b003e-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="b003e-109">C\#</span><span class="sxs-lookup"><span data-stu-id="b003e-109">C\#</span></span>

<span data-ttu-id="b003e-110">Als u uw organisatieprofiel wilt bijwerken, haalt u het profiel op en maakt u eventuele benodigde wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="b003e-110">To update your organization profile, retrieve the profile and make any necessary changes.</span></span> <span data-ttu-id="b003e-111">Gebruik vervolgens de verzameling **IAggregatePartner.Profiles** en roep de **eigenschap OrganizationProfile aan.**</span><span class="sxs-lookup"><span data-stu-id="b003e-111">Then, use your **IAggregatePartner.Profiles** collection and call the **OrganizationProfile** property.</span></span> <span data-ttu-id="b003e-112">Roep ten slotte de **methode Update()** aan.</span><span class="sxs-lookup"><span data-stu-id="b003e-112">Finally, call the **Update()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

OrganizationProfile organizationProfile = partnerOperations.Profiles.OrganizationProfile.Get();

// Generating a random phone number to update in the organization profile
organizationProfile.DefaultAddress.PhoneNumber = ((long)(new Random().NextDouble() * 9000000000) + 1000000000).ToString(CultureInfo.InvariantCulture);

OrganizationProfile updatedOrganizationProfile = partnerOperations.Profiles.OrganizationProfile.Update(organizationProfile);
```

<span data-ttu-id="b003e-113">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="b003e-113">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="b003e-114">**Project:** PartnerCenterSDK.FeaturesSamples-klasse: UpdateOrganizationProfile.cs </span><span class="sxs-lookup"><span data-stu-id="b003e-114">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: UpdateOrganizationProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="b003e-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="b003e-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b003e-116">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="b003e-116">Request syntax</span></span>

| <span data-ttu-id="b003e-117">Methode</span><span class="sxs-lookup"><span data-stu-id="b003e-117">Method</span></span>  | <span data-ttu-id="b003e-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="b003e-118">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="b003e-119">**PUT**</span><span class="sxs-lookup"><span data-stu-id="b003e-119">**PUT**</span></span> | <span data-ttu-id="b003e-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/organization HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b003e-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/organization HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="b003e-121">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="b003e-121">Request headers</span></span>

<span data-ttu-id="b003e-122">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="b003e-122">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b003e-123">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="b003e-123">Request body</span></span>

<span data-ttu-id="b003e-124">Geen.</span><span class="sxs-lookup"><span data-stu-id="b003e-124">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b003e-125">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b003e-125">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="b003e-126">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="b003e-126">REST response</span></span>

<span data-ttu-id="b003e-127">Als dit lukt, retourneert deze methode een **OrganizationProfile-object** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="b003e-127">If successful, this method returns an **OrganizationProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b003e-128">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="b003e-128">Response success and error codes</span></span>

<span data-ttu-id="b003e-129">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="b003e-129">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b003e-130">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="b003e-130">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b003e-131">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="b003e-131">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b003e-132">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="b003e-132">Response example</span></span>

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
