---
title: Een adres valideren
description: Een adres valideren met behulp van de adresvalidatie-API.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 2eeca91b0e5a507dac6df4ecf61a56aed2d2d921
ms.sourcegitcommit: 51237e7e98d71a7e0590b4d6a4034b6409542126
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2021
ms.locfileid: "113572077"
---
# <a name="validate-an-address"></a><span data-ttu-id="fd8b3-103">Een adres valideren</span><span class="sxs-lookup"><span data-stu-id="fd8b3-103">Validate an address</span></span>

<span data-ttu-id="fd8b3-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="fd8b3-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="fd8b3-105">Een adres valideren met behulp van de adresvalidatie-API.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-105">How to validate an address using the address validation API.</span></span>

<span data-ttu-id="fd8b3-106">De adresvalidatie-API mag alleen worden gebruikt voor de prevalidatie van updates van klantprofiel.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-106">The address validation API should only be used for pre-validation of customer profile updates.</span></span> <span data-ttu-id="fd8b3-107">Gebruik het met het begrip dat als het land de Verenigde Staten, Canada, China of Mexico is, het staatveld wordt gevalideerd op een lijst met geldige staten voor het desbetreffende land.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-107">Use it with the understanding that if the country is the United States, Canada, China, or Mexico, the state field is validated against a list of valid states for the respective country.</span></span> <span data-ttu-id="fd8b3-108">In alle andere landen wordt deze test niet uitgevoerd en controleert de API alleen of de status een geldige tekenreeks is.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-108">In all other countries, this test does not occur, and the API only checks that the state is a valid string.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fd8b3-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fd8b3-109">Prerequisites</span></span>

<span data-ttu-id="fd8b3-110">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="fd8b3-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fd8b3-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="fd8b3-112">C\#</span><span class="sxs-lookup"><span data-stu-id="fd8b3-112">C\#</span></span>

<span data-ttu-id="fd8b3-113">Als u een adres wilt valideren, instantieer dan eerst een nieuw **adresobject** en vul dit met het adres dat u wilt valideren.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-113">To validate an address, first instantiate a new **Address** object and populate it with the address to validate.</span></span> <span data-ttu-id="fd8b3-114">Haal vervolgens een interface op voor **validatiebewerkingen** van de eigenschap **IAggregatePartner.Validations** en roep de **methode IsAddressValid** aan met het adresobject.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-114">Then, retrieve an interface to **Validations** operations from the **IAggregatePartner.Validations** property, and call the **IsAddressValid** method with the address object.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="fd8b3-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fd8b3-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fd8b3-116">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="fd8b3-116">Request syntax</span></span>

| <span data-ttu-id="fd8b3-117">Methode</span><span class="sxs-lookup"><span data-stu-id="fd8b3-117">Method</span></span>   | <span data-ttu-id="fd8b3-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fd8b3-118">Request URI</span></span>                                                                 |
|----------|-----------------------------------------------------------------------------|
| <span data-ttu-id="fd8b3-119">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="fd8b3-119">**POST**</span></span> | <span data-ttu-id="fd8b3-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/validations/address HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fd8b3-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/validations/address HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="fd8b3-121">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="fd8b3-121">Request headers</span></span>

<span data-ttu-id="fd8b3-122">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="fd8b3-122">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fd8b3-123">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="fd8b3-123">Request body</span></span>

