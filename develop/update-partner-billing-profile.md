---
title: Het factureringsprofiel van een partner bijwerken
description: Werkt het factureringsprofiel van een partner bij.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: parthpandyaMSFT
ms.author: parthp
ms.openlocfilehash: 2b09a0045df15d774c892a59fba8502d4d4f7024
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529763"
---
# <a name="update-the-partner-billing-profile"></a><span data-ttu-id="e7c16-103">Het factureringsprofiel van een partner bijwerken</span><span class="sxs-lookup"><span data-stu-id="e7c16-103">Update the partner billing profile</span></span>

<span data-ttu-id="e7c16-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e7c16-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e7c16-105">Het factureringsprofiel van een partner wordt bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="e7c16-105">Updates a partner's billing profile</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e7c16-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e7c16-106">Prerequisites</span></span>

- <span data-ttu-id="e7c16-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e7c16-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e7c16-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="e7c16-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="e7c16-109">C\#</span><span class="sxs-lookup"><span data-stu-id="e7c16-109">C\#</span></span>

<span data-ttu-id="e7c16-110">Als u een partnerfactureringsprofiel wilt bijwerken, haalt u het bestaande profiel op.</span><span class="sxs-lookup"><span data-stu-id="e7c16-110">To update a partner billing profile, retrieve the existing profile.</span></span> <span data-ttu-id="e7c16-111">Nadat u het profiel hebt bijgewerkt, gebruikt u de **verzameling IAggregatePartner.Profiles** en roept u de **eigenschap BillingProfile aan.**</span><span class="sxs-lookup"><span data-stu-id="e7c16-111">Once you have updated the profile, use your **IAggregatePartner.Profiles** collection and call the **BillingProfile** property.</span></span> <span data-ttu-id="e7c16-112">Roep ten slotte de **methode Update()** aan.</span><span class="sxs-lookup"><span data-stu-id="e7c16-112">Finally, call the **Update()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

BillingProfile existingBillingProfile = partnerOperations.Profiles.BillingProfile.Get();

// update the profile with a purchase order number
existingBillingProfile.PurchaseOrderNumber = new Random().Next(9000, 10000).ToString(CultureInfo.InvariantCulture);

BillingProfile updatedPartnerBillingProfile = partnerOperations.Profiles.BillingProfile.Update(existingBillingProfile);
```

<span data-ttu-id="e7c16-113">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="e7c16-113">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="e7c16-114">**Project**: Partnercentrum-SDK Samples **Class**: UpdateBillingProfile.cs</span><span class="sxs-lookup"><span data-stu-id="e7c16-114">**Project**: Partner Center SDK Samples **Class**: UpdateBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="e7c16-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e7c16-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e7c16-116">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e7c16-116">Request syntax</span></span>

| <span data-ttu-id="e7c16-117">Methode</span><span class="sxs-lookup"><span data-stu-id="e7c16-117">Method</span></span>  | <span data-ttu-id="e7c16-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e7c16-118">Request URI</span></span>                                                              |
|---------|--------------------------------------------------------------------------|
| <span data-ttu-id="e7c16-119">**PUT**</span><span class="sxs-lookup"><span data-stu-id="e7c16-119">**PUT**</span></span> | <span data-ttu-id="e7c16-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/billing HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e7c16-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/billing HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e7c16-121">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e7c16-121">Request headers</span></span>

<span data-ttu-id="e7c16-122">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e7c16-122">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e7c16-123">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e7c16-123">Request body</span></span>

<span data-ttu-id="e7c16-124">Geen.</span><span class="sxs-lookup"><span data-stu-id="e7c16-124">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e7c16-125">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e7c16-125">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="e7c16-126">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e7c16-126">REST response</span></span>

<span data-ttu-id="e7c16-127">Als dit lukt, retourneert deze methode een **BillingProfile-object** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="e7c16-127">If successful, this method returns a **BillingProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e7c16-128">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e7c16-128">Response success and error codes</span></span>

<span data-ttu-id="e7c16-129">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e7c16-129">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e7c16-130">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e7c16-130">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e7c16-131">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="e7c16-131">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e7c16-132">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e7c16-132">Response example</span></span>

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
