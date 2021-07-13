---
title: Een adres valideren
description: Een adres valideren met behulp van de adresvalidatie-API.
ms.date: 05/17/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 30f5cd526ab038dce400e79822d89b8086ba3799
ms.sourcegitcommit: 41bf9dca55f4c96d382b327a75b2d2418edfc9bc
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/13/2021
ms.locfileid: "113655622"
---
# <a name="validate-an-address"></a><span data-ttu-id="2ccb4-103">Een adres valideren</span><span class="sxs-lookup"><span data-stu-id="2ccb4-103">Validate an address</span></span>

<span data-ttu-id="2ccb4-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2ccb4-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2ccb4-105">Een adres valideren met behulp van de adresvalidatie-API.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-105">How to validate an address using the address validation API.</span></span>

<span data-ttu-id="2ccb4-106">De adresvalidatie-API mag alleen worden gebruikt voor de prevalidatie van updates van klantprofiel.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-106">The address validation API should only be used for pre-validation of customer profile updates.</span></span> <span data-ttu-id="2ccb4-107">Gebruik het veld met de kennis dat als het land de Verenigde Staten, Canada, China of Mexico is, het veld Staat wordt gevalideerd met een lijst met geldige staten voor het desbetreffende land.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-107">Use it with the understanding that if the country is the United States, Canada, China, or Mexico, the state field is validated against a list of valid states for the respective country.</span></span> <span data-ttu-id="2ccb4-108">In alle andere landen wordt deze test niet uitgevoerd en controleert de API alleen of de status een geldige tekenreeks is.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-108">In all other countries, this test does not occur, and the API only checks that the state is a valid string.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ccb4-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2ccb4-109">Prerequisites</span></span>

<span data-ttu-id="2ccb4-110">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2ccb4-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2ccb4-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="2ccb4-112">C\#</span><span class="sxs-lookup"><span data-stu-id="2ccb4-112">C\#</span></span>

<span data-ttu-id="2ccb4-113">Als u een adres wilt valideren, instantieert u eerst een nieuw **adresobject** en vult u dit met het adres dat u wilt valideren.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-113">To validate an address, first instantiate a new **Address** object and populate it with the address to validate.</span></span> <span data-ttu-id="2ccb4-114">Haal vervolgens een interface op voor **validatiebewerkingen** van de eigenschap **IAggregatePartner.Validations** en roep de **methode IsAddressValid** aan met het adresobject.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-114">Then, retrieve an interface to **Validations** operations from the **IAggregatePartner.Validations** property, and call the **IsAddressValid** method with the address object.</span></span>

```csharp
IAggregatePartner partnerOperations;

// Create an address to validate.
Address address = new Address()
{
    AddressLine1 = "One Microsoft Way",
    City = "Redmond",
    State = "WA",
    PostalCode = "98052",
    Country = "US"
};

// Validate the address.
AddressValidationResponse result = partnerOperations.Validations.IsAddressValid(address);

// If the request completes successfully, you can inspect the response object.

// See the status of the validation.
Console.WriteLine($"Status: {addressValidationResult.Status}");

// See the validation message returned.
Console.WriteLine($"Validation Message Returned: {addressValidationResult.ValidationMessage ?? "No message returned."}");

// See the original address submitted for validation.
Console.WriteLine($"Original Address:\n{this.DisplayAddress(addressValidationResult.OriginalAddress)}");

// See the suggested addresses returned by the API, if any exist.
Console.WriteLine($"Suggested Addresses Returned: {addressValidationResult.SuggestedAddresses?.Count ?? "None."}");

if (addressValidationResult.SuggestedAddresses != null && addressValidationResult.SuggestedAddresses.Any())
{
    addressValidationResult.SuggestedAddresses.ForEach(a => Console.WriteLine(this.DisplayAddress(a)));
}

// Helper method to pretty-print an Address object.
private string DisplayAddress(Address address)
{
    StringBuilder sb = new StringBuilder();

    foreach (var property in address.GetType().GetProperties())
    {
        sb.AppendLine($"{property.Name}: {property.GetValue(address) ?? "None to Display."}");
    }

    return sb.ToString();
}
```

## <a name="rest-request"></a><span data-ttu-id="2ccb4-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="2ccb4-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2ccb4-116">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="2ccb4-116">Request syntax</span></span>

