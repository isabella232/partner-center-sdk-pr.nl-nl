---
title: De inrichtingsstatus van het abonnement ophalen
description: De inrichtingsstatus van het abonnement voor een klantabonnement op te halen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f8797fa494cd77f11a1179d6406ca021f0d7788c
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548699"
---
# <a name="get-subscription-provisioning-status"></a><span data-ttu-id="71fb6-103">De inrichtingsstatus van het abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="71fb6-103">Get subscription provisioning status</span></span>

<span data-ttu-id="71fb6-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="71fb6-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="71fb6-105">De inrichtingsstatus van het abonnement voor een klantabonnement op te halen.</span><span class="sxs-lookup"><span data-stu-id="71fb6-105">How to get the subscription provisioning status for a customer subscription.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="71fb6-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="71fb6-106">Prerequisites</span></span>

- <span data-ttu-id="71fb6-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="71fb6-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="71fb6-108">Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="71fb6-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="71fb6-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="71fb6-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="71fb6-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="71fb6-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="71fb6-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="71fb6-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="71fb6-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="71fb6-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="71fb6-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="71fb6-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="71fb6-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="71fb6-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="71fb6-115">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="71fb6-115">A subscription identifier.</span></span>

- <span data-ttu-id="71fb6-116">Gedelegeerde beheerdersmachtigingen voor het abonnement zijn vereist om deze bewerking uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="71fb6-116">Delegated admin permissions on the subscription are required to perform this operation.</span></span>

## <a name="c"></a><span data-ttu-id="71fb6-117">C\#</span><span class="sxs-lookup"><span data-stu-id="71fb6-117">C\#</span></span>

<span data-ttu-id="71fb6-118">Als u de inrichtingsstatus van een abonnement wilt weten, gebruikt u eerst de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="71fb6-118">To get the provisioning status of a subscription, begin by using the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="71fb6-119">Haal vervolgens een interface op voor abonnementsbewerkingen door de methode [**Subscriptions.ById aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) te roepen met de abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="71fb6-119">Then, get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the subscription ID.</span></span> <span data-ttu-id="71fb6-120">Gebruik vervolgens de eigenschap [**ProvisioningStatus**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.provisioningstatus) om een interface te verkrijgen voor de inrichtingsstatusbewerkingen van het huidige abonnement en roep vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionprovisioningstatus.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionprovisioningstatus.getasync) aan om het object [**SubscriptionProvisioningStatus**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionprovisioningstatus) op te halen.</span><span class="sxs-lookup"><span data-stu-id="71fb6-120">Next, use the [**ProvisioningStatus**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.provisioningstatus) property to obtain an interface to the current subscription's provisioning status operations, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionprovisioningstatus.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionprovisioningstatus.getasync) method to retrieve the [**SubscriptionProvisioningStatus**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionprovisioningstatus) object.</span></span>

``` csharp
// IAggregatePartner partnerOperations.
// string customerId;
// string subscriptionId;

// Retrieve a subscription's provisioning status.
var provisioningStatus = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionID).ProvisioningStatus.Get();
```

## <a name="rest-request"></a><span data-ttu-id="71fb6-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="71fb6-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="71fb6-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="71fb6-122">Request syntax</span></span>

| <span data-ttu-id="71fb6-123">Methode</span><span class="sxs-lookup"><span data-stu-id="71fb6-123">Method</span></span>  | <span data-ttu-id="71fb6-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="71fb6-124">Request URI</span></span>                                                                                                                        |
|---------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="71fb6-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="71fb6-125">**GET**</span></span> | <span data-ttu-id="71fb6-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/provisioningstatus HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="71fb6-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/provisioningstatus HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="71fb6-127">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="71fb6-127">URI parameters</span></span>

