---
title: Factureringsprofiel van een partner ophalen
description: Hiermee wordt een object opgehaald dat het facturerings Profiel van de partner vertegenwoordigt.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 94c5ff8fc351282ca3b4721511f02ba6a0cc403c
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767541"
---
# <a name="get-partner-billing-profile"></a><span data-ttu-id="8a60a-103">Factureringsprofiel van een partner ophalen</span><span class="sxs-lookup"><span data-stu-id="8a60a-103">Get partner billing profile</span></span>

<span data-ttu-id="8a60a-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="8a60a-104">**Applies To**</span></span>

- <span data-ttu-id="8a60a-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="8a60a-105">Partner Center</span></span>
- <span data-ttu-id="8a60a-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="8a60a-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="8a60a-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="8a60a-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="8a60a-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="8a60a-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="8a60a-109">Hiermee wordt een object opgehaald dat het facturerings Profiel van de partner vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8a60a-109">Gets an object representing the partner's billing profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8a60a-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="8a60a-110">Prerequisites</span></span>

- <span data-ttu-id="8a60a-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8a60a-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8a60a-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="8a60a-112">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="8a60a-113">C\#</span><span class="sxs-lookup"><span data-stu-id="8a60a-113">C\#</span></span>

<span data-ttu-id="8a60a-114">Als u een facturerings profiel voor partners wilt ophalen, gebruikt u de verzameling **IAggregatePartner. Profiles** en roept u de eigenschap **BillingProfile** aan.</span><span class="sxs-lookup"><span data-stu-id="8a60a-114">To get a partner billing profile, use your **IAggregatePartner.Profiles** collection and call the **BillingProfile** property.</span></span> <span data-ttu-id="8a60a-115">Roep ten slotte de methoden [**Get ()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="8a60a-115">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

BillingProfile billingProfile = partnerOperations.Profiles.BillingProfile.Get();
```

<span data-ttu-id="8a60a-116">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="8a60a-116">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="8a60a-117">**Project**: PartnerCenterSDK. FeaturesSamples- **klasse**: GetBillingProfile.cs</span><span class="sxs-lookup"><span data-stu-id="8a60a-117">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: GetBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="8a60a-118">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="8a60a-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8a60a-119">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="8a60a-119">Request syntax</span></span>

| <span data-ttu-id="8a60a-120">Methode</span><span class="sxs-lookup"><span data-stu-id="8a60a-120">Method</span></span>  | <span data-ttu-id="8a60a-121">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="8a60a-121">Request URI</span></span>                                                              |
|---------|--------------------------------------------------------------------------|
| <span data-ttu-id="8a60a-122">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="8a60a-122">**GET**</span></span> | <span data-ttu-id="8a60a-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/Profiles/billing http/1.1</span><span class="sxs-lookup"><span data-stu-id="8a60a-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/billing HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8a60a-124">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="8a60a-124">Request headers</span></span>

<span data-ttu-id="8a60a-125">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="8a60a-125">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8a60a-126">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="8a60a-126">Request body</span></span>

<span data-ttu-id="8a60a-127">Geen.</span><span class="sxs-lookup"><span data-stu-id="8a60a-127">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="8a60a-128">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="8a60a-128">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/billing HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a0dd6cde-b24c-413c-af24-416446dc5599
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
```

## <a name="rest-response"></a><span data-ttu-id="8a60a-129">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="8a60a-129">REST response</span></span>

<span data-ttu-id="8a60a-130">Als dit lukt, retourneert deze methode een **BillingProfile** -object in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="8a60a-130">If successful, this method returns a **BillingProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8a60a-131">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="8a60a-131">Response success and error codes</span></span>

<span data-ttu-id="8a60a-132">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="8a60a-132">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8a60a-133">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="8a60a-133">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8a60a-134">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="8a60a-134">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8a60a-135">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="8a60a-135">Response example</span></span>

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
