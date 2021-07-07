---
title: De bijnaam voor een abonnement bijwerken
description: Werkt de gebruiksvriendelijke naam of bijnaam voor het abonnement van een klant bij.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 195a85fcf29b3e4c9fe0e578d4d8cb80ca068c40
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530001"
---
# <a name="update-the-nickname-for-a-subscription"></a><span data-ttu-id="a2878-103">De bijnaam voor een abonnement bijwerken</span><span class="sxs-lookup"><span data-stu-id="a2878-103">Update the nickname for a subscription</span></span>

<span data-ttu-id="a2878-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="a2878-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="a2878-105">Werkt de gebruiksvriendelijke naam of bijnaam voor het abonnement van een klant [bij.](subscription-resources.md)</span><span class="sxs-lookup"><span data-stu-id="a2878-105">Updates the friendly name or nickname for a customer's [Subscription](subscription-resources.md).</span></span> <span data-ttu-id="a2878-106">Deze naam wordt weergegeven in Partner Center om de abonnementen in het account van de klant te onderscheiden.</span><span class="sxs-lookup"><span data-stu-id="a2878-106">This name appears in Partner Center to help differentiate the subscriptions in the customer's account.</span></span>

<span data-ttu-id="a2878-107">In het Partner Center dashboard kunt u deze bewerking uitvoeren door eerst [een klant te selecteren.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="a2878-107">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="a2878-108">Selecteer vervolgens het abonnement in kwestie dat u de naam wilt geven.</span><span class="sxs-lookup"><span data-stu-id="a2878-108">Then, select the subscription in question that you wish to rename.</span></span> <span data-ttu-id="a2878-109">Als u wilt voltooien, wijzigt u de naam in **het veld Bijnaam** van abonnement en selecteert u vervolgens **Verzenden.**</span><span class="sxs-lookup"><span data-stu-id="a2878-109">To finish, change the name in the **Subscription nickname** field, then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a2878-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a2878-110">Prerequisites</span></span>

- <span data-ttu-id="a2878-111">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a2878-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a2878-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="a2878-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="a2878-113">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a2878-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="a2878-114">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="a2878-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="a2878-115">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="a2878-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="a2878-116">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="a2878-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="a2878-117">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="a2878-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="a2878-118">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a2878-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="a2878-119">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="a2878-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="a2878-120">C\#</span><span class="sxs-lookup"><span data-stu-id="a2878-120">C\#</span></span>

<span data-ttu-id="a2878-121">Als u de bijnaam van het abonnement van een klant wilt bijwerken, moet u eerst het abonnement downloaden [en](get-a-subscription-by-id.md)vervolgens de eigenschap [**FriendlyName van het abonnement**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.friendlyname) wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a2878-121">To update the nickname of a customer's subscription, first [Get the subscription](get-a-subscription-by-id.md), then change the subscription's [**FriendlyName**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.friendlyname) property.</span></span> <span data-ttu-id="a2878-122">Zodra de wijziging is aangebracht, gebruikt u de [**verzameling IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) en roept u de [**methode ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="a2878-122">Once the change is made, use your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="a2878-123">Roep vervolgens de [**eigenschap Abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) aan, gevolgd door de [**methode ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="a2878-123">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="a2878-124">Vervolgens roept u de methode [**Patch()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.patch) aan.</span><span class="sxs-lookup"><span data-stu-id="a2878-124">Then, finish by calling the [**Patch()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.patch) method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var SelectedcustomerId as string;

ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.Get();
Subscription selectedSubscription = customerSubscriptions.Items.FirstOrDefault(sub => sub.Status == SubscriptionStatus.Active);

// Apply changes to subscription;

var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

<span data-ttu-id="a2878-125">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="a2878-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="a2878-126">**Project:** Klasse PartnerSDK.FeatureSamples: UpdateSubscription.cs </span><span class="sxs-lookup"><span data-stu-id="a2878-126">**Project**: PartnerSDK.FeatureSamples **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="a2878-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="a2878-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a2878-128">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="a2878-128">Request syntax</span></span>

| <span data-ttu-id="a2878-129">Methode</span><span class="sxs-lookup"><span data-stu-id="a2878-129">Method</span></span>    | <span data-ttu-id="a2878-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="a2878-130">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a2878-131">**Patch**</span><span class="sxs-lookup"><span data-stu-id="a2878-131">**PATCH**</span></span> | <span data-ttu-id="a2878-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a2878-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="a2878-133">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="a2878-133">URI parameter</span></span>

<span data-ttu-id="a2878-134">Deze tabel bevat de vereiste queryparameter om de bijnaam van het abonnement bij te werken.</span><span class="sxs-lookup"><span data-stu-id="a2878-134">This table lists the required query parameter to update the subscription nickname.</span></span>

| <span data-ttu-id="a2878-135">Naam</span><span class="sxs-lookup"><span data-stu-id="a2878-135">Name</span></span>                    | <span data-ttu-id="a2878-136">Type</span><span class="sxs-lookup"><span data-stu-id="a2878-136">Type</span></span>     | <span data-ttu-id="a2878-137">Vereist</span><span class="sxs-lookup"><span data-stu-id="a2878-137">Required</span></span> | <span data-ttu-id="a2878-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a2878-138">Description</span></span>                          |
|-------------------------|----------|----------|--------------------------------------|
| <span data-ttu-id="a2878-139">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="a2878-139">**customer-tenant-id**</span></span>  | <span data-ttu-id="a2878-140">**guid**</span><span class="sxs-lookup"><span data-stu-id="a2878-140">**guid**</span></span> | <span data-ttu-id="a2878-141">J</span><span class="sxs-lookup"><span data-stu-id="a2878-141">Y</span></span>        | <span data-ttu-id="a2878-142">De **klant-tenant-id** (een GUID).</span><span class="sxs-lookup"><span data-stu-id="a2878-142">The **customer-tenant-id** (a GUID).</span></span> |
| <span data-ttu-id="a2878-143">**id-for-subscription**</span><span class="sxs-lookup"><span data-stu-id="a2878-143">**id-for-subscription**</span></span> | <span data-ttu-id="a2878-144">**guid**</span><span class="sxs-lookup"><span data-stu-id="a2878-144">**guid**</span></span> | <span data-ttu-id="a2878-145">J</span><span class="sxs-lookup"><span data-stu-id="a2878-145">Y</span></span>        | <span data-ttu-id="a2878-146">De abonnements-id (een GUID).</span><span class="sxs-lookup"><span data-stu-id="a2878-146">The subscription ID (a GUID).</span></span>        |

### <a name="request-headers"></a><span data-ttu-id="a2878-147">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="a2878-147">Request headers</span></span>

<span data-ttu-id="a2878-148">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="a2878-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a2878-149">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="a2878-149">Request body</span></span>

<span data-ttu-id="a2878-150">Een volledige **abonnementsresource** is vereist in de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="a2878-150">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="a2878-151">Zorg ervoor **dat de eigenschap FriendlyName** is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="a2878-151">Ensure the **FriendlyName** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="a2878-152">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="a2878-152">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="a2878-153">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="a2878-153">REST response</span></span>

<span data-ttu-id="a2878-154">Als dit lukt, retourneert deze methode [bijgewerkte eigenschappen van](subscription-resources.md) abonnementsresources in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="a2878-154">If successful, this method returns updated [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a2878-155">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="a2878-155">Response success and error codes</span></span>

<span data-ttu-id="a2878-156">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="a2878-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a2878-157">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="a2878-157">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a2878-158">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="a2878-158">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="a2878-159">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="a2878-159">Response example</span></span>

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
