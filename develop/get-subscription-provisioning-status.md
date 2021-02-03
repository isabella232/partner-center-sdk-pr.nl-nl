---
title: De inrichtingsstatus van het abonnement ophalen
description: De inrichtings status van het abonnement ophalen voor een klant abonnement.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 38544aa380ba0a6a8804ae45f7d8ae7cb431d3ba
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767542"
---
# <a name="get-subscription-provisioning-status"></a><span data-ttu-id="2ef70-103">De inrichtingsstatus van het abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="2ef70-103">Get subscription provisioning status</span></span>

<span data-ttu-id="2ef70-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="2ef70-104">**Applies To**</span></span>

- <span data-ttu-id="2ef70-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="2ef70-105">Partner Center</span></span>
- <span data-ttu-id="2ef70-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="2ef70-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="2ef70-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="2ef70-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="2ef70-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2ef70-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2ef70-109">De inrichtings status van het abonnement ophalen voor een klant abonnement.</span><span class="sxs-lookup"><span data-stu-id="2ef70-109">How to get the subscription provisioning status for a customer subscription.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ef70-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2ef70-110">Prerequisites</span></span>

- <span data-ttu-id="2ef70-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2ef70-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2ef70-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="2ef70-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="2ef70-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2ef70-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="2ef70-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="2ef70-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="2ef70-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="2ef70-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="2ef70-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="2ef70-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="2ef70-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="2ef70-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="2ef70-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2ef70-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="2ef70-119">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="2ef70-119">A subscription identifier.</span></span>

- <span data-ttu-id="2ef70-120">Gedelegeerde beheerders machtigingen voor het abonnement zijn vereist om deze bewerking uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="2ef70-120">Delegated admin permissions on the subscription are required to perform this operation.</span></span>

## <a name="c"></a><span data-ttu-id="2ef70-121">C\#</span><span class="sxs-lookup"><span data-stu-id="2ef70-121">C\#</span></span>

<span data-ttu-id="2ef70-122">Als u de inrichtings status van een abonnement wilt ophalen, begint u met de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="2ef70-122">To get the provisioning status of a subscription, begin by using the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="2ef70-123">Vervolgens krijgt u een interface voor abonnements bewerkingen door de methode [**abonnementen. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) aan te roepen met de abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="2ef70-123">Then, get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the subscription ID.</span></span> <span data-ttu-id="2ef70-124">Gebruik vervolgens de eigenschap [**ProvisioningStatus**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.provisioningstatus) om een interface te verkrijgen voor de inrichtings status bewerkingen van het huidige abonnement en roep vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionprovisioningstatus.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionprovisioningstatus.getasync) aan om het [**SubscriptionProvisioningStatus**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionprovisioningstatus) -object op te halen.</span><span class="sxs-lookup"><span data-stu-id="2ef70-124">Next, use the [**ProvisioningStatus**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.provisioningstatus) property to obtain an interface to the current subscription's provisioning status operations, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionprovisioningstatus.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionprovisioningstatus.getasync) method to retrieve the [**SubscriptionProvisioningStatus**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionprovisioningstatus) object.</span></span>

``` csharp
// IAggregatePartner partnerOperations.
// string customerId;
// string subscriptionId;

// Retrieve a subscription's provisioning status.
var provisioningStatus = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionID).ProvisioningStatus.Get();
```

## <a name="rest-request"></a><span data-ttu-id="2ef70-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="2ef70-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2ef70-126">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2ef70-126">Request syntax</span></span>

| <span data-ttu-id="2ef70-127">Methode</span><span class="sxs-lookup"><span data-stu-id="2ef70-127">Method</span></span>  | <span data-ttu-id="2ef70-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="2ef70-128">Request URI</span></span>                                                                                                                        |
|---------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2ef70-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="2ef70-129">**GET**</span></span> | <span data-ttu-id="2ef70-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Subscriptions/{Subscription-id}/provisioningstatus http/1.1</span><span class="sxs-lookup"><span data-stu-id="2ef70-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/provisioningstatus HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="2ef70-131">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="2ef70-131">URI parameters</span></span>

