---
title: Een lijst met invoegtoepassingen voor een abonnement ophalen
description: Een verzameling invoeg toepassingen ophalen die een klant heeft gekozen voor het toevoegen van een abonnement.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 4e62ad22cf30c34dedfeb628003c695e33b78758
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767373"
---
# <a name="get-a-list-of-add-ons-for-a-subscription"></a><span data-ttu-id="e157d-103">Een lijst met invoegtoepassingen voor een abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="e157d-103">Get a list of add-ons for a subscription</span></span>

<span data-ttu-id="e157d-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="e157d-104">**Applies to:**</span></span>

- <span data-ttu-id="e157d-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e157d-105">Partner Center</span></span>
- <span data-ttu-id="e157d-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="e157d-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="e157d-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="e157d-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="e157d-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e157d-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e157d-109">In dit artikel wordt beschreven hoe u een verzameling invoeg toepassingen kunt ophalen die een klant heeft gekozen om toe te voegen aan hun **[abonnements](subscription-resources.md)** resource.</span><span class="sxs-lookup"><span data-stu-id="e157d-109">This article describes how to get a collection of add-ons that a customer has chosen to add to their **[Subscription](subscription-resources.md)** resource.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e157d-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e157d-110">Prerequisites</span></span>

- <span data-ttu-id="e157d-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e157d-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e157d-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="e157d-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="e157d-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e157d-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e157d-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="e157d-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e157d-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="e157d-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e157d-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="e157d-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e157d-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="e157d-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e157d-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e157d-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="e157d-119">Een abonnements-ID.</span><span class="sxs-lookup"><span data-stu-id="e157d-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="e157d-120">C\#</span><span class="sxs-lookup"><span data-stu-id="e157d-120">C\#</span></span>

<span data-ttu-id="e157d-121">De lijst met invoeg toepassingen voor het abonnement van een klant ophalen:</span><span class="sxs-lookup"><span data-stu-id="e157d-121">To get the list of add-ons for a customer's subscription:</span></span>

1. <span data-ttu-id="e157d-122">Gebruik uw verzameling **IAggregatePartner. Customers** om de methode **ById ()** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="e157d-122">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="e157d-123">Roep de eigenschap [**abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) aan, gevolgd door de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) .</span><span class="sxs-lookup"><span data-stu-id="e157d-123">Call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span>

3. <span data-ttu-id="e157d-124">Roep de eigenschap [**Addons**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.addons) aan, gevolgd door [**Get ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.getasync).</span><span class="sxs-lookup"><span data-stu-id="e157d-124">Call the [**Addons**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.addons) property, followed by [**Get()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.getasync).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// var selectedSubscription Subscription;

var subscriptionDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).AddOns.Get();

```

<span data-ttu-id="e157d-125">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="e157d-125">For an example, see the following:</span></span>

- <span data-ttu-id="e157d-126">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="e157d-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="e157d-127">Project: **PartnerSDK. FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="e157d-127">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="e157d-128">Klasse: **SubscriptionAddons.cs**</span><span class="sxs-lookup"><span data-stu-id="e157d-128">Class: **SubscriptionAddons.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="e157d-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e157d-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e157d-130">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e157d-130">Request syntax</span></span>

| <span data-ttu-id="e157d-131">Methode</span><span class="sxs-lookup"><span data-stu-id="e157d-131">Method</span></span>  | <span data-ttu-id="e157d-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e157d-132">Request URI</span></span>                                                                                                                       |
|---------|-----------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e157d-133">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e157d-133">**GET**</span></span> | <span data-ttu-id="e157d-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{id-for-Subscription}/addons http/1.1</span><span class="sxs-lookup"><span data-stu-id="e157d-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/addons HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="e157d-135">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="e157d-135">URI parameter</span></span>

<span data-ttu-id="e157d-136">Deze tabel bevat de vereiste query parameters om de lijst met invoeg toepassingen voor het abonnement op te halen.</span><span class="sxs-lookup"><span data-stu-id="e157d-136">This table lists the required query parameters to get the list of add-ons for the subscription.</span></span>

| <span data-ttu-id="e157d-137">Naam</span><span class="sxs-lookup"><span data-stu-id="e157d-137">Name</span></span>                    | <span data-ttu-id="e157d-138">Type</span><span class="sxs-lookup"><span data-stu-id="e157d-138">Type</span></span>     | <span data-ttu-id="e157d-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="e157d-139">Required</span></span> | <span data-ttu-id="e157d-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e157d-140">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="e157d-141">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="e157d-141">**customer-tenant-id**</span></span>  | <span data-ttu-id="e157d-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="e157d-142">**guid**</span></span> | <span data-ttu-id="e157d-143">J</span><span class="sxs-lookup"><span data-stu-id="e157d-143">Y</span></span>        | <span data-ttu-id="e157d-144">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="e157d-144">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="e157d-145">**id voor abonnement**</span><span class="sxs-lookup"><span data-stu-id="e157d-145">**id-for-subscription**</span></span> | <span data-ttu-id="e157d-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="e157d-146">**guid**</span></span> | <span data-ttu-id="e157d-147">J</span><span class="sxs-lookup"><span data-stu-id="e157d-147">Y</span></span>        | <span data-ttu-id="e157d-148">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="e157d-148">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e157d-149">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e157d-149">Request headers</span></span>

<span data-ttu-id="e157d-150">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e157d-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e157d-151">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e157d-151">Request body</span></span>

<span data-ttu-id="e157d-152">Geen.</span><span class="sxs-lookup"><span data-stu-id="e157d-152">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e157d-153">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e157d-153">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription>/addons HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 429902e2-ea2f-4704-b8a0-27fc53c539ba
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
```

## <a name="rest-response"></a><span data-ttu-id="e157d-154">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e157d-154">REST response</span></span>

<span data-ttu-id="e157d-155">Als dit lukt, retourneert deze methode een verzameling resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="e157d-155">If successful, this method returns a collection of resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e157d-156">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="e157d-156">Response success and error codes</span></span>

<span data-ttu-id="e157d-157">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="e157d-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e157d-158">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e157d-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e157d-159">Zie [fout codes](error-codes.md)voor een volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="e157d-159">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e157d-160">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e157d-160">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 73754
Content-Type: application/json
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
MS-RequestId: 16fee928-dc2c-412f-adbb-871f68babf16
Date: Wed, 25 Nov 2015 05:50:45 GMT

{
    "totalCount": 37,
    "items": [{
        "id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
        "entitlementId": "42226ed6-070a-4e0f-b80c-4cdfB3e97aa7",
        "friendlyName": "Myofferpurchase",
        "quantity": 1,
        "unitType": "none",
        "creationDate": "2015-11-25T06: 41: 12Z",
        "effectiveStartDate": "2015-11-24T08: 00: 00Z",
        "commitmentEndDate": "2016-12-12T08: 00: 00Z",
        "status": "active",
        "autoRenewEnabled": false,
        "billingType": "none",
        "contractType": "subscription",
        "links": {
            "offer": {
                "uri": "/v1/offers/0CCA44D6-68E9-4762-94EE-31ECE98783B9",
                "method": "GET",
                "headers": []
            },
            "self": {
                "uri": "/subscriptions?key=<key>",
                "method": "GET",
                "headers": []
            }
        },
        "orderId": "6183db3d-6318-4e52-877e-25806e4971be",
        "attributes": {
            "etag": "<etag>",
            "objectType": "Subscription"
        }
    }],
    "attributes": {
        "objectType": "Collection"
    }
}
```
