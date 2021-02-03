---
title: Een proefabonnement converteren naar betaald
description: Meer informatie over het gebruik van partner Center-Api's voor het converteren van een proef abonnement op een betaalde versie.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 59dcf6caf21d407b2fba4cc8438bc435fda9dc77
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2020
ms.locfileid: "97767616"
---
# <a name="convert-a-trial-subscription-to-paid-using-partner-center-apis"></a><span data-ttu-id="56c30-103">Een proef abonnement converteren naar betaald met partner Center-Api's</span><span class="sxs-lookup"><span data-stu-id="56c30-103">Convert a trial subscription to paid using Partner Center APIs</span></span>

<span data-ttu-id="56c30-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="56c30-104">**Applies to:**</span></span>

- <span data-ttu-id="56c30-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="56c30-105">Partner Center</span></span>

<span data-ttu-id="56c30-106">U kunt een proef abonnement converteren naar betaald.</span><span class="sxs-lookup"><span data-stu-id="56c30-106">You can convert a trial subscription to paid.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="56c30-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="56c30-107">Prerequisites</span></span>

- <span data-ttu-id="56c30-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="56c30-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="56c30-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="56c30-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="56c30-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="56c30-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="56c30-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="56c30-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="56c30-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="56c30-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="56c30-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="56c30-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="56c30-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="56c30-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="56c30-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="56c30-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="56c30-116">Een abonnements-ID voor een actief proef abonnement.</span><span class="sxs-lookup"><span data-stu-id="56c30-116">A subscription ID for an active trial subscription.</span></span>

- <span data-ttu-id="56c30-117">Een beschik bare conversie aanbieding.</span><span class="sxs-lookup"><span data-stu-id="56c30-117">An available conversion offer.</span></span>

## <a name="convert-a-trial-subscription-to-paid-through-code"></a><span data-ttu-id="56c30-118">Een proef abonnement converteren naar betaald via code</span><span class="sxs-lookup"><span data-stu-id="56c30-118">Convert a trial subscription to paid through code</span></span>

<span data-ttu-id="56c30-119">Als u een proef abonnement wilt omzetten in een betaalde versie, moet u eerst een verzameling van de beschik bare proef versies ophalen.</span><span class="sxs-lookup"><span data-stu-id="56c30-119">To convert a trial subscription to a paid one, you must first obtain a collection of the trial conversions available.</span></span> <span data-ttu-id="56c30-120">Vervolgens moet u het conversie aanbod kiezen dat u wilt kopen.</span><span class="sxs-lookup"><span data-stu-id="56c30-120">Then, you must choose the conversion offer that you want to purchase.</span></span>

<span data-ttu-id="56c30-121">In de conversie aanbiedingen wordt een hoeveelheid opgegeven die standaard hetzelfde aantal licenties heeft als het proef abonnement.</span><span class="sxs-lookup"><span data-stu-id="56c30-121">The conversion offers will specify a quantity that defaults to the same number of licenses as the trial subscription.</span></span> <span data-ttu-id="56c30-122">U kunt dit aantal wijzigen door de eigenschap [**hoeveelheid**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion.quantity) in te stellen op het aantal licenties dat u wilt kopen.</span><span class="sxs-lookup"><span data-stu-id="56c30-122">You can change this quantity by setting the [**Quantity**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion.quantity) property to the number of licenses that you want to purchase.</span></span>

> [!NOTE]
> <span data-ttu-id="56c30-123">Ongeacht het aantal aangeschafte licenties, wordt de abonnements-ID van de proef versie opnieuw gebruikt voor de aangeschafte licenties.</span><span class="sxs-lookup"><span data-stu-id="56c30-123">Regardless of the number of licenses purchased, the subscription ID of the trial is reused for the purchased licenses.</span></span> <span data-ttu-id="56c30-124">Als gevolg hiervan verdwijnt de proef versie en wordt deze vervangen door de aankoop.</span><span class="sxs-lookup"><span data-stu-id="56c30-124">As a result, the trial in effect disappears and is replaced by the purchase.</span></span>

