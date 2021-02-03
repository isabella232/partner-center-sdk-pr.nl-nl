---
title: De product upgrade status voor een klant ophalen
description: U kunt de ProductUpgradeRequest-Resource gebruiken om de status van een product upgrade voor een klant te bepalen voor een nieuwe product familie, zoals van een Microsoft Azure (MS-AZR-0145P) naar een Azure-abonnement.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1819887d459ec72a48ea2b7a5a4121dc56718313
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767281"
---
# <a name="get-the-product-upgrade-status-for-a-customer"></a><span data-ttu-id="c5720-103">De product upgrade status voor een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="c5720-103">Get the product upgrade status for a customer</span></span>

<span data-ttu-id="c5720-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="c5720-104">**Applies to:**</span></span>

- <span data-ttu-id="c5720-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="c5720-105">Partner Center</span></span>

<span data-ttu-id="c5720-106">U kunt de [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) -Resource gebruiken om de status van een upgrade naar een nieuwe product familie op te halen.</span><span class="sxs-lookup"><span data-stu-id="c5720-106">You can use the [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) resource to get the status of an upgrade to a new product family.</span></span> <span data-ttu-id="c5720-107">Deze resource is van toepassing wanneer u een upgrade uitvoert van een klant van een Microsoft Azure (MS-AZR-0145P) naar een Azure-abonnement.</span><span class="sxs-lookup"><span data-stu-id="c5720-107">This resource applies when you're upgrading a customer from an Microsoft Azure (MS-AZR-0145P) subscription to an Azure plan.</span></span> <span data-ttu-id="c5720-108">Een succes volle aanvraag retourneert de [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) -resource.</span><span class="sxs-lookup"><span data-stu-id="c5720-108">A successful request returns the [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) resource.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c5720-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c5720-109">Prerequisites</span></span>

- <span data-ttu-id="c5720-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c5720-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c5720-111">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="c5720-111">This scenario supports authentication with App+User credentials.</span></span> <span data-ttu-id="c5720-112">Volg het [model voor beveiligde apps](enable-secure-app-model.md) wanneer u app + gebruikers authenticatie met partner Center api's gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c5720-112">Follow the [secure app model](enable-secure-app-model.md) when using App+User authentication with Partner Center APIs.</span></span>

- <span data-ttu-id="c5720-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c5720-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="c5720-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="c5720-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="c5720-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="c5720-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="c5720-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="c5720-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="c5720-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="c5720-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="c5720-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c5720-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="c5720-119">De product familie.</span><span class="sxs-lookup"><span data-stu-id="c5720-119">The product family.</span></span>

- <span data-ttu-id="c5720-120">De upgrade-ID van een upgrade-aanvraag.</span><span class="sxs-lookup"><span data-stu-id="c5720-120">The upgrade-id of an upgrade request.</span></span>

## <a name="c"></a><span data-ttu-id="c5720-121">C\#</span><span class="sxs-lookup"><span data-stu-id="c5720-121">C\#</span></span>

<span data-ttu-id="c5720-122">Controleren of een klant in aanmerking komt voor een upgrade naar een Azure-abonnement:</span><span class="sxs-lookup"><span data-stu-id="c5720-122">To check if a customer is eligible to upgrade to Azure plan:</span></span>

1. <span data-ttu-id="c5720-123">Maak een **ProductUpgradesRequest** -object en geef de klant-id en ' Azure ' op als de product familie.</span><span class="sxs-lookup"><span data-stu-id="c5720-123">Create a **ProductUpgradesRequest** object and specify the customer identifier and "Azure" as the product family.</span></span>

2. <span data-ttu-id="c5720-124">Gebruik de verzameling **IAggregatePartner. ProductUpgrades** .</span><span class="sxs-lookup"><span data-stu-id="c5720-124">Use the **IAggregatePartner.ProductUpgrades** collection.</span></span>

3. <span data-ttu-id="c5720-125">Roep de **ById** -methode aan en geef de **upgrade-ID** door.</span><span class="sxs-lookup"><span data-stu-id="c5720-125">Call the **ById** method and pass in the **upgrade-id**.</span></span>

4. <span data-ttu-id="c5720-126">Roep de methode **CheckStatus** aan en geef het object **ProductUpgradesRequest** door, waardoor een **ProductUpgradeStatus** -object wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c5720-126">Call the **CheckStatus** method and pass in the **ProductUpgradesRequest** object, which will return a **ProductUpgradeStatus** object.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="c5720-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c5720-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c5720-128">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c5720-128">Request syntax</span></span>

| <span data-ttu-id="c5720-129">Methode</span><span class="sxs-lookup"><span data-stu-id="c5720-129">Method</span></span>   | <span data-ttu-id="c5720-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c5720-130">Request URI</span></span> |
|----------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="c5720-131">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="c5720-131">**POST**</span></span> | <span data-ttu-id="c5720-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/{upgrade-ID}/status http/1.1</span><span class="sxs-lookup"><span data-stu-id="c5720-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/{upgrade-id}/status HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="c5720-133">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="c5720-133">URI parameter</span></span>

<span data-ttu-id="c5720-134">Gebruik de volgende query parameter om de klant op te geven voor wie u de upgrade status van een product hebt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c5720-134">Use the following query parameter to specify the customer for whom you're getting a product upgrade status.</span></span>

| <span data-ttu-id="c5720-135">Naam</span><span class="sxs-lookup"><span data-stu-id="c5720-135">Name</span></span>               | <span data-ttu-id="c5720-136">Type</span><span class="sxs-lookup"><span data-stu-id="c5720-136">Type</span></span> | <span data-ttu-id="c5720-137">Vereist</span><span class="sxs-lookup"><span data-stu-id="c5720-137">Required</span></span> | <span data-ttu-id="c5720-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c5720-138">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="c5720-139">**upgrade-ID**</span><span class="sxs-lookup"><span data-stu-id="c5720-139">**upgrade-id**</span></span> | <span data-ttu-id="c5720-140">GUID</span><span class="sxs-lookup"><span data-stu-id="c5720-140">GUID</span></span> | <span data-ttu-id="c5720-141">Yes</span><span class="sxs-lookup"><span data-stu-id="c5720-141">Yes</span></span> | <span data-ttu-id="c5720-142">De waarde is een upgrade-ID met een GUID-indeling.</span><span class="sxs-lookup"><span data-stu-id="c5720-142">The value is a GUID-formatted upgrade identifier.</span></span> <span data-ttu-id="c5720-143">U kunt deze id gebruiken om een upgrade op te geven die moet worden gevolgd.</span><span class="sxs-lookup"><span data-stu-id="c5720-143">You can use this identifier to specify an upgrade to track.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c5720-144">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c5720-144">Request headers</span></span>

<span data-ttu-id="c5720-145">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c5720-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c5720-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c5720-146">Request body</span></span>

<span data-ttu-id="c5720-147">De aanvraag tekst moet een [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) -resource bevatten.</span><span class="sxs-lookup"><span data-stu-id="c5720-147">The request body must contain a [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="c5720-148">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c5720-148">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="c5720-149">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c5720-149">REST response</span></span>

<span data-ttu-id="c5720-150">Als dit lukt, retourneert deze methode een [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) -resource in de hoofd tekst.</span><span class="sxs-lookup"><span data-stu-id="c5720-150">If successful, this method returns a [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) resource in the body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c5720-151">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="c5720-151">Response success and error codes</span></span>

<span data-ttu-id="c5720-152">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="c5720-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c5720-153">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c5720-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c5720-154">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="c5720-154">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c5720-155">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="c5720-155">Response example</span></span>

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
