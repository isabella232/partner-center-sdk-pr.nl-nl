---
title: De hoeveelheid van een abonnement wijzigen
description: Meer informatie over het gebruik van partner Center-Api's om het aantal licenties voor een klant abonnement te wijzigen. U kunt dit ook doen in het dash board van partner Center.
ms.date: 06/05/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b9b781c50895aa3a14819bec43fcca1e931e3b30
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2020
ms.locfileid: "97767618"
---
# <a name="change-the-quantity-of-licenses-in-a-customer-subscription"></a><span data-ttu-id="cdaa1-104">Het aantal licenties in een klant abonnement wijzigen</span><span class="sxs-lookup"><span data-stu-id="cdaa1-104">Change the quantity of licenses in a customer subscription</span></span>

<span data-ttu-id="cdaa1-105">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="cdaa1-105">**Applies to:**</span></span>

- <span data-ttu-id="cdaa1-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="cdaa1-106">Partner Center</span></span>
- <span data-ttu-id="cdaa1-107">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="cdaa1-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="cdaa1-108">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="cdaa1-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="cdaa1-109">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="cdaa1-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="cdaa1-110">Hiermee wordt een [abonnement](subscription-resources.md) bijgewerkt om het aantal licenties te verhogen of te verlagen.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-110">Updates a [subscription](subscription-resources.md) to increase or decrease the quantity of licenses.</span></span>

<span data-ttu-id="cdaa1-111">In het dash board van de partner centrum kan deze bewerking worden uitgevoerd door eerst [een klant te selecteren](get-a-customer-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="cdaa1-111">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="cdaa1-112">Selecteer vervolgens het abonnement waarvan u de naam wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-112">Then, select the subscription in question that you wish to rename.</span></span> <span data-ttu-id="cdaa1-113">Als u wilt volt ooien, wijzigt u de waarde in het veld **aantal** en selecteert u vervolgens **verzenden.**</span><span class="sxs-lookup"><span data-stu-id="cdaa1-113">To finish, change the value in the **Quantity** field, then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cdaa1-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cdaa1-114">Prerequisites</span></span>

- <span data-ttu-id="cdaa1-115">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cdaa1-115">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cdaa1-116">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-116">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="cdaa1-117">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cdaa1-117">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="cdaa1-118">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-118">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="cdaa1-119">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-119">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="cdaa1-120">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-120">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="cdaa1-121">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="cdaa1-121">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="cdaa1-122">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cdaa1-122">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="cdaa1-123">Een abonnements-ID.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-123">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="cdaa1-124">C\#</span><span class="sxs-lookup"><span data-stu-id="cdaa1-124">C\#</span></span>

<span data-ttu-id="cdaa1-125">Als u het aantal van het abonnement van een klant wilt wijzigen, moet u eerst [het abonnement ophalen](get-a-subscription-by-id.md)en vervolgens de eigenschap [**hoeveelheid**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.quantity) van het abonnement wijzigen.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-125">To change the quantity of a customer's subscription, first [get the subscription](get-a-subscription-by-id.md), then change the subscription's [**Quantity**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.quantity) property.</span></span> <span data-ttu-id="cdaa1-126">Nadat de wijziging is aangebracht, gebruikt u de verzameling **IAggregatePartner. Customers** en roept u de methode **ById ()** aan.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-126">Once the change is made, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="cdaa1-127">Roep vervolgens de eigenschap [**abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) aan, gevolgd door de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) .</span><span class="sxs-lookup"><span data-stu-id="cdaa1-127">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span> <span data-ttu-id="cdaa1-128">Voltooi vervolgens de methode **patch ()** .</span><span class="sxs-lookup"><span data-stu-id="cdaa1-128">Then, finish by calling the **Patch()** method.</span></span>

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

<span data-ttu-id="cdaa1-129">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="cdaa1-129">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="cdaa1-130">**Project**: PartnerSDK. FeatureSample- **klasse**: UpdateSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="cdaa1-130">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="cdaa1-131">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="cdaa1-131">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cdaa1-132">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cdaa1-132">Request syntax</span></span>

| <span data-ttu-id="cdaa1-133">Methode</span><span class="sxs-lookup"><span data-stu-id="cdaa1-133">Method</span></span>    | <span data-ttu-id="cdaa1-134">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="cdaa1-134">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="cdaa1-135">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="cdaa1-135">**PATCH**</span></span> | <span data-ttu-id="cdaa1-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{id-for-Subscription} http/1.1</span><span class="sxs-lookup"><span data-stu-id="cdaa1-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="cdaa1-137">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="cdaa1-137">URI parameter</span></span>

<span data-ttu-id="cdaa1-138">Deze tabel bevat de vereiste query parameter voor het wijzigen van de hoeveelheid van het abonnement.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-138">This table lists the required query parameter to change the quantity of the subscription.</span></span>

