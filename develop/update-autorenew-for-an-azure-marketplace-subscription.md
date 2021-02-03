---
title: Automatisch verlengen bijwerken voor een abonnement op de commerciële marketplace
description: De eigenschap autorenew bijwerken voor een abonnements resource die overeenkomt met de klant-en abonnements-ID.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8dccec57901ea4ea429b74044e3b6c28178c43f6
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767456"
---
# <a name="update-autorenew-for-a-commercial-marketplace-subscription"></a><span data-ttu-id="43293-103">Automatisch verlengen bijwerken voor een abonnement op de commerciële marketplace</span><span class="sxs-lookup"><span data-stu-id="43293-103">Update autorenew for a commercial marketplace subscription</span></span>

<span data-ttu-id="43293-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="43293-104">**Applies To**</span></span>

- <span data-ttu-id="43293-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="43293-105">Partner Center</span></span>

<span data-ttu-id="43293-106">De eigenschap autorenew bijwerken voor een commerciële Marketplace- [abonnements](subscription-resources.md) resource die overeenkomt met de klant-en abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="43293-106">Update the autorenew property for a commercial marketplace [Subscription](subscription-resources.md) resource that matches the customer and subscription ID.</span></span>

<span data-ttu-id="43293-107">In het dash board van de partner centrum wordt deze bewerking uitgevoerd door eerst [een klant te selecteren](get-a-customer-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="43293-107">In the Partner Center dashboard, this operation is performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="43293-108">Selecteer vervolgens het abonnement dat u wilt bijwerken.</span><span class="sxs-lookup"><span data-stu-id="43293-108">Then, select the subscription that you wish to update.</span></span> <span data-ttu-id="43293-109">Schakel ten slotte de optie **automatisch vernieuwen** in en selecteer vervolgens **verzenden**.</span><span class="sxs-lookup"><span data-stu-id="43293-109">Finally, toggle the **Auto-renew** option, then select **Submit**.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="43293-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="43293-110">Prerequisites</span></span>

- <span data-ttu-id="43293-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="43293-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="43293-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="43293-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="43293-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="43293-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="43293-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="43293-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="43293-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="43293-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="43293-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="43293-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="43293-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="43293-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="43293-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="43293-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="43293-119">Een abonnements-ID.</span><span class="sxs-lookup"><span data-stu-id="43293-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="43293-120">C\#</span><span class="sxs-lookup"><span data-stu-id="43293-120">C\#</span></span>

<span data-ttu-id="43293-121">Als u het abonnement van een klant wilt bijwerken, moet u eerst [het abonnement ophalen](get-a-subscription-by-id.md)en vervolgens de eigenschap [**autoRenewEnabled**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.autoRenewEnabled) van het abonnement instellen.</span><span class="sxs-lookup"><span data-stu-id="43293-121">To update a customer's subscription, first [Get the subscription](get-a-subscription-by-id.md), then set the subscription's [**autoRenewEnabled**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.autoRenewEnabled) property.</span></span> <span data-ttu-id="43293-122">Nadat de wijziging is aangebracht, gebruikt u de verzameling **IAggregatePartner. Customers** en roept u de methode **ById ()** aan.</span><span class="sxs-lookup"><span data-stu-id="43293-122">Once the change is made, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="43293-123">Roep vervolgens de eigenschap [**abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) aan, gevolgd door de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) .</span><span class="sxs-lookup"><span data-stu-id="43293-123">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="43293-124">Voltooi vervolgens de methode **patch ()** .</span><span class="sxs-lookup"><span data-stu-id="43293-124">Then, finish by calling the **Patch()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// Subscription selectedSubscription;

// turn off auto renew.
selectedSubscription.AutoRenewEnabled = false;
var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

<span data-ttu-id="43293-125">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="43293-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="43293-126">**Project**: PartnerSDK. FeatureSample- **klasse**: UpdateSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="43293-126">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="43293-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="43293-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="43293-128">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="43293-128">Request syntax</span></span>

| <span data-ttu-id="43293-129">Methode</span><span class="sxs-lookup"><span data-stu-id="43293-129">Method</span></span>    | <span data-ttu-id="43293-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="43293-130">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="43293-131">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="43293-131">**PATCH**</span></span> | <span data-ttu-id="43293-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{id-for-Subscription} http/1.1</span><span class="sxs-lookup"><span data-stu-id="43293-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="43293-133">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="43293-133">URI parameter</span></span>

<span data-ttu-id="43293-134">Deze tabel bevat de vereiste query parameter om het abonnement te onderbreken.</span><span class="sxs-lookup"><span data-stu-id="43293-134">This table lists the required query parameter to suspend the subscription.</span></span>

| <span data-ttu-id="43293-135">Naam</span><span class="sxs-lookup"><span data-stu-id="43293-135">Name</span></span>                    | <span data-ttu-id="43293-136">Type</span><span class="sxs-lookup"><span data-stu-id="43293-136">Type</span></span>     | <span data-ttu-id="43293-137">Vereist</span><span class="sxs-lookup"><span data-stu-id="43293-137">Required</span></span> | <span data-ttu-id="43293-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="43293-138">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="43293-139">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="43293-139">**customer-tenant-id**</span></span>  | <span data-ttu-id="43293-140">**GPT**</span><span class="sxs-lookup"><span data-stu-id="43293-140">**GUID**</span></span> | <span data-ttu-id="43293-141">J</span><span class="sxs-lookup"><span data-stu-id="43293-141">Y</span></span>        | <span data-ttu-id="43293-142">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="43293-142">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="43293-143">**id voor abonnement**</span><span class="sxs-lookup"><span data-stu-id="43293-143">**id-for-subscription**</span></span> | <span data-ttu-id="43293-144">**GPT**</span><span class="sxs-lookup"><span data-stu-id="43293-144">**GUID**</span></span> | <span data-ttu-id="43293-145">J</span><span class="sxs-lookup"><span data-stu-id="43293-145">Y</span></span>        | <span data-ttu-id="43293-146">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="43293-146">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="43293-147">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="43293-147">Request headers</span></span>

<span data-ttu-id="43293-148">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="43293-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="43293-149">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="43293-149">Request body</span></span>

<span data-ttu-id="43293-150">Er is een volledige **abonnements** resource voor commerciële Marketplace vereist in de hoofd tekst van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="43293-150">A full commercial marketplace **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="43293-151">Zorg ervoor dat de eigenschap **AutoRenewEnabled** is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="43293-151">Ensure that the **AutoRenewEnabled** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="43293-152">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="43293-152">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="43293-153">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="43293-153">REST response</span></span>

<span data-ttu-id="43293-154">Als dit lukt, retourneert deze methode bijgewerkte eigenschappen van [abonnements](subscription-resources.md) bronnen in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="43293-154">If successful, this method returns updated [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="43293-155">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="43293-155">Response success and error codes</span></span>

<span data-ttu-id="43293-156">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="43293-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="43293-157">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="43293-157">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="43293-158">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="43293-158">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="43293-159">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="43293-159">Response example</span></span>

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