| <span data-ttu-id="2ccb4-117">Methode</span><span class="sxs-lookup"><span data-stu-id="2ccb4-117">Method</span></span>   | <span data-ttu-id="2ccb4-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="2ccb4-118">Request URI</span></span>                                                                 |
|----------|-----------------------------------------------------------------------------|
| <span data-ttu-id="2ccb4-119">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="2ccb4-119">**POST**</span></span> | <span data-ttu-id="2ccb4-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/validations/address HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="2ccb4-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/validations/address HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="2ccb4-121">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="2ccb4-121">Request headers</span></span>

<span data-ttu-id="2ccb4-122">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="2ccb4-122">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2ccb4-123">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="2ccb4-123">Request body</span></span>

<span data-ttu-id="2ccb4-124">In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-124">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="2ccb4-125">Naam</span><span class="sxs-lookup"><span data-stu-id="2ccb4-125">Name</span></span>         | <span data-ttu-id="2ccb4-126">Type</span><span class="sxs-lookup"><span data-stu-id="2ccb4-126">Type</span></span>   | <span data-ttu-id="2ccb4-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="2ccb4-127">Required</span></span> | <span data-ttu-id="2ccb4-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2ccb4-128">Description</span></span>                                                |
|--------------|--------|----------|------------------------------------------------------------|
| <span data-ttu-id="2ccb4-129">addressline1</span><span class="sxs-lookup"><span data-stu-id="2ccb4-129">addressline1</span></span> | <span data-ttu-id="2ccb4-130">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2ccb4-130">string</span></span> | <span data-ttu-id="2ccb4-131">J</span><span class="sxs-lookup"><span data-stu-id="2ccb4-131">Y</span></span>        | <span data-ttu-id="2ccb4-132">De eerste regel van het adres.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-132">The first line of the address.</span></span>                             |
| <span data-ttu-id="2ccb4-133">addressline2</span><span class="sxs-lookup"><span data-stu-id="2ccb4-133">addressline2</span></span> | <span data-ttu-id="2ccb4-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2ccb4-134">string</span></span> | <span data-ttu-id="2ccb4-135">N</span><span class="sxs-lookup"><span data-stu-id="2ccb4-135">N</span></span>        | <span data-ttu-id="2ccb4-136">De tweede regel van het adres.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-136">The second line of the address.</span></span> <span data-ttu-id="2ccb4-137">Deze eigenschap is optioneel.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-137">This property is optional.</span></span> |
| <span data-ttu-id="2ccb4-138">city</span><span class="sxs-lookup"><span data-stu-id="2ccb4-138">city</span></span>         | <span data-ttu-id="2ccb4-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2ccb4-139">string</span></span> | <span data-ttu-id="2ccb4-140">J</span><span class="sxs-lookup"><span data-stu-id="2ccb4-140">Y</span></span>        | <span data-ttu-id="2ccb4-141">De plaats.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-141">The city.</span></span>                                                  |
| <span data-ttu-id="2ccb4-142">staat</span><span class="sxs-lookup"><span data-stu-id="2ccb4-142">state</span></span>        | <span data-ttu-id="2ccb4-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2ccb4-143">string</span></span> | <span data-ttu-id="2ccb4-144">J</span><span class="sxs-lookup"><span data-stu-id="2ccb4-144">Y</span></span>        | <span data-ttu-id="2ccb4-145">De status.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-145">The state.</span></span>                                                 |
| <span data-ttu-id="2ccb4-146">postalcode</span><span class="sxs-lookup"><span data-stu-id="2ccb4-146">postalcode</span></span>   | <span data-ttu-id="2ccb4-147">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2ccb4-147">string</span></span> | <span data-ttu-id="2ccb4-148">J</span><span class="sxs-lookup"><span data-stu-id="2ccb4-148">Y</span></span>        | <span data-ttu-id="2ccb4-149">De postcode.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-149">The postal code.</span></span>                                           |
| <span data-ttu-id="2ccb4-150">country</span><span class="sxs-lookup"><span data-stu-id="2ccb4-150">country</span></span>      | <span data-ttu-id="2ccb4-151">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2ccb4-151">string</span></span> | <span data-ttu-id="2ccb4-152">J</span><span class="sxs-lookup"><span data-stu-id="2ccb4-152">Y</span></span>        | <span data-ttu-id="2ccb4-153">Het iso-2-landnummer met twee tekens.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-153">The two-character ISO alpha-2 country code.</span></span>                |

### <a name="response-details"></a><span data-ttu-id="2ccb4-154">Antwoorddetails</span><span class="sxs-lookup"><span data-stu-id="2ccb4-154">Response details</span></span>