<span data-ttu-id="fd8b3-124">In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-124">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="fd8b3-125">Naam</span><span class="sxs-lookup"><span data-stu-id="fd8b3-125">Name</span></span>         | <span data-ttu-id="fd8b3-126">Type</span><span class="sxs-lookup"><span data-stu-id="fd8b3-126">Type</span></span>   | <span data-ttu-id="fd8b3-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="fd8b3-127">Required</span></span> | <span data-ttu-id="fd8b3-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fd8b3-128">Description</span></span>                                                |
|--------------|--------|----------|------------------------------------------------------------|
| <span data-ttu-id="fd8b3-129">addressline1</span><span class="sxs-lookup"><span data-stu-id="fd8b3-129">addressline1</span></span> | <span data-ttu-id="fd8b3-130">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fd8b3-130">string</span></span> | <span data-ttu-id="fd8b3-131">J</span><span class="sxs-lookup"><span data-stu-id="fd8b3-131">Y</span></span>        | <span data-ttu-id="fd8b3-132">De eerste regel van het adres.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-132">The first line of the address.</span></span>                             |
| <span data-ttu-id="fd8b3-133">addressline2</span><span class="sxs-lookup"><span data-stu-id="fd8b3-133">addressline2</span></span> | <span data-ttu-id="fd8b3-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fd8b3-134">string</span></span> | <span data-ttu-id="fd8b3-135">N</span><span class="sxs-lookup"><span data-stu-id="fd8b3-135">N</span></span>        | <span data-ttu-id="fd8b3-136">De tweede regel van het adres.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-136">The second line of the address.</span></span> <span data-ttu-id="fd8b3-137">Deze eigenschap is optioneel.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-137">This property is optional.</span></span> |
| <span data-ttu-id="fd8b3-138">city</span><span class="sxs-lookup"><span data-stu-id="fd8b3-138">city</span></span>         | <span data-ttu-id="fd8b3-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fd8b3-139">string</span></span> | <span data-ttu-id="fd8b3-140">J</span><span class="sxs-lookup"><span data-stu-id="fd8b3-140">Y</span></span>        | <span data-ttu-id="fd8b3-141">De plaats.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-141">The city.</span></span>                                                  |
| <span data-ttu-id="fd8b3-142">staat</span><span class="sxs-lookup"><span data-stu-id="fd8b3-142">state</span></span>        | <span data-ttu-id="fd8b3-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fd8b3-143">string</span></span> | <span data-ttu-id="fd8b3-144">J</span><span class="sxs-lookup"><span data-stu-id="fd8b3-144">Y</span></span>        | <span data-ttu-id="fd8b3-145">De status.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-145">The state.</span></span>                                                 |
| <span data-ttu-id="fd8b3-146">postalcode</span><span class="sxs-lookup"><span data-stu-id="fd8b3-146">postalcode</span></span>   | <span data-ttu-id="fd8b3-147">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fd8b3-147">string</span></span> | <span data-ttu-id="fd8b3-148">J</span><span class="sxs-lookup"><span data-stu-id="fd8b3-148">Y</span></span>        | <span data-ttu-id="fd8b3-149">De postcode.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-149">The postal code.</span></span>                                           |
| <span data-ttu-id="fd8b3-150">country</span><span class="sxs-lookup"><span data-stu-id="fd8b3-150">country</span></span>      | <span data-ttu-id="fd8b3-151">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fd8b3-151">string</span></span> | <span data-ttu-id="fd8b3-152">J</span><span class="sxs-lookup"><span data-stu-id="fd8b3-152">Y</span></span>        | <span data-ttu-id="fd8b3-153">De iso-2-landcode met twee tekens.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-153">The two-character ISO alpha-2 country code.</span></span>                |

### <a name="response-details"></a><span data-ttu-id="fd8b3-154">Antwoorddetails</span><span class="sxs-lookup"><span data-stu-id="fd8b3-154">Response details</span></span>

<span data-ttu-id="fd8b3-155">Het antwoord retournt een van de volgende statusberichten:</span><span class="sxs-lookup"><span data-stu-id="fd8b3-155">The response will return one of the following status messages:</span></span>

