---
title: Een product upgrade-entiteit maken voor een klant
description: U kunt de ProductUpgradeRequest-Resource gebruiken om een product upgrade-entiteit te maken om een klant bij te werken naar een bepaalde product familie.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 45830033d93e0906eafc169cf04b997e2ff7c3d8
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767199"
---
# <a name="create-a-product-upgrade-entity-for-a-customer"></a><span data-ttu-id="55445-103">Een product upgrade-entiteit maken voor een klant</span><span class="sxs-lookup"><span data-stu-id="55445-103">Create a product upgrade entity for a customer</span></span>

<span data-ttu-id="55445-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="55445-104">**Applies to:**</span></span>

- <span data-ttu-id="55445-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="55445-105">Partner Center</span></span>

<span data-ttu-id="55445-106">U kunt een product upgrade-entiteit maken om een klant bij te werken naar een bepaalde product familie (bijvoorbeeld Azure-abonnement) met behulp van de **ProductUpgradeRequest** -resource.</span><span class="sxs-lookup"><span data-stu-id="55445-106">You can create a product upgrade entity to upgrade a customer to a given product family (for example, Azure plan) using the **ProductUpgradeRequest** resource.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="55445-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="55445-107">Prerequisites</span></span>

- <span data-ttu-id="55445-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="55445-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="55445-109">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="55445-109">This scenario supports authentication with App+User credentials.</span></span> <span data-ttu-id="55445-110">Volg het [model voor beveiligde apps](enable-secure-app-model.md) wanneer u app + gebruikers authenticatie met partner Center api's gebruikt.</span><span class="sxs-lookup"><span data-stu-id="55445-110">Follow the [secure app model](enable-secure-app-model.md) when using App+User authentication with Partner Center APIs.</span></span>

- <span data-ttu-id="55445-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="55445-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="55445-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="55445-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="55445-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="55445-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="55445-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="55445-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="55445-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="55445-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="55445-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="55445-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="55445-117">De product familie waarvoor u de klant wilt bijwerken.</span><span class="sxs-lookup"><span data-stu-id="55445-117">The product family to which you want to upgrade the customer.</span></span>

## <a name="c"></a><span data-ttu-id="55445-118">C\#</span><span class="sxs-lookup"><span data-stu-id="55445-118">C\#</span></span>

<span data-ttu-id="55445-119">Een upgrade uitvoeren van een klant naar een Azure-abonnement:</span><span class="sxs-lookup"><span data-stu-id="55445-119">To upgrade a customer to Azure plan:</span></span>

1. <span data-ttu-id="55445-120">Maak een **ProductUpgradesRequest** -object en geef de klant-id en ' Azure ' op als de product familie.</span><span class="sxs-lookup"><span data-stu-id="55445-120">Create a **ProductUpgradesRequest** object and specify the customer identifier and "Azure" as the product family.</span></span>

2. <span data-ttu-id="55445-121">Gebruik de verzameling **IAggregatePartner. ProductUpgrades** .</span><span class="sxs-lookup"><span data-stu-id="55445-121">Use the **IAggregatePartner.ProductUpgrades** collection.</span></span>

3. <span data-ttu-id="55445-122">Roep de **Create** -methode aan en geef het object **ProductUpgradesRequest** door. Hiermee wordt een teken reeks voor de **locatie-header** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="55445-122">Call the **Create** method and pass in the **ProductUpgradesRequest** object, which will return a **location header** string.</span></span>

4. <span data-ttu-id="55445-123">Pak de **upgrade-ID** uit van de teken reeks voor de locatie-header die kan worden gebruikt om [de upgrade status](get-product-upgrade-status.md)op te vragen.</span><span class="sxs-lookup"><span data-stu-id="55445-123">Extract the **upgrade-id** from the location header string which can be used to [query the upgrade status](get-product-upgrade-status.md).</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="55445-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="55445-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="55445-125">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="55445-125">Request syntax</span></span>

| <span data-ttu-id="55445-126">Methode</span><span class="sxs-lookup"><span data-stu-id="55445-126">Method</span></span>   | <span data-ttu-id="55445-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="55445-127">Request URI</span></span>                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="55445-128">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="55445-128">**POST**</span></span> | <span data-ttu-id="55445-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/productupgrades http/1.1</span><span class="sxs-lookup"><span data-stu-id="55445-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/productupgrades HTTP/1.1</span></span> |

#### <a name="request-headers"></a><span data-ttu-id="55445-130">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="55445-130">Request headers</span></span>

<span data-ttu-id="55445-131">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="55445-131">For more information, see [Partner Center REST headers](headers.md).</span></span>

#### <a name="request-body"></a><span data-ttu-id="55445-132">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="55445-132">Request body</span></span>

<span data-ttu-id="55445-133">De aanvraag tekst moet een [ProductUpgradeRequest](product-upgrade-resources.md#productupgraderequest) -resource bevatten.</span><span class="sxs-lookup"><span data-stu-id="55445-133">The request body must contain a [ProductUpgradeRequest](product-upgrade-resources.md#productupgraderequest) resource.</span></span>

#### <a name="request-example"></a><span data-ttu-id="55445-134">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="55445-134">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="55445-135">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="55445-135">REST response</span></span>

<span data-ttu-id="55445-136">Als dit is gelukt, bevat het antwoord een **locatie** header met een URI die kan worden gebruikt om de upgrade status van het product op te halen.</span><span class="sxs-lookup"><span data-stu-id="55445-136">If successful, the response contains a **Location** header that has a URI that can be used to retrieve product upgrade status.</span></span> <span data-ttu-id="55445-137">Sla deze URI op voor gebruik met andere verwante REST Api's.</span><span class="sxs-lookup"><span data-stu-id="55445-137">Save this URI for use with other related REST APIs.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="55445-138">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="55445-138">Response success and error codes</span></span>

<span data-ttu-id="55445-139">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="55445-139">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="55445-140">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="55445-140">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="55445-141">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="55445-141">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="55445-142">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="55445-142">Response example</span></span>

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
