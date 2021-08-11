---
title: Een lijst met klanten ophalen die zijn gefilterd op basis van een zoekveld
description: Haalt een verzameling klantbronnen op die overeenkomen met een filter. U kunt desgewenst een paginaformaat instellen. U kunt filteren op bedrijfsnaam, domein, indirecte reseller of indirecte cloudoplossingsprovider (CSP).
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 4e77edd3e7d94711ad18796c0afb4db30c50abf0bc9636335b413a5d41dff9c8
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115993092"
---
# <a name="get-a-list-of-customers-filtered-by-a-search-field"></a>Een lijst met klanten ophalen die zijn gefilterd op basis van een zoekveld

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Haalt een verzameling [klantbronnen op](customer-resources.md#customer) die overeenkomen met een filter. U kunt desgewenst een paginaformaat instellen. U kunt filteren op bedrijfsnaam, domein, indirecte reseller of indirecte cloudoplossingsprovider (CSP).

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een door de gebruiker samengesteld filter.

## <a name="c"></a>C\#

Als u een verzameling klanten wilt ophalen die overeenkomen met een filter, instantieer dan eerst een [**SimpleFieldFilter-object**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) om het filter te maken. U moet een tekenreeks doorgeven die [**customerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield)bevat en het type filterbewerking als [**FieldFilterOperation.StartsWith aangeven.**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation) Dat is de enige veldfilterbewerking die wordt ondersteund door het eindpunt van de klant. U moet ook de tekenreeks verstrekken om op te filteren.

Maak vervolgens een [**iQuery-object**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) om door te geven aan de query door de [**methode BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) aan te roepen en dit door te geven aan het filter. BuildSimplyQuery is slechts een van de querytypen die wordt ondersteund door de [**klasse QueryFactory.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory)

Als u ten slotte het filter wilt uitvoeren en het resultaat wilt krijgen, gebruikt u [**eerst IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) om een interface te krijgen met de klantbewerkingen van de partner. Roep vervolgens de [**methode Query**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) of [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) aan.

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

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project:** Partnercentrum-SDK Samples **Class:** FilterCustomers.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size}&filter={filter} HTTP/1.1 |

### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende queryparameters.

| Naam   | Type   | Vereist | Beschrijving                                                                    |
|--------|--------|----------|--------------------------------------------------------------------------------|
| grootte   | int    | No       | Het aantal resultaten dat in één keer moet worden weergegeven. Deze parameter is optioneel. |
| filter | filter | Yes      | Het filter dat moet worden toegepast op klanten. Dit moet een gecodeerde tekenreeks zijn.              |

### <a name="filter-syntax"></a>Filtersyntaxis

U moet de filterparameter opstellen als een reeks door komma's gescheiden sleutel-waardeparen. Elke sleutel en waarde moeten afzonderlijk worden aangehaald en gescheiden door een dubbele punt. Het volledige filter moet worden gecodeerd.

Een niet-gecodeerd voorbeeld ziet er als volgende uit:

```http
?filter{"Field":"CompanyName","Value":"cont","Operator":"starts_with"}
```

In de volgende tabel worden de vereiste sleutel-waardeparen beschreven:

| Sleutel      | Waarde                                                                                                                    |
|----------|--------------------------------------------------------------------------------------------------------------------------|
| Veld    | Het veld dat moet worden gefilterd. De geldige waarden vindt u in [**CustomerSearchField.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield) |
| Waarde    | De waarde om op te filteren. Het geval van de waarde wordt genegeerd.                                                                |
| Operator | De operator die moet worden toegepast. De enige ondersteunde waarde voor dit klantscenario is 'begint \_ met'.                            |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

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

Als dit lukt, retourneert deze methode een verzameling overeenkomende [Klantresources](customer-resources.md#customer) in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

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
