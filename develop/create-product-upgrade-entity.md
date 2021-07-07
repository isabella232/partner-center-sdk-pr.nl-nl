---
title: Een entiteit voor productupgrade maken voor een klant
description: U kunt de resource ProductUpgradeRequest gebruiken om een entiteit voor productupgrade te maken om een klant te upgraden naar een bepaalde productfamilie.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4e346b7f5294a8847047c85115d8c80f34eaca84
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973398"
---
# <a name="create-a-product-upgrade-entity-for-a-customer"></a><span data-ttu-id="eddc5-103">Een entiteit voor productupgrade maken voor een klant</span><span class="sxs-lookup"><span data-stu-id="eddc5-103">Create a product upgrade entity for a customer</span></span>

<span data-ttu-id="eddc5-104">U kunt een entiteit voor productupgrade maken om een klant te upgraden naar een bepaalde productfamilie (bijvoorbeeld een Azure-plan) met behulp van de **productUpgradeRequest-resource.**</span><span class="sxs-lookup"><span data-stu-id="eddc5-104">You can create a product upgrade entity to upgrade a customer to a given product family (for example, Azure plan) using the **ProductUpgradeRequest** resource.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eddc5-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="eddc5-105">Prerequisites</span></span>

- <span data-ttu-id="eddc5-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="eddc5-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="eddc5-107">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="eddc5-107">This scenario supports authentication with App+User credentials.</span></span> <span data-ttu-id="eddc5-108">Volg het [model voor beveiligde apps bij](enable-secure-app-model.md) het gebruik van App+User-verificatie met Partner Center API's.</span><span class="sxs-lookup"><span data-stu-id="eddc5-108">Follow the [secure app model](enable-secure-app-model.md) when using App+User authentication with Partner Center APIs.</span></span>

- <span data-ttu-id="eddc5-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eddc5-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="eddc5-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="eddc5-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="eddc5-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="eddc5-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="eddc5-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="eddc5-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="eddc5-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="eddc5-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="eddc5-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eddc5-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="eddc5-115">De productfamilie waarvoor u de klant wilt upgraden.</span><span class="sxs-lookup"><span data-stu-id="eddc5-115">The product family to which you want to upgrade the customer.</span></span>

## <a name="c"></a><span data-ttu-id="eddc5-116">C\#</span><span class="sxs-lookup"><span data-stu-id="eddc5-116">C\#</span></span>

<span data-ttu-id="eddc5-117">Een klant upgraden naar een Azure-abonnement:</span><span class="sxs-lookup"><span data-stu-id="eddc5-117">To upgrade a customer to Azure plan:</span></span>

1. <span data-ttu-id="eddc5-118">Maak een **ProductUpgradesRequest-object** en geef de klant-id en 'Azure' op als de productfamilie.</span><span class="sxs-lookup"><span data-stu-id="eddc5-118">Create a **ProductUpgradesRequest** object and specify the customer identifier and "Azure" as the product family.</span></span>

2. <span data-ttu-id="eddc5-119">Gebruik de **verzameling IAggregatePartner.ProductUpgrades.**</span><span class="sxs-lookup"><span data-stu-id="eddc5-119">Use the **IAggregatePartner.ProductUpgrades** collection.</span></span>

3. <span data-ttu-id="eddc5-120">Roep de **methode Create** aan en geef het **productUpgradesRequest-object** door, waarmee een locatieheaderreeks **wordt** retourneert.</span><span class="sxs-lookup"><span data-stu-id="eddc5-120">Call the **Create** method and pass in the **ProductUpgradesRequest** object, which will return a **location header** string.</span></span>

4. <span data-ttu-id="eddc5-121">Extraheren van **de upgrade-id** uit de locatieheaderreeks die kan worden gebruikt om de [upgradestatus op te vragen.](get-product-upgrade-status.md)</span><span class="sxs-lookup"><span data-stu-id="eddc5-121">Extract the **upgrade-id** from the location header string that can be used to [query the upgrade status](get-product-upgrade-status.md).</span></span>

```csharp
// IAggregatePartner partnerOperations;

string selectedCustomerId = "58e2af4f-0ad3-4688-8744-be2357cd939a";

string selectedProductFamily = "Azure";

var productUpgradeRequest = new ProductUpgradesRequest
{
    CustomerId = selectedCustomerId,
    ProductFamily = selectedProductFamily
};

var productUpgradeLocationHeader = partnerOperations.ProductUpgrades.Create(productUpgradeRequest);

var upgradeId = Regex.Split(productUpgradeLocationHeader, "/")[1];

```

## <a name="rest-request"></a><span data-ttu-id="eddc5-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="eddc5-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="eddc5-123">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="eddc5-123">Request syntax</span></span>

| <span data-ttu-id="eddc5-124">Methode</span><span class="sxs-lookup"><span data-stu-id="eddc5-124">Method</span></span>   | <span data-ttu-id="eddc5-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="eddc5-125">Request URI</span></span>                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="eddc5-126">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="eddc5-126">**POST**</span></span> | <span data-ttu-id="eddc5-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/productupgrades HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="eddc5-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/productupgrades HTTP/1.1</span></span> |

#### <a name="request-headers"></a><span data-ttu-id="eddc5-128">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="eddc5-128">Request headers</span></span>

<span data-ttu-id="eddc5-129">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="eddc5-129">For more information, see [Partner Center REST headers](headers.md).</span></span>

#### <a name="request-body"></a><span data-ttu-id="eddc5-130">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="eddc5-130">Request body</span></span>

<span data-ttu-id="eddc5-131">De aanvraag body moet een [ProductUpgradeRequest-resource](product-upgrade-resources.md#productupgraderequest) bevatten.</span><span class="sxs-lookup"><span data-stu-id="eddc5-131">The request body must contain a [ProductUpgradeRequest](product-upgrade-resources.md#productupgraderequest) resource.</span></span>

#### <a name="request-example"></a><span data-ttu-id="eddc5-132">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="eddc5-132">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/productupgrades HTTP/1.1
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
  "productFamily": "Azure"
}
```

## <a name="rest-response"></a><span data-ttu-id="eddc5-133">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="eddc5-133">REST response</span></span>

<span data-ttu-id="eddc5-134">Als dit lukt, bevat het antwoord een **Location-header** met een URI die kan worden gebruikt om de status van de productupgrade op te halen.</span><span class="sxs-lookup"><span data-stu-id="eddc5-134">If successful, the response contains a **Location** header that has a URI that can be used to retrieve product upgrade status.</span></span> <span data-ttu-id="eddc5-135">Sla deze URI op voor gebruik met andere gerelateerde REST API's.</span><span class="sxs-lookup"><span data-stu-id="eddc5-135">Save this URI for use with other related REST APIs.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="eddc5-136">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="eddc5-136">Response success and error codes</span></span>

<span data-ttu-id="eddc5-137">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="eddc5-137">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="eddc5-138">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="eddc5-138">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="eddc5-139">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="eddc5-139">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="eddc5-140">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="eddc5-140">Response example</span></span>

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: productUpgrades/42d075a4-bfe7-43e7-af6d-7c68a57edcb4
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: cb82f7d6-f0d9-44d4-82f9-f6eee6e68390
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
Date: Thu, 28 Sep 2019 20:35:35 GMT
```
