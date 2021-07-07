---
title: Een adres valideren
description: Een adres valideren met behulp van de adresvalidatie-API.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 14d45977f3af6e8bba1b7cb7f969aa7c5bb671da
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529882"
---
# <a name="validate-an-address"></a><span data-ttu-id="4e65c-103">Een adres valideren</span><span class="sxs-lookup"><span data-stu-id="4e65c-103">Validate an address</span></span>

<span data-ttu-id="4e65c-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="4e65c-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="4e65c-105">Een adres valideren met behulp van de adresvalidatie-API.</span><span class="sxs-lookup"><span data-stu-id="4e65c-105">How to validate an address using the address validation API.</span></span>

<span data-ttu-id="4e65c-106">De adresvalidatie-API mag alleen worden gebruikt voor de prevalidatie van updates van klantprofiel.</span><span class="sxs-lookup"><span data-stu-id="4e65c-106">The address validation API should only be used for pre-validation of customer profile updates.</span></span> <span data-ttu-id="4e65c-107">Gebruik het met het begrip dat als het land de Verenigde Staten, Canada, China of Mexico is, het staatveld wordt gevalideerd met een lijst met geldige staten voor het desbetreffende land.</span><span class="sxs-lookup"><span data-stu-id="4e65c-107">Use it with the understanding that if the country is the United States, Canada, China, or Mexico, the state field is validated against a list of valid states for the respective country.</span></span> <span data-ttu-id="4e65c-108">In alle andere landen wordt deze test niet uitgevoerd en controleert de API alleen of de status een geldige tekenreeks is.</span><span class="sxs-lookup"><span data-stu-id="4e65c-108">In all other countries, this test does not occur, and the API only checks that the state is a valid string.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4e65c-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4e65c-109">Prerequisites</span></span>

<span data-ttu-id="4e65c-110">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4e65c-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4e65c-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="4e65c-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="4e65c-112">C\#</span><span class="sxs-lookup"><span data-stu-id="4e65c-112">C\#</span></span>

<span data-ttu-id="4e65c-113">Als u een adres wilt valideren, instantieer dan eerst een nieuw **adresobject** en vul dit met het adres dat u wilt valideren.</span><span class="sxs-lookup"><span data-stu-id="4e65c-113">To validate an address, first instantiate a new **Address** object and populate it with the address to validate.</span></span> <span data-ttu-id="4e65c-114">Haal vervolgens een interface op voor **validatiebewerkingen** van de eigenschap **IAggregatePartner.Validations** en roep de **methode IsAddressValid** aan met het adresobject.</span><span class="sxs-lookup"><span data-stu-id="4e65c-114">Then, retrieve an interface to **Validations** operations from the **IAggregatePartner.Validations** property, and call the **IsAddressValid** method with the address object.</span></span>

```csharp
// IAggregatePartner partnerOperations;

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
bool result = partnerOperations.Validations.IsAddressValid(address);

// If the address is valid, the result should equal true.
Console.WriteLine("Result: " + result.ToString());

// The following is an example that causes address validation to fail.
try
{
    // Change to an invalid postal code for this address.
    address.PostalCode = "98007";

    // Validate the address.
    result = partnerOperations.Validations.IsAddressValid(address);

    Console.WriteLine("ERROR: The code should have thrown an exception - BadRequest(400).");
}
catch (PartnerException exception)
{
    if (exception.ErrorCategory == PartnerErrorCategory.BadInput)
    {
        Console.WriteLine(exception.ErrorCategory.ToString());
        Console.WriteLine("Exception:");
        Console.WriteLine("Message: {0}", exception.Message);
    }
    else
    {
        throw;
    }
}
```

## <a name="java"></a><span data-ttu-id="4e65c-115">Java</span><span class="sxs-lookup"><span data-stu-id="4e65c-115">Java</span></span>

<span data-ttu-id="4e65c-116">Als u een adres wilt valideren, instantieer dan eerst een nieuw **adresobject** en vul dit met het adres dat u wilt valideren.</span><span class="sxs-lookup"><span data-stu-id="4e65c-116">To validate an address, first instantiate a new **Address** object and populate it with the address to validate.</span></span> <span data-ttu-id="4e65c-117">Haal vervolgens een interface voor **validatiebewerkingen** op uit de **functie IAggregatePartner.getValidations** en roep de **methode isAddressValid** aan met het adresobject.</span><span class="sxs-lookup"><span data-stu-id="4e65c-117">Then, retrieve an interface to **Validations** operations from the **IAggregatePartner.getValidations** function, and call the **isAddressValid** method with the address object.</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

