---
title: Een lijst met aanbiedingen voor omzetten van de proefversie ophalen
description: Een lijst met aanbiedingen voor proefconversie ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 981910560faf7b7957b28e643c09a003826b9cff
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873918"
---
# <a name="get-a-list-of-trial-conversion-offers"></a><span data-ttu-id="18451-103">Een lijst met aanbiedingen voor omzetten van de proefversie ophalen</span><span class="sxs-lookup"><span data-stu-id="18451-103">Get a list of trial conversion offers</span></span>

<span data-ttu-id="18451-104">Een lijst met aanbiedingen voor proefconversie ophalen.</span><span class="sxs-lookup"><span data-stu-id="18451-104">How to retrieve a list of trial conversion offers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="18451-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="18451-105">Prerequisites</span></span>

- <span data-ttu-id="18451-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="18451-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="18451-107">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="18451-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="18451-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="18451-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="18451-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="18451-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="18451-110">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="18451-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="18451-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="18451-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="18451-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="18451-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="18451-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="18451-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="18451-114">Een abonnements-id voor een actief proefabonnement.</span><span class="sxs-lookup"><span data-stu-id="18451-114">A subscription ID for an active trial subscription.</span></span>

## <a name="c"></a><span data-ttu-id="18451-115">C\#</span><span class="sxs-lookup"><span data-stu-id="18451-115">C\#</span></span>

<span data-ttu-id="18451-116">Als u een lijst met beschikbare proefconversies wilt, gebruikt u eerst de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="18451-116">To get a list of trial conversions available, start by using the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="18451-117">Haal vervolgens een interface op voor abonnementsbewerkingen door de methode [**Subscriptions.ById aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) te roepen met de abonnements-id van het proefabonnement.</span><span class="sxs-lookup"><span data-stu-id="18451-117">Then, get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the trial subscription ID.</span></span> <span data-ttu-id="18451-118">Gebruik vervolgens de eigenschap [**Conversies**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) om een interface te verkrijgen voor de beschikbare bewerkingen op conversies en roep vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) aan om een verzameling beschikbare conversieaanbiedingen [**op te**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) halen.</span><span class="sxs-lookup"><span data-stu-id="18451-118">Next, use the [**Conversions**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) property to obtain an interface to the available operations on conversions, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) method to retrieve a collection of available [**Conversion**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) offers.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

// Get the available conversions.
var conversions =
    partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId).Conversions.Get();
```

## <a name="rest-request"></a><span data-ttu-id="18451-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="18451-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="18451-120">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="18451-120">Request syntax</span></span>

| <span data-ttu-id="18451-121">Methode</span><span class="sxs-lookup"><span data-stu-id="18451-121">Method</span></span>  | <span data-ttu-id="18451-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="18451-122">Request URI</span></span>                                                                                                                 |
|---------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="18451-123">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="18451-123">**GET**</span></span> | <span data-ttu-id="18451-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="18451-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="18451-125">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="18451-125">URI parameter</span></span>

<span data-ttu-id="18451-126">Gebruik de volgende padparameters om het klant- en proefabonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="18451-126">Use the following path parameters to identify the customer and trial subscription.</span></span>

| <span data-ttu-id="18451-127">Naam</span><span class="sxs-lookup"><span data-stu-id="18451-127">Name</span></span>            | <span data-ttu-id="18451-128">Type</span><span class="sxs-lookup"><span data-stu-id="18451-128">Type</span></span>   | <span data-ttu-id="18451-129">Vereist</span><span class="sxs-lookup"><span data-stu-id="18451-129">Required</span></span> | <span data-ttu-id="18451-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="18451-130">Description</span></span>                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="18451-131">customer-id</span><span class="sxs-lookup"><span data-stu-id="18451-131">customer-id</span></span>     | <span data-ttu-id="18451-132">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="18451-132">string</span></span> | <span data-ttu-id="18451-133">Ja</span><span class="sxs-lookup"><span data-stu-id="18451-133">Yes</span></span>      | <span data-ttu-id="18451-134">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="18451-134">A GUID formatted string that identifies the customer.</span></span>           |
| <span data-ttu-id="18451-135">subscription-id</span><span class="sxs-lookup"><span data-stu-id="18451-135">subscription-id</span></span> | <span data-ttu-id="18451-136">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="18451-136">string</span></span> | <span data-ttu-id="18451-137">Ja</span><span class="sxs-lookup"><span data-stu-id="18451-137">Yes</span></span>      | <span data-ttu-id="18451-138">Een tekenreeks met GUID-indeling die het proefabonnement identificeert.</span><span class="sxs-lookup"><span data-stu-id="18451-138">A GUID formatted string that identifies the trial subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="18451-139">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="18451-139">Request headers</span></span>

<span data-ttu-id="18451-140">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="18451-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="18451-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="18451-141">Request body</span></span>

<span data-ttu-id="18451-142">Geen.</span><span class="sxs-lookup"><span data-stu-id="18451-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="18451-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="18451-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/488745B5-2086-4912-802C-6ABB9F7C3638/conversions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e17f5bc6-24bf-4cbe-b632-d7fc6cec3058
MS-CorrelationId: 8daa6d54-72ab-4d6b-9c7d-9266d3734a47
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="18451-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="18451-144">REST response</span></span>

<span data-ttu-id="18451-145">Als dit lukt, bevat de antwoord-body een verzameling [conversieresources.](conversions-resources.md#conversionresult)</span><span class="sxs-lookup"><span data-stu-id="18451-145">If successful, the response body contains a collection of [Conversion](conversions-resources.md#conversionresult) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="18451-146">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="18451-146">Response success and error codes</span></span>

<span data-ttu-id="18451-147">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="18451-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="18451-148">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="18451-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="18451-149">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="18451-149">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="18451-150">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="18451-150">Response example</span></span>

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
