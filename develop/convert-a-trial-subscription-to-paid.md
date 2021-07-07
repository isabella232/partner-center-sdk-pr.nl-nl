---
title: Een proefabonnement converteren naar betaald
description: Meer informatie over het gebruik Partner Center API's om een proefabonnement te converteren naar een betaald abonnement.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c1876cfc796b683bfff00b7d137bcfe0b7162c78
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973856"
---
# <a name="convert-a-trial-subscription-to-paid-using-partner-center-apis"></a><span data-ttu-id="5bacd-103">Een proefabonnement converteren naar betaald met behulp Partner Center API's</span><span class="sxs-lookup"><span data-stu-id="5bacd-103">Convert a trial subscription to paid using Partner Center APIs</span></span>

<span data-ttu-id="5bacd-104">U kunt een proefabonnement converteren naar betaald.</span><span class="sxs-lookup"><span data-stu-id="5bacd-104">You can convert a trial subscription to paid.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5bacd-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="5bacd-105">Prerequisites</span></span>

- <span data-ttu-id="5bacd-106">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="5bacd-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5bacd-107">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="5bacd-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="5bacd-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5bacd-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="5bacd-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="5bacd-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="5bacd-110">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="5bacd-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="5bacd-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="5bacd-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="5bacd-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="5bacd-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="5bacd-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5bacd-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="5bacd-114">Een abonnements-id voor een actief proefabonnement.</span><span class="sxs-lookup"><span data-stu-id="5bacd-114">A subscription ID for an active trial subscription.</span></span>

- <span data-ttu-id="5bacd-115">Een beschikbare conversieaanbieding.</span><span class="sxs-lookup"><span data-stu-id="5bacd-115">An available conversion offer.</span></span>

## <a name="convert-a-trial-subscription-to-a-paid-subscription-through-code"></a><span data-ttu-id="5bacd-116">Een proefabonnement converteren naar een betaald abonnement via code</span><span class="sxs-lookup"><span data-stu-id="5bacd-116">Convert a trial subscription to a paid subscription through code</span></span>

<span data-ttu-id="5bacd-117">Als u een proefabonnement wilt converteren naar een betaald abonnement, moet u eerst een verzameling van de beschikbare proefversies verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="5bacd-117">To convert a trial subscription to a paid one, you must first obtain a collection of the trial conversions available.</span></span> <span data-ttu-id="5bacd-118">Vervolgens moet u de conversieaanbieding kiezen die u wilt kopen.</span><span class="sxs-lookup"><span data-stu-id="5bacd-118">Then, you must choose the conversion offer that you want to purchase.</span></span>

<span data-ttu-id="5bacd-119">Met de conversieaanbiedingen wordt een hoeveelheid opgegeven die standaard hetzelfde aantal licenties heeft als het proefabonnement.</span><span class="sxs-lookup"><span data-stu-id="5bacd-119">The conversion offers will specify a quantity that defaults to the same number of licenses as the trial subscription.</span></span> <span data-ttu-id="5bacd-120">U kunt deze hoeveelheid wijzigen door de eigenschap [**Quantity**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion.quantity) in te stellen op het aantal licenties dat u wilt kopen.</span><span class="sxs-lookup"><span data-stu-id="5bacd-120">You can change this quantity by setting the [**Quantity**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion.quantity) property to the number of licenses that you want to purchase.</span></span>

> [!NOTE]
> <span data-ttu-id="5bacd-121">Ongeacht het aantal aangeschafte licenties, wordt de abonnements-id van de proefversie opnieuw gebruikt voor de aangeschafte licenties.</span><span class="sxs-lookup"><span data-stu-id="5bacd-121">Regardless of the number of licenses purchased, the subscription ID of the trial is reused for the purchased licenses.</span></span> <span data-ttu-id="5bacd-122">Als gevolg hiervan verdwijnt de proefversie van kracht en wordt deze vervangen door de aankoop.</span><span class="sxs-lookup"><span data-stu-id="5bacd-122">As a result, the trial in effect disappears and is replaced by the purchase.</span></span>

<span data-ttu-id="5bacd-123">Gebruik de volgende stappen om een proefabonnement te converteren via code:</span><span class="sxs-lookup"><span data-stu-id="5bacd-123">Use the following steps to convert a trial subscription through code:</span></span>

1. <span data-ttu-id="5bacd-124">Haal een interface op voor de beschikbare abonnementsbewerkingen.</span><span class="sxs-lookup"><span data-stu-id="5bacd-124">Get an interface to the subscription operations available.</span></span> <span data-ttu-id="5bacd-125">U moet de klant identificeren en de abonnements-id van het proefabonnement opgeven.</span><span class="sxs-lookup"><span data-stu-id="5bacd-125">You must identify the customer and specify the subscription identifier of the trial subscription.</span></span>

    ``` csharp
    var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
    ```

