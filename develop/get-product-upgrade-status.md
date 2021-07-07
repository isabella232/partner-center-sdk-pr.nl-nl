---
title: De status van de productupgrade voor een klant op te halen
description: U kunt de productUpgradeRequest-resource gebruiken om de status van een productupgrade voor een klant naar een nieuwe productfamilie te bepalen, zoals van een Microsoft Azure-abonnement (MS-AZR-0145P) naar een Azure-abonnement.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 03d925dd0fae987226ad1f8e71fad380ba144b83
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445558"
---
# <a name="get-the-product-upgrade-status-for-a-customer"></a><span data-ttu-id="59331-103">De status van de productupgrade voor een klant op te halen</span><span class="sxs-lookup"><span data-stu-id="59331-103">Get the product upgrade status for a customer</span></span>

<span data-ttu-id="59331-104">U kunt de [**resource ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) gebruiken om de status van een upgrade naar een nieuwe productfamilie op te halen.</span><span class="sxs-lookup"><span data-stu-id="59331-104">You can use the [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) resource to get the status of an upgrade to a new product family.</span></span> <span data-ttu-id="59331-105">Deze resource is van toepassing wanneer u een klant upgradet van een Microsoft Azure-abonnement (MS-AZR-0145P) naar een Azure-abonnement.</span><span class="sxs-lookup"><span data-stu-id="59331-105">This resource applies when you're upgrading a customer from a Microsoft Azure (MS-AZR-0145P) subscription to an Azure plan.</span></span> <span data-ttu-id="59331-106">Een geslaagde aanvraag retourneert [**de resource ProductUpgradesEligibility.**](product-upgrade-resources.md#productupgradeseligibility)</span><span class="sxs-lookup"><span data-stu-id="59331-106">A successful request returns the [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) resource.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59331-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="59331-107">Prerequisites</span></span>

- <span data-ttu-id="59331-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="59331-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="59331-109">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="59331-109">This scenario supports authentication with App+User credentials.</span></span> <span data-ttu-id="59331-110">Volg het [model voor beveiligde apps bij](enable-secure-app-model.md) het gebruik van App+User-verificatie met Partner Center API's.</span><span class="sxs-lookup"><span data-stu-id="59331-110">Follow the [secure app model](enable-secure-app-model.md) when using App+User authentication with Partner Center APIs.</span></span>

- <span data-ttu-id="59331-111">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="59331-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="59331-112">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="59331-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="59331-113">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="59331-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="59331-114">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="59331-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="59331-115">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="59331-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="59331-116">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="59331-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="59331-117">De productfamilie.</span><span class="sxs-lookup"><span data-stu-id="59331-117">The product family.</span></span>

- <span data-ttu-id="59331-118">De upgrade-id van een upgradeaanvraag.</span><span class="sxs-lookup"><span data-stu-id="59331-118">The upgrade-id of an upgrade request.</span></span>

## <a name="c"></a><span data-ttu-id="59331-119">C\#</span><span class="sxs-lookup"><span data-stu-id="59331-119">C\#</span></span>

<span data-ttu-id="59331-120">Ga als volgende te werk om te controleren of een klant in aanmerking komt voor een upgrade naar een Azure-plan:</span><span class="sxs-lookup"><span data-stu-id="59331-120">To check if a customer is eligible to upgrade to Azure plan:</span></span>

1. <span data-ttu-id="59331-121">Maak een **ProductUpgradesRequest-object** en geef de klant-id en 'Azure' op als de productfamilie.</span><span class="sxs-lookup"><span data-stu-id="59331-121">Create a **ProductUpgradesRequest** object and specify the customer identifier and "Azure" as the product family.</span></span>

2. <span data-ttu-id="59331-122">Gebruik de **verzameling IAggregatePartner.ProductUpgrades.**</span><span class="sxs-lookup"><span data-stu-id="59331-122">Use the **IAggregatePartner.ProductUpgrades** collection.</span></span>

3. <span data-ttu-id="59331-123">Roep de **ById-methode** aan en geef **de upgrade-id door.**</span><span class="sxs-lookup"><span data-stu-id="59331-123">Call the **ById** method and pass in the **upgrade-id**.</span></span>

4. <span data-ttu-id="59331-124">Roep de **methode CheckStatus** aan en geef het **productUpgradesRequest-object** door. Dit retourneert een **ProductUpgradeStatus-object.**</span><span class="sxs-lookup"><span data-stu-id="59331-124">Call the **CheckStatus** method and pass in the **ProductUpgradesRequest** object, which will return a **ProductUpgradeStatus** object.</span></span>

