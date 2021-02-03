---
title: Een adres valideren
description: Een adres valideren met de adres verificatie-API.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 22d5faec2fdab4907067bb01cb74e110032dea9a
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767238"
---
# <a name="validate-an-address"></a><span data-ttu-id="6b690-103">Een adres valideren</span><span class="sxs-lookup"><span data-stu-id="6b690-103">Validate an address</span></span>

<span data-ttu-id="6b690-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="6b690-104">**Applies To**</span></span>

- <span data-ttu-id="6b690-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="6b690-105">Partner Center</span></span>
- <span data-ttu-id="6b690-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="6b690-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="6b690-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="6b690-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="6b690-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6b690-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6b690-109">Een adres valideren met de adres verificatie-API.</span><span class="sxs-lookup"><span data-stu-id="6b690-109">How to validate an address using the address validation API.</span></span>

<span data-ttu-id="6b690-110">De adres validatie-API mag alleen worden gebruikt voor het vooraf valideren van updates van het klant profiel.</span><span class="sxs-lookup"><span data-stu-id="6b690-110">The address validation API should only be used for pre-validation of customer profile updates.</span></span> <span data-ttu-id="6b690-111">Gebruik het met de uitleg dat als het land de Verenigde Staten, Canada, China of Mexico is, het veld Status wordt gevalideerd op basis van een lijst met geldige statussen voor het desbetreffende land.</span><span class="sxs-lookup"><span data-stu-id="6b690-111">Use it with the understanding that if the country is the United States, Canada, China, or Mexico, the state field is validated against a list of valid states for the respective country.</span></span> <span data-ttu-id="6b690-112">In alle andere landen treedt deze test niet op en controleert de API alleen of de status een geldige teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="6b690-112">In all other countries, this test does not occur, and the API only checks that the state is a valid string.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6b690-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6b690-113">Prerequisites</span></span>

<span data-ttu-id="6b690-114">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6b690-114">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6b690-115">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="6b690-115">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="6b690-116">C\#</span><span class="sxs-lookup"><span data-stu-id="6b690-116">C\#</span></span>

<span data-ttu-id="6b690-117">Als u een adres wilt valideren, moet u eerst een nieuw **adres** object instantiëren en dit invullen met het te valideren adres.</span><span class="sxs-lookup"><span data-stu-id="6b690-117">To validate an address, first instantiate a new **Address** object and populate it with the address to validate.</span></span> <span data-ttu-id="6b690-118">Vervolgens haalt u een interface op met **validatie** bewerkingen van de eigenschap **IAggregatePartner. validions** en roept u de methode **IsAddressValid** aan met het object address.</span><span class="sxs-lookup"><span data-stu-id="6b690-118">Then, retrieve an interface to **Validations** operations from the **IAggregatePartner.Validations** property, and call the **IsAddressValid** method with the address object.</span></span>

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

## <a name="java"></a><span data-ttu-id="6b690-119">Java</span><span class="sxs-lookup"><span data-stu-id="6b690-119">Java</span></span>

<span data-ttu-id="6b690-120">Als u een adres wilt valideren, moet u eerst een nieuw **adres** object instantiëren en dit invullen met het te valideren adres.</span><span class="sxs-lookup"><span data-stu-id="6b690-120">To validate an address, first instantiate a new **Address** object and populate it with the address to validate.</span></span> <span data-ttu-id="6b690-121">Vervolgens haalt u een interface op met **validatie** bewerkingen van de functie **IAggregatePartner. getValidations** en roept u de **isAddressValid** -methode aan met het object address.</span><span class="sxs-lookup"><span data-stu-id="6b690-121">Then, retrieve an interface to **Validations** operations from the **IAggregatePartner.getValidations** function, and call the **isAddressValid** method with the address object.</span></span>

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

## <a name="powershell"></a><span data-ttu-id="6b690-122">PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b690-122">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="6b690-123">Als u een adres wilt valideren, voert u de [**test-PartnerAddress**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Test-PartnerAddress.md) uit met de adres parameters die zijn ingevuld.</span><span class="sxs-lookup"><span data-stu-id="6b690-123">To validate an address, execute the [**Test-PartnerAddress**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Test-PartnerAddress.md) with the address parameters populated.</span></span>

```powershell
Test-PartnerAddress -AddressLine1 '700 Bellevue Way NE' -City 'Bellevue' -Country 'US' -PostalCode '98004' -State 'WA'
```

## <a name="rest-request"></a><span data-ttu-id="6b690-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="6b690-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6b690-125">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6b690-125">Request syntax</span></span>

| <span data-ttu-id="6b690-126">Methode</span><span class="sxs-lookup"><span data-stu-id="6b690-126">Method</span></span>   | <span data-ttu-id="6b690-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="6b690-127">Request URI</span></span>                                                                 |
|----------|-----------------------------------------------------------------------------|
| <span data-ttu-id="6b690-128">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="6b690-128">**POST**</span></span> | <span data-ttu-id="6b690-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/validations/Address http/1.1</span><span class="sxs-lookup"><span data-stu-id="6b690-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/validations/address HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="6b690-130">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="6b690-130">Request headers</span></span>

<span data-ttu-id="6b690-131">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="6b690-131">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6b690-132">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="6b690-132">Request body</span></span>