<span data-ttu-id="56c30-125">Voer de volgende stappen uit om een proef abonnement te converteren met behulp van code:</span><span class="sxs-lookup"><span data-stu-id="56c30-125">Use the following steps to convert a trial subscription through code:</span></span>

1. <span data-ttu-id="56c30-126">Een interface voor de beschik bare abonnements bewerkingen ophalen.</span><span class="sxs-lookup"><span data-stu-id="56c30-126">Get an interface to the subscription operations available.</span></span> <span data-ttu-id="56c30-127">U moet de klant identificeren en de abonnements-id van het proef abonnement opgeven.</span><span class="sxs-lookup"><span data-stu-id="56c30-127">You must identify the customer and specify the subscription identifier of the trial subscription.</span></span>

    ``` csharp
    var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
    ```

2. <span data-ttu-id="56c30-128">Een verzameling van de beschik bare conversie aanbiedingen ophalen.</span><span class="sxs-lookup"><span data-stu-id="56c30-128">Get a collection of the available conversion offers.</span></span> <span data-ttu-id="56c30-129">Zie voor meer informatie en Details over de aanvraag/reactie voor deze methode [een lijst met aanbiedingen voor proef conversie ophalen](get-a-list-of-trial-conversion-offers.md).</span><span class="sxs-lookup"><span data-stu-id="56c30-129">For more information and details on the request/response for this method, see [Get a list of trial conversion offers](get-a-list-of-trial-conversion-offers.md).</span></span>

    ``` csharp
    var conversions = subscriptionOperations.Conversions.Get();
    ```

3. <span data-ttu-id="56c30-130">Kies een conversie aanbieding.</span><span class="sxs-lookup"><span data-stu-id="56c30-130">Choose a conversion offer.</span></span> <span data-ttu-id="56c30-131">Met de volgende code wordt de eerste conversie aanbieding in de verzameling gekozen.</span><span class="sxs-lookup"><span data-stu-id="56c30-131">The following code chooses the first conversion offer in the collection.</span></span>

    ``` csharp
    var selectedConversion = conversions.Items.ToList()[0];
    ```

4. <span data-ttu-id="56c30-132">Geef desgewenst het aantal licenties op dat u wilt aanschaffen.</span><span class="sxs-lookup"><span data-stu-id="56c30-132">Optionally, specify the number of licenses to purchase.</span></span> <span data-ttu-id="56c30-133">De standaard waarde is het aantal licenties in het proef abonnement.</span><span class="sxs-lookup"><span data-stu-id="56c30-133">The default is the number of licenses in the trial subscription.</span></span>

    ``` csharp
    selectedConversion.Quantity = 10;
    ```

5. <span data-ttu-id="56c30-134">Roep de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) aan om het proef abonnement te converteren naar betaald.</span><span class="sxs-lookup"><span data-stu-id="56c30-134">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) method to convert the trial subscription to paid.</span></span>

    ``` csharp
    var convertResult = subscriptionOperations.Conversions.Create(selectedConversion);
    ```

## <a name="c"></a><span data-ttu-id="56c30-135">C\#</span><span class="sxs-lookup"><span data-stu-id="56c30-135">C\#</span></span>

<span data-ttu-id="56c30-136">U kunt als volgt een proef abonnement omzetten naar een betaalde versie:</span><span class="sxs-lookup"><span data-stu-id="56c30-136">To convert a trial subscription to a paid one:</span></span>

1. <span data-ttu-id="56c30-137">Gebruik de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="56c30-137">Use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="56c30-138">Een interface voor het uitvoeren van abonnementen ophalen door de methode [**abonnementen. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) aan te roepen met de id van het proef abonnement.</span><span class="sxs-lookup"><span data-stu-id="56c30-138">Get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the trial subscription ID.</span></span> <span data-ttu-id="56c30-139">Sla een verwijzing op naar de operations-interface van het abonnement in een lokale variabele.</span><span class="sxs-lookup"><span data-stu-id="56c30-139">Save a reference to the subscription operations interface in a local variable.</span></span>

