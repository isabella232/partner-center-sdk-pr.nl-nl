---
title: De ondersteuningscontactpersoon van een abonnement ophalen
description: Een ondersteunings contact voor een abonnement ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: df3bce48902d95dc541c4a45e4e633569fc4406e
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767352"
---
# <a name="get-a-subscriptions-support-contact"></a><span data-ttu-id="7fbb7-103">De ondersteuningscontactpersoon van een abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="7fbb7-103">Get a subscription's support contact</span></span>

<span data-ttu-id="7fbb7-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="7fbb7-104">**Applies To**</span></span>

- <span data-ttu-id="7fbb7-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="7fbb7-105">Partner Center</span></span>
- <span data-ttu-id="7fbb7-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="7fbb7-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="7fbb7-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="7fbb7-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="7fbb7-108">Een ondersteunings contact voor een abonnement ophalen.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-108">How to get a subscription's support contact.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7fbb7-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7fbb7-109">Prerequisites</span></span>

- <span data-ttu-id="7fbb7-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7fbb7-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7fbb7-111">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="7fbb7-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7fbb7-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="7fbb7-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="7fbb7-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="7fbb7-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="7fbb7-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="7fbb7-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="7fbb7-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7fbb7-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="7fbb7-118">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-118">A subscription identifier.</span></span>

## <a name="c"></a><span data-ttu-id="7fbb7-119">C\#</span><span class="sxs-lookup"><span data-stu-id="7fbb7-119">C\#</span></span>

<span data-ttu-id="7fbb7-120">Als u het ondersteunings contact van een abonnement wilt ontvangen, gebruikt u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-120">To get a subscription's support contact, start by using the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="7fbb7-121">Vervolgens krijgt u een interface voor abonnements bewerkingen door de methode [**abonnementen. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) aan te roepen met de abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-121">Then, get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the subscription ID.</span></span> <span data-ttu-id="7fbb7-122">Gebruik vervolgens de eigenschap [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) om een interface te verkrijgen voor de ondersteuning van contact bewerkingen en roep vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) aan om het [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact) -object op te halen.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-122">Next, use the [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) property to obtain an interface to support contact operations, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) method to retrieve the [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact) object.</span></span>

``` csharp
// IAggregatePartner partnerOperations.
// string customerId;
// string subscriptionId;

// Retrieve subscription's support contact.
var supportContact = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId).SupportContact.Get();
```

<span data-ttu-id="7fbb7-123">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="7fbb7-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="7fbb7-124">**Project**: Partner Center SDK-voor beelden **klasse**: GetSubscriptionSupportContact.cs</span><span class="sxs-lookup"><span data-stu-id="7fbb7-124">**Project**: Partner Center SDK Samples **Class**: GetSubscriptionSupportContact.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="7fbb7-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="7fbb7-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7fbb7-126">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7fbb7-126">Request syntax</span></span>

| <span data-ttu-id="7fbb7-127">Methode</span><span class="sxs-lookup"><span data-stu-id="7fbb7-127">Method</span></span>  | <span data-ttu-id="7fbb7-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="7fbb7-128">Request URI</span></span>                                                                                                                    |
|---------|--------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7fbb7-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7fbb7-129">**GET**</span></span> | <span data-ttu-id="7fbb7-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Subscriptions/{Subscription-id}/supportcontact http/1.1</span><span class="sxs-lookup"><span data-stu-id="7fbb7-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/supportcontact HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="7fbb7-131">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="7fbb7-131">URI parameter</span></span>

<span data-ttu-id="7fbb7-132">Gebruik de volgende Path-para meters om de klant en het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-132">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="7fbb7-133">Naam</span><span class="sxs-lookup"><span data-stu-id="7fbb7-133">Name</span></span>            | <span data-ttu-id="7fbb7-134">Type</span><span class="sxs-lookup"><span data-stu-id="7fbb7-134">Type</span></span>   | <span data-ttu-id="7fbb7-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="7fbb7-135">Required</span></span> | <span data-ttu-id="7fbb7-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7fbb7-136">Description</span></span>                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="7fbb7-137">klant-id</span><span class="sxs-lookup"><span data-stu-id="7fbb7-137">customer-id</span></span>     | <span data-ttu-id="7fbb7-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7fbb7-138">string</span></span> | <span data-ttu-id="7fbb7-139">Yes</span><span class="sxs-lookup"><span data-stu-id="7fbb7-139">Yes</span></span>      | <span data-ttu-id="7fbb7-140">Een teken reeks met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-140">A GUID formatted string that identifies the customer.</span></span>           |
| <span data-ttu-id="7fbb7-141">abonnement-id</span><span class="sxs-lookup"><span data-stu-id="7fbb7-141">subscription-id</span></span> | <span data-ttu-id="7fbb7-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7fbb7-142">string</span></span> | <span data-ttu-id="7fbb7-143">Yes</span><span class="sxs-lookup"><span data-stu-id="7fbb7-143">Yes</span></span>      | <span data-ttu-id="7fbb7-144">Een teken reeks met een GUID-indeling waarmee het proef abonnement wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-144">A GUID formatted string that identifies the trial subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="7fbb7-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="7fbb7-145">Request headers</span></span>

<span data-ttu-id="7fbb7-146">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="7fbb7-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7fbb7-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="7fbb7-147">Request body</span></span>

<span data-ttu-id="7fbb7-148">Geen.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="7fbb7-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7fbb7-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/C8D8FBAB-6A62-44DC-BE50-B7C74E43A296/supportcontact HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: d052776c-e8fd-4803-b6a3-1659055ac3c4
MS-CorrelationId: a6c552a8-1922-4d0c-bb94-335a33334d14
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="7fbb7-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="7fbb7-150">REST response</span></span>

<span data-ttu-id="7fbb7-151">Als dit lukt, bevat de antwoord tekst de [SupportContact](subscription-resources.md#supportcontact) -resource.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-151">If successful, the response body contains the [SupportContact](subscription-resources.md#supportcontact) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7fbb7-152">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="7fbb7-152">Response success and error codes</span></span>

<span data-ttu-id="7fbb7-153">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7fbb7-154">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7fbb7-155">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="7fbb7-155">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="7fbb7-156">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="7fbb7-156">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 328
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a6c552a8-1922-4d0c-bb94-335a33334d14
MS-RequestId: d052776c-e8fd-4803-b6a3-1659055ac3c4
MS-CV: bLbUhqy0+ESOX1v4.0
MS-ServerId: 201022015
Date: Tue, 20 Jun 2017 19:30:19 GMT

{
    "supportTenantId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "supportMpnId": "4391507",
    "name": "Trey Research",
    "links": {
        "self": {
            "uri": "/customers/0C39D6D5-C70D-4C55-BC02-F620844F3FD1/subscriptions/C8D8FBAB-6A62-44DC-BE50-B7C74E43A296/supportcontact",
            "method": "Get",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "SupportContact"
    }
}
```
