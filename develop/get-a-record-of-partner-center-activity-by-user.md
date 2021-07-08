---
title: Een record van Partnercentrum-activiteiten ophalen
description: Het ophalen van een record van bewerkingen, zoals uitgevoerd door een partnergebruiker of -toepassing, gedurende een bepaalde periode.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: aec933d4b681d99080619505792bde56bdd25580
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873968"
---
# <a name="get-a-record-of-partner-center-activity"></a>Een record van Partnercentrum-activiteiten ophalen

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

In dit artikel wordt beschreven hoe u een record kunt ophalen van bewerkingen die gedurende een bepaalde periode door een partnergebruiker of toepassing zijn uitgevoerd.

Gebruik deze API om controlerecords op te halen voor de afgelopen 30 dagen vanaf de huidige datum, of voor een datumbereik dat is opgegeven door de begindatum en/of einddatum op te neemt. Houd er echter rekening mee dat om prestatieredenen de beschikbaarheid van gegevens in het activiteitenlogboek is beperkt tot de afgelopen 90 dagen. Aanvragen met een begindatum die langer is dan 90 dagen vóór de huidige datum, ontvangen een uitzondering met een slechte aanvraag (foutcode: 400) en een geschikt bericht.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

## <a name="c"></a>C\#

Als u een record met Partner Center wilt ophalen, moet u eerst het datumbereik bepalen voor de records die u wilt ophalen. In het volgende codevoorbeeld wordt alleen een begindatum gebruikt, maar u kunt ook een einddatum opnemen. Zie de Query-methode voor [**meer**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) informatie. Maak vervolgens de variabelen die u nodig hebt voor het type filter dat u wilt toepassen en wijs de juiste waarden toe. Als u bijvoorbeeld wilt filteren op bedrijfsnaamsubtekenreeks, maakt u een variabele om de subtekenreeks op te nemen. Als u wilt filteren op klant-id, maakt u een variabele voor de id.

In het volgende voorbeeld wordt voorbeeldcode verstrekt om te filteren op een bedrijfsnaamsubtekenreeks, klant-id of resourcetype. Kies een optie en maak commentaar van de andere. In elk geval instantieert u eerst een [**SimpleFieldFilter-object**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) met behulp van de standaard [**constructor om**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter.-ctor) het filter te maken. U moet een tekenreeks doorgeven die het veld bevat dat moet worden gezocht en de juiste operator om toe te passen, zoals wordt weergegeven. U moet ook de tekenreeks verstrekken om op te filteren.

Gebruik vervolgens de eigenschap [**AuditRecords**](/dotnet/api/microsoft.store.partnercenter.ipartner.auditrecords) om een interface op te halen voor het controleren van recordbewerkingen en roep de methode [**Query**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) of [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.queryasync) aan om het filter uit te voeren en de verzameling [**auditrecords**](/dotnet/api/microsoft.store.partnercenter.models.auditing.auditrecord) op te halen die de eerste pagina van het resultaat vertegenwoordigen. Geef de methode door aan de begindatum, een optionele einddatum die hier niet wordt gebruikt in het voorbeeld en een [**IQuery-object**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) dat een query op een entiteit vertegenwoordigt. Het IQuery-object wordt gemaakt door het hierboven gemaakte filter door te geven aan de [**BuildSimpleQuery-methode van**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) [**QueryFactory.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory)

Zodra u de eerste pagina met items hebt, gebruikt u de methode [**Enumerators.AuditRecords.Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) om een enumerator te maken die u kunt gebruiken om de resterende pagina's te controleren.

```csharp
// IAggregatePartner partnerOperations;

var startDate = new DateTime(DateTime.Now.Year, DateTime.Now.Month, 01);

// First perform the query, then get the enumerator. Choose one of the following and comment out the other two.

// To retrieve audit records by company name substring (for example "bri" matches "Fabrikam, Inc.").
var searchSubstring="bri";
var filter = new SimpleFieldFilter(AuditRecordSearchField.CompanyName.ToString(), FieldFilterOperation.Substring, searchSubstring);
var auditRecordsPage = partnerOperations.AuditRecords.Query(startDate.Date, query: QueryFactory.Instance.BuildSimpleQuery(filter));

// To retrieve audit records by customer ID.
var customerId="0c39d6d5-c70d-4c55-bc02-f620844f3fd1";
var filter = new SimpleFieldFilter(AuditRecordSearchField.CustomerId.ToString(), FieldFilterOperation.Equals, customerId);
var auditRecordsPage = partnerOperations.AuditRecords.Query(startDate.Date, query: QueryFactory.Instance.BuildSimpleQuery(filter));

// To retrieve audit records by resource type.
int resourceTypeInt = 3; // Subscription Resource.
string searchField = Enum.GetName(typeof(ResourceType), resourceTypeInt);
var filter = new SimpleFieldFilter(AuditRecordSearchField.ResourceType.ToString(), FieldFilterOperation.Equals, searchField);
var auditRecordsPage = partnerOperations.AuditRecords.Query(startDate.Date, query: QueryFactory.Instance.BuildSimpleQuery(filter));

var auditRecordEnumerator = partnerOperations.Enumerators.AuditRecords.Create(auditRecordsPage);

int pageNumber = 1;
while (auditRecordEnumerator.HasValue)
{
    // Work with the current page.
    foreach (var c in auditRecordEnumerator.Current.Items)
    {
        // Display some info, such as operation type, operation date, and operation status.
        Console.WriteLine(string.Format("{0} {1} {2}.", c.OperationType, c.OperationDate, c.OperationStatus));
    }

    // Get the next page of audit records.
    auditRecordEnumerator.Next();
}
```

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project:** Partnercentrum-SDK **map Samples:** Controle

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                                                                                                    |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate} HTTP/1.1                                                                                                     |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate} HTTP/1.1                                                                                   |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"CompanyName","Value":"{searchSubstring}","Operator":"substring"} HTTP/1.1 |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"CustomerId","Value":"{customerId}","Operator":"equals"} HTTP/1.1          |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"ResourceType","Value":"{resourceType}","Operator":"equals"} HTTP/1.1      |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameters bij het maken van de aanvraag.