| <span data-ttu-id="cdaa1-139">Naam</span><span class="sxs-lookup"><span data-stu-id="cdaa1-139">Name</span></span>                    | <span data-ttu-id="cdaa1-140">Type</span><span class="sxs-lookup"><span data-stu-id="cdaa1-140">Type</span></span>     | <span data-ttu-id="cdaa1-141">Vereist</span><span class="sxs-lookup"><span data-stu-id="cdaa1-141">Required</span></span> | <span data-ttu-id="cdaa1-142">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cdaa1-142">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="cdaa1-143">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="cdaa1-143">**customer-tenant-id**</span></span>  | <span data-ttu-id="cdaa1-144">**guid**</span><span class="sxs-lookup"><span data-stu-id="cdaa1-144">**guid**</span></span> | <span data-ttu-id="cdaa1-145">J</span><span class="sxs-lookup"><span data-stu-id="cdaa1-145">Y</span></span>        | <span data-ttu-id="cdaa1-146">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-146">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="cdaa1-147">**id voor abonnement**</span><span class="sxs-lookup"><span data-stu-id="cdaa1-147">**id-for-subscription**</span></span> | <span data-ttu-id="cdaa1-148">**guid**</span><span class="sxs-lookup"><span data-stu-id="cdaa1-148">**guid**</span></span> | <span data-ttu-id="cdaa1-149">J</span><span class="sxs-lookup"><span data-stu-id="cdaa1-149">Y</span></span>        | <span data-ttu-id="cdaa1-150">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-150">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="cdaa1-151">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="cdaa1-151">Request headers</span></span>

<span data-ttu-id="cdaa1-152">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="cdaa1-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cdaa1-153">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="cdaa1-153">Request body</span></span>

<span data-ttu-id="cdaa1-154">Een volledige **abonnements** resource is vereist in de aanvraag tekst.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-154">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="cdaa1-155">Zorg ervoor dat de eigenschap **hoeveelheid** is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-155">Ensure that the **Quantity** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="cdaa1-156">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cdaa1-156">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="cdaa1-157">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="cdaa1-157">REST response</span></span>

<span data-ttu-id="cdaa1-158">Als dit lukt, retourneert deze methode de status code van de **HTTP-status 200** en de bijgewerkte eigenschappen van de [abonnements resource](subscription-resources.md)  in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-158">If successful, this method returns an **HTTP status 200** status code and updated [subscription resource](subscription-resources.md)  properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cdaa1-159">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="cdaa1-159">Response success and error codes</span></span>

<span data-ttu-id="cdaa1-160">Elke reactie retourneert een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-160">Each response returns an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cdaa1-161">Gebruik een hulp programma voor netwerk tracering om de status code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-161">Use a network trace tool to read the status code, error type, and additional parameters.</span></span> <span data-ttu-id="cdaa1-162">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-162">For the full list, see [Error Codes](error-codes.md).</span></span>

<span data-ttu-id="cdaa1-163">Wanneer de patch bewerking langer duurt dan de verwachte tijd, verzendt het partner centrum een **HTTP-status** code van 202 en een locatie-header die verwijst naar waar het abonnement moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-163">When the patch operation takes longer than the expected time, the Partner Center sends an **HTTP status 202** status code and a location header that points to where to retrieve the subscription.</span></span> <span data-ttu-id="cdaa1-164">U kunt periodiek een query uitvoeren op het abonnement om de status-en hoeveelheid wijzigingen te bewaken.</span><span class="sxs-lookup"><span data-stu-id="cdaa1-164">You can query the subscription periodically to monitor the status and quantity changes.</span></span>

### <a name="response-examples"></a><span data-ttu-id="cdaa1-165">Antwoord voorbeelden</span><span class="sxs-lookup"><span data-stu-id="cdaa1-165">Response examples</span></span>

#### <a name="response-example-1"></a><span data-ttu-id="cdaa1-166">Antwoord voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="cdaa1-166">Response example 1</span></span>

<span data-ttu-id="cdaa1-167">Geslaagde aanvraag met een **HTTP-status 200-** status code:</span><span class="sxs-lookup"><span data-stu-id="cdaa1-167">Successful request with an **HTTP status 200** status code:</span></span>

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

#### <a name="response-example-2"></a><span data-ttu-id="cdaa1-168">Antwoord voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="cdaa1-168">Response example 2</span></span>

<span data-ttu-id="cdaa1-169">Geslaagde aanvraag met een **HTTP-status 202-** status code:</span><span class="sxs-lookup"><span data-stu-id="cdaa1-169">Successful request with an **HTTP status 202** status code:</span></span>

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
