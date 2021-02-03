---
title: Een abonnement op de commerciële marketplace annuleren
description: Meer informatie over het gebruik van partner Center-Api's voor het annuleren van een commerciële Marketplace-abonnements resource die overeenkomt met een klant en abonnements-ID.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 38708c17b31e39a5e7c436e0d76b4ebabbc3a801
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2020
ms.locfileid: "97767620"
---
# <a name="cancel-a-commercial-marketplace-subscription-using-partner-center-apis"></a><span data-ttu-id="973d0-103">Een abonnement op commerciële Marketplace annuleren met partner Center-Api's</span><span class="sxs-lookup"><span data-stu-id="973d0-103">Cancel a commercial marketplace subscription using Partner Center APIs</span></span>

<span data-ttu-id="973d0-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="973d0-104">**Applies to:**</span></span>

- <span data-ttu-id="973d0-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="973d0-105">Partner Center</span></span>

<span data-ttu-id="973d0-106">In dit artikel wordt beschreven hoe u partner Center API kunt gebruiken om een resource voor commerciële Marketplace- [abonnementen](subscription-resources.md) te annuleren die overeenkomt met de klant en de abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="973d0-106">This article describes how you can use Partner Center API to cancel a commercial marketplace [subscription](subscription-resources.md) resource that matches the customer and subscription ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="973d0-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="973d0-107">Prerequisites</span></span>

- <span data-ttu-id="973d0-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="973d0-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="973d0-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="973d0-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="973d0-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="973d0-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="973d0-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="973d0-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="973d0-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="973d0-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="973d0-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="973d0-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="973d0-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="973d0-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="973d0-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="973d0-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="973d0-116">Een abonnements-ID.</span><span class="sxs-lookup"><span data-stu-id="973d0-116">A subscription ID.</span></span>

## <a name="partner-center-dashboard-method"></a><span data-ttu-id="973d0-117">Dash board-methode partner centrum</span><span class="sxs-lookup"><span data-stu-id="973d0-117">Partner Center dashboard method</span></span>

<span data-ttu-id="973d0-118">Een abonnement op een commerciële Marketplace annuleren in het dash board van de partner centrum:</span><span class="sxs-lookup"><span data-stu-id="973d0-118">To cancel a commercial marketplace subscription in the Partner Center dashboard:</span></span>

1. <span data-ttu-id="973d0-119">[Selecteer een klant](get-a-customer-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="973d0-119">[Select a customer](get-a-customer-by-name.md).</span></span>

2. <span data-ttu-id="973d0-120">Selecteer het abonnement dat u wilt annuleren.</span><span class="sxs-lookup"><span data-stu-id="973d0-120">Select the subscription that you wish to cancel.</span></span>

3. <span data-ttu-id="973d0-121">Kies de optie **abonnement annuleren** en selecteer vervolgens **verzenden**.</span><span class="sxs-lookup"><span data-stu-id="973d0-121">Choose the **Cancel subscription** option, then select **Submit**.</span></span>

## <a name="c"></a><span data-ttu-id="973d0-122">C\#</span><span class="sxs-lookup"><span data-stu-id="973d0-122">C\#</span></span>

<span data-ttu-id="973d0-123">Het abonnement van een klant annuleren:</span><span class="sxs-lookup"><span data-stu-id="973d0-123">To cancel a customer's subscription:</span></span>

1. <span data-ttu-id="973d0-124">[Het abonnement ophalen op basis van de id](get-a-subscription-by-id.md).</span><span class="sxs-lookup"><span data-stu-id="973d0-124">[Get the subscription by ID](get-a-subscription-by-id.md).</span></span>

2. <span data-ttu-id="973d0-125">Wijzig de eigenschap [**status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) van het abonnement.</span><span class="sxs-lookup"><span data-stu-id="973d0-125">Change the subscription's [**Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) property.</span></span> <span data-ttu-id="973d0-126">Zie [SubscriptionStatus Enumeration (Engelstalig)](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus)voor meer informatie over **status** codes.</span><span class="sxs-lookup"><span data-stu-id="973d0-126">For information on **Status** codes, see [SubscriptionStatus enumeration](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span></span>

3. <span data-ttu-id="973d0-127">Nadat de wijziging is aangebracht, gebruikt u uw **`IAggregatePartner.Customers`** verzameling en roept u de methode **ById ()** aan.</span><span class="sxs-lookup"><span data-stu-id="973d0-127">After the change is made, use your **`IAggregatePartner.Customers`** collection and call the **ById()** method.</span></span>

4. <span data-ttu-id="973d0-128">Roep de eigenschap [**abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) aan, gevolgd door de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) .</span><span class="sxs-lookup"><span data-stu-id="973d0-128">Call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span>

