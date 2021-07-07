---
title: Controleer of een klant in aanmerking komt voor een upgrade naar een Azure-plan
description: U kunt de Resource ProductUpgradeRequest gebruiken om een ProductUpgradesEligibility-resource te retourneren om te bepalen of een klant in aanmerking komt voor een upgrade van een Microsoft Azure-abonnement (MS-AZR-0145P) naar een Azure-abonnement.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 34a20611c7d92042b5432c5ffb3ba4702d77e0c2
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446255"
---
# <a name="check-a-customers-eligibility-for-upgrading-to-an-azure-plan"></a><span data-ttu-id="2d953-103">Controleer of een klant in aanmerking komt voor een upgrade naar een Azure-plan</span><span class="sxs-lookup"><span data-stu-id="2d953-103">Check a customer's eligibility for upgrading to an Azure plan</span></span>

<span data-ttu-id="2d953-104">U kunt de resource [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) gebruiken om te controleren of een klant in aanmerking komt voor een upgrade naar een Azure-plan vanuit een Microsoft Azure-abonnement (MS-AZR-0145P) Deze methode retourneert een [**ProductUpgradesEligibility-resource**](product-upgrade-resources.md#productupgradeseligibility) met de geschiktheid voor productupgrades van de klant.</span><span class="sxs-lookup"><span data-stu-id="2d953-104">You can use the [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) resource to check if a customer is eligible to upgrade to an Azure plan from a Microsoft Azure (MS-AZR-0145P) subscription This method returns a [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) resource with the customer's product upgrade eligibility.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2d953-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2d953-105">Prerequisites</span></span>

- <span data-ttu-id="2d953-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2d953-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2d953-107">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="2d953-107">This scenario supports authentication with App+User credentials.</span></span> <span data-ttu-id="2d953-108">Volg het [model voor beveiligde apps bij](enable-secure-app-model.md) het gebruik van App+User-verificatie met Partner Center API's.</span><span class="sxs-lookup"><span data-stu-id="2d953-108">Follow the [secure app model](enable-secure-app-model.md) when using App+User authentication with Partner Center APIs.</span></span>

- <span data-ttu-id="2d953-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2d953-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="2d953-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="2d953-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="2d953-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="2d953-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="2d953-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="2d953-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="2d953-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="2d953-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="2d953-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2d953-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="2d953-115">De productfamilie.</span><span class="sxs-lookup"><span data-stu-id="2d953-115">The product family.</span></span>

## <a name="c"></a><span data-ttu-id="2d953-116">C\#</span><span class="sxs-lookup"><span data-stu-id="2d953-116">C\#</span></span>

<span data-ttu-id="2d953-117">Ga als volgende te werk om te controleren of een klant in aanmerking komt voor een upgrade naar een Azure-abonnement:</span><span class="sxs-lookup"><span data-stu-id="2d953-117">To check if a customer is eligible to upgrade to Azure plan:</span></span>

1. <span data-ttu-id="2d953-118">Maak een **ProductUpgradesRequest-object** en geef de klant-id en 'Azure' op als de productfamilie.</span><span class="sxs-lookup"><span data-stu-id="2d953-118">Create a **ProductUpgradesRequest** object and specify the customer identifier and "Azure" as the product family.</span></span>

2. <span data-ttu-id="2d953-119">Gebruik de **verzameling IAggregatePartner.ProductUpgrades.**</span><span class="sxs-lookup"><span data-stu-id="2d953-119">Use the **IAggregatePartner.ProductUpgrades** collection.</span></span>
3. <span data-ttu-id="2d953-120">Roep de **CheckEligibility-methode** aan en geef het **productUpgradesRequest-object** door, dat een **ProductUpgradesEligibility-object** retourneert.</span><span class="sxs-lookup"><span data-stu-id="2d953-120">Call the **CheckEligibility** method and pass in the **ProductUpgradesRequest** object, which will return a **ProductUpgradesEligibility** object.</span></span>

```csharp
// IAggregatePartner partnerOperations;

string selectedCustomerId = "58e2af4f-0ad3-4688-8744-be2357cd939a";

string selectedProductFamily = "azure";

var productUpgradeRequest = new ProductUpgradesRequest
{
    CustomerId = selectedCustomerId,
    ProductFamily = selectedProductFamily
};

ProductUpgradesEligibility productUpgradeEligibility = partnerOperations.ProductUpgrades.CheckEligibility(productUpgradeRequest);

if (productUpgradeEligibility.IsEligibile)
{
    ....
}

```

## <a name="rest-request"></a><span data-ttu-id="2d953-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="2d953-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2d953-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="2d953-122">Request syntax</span></span>

| <span data-ttu-id="2d953-123">Methode</span><span class="sxs-lookup"><span data-stu-id="2d953-123">Method</span></span>   | <span data-ttu-id="2d953-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="2d953-124">Request URI</span></span>                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="2d953-125">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="2d953-125">**POST**</span></span> | <span data-ttu-id="2d953-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/eligibility HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="2d953-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/eligibility HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="2d953-127">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="2d953-127">Request headers</span></span>

<span data-ttu-id="2d953-128">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="2d953-128">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2d953-129">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="2d953-129">Request body</span></span>

<span data-ttu-id="2d953-130">De aanvraag body moet een [**ProductUpgradeRequest-resource**](product-upgrade-resources.md#productupgraderequest) bevatten.</span><span class="sxs-lookup"><span data-stu-id="2d953-130">The request body must contain a [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="2d953-131">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2d953-131">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/productupgrades/eligibility HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c245d5f2-1de3-4ae0-9e42-95e38e3cb8ff
MS-CorrelationId: e3f26e6a-044f-4371-ad52-0d91ce4200be
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 340
Expect: 100-continue
Connection: Keep-Alive
{
        "customerId": "4c721420-72ad-4708-a0a7-371a2f7b0969",
        "productFamily": "azure"
}
```

## <a name="rest-response"></a><span data-ttu-id="2d953-132">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="2d953-132">REST response</span></span>

<span data-ttu-id="2d953-133">Als dit lukt, retourneert deze methode een [**ProductUpgradesEligibility-resource**](product-upgrade-resources.md#productupgradeseligibility) in de body.</span><span class="sxs-lookup"><span data-stu-id="2d953-133">If successful, this method returns a [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) resource in the body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2d953-134">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="2d953-134">Response success and error codes</span></span>

<span data-ttu-id="2d953-135">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="2d953-135">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2d953-136">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="2d953-136">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2d953-137">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="2d953-137">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2d953-138">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="2d953-138">Response example</span></span>

```http
HTTP/1.1 200 Ok
Content-Length: 150
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: cb82f7d6-f0d9-44d4-82f9-f6eee6e68390
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
Date: Thu, 04 Oct 2019 20:35:35 GMT

{
    "customerId": "c1958bc7-3284-4952-a257-de594ee64743",
    "isEligible": true,
    "productFamily": "azure"
}
```