<span data-ttu-id="6b690-133">In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="6b690-133">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="6b690-134">Naam</span><span class="sxs-lookup"><span data-stu-id="6b690-134">Name</span></span>         | <span data-ttu-id="6b690-135">Type</span><span class="sxs-lookup"><span data-stu-id="6b690-135">Type</span></span>   | <span data-ttu-id="6b690-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="6b690-136">Required</span></span> | <span data-ttu-id="6b690-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6b690-137">Description</span></span>                                                |
|--------------|--------|----------|------------------------------------------------------------|
| <span data-ttu-id="6b690-138">addressline1</span><span class="sxs-lookup"><span data-stu-id="6b690-138">addressline1</span></span> | <span data-ttu-id="6b690-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6b690-139">string</span></span> | <span data-ttu-id="6b690-140">J</span><span class="sxs-lookup"><span data-stu-id="6b690-140">Y</span></span>        | <span data-ttu-id="6b690-141">De eerste regel van het adres.</span><span class="sxs-lookup"><span data-stu-id="6b690-141">The first line of the address.</span></span>                             |
| <span data-ttu-id="6b690-142">addressline2</span><span class="sxs-lookup"><span data-stu-id="6b690-142">addressline2</span></span> | <span data-ttu-id="6b690-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6b690-143">string</span></span> | <span data-ttu-id="6b690-144">N</span><span class="sxs-lookup"><span data-stu-id="6b690-144">N</span></span>        | <span data-ttu-id="6b690-145">De tweede regel van het adres.</span><span class="sxs-lookup"><span data-stu-id="6b690-145">The second line of the address.</span></span> <span data-ttu-id="6b690-146">Deze eigenschap is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6b690-146">This property is optional.</span></span> |
| <span data-ttu-id="6b690-147">city</span><span class="sxs-lookup"><span data-stu-id="6b690-147">city</span></span>         | <span data-ttu-id="6b690-148">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6b690-148">string</span></span> | <span data-ttu-id="6b690-149">J</span><span class="sxs-lookup"><span data-stu-id="6b690-149">Y</span></span>        | <span data-ttu-id="6b690-150">De plaats.</span><span class="sxs-lookup"><span data-stu-id="6b690-150">The city.</span></span>                                                  |
| <span data-ttu-id="6b690-151">staat</span><span class="sxs-lookup"><span data-stu-id="6b690-151">state</span></span>        | <span data-ttu-id="6b690-152">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6b690-152">string</span></span> | <span data-ttu-id="6b690-153">J</span><span class="sxs-lookup"><span data-stu-id="6b690-153">Y</span></span>        | <span data-ttu-id="6b690-154">De status.</span><span class="sxs-lookup"><span data-stu-id="6b690-154">The state.</span></span>                                                 |
| <span data-ttu-id="6b690-155">postalcode</span><span class="sxs-lookup"><span data-stu-id="6b690-155">postalcode</span></span>   | <span data-ttu-id="6b690-156">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6b690-156">string</span></span> | <span data-ttu-id="6b690-157">J</span><span class="sxs-lookup"><span data-stu-id="6b690-157">Y</span></span>        | <span data-ttu-id="6b690-158">De post code.</span><span class="sxs-lookup"><span data-stu-id="6b690-158">The postal code.</span></span>                                           |
| <span data-ttu-id="6b690-159">country</span><span class="sxs-lookup"><span data-stu-id="6b690-159">country</span></span>      | <span data-ttu-id="6b690-160">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6b690-160">string</span></span> | <span data-ttu-id="6b690-161">J</span><span class="sxs-lookup"><span data-stu-id="6b690-161">Y</span></span>        | <span data-ttu-id="6b690-162">De ISO alpha-2-land code van twee tekens.</span><span class="sxs-lookup"><span data-stu-id="6b690-162">The two-character ISO alpha-2 country code.</span></span>                |

### <a name="request-example"></a><span data-ttu-id="6b690-163">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6b690-163">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="6b690-164">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="6b690-164">REST response</span></span>

<span data-ttu-id="6b690-165">Als de methode is geslaagd, wordt een status code 200 geretourneerd, zoals wordt weer gegeven in het voor beeld van een validatie van de reactie: hieronder.</span><span class="sxs-lookup"><span data-stu-id="6b690-165">If successful, the method returns a status code 200 as demonstrated in the Response - validation succeeded example shown below.</span></span>

<span data-ttu-id="6b690-166">Als de aanvraag mislukt, retourneert de methode de status code 400, zoals wordt gedemonstreerd in het voor beeld van een mislukte validatie van antwoorden.</span><span class="sxs-lookup"><span data-stu-id="6b690-166">If the request fails, the method returns a status code 400 as demonstrated in the Response - validation failed example shown below.</span></span> <span data-ttu-id="6b690-167">De antwoord tekst bevat een JSON-nettolading met aanvullende informatie over de fout.</span><span class="sxs-lookup"><span data-stu-id="6b690-167">The response body contains a JSON payload with additional information about the error.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6b690-168">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="6b690-168">Response success and error codes</span></span>

<span data-ttu-id="6b690-169">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="6b690-169">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6b690-170">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="6b690-170">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6b690-171">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="6b690-171">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response---validation-succeeded-example"></a><span data-ttu-id="6b690-172">Antwoord: voor beeld van validatie geslaagd</span><span class="sxs-lookup"><span data-stu-id="6b690-172">Response - validation succeeded example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 0
MS-CorrelationId: 8a853a1a-b0e6-4cb0-ae87-d6dd32ac3a0c
MS-RequestId: 0b30452a-8be2-4b8b-b25b-2d4850f4345f
MS-CV: IqhjoWVyq0Kl81dO.0
MS-ServerId: 030011719
Date: Mon, 13 Mar 2017 23:56:12 GMT
```

### <a name="response---validation-failed-example"></a><span data-ttu-id="6b690-173">Antwoord: voor beeld van mislukte validatie</span><span class="sxs-lookup"><span data-stu-id="6b690-173">Response - validation failed example</span></span>

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