3. <span data-ttu-id="56c30-140">Gebruik de eigenschap [**conversies**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) om een interface te verkrijgen voor de beschik bare bewerkingen op conversies en roep vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) aan om een verzameling beschik bare [**conversie**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) aanbiedingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="56c30-140">Use the [**Conversions**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) property to obtain an interface to the available operations on conversions, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) method to retrieve a collection of available [**Conversion**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) offers.</span></span> <span data-ttu-id="56c30-141">U moet er een kiezen.</span><span class="sxs-lookup"><span data-stu-id="56c30-141">You must choose one.</span></span> <span data-ttu-id="56c30-142">In het volgende voor beeld wordt standaard de eerste conversie beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="56c30-142">The following example defaults to the first conversion available.</span></span>

4. <span data-ttu-id="56c30-143">Gebruik de verwijzing naar de operations-interface voor abonnementen die u hebt opgeslagen in een lokale variabele en de eigenschap [**conversies**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) om een interface te verkrijgen voor de beschik bare bewerkingen op conversies.</span><span class="sxs-lookup"><span data-stu-id="56c30-143">Use the reference to the subscription operations interface that you saved in a local variable and the [**Conversions**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) property to obtain an interface to the available operations on conversions.</span></span>

5. <span data-ttu-id="56c30-144">Geef het geselecteerde object voor de conversie aanbieding door aan de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) om de proef versie te converteren.</span><span class="sxs-lookup"><span data-stu-id="56c30-144">Pass the selected conversion offer object to the [**Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) method to attempt the trial conversion.</span></span>

### <a name="c-example"></a><span data-ttu-id="56c30-145">C- \# voor beeld</span><span class="sxs-lookup"><span data-stu-id="56c30-145">C\# example</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

// Get subscription operations for the trial subscription.
var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);

// Get the available conversions.
var conversions = subscriptionOperations.Conversions.Get();

