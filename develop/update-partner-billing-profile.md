---
title: Het factureringsprofiel van een partner bijwerken
description: Hiermee wordt het facturerings Profiel van een partner bijgewerkt.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: parthpandyaMSFT
ms.author: parthp
ms.openlocfilehash: 34e7d2396d6dbdd45a6cf87a3bda481f51326f1e
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767325"
---
# <a name="update-the-partner-billing-profile"></a><span data-ttu-id="00db9-103">Het factureringsprofiel van een partner bijwerken</span><span class="sxs-lookup"><span data-stu-id="00db9-103">Update the partner billing profile</span></span>

<span data-ttu-id="00db9-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="00db9-104">**Applies To**</span></span>

- <span data-ttu-id="00db9-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="00db9-105">Partner Center</span></span>
- <span data-ttu-id="00db9-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="00db9-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="00db9-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="00db9-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="00db9-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="00db9-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="00db9-109">Hiermee wordt het facturerings Profiel van een partner bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="00db9-109">Updates a partner's billing profile</span></span>

## <a name="prerequisites"></a><span data-ttu-id="00db9-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="00db9-110">Prerequisites</span></span>

- <span data-ttu-id="00db9-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="00db9-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="00db9-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="00db9-112">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="00db9-113">C\#</span><span class="sxs-lookup"><span data-stu-id="00db9-113">C\#</span></span>

<span data-ttu-id="00db9-114">Als u een facturerings profiel voor de partner wilt bijwerken, haalt u het bestaande profiel op.</span><span class="sxs-lookup"><span data-stu-id="00db9-114">To update a partner billing profile, retrieve the existing profile.</span></span> <span data-ttu-id="00db9-115">Nadat u het profiel hebt bijgewerkt, gebruikt u de verzameling **IAggregatePartner. Profiles** en roept u de eigenschap **BillingProfile** aan.</span><span class="sxs-lookup"><span data-stu-id="00db9-115">Once you have updated the profile, use your **IAggregatePartner.Profiles** collection and call the **BillingProfile** property.</span></span> <span data-ttu-id="00db9-116">Roep ten slotte de methode **Update ()** aan.</span><span class="sxs-lookup"><span data-stu-id="00db9-116">Finally, call the **Update()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

BillingProfile existingBillingProfile = partnerOperations.Profiles.BillingProfile.Get();

// update the profile with a purchase order number
existingBillingProfile.PurchaseOrderNumber = new Random().Next(9000, 10000).ToString(CultureInfo.InvariantCulture);

BillingProfile updatedPartnerBillingProfile = partnerOperations.Profiles.BillingProfile.Update(existingBillingProfile);
```

<span data-ttu-id="00db9-117">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="00db9-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="00db9-118">**Project**: Partner Center SDK-voor beelden **klasse**: UpdateBillingProfile.cs</span><span class="sxs-lookup"><span data-stu-id="00db9-118">**Project**: Partner Center SDK Samples **Class**: UpdateBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="00db9-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="00db9-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="00db9-120">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="00db9-120">Request syntax</span></span>

| <span data-ttu-id="00db9-121">Methode</span><span class="sxs-lookup"><span data-stu-id="00db9-121">Method</span></span>  | <span data-ttu-id="00db9-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="00db9-122">Request URI</span></span>                                                              |
|---------|--------------------------------------------------------------------------|
| <span data-ttu-id="00db9-123">**PUT**</span><span class="sxs-lookup"><span data-stu-id="00db9-123">**PUT**</span></span> | <span data-ttu-id="00db9-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/Profiles/billing http/1.1</span><span class="sxs-lookup"><span data-stu-id="00db9-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/billing HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="00db9-125">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="00db9-125">Request headers</span></span>

<span data-ttu-id="00db9-126">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="00db9-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="00db9-127">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="00db9-127">Request body</span></span>

<span data-ttu-id="00db9-128">Geen.</span><span class="sxs-lookup"><span data-stu-id="00db9-128">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="00db9-129">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="00db9-129">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/profiles/billing HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 9231559e-ed95-41e4-810b-e754ae32dc2f
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
Content-Length: 613
Expect: 100-continue

{
    "CompanyName":"TEST_TEST_BugBash1",
    "Address":{
        "Country":"US",
        "Region":null,
        "City":"Redmond",
        "State":"WA",
        "AddressLine1":"1 Microsoft Way",
        "AddressLine2":"","PostalCode":"98052",
        "FirstName":null,
        "LastName":null,
        "PhoneNumber":null
    },
    "PrimaryContact":{
        "FirstName":"Test",
        "LastName":"Customer",
        "Email":null,
        "PhoneNumber":""
    },
    "PurchaseOrderNumber":"9888",
    "TaxId":<TaxId>,
    "BillingCurrency":"USD",
    "Links":{
        "Self":{
            "Uri":"/profiles/billing",
            "Method":"GET","Headers":[]
        }
    },
    "Attributes":{
        "Etag":<etag>,
        "ObjectType":"BillingProfile"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="00db9-130">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="00db9-130">REST response</span></span>

<span data-ttu-id="00db9-131">Als dit lukt, retourneert deze methode een **BillingProfile** -object in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="00db9-131">If successful, this method returns a **BillingProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="00db9-132">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="00db9-132">Response success and error codes</span></span>

<span data-ttu-id="00db9-133">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="00db9-133">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="00db9-134">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="00db9-134">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="00db9-135">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="00db9-135">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="00db9-136">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="00db9-136">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 568
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
MS-RequestId: 9231559e-ed95-41e4-810b-e754ae32dc2f
Date: Mon, 21 Mar 2016 05:47:16 GMT

{
    "CompanyName":"TEST_TEST_BugBash1",
    "Address":{
        "Country":"US",
        "Region":null,
        "City":"Redmond",
        "State":"WA",
        "AddressLine1":"1 Microsoft Way",
        "AddressLine2":"","PostalCode":"98052",
        "FirstName":null,
        "LastName":null,
        "PhoneNumber":null
    },
    "PrimaryContact":{
        "FirstName":"Test",
        "LastName":"Customer",
        "Email":null,
        "PhoneNumber":""
    },
    "PurchaseOrderNumber":"9888",
    "TaxId":<TaxId>,
    "BillingCurrency":"USD",
    "Links":{
        "Self":{
            "Uri":"/profiles/billing",
            "Method":"GET","Headers":[]
        }
    },
    "Attributes":{
        "Etag":<etag>,
        "ObjectType":"BillingProfile"
    }
}
```
