---
title: Een lijst met aanbiedingen voor omzetten van de proefversie ophalen
description: Een lijst met aanbiedingen voor proef conversie ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e1eadecde9efa0b59fc7790bd474889bb32821dc
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767441"
---
# <a name="get-a-list-of-trial-conversion-offers"></a><span data-ttu-id="e6cd3-103">Een lijst met aanbiedingen voor omzetten van de proefversie ophalen</span><span class="sxs-lookup"><span data-stu-id="e6cd3-103">Get a list of trial conversion offers</span></span>

<span data-ttu-id="e6cd3-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="e6cd3-104">**Applies To**</span></span>

- <span data-ttu-id="e6cd3-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e6cd3-105">Partner Center</span></span>

<span data-ttu-id="e6cd3-106">Een lijst met aanbiedingen voor proef conversie ophalen.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-106">How to retrieve a list of trial conversion offers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e6cd3-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e6cd3-107">Prerequisites</span></span>

- <span data-ttu-id="e6cd3-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e6cd3-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e6cd3-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="e6cd3-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e6cd3-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e6cd3-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e6cd3-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e6cd3-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e6cd3-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="e6cd3-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e6cd3-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e6cd3-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="e6cd3-116">Een abonnements-ID voor een actief proef abonnement.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-116">A subscription ID for an active trial subscription.</span></span>

## <a name="c"></a><span data-ttu-id="e6cd3-117">C\#</span><span class="sxs-lookup"><span data-stu-id="e6cd3-117">C\#</span></span>

<span data-ttu-id="e6cd3-118">Als u een lijst met beschik bare proef versies wilt ophalen, moet u eerst de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id gebruiken om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-118">To get a list of trial conversions available, start by using the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="e6cd3-119">Vervolgens krijgt u een interface voor het uitvoeren van een abonnement door de methode [**abonnementen. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) aan te roepen met de id van het proef abonnement.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-119">Then, get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the trial subscription ID.</span></span> <span data-ttu-id="e6cd3-120">Gebruik vervolgens de eigenschap [**conversies**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) om een interface te verkrijgen voor de beschik bare bewerkingen op conversies en roep vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) aan om een verzameling beschik bare [**conversie**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) aanbiedingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-120">Next, use the [**Conversions**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) property to obtain an interface to the available operations on conversions, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) method to retrieve a collection of available [**Conversion**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) offers.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

// Get the available conversions.
var conversions =
    partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId).Conversions.Get();
```

## <a name="rest-request"></a><span data-ttu-id="e6cd3-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e6cd3-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e6cd3-122">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e6cd3-122">Request syntax</span></span>

| <span data-ttu-id="e6cd3-123">Methode</span><span class="sxs-lookup"><span data-stu-id="e6cd3-123">Method</span></span>  | <span data-ttu-id="e6cd3-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e6cd3-124">Request URI</span></span>                                                                                                                 |
|---------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e6cd3-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e6cd3-125">**GET**</span></span> | <span data-ttu-id="e6cd3-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Subscriptions/{Subscription-id}/conversions http/1.1</span><span class="sxs-lookup"><span data-stu-id="e6cd3-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="e6cd3-127">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="e6cd3-127">URI parameter</span></span>

<span data-ttu-id="e6cd3-128">Gebruik de volgende Path-para meters om het klant-en proef abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-128">Use the following path parameters to identify the customer and trial subscription.</span></span>

| <span data-ttu-id="e6cd3-129">Naam</span><span class="sxs-lookup"><span data-stu-id="e6cd3-129">Name</span></span>            | <span data-ttu-id="e6cd3-130">Type</span><span class="sxs-lookup"><span data-stu-id="e6cd3-130">Type</span></span>   | <span data-ttu-id="e6cd3-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="e6cd3-131">Required</span></span> | <span data-ttu-id="e6cd3-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e6cd3-132">Description</span></span>                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="e6cd3-133">klant-id</span><span class="sxs-lookup"><span data-stu-id="e6cd3-133">customer-id</span></span>     | <span data-ttu-id="e6cd3-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e6cd3-134">string</span></span> | <span data-ttu-id="e6cd3-135">Yes</span><span class="sxs-lookup"><span data-stu-id="e6cd3-135">Yes</span></span>      | <span data-ttu-id="e6cd3-136">Een teken reeks met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-136">A GUID formatted string that identifies the customer.</span></span>           |
| <span data-ttu-id="e6cd3-137">abonnement-id</span><span class="sxs-lookup"><span data-stu-id="e6cd3-137">subscription-id</span></span> | <span data-ttu-id="e6cd3-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e6cd3-138">string</span></span> | <span data-ttu-id="e6cd3-139">Yes</span><span class="sxs-lookup"><span data-stu-id="e6cd3-139">Yes</span></span>      | <span data-ttu-id="e6cd3-140">Een teken reeks met een GUID-indeling waarmee het proef abonnement wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-140">A GUID formatted string that identifies the trial subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e6cd3-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e6cd3-141">Request headers</span></span>

<span data-ttu-id="e6cd3-142">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e6cd3-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e6cd3-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e6cd3-143">Request body</span></span>

<span data-ttu-id="e6cd3-144">Geen.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e6cd3-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e6cd3-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/488745B5-2086-4912-802C-6ABB9F7C3638/conversions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e17f5bc6-24bf-4cbe-b632-d7fc6cec3058
MS-CorrelationId: 8daa6d54-72ab-4d6b-9c7d-9266d3734a47
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="e6cd3-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e6cd3-146">REST response</span></span>

<span data-ttu-id="e6cd3-147">Als dit lukt, bevat de antwoord tekst een verzameling [conversie](conversions-resources.md#conversionresult) resources.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-147">If successful, the response body contains a collection of [Conversion](conversions-resources.md#conversionresult) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e6cd3-148">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="e6cd3-148">Response success and error codes</span></span>

<span data-ttu-id="e6cd3-149">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e6cd3-150">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e6cd3-151">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="e6cd3-151">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e6cd3-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e6cd3-152">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 305
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 8daa6d54-72ab-4d6b-9c7d-9266d3734a47
MS-RequestId: e17f5bc6-24bf-4cbe-b632-d7fc6cec3058
MS-CV: feJByqU1X0ObaTQr.0
MS-ServerId: 030011719
Date: Thu, 15 Jun 2017 23:10:01 GMT

 {
    "totalCount": 1,
    "items": [{
            "offerId": "C0BD2E08-11AC-4836-BDC7-3712E744922F",
            "targetOfferId": "031C9E47-4802-4248-838E-778FB1D2CC05",
            "orderId": "D51A052E-043C-4A2A-AA37-2BB938CEF6C1",
            "quantity": 25,
            "billingCycle": "monthly",
            "attributes": {
                "objectType": "Conversion"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