// If there are no conversions available, we&#39;re done.
// Otherwise, convert the trial to the first available conversion offer.
if (conversions.TotalCount <= 0)
{
    System.Console.WriteLine("This subscription has no conversions");
}
else
{
    // Default to the first conversion.
    var selectedConversion = conversions.Items.ToList()[0];

    // Convert the trial and return the result.
    var convertResult = subscriptionOperations.Conversions.Create(selectedConversion);
}
```

## <a name="rest-request"></a><span data-ttu-id="56c30-146">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="56c30-146">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="56c30-147">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="56c30-147">Request syntax</span></span>

| <span data-ttu-id="56c30-148">Methode</span><span class="sxs-lookup"><span data-stu-id="56c30-148">Method</span></span>   | <span data-ttu-id="56c30-149">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="56c30-149">Request URI</span></span>                                                                                                                 |
|----------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="56c30-150">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="56c30-150">**POST**</span></span> | <span data-ttu-id="56c30-151">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Subscriptions/{Subscription-id}/conversions http/1.1</span><span class="sxs-lookup"><span data-stu-id="56c30-151">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="56c30-152">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="56c30-152">URI parameter</span></span>

<span data-ttu-id="56c30-153">Gebruik de volgende Path-para meters om het klant-en proef abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="56c30-153">Use the following path parameters to identify the customer and trial subscription.</span></span>

| <span data-ttu-id="56c30-154">Naam</span><span class="sxs-lookup"><span data-stu-id="56c30-154">Name</span></span>            | <span data-ttu-id="56c30-155">Type</span><span class="sxs-lookup"><span data-stu-id="56c30-155">Type</span></span>   | <span data-ttu-id="56c30-156">Vereist</span><span class="sxs-lookup"><span data-stu-id="56c30-156">Required</span></span> | <span data-ttu-id="56c30-157">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="56c30-157">Description</span></span>                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="56c30-158">klant-id</span><span class="sxs-lookup"><span data-stu-id="56c30-158">customer-id</span></span>     | <span data-ttu-id="56c30-159">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="56c30-159">string</span></span> | <span data-ttu-id="56c30-160">Yes</span><span class="sxs-lookup"><span data-stu-id="56c30-160">Yes</span></span>      | <span data-ttu-id="56c30-161">Een teken reeks met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="56c30-161">A GUID formatted string that identifies the customer.</span></span>           |
| <span data-ttu-id="56c30-162">abonnement-id</span><span class="sxs-lookup"><span data-stu-id="56c30-162">subscription-id</span></span> | <span data-ttu-id="56c30-163">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="56c30-163">string</span></span> | <span data-ttu-id="56c30-164">Yes</span><span class="sxs-lookup"><span data-stu-id="56c30-164">Yes</span></span>      | <span data-ttu-id="56c30-165">Een teken reeks met een GUID-indeling waarmee het proef abonnement wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="56c30-165">A GUID formatted string that identifies the trial subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="56c30-166">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="56c30-166">Request headers</span></span>

<span data-ttu-id="56c30-167">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="56c30-167">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="56c30-168">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="56c30-168">Request body</span></span>

<span data-ttu-id="56c30-169">Een gevulde [conversie](conversions-resources.md#conversion) resource moet worden opgenomen in de hoofd tekst van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="56c30-169">A populated [Conversion](conversions-resources.md#conversion) resource must be included in the request body.</span></span>

### <a name="request-example"></a><span data-ttu-id="56c30-170">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="56c30-170">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/488745B5-2086-4912-802C-6ABB9F7C3638/conversions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bd0cde7f-ba87-4010-8a73-1190b641f2a4
MS-CorrelationId: 8daa6d54-72ab-4d6b-9c7d-9266d3734a47
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 234
Expect: 100-continue

{
    "OfferId": "C0BD2E08-11AC-4836-BDC7-3712E744922F",
    "TargetOfferId": "031C9E47-4802-4248-838E-778FB1D2CC05",
    "OrderId": "D51A052E-043C-4A2A-AA37-2BB938CEF6C1",
    "Quantity": 25,
    "BillingCycle": "monthly",
    "Attributes": {
        "ObjectType": "Conversion"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="56c30-171">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="56c30-171">REST response</span></span>

<span data-ttu-id="56c30-172">Als dit lukt, bevat de antwoord tekst een [ConversionResult](conversions-resources.md#conversionresult) -resource.</span><span class="sxs-lookup"><span data-stu-id="56c30-172">If successful, the response body contains a [ConversionResult](conversions-resources.md#conversionresult) resource.</span></span>

#### <a name="response-success-and-error-codes"></a><span data-ttu-id="56c30-173">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="56c30-173">Response success and error codes</span></span>

<span data-ttu-id="56c30-174">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="56c30-174">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="56c30-175">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="56c30-175">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="56c30-176">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="56c30-176">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

#### <a name="response-example"></a><span data-ttu-id="56c30-177">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="56c30-177">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 211
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 8daa6d54-72ab-4d6b-9c7d-9266d3734a47
MS-RequestId: bd0cde7f-ba87-4010-8a73-1190b641f2a4
MS-CV: kW4GzmhvHEqCq1ls.0
MS-ServerId: 030020643
Date: Thu, 15 Jun 2017 23:10:40 GMT

 {
    "subscriptionId": "488745B5-2086-4912-802C-6ABB9F7C3638",
    "offerId": "C0BD2E08-11AC-4836-BDC7-3712E744922F",
    "targetOfferId": "031C9E47-4802-4248-838E-778FB1D2CC05",
    "attributes": {
        "objectType": "ConversionResult"
    }
}
```
