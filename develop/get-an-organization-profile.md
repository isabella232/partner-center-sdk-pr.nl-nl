---
title: Een organisatieprofiel ophalen
description: Haalt een -object op dat het organisatieprofiel van de partner vertegenwoordigt.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 1c7272761612e573388d4facea1a78808a5bad52
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760552"
---
# <a name="get-an-organization-profile"></a><span data-ttu-id="cd022-103">Een organisatieprofiel ophalen</span><span class="sxs-lookup"><span data-stu-id="cd022-103">Get an organization profile</span></span>

<span data-ttu-id="cd022-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="cd022-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="cd022-105">Haalt een -object op dat het organisatieprofiel van de partner vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="cd022-105">Gets an object representing the partner's organization profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cd022-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cd022-106">Prerequisites</span></span>

- <span data-ttu-id="cd022-107">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="cd022-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cd022-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="cd022-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="cd022-109">C\#</span><span class="sxs-lookup"><span data-stu-id="cd022-109">C\#</span></span>

<span data-ttu-id="cd022-110">Als u uw organisatieprofiel wilt ophalen, gebruikt u de **verzameling IAggregatePartner.Profiles** en roept u de **eigenschap OrganizationProfile aan.**</span><span class="sxs-lookup"><span data-stu-id="cd022-110">To get your organization profile, use your **IAggregatePartner.Profiles** collection and call the **OrganizationProfile** property.</span></span> <span data-ttu-id="cd022-111">Roep ten slotte de [**methoden Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.get) of [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="cd022-111">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.iorganizationprofile.getasync) methods.</span></span>

```csharp
// IAggregatePartner partnerOperations;

OrganizationProfile organizationProfile = partnerOperations.Profiles.OrganizationProfile.Get();
```

<span data-ttu-id="cd022-112">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="cd022-112">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="cd022-113">**Project:** PartnerCenterSDK.FeaturesSamples-klasse: GetOrganizationProfile.cs </span><span class="sxs-lookup"><span data-stu-id="cd022-113">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetOrganizationProfile.cs</span></span>

## <a name="java"></a><span data-ttu-id="cd022-114">Java</span><span class="sxs-lookup"><span data-stu-id="cd022-114">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="cd022-115">Gebruik de functie **IAggregatePartner.getProfiles** en roep de **functie getOrganizationProfile** aan om uw organisatieprofiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="cd022-115">To get your organization profile, use your **IAggregatePartner.getProfiles** function and call the **getOrganizationProfile** function.</span></span> <span data-ttu-id="cd022-116">Roep ten slotte de **functie get()** aan.</span><span class="sxs-lookup"><span data-stu-id="cd022-116">Finally, call the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;

OrganizationProfile organizationProfile = partnerOperations.getProfiles().getOrganizationProfile().get();
```

## <a name="powershell"></a><span data-ttu-id="cd022-117">PowerShell</span><span class="sxs-lookup"><span data-stu-id="cd022-117">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="cd022-118">Voer de opdracht [**Get-PartnerOrganizationProfile**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOrganizationProfile.md) uit om uw organisatieprofiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="cd022-118">To get your organization profile, execute the [**Get-PartnerOrganizationProfile**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerOrganizationProfile.md) command.</span></span>

```powershell
Get-PartnerOrganizationProfile
```

## <a name="rest-request"></a><span data-ttu-id="cd022-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="cd022-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cd022-120">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="cd022-120">Request syntax</span></span>

| <span data-ttu-id="cd022-121">Methode</span><span class="sxs-lookup"><span data-stu-id="cd022-121">Method</span></span>  | <span data-ttu-id="cd022-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="cd022-122">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="cd022-123">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="cd022-123">**GET**</span></span> | <span data-ttu-id="cd022-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/organization HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="cd022-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/organization HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="cd022-125">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="cd022-125">Request headers</span></span>

<span data-ttu-id="cd022-126">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="cd022-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cd022-127">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="cd022-127">Request body</span></span>

<span data-ttu-id="cd022-128">Geen.</span><span class="sxs-lookup"><span data-stu-id="cd022-128">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="cd022-129">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cd022-129">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/organization HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b85cb7ab-cc2e-4966-93f0-cf0d8377a93f
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
```

## <a name="rest-response"></a><span data-ttu-id="cd022-130">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="cd022-130">REST response</span></span>

<span data-ttu-id="cd022-131">Als dit lukt, retourneert deze methode een **OrganizationProfile-object** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="cd022-131">If successful, this method returns an **OrganizationProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cd022-132">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="cd022-132">Response success and error codes</span></span>

<span data-ttu-id="cd022-133">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="cd022-133">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cd022-134">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="cd022-134">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="cd022-135">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="cd022-135">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="cd022-136">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="cd022-136">Response example</span></span>

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
