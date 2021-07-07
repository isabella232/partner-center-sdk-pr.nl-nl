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
# <a name="validate-an-address"></a>Een adres valideren

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Een adres valideren met behulp van de adresvalidatie-API.

De adresvalidatie-API mag alleen worden gebruikt voor de prevalidatie van updates van klantprofiel. Gebruik het met het begrip dat als het land de Verenigde Staten, Canada, China of Mexico is, het staatveld wordt gevalideerd met een lijst met geldige staten voor het desbetreffende land. In alle andere landen wordt deze test niet uitgevoerd en controleert de API alleen of de status een geldige tekenreeks is.

## <a name="prerequisites"></a>Vereisten

Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

## <a name="c"></a>C\#

Als u een adres wilt valideren, instantieer dan eerst een nieuw **adresobject** en vul dit met het adres dat u wilt valideren. Haal vervolgens een interface op voor **validatiebewerkingen** van de eigenschap **IAggregatePartner.Validations** en roep de **methode IsAddressValid** aan met het adresobject.

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

## <a name="java"></a>Java

Als u een adres wilt valideren, instantieer dan eerst een nieuw **adresobject** en vul dit met het adres dat u wilt valideren. Haal vervolgens een interface voor **validatiebewerkingen** op uit de **functie IAggregatePartner.getValidations** en roep de **methode isAddressValid** aan met het adresobject.

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

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Als u een adres wilt valideren, voert [**u het Test-PartnerAddress uit**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Test-PartnerAddress.md) met de adresparameters ingevuld.

```powershell
Test-PartnerAddress -AddressLine1 '700 Bellevue Way NE' -City 'Bellevue' -Country 'US' -PostalCode '98004' -State 'WA'
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                 |
|----------|-----------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/validations/address HTTP/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.

| Naam         | Type   | Vereist | Beschrijving                                                |
|--------------|--------|----------|------------------------------------------------------------|
| addressline1 | tekenreeks | J        | De eerste regel van het adres.                             |
| addressline2 | tekenreeks | N        | De tweede regel van het adres. Deze eigenschap is optioneel. |
| city         | tekenreeks | J        | De plaats.                                                  |
| staat        | tekenreeks | J        | De status.                                                 |
| postalcode   | tekenreeks | J        | De postcode.                                           |
| country      | tekenreeks | J        | De iso-alfa-2-landcode van twee tekens.                |

### <a name="request-example"></a>Voorbeeld van aanvraag

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

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert de methode een statuscode 200, zoals wordt gedemonstreerd in het voorbeeld Antwoord - validatie geslaagd, zoals hieronder wordt weergegeven.

Als de aanvraag mislukt, retourneert de methode een statuscode 400, zoals wordt gedemonstreerd in het voorbeeld Antwoord - validatie mislukt, zoals hieronder wordt weergegeven. De antwoord-body bevat een JSON-nettolading met aanvullende informatie over de fout.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response---validation-succeeded-example"></a>Antwoord : voorbeeld van validatie geslaagd

```http
HTTP/1.1 200 OK
Content-Length: 0
MS-CorrelationId: 8a853a1a-b0e6-4cb0-ae87-d6dd32ac3a0c
MS-RequestId: 0b30452a-8be2-4b8b-b25b-2d4850f4345f
MS-CV: IqhjoWVyq0Kl81dO.0
MS-ServerId: 030011719
Date: Mon, 13 Mar 2017 23:56:12 GMT
```

### <a name="response---validation-failed-example"></a>Antwoord: voorbeeld validatie mislukt

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
