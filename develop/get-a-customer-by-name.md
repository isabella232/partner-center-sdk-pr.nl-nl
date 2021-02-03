---
title: Een lijst met klanten ophalen die zijn gefilterd op basis van een zoekveld
description: Hiermee wordt een verzameling klant resources opgehaald die overeenkomen met een filter. U kunt desgewenst een pagina grootte instellen. U kunt filteren op bedrijfs naam, domein, indirecte wederverkoper of indirecte Cloud Solution Provider (CSP).
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: aad9524dbe2c9edbbd7c1d50da7a448f6872fcb9
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767386"
---
# <a name="get-a-list-of-customers-filtered-by-a-search-field"></a>Een lijst met klanten ophalen die zijn gefilterd op basis van een zoekveld

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Hiermee wordt een verzameling [klant](customer-resources.md#customer) resources opgehaald die overeenkomen met een filter. U kunt desgewenst een pagina grootte instellen. U kunt filteren op bedrijfs naam, domein, indirecte wederverkoper of indirecte Cloud Solution Provider (CSP).

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een door de gebruiker samengesteld filter.

## <a name="c"></a>C\#

Als u een verzameling klanten wilt ophalen die overeenkomen met een filter, moet u eerst een [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) -object instantiëren om het filter te maken. U moet een teken reeks door geven die de [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield)bevat en het type filter bewerking aangeven als [**FieldFilterOperation. StartsWith**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation). Dat is de enige veld Filter bewerking die wordt ondersteund door het eind punt van de klant. U moet ook de teken reeks opgeven waarop u wilt filteren.

Instantiër vervolgens een [**iQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) -object om door te geven aan de query door de methode [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) aan te roepen en het filter door te geven. BuildSimplyQuery is slechts een van de typen query's die worden ondersteund door de klasse [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) .

Ten slotte, om het filter uit te voeren en het resultaat te verkrijgen, moet u eerst [**IAggregatePartner. klanten**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) gebruiken om een interface te verkrijgen voor de klant activiteiten van de partner. Roep vervolgens de methode [**query**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) of [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) aan.

``` csharp
IAggregatePartner partnerOperations;

// Specify the partial string to filter by (to match Contoso).
string searchPrefix = "cont"

// Create a simple field filter.
var fieldFilter = new SimpleFieldFilter(
    CustomerSearchField.CompanyName.ToString(),
    FieldFilterOperation.StartsWith,
    searchPrefix);

// Create an iQuery object to pass to the Query method.
var myQuery = QueryFactory.Instance.BuildSimpleQuery(fieldFilter);

// Get the collection of matching customers.
var customers = partnerOperations.Customers.Query(myQuery);
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: FilterCustomers.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers? grootte = {size} &filter = {filter} http/1.1 |

### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende query parameters.

| Naam   | Type   | Vereist | Beschrijving                                                                    |
|--------|--------|----------|--------------------------------------------------------------------------------|
| grootte   | int    | No       | Het aantal resultaten dat tegelijk moet worden weer gegeven. Deze parameter is optioneel. |
| filter | filter | Yes      | Het filter dat op klanten moet worden toegepast. Dit moet een gecodeerde teken reeks zijn.              |

### <a name="filter-syntax"></a>Filter syntaxis

U moet de filter parameter opstellen als een reeks door komma's gescheiden, sleutel-waardeparen. Elke sleutel en waarde moeten afzonderlijk worden genoteerd en gescheiden door een dubbele punt. Het volledige filter moet zijn gecodeerd.

Een niet-gecodeerd voor beeld ziet er als volgt uit:

```http
?filter{"Field":"CompanyName","Value":"cont","Operator":"starts_with"}
```

In de volgende tabel worden de vereiste sleutel-waardeparen beschreven:

| Sleutel      | Waarde                                                                                                                    |
|----------|--------------------------------------------------------------------------------------------------------------------------|
| Veld    | Het veld dat moet worden gefilterd. U kunt de geldige waarden vinden in [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield). |
| Waarde    | De waarde waarop moet worden gefilterd. Het geval van de waarde wordt genegeerd.                                                                |
| Operator | De operator die moet worden toegepast. De enige ondersteunde waarde voor dit klant scenario is "begint \_ met".                            |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=0&filter=%7B%22Field%22%3A%22CompanyName%22%2C%22Value%22%3A%22Cont%22%2C%22Operator%22%3A%22starts_with%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 5ce66de5-eea9-486f-a11c-c852aa3d1502
MS-CorrelationId: a2a912ee-d595-47e2-97ae-1b0ae1efa13d
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een verzameling overeenkomende [klant](customer-resources.md#customer) resources in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 1839
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a2a912ee-d595-47e2-97ae-1b0ae1efa13d
MS-RequestId: dfeda56c-1af5-43fc-a9c0-346b9e85dc96
MS-CV: n0lMNyJtaUC802pO.0
MS-ServerId: 202010223
Date: Fri, 24 Feb 2017 22:08:20 GMT

{
    "totalCount": 3,
    "items": [{
            "id": "c5757d70-06f3-4f23-8367-5a9e55019f94",
            "companyProfile": {
                "tenantId": "c5757d70-06f3-4f23-8367-5a9e55019f94",
                "domain": "contoso190.onmicrosoft.com",
                "companyName": "Contoso190",
                "links": {
                    "self": {
                        "uri": "/customers/c5757d70-06f3-4f23-8367-5a9e55019f94/profiles/company",
                        "method": "GET",
                        "headers": []
                    }
                },
                "attributes": {
                    "objectType": "CustomerCompanyProfile"
                }
            },
            "relationshipToPartner": "reseller",
            "links": {
                "self": {
                    "uri": "/customers/c5757d70-06f3-4f23-8367-5a9e55019f94",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }, {
            "id": "7b26b357-9ca3-48b8-a58e-4febe2662a5d",
            "companyProfile": {
                "tenantId": "7b26b357-9ca3-48b8-a58e-4febe2662a5d",
                "domain": "ContosoCorpCo.onmicrosoft.com",
                "companyName": "Contoso",
                "links": {
                    "self": {
                        "uri": "/customers/7b26b357-9ca3-48b8-a58e-4febe2662a5d/profiles/company",
                        "method": "GET",
                        "headers": []
                    }
                },
                "attributes": {
                    "objectType": "CustomerCompanyProfile"
                }
            },
            "relationshipToPartner": "reseller",
            "links": {
                "self": {
                    "uri": "/customers/7b26b357-9ca3-48b8-a58e-4febe2662a5d",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }, {
            "id": "bfbd6ef0-311f-47ec-bbd7-0fcb7846661b",
            "companyProfile": {
                "tenantId": "bfbd6ef0-311f-47ec-bbd7-0fcb7846661b",
                "domain": "contosocorpdemo.onmicrosoft.com",
                "companyName": "Contoso",
                "links": {
                    "self": {
                        "uri": "/customers/bfbd6ef0-311f-47ec-bbd7-0fcb7846661b/profiles/company",
                        "method": "GET",
                        "headers": []
                    }
                },
                "attributes": {
                    "objectType": "CustomerCompanyProfile"
                }
            },
            "relationshipToPartner": "reseller",
            "links": {
                "self": {
                    "uri": "/customers/bfbd6ef0-311f-47ec-bbd7-0fcb7846661b",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers?size=0&filter=%7B%22Field%22%3A%22Domain%22%2C%22Value%22%3A%22cont%22%2C%22Operator%22%3A%22starts_with%22%7D",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