<span data-ttu-id="2ccb4-155">Het antwoord retournt een van de volgende statusberichten:</span><span class="sxs-lookup"><span data-stu-id="2ccb4-155">The response will return one of the following status messages:</span></span>

| <span data-ttu-id="2ccb4-156">Status</span><span class="sxs-lookup"><span data-stu-id="2ccb4-156">Status</span></span>     | <span data-ttu-id="2ccb4-157">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2ccb4-157">Description</span></span> |    <span data-ttu-id="2ccb4-158">Aantal geretourneerde voorgestelde adressen</span><span class="sxs-lookup"><span data-stu-id="2ccb4-158">Number of suggested addresses returned</span></span> |
|-------|---------------|-------------------|
|<span data-ttu-id="2ccb4-159">Geverifieerd verzendbaar</span><span class="sxs-lookup"><span data-stu-id="2ccb4-159">Verified shippable</span></span> | <span data-ttu-id="2ccb4-160">Het adres wordt geverifieerd en kan worden verzonden naar .</span><span class="sxs-lookup"><span data-stu-id="2ccb4-160">Address is verified and can be shipped to.</span></span> | <span data-ttu-id="2ccb4-161">Enkelvoudig</span><span class="sxs-lookup"><span data-stu-id="2ccb4-161">Single</span></span> |
|<span data-ttu-id="2ccb4-162">Geverifieerd</span><span class="sxs-lookup"><span data-stu-id="2ccb4-162">Verified</span></span> | <span data-ttu-id="2ccb4-163">Het adres wordt geverifieerd.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-163">Address is verified.</span></span> | <span data-ttu-id="2ccb4-164">Enkelvoudig</span><span class="sxs-lookup"><span data-stu-id="2ccb4-164">Single</span></span> |
|<span data-ttu-id="2ccb4-165">Interactie vereist</span><span class="sxs-lookup"><span data-stu-id="2ccb4-165">Interaction required</span></span> | <span data-ttu-id="2ccb4-166">Voorgesteld adres is aanzienlijk gewijzigd en er is een gebruikersbevestiging nodig.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-166">Suggested address has been changed significantly and needs user confirmation.</span></span> | <span data-ttu-id="2ccb4-167">Enkelvoudig</span><span class="sxs-lookup"><span data-stu-id="2ccb4-167">Single</span></span> |
|<span data-ttu-id="2ccb4-168">Gedeeltelijk straat</span><span class="sxs-lookup"><span data-stu-id="2ccb4-168">Street partial</span></span> | <span data-ttu-id="2ccb4-169">De opgegeven straat in het adres is gedeeltelijk en heeft meer informatie nodig.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-169">The given street in the address is partial and needs more info.</span></span> | <span data-ttu-id="2ccb4-170">Meerdere, maximaal drie</span><span class="sxs-lookup"><span data-stu-id="2ccb4-170">Multiple—maximum of three</span></span> |
|<span data-ttu-id="2ccb4-171">Gedeeltelijk lokaal</span><span class="sxs-lookup"><span data-stu-id="2ccb4-171">Premises partial</span></span> | <span data-ttu-id="2ccb4-172">De opgegeven locatie (gebouwnummer, suitenummer en andere) is gedeeltelijk en heeft meer informatie nodig.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-172">The given premises (building number, suite number, and others) are partial and need more info.</span></span> | <span data-ttu-id="2ccb4-173">Meerdere, maximaal drie</span><span class="sxs-lookup"><span data-stu-id="2ccb4-173">Multiple—maximum of three</span></span> |
|<span data-ttu-id="2ccb4-174">Meerdere</span><span class="sxs-lookup"><span data-stu-id="2ccb4-174">Multiple</span></span> | <span data-ttu-id="2ccb4-175">Er zijn meerdere velden die gedeeltelijk in het adres zijn (mogelijk ook gedeeltelijk en gedeeltelijk van de straat).</span><span class="sxs-lookup"><span data-stu-id="2ccb4-175">There are multiple fields that are partial in the address (potentially also including street partial and premises partial).</span></span> | <span data-ttu-id="2ccb4-176">Meerdere, maximaal drie</span><span class="sxs-lookup"><span data-stu-id="2ccb4-176">Multiple—maximum of three</span></span> |
|<span data-ttu-id="2ccb4-177">Geen</span><span class="sxs-lookup"><span data-stu-id="2ccb4-177">None</span></span> | <span data-ttu-id="2ccb4-178">Het adres is onjuist.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-178">Address is incorrect.</span></span> | <span data-ttu-id="2ccb4-179">Geen</span><span class="sxs-lookup"><span data-stu-id="2ccb4-179">None</span></span> |
|<span data-ttu-id="2ccb4-180">Niet gevalideerd</span><span class="sxs-lookup"><span data-stu-id="2ccb4-180">Not validated</span></span> | <span data-ttu-id="2ccb4-181">Het adres kan niet worden verzonden via het validatieproces.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-181">Address was not able to be sent through the validation process.</span></span> | <span data-ttu-id="2ccb4-182">Geen</span><span class="sxs-lookup"><span data-stu-id="2ccb4-182">None</span></span> |

