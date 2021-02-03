---
title: Controleren of de klant in aanmerking komt voor een upgrade naar een Azure-abonnement
description: U kunt de ProductUpgradeRequest-Resource gebruiken om een ProductUpgradesEligibility-resource te retour neren om te bepalen of een klant in aanmerking komt voor een upgrade van een Microsoft Azure (MS-AZR-0145P) naar een Azure-abonnement.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 568ed3f4cff7d9cd520e608d43cb89bb78e00ccc
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767169"
---
# <a name="check-a-customers-eligibility-for-upgrading-to-an-azure-plan"></a><span data-ttu-id="f44a5-103">Controleren of de klant in aanmerking komt voor een upgrade naar een Azure-abonnement</span><span class="sxs-lookup"><span data-stu-id="f44a5-103">Check a customer's eligibility for upgrading to an Azure plan</span></span>

<span data-ttu-id="f44a5-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="f44a5-104">**Applies to:**</span></span>

- <span data-ttu-id="f44a5-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="f44a5-105">Partner Center</span></span>

<span data-ttu-id="f44a5-106">U kunt de [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) -Resource gebruiken om te controleren of een klant in aanmerking komt voor een upgrade naar een Azure-abonnement van een Microsoft Azure (MS-AZR-0145P). deze methode retourneert een [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) -resource met de product upgrade van de klant.</span><span class="sxs-lookup"><span data-stu-id="f44a5-106">You can use the [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) resource to check if a customer is eligible to upgrade to an Azure plan from a Microsoft Azure (MS-AZR-0145P) subscription This method returns a [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) resource with the customer's product upgrade eligibility.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f44a5-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f44a5-107">Prerequisites</span></span>

- <span data-ttu-id="f44a5-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f44a5-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f44a5-109">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="f44a5-109">This scenario supports authentication with App+User credentials.</span></span> <span data-ttu-id="f44a5-110">Volg het [model voor beveiligde apps](enable-secure-app-model.md) wanneer u app + gebruikers authenticatie met partner Center api's gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f44a5-110">Follow the [secure app model](enable-secure-app-model.md) when using App+User authentication with Partner Center APIs.</span></span>

- <span data-ttu-id="f44a5-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f44a5-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f44a5-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="f44a5-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f44a5-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="f44a5-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f44a5-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="f44a5-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f44a5-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="f44a5-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f44a5-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f44a5-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="f44a5-117">De product familie.</span><span class="sxs-lookup"><span data-stu-id="f44a5-117">The product family.</span></span>

## <a name="c"></a><span data-ttu-id="f44a5-118">C\#</span><span class="sxs-lookup"><span data-stu-id="f44a5-118">C\#</span></span>

<span data-ttu-id="f44a5-119">Controleren of een klant in aanmerking komt voor een upgrade naar een Azure-abonnement:</span><span class="sxs-lookup"><span data-stu-id="f44a5-119">To check if a customer is eligible to upgrade to Azure plan:</span></span>

1. <span data-ttu-id="f44a5-120">Maak een **ProductUpgradesRequest** -object en geef de klant-id en ' Azure ' op als de product familie.</span><span class="sxs-lookup"><span data-stu-id="f44a5-120">Create a **ProductUpgradesRequest** object and specify the customer identifier and "Azure" as the product family.</span></span>

2. <span data-ttu-id="f44a5-121">Gebruik de verzameling **IAggregatePartner. ProductUpgrades** .</span><span class="sxs-lookup"><span data-stu-id="f44a5-121">Use the **IAggregatePartner.ProductUpgrades** collection.</span></span>
3. <span data-ttu-id="f44a5-122">Roep de methode **CheckEligibility** aan en geef het object **ProductUpgradesRequest** door, waardoor een **ProductUpgradesEligibility** -object wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f44a5-122">Call the **CheckEligibility** method and pass in the **ProductUpgradesRequest** object, which will return a **ProductUpgradesEligibility** object.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="f44a5-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="f44a5-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f44a5-124">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="f44a5-124">Request syntax</span></span>

| <span data-ttu-id="f44a5-125">Methode</span><span class="sxs-lookup"><span data-stu-id="f44a5-125">Method</span></span>   | <span data-ttu-id="f44a5-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="f44a5-126">Request URI</span></span>                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="f44a5-127">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="f44a5-127">**POST**</span></span> | <span data-ttu-id="f44a5-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/Eligibility http/1.1</span><span class="sxs-lookup"><span data-stu-id="f44a5-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/eligibility HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="f44a5-129">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="f44a5-129">Request headers</span></span>

<span data-ttu-id="f44a5-130">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="f44a5-130">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f44a5-131">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="f44a5-131">Request body</span></span>

<span data-ttu-id="f44a5-132">De aanvraag tekst moet een [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) -resource bevatten.</span><span class="sxs-lookup"><span data-stu-id="f44a5-132">The request body must contain a [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="f44a5-133">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="f44a5-133">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="f44a5-134">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="f44a5-134">REST response</span></span>

<span data-ttu-id="f44a5-135">Als dit lukt, retourneert deze methode een [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) -resource in de hoofd tekst.</span><span class="sxs-lookup"><span data-stu-id="f44a5-135">If successful, this method returns a [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) resource in the body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f44a5-136">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="f44a5-136">Response success and error codes</span></span>

<span data-ttu-id="f44a5-137">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="f44a5-137">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f44a5-138">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="f44a5-138">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f44a5-139">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="f44a5-139">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="f44a5-140">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="f44a5-140">Response example</span></span>

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
