---
title: Een bedrijfsprofiel van een klant ophalen
description: Haalt het bedrijfsprofiel van een klant op.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: a1c0c8401207f4b0bb33755a8eabc66de0ad9ff9
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874972"
---
# <a name="get-a-customers-company-profile"></a>Een bedrijfsprofiel van een klant ophalen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Haalt het bedrijfsprofiel van een klant op.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Als u het bedrijfsprofiel voor een klant wilt op halen, roept u de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant te identificeren. Haal vervolgens de [**ICustomerProfileCollection-interface**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection) van de klant op uit de eigenschap [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) om toegang te krijgen tot de bedrijfseigenschap. Haal vervolgens de [**interface ICustomerReadonlyProfile**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1) op uit de eigenschap [**ICustomerProfileCollection.Company**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.company) en roep de [**methoden Get()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) of [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync) aan.

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

var companyProfile = partnerOperations.Customers.ById(customerId).Profiles.Company.Get();
```

**Voorbeeld:** [download de Partnercentrum-SDK](https://go.microsoft.com/fwlink/p/?LinkId=746681). **Project:** Klasse PartnerSdk.FeatureSamples: GetCustomerCompanyProfile.cs 

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Als u het bedrijfsprofiel voor een klant wilt op halen, roept u de functie **IAggregatePartner.getCustomers().byId** aan met de klant-id om de klant te identificeren. Haal vervolgens de **ICustomerProfileCollection-interface** van de klant op uit de functie [**getProfiles**] om toegang te krijgen tot de bedrijfseigenschap. Haal vervolgens de **interface ICustomerReadonlyProfile** op uit de functie **ICustomerProfileCollection.getCompany** en roep de **functie get** aan.

```java
// IAggregatePartner partnerOperations;
// String customerId;

CustomerCompanyProfile companyProfile = partnerOperations.getCustomers().byId(customerId).getProfiles().getCompany().get();
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                             |
|---------|-------------------------------------------------------------------------|
| **Toevoegen** | *{baseURL}*/v1/customers/{customer-tenant-id}/profiles/company HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om het bedrijfsprofiel op te halen.

| Naam                   | Type     | Vereist | Beschrijving                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **customer-tenant-id** | **guid** | J        | De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers Partner Center [meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/profiles/company HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0b6f039c-e4b5-4b9e-bdac-b39077bb60da
MS-CorrelationId: ffa9174c-dbcb-47de-b70d-10e640a7f1b4
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode informatie in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center de volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 488
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ffa9174c-dbcb-47de-b70d-10e640a7f1b4
MS-RequestId: 0b6f039c-e4b5-4b9e-bdac-b39077bb60da
MS-CV: /e74N8OrkE29ycwZ.0
MS-ServerId: 101112202
Date: Wed, 04 Jan 2017 19:48:51 GMT

{
    "tenantId": "4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04",
    "domain": "dtdemocspcustomer005.onmicrosoft.com",
    "companyName": "DT Demo CSP Customer 005",
    "address": {
        "country": "US",
        "region": "WA",
        "city": "Redmond ",
        "addressLine1": "1 Microsoft Way",
        "postalCode": "98052",
        "phoneNumber": "4155551212"
    },
    "email": "daniel@hotmail.com.tw",
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/profiles/company",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "CustomerCompanyProfile"
    }
}
```