### <a name="request-example"></a><span data-ttu-id="2ccb4-183">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2ccb4-183">Request example</span></span>

```http
# "VerifiedShippable" Request Example

POST https://api.partnercenter.microsoft.com/v1/validations/address HTTP/1.1
Accept: application/json
Content-Type: application/json
Authorization: Bearer <token>
MS-CorrelationId: 29624f3c-90cb-4d34-a7e9-bd2de6d35218
MS-RequestId: eb55c2b8-6f4b-4b44-9557-f76df624b8c0
Host: api.partnercenter.microsoft.com
Content-Length: 137
X-Locale: en-US

{
    "AddressLine1": "1 Microsoft Way",
    "City": "Redmond",
    "State": "WA",
    "PostalCode": "98052",
    "Country": "US"
}

# "StreetPartial" Request Example

POST https://api.partnercenter.microsoft.com/v1/validations/address HTTP/1.1
Accept: application/json
Content-Type: application/json
Authorization: Bearer <token>
MS-CorrelationId: 2c95c9bc-fdfb-4c6a-84f4-57c9b0826b43
MS-RequestId: ee6cf74c-3ab5-48d6-9269-4a4b75bd59dc
Host: api.partnercenter.microsoft.com
Content-Length: 135
X-Locale: en-US

{
    "AddressLine1": "Microsoft Way",
    "City": "Redmond",
    "State": "WA",
    "PostalCode": "98052",
    "Country": "US"
}
```

## <a name="rest-response"></a><span data-ttu-id="2ccb4-184">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="2ccb4-184">REST response</span></span>

<span data-ttu-id="2ccb4-185">Als dit lukt, retourneert de methode een **AddressValidationResponse-object** in de antwoord-body, met een **HTTP 200-statuscode.**</span><span class="sxs-lookup"><span data-stu-id="2ccb4-185">If successful, the method returns an **AddressValidationResponse** object in the response body, with a **HTTP 200** status code.</span></span> <span data-ttu-id="2ccb4-186">Hieronder kunt u een voorbeeld bekijken.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-186">An example is shown below.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2ccb4-187">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="2ccb4-187">Response success and error codes</span></span>

<span data-ttu-id="2ccb4-188">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-188">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2ccb4-189">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="2ccb4-189">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2ccb4-190">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="2ccb4-190">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2ccb4-191">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="2ccb4-191">Response example</span></span>

```http
# "VerifiedShippable" Response Example

HTTP/1.1 200 OK
Date: Mon, 17 May 2021 23:19:19 GMT
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 29624f3c-90cb-4d34-a7e9-bd2de6d35218
MS-RequestId: eb55c2b8-6f4b-4b44-9557-f76df624b8c0
X-Locale: en-US
 
{
    "originalAddress": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "1 Microsoft Way",
        "postalCode": "98052"
    },
    "suggestedAddresses": [
        {
            "country": "US",
            "city": "Redmond",
            "state": "WA",
            "addressLine1": "1 Microsoft Way",
            "postalCode": "98052-8300"
        }
    ],
    "status": "VerifiedShippable"
}

# "StreetPartial" Response Example

HTTP/1.1 200 OK
Date: Mon, 17 May 2021 23:34:08 GMT
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 2c95c9bc-fdfb-4c6a-84f4-57c9b0826b43
MS-RequestId: ee6cf74c-3ab5-48d6-9269-4a4b75bd59dc
X-Locale: en-US
 
{
    "originalAddress": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "Microsoft Way",
        "postalCode": "98052"
    },
    "suggestedAddresses": [
        {
            "country": "US",
            "city": "Redmond",
            "state": "WA",
            "addressLine1": "1 Microsoft Way",
            "postalCode": "98052-6399"
        }
    ],
    "status": "StreetPartial",
    "validationMessage": "Address field invalid for property: 'Region', 'PostalCode', 'City'"
}
```