| <span data-ttu-id="fd8b3-156">Status</span><span class="sxs-lookup"><span data-stu-id="fd8b3-156">Status</span></span>     | <span data-ttu-id="fd8b3-157">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fd8b3-157">Description</span></span> |    <span data-ttu-id="fd8b3-158">Aantal voorgestelde adressen dat wordt geretourneerd</span><span class="sxs-lookup"><span data-stu-id="fd8b3-158">Number of suggested addresses returned</span></span> |
|-------|---------------|-------------------|
|<span data-ttu-id="fd8b3-159">Geverifieerd verzendbaar</span><span class="sxs-lookup"><span data-stu-id="fd8b3-159">Verified shippable</span></span> | <span data-ttu-id="fd8b3-160">Het adres wordt geverifieerd en kan worden verzonden naar .</span><span class="sxs-lookup"><span data-stu-id="fd8b3-160">Address is verified and can be shipped to.</span></span> | <span data-ttu-id="fd8b3-161">Enkelvoudig</span><span class="sxs-lookup"><span data-stu-id="fd8b3-161">Single</span></span> |
|<span data-ttu-id="fd8b3-162">Geverifieerd</span><span class="sxs-lookup"><span data-stu-id="fd8b3-162">Verified</span></span> | <span data-ttu-id="fd8b3-163">Het adres wordt geverifieerd.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-163">Address is verified.</span></span> | <span data-ttu-id="fd8b3-164">Enkelvoudig</span><span class="sxs-lookup"><span data-stu-id="fd8b3-164">Single</span></span> |
|<span data-ttu-id="fd8b3-165">Interactie vereist</span><span class="sxs-lookup"><span data-stu-id="fd8b3-165">Interaction required</span></span> | <span data-ttu-id="fd8b3-166">Voorgesteld adres is aanzienlijk gewijzigd en moet worden bevestigd door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-166">Suggested address has been changed significantly and needs user confirmation.</span></span> | <span data-ttu-id="fd8b3-167">Enkelvoudig</span><span class="sxs-lookup"><span data-stu-id="fd8b3-167">Single</span></span> |
|<span data-ttu-id="fd8b3-168">Gedeeltelijk straat</span><span class="sxs-lookup"><span data-stu-id="fd8b3-168">Street partial</span></span> | <span data-ttu-id="fd8b3-169">De opgegeven straat in het adres is gedeeltelijk en heeft meer informatie nodig.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-169">The given street in the address is partial and needs more info.</span></span> | <span data-ttu-id="fd8b3-170">Meerdere: maximaal drie</span><span class="sxs-lookup"><span data-stu-id="fd8b3-170">Multiple—maximum of three</span></span> |
|<span data-ttu-id="fd8b3-171">Gedeeltelijk locatie</span><span class="sxs-lookup"><span data-stu-id="fd8b3-171">Premises partial</span></span> | <span data-ttu-id="fd8b3-172">De opgegeven locatie (gebouwnummer, suitenummer en andere) is gedeeltelijk en heeft meer informatie nodig.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-172">The given premises (building number, suite number, and others) are partial and need more info.</span></span> | <span data-ttu-id="fd8b3-173">Meerdere: maximaal drie</span><span class="sxs-lookup"><span data-stu-id="fd8b3-173">Multiple—maximum of three</span></span> |
|<span data-ttu-id="fd8b3-174">Meerdere</span><span class="sxs-lookup"><span data-stu-id="fd8b3-174">Multiple</span></span> | <span data-ttu-id="fd8b3-175">Er zijn meerdere velden die gedeeltelijk in het adres zijn (mogelijk ook gedeeltelijk en gedeeltelijk van de straat).</span><span class="sxs-lookup"><span data-stu-id="fd8b3-175">There are multiple fields that are partial in the address (potentially also including street partial and premises partial).</span></span> | <span data-ttu-id="fd8b3-176">Meerdere: maximaal drie</span><span class="sxs-lookup"><span data-stu-id="fd8b3-176">Multiple—maximum of three</span></span> |
|<span data-ttu-id="fd8b3-177">Geen</span><span class="sxs-lookup"><span data-stu-id="fd8b3-177">None</span></span> | <span data-ttu-id="fd8b3-178">Het adres is onjuist.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-178">Address is incorrect.</span></span> | <span data-ttu-id="fd8b3-179">Geen</span><span class="sxs-lookup"><span data-stu-id="fd8b3-179">None</span></span> |
|<span data-ttu-id="fd8b3-180">Niet gevalideerd</span><span class="sxs-lookup"><span data-stu-id="fd8b3-180">Not validated</span></span> | <span data-ttu-id="fd8b3-181">Het adres kan niet worden verzonden via het validatieproces.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-181">Address was not able to be sent through the validation process.</span></span> | <span data-ttu-id="fd8b3-182">Geen</span><span class="sxs-lookup"><span data-stu-id="fd8b3-182">None</span></span> |

### <a name="request-example"></a><span data-ttu-id="fd8b3-183">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fd8b3-183">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="fd8b3-184">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fd8b3-184">REST response</span></span>

<span data-ttu-id="fd8b3-185">Als dit lukt, retourneert de methode een **AddressValidationResponse-object** in de antwoord-body, met een **HTTP 200-statuscode.**</span><span class="sxs-lookup"><span data-stu-id="fd8b3-185">If successful, the method returns an **AddressValidationResponse** object in the response body, with a **HTTP 200** status code.</span></span> <span data-ttu-id="fd8b3-186">Hieronder kunt u een voorbeeld bekijken.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-186">An example is shown below.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fd8b3-187">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="fd8b3-187">Response success and error codes</span></span>

<span data-ttu-id="fd8b3-188">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-188">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fd8b3-189">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fd8b3-189">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fd8b3-190">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="fd8b3-190">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fd8b3-191">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fd8b3-191">Response example</span></span>

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