2. <span data-ttu-id="5bacd-126">Een verzameling van de beschikbare conversieaanbiedingen ophalen.</span><span class="sxs-lookup"><span data-stu-id="5bacd-126">Get a collection of the available conversion offers.</span></span> <span data-ttu-id="5bacd-127">Zie Get a list of trial conversion offers (Een lijst met aanbiedingen voor proefconversie verkrijgen) voor meer informatie en details over de aanvraag/reactie [voor deze methode.](get-a-list-of-trial-conversion-offers.md)</span><span class="sxs-lookup"><span data-stu-id="5bacd-127">For more information and details on the request/response for this method, see [Get a list of trial conversion offers](get-a-list-of-trial-conversion-offers.md).</span></span>

    ``` csharp
    var conversions = subscriptionOperations.Conversions.Get();
    ```

3. <span data-ttu-id="5bacd-128">Kies een conversieaanbieding.</span><span class="sxs-lookup"><span data-stu-id="5bacd-128">Choose a conversion offer.</span></span> <span data-ttu-id="5bacd-129">Met de volgende code wordt de eerste conversieaanbieding in de verzameling gekozen.</span><span class="sxs-lookup"><span data-stu-id="5bacd-129">The following code chooses the first conversion offer in the collection.</span></span>

    ``` csharp
    var selectedConversion = conversions.Items.ToList()[0];
    ```

4. <span data-ttu-id="5bacd-130">Geef desgewenst het aantal licenties op dat moet worden gekocht.</span><span class="sxs-lookup"><span data-stu-id="5bacd-130">Optionally, specify the number of licenses to purchase.</span></span> <span data-ttu-id="5bacd-131">De standaardwaarde is het aantal licenties in het proefabonnement.</span><span class="sxs-lookup"><span data-stu-id="5bacd-131">The default is the number of licenses in the trial subscription.</span></span>

    ``` csharp
    selectedConversion.Quantity = 10;
    ```

5. <span data-ttu-id="5bacd-132">Roep de [**methode Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) of [**CreateAsync aan**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) om het proefabonnement te converteren naar betaald.</span><span class="sxs-lookup"><span data-stu-id="5bacd-132">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) method to convert the trial subscription to paid.</span></span>

    ``` csharp
    var convertResult = subscriptionOperations.Conversions.Create(selectedConversion);
    ```

## <a name="c"></a><span data-ttu-id="5bacd-133">C\#</span><span class="sxs-lookup"><span data-stu-id="5bacd-133">C\#</span></span>

<span data-ttu-id="5bacd-134">Een proefabonnement converteren naar een betaald abonnement:</span><span class="sxs-lookup"><span data-stu-id="5bacd-134">To convert a trial subscription to a paid one:</span></span>

1. <span data-ttu-id="5bacd-135">Gebruik de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="5bacd-135">Use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="5bacd-136">Haal een interface op voor abonnementsbewerkingen door de methode [**Subscriptions.ById aan te**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) roepen met de abonnements-id van het proefabonnement.</span><span class="sxs-lookup"><span data-stu-id="5bacd-136">Get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the trial subscription ID.</span></span> <span data-ttu-id="5bacd-137">Sla een verwijzing naar de interface voor abonnementsbewerkingen op in een lokale variabele.</span><span class="sxs-lookup"><span data-stu-id="5bacd-137">Save a reference to the subscription operations interface in a local variable.</span></span>

3. <span data-ttu-id="5bacd-138">Gebruik de [**eigenschap Conversies**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) om een interface te verkrijgen voor de beschikbare bewerkingen op conversies en roep vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) aan om een verzameling beschikbare conversieaanbiedingen [**op te**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) halen.</span><span class="sxs-lookup"><span data-stu-id="5bacd-138">Use the [**Conversions**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) property to obtain an interface to the available operations on conversions, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) method to retrieve a collection of available [**Conversion**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) offers.</span></span> <span data-ttu-id="5bacd-139">U moet er een kiezen.</span><span class="sxs-lookup"><span data-stu-id="5bacd-139">You must choose one.</span></span> <span data-ttu-id="5bacd-140">In het volgende voorbeeld wordt standaard de eerste beschikbare conversie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5bacd-140">The following example defaults to the first conversion available.</span></span>

4. <span data-ttu-id="5bacd-141">Gebruik de verwijzing naar de interface voor [**abonnementsbewerkingen**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) die u hebt opgeslagen in een lokale variabele en de eigenschap Conversies om een interface te verkrijgen voor de beschikbare bewerkingen op conversies.</span><span class="sxs-lookup"><span data-stu-id="5bacd-141">Use the reference to the subscription operations interface that you saved in a local variable and the [**Conversions**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) property to obtain an interface to the available operations on conversions.</span></span>