5. <span data-ttu-id="973d0-129">Roep de methode **patch ()** aan.</span><span class="sxs-lookup"><span data-stu-id="973d0-129">Call the **Patch()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// Subscription selectedSubscription;

selectedSubscription.Status = SubscriptionStatus.Deleted;
var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

### <a name="sample-console-test-app"></a><span data-ttu-id="973d0-130">Voor beeld-console test-app</span><span class="sxs-lookup"><span data-stu-id="973d0-130">Sample console test app</span></span>

<span data-ttu-id="973d0-131">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="973d0-131">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="973d0-132">**Project**: PartnerSDK. FeatureSample- **klasse**: UpdateSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="973d0-132">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="973d0-133">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="973d0-133">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="973d0-134">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="973d0-134">Request syntax</span></span>

| <span data-ttu-id="973d0-135">Methode</span><span class="sxs-lookup"><span data-stu-id="973d0-135">Method</span></span>    | <span data-ttu-id="973d0-136">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="973d0-136">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="973d0-137">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="973d0-137">**PATCH**</span></span> | <span data-ttu-id="973d0-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{id-for-Subscription} http/1.1</span><span class="sxs-lookup"><span data-stu-id="973d0-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="973d0-139">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="973d0-139">URI parameter</span></span>

<span data-ttu-id="973d0-140">Deze tabel bevat de vereiste query parameter om het abonnement te onderbreken.</span><span class="sxs-lookup"><span data-stu-id="973d0-140">This table lists the required query parameter to suspend the subscription.</span></span>

| <span data-ttu-id="973d0-141">Naam</span><span class="sxs-lookup"><span data-stu-id="973d0-141">Name</span></span>                    | <span data-ttu-id="973d0-142">Type</span><span class="sxs-lookup"><span data-stu-id="973d0-142">Type</span></span>     | <span data-ttu-id="973d0-143">Vereist</span><span class="sxs-lookup"><span data-stu-id="973d0-143">Required</span></span> | <span data-ttu-id="973d0-144">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="973d0-144">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="973d0-145">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="973d0-145">**customer-tenant-id**</span></span>  | <span data-ttu-id="973d0-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="973d0-146">**guid**</span></span> | <span data-ttu-id="973d0-147">J</span><span class="sxs-lookup"><span data-stu-id="973d0-147">Y</span></span>        | <span data-ttu-id="973d0-148">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="973d0-148">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="973d0-149">**id voor abonnement**</span><span class="sxs-lookup"><span data-stu-id="973d0-149">**id-for-subscription**</span></span> | <span data-ttu-id="973d0-150">**guid**</span><span class="sxs-lookup"><span data-stu-id="973d0-150">**guid**</span></span> | <span data-ttu-id="973d0-151">J</span><span class="sxs-lookup"><span data-stu-id="973d0-151">Y</span></span>        | <span data-ttu-id="973d0-152">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="973d0-152">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="973d0-153">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="973d0-153">Request headers</span></span>

<span data-ttu-id="973d0-154">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="973d0-154">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="973d0-155">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="973d0-155">Request body</span></span>