<span data-ttu-id="2ef70-132">Gebruik de volgende Path-para meters om de klant en het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="2ef70-132">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="2ef70-133">Naam</span><span class="sxs-lookup"><span data-stu-id="2ef70-133">Name</span></span>            | <span data-ttu-id="2ef70-134">Type</span><span class="sxs-lookup"><span data-stu-id="2ef70-134">Type</span></span>   | <span data-ttu-id="2ef70-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="2ef70-135">Required</span></span> | <span data-ttu-id="2ef70-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2ef70-136">Description</span></span>                                               |
|-----------------|--------|----------|-----------------------------------------------------------|
| <span data-ttu-id="2ef70-137">klant-id</span><span class="sxs-lookup"><span data-stu-id="2ef70-137">customer-id</span></span>     | <span data-ttu-id="2ef70-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2ef70-138">string</span></span> | <span data-ttu-id="2ef70-139">Yes</span><span class="sxs-lookup"><span data-stu-id="2ef70-139">Yes</span></span>      | <span data-ttu-id="2ef70-140">Een teken reeks met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="2ef70-140">A GUID formatted string that identifies the customer.</span></span>     |
| <span data-ttu-id="2ef70-141">abonnement-id</span><span class="sxs-lookup"><span data-stu-id="2ef70-141">subscription-id</span></span> | <span data-ttu-id="2ef70-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2ef70-142">string</span></span> | <span data-ttu-id="2ef70-143">Yes</span><span class="sxs-lookup"><span data-stu-id="2ef70-143">Yes</span></span>      | <span data-ttu-id="2ef70-144">Een teken reeks met een GUID-indeling waarmee het abonnement wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="2ef70-144">A GUID formatted string that identifies the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="2ef70-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="2ef70-145">Request headers</span></span>

<span data-ttu-id="2ef70-146">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2ef70-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2ef70-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="2ef70-147">Request body</span></span>

<span data-ttu-id="2ef70-148">Geen.</span><span class="sxs-lookup"><span data-stu-id="2ef70-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="2ef70-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2ef70-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/34828C05-C16C-4D6F-9CFC-4D2650EF19A1/provisioningstatus HTTP/1.1
Accept: application/json, text/plain, */*
Authorization: Bearer <token>
MS-RequestId: d0e38dfd-a2c5-4a14-ac06-12d30f0ec54e
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="2ef70-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="2ef70-150">REST response</span></span>

<span data-ttu-id="2ef70-151">Als dit lukt, bevat de antwoord tekst een [SubscriptionProvisioningStatus](subscription-resources.md#subscriptionprovisioningstatus) -resource.</span><span class="sxs-lookup"><span data-stu-id="2ef70-151">If successful, the response body contains a [SubscriptionProvisioningStatus](subscription-resources.md#subscriptionprovisioningstatus) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2ef70-152">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="2ef70-152">Response success and error codes</span></span>

<span data-ttu-id="2ef70-153">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="2ef70-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2ef70-154">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="2ef70-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2ef70-155">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="2ef70-155">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2ef70-156">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="2ef70-156">Response example</span></span>

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

## <a name="remarks"></a><span data-ttu-id="2ef70-157">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2ef70-157">Remarks</span></span>

- <span data-ttu-id="2ef70-158">Tijdens een licentie wijzigings toewijzing wordt het veld Status in [SubscriptionProvisioningStatus](subscription-resources.md#subscriptionprovisioningstatus) ingesteld op ' in behandeling '.</span><span class="sxs-lookup"><span data-stu-id="2ef70-158">During a license change assignment, the status field in [SubscriptionProvisioningStatus](subscription-resources.md#subscriptionprovisioningstatus) is set to "pending".</span></span>

- <span data-ttu-id="2ef70-159">Het veld Status wordt elke vijf tien minuten bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="2ef70-159">The status field is updated every fifteen minutes.</span></span>