```java
// IAggregatePartner partnerOperations;

// Create an address to validate.
Address address = new Address();

address.setAddressLine1("One Microsoft Way");
address.setCity("Redmond");
address.setState("WA");
address.setCountry("US");
address.setPostalCode("98052");

try
{
    // Validate the address
    Boolean validationResult = partnerOperations.getValidations().isAddressValid(address);

    System.out.println(validationResult ? "The address is valid." : "Invalid address");
}
catch (Exception exception)
{
    System.out.println("Address is invalid");

    if (! StringHelper.isNullOrWhiteSpace(exception.getMessage()))
    {
        System.out.println(exception.getMessage());
    }
}
```

## <a name="powershell"></a><span data-ttu-id="4e65c-118">PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e65c-118">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="4e65c-119">Als u een adres wilt valideren, voert [**u het Test-PartnerAddress uit**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Test-PartnerAddress.md) met de adresparameters ingevuld.</span><span class="sxs-lookup"><span data-stu-id="4e65c-119">To validate an address, execute the [**Test-PartnerAddress**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Test-PartnerAddress.md) with the address parameters populated.</span></span>

```powershell
Test-PartnerAddress -AddressLine1 '700 Bellevue Way NE' -City 'Bellevue' -Country 'US' -PostalCode '98004' -State 'WA'
```

## <a name="rest-request"></a><span data-ttu-id="4e65c-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="4e65c-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4e65c-121">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="4e65c-121">Request syntax</span></span>

| <span data-ttu-id="4e65c-122">Methode</span><span class="sxs-lookup"><span data-stu-id="4e65c-122">Method</span></span>   | <span data-ttu-id="4e65c-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="4e65c-123">Request URI</span></span>                                                                 |
|----------|-----------------------------------------------------------------------------|
| <span data-ttu-id="4e65c-124">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="4e65c-124">**POST**</span></span> | <span data-ttu-id="4e65c-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/validations/address HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4e65c-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/validations/address HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4e65c-126">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="4e65c-126">Request headers</span></span>

<span data-ttu-id="4e65c-127">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="4e65c-127">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4e65c-128">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="4e65c-128">Request body</span></span>

<span data-ttu-id="4e65c-129">In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="4e65c-129">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="4e65c-130">Naam</span><span class="sxs-lookup"><span data-stu-id="4e65c-130">Name</span></span>         | <span data-ttu-id="4e65c-131">Type</span><span class="sxs-lookup"><span data-stu-id="4e65c-131">Type</span></span>   | <span data-ttu-id="4e65c-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="4e65c-132">Required</span></span> | <span data-ttu-id="4e65c-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4e65c-133">Description</span></span>                                                |
|--------------|--------|----------|------------------------------------------------------------|
| <span data-ttu-id="4e65c-134">addressline1</span><span class="sxs-lookup"><span data-stu-id="4e65c-134">addressline1</span></span> | <span data-ttu-id="4e65c-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4e65c-135">string</span></span> | <span data-ttu-id="4e65c-136">J</span><span class="sxs-lookup"><span data-stu-id="4e65c-136">Y</span></span>        | <span data-ttu-id="4e65c-137">De eerste regel van het adres.</span><span class="sxs-lookup"><span data-stu-id="4e65c-137">The first line of the address.</span></span>                             |
| <span data-ttu-id="4e65c-138">addressline2</span><span class="sxs-lookup"><span data-stu-id="4e65c-138">addressline2</span></span> | <span data-ttu-id="4e65c-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4e65c-139">string</span></span> | <span data-ttu-id="4e65c-140">N</span><span class="sxs-lookup"><span data-stu-id="4e65c-140">N</span></span>        | <span data-ttu-id="4e65c-141">De tweede regel van het adres.</span><span class="sxs-lookup"><span data-stu-id="4e65c-141">The second line of the address.</span></span> <span data-ttu-id="4e65c-142">Deze eigenschap is optioneel.</span><span class="sxs-lookup"><span data-stu-id="4e65c-142">This property is optional.</span></span> |
| <span data-ttu-id="4e65c-143">city</span><span class="sxs-lookup"><span data-stu-id="4e65c-143">city</span></span>         | <span data-ttu-id="4e65c-144">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4e65c-144">string</span></span> | <span data-ttu-id="4e65c-145">J</span><span class="sxs-lookup"><span data-stu-id="4e65c-145">Y</span></span>        | <span data-ttu-id="4e65c-146">De plaats.</span><span class="sxs-lookup"><span data-stu-id="4e65c-146">The city.</span></span>                                                  |
| <span data-ttu-id="4e65c-147">staat</span><span class="sxs-lookup"><span data-stu-id="4e65c-147">state</span></span>        | <span data-ttu-id="4e65c-148">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4e65c-148">string</span></span> | <span data-ttu-id="4e65c-149">J</span><span class="sxs-lookup"><span data-stu-id="4e65c-149">Y</span></span>        | <span data-ttu-id="4e65c-150">De status.</span><span class="sxs-lookup"><span data-stu-id="4e65c-150">The state.</span></span>                                                 |
| <span data-ttu-id="4e65c-151">postalcode</span><span class="sxs-lookup"><span data-stu-id="4e65c-151">postalcode</span></span>   | <span data-ttu-id="4e65c-152">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4e65c-152">string</span></span> | <span data-ttu-id="4e65c-153">J</span><span class="sxs-lookup"><span data-stu-id="4e65c-153">Y</span></span>        | <span data-ttu-id="4e65c-154">De postcode.</span><span class="sxs-lookup"><span data-stu-id="4e65c-154">The postal code.</span></span>                                           |
| <span data-ttu-id="4e65c-155">country</span><span class="sxs-lookup"><span data-stu-id="4e65c-155">country</span></span>      | <span data-ttu-id="4e65c-156">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4e65c-156">string</span></span> | <span data-ttu-id="4e65c-157">J</span><span class="sxs-lookup"><span data-stu-id="4e65c-157">Y</span></span>        | <span data-ttu-id="4e65c-158">De iso-alfa-2-landcode van twee tekens.</span><span class="sxs-lookup"><span data-stu-id="4e65c-158">The two-character ISO alpha-2 country code.</span></span>                |

### <a name="request-example"></a><span data-ttu-id="4e65c-159">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4e65c-159">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/validations/address HTTP/1.1
Content-Type: application/json
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0b30452a-8be2-4b8b-b25b-2d4850f4345f
MS-CorrelationId: 8a853a1a-b0e6-4cb0-ae87-d6dd32ac3a0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 129

{
    "AddressLine1": "One Microsoft Way",
    "City": "Redmond",
    "State": "WA",
    "PostalCode": "98052",
    "Country": "US"
}
```

## <a name="rest-response"></a><span data-ttu-id="4e65c-160">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="4e65c-160">REST response</span></span>

<span data-ttu-id="4e65c-161">Als dit lukt, retourneert de methode een statuscode 200, zoals wordt gedemonstreerd in het voorbeeld Antwoord - validatie geslaagd, zoals hieronder wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="4e65c-161">If successful, the method returns a status code 200 as demonstrated in the Response - validation succeeded example shown below.</span></span>

<span data-ttu-id="4e65c-162">Als de aanvraag mislukt, retourneert de methode een statuscode 400, zoals wordt gedemonstreerd in het voorbeeld Antwoord - validatie mislukt, zoals hieronder wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="4e65c-162">If the request fails, the method returns a status code 400 as demonstrated in the Response - validation failed example shown below.</span></span> <span data-ttu-id="4e65c-163">De antwoord-body bevat een JSON-nettolading met aanvullende informatie over de fout.</span><span class="sxs-lookup"><span data-stu-id="4e65c-163">The response body contains a JSON payload with additional information about the error.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4e65c-164">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="4e65c-164">Response success and error codes</span></span>

<span data-ttu-id="4e65c-165">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="4e65c-165">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4e65c-166">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="4e65c-166">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4e65c-167">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="4e65c-167">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response---validation-succeeded-example"></a><span data-ttu-id="4e65c-168">Antwoord : voorbeeld van validatie geslaagd</span><span class="sxs-lookup"><span data-stu-id="4e65c-168">Response - validation succeeded example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 0
MS-CorrelationId: 8a853a1a-b0e6-4cb0-ae87-d6dd32ac3a0c
MS-RequestId: 0b30452a-8be2-4b8b-b25b-2d4850f4345f
MS-CV: IqhjoWVyq0Kl81dO.0
MS-ServerId: 030011719
Date: Mon, 13 Mar 2017 23:56:12 GMT
```

### <a name="response---validation-failed-example"></a><span data-ttu-id="4e65c-169">Antwoord: voorbeeld validatie mislukt</span><span class="sxs-lookup"><span data-stu-id="4e65c-169">Response - validation failed example</span></span>

```http
HTTP/1.1 400 Bad Request
Content-Length: 418
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 8a853a1a-b0e6-4cb0-ae87-d6dd32ac3a0c
MS-RequestId: 0b30452a-8be2-4b8b-b25b-2d4850f4345f
MS-CV: pdlItMyvtkmGHDWt.0
MS-ServerId: 101112012
Date: Tue, 14 Mar 2017 01:57:55 GMT

{
    "code": 2007,
    "description": "{\"code\":\"60071\",\"reason\":\"ZipCityInvalid - Details: Field - &#39;City&#39; is corrected from OldValue: &#39;Redmond&#39; to NewValue: &#39;BELLEVUE&#39;.\",\"corrected_address\":{\"country\":\"US\",\"region\":\"WA\",\"city\":\"BELLEVUE\",\"address_line1\":\"One Microsoft Way\",\"postal_code\":\"98007\"},\"object_type\":\"AddressValidation\",\"resource_status\":\"Active\"}",
    "data": [],
    "source": "PartnerFD"
}
```