| Naam      | Type   | Vereist | Beschrijving                                                                                                                                                                                                                |
|-----------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Startdate | date   | Nee       | De begindatum in de indeling yyyy-mm-dd. Als er geen is opgegeven, wordt de resultatenset standaard ingesteld op 30 dagen vóór de aanvraagdatum. Deze parameter is optioneel wanneer een filter wordt opgegeven.                                          |
| Enddate   | date   | Nee       | De einddatum in de indeling yyyy-mm-dd. Deze parameter is optioneel wanneer een filter wordt opgegeven. Wanneer de einddatum wordt weggelaten of ingesteld op null, retourneert de aanvraag het maximumvenster of gebruikt vandaag als de einddatum, wat kleiner is. |
| filter    | tekenreeks | No       | Het filter dat moet worden toegepast. Deze parameter moet een gecodeerde tekenreeks zijn. Deze parameter is optioneel wanneer de begindatum of einddatum wordt opgegeven.                                                                                              |

### <a name="filter-syntax"></a>Filtersyntaxis
U moet de filterparameter opstellen als een reeks door komma's gescheiden sleutel-waardeparen. Elke sleutel en waarde moeten afzonderlijk worden aangehaald en gescheiden door een dubbele punt. Het hele filter moet worden gecodeerd.

Een niet-gecodeerd voorbeeld ziet er als volgende uit:

```
?filter{"Field":"CompanyName","Value":"bri","Operator":"substring"}
```

In de volgende tabel worden de vereiste sleutel-waardeparen beschreven:

| Sleutel                 | Waarde                             |
|:--------------------|:----------------------------------|
| Veld               | Het veld dat moet worden gefilterd. De ondersteunde waarden vindt u in [Aanvraagsyntaxis.](get-a-record-of-partner-center-activity-by-user.md#rest-request)                                         |
| Waarde               | De waarde die moet worden gefilterd op. Het geval van de waarde wordt genegeerd. De volgende waardeparameters worden ondersteund, zoals wordt weergegeven in [Aanvraagsyntaxis:](get-a-record-of-partner-center-activity-by-user.md#rest-request)<br/><br/>                                                                *searchSubstring:* vervang door de naam van het bedrijf. U kunt een subtekenreeks invoeren die overeen komt met een deel van de bedrijfsnaam (komt bijvoorbeeld `bri` overeen met `Fabrikam, Inc` ).<br/>**Voorbeeld:**`"Value":"bri"`<br/><br/>                                                                *customerId:* vervang door een tekenreeks met GUID-indeling die de klant-id vertegenwoordigt.<br/>**Voorbeeld:**`"Value":"0c39d6d5-c70d-4c55-bc02-f620844f3fd1"`<br/><br/>                                                                                        *resourceType:* vervang door het type resource waarvoor controlerecords moeten worden opgehaald (bijvoorbeeld Abonnement). De beschikbare resourcetypen worden gedefinieerd in [ResourceType](/dotnet/api/microsoft.store.partnercenter.models.auditing.resourcetype).<br/>**Voorbeeld:**`"Value":"Subscription"`                                 |
| Operator          | De operator die moet worden toegepast. De ondersteunde operators vindt u in [Aanvraagsyntaxis.](get-a-record-of-partner-center-activity-by-user.md#rest-request)   |

### <a name="request-headers"></a>Aanvraagheaders

- Zie [Parter Center REST-headers voor meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/auditrecords?startDate=6/1/2017%2012:00:00%20AM&filter=%7B%22Field%22:%22CustomerId%22,%22Value%22:%220c39d6d5-c70d-4c55-bc02-f620844f3fd1%22,%22Operator%22:%22equals%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 127facaa-e389-41f8-8bb7-1d1af99db893
MS-CorrelationId: de9c2ccc-40dd-4186-9660-65b9b64c3d14
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een reeks activiteiten die voldoen aan de filters.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 2859
Content-Type: application/json; charset=utf-8
MS-CorrelationId: de9c2ccc-40dd-4186-9660-65b9b64c3d14
MS-RequestId: 127facaa-e389-41f8-8bb7-1d1af99db893
MS-CV: 4xDKynq/zE2im0wj.0
MS-ServerId: 030011719
Date: Tue, 27 Jun 2017 22:19:46 GMT

{
    "totalCount": 2,
    "items": [{
            "partnerId": "3b33e682-00c3-41ee-9dd2-a548adf56438",
            "customerId": "0c39d6d5-c70d-4c55-bc02-f620844f3fd1",
            "customerName": "Relecloud",
            "userPrincipalName": "admin@domain.onmicrosoft.com",
            "resourceType": "order",
            "resourceNewValue": "{\"Id\":\"d51a052e-043c-4a2a-aa37-2bb938cef6c1\",\"ReferenceCustomerId\":\"0c39d6d5-c70d-4c55-bc02-f620844f3fd1\",\"BillingCycle\":\"none\",\"LineItems\":[{\"LineItemNumber\":0,\"OfferId\":\"C0BD2E08-11AC-4836-BDC7-3712E744922F\",\"SubscriptionId\":\"488745B5-2086-4912-802C-6ABB9F7C3638\",\"ParentSubscriptionId\":null,\"FriendlyName\":\"Office 365 Business Premium Trial\",\"Quantity\":25,\"PartnerIdOnRecord\":null,\"Links\":{\"Subscription\":{\"Uri\":\"/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/488745B5-2086-4912-802C-6ABB9F7C3638\",\"Method\":\"GET\",\"Headers\":[]}}}],\"CreationDate\":\"2017-06-15T15:56:04.077-07:00\",\"Links\":{\"Self\":{\"Uri\":\"/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/orders/d51a052e-043c-4a2a-aa37-2bb938cef6c1\",\"Method\":\"GET\",\"Headers\":[]}},\"Attributes\":{\"Etag\":\"eyJpZCI6ImQ1MWEwNTJlLTA0M2MtNGEyYS1hYTM3LTJiYjkzOGNlZjZjMSIsInZlcnNpb24iOjF9\",\"ObjectType\":\"Order\"}}",
            "operationType": "create_order",
            "operationDate": "2017-06-15T22:56:05.0589308Z",
            "operationStatus": "succeeded",
            "customizedData": [{
                    "key": "OrderId",
                    "value": "d51a052e-043c-4a2a-aa37-2bb938cef6c1"
                }, {
                    "key": "BillingCycle",
                    "value": "None"
                }, {
                    "key": "OfferId-0",
                    "value": "C0BD2E08-11AC-4836-BDC7-3712E744922F"
                }, {
                    "key": "SubscriptionId-0",
                    "value": "488745B5-2086-4912-802C-6ABB9F7C3638"
                }, {
                    "key": "SubscriptionName-0",
                    "value": "Office 365 Business Premium Trial"
                }, {
                    "key": "Quantity-0",
                    "value": "25"
                }, {
                    "key": "PartnerOnRecord-0",
                    "value": null
                }
            ],
            "attributes": {
                "objectType": "AuditRecord"
            }
        }, {
            "partnerId": "3b33e682-00c3-41ee-9dd2-a548adf56438",
            "customerId": "0c39d6d5-c70d-4c55-bc02-f620844f3fd1",
            "customerName": "Relecloud",
            "userPrincipalName": "admin@domain.onmicrosoft.com",
            "applicationId": "Partner Center Native App",
            "resourceType": "license",
            "resourceNewValue": "{\"LicensesToAssign\":[{\"ExcludedPlans\":null,\"SkuId\":\"efccb6f7-5641-4e0e-bd10-b4976e1bf68e\"}],\"LicensesToRemove\":null,\"LicenseWarnings\":[],\"Attributes\":{\"ObjectType\":\"LicenseUpdate\"}}",
            "operationType": "update_customer_user_licenses",
            "operationDate": "2017-06-01T20:09:07.0450483Z",
            "operationStatus": "succeeded",
            "customizedData": [{
                    "key": "CustomerUserId",
                    "value": "482e2152-4b49-48ec-b715-823365ce3d4c"
                }, {
                    "key": "AddedLicenseSkuId",
                    "value": "efccb6f7-5641-4e0e-bd10-b4976e1bf68e"
                }
            ],
            "attributes": {
                "objectType": "AuditRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/auditrecords?startDate=2017-06-01&size=500&filter=%7B%22Field%22%3A%22CustomerId%22%2C%22Value%22%3A%220c39d6d5-c70d-4c55-bc02-f620844f3fd1%22%2C%22Operator%22%3A%22equals%22%7D",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```