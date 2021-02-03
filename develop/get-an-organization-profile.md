---
title: Een organisatieprofiel ophalen
description: Hiermee wordt een object opgehaald dat het organisatie profiel van de partner vertegenwoordigt.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 132a1e0efa3efea69d4bf649e55b412e300b0685
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767550"
---
# <a name="get-an-organization-profile"></a><span data-ttu-id="4e845-103">Een organisatieprofiel ophalen</span><span class="sxs-lookup"><span data-stu-id="4e845-103">Get an organization profile</span></span>

<span data-ttu-id="4e845-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="4e845-104">**Applies To**</span></span>

- <span data-ttu-id="4e845-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="4e845-105">Partner Center</span></span>
- <span data-ttu-id="4e845-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="4e845-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="4e845-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="4e845-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="4e845-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="4e845-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="4e845-109">Hiermee wordt een object opgehaald dat het organisatie profiel van de partner vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="4e845-109">Gets an object representing the partner's organization profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4e845-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4e845-110">Prerequisites</span></span>

- <span data-ttu-id="4e845-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4e845-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4e845-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="4e845-112">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="4e845-113">C\#</span><span class="sxs-lookup"><span data-stu-id="4e845-113">C\#</span></span>

<span data-ttu-id="4e845-114">Om uw organisatie profiel op te halen, gebruikt u uw **IAggregatePartner. Profiles** -verzameling en roept u de eigenschap **OrganizationProfile** aan.</span><span class="sxs-lookup"><span data-stu-id="4e845-114">To get your organization profile, use your **IAggregatePartner.Profiles** collection and call the **OrganizationProfile** property.</span></span> <span data-ttu-id="4e845-115">Roep ten slotte de methoden [**Get ()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="4e845-115">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.getasync) methods.</span></span>

```csharp
// IAggregatePartner partnerOperations;

OrganizationProfile organizationProfile = partnerOperations.Profiles.OrganizationProfile.Get();
```

<span data-ttu-id="4e845-116">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="4e845-116">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="4e845-117">**Project**: PartnerCenterSDK. FeaturesSamples- **klasse**: GetOrganizationProfile.cs</span><span class="sxs-lookup"><span data-stu-id="4e845-117">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetOrganizationProfile.cs</span></span>

## <a name="java"></a><span data-ttu-id="4e845-118">Java</span><span class="sxs-lookup"><span data-stu-id="4e845-118">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="4e845-119">Als u uw organisatie profiel wilt ophalen, gebruikt u de functie **IAggregatePartner. getProfiles** en roept u de functie **getOrganizationProfile** aan.</span><span class="sxs-lookup"><span data-stu-id="4e845-119">To get your organization profile, use your **IAggregatePartner.getProfiles** function and call the **getOrganizationProfile** function.</span></span> <span data-ttu-id="4e845-120">Roep ten slotte de functie **Get ()** aan.</span><span class="sxs-lookup"><span data-stu-id="4e845-120">Finally, call the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;

OrganizationProfile organizationProfile = partnerOperations.getProfiles().getOrganizationProfile().get();
```

## <a name="powershell"></a><span data-ttu-id="4e845-121">PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e845-121">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="4e845-122">Voer de opdracht [**Get-PartnerOrganizationProfile**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOrganizationProfile.md) uit om uw organisatie profiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="4e845-122">To get your organization profile, execute the [**Get-PartnerOrganizationProfile**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOrganizationProfile.md) command.</span></span>

```powershell
Get-PartnerOrganizationProfile
```

## <a name="rest-request"></a><span data-ttu-id="4e845-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="4e845-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4e845-124">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4e845-124">Request syntax</span></span>

| <span data-ttu-id="4e845-125">Methode</span><span class="sxs-lookup"><span data-stu-id="4e845-125">Method</span></span>  | <span data-ttu-id="4e845-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="4e845-126">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="4e845-127">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="4e845-127">**GET**</span></span> | <span data-ttu-id="4e845-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/Profiles/Organization http/1.1</span><span class="sxs-lookup"><span data-stu-id="4e845-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/organization HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4e845-129">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="4e845-129">Request headers</span></span>

<span data-ttu-id="4e845-130">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="4e845-130">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4e845-131">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="4e845-131">Request body</span></span>

<span data-ttu-id="4e845-132">Geen.</span><span class="sxs-lookup"><span data-stu-id="4e845-132">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="4e845-133">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4e845-133">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/organization HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b85cb7ab-cc2e-4966-93f0-cf0d8377a93f
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
```

## <a name="rest-response"></a><span data-ttu-id="4e845-134">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="4e845-134">REST response</span></span>

<span data-ttu-id="4e845-135">Als dit lukt, retourneert deze methode een **OrganizationProfile** -object in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="4e845-135">If successful, this method returns an **OrganizationProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4e845-136">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="4e845-136">Response success and error codes</span></span>

<span data-ttu-id="4e845-137">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="4e845-137">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4e845-138">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="4e845-138">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4e845-139">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="4e845-139">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4e845-140">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="4e845-140">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 648
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
MS-RequestId: b85cb7ab-cc2e-4966-93f0-cf0d8377a93f
Date: Tue, 22 Mar 2016 17:11:06 GMT

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
