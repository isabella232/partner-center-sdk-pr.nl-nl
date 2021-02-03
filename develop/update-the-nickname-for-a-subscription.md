---
title: De bijnaam voor een abonnement bijwerken
description: Hiermee wordt de beschrijvende naam of bijnaam van het abonnement van een klant bijgewerkt.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 57a9fec4b69d4a64128425ea58b4bb84d0d7dd54
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767476"
---
# <a name="update-the-nickname-for-a-subscription"></a><span data-ttu-id="848d2-103">De bijnaam voor een abonnement bijwerken</span><span class="sxs-lookup"><span data-stu-id="848d2-103">Update the nickname for a subscription</span></span>

<span data-ttu-id="848d2-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="848d2-104">**Applies To**</span></span>

- <span data-ttu-id="848d2-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="848d2-105">Partner Center</span></span>
- <span data-ttu-id="848d2-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="848d2-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="848d2-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="848d2-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="848d2-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="848d2-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="848d2-109">Hiermee wordt de beschrijvende naam of bijnaam van het [abonnement](subscription-resources.md)van een klant bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="848d2-109">Updates the friendly name or nickname for a customer's [Subscription](subscription-resources.md).</span></span> <span data-ttu-id="848d2-110">Deze naam wordt weer gegeven in het partner centrum om te helpen bij het onderscheiden van de abonnementen in het account van de klant.</span><span class="sxs-lookup"><span data-stu-id="848d2-110">This name appears in Partner Center to help differentiate the subscriptions in the customer's account.</span></span>

<span data-ttu-id="848d2-111">In het dash board van de partner centrum kan deze bewerking worden uitgevoerd door eerst [een klant te selecteren](get-a-customer-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="848d2-111">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="848d2-112">Selecteer vervolgens het abonnement waarvan u de naam wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="848d2-112">Then, select the subscription in question that you wish to rename.</span></span> <span data-ttu-id="848d2-113">Als u wilt volt ooien, wijzigt u de naam in het veld **bijnaam van abonnement** en selecteert u vervolgens **verzenden.**</span><span class="sxs-lookup"><span data-stu-id="848d2-113">To finish, change the name in the **Subscription nickname** field, then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="848d2-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="848d2-114">Prerequisites</span></span>

- <span data-ttu-id="848d2-115">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="848d2-115">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="848d2-116">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="848d2-116">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="848d2-117">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="848d2-117">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="848d2-118">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="848d2-118">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="848d2-119">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="848d2-119">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="848d2-120">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="848d2-120">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="848d2-121">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="848d2-121">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="848d2-122">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="848d2-122">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="848d2-123">Een abonnements-ID.</span><span class="sxs-lookup"><span data-stu-id="848d2-123">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="848d2-124">C\#</span><span class="sxs-lookup"><span data-stu-id="848d2-124">C\#</span></span>

<span data-ttu-id="848d2-125">Als u de bijnaam van het abonnement van een klant wilt bijwerken, moet u eerst [het abonnement ophalen](get-a-subscription-by-id.md)en vervolgens de eigenschap [**FriendlyName**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.friendlyname) van het abonnement wijzigen.</span><span class="sxs-lookup"><span data-stu-id="848d2-125">To update the nickname of a customer's subscription, first [Get the subscription](get-a-subscription-by-id.md), then change the subscription's [**FriendlyName**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.friendlyname) property.</span></span> <span data-ttu-id="848d2-126">Nadat de wijziging is aangebracht, gebruikt u de verzameling [**IPartner. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) en roept u de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="848d2-126">Once the change is made, use your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="848d2-127">Roep vervolgens de eigenschap [**abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) aan, gevolgd door de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) .</span><span class="sxs-lookup"><span data-stu-id="848d2-127">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="848d2-128">Voltooi vervolgens de methode [**patch ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.patch) .</span><span class="sxs-lookup"><span data-stu-id="848d2-128">Then, finish by calling the [**Patch()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.patch) method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var SelectedcustomerId as string;

ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.Get();
Subscription selectedSubscription = customerSubscriptions.Items.FirstOrDefault(sub => sub.Status == SubscriptionStatus.Active);

// Apply changes to subscription;

var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

