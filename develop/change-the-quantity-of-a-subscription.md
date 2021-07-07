---
title: De hoeveelheid van een abonnement wijzigen
description: Meer informatie over het gebruik Partner Center API's om het aantal licenties voor een klantabonnement te wijzigen. U kunt dit ook doen in het Partner Center dashboard.
ms.date: 06/05/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d57ece4dd19ef2852f39130916222c54a9ccc85a
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974094"
---
# <a name="change-the-quantity-of-licenses-in-a-customer-subscription"></a><span data-ttu-id="c3bdd-104">Het aantal licenties in een klantabonnement wijzigen</span><span class="sxs-lookup"><span data-stu-id="c3bdd-104">Change the quantity of licenses in a customer subscription</span></span>

<span data-ttu-id="c3bdd-105">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c3bdd-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c3bdd-106">Werkt een [abonnement bij](subscription-resources.md) om het aantal licenties te verhogen of te verlagen.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-106">Updates a [subscription](subscription-resources.md) to increase or decrease the quantity of licenses.</span></span>

<span data-ttu-id="c3bdd-107">In het Partner Center dashboard kunt u deze bewerking uitvoeren door eerst [een klant te selecteren.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="c3bdd-107">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="c3bdd-108">Selecteer vervolgens het abonnement in kwestie dat u de naam wilt geven.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-108">Then, select the subscription in question that you wish to rename.</span></span> <span data-ttu-id="c3bdd-109">Als u wilt voltooien, wijzigt u de waarde in **het veld Hoeveelheid** en selecteert u vervolgens **Verzenden.**</span><span class="sxs-lookup"><span data-stu-id="c3bdd-109">To finish, change the value in the **Quantity** field, then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3bdd-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c3bdd-110">Prerequisites</span></span>

- <span data-ttu-id="c3bdd-111">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c3bdd-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c3bdd-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="c3bdd-113">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c3bdd-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="c3bdd-114">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="c3bdd-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="c3bdd-115">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="c3bdd-116">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="c3bdd-117">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="c3bdd-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="c3bdd-118">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c3bdd-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="c3bdd-119">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="c3bdd-120">C\#</span><span class="sxs-lookup"><span data-stu-id="c3bdd-120">C\#</span></span>

<span data-ttu-id="c3bdd-121">Als u de hoeveelheid van het abonnement van een klant wilt wijzigen, moet u eerst [het](get-a-subscription-by-id.md)abonnement op halen en vervolgens de eigenschap Hoeveelheid van [**het abonnement**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.quantity) wijzigen.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-121">To change the quantity of a customer's subscription, first [get the subscription](get-a-subscription-by-id.md), then change the subscription's [**Quantity**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.quantity) property.</span></span> <span data-ttu-id="c3bdd-122">Zodra de wijziging is aangebracht, gebruikt u de **verzameling IAggregatePartner.Customers** en roept u de **methode ById()** aan.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-122">Once the change is made, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="c3bdd-123">Roep vervolgens de [**eigenschap Abonnementen aan,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) gevolgd door de [**methode ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="c3bdd-123">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="c3bdd-124">Vervolgens roept u de methode **Patch()** aan.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-124">Then, finish by calling the **Patch()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var customerId;
// var subscriptionId;

//retrieving the subscription, for the purpose of the sample
ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.Get();
Subscription selectedSubscription = customerSubscriptions.Items.FirstOrDefault(sub => sub.Status == SubscriptionStatus.Active);

//update selected subscription,
selectedSubscription.Quantity++;

var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

<span data-ttu-id="c3bdd-125">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="c3bdd-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="c3bdd-126">**Project:** PartnerSDK.FeatureSample-klasse: UpdateSubscription.cs </span><span class="sxs-lookup"><span data-stu-id="c3bdd-126">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="c3bdd-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c3bdd-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c3bdd-128">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="c3bdd-128">Request syntax</span></span>

| <span data-ttu-id="c3bdd-129">Methode</span><span class="sxs-lookup"><span data-stu-id="c3bdd-129">Method</span></span>    | <span data-ttu-id="c3bdd-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c3bdd-130">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c3bdd-131">**Patch**</span><span class="sxs-lookup"><span data-stu-id="c3bdd-131">**PATCH**</span></span> | <span data-ttu-id="c3bdd-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c3bdd-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="c3bdd-133">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="c3bdd-133">URI parameter</span></span>

<span data-ttu-id="c3bdd-134">Deze tabel bevat de vereiste queryparameter om de hoeveelheid van het abonnement te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-134">This table lists the required query parameter to change the quantity of the subscription.</span></span>

| <span data-ttu-id="c3bdd-135">Naam</span><span class="sxs-lookup"><span data-stu-id="c3bdd-135">Name</span></span>                    | <span data-ttu-id="c3bdd-136">Type</span><span class="sxs-lookup"><span data-stu-id="c3bdd-136">Type</span></span>     | <span data-ttu-id="c3bdd-137">Vereist</span><span class="sxs-lookup"><span data-stu-id="c3bdd-137">Required</span></span> | <span data-ttu-id="c3bdd-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c3bdd-138">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="c3bdd-139">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="c3bdd-139">**customer-tenant-id**</span></span>  | <span data-ttu-id="c3bdd-140">**guid**</span><span class="sxs-lookup"><span data-stu-id="c3bdd-140">**guid**</span></span> | <span data-ttu-id="c3bdd-141">J</span><span class="sxs-lookup"><span data-stu-id="c3bdd-141">Y</span></span>        | <span data-ttu-id="c3bdd-142">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-142">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="c3bdd-143">**id-for-subscription**</span><span class="sxs-lookup"><span data-stu-id="c3bdd-143">**id-for-subscription**</span></span> | <span data-ttu-id="c3bdd-144">**guid**</span><span class="sxs-lookup"><span data-stu-id="c3bdd-144">**guid**</span></span> | <span data-ttu-id="c3bdd-145">J</span><span class="sxs-lookup"><span data-stu-id="c3bdd-145">Y</span></span>        | <span data-ttu-id="c3bdd-146">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-146">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c3bdd-147">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c3bdd-147">Request headers</span></span>

<span data-ttu-id="c3bdd-148">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="c3bdd-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c3bdd-149">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c3bdd-149">Request body</span></span>

<span data-ttu-id="c3bdd-150">Een volledige **abonnementsresource** is vereist in de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-150">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="c3bdd-151">Zorg ervoor dat **de eigenschap Quantity** is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-151">Ensure that the **Quantity** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="c3bdd-152">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c3bdd-152">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="c3bdd-153">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c3bdd-153">REST response</span></span>

<span data-ttu-id="c3bdd-154">Als dit lukt, retourneert deze methode een **HTTP-status 200-statuscode** en bijgewerkte eigenschappen van abonnementsresources in de antwoord-body. [](subscription-resources.md)</span><span class="sxs-lookup"><span data-stu-id="c3bdd-154">If successful, this method returns an **HTTP status 200** status code and updated [subscription resource](subscription-resources.md)  properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c3bdd-155">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="c3bdd-155">Response success and error codes</span></span>

<span data-ttu-id="c3bdd-156">Elk antwoord retourneert een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-156">Each response returns an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c3bdd-157">Gebruik een hulpprogramma voor netwerk traceren om de statuscode, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-157">Use a network trace tool to read the status code, error type, and additional parameters.</span></span> <span data-ttu-id="c3bdd-158">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="c3bdd-158">For the full list, see [Error Codes](error-codes.md).</span></span>

<span data-ttu-id="c3bdd-159">Wanneer de patchbewerking langer duurt dan de verwachte tijd, verzendt de Partner Center een **HTTP-statuscode 202** en een locatieheader die wijst naar waar het abonnement moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-159">When the patch operation takes longer than the expected time, the Partner Center sends an **HTTP status 202** status code and a location header that points to where to retrieve the subscription.</span></span> <span data-ttu-id="c3bdd-160">U kunt periodiek een query uitvoeren op het abonnement om de status- en hoeveelheidswijzigingen te controleren.</span><span class="sxs-lookup"><span data-stu-id="c3bdd-160">You can query the subscription periodically to monitor the status and quantity changes.</span></span>

### <a name="response-examples"></a><span data-ttu-id="c3bdd-161">Antwoordvoorbeelden</span><span class="sxs-lookup"><span data-stu-id="c3bdd-161">Response examples</span></span>

#### <a name="response-example-1"></a><span data-ttu-id="c3bdd-162">Antwoordvoorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="c3bdd-162">Response example 1</span></span>

<span data-ttu-id="c3bdd-163">Geslaagde aanvraag met **een HTTP-statuscode 200:**</span><span class="sxs-lookup"><span data-stu-id="c3bdd-163">Successful request with an **HTTP status 200** status code:</span></span>

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

#### <a name="response-example-2"></a><span data-ttu-id="c3bdd-164">Antwoordvoorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="c3bdd-164">Response example 2</span></span>

<span data-ttu-id="c3bdd-165">Geslaagde aanvraag met een **HTTP-statuscode 202:**</span><span class="sxs-lookup"><span data-stu-id="c3bdd-165">Successful request with an **HTTP status 202** status code:</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscriptionID> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 01880c1b-1966-40f0-d470-501a66d9948b
MS-CorrelationId: 2c5827c1-d5f9-4835-cc6d-f1918b782c79
Content-Type: application/json
Content-Length: 1432
Connection: Keep-Alive
Location: /customers/<customer-tenant-id>/subscriptions/<subscriptionID>
```