<span data-ttu-id="973d0-156">Een volledige **abonnements** resource is vereist in de aanvraag tekst.</span><span class="sxs-lookup"><span data-stu-id="973d0-156">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="973d0-157">Zorg ervoor dat de eigenschap **status** is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="973d0-157">Ensure that the **Status** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="973d0-158">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="973d0-158">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
If-Match: <etag>
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "id": "6e7aa601-629e-461b-8933-0898c3cc3c7c",
    "offerId": "DZH318Z0BXWC:0001:DZH318Z0BMJX",
    "offerName": "offer Name",
    "friendlyName": "friendly Name",
    "quantity": 1,
    "unitType": "License(s)",
    "hasPurchasableAddons": false,
    "creationDate": "2019-01-04T01:00:12.6647304Z",
    "effectiveStartDate": "2019-01-09T00:21:45.9263727+00:00",
    "commitmentEndDate": "2019-02-08T00:21:45.9263727+00:00",
    "status": "deleted",
    "autoRenewEnabled": false,
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1M",
    "refundOptions": [{
        "type": "Full",
        "expiresAt": "2019-01-10T00:21:45.9263727+00:00"
    }],
    "isMicrosoftProduct": false,
    "partnerId": "",
    "contractType": "subscription",
    "publisherName": "publisher Name",
    "orderId": "ImxjLNL4_fOc-2KoyOxGTZcrlIquzls11",
    "attributes": {"objectType": "Subscription"},
}
```

## <a name="rest-response"></a><span data-ttu-id="973d0-159">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="973d0-159">REST response</span></span>

<span data-ttu-id="973d0-160">Als dit lukt, retourneert deze methode verwijderde eigenschappen van de [abonnements](subscription-resources.md) resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="973d0-160">If successful, this method returns deleted [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="973d0-161">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="973d0-161">Response success and error codes</span></span>

<span data-ttu-id="973d0-162">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="973d0-162">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="973d0-163">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="973d0-163">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="973d0-164">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="973d0-164">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="973d0-165">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="973d0-165">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1322
Content-Type: application/json; charset=utf-8
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
X-Locale: en-US

{
    "id": "6e7aa601-629e-461b-8933-0898c3cc3c7c",
    "offerId": "DZH318Z0BXWC:0001:DZH318Z0BMJX",
    "offerName": "offer Name",
    "friendlyName": "friendly Name",
    "quantity": 1,
    "unitType": "License(s)",
    "hasPurchasableAddons": false,
    "creationDate": "2019-01-04T01:00:12.6647304Z",
    "effectiveStartDate": "2019-01-09T00:21:45.9263727+00:00",
    "commitmentEndDate": "2019-02-08T00:21:45.9263727+00:00",
    "status": "deleted",
    "autoRenewEnabled": false,
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1M",
    "refundOptions": [
        {
            "type": "Full",
            "expiresAt": "2019-01-10T00:21:45.9263727+00:00"
        }
    ],
    "isMicrosoftProduct": false,
    "partnerId": "",
    "contractType": "subscription",
    "links": {
        "product": {
            "uri": "/products/DZH318Z0BXWC?country=US",
            "method": "GET",
            "headers": []
        },
        "sku": {
            "uri": "/products/DZH318Z0BXWC/skus/0001?country=US",
            "method": "GET",
            "headers": []
        },
        "availability": {
            "uri": "/products/DZH318Z0BXWC/skus/0001/availabilities/DZH318Z0BMJX?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/5921f00a-32c0-4457-aaa1-e8018c650895/subscriptions/6e7aa601-629e-461b-8933-0898c3cc3c7c",
            "method": "GET",
            "headers": []
        }
    },
    "publisherName": "publishe rName",
    "orderId": "ImxjLNL4_fOc-2KoyOxGTZcrlIquzls11",
    "attributes": {
        "etag": "",
        "objectType": "Subscription"
    }
}
```