5. <span data-ttu-id="5bacd-142">Geef het geselecteerde conversieaanbiedingsobject door aan [**de methode Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) om de conversie van het proefabonnement te proberen.</span><span class="sxs-lookup"><span data-stu-id="5bacd-142">Pass the selected conversion offer object to the [**Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) method to attempt the trial conversion.</span></span>

### <a name="c-example"></a><span data-ttu-id="5bacd-143">\#C-voorbeeld</span><span class="sxs-lookup"><span data-stu-id="5bacd-143">C\# example</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="5bacd-144">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="5bacd-144">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5bacd-145">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="5bacd-145">Request syntax</span></span>

| <span data-ttu-id="5bacd-146">Methode</span><span class="sxs-lookup"><span data-stu-id="5bacd-146">Method</span></span>   | <span data-ttu-id="5bacd-147">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="5bacd-147">Request URI</span></span>                                                                                                                 |
|----------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5bacd-148">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="5bacd-148">**POST**</span></span> | <span data-ttu-id="5bacd-149">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="5bacd-149">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="5bacd-150">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="5bacd-150">URI parameter</span></span>

<span data-ttu-id="5bacd-151">Gebruik de volgende padparameters om de klant en het proefabonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="5bacd-151">Use the following path parameters to identify the customer and trial subscription.</span></span>

| <span data-ttu-id="5bacd-152">Naam</span><span class="sxs-lookup"><span data-stu-id="5bacd-152">Name</span></span>            | <span data-ttu-id="5bacd-153">Type</span><span class="sxs-lookup"><span data-stu-id="5bacd-153">Type</span></span>   | <span data-ttu-id="5bacd-154">Vereist</span><span class="sxs-lookup"><span data-stu-id="5bacd-154">Required</span></span> | <span data-ttu-id="5bacd-155">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5bacd-155">Description</span></span>                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="5bacd-156">customer-id</span><span class="sxs-lookup"><span data-stu-id="5bacd-156">customer-id</span></span>     | <span data-ttu-id="5bacd-157">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="5bacd-157">string</span></span> | <span data-ttu-id="5bacd-158">Ja</span><span class="sxs-lookup"><span data-stu-id="5bacd-158">Yes</span></span>      | <span data-ttu-id="5bacd-159">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="5bacd-159">A GUID formatted string that identifies the customer.</span></span>           |
| <span data-ttu-id="5bacd-160">subscription-id</span><span class="sxs-lookup"><span data-stu-id="5bacd-160">subscription-id</span></span> | <span data-ttu-id="5bacd-161">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="5bacd-161">string</span></span> | <span data-ttu-id="5bacd-162">Ja</span><span class="sxs-lookup"><span data-stu-id="5bacd-162">Yes</span></span>      | <span data-ttu-id="5bacd-163">Een tekenreeks met GUID-indeling die het proefabonnement identificeert.</span><span class="sxs-lookup"><span data-stu-id="5bacd-163">A GUID formatted string that identifies the trial subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="5bacd-164">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="5bacd-164">Request headers</span></span>

<span data-ttu-id="5bacd-165">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="5bacd-165">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5bacd-166">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="5bacd-166">Request body</span></span>

<span data-ttu-id="5bacd-167">Een ingevulde [conversieresource](conversions-resources.md#conversion) moet worden opgenomen in de aanvraag body.</span><span class="sxs-lookup"><span data-stu-id="5bacd-167">A populated [Conversion](conversions-resources.md#conversion) resource must be included in the request body.</span></span>

### <a name="request-example"></a><span data-ttu-id="5bacd-168">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="5bacd-168">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="5bacd-169">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="5bacd-169">REST response</span></span>

<span data-ttu-id="5bacd-170">Als dit lukt, bevat de antwoord-body een [ConversionResult-resource.](conversions-resources.md#conversionresult)</span><span class="sxs-lookup"><span data-stu-id="5bacd-170">If successful, the response body contains a [ConversionResult](conversions-resources.md#conversionresult) resource.</span></span>

#### <a name="response-success-and-error-codes"></a><span data-ttu-id="5bacd-171">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="5bacd-171">Response success and error codes</span></span>

<span data-ttu-id="5bacd-172">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="5bacd-172">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5bacd-173">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="5bacd-173">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5bacd-174">Zie voor de volledige lijst Partner Center [foutcodes.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="5bacd-174">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

#### <a name="response-example"></a><span data-ttu-id="5bacd-175">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="5bacd-175">Response example</span></span>

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