<span data-ttu-id="71fb6-128">Gebruik de volgende padparameters om de klant en het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="71fb6-128">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="71fb6-129">Naam</span><span class="sxs-lookup"><span data-stu-id="71fb6-129">Name</span></span>            | <span data-ttu-id="71fb6-130">Type</span><span class="sxs-lookup"><span data-stu-id="71fb6-130">Type</span></span>   | <span data-ttu-id="71fb6-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="71fb6-131">Required</span></span> | <span data-ttu-id="71fb6-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="71fb6-132">Description</span></span>                                               |
|-----------------|--------|----------|-----------------------------------------------------------|
| <span data-ttu-id="71fb6-133">customer-id</span><span class="sxs-lookup"><span data-stu-id="71fb6-133">customer-id</span></span>     | <span data-ttu-id="71fb6-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="71fb6-134">string</span></span> | <span data-ttu-id="71fb6-135">Ja</span><span class="sxs-lookup"><span data-stu-id="71fb6-135">Yes</span></span>      | <span data-ttu-id="71fb6-136">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="71fb6-136">A GUID formatted string that identifies the customer.</span></span>     |
| <span data-ttu-id="71fb6-137">subscription-id</span><span class="sxs-lookup"><span data-stu-id="71fb6-137">subscription-id</span></span> | <span data-ttu-id="71fb6-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="71fb6-138">string</span></span> | <span data-ttu-id="71fb6-139">Ja</span><span class="sxs-lookup"><span data-stu-id="71fb6-139">Yes</span></span>      | <span data-ttu-id="71fb6-140">Een tekenreeks met GUID-indeling die het abonnement identificeert.</span><span class="sxs-lookup"><span data-stu-id="71fb6-140">A GUID formatted string that identifies the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="71fb6-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="71fb6-141">Request headers</span></span>

<span data-ttu-id="71fb6-142">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="71fb6-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="71fb6-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="71fb6-143">Request body</span></span>

<span data-ttu-id="71fb6-144">Geen.</span><span class="sxs-lookup"><span data-stu-id="71fb6-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="71fb6-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="71fb6-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/34828C05-C16C-4D6F-9CFC-4D2650EF19A1/provisioningstatus HTTP/1.1
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
MS-RequestId: d0e38dfd-a2c5-4a14-ac06-12d30f0ec54e
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="71fb6-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="71fb6-146">REST response</span></span>

<span data-ttu-id="71fb6-147">Als dit lukt, bevat de antwoord-body de resource [SubscriptionProvisioningStatus.](subscription-resources.md#subscriptionprovisioningstatus)</span><span class="sxs-lookup"><span data-stu-id="71fb6-147">If successful, the response body contains a [SubscriptionProvisioningStatus](subscription-resources.md#subscriptionprovisioningstatus) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="71fb6-148">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="71fb6-148">Response success and error codes</span></span>

<span data-ttu-id="71fb6-149">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="71fb6-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="71fb6-150">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="71fb6-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="71fb6-151">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="71fb6-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="71fb6-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="71fb6-152">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
MS-RequestId: d0e38dfd-a2c5-4a14-ac06-12d30f0ec54e
MS-CV: InswEQre402koceL.0
MS-ServerId: 030020344
Date: Thu, 20 Apr 2017 19:23:39 GMT

{
    "skuId": "6FD2C87F-B296-42F0-B197-1E91E994B900",
    "status": "success",
    "quantity": 5,
    "endDate": "2018-05-10T00:00:00Z",
    "attributes": {
        "objectType": "SubscriptionProvisioningStatus"
    }
}
```

## <a name="remarks"></a><span data-ttu-id="71fb6-153">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="71fb6-153">Remarks</span></span>

- <span data-ttu-id="71fb6-154">Tijdens een licentiewijzigingstoewijzing is het statusveld in [SubscriptionProvisioningStatus](subscription-resources.md#subscriptionprovisioningstatus) ingesteld op 'in behandeling'.</span><span class="sxs-lookup"><span data-stu-id="71fb6-154">During a license change assignment, the status field in [SubscriptionProvisioningStatus](subscription-resources.md#subscriptionprovisioningstatus) is set to "pending".</span></span>

- <span data-ttu-id="71fb6-155">Het statusveld wordt elke 15 minuten bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="71fb6-155">The status field is updated every 15 minutes.</span></span>
