---
title: Een record van Partnercentrum-activiteiten ophalen
description: Het ophalen van een record van bewerkingen, zoals uitgevoerd door een partner gebruiker of toepassing, gedurende een bepaalde periode.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 2f37eae8bb96c1c1e7008e8c566b085e25d8807d
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767438"
---
# <a name="get-a-record-of-partner-center-activity"></a>Een record van Partnercentrum-activiteiten ophalen

**Van toepassing op**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

In dit artikel wordt beschreven hoe u een record kunt ophalen van bewerkingen die gedurende een bepaalde periode zijn uitgevoerd door een partner gebruiker of-toepassing.

Gebruik deze API om controle records op te halen voor de afgelopen 30 dagen vanaf de huidige datum of voor een datum bereik dat is opgegeven met inbegrip van de begin datum en/of de eind datum. Houd er echter rekening mee dat de beschik baarheid van het activiteiten logboek voor de prestaties beperkt is tot de vorige 90 dagen. Aanvragen met een begin datum die groter is dan 90 dagen vóór de huidige datum worden een ongeldige aanvraag uitzondering ontvangen (fout code: 400) en een geschikt bericht.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

## <a name="c"></a>C\#

Als u een record van partner Center-bewerkingen wilt ophalen, moet u eerst het datum bereik instellen voor de records die u wilt ophalen. In het volgende code voorbeeld wordt alleen een begin datum gebruikt, maar u kunt ook een eind datum toevoegen. Zie de [**query**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) methode voor meer informatie. Maak vervolgens de variabelen die u nodig hebt voor het type filter dat u wilt Toep assen en wijs de juiste waarden toe. Als u bijvoorbeeld wilt filteren op subtekenreeks bedrijfs naam, maakt u een variabele voor de subtekenreeks. Als u wilt filteren op klant-ID, maakt u een variabele om de ID op te slaan.

In het volgende voor beeld wordt de voorbeeld code verschaft om te filteren op een subtekenreeks van een bedrijfs naam, een klant-ID of een resource type. U kunt een opmerking kiezen en de andere opmerkingen toevoegen. In elk geval maakt u eerst een [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) -object met behulp van de standaard [**constructor**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter.-ctor) om het filter te maken. U moet een teken reeks door geven die het veld bevat waarop moet worden gezocht en de toepasselijke operator die u wilt Toep assen, zoals wordt weer gegeven. U moet ook de teken reeks opgeven waarop moet worden gefilterd.

Gebruik vervolgens de eigenschap [**AuditRecords**](/dotnet/api/microsoft.store.partnercenter.ipartner.auditrecords) om een interface op te halen voor het controleren van record bewerkingen en roep de methode [**query**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) of [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.queryasync) aan om het filter uit te voeren en de verzameling van [**AuditRecord**](/dotnet/api/microsoft.store.partnercenter.models.auditing.auditrecord) te verkrijgen die de eerste pagina van het resultaat voor stelt. Geef de methode de start datum, een optionele eind datum die niet in het voor beeld wordt gebruikt en een [**IQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) -object dat een query op een entiteit vertegenwoordigt. Het IQuery-object wordt gemaakt door het hierboven gemaakte filter door te geven aan de [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) -methode [**van QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) .

Wanneer u de eerste pagina van de items hebt, gebruikt u de methode [**enumerats. AuditRecords. Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) om een enumerator te maken die u kunt gebruiken om de resterende pagina's te herhalen.

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

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **map**: controleren

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                                                                                                                    |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords? start date = {start date} http/1.1                                                                                                     |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords? start date = {start date} &EndDate = {ENDDATE} http/1.1                                                                                   |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords? start date = {start date} &EndDate = {endDate} &filter = {"veld:" CompanyName "," waarde ":" {searchSubstring} "," operator ":" subtekenreeks "} http/1.1 |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords? start date = {start date} &EndDate = {endDate} &filter = {"veld": "KlantId", "waarde": "{KlantId}", "operator": "is gelijk aan"} http/1.1          |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords? start date = {start date} &EndDate = {endDate} &filter = {"veld:" resource type "," waarde ":" {resource type} "," operator ":" is gelijk aan "} http/1.1      |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende query parameters bij het maken van de aanvraag.