<span data-ttu-id="848d2-129">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="848d2-129">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="848d2-130">**Project**: PartnerSDK. FeatureSamples- **klasse**: UpdateSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="848d2-130">**Project**: PartnerSDK.FeatureSamples **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="848d2-131">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="848d2-131">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="848d2-132">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="848d2-132">Request syntax</span></span>

| <span data-ttu-id="848d2-133">Methode</span><span class="sxs-lookup"><span data-stu-id="848d2-133">Method</span></span>    | <span data-ttu-id="848d2-134">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="848d2-134">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="848d2-135">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="848d2-135">**PATCH**</span></span> | <span data-ttu-id="848d2-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{id-for-Subscription} http/1.1</span><span class="sxs-lookup"><span data-stu-id="848d2-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="848d2-137">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="848d2-137">URI parameter</span></span>

<span data-ttu-id="848d2-138">Deze tabel bevat de vereiste query parameter voor het bijwerken van de bijnaam van het abonnement.</span><span class="sxs-lookup"><span data-stu-id="848d2-138">This table lists the required query parameter to update the subscription nickname.</span></span>

| <span data-ttu-id="848d2-139">Naam</span><span class="sxs-lookup"><span data-stu-id="848d2-139">Name</span></span>                    | <span data-ttu-id="848d2-140">Type</span><span class="sxs-lookup"><span data-stu-id="848d2-140">Type</span></span>     | <span data-ttu-id="848d2-141">Vereist</span><span class="sxs-lookup"><span data-stu-id="848d2-141">Required</span></span> | <span data-ttu-id="848d2-142">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="848d2-142">Description</span></span>                          |
|-------------------------|----------|----------|--------------------------------------|
| <span data-ttu-id="848d2-143">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="848d2-143">**customer-tenant-id**</span></span>  | <span data-ttu-id="848d2-144">**guid**</span><span class="sxs-lookup"><span data-stu-id="848d2-144">**guid**</span></span> | <span data-ttu-id="848d2-145">J</span><span class="sxs-lookup"><span data-stu-id="848d2-145">Y</span></span>        | <span data-ttu-id="848d2-146">De **klant-Tenant-id** (een GUID).</span><span class="sxs-lookup"><span data-stu-id="848d2-146">The **customer-tenant-id** (a GUID).</span></span> |
| <span data-ttu-id="848d2-147">**id voor abonnement**</span><span class="sxs-lookup"><span data-stu-id="848d2-147">**id-for-subscription**</span></span> | <span data-ttu-id="848d2-148">**guid**</span><span class="sxs-lookup"><span data-stu-id="848d2-148">**guid**</span></span> | <span data-ttu-id="848d2-149">J</span><span class="sxs-lookup"><span data-stu-id="848d2-149">Y</span></span>        | <span data-ttu-id="848d2-150">De abonnements-ID (een GUID).</span><span class="sxs-lookup"><span data-stu-id="848d2-150">The subscription ID (a GUID).</span></span>        |

### <a name="request-headers"></a><span data-ttu-id="848d2-151">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="848d2-151">Request headers</span></span>

<span data-ttu-id="848d2-152">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="848d2-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="848d2-153">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="848d2-153">Request body</span></span>

<span data-ttu-id="848d2-154">Een volledige **abonnements** resource is vereist in de aanvraag tekst.</span><span class="sxs-lookup"><span data-stu-id="848d2-154">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="848d2-155">Zorg ervoor dat de eigenschap **FriendlyName** is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="848d2-155">Ensure the **FriendlyName** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="848d2-156">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="848d2-156">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscriptionID> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "Id": "<subscriptionID>",
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
    OrderId": "6183db3d-6318-4e52-877e-25806e4971be",
    "Attributes": {
        "Etag": "<etag>",
        "ObjectType": "Subscription"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="848d2-157">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="848d2-157">REST response</span></span>

<span data-ttu-id="848d2-158">Als dit lukt, retourneert deze methode bijgewerkte eigenschappen van [abonnements](subscription-resources.md) bronnen in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="848d2-158">If successful, this method returns updated [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="848d2-159">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="848d2-159">Response success and error codes</span></span>

<span data-ttu-id="848d2-160">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="848d2-160">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="848d2-161">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="848d2-161">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="848d2-162">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="848d2-162">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="848d2-163">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="848d2-163">Response example</span></span>

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
    "Id": "<subscriptionID>",
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
