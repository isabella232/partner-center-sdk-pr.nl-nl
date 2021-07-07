---
title: Een opgeschort abonnement opnieuw activeren
description: Een abonnement dat eerder is opgeschort voor niet-vooruitbetaling opnieuw activeren. In het Partner Center dashboard kunt u deze bewerking uitvoeren door eerst een klant te selecteren.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c2b6e3574119f9c645cc3f730047d2a23484ad8a
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547704"
---
# <a name="reactivate-a-suspended-subscription"></a><span data-ttu-id="6bade-104">Een opgeschort abonnement opnieuw activeren</span><span class="sxs-lookup"><span data-stu-id="6bade-104">Reactivate a suspended subscription</span></span>

<span data-ttu-id="6bade-105">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6bade-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6bade-106">Een abonnement dat [eerder](subscription-resources.md) is opgeschort voor niet-vooruitbetaling opnieuw activeren.</span><span class="sxs-lookup"><span data-stu-id="6bade-106">Reactivates a [Subscription](subscription-resources.md) that was previously suspended for nonpayment.</span></span>

<span data-ttu-id="6bade-107">In het Partner Center dashboard kunt u deze bewerking uitvoeren door eerst [een klant te selecteren.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="6bade-107">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="6bade-108">Selecteer vervolgens het abonnement in kwestie dat u een andere naam wilt geven.</span><span class="sxs-lookup"><span data-stu-id="6bade-108">Then, select the subscription in question that you wish to rename.</span></span> <span data-ttu-id="6bade-109">Als u wilt voltooien, kiest **u de knop** Actief en selecteert u vervolgens **Verzenden.**</span><span class="sxs-lookup"><span data-stu-id="6bade-109">To finish, choose the **Active** button, then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6bade-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6bade-110">Prerequisites</span></span>

- <span data-ttu-id="6bade-111">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="6bade-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6bade-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="6bade-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="6bade-113">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6bade-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="6bade-114">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="6bade-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="6bade-115">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="6bade-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="6bade-116">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="6bade-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="6bade-117">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="6bade-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="6bade-118">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6bade-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="6bade-119">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="6bade-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="6bade-120">C\#</span><span class="sxs-lookup"><span data-stu-id="6bade-120">C\#</span></span>

<span data-ttu-id="6bade-121">Als u het abonnement van een klant opnieuw wilt activeren, moet u eerst [het abonnement](get-a-subscription-by-id.md)op halen en vervolgens de eigenschap Status van [**het abonnement**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) wijzigen.</span><span class="sxs-lookup"><span data-stu-id="6bade-121">To reactivate a customer's subscription, first [Get the subscription](get-a-subscription-by-id.md), then change the subscription's [**Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) property.</span></span> <span data-ttu-id="6bade-122">Raadpleeg [SubscriptionStatus enumeration/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus) voor informatie over statuscodes. </span><span class="sxs-lookup"><span data-stu-id="6bade-122">For information on **Status** codes, consult [SubscriptionStatus enumeration/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span></span> <span data-ttu-id="6bade-123">Zodra de wijziging is aangebracht, gebruikt u de [**verzameling IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) en roept u de [**methode ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="6bade-123">Once the change is made, use your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="6bade-124">Roep vervolgens de [**eigenschap Abonnementen aan,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) gevolgd door de [**methode ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="6bade-124">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="6bade-125">Vervolgens roept u de methode [**Patch()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.patch) aan.</span><span class="sxs-lookup"><span data-stu-id="6bade-125">Then, finish by calling the [**Patch()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.patch) method.</span></span>

``` csharp
// IPartner partnerOperations;
// var selectedCustomer as Customer;
// var selectedSubscription as Subscription;

updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(
   new Subscription()
   {
      Status = SubscriptionStatus.Active
   });

```

<span data-ttu-id="6bade-126">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="6bade-126">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="6bade-127">**Project:** FeatureSamplesApplication.</span><span class="sxs-lookup"><span data-stu-id="6bade-127">**Project**: FeatureSamplesApplication.</span></span> <span data-ttu-id="6bade-128">**Klasse**: UpdateSubscription</span><span class="sxs-lookup"><span data-stu-id="6bade-128">**Class**: UpdateSubscription</span></span>

## <a name="rest-request"></a><span data-ttu-id="6bade-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="6bade-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6bade-130">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="6bade-130">Request syntax</span></span>

| <span data-ttu-id="6bade-131">Methode</span><span class="sxs-lookup"><span data-stu-id="6bade-131">Method</span></span>    | <span data-ttu-id="6bade-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="6bade-132">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6bade-133">**Patch**</span><span class="sxs-lookup"><span data-stu-id="6bade-133">**PATCH**</span></span> | <span data-ttu-id="6bade-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6bade-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="6bade-135">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="6bade-135">URI parameter</span></span>

<span data-ttu-id="6bade-136">Deze tabel bevat de vereiste queryparameter om het abonnement opnieuw te activeren.</span><span class="sxs-lookup"><span data-stu-id="6bade-136">This table lists the required query parameter to reactivate the subscription.</span></span>

| <span data-ttu-id="6bade-137">Naam</span><span class="sxs-lookup"><span data-stu-id="6bade-137">Name</span></span>                    | <span data-ttu-id="6bade-138">Type</span><span class="sxs-lookup"><span data-stu-id="6bade-138">Type</span></span>     | <span data-ttu-id="6bade-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="6bade-139">Required</span></span> | <span data-ttu-id="6bade-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6bade-140">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="6bade-141">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="6bade-141">**customer-tenant-id**</span></span>  | <span data-ttu-id="6bade-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="6bade-142">**guid**</span></span> | <span data-ttu-id="6bade-143">J</span><span class="sxs-lookup"><span data-stu-id="6bade-143">Y</span></span>        | <span data-ttu-id="6bade-144">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="6bade-144">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="6bade-145">**id-for-subscription**</span><span class="sxs-lookup"><span data-stu-id="6bade-145">**id-for-subscription**</span></span> | <span data-ttu-id="6bade-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="6bade-146">**guid**</span></span> | <span data-ttu-id="6bade-147">J</span><span class="sxs-lookup"><span data-stu-id="6bade-147">Y</span></span>        | <span data-ttu-id="6bade-148">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="6bade-148">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="6bade-149">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="6bade-149">Request headers</span></span>

<span data-ttu-id="6bade-150">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="6bade-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6bade-151">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="6bade-151">Request body</span></span>

<span data-ttu-id="6bade-152">Een volledige **abonnementsresource** is vereist in de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="6bade-152">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="6bade-153">Zorg ervoor dat **de eigenschap Status** is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="6bade-153">Ensure that the **Status** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="6bade-154">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6bade-154">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
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
    "Status": "active",
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

## <a name="rest-response"></a><span data-ttu-id="6bade-155">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="6bade-155">REST response</span></span>

<span data-ttu-id="6bade-156">Als dit lukt, retourneert deze methode [bijgewerkte eigenschappen van](subscription-resources.md) abonnementsresources in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="6bade-156">If successful, this method returns updated [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6bade-157">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="6bade-157">Response success and error codes</span></span>

<span data-ttu-id="6bade-158">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="6bade-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6bade-159">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="6bade-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6bade-160">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="6bade-160">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6bade-161">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="6bade-161">Response example</span></span>

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
    "Status": "active",
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