| Naam      | Type   | Vereist | Beschrijving                                                                                                                                                                                                                |
|-----------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Begin | date   | No       | De begin datum in de indeling jjjj-mm-dd. Als er geen is opgegeven, wordt de resultatenset standaard ingesteld op 30 dagen vóór de aanvraag datum. Deze para meter is optioneel wanneer een filter wordt opgegeven.                                          |
| endDate   | date   | No       | De eind datum in de indeling jjjj-mm-dd. Deze para meter is optioneel wanneer een filter wordt opgegeven. Wanneer de eind datum wordt wegge laten of op NULL wordt ingesteld, retourneert de aanvraag het maximum venster of wordt het vandaag als eind datum gebruikt, afhankelijk van wat kleiner is. |
| filter    | tekenreeks | No       | Het filter dat moet worden toegepast. Deze para meter moet een gecodeerde teken reeks zijn. Deze para meter is optioneel wanneer de begin-of eind datum wordt opgegeven.                                                                                              |

### <a name="filter-syntax"></a>Filter syntaxis
U moet de filter parameter opstellen als een reeks door komma's gescheiden, sleutel-waardeparen. Elke sleutel en waarde moeten afzonderlijk worden genoteerd en gescheiden door een dubbele punt. Het volledige filter moet zijn gecodeerd.

Een niet-gecodeerd voor beeld ziet er als volgt uit:

```
?filter{"Field":"CompanyName","Value":"bri","Operator":"substring"}
```

In de volgende tabel worden de vereiste sleutel-waardeparen beschreven:

| Sleutel                 | Waarde                             |
|:--------------------|:----------------------------------|
| Veld               | Het veld dat moet worden gefilterd. De ondersteunde waarden zijn te vinden in de [aanvraag syntaxis](get-a-record-of-partner-center-activity-by-user.md#rest-request).                                         |
| Waarde               | De waarde waarop moet worden gefilterd. Het geval van de waarde wordt genegeerd. De volgende waarde-para meters worden ondersteund, zoals wordt weer gegeven in de [aanvraag syntaxis](get-a-record-of-partner-center-activity-by-user.md#rest-request):<br/><br/>                                                                *searchSubstring* : Vervang door de naam van het bedrijf. U kunt een subtekenreeks invoeren die overeenkomt met een deel van de bedrijfs naam (bijvoorbeeld komt `bri` overeen met `Fabrikam, Inc` ).<br/>**Voor beeld:**`"Value":"bri"`<br/><br/>                                                                *KlantId* -vervangen door een teken reeks met een GUID-indeling die de klant-id vertegenwoordigt.<br/>**Voor beeld:**`"Value":"0c39d6d5-c70d-4c55-bc02-f620844f3fd1"`<br/><br/>                                                                                        *resource* type: Vervang door het type resource waarvoor controle records moeten worden opgehaald (bijvoorbeeld abonnement). De beschik bare resource typen worden gedefinieerd in [resource type](/dotnet/api/microsoft.store.partnercenter.models.auditing.resourcetype).<br/>**Voor beeld:**`"Value":"Subscription"`                                 |
| Operator          | De operator die moet worden toegepast. De ondersteunde Opera tors zijn te vinden in de [aanvraag syntaxis](get-a-record-of-partner-center-activity-by-user.md#rest-request).   |

### <a name="request-headers"></a>Aanvraagheaders

- Zie [rest-headers Centers](headers.md) voor meer informatie.

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

Als dit lukt, retourneert deze methode een set activiteiten die aan de filters voldoen.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

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