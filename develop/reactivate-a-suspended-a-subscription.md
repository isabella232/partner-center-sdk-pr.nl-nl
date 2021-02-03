---
title: Een opgeschort abonnement opnieuw activeren
description: Hiermee wordt een abonnement dat eerder is geschorst voor niet-betaling opnieuw geactiveerd. In het dash board van de partner centrum kan deze bewerking worden uitgevoerd door eerst een klant te selecteren.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 17c63e9c6d4c9e111bfea28e97319696534fa122
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767466"
---
# <a name="reactivate-a-suspended-subscription"></a><span data-ttu-id="05493-103">Een opgeschort abonnement opnieuw activeren</span><span class="sxs-lookup"><span data-stu-id="05493-103">Reactivate a suspended subscription</span></span>

<span data-ttu-id="05493-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="05493-104">**Applies To**</span></span>

- <span data-ttu-id="05493-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="05493-105">Partner Center</span></span>
- <span data-ttu-id="05493-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="05493-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="05493-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="05493-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="05493-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="05493-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="05493-109">Hiermee wordt een [abonnement](subscription-resources.md) dat eerder is geschorst voor niet-betaling opnieuw geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="05493-109">Reactivates a [Subscription](subscription-resources.md) that was previously suspended for nonpayment.</span></span>

<span data-ttu-id="05493-110">In het dash board van de partner centrum kan deze bewerking worden uitgevoerd door eerst [een klant te selecteren](get-a-customer-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="05493-110">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="05493-111">Selecteer vervolgens het abonnement waarvan u de naam wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="05493-111">Then, select the subscription in question that you wish to rename.</span></span> <span data-ttu-id="05493-112">Als u klaar bent, kiest u de knop **actief** en selecteert u vervolgens **verzenden.**</span><span class="sxs-lookup"><span data-stu-id="05493-112">To finish, choose the **Active** button, then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="05493-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="05493-113">Prerequisites</span></span>

- <span data-ttu-id="05493-114">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="05493-114">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="05493-115">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="05493-115">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="05493-116">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="05493-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="05493-117">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="05493-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="05493-118">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="05493-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="05493-119">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="05493-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="05493-120">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="05493-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="05493-121">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="05493-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="05493-122">Een abonnements-ID.</span><span class="sxs-lookup"><span data-stu-id="05493-122">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="05493-123">C\#</span><span class="sxs-lookup"><span data-stu-id="05493-123">C\#</span></span>

<span data-ttu-id="05493-124">Als u het abonnement van een klant opnieuw wilt activeren, moet u eerst [het abonnement ophalen](get-a-subscription-by-id.md)en vervolgens de eigenschap [**status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) van het abonnement wijzigen.</span><span class="sxs-lookup"><span data-stu-id="05493-124">To reactivate a customer's subscription, first [Get the subscription](get-a-subscription-by-id.md), then change the subscription's [**Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) property.</span></span> <span data-ttu-id="05493-125">Voor informatie over **status** codes raadpleegt u [SubscriptionStatus Enumeration/DotNet/API/micro soft. Store. partnercenter. Models. abonnementen. SubscriptionStatus).</span><span class="sxs-lookup"><span data-stu-id="05493-125">For information on **Status** codes, consult [SubscriptionStatus enumeration/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span></span> <span data-ttu-id="05493-126">Nadat de wijziging is aangebracht, gebruikt u de verzameling [**IPartner. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) en roept u de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="05493-126">Once the change is made, use your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="05493-127">Roep vervolgens de eigenschap [**abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) aan, gevolgd door de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) .</span><span class="sxs-lookup"><span data-stu-id="05493-127">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="05493-128">Voltooi vervolgens de methode [**patch ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.patch) .</span><span class="sxs-lookup"><span data-stu-id="05493-128">Then, finish by calling the [**Patch()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.patch) method.</span></span>

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

<span data-ttu-id="05493-129">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="05493-129">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="05493-130">**Project**: FeatureSamplesApplication.</span><span class="sxs-lookup"><span data-stu-id="05493-130">**Project**: FeatureSamplesApplication.</span></span> <span data-ttu-id="05493-131">**Klasse**: UpdateSubscription</span><span class="sxs-lookup"><span data-stu-id="05493-131">**Class**: UpdateSubscription</span></span>

## <a name="rest-request"></a><span data-ttu-id="05493-132">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="05493-132">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="05493-133">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="05493-133">Request syntax</span></span>

| <span data-ttu-id="05493-134">Methode</span><span class="sxs-lookup"><span data-stu-id="05493-134">Method</span></span>    | <span data-ttu-id="05493-135">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="05493-135">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="05493-136">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="05493-136">**PATCH**</span></span> | <span data-ttu-id="05493-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{id-for-Subscription} http/1.1</span><span class="sxs-lookup"><span data-stu-id="05493-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="05493-138">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="05493-138">URI parameter</span></span>

<span data-ttu-id="05493-139">Deze tabel bevat de vereiste query parameter om het abonnement opnieuw te activeren.</span><span class="sxs-lookup"><span data-stu-id="05493-139">This table lists the required query parameter to reactivate the subscription.</span></span>

| <span data-ttu-id="05493-140">Naam</span><span class="sxs-lookup"><span data-stu-id="05493-140">Name</span></span>                    | <span data-ttu-id="05493-141">Type</span><span class="sxs-lookup"><span data-stu-id="05493-141">Type</span></span>     | <span data-ttu-id="05493-142">Vereist</span><span class="sxs-lookup"><span data-stu-id="05493-142">Required</span></span> | <span data-ttu-id="05493-143">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="05493-143">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="05493-144">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="05493-144">**customer-tenant-id**</span></span>  | <span data-ttu-id="05493-145">**guid**</span><span class="sxs-lookup"><span data-stu-id="05493-145">**guid**</span></span> | <span data-ttu-id="05493-146">J</span><span class="sxs-lookup"><span data-stu-id="05493-146">Y</span></span>        | <span data-ttu-id="05493-147">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="05493-147">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="05493-148">**id voor abonnement**</span><span class="sxs-lookup"><span data-stu-id="05493-148">**id-for-subscription**</span></span> | <span data-ttu-id="05493-149">**guid**</span><span class="sxs-lookup"><span data-stu-id="05493-149">**guid**</span></span> | <span data-ttu-id="05493-150">J</span><span class="sxs-lookup"><span data-stu-id="05493-150">Y</span></span>        | <span data-ttu-id="05493-151">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="05493-151">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="05493-152">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="05493-152">Request headers</span></span>

<span data-ttu-id="05493-153">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="05493-153">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="05493-154">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="05493-154">Request body</span></span>

<span data-ttu-id="05493-155">Een volledige **abonnements** resource is vereist in de aanvraag tekst.</span><span class="sxs-lookup"><span data-stu-id="05493-155">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="05493-156">Zorg ervoor dat de eigenschap **status** is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="05493-156">Ensure that the **Status** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="05493-157">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="05493-157">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="05493-158">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="05493-158">REST response</span></span>

<span data-ttu-id="05493-159">Als dit lukt, retourneert deze methode bijgewerkte eigenschappen van [abonnements](subscription-resources.md) bronnen in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="05493-159">If successful, this method returns updated [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="05493-160">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="05493-160">Response success and error codes</span></span>

<span data-ttu-id="05493-161">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="05493-161">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="05493-162">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="05493-162">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="05493-163">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="05493-163">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="05493-164">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="05493-164">Response example</span></span>

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
