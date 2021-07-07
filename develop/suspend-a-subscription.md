---
title: Een abonnement opschorten
description: Schort een abonnementsresource uit die overeenkomt met de klant- en abonnements-id vanwege fraude of niet-betaling. In het Partner Center kan deze bewerking worden uitgevoerd door eerst een klant te selecteren.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7dae7c3422a403c48a2b10424c4ae5dbdbc498ea
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547339"
---
# <a name="suspend-a-subscription"></a><span data-ttu-id="e8324-104">Een abonnement opschorten</span><span class="sxs-lookup"><span data-stu-id="e8324-104">Suspend a subscription</span></span>

<span data-ttu-id="e8324-105">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e8324-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e8324-106">Schort een [abonnementsresource](subscription-resources.md) uit die overeenkomt met de klant- en abonnements-id vanwege fraude of niet-betaling.</span><span class="sxs-lookup"><span data-stu-id="e8324-106">Suspends a [Subscription](subscription-resources.md) resource that matches the customer and subscription ID due to fraud or non-payment.</span></span>

<span data-ttu-id="e8324-107">In het Partner Center dashboard kunt u deze bewerking uitvoeren door eerst [een klant te selecteren.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="e8324-107">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="e8324-108">Selecteer vervolgens het abonnement in kwestie dat u een andere naam wilt geven.</span><span class="sxs-lookup"><span data-stu-id="e8324-108">Then, select the subscription in question that you wish to rename.</span></span> <span data-ttu-id="e8324-109">Als u wilt voltooien, kiest **u de knop Suspended** en selecteert u **vervolgens Submit.**</span><span class="sxs-lookup"><span data-stu-id="e8324-109">To finish, choose the **Suspended** button, then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e8324-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e8324-110">Prerequisites</span></span>

- <span data-ttu-id="e8324-111">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e8324-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e8324-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="e8324-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="e8324-113">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e8324-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e8324-114">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="e8324-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e8324-115">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="e8324-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e8324-116">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="e8324-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e8324-117">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="e8324-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e8324-118">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e8324-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="e8324-119">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="e8324-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="e8324-120">C\#</span><span class="sxs-lookup"><span data-stu-id="e8324-120">C\#</span></span>

<span data-ttu-id="e8324-121">Als u het abonnement van een klant wilt opschorten, moet u eerst [het abonnement op halen](get-a-subscription-by-id.md)en vervolgens de eigenschap Status van het [**abonnement**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) wijzigen.</span><span class="sxs-lookup"><span data-stu-id="e8324-121">To suspend a customer's subscription, first [Get the subscription](get-a-subscription-by-id.md), then change the subscription's [**Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) property.</span></span> <span data-ttu-id="e8324-122">Raadpleeg [SubscriptionStatus enumeration/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus) voor informatie over **statuscodes.**</span><span class="sxs-lookup"><span data-stu-id="e8324-122">For information on **Status** codes, consult [SubscriptionStatus enumeration/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span></span> <span data-ttu-id="e8324-123">Zodra de wijziging is aangebracht, gebruikt u de **verzameling IAggregatePartner.Customers** en roept u de **methode ById()** aan.</span><span class="sxs-lookup"><span data-stu-id="e8324-123">Once the change is made, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="e8324-124">Roep vervolgens de [**eigenschap Abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) aan, gevolgd door de [**methode ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="e8324-124">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="e8324-125">Vervolgens roept u de methode **Patch()** aan.</span><span class="sxs-lookup"><span data-stu-id="e8324-125">Then, finish by calling the **Patch()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// Subscription selectedSubscription;

updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(
   new Subscription()
   {
      Status = SubscriptionStatus.Suspended
   });
```

<span data-ttu-id="e8324-126">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="e8324-126">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="e8324-127">**Project:** PartnerSDK.FeatureSample-klasse: UpdateSubscription.cs </span><span class="sxs-lookup"><span data-stu-id="e8324-127">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="e8324-128">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e8324-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e8324-129">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e8324-129">Request syntax</span></span>

| <span data-ttu-id="e8324-130">Methode</span><span class="sxs-lookup"><span data-stu-id="e8324-130">Method</span></span>    | <span data-ttu-id="e8324-131">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e8324-131">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e8324-132">**Patch**</span><span class="sxs-lookup"><span data-stu-id="e8324-132">**PATCH**</span></span> | <span data-ttu-id="e8324-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e8324-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="e8324-134">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="e8324-134">URI parameter</span></span>

<span data-ttu-id="e8324-135">Deze tabel bevat de vereiste queryparameter om het abonnement op te schorten.</span><span class="sxs-lookup"><span data-stu-id="e8324-135">This table lists the required query parameter to suspend the subscription.</span></span>

| <span data-ttu-id="e8324-136">Naam</span><span class="sxs-lookup"><span data-stu-id="e8324-136">Name</span></span>                    | <span data-ttu-id="e8324-137">Type</span><span class="sxs-lookup"><span data-stu-id="e8324-137">Type</span></span>     | <span data-ttu-id="e8324-138">Vereist</span><span class="sxs-lookup"><span data-stu-id="e8324-138">Required</span></span> | <span data-ttu-id="e8324-139">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e8324-139">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="e8324-140">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="e8324-140">**customer-tenant-id**</span></span>  | <span data-ttu-id="e8324-141">**guid**</span><span class="sxs-lookup"><span data-stu-id="e8324-141">**guid**</span></span> | <span data-ttu-id="e8324-142">J</span><span class="sxs-lookup"><span data-stu-id="e8324-142">Y</span></span>        | <span data-ttu-id="e8324-143">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="e8324-143">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="e8324-144">**id-for-subscription**</span><span class="sxs-lookup"><span data-stu-id="e8324-144">**id-for-subscription**</span></span> | <span data-ttu-id="e8324-145">**guid**</span><span class="sxs-lookup"><span data-stu-id="e8324-145">**guid**</span></span> | <span data-ttu-id="e8324-146">J</span><span class="sxs-lookup"><span data-stu-id="e8324-146">Y</span></span>        | <span data-ttu-id="e8324-147">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="e8324-147">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e8324-148">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e8324-148">Request headers</span></span>

<span data-ttu-id="e8324-149">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e8324-149">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e8324-150">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e8324-150">Request body</span></span>

<span data-ttu-id="e8324-151">Een volledige **abonnementsresource** is vereist in de aanvraag body.</span><span class="sxs-lookup"><span data-stu-id="e8324-151">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="e8324-152">Zorg ervoor dat **de eigenschap Status** is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="e8324-152">Ensure that the **Status** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="e8324-153">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e8324-153">Request example</span></span>

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
    "Id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
    "FriendlyName": "nickname",
    "Quantity": 2,
    "UnitType": "none",
    "ParentSubscriptionId": null,
    "CreationDate": "2015-11-25T06:41:12Z",
    "EffectiveStartDate": "2015-11-24T08:00:00Z",
    "CommitmentEndDate": "2016-12-12T08:00:00Z",
    "Status": "suspended",
    "AutoRenewEnabled": false,
    "BillingType": "none",
    "PartnerId": null,
    "ContractType": "subscription",
    "OrderId": "6183db3d-6318-4e52-877e-25806e4971be",
    "Attributes": {
        "Etag": "<etag>",
        "ObjectType": "Subscription"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="e8324-154">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e8324-154">REST response</span></span>

<span data-ttu-id="e8324-155">Als dit lukt, retourneert deze methode [bijgewerkte eigenschappen van](subscription-resources.md) abonnementsresources in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="e8324-155">If successful, this method returns updated [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e8324-156">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e8324-156">Response success and error codes</span></span>

<span data-ttu-id="e8324-157">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e8324-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e8324-158">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e8324-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e8324-159">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="e8324-159">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e8324-160">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e8324-160">Response example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscriptionID> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-Contract-Version: v1
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "Id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
    "FriendlyName": "nickname",
    "Quantity": 2,
    "UnitType": "none",
    "ParentSubscriptionId": null,
    "CreationDate": "2015-11-25T06:41:12Z",
    "EffectiveStartDate": "2015-11-24T08:00:00Z",
    "CommitmentEndDate": "2016-12-12T08:00:00Z",
    "Status": "suspended",
    "AutoRenewEnabled": false,
    "BillingType": "none",
    "PartnerId": null,
    "ContractType": "subscription",
    "Links": {
        "Offer": {
            "Uri": "/v1/offers/0CCA44D6-68E9-4762-94EE-31ECE98783B9",
            "Method": "GET",
            "Headers": []
        },
        "Entitlement": {
            "Uri": "/entitlements?key=<key>",
            "Method": "GET",
            "Headers": []
        },
        "Self": {
            "Uri": "/subscriptions?key=<key>",
            "Method": "GET",
            "Headers": []
        }
    },
    "OrderId": "6183db3d-6318-4e52-877e-25806e4971be",
    "Attributes": {
        "Etag": "<etag>",
        "ObjectType": "Subscription"
    }
}
```