```csharp
// IAggregatePartner partnerOperations;

string selectedCustomerId = "58e2af4f-0ad3-4688-8744-be2357cd939a";

string selectedProductFamily = "azure";

var productUpgradeRequest = new ProductUpgradesRequest
{
    CustomerId = selectedCustomerId,
    ProductFamily = selectedProductFamily
};

ProductUpgradesStatus productUpgradeStatus = partnerOperations.ProductUpgrades.ById(selectedUpgradeId).CheckStatus(productUpgradeRequest);

if (productUpgradeEligibility.IsEligibile)
{
    ....
}

```

## <a name="rest-request"></a><span data-ttu-id="59331-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="59331-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="59331-126">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="59331-126">Request syntax</span></span>

| <span data-ttu-id="59331-127">Methode</span><span class="sxs-lookup"><span data-stu-id="59331-127">Method</span></span>   | <span data-ttu-id="59331-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="59331-128">Request URI</span></span> |
|----------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="59331-129">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="59331-129">**POST**</span></span> | <span data-ttu-id="59331-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/{upgrade-id}/status HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="59331-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/{upgrade-id}/status HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="59331-131">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="59331-131">URI parameter</span></span>

<span data-ttu-id="59331-132">Gebruik de volgende queryparameter om de klant op te geven voor wie u de status van een productupgrade krijgt.</span><span class="sxs-lookup"><span data-stu-id="59331-132">Use the following query parameter to specify the customer for whom you're getting a product upgrade status.</span></span>

| <span data-ttu-id="59331-133">Naam</span><span class="sxs-lookup"><span data-stu-id="59331-133">Name</span></span>               | <span data-ttu-id="59331-134">Type</span><span class="sxs-lookup"><span data-stu-id="59331-134">Type</span></span> | <span data-ttu-id="59331-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="59331-135">Required</span></span> | <span data-ttu-id="59331-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="59331-136">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="59331-137">**upgrade-id**</span><span class="sxs-lookup"><span data-stu-id="59331-137">**upgrade-id**</span></span> | <span data-ttu-id="59331-138">GUID</span><span class="sxs-lookup"><span data-stu-id="59331-138">GUID</span></span> | <span data-ttu-id="59331-139">Ja</span><span class="sxs-lookup"><span data-stu-id="59331-139">Yes</span></span> | <span data-ttu-id="59331-140">De waarde is een upgrade-id met GUID-indeling.</span><span class="sxs-lookup"><span data-stu-id="59331-140">The value is a GUID-formatted upgrade identifier.</span></span> <span data-ttu-id="59331-141">U kunt deze id gebruiken om een bij te houden upgrade op te geven.</span><span class="sxs-lookup"><span data-stu-id="59331-141">You can use this identifier to specify an upgrade to track.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="59331-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="59331-142">Request headers</span></span>

<span data-ttu-id="59331-143">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="59331-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="59331-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="59331-144">Request body</span></span>

<span data-ttu-id="59331-145">De aanvraag body moet een [**ProductUpgradeRequest-resource**](product-upgrade-resources.md#productupgraderequest) bevatten.</span><span class="sxs-lookup"><span data-stu-id="59331-145">The request body must contain a [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="59331-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="59331-146">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/productupgrades/42d075a4-bfe7-43e7-af6d-7c68a57edcb4/status  HTTP/1.1
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
 {
    "customerId": "4c721420-72ad-4708-a0a7-371a2f7b0969",
    "productFamily": "azure"
  }
  "Attributes": {
  "ObjectType": "ProductUpgradeRequest"
  }
}
```

## <a name="rest-response"></a><span data-ttu-id="59331-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="59331-147">REST response</span></span>

<span data-ttu-id="59331-148">Als dit lukt, retourneert deze methode een [**ProductUpgradesEligibility-resource**](product-upgrade-resources.md#productupgradeseligibility) in de body.</span><span class="sxs-lookup"><span data-stu-id="59331-148">If successful, this method returns a [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) resource in the body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="59331-149">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="59331-149">Response success and error codes</span></span>

<span data-ttu-id="59331-150">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="59331-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="59331-151">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="59331-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="59331-152">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="59331-152">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="59331-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="59331-153">Response example</span></span>

```http
HTTP/1.1 200 Ok
Content-Length: 150
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: cb82f7d6-f0d9-44d4-82f9-f6eee6e68390
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
Date: Thu, 04 Oct 2019 20:35:35 GMT

{
    "id": "42d075a4-bfe7-43e7-af6d-7c68a57edcb4",
    "status": "Completed",
    "productFamily": "Azure",
    "lineItems": [
        {
            "sourceProduct": {
                "id": "b1beb621-3cad-4d7a-b360-62db33ce028e",
                "name": "AzureSubscription"
            },
            "targetProduct": {
                "id": "d231908e-31c1-de0e-027b-bc5ce11f09d9",
                "name": "Microsoft Azure plan"
            },
            "upgradedDate": "2019-08-29T23:47:28.8524555Z",
            "status": "Completed"
        }
    ]
}

```
