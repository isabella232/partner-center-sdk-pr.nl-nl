---
title: Automatisch verlengen bijwerken voor een abonnement op de commerciële marketplace
description: Werk de eigenschap autorenew bij voor een abonnementsresource die overeenkomt met de klant- en abonnements-id.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: cc0b4c4bff5e8762ffcc2552b2e9e36bcf93686c
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446663"
---
# <a name="update-autorenew-for-a-commercial-marketplace-subscription"></a><span data-ttu-id="8526a-103">Automatisch verlengen bijwerken voor een abonnement op de commerciële marketplace</span><span class="sxs-lookup"><span data-stu-id="8526a-103">Update autorenew for a commercial marketplace subscription</span></span>

<span data-ttu-id="8526a-104">Werk de eigenschap autorenew bij voor een commerciële [marketplace-abonnementsresource](subscription-resources.md) die overeenkomt met de klant- en abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="8526a-104">Update the autorenew property for a commercial marketplace [Subscription](subscription-resources.md) resource that matches the customer and subscription ID.</span></span>

<span data-ttu-id="8526a-105">In het Partner Center dashboard wordt deze bewerking uitgevoerd door eerst [een klant te selecteren.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="8526a-105">In the Partner Center dashboard, this operation is performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="8526a-106">Selecteer vervolgens het abonnement dat u wilt bijwerken.</span><span class="sxs-lookup"><span data-stu-id="8526a-106">Then, select the subscription that you wish to update.</span></span> <span data-ttu-id="8526a-107">Schakel ten slotte de optie **Automatisch verlengen** in en selecteer **verzenden.**</span><span class="sxs-lookup"><span data-stu-id="8526a-107">Finally, toggle the **Auto-renew** option, then select **Submit**.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8526a-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="8526a-108">Prerequisites</span></span>

- <span data-ttu-id="8526a-109">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8526a-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8526a-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="8526a-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="8526a-111">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8526a-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="8526a-112">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="8526a-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="8526a-113">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="8526a-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="8526a-114">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="8526a-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="8526a-115">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="8526a-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="8526a-116">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8526a-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="8526a-117">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="8526a-117">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="8526a-118">C\#</span><span class="sxs-lookup"><span data-stu-id="8526a-118">C\#</span></span>

<span data-ttu-id="8526a-119">Als u het abonnement van een klant wilt bijwerken, moet u eerst [het](get-a-subscription-by-id.md)abonnement downloaden en vervolgens de eigenschap [**autoRenewEnabled van het abonnement**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.autoRenewEnabled) instellen.</span><span class="sxs-lookup"><span data-stu-id="8526a-119">To update a customer's subscription, first [Get the subscription](get-a-subscription-by-id.md), then set the subscription's [**autoRenewEnabled**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.autoRenewEnabled) property.</span></span> <span data-ttu-id="8526a-120">Zodra de wijziging is aangebracht, gebruikt u de **verzameling IAggregatePartner.Customers** en roept u de **methode ById()** aan.</span><span class="sxs-lookup"><span data-stu-id="8526a-120">Once the change is made, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="8526a-121">Roep vervolgens de [**eigenschap Abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) aan, gevolgd door de [**methode ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="8526a-121">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="8526a-122">Vervolgens roept u de methode **Patch()** aan.</span><span class="sxs-lookup"><span data-stu-id="8526a-122">Then, finish by calling the **Patch()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// Subscription selectedSubscription;

// turn off auto renew.
selectedSubscription.AutoRenewEnabled = false;
var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

<span data-ttu-id="8526a-123">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="8526a-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="8526a-124">**Project:** PartnerSDK.FeatureSample-klasse: UpdateSubscription.cs </span><span class="sxs-lookup"><span data-stu-id="8526a-124">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="8526a-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="8526a-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8526a-126">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="8526a-126">Request syntax</span></span>

| <span data-ttu-id="8526a-127">Methode</span><span class="sxs-lookup"><span data-stu-id="8526a-127">Method</span></span>    | <span data-ttu-id="8526a-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="8526a-128">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8526a-129">**Patch**</span><span class="sxs-lookup"><span data-stu-id="8526a-129">**PATCH**</span></span> | <span data-ttu-id="8526a-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8526a-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="8526a-131">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="8526a-131">URI parameter</span></span>

<span data-ttu-id="8526a-132">Deze tabel bevat de vereiste queryparameter om het abonnement op te schorten.</span><span class="sxs-lookup"><span data-stu-id="8526a-132">This table lists the required query parameter to suspend the subscription.</span></span>

| <span data-ttu-id="8526a-133">Naam</span><span class="sxs-lookup"><span data-stu-id="8526a-133">Name</span></span>                    | <span data-ttu-id="8526a-134">Type</span><span class="sxs-lookup"><span data-stu-id="8526a-134">Type</span></span>     | <span data-ttu-id="8526a-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="8526a-135">Required</span></span> | <span data-ttu-id="8526a-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8526a-136">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="8526a-137">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="8526a-137">**customer-tenant-id**</span></span>  | <span data-ttu-id="8526a-138">**Guid**</span><span class="sxs-lookup"><span data-stu-id="8526a-138">**GUID**</span></span> | <span data-ttu-id="8526a-139">J</span><span class="sxs-lookup"><span data-stu-id="8526a-139">Y</span></span>        | <span data-ttu-id="8526a-140">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="8526a-140">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="8526a-141">**id-for-subscription**</span><span class="sxs-lookup"><span data-stu-id="8526a-141">**id-for-subscription**</span></span> | <span data-ttu-id="8526a-142">**Guid**</span><span class="sxs-lookup"><span data-stu-id="8526a-142">**GUID**</span></span> | <span data-ttu-id="8526a-143">J</span><span class="sxs-lookup"><span data-stu-id="8526a-143">Y</span></span>        | <span data-ttu-id="8526a-144">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="8526a-144">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8526a-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="8526a-145">Request headers</span></span>

<span data-ttu-id="8526a-146">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="8526a-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8526a-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="8526a-147">Request body</span></span>

<span data-ttu-id="8526a-148">Een volledige commerciële **marketplace-abonnementsresource** is vereist in de aanvraag body.</span><span class="sxs-lookup"><span data-stu-id="8526a-148">A full commercial marketplace **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="8526a-149">Zorg ervoor dat **de eigenschap AutoRenewEnabled** is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="8526a-149">Ensure that the **AutoRenewEnabled** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="8526a-150">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="8526a-150">Request example</span></span>

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
    "status": "active",
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

## <a name="rest-response"></a><span data-ttu-id="8526a-151">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="8526a-151">REST response</span></span>

<span data-ttu-id="8526a-152">Als dit lukt, retourneert deze methode [bijgewerkte eigenschappen van](subscription-resources.md) abonnementsresources in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="8526a-152">If successful, this method returns updated [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8526a-153">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="8526a-153">Response success and error codes</span></span>

<span data-ttu-id="8526a-154">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="8526a-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8526a-155">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="8526a-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8526a-156">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="8526a-156">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8526a-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="8526a-157">Response example</span></span>

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
    "status": "active",
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
