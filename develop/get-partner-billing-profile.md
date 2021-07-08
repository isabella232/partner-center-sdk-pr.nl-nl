---
title: Factureringsprofiel van een partner ophalen
description: Haalt een -object op dat het factureringsprofiel van de partner vertegenwoordigt.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 225d8ea2d92933838ae47eaf3308276aa1f1684c
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548971"
---
# <a name="get-partner-billing-profile"></a><span data-ttu-id="fb246-103">Factureringsprofiel van een partner ophalen</span><span class="sxs-lookup"><span data-stu-id="fb246-103">Get partner billing profile</span></span>

<span data-ttu-id="fb246-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="fb246-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="fb246-105">Haalt een -object op dat het factureringsprofiel van de partner vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="fb246-105">Gets an object representing the partner's billing profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fb246-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fb246-106">Prerequisites</span></span>

- <span data-ttu-id="fb246-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fb246-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fb246-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="fb246-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="fb246-109">C\#</span><span class="sxs-lookup"><span data-stu-id="fb246-109">C\#</span></span>

<span data-ttu-id="fb246-110">Als u een partnerfactureringsprofiel wilt ophalen, gebruikt u de verzameling **IAggregatePartner.Profiles** en roept u de **eigenschap BillingProfile aan.**</span><span class="sxs-lookup"><span data-stu-id="fb246-110">To get a partner billing profile, use your **IAggregatePartner.Profiles** collection and call the **BillingProfile** property.</span></span> <span data-ttu-id="fb246-111">Roep ten slotte de [**methoden Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.get) of [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="fb246-111">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

BillingProfile billingProfile = partnerOperations.Profiles.BillingProfile.Get();
```

<span data-ttu-id="fb246-112">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="fb246-112">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="fb246-113">**Project:** PartnerCenterSDK.FeaturesKlasse: GetBillingProfile.cs </span><span class="sxs-lookup"><span data-stu-id="fb246-113">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="fb246-114">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fb246-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fb246-115">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="fb246-115">Request syntax</span></span>

| <span data-ttu-id="fb246-116">Methode</span><span class="sxs-lookup"><span data-stu-id="fb246-116">Method</span></span>  | <span data-ttu-id="fb246-117">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fb246-117">Request URI</span></span>                                                              |
|---------|--------------------------------------------------------------------------|
| <span data-ttu-id="fb246-118">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fb246-118">**GET**</span></span> | <span data-ttu-id="fb246-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/billing HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fb246-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/billing HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="fb246-120">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="fb246-120">Request headers</span></span>

<span data-ttu-id="fb246-121">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="fb246-121">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fb246-122">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="fb246-122">Request body</span></span>

<span data-ttu-id="fb246-123">Geen.</span><span class="sxs-lookup"><span data-stu-id="fb246-123">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="fb246-124">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fb246-124">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/billing HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a0dd6cde-b24c-413c-af24-416446dc5599
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
```

## <a name="rest-response"></a><span data-ttu-id="fb246-125">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fb246-125">REST response</span></span>

<span data-ttu-id="fb246-126">Als dit lukt, retourneert deze methode een **BillingProfile-object** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="fb246-126">If successful, this method returns a **BillingProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fb246-127">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="fb246-127">Response success and error codes</span></span>

<span data-ttu-id="fb246-128">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="fb246-128">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fb246-129">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fb246-129">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fb246-130">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="fb246-130">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fb246-131">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fb246-131">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 568
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
MS-RequestId: a0dd6cde-b24c-413c-af24-416446dc5599
Date: Tue, 22 Mar 2016 17:10:02 GMT

{
    "companyName":"TEST_TEST_BugBash1",
    "address":{
        "country":"US",
        "city":"Redmond",
        "state":"WA",
        "addressLine1":"1 Microsoft Way",
        "addressLine2":"","postalCode":"98052"
    },
    "primaryContact":{
        "firstName":"James",
        "lastName":"Burk",
        "phoneNumber":"2066017143"
    },
    "purchaseOrderNumber":"9888",
    "taxId":"12-345678",
    "billingCurrency":"USD",
    "profileType":"BillingProfile",
    "links":{
        "self":{
            "uri":"/profiles/billing",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "etag":<etag>,
        "objectType":"BillingProfile"
    }
}
```
