---
title: Gebruiksrecords van een klant ophalen voor Azure
description: U kunt de Azure-gebruiks API gebruiken om de gebruiks gegevens van het Azure-abonnement van een klant te verkrijgen voor een opgegeven periode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: bcdeb51b04039fd05b923150c85119385c0537e0
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767375"
---
# <a name="get-a-customers-utilization-records-for-azure"></a>Gebruiksrecords van een klant ophalen voor Azure

**Van toepassing op:**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

U kunt de gebruiks gegevens van het Azure-abonnement van een klant voor een opgegeven periode ophalen met behulp van de Azure-gebruiks-API.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Een abonnements-id.

Deze API retourneert dagelijks en niet-geclassificeerd verbruik voor een wille keurige tijds Panne. *Deze API wordt echter niet ondersteund voor Azure-abonnementen*. Als u een Azure-abonnement hebt, raadpleegt u de artikelen niet- [gefactureerde verbruiks regel items factureren](get-invoice-unbilled-consumption-lineitems.md) en [factuur verbruik regel items factureren ophalen](get-invoice-billed-consumption-lineitems.md) . In deze artikelen wordt beschreven hoe u het geclassificeerde verbruik op dagelijks niveau per resource kunt ophalen. Dit aantal is gelijk aan de gegevens van de dagelijks korrel die worden geleverd door de Azure-gebruiks-API. U moet de factuur-ID gebruiken om gefactureerde gebruiks gegevens op te halen. U kunt ook huidige en vorige Peri Oden gebruiken om niet-gefactureerde gebruik te schatten. *Gevarieerde gegevens en filters voor een wille keurig datum bereik worden momenteel niet ondersteund voor Azure plan-abonnements resources*.

## <a name="azure-utilization-api"></a>Azure-gebruiks-API

Deze Azure-gebruiks-API biedt toegang tot gebruiks records voor een tijds periode die aangeeft wanneer het gebruik is gerapporteerd in het facturerings systeem. Het biedt toegang tot dezelfde gebruiks gegevens die worden gebruikt voor het maken en berekenen van het afstemmings bestand. Het heeft echter geen kennis van de logica voor het afstemmen van het facturerings systeem. U mag geen samen vatting van de resultaten van een afstemmings bestand verwachten dat overeenkomt met het resultaat dat is opgehaald uit deze API precies voor dezelfde periode.

Het facturerings systeem neemt bijvoorbeeld dezelfde gebruiks gegevens op en past de regels voor de achterstand toe om te bepalen wat er in een afstemmings bestand is verwerkt. Wanneer een facturerings periode wordt gesloten, wordt alle gebruik tot het eind van de dag waarop de facturerings periode eindigt, opgenomen in het afstemmings bestand. Een vertraagd gebruik binnen de facturerings periode die binnen 24 uur na het einde van de facturerings periode wordt gerapporteerd, wordt in het volgende afstemmings bestand verwerkt. Zie [verbruiks gegevens ophalen voor een Azure-abonnement](/previous-versions/azure/reference/mt219001(v=azure.100))voor de regels voor de achterstand van hoe de partner wordt gefactureerd.

Deze REST API is gewisseld. Als de reactie lading groter is dan één pagina, moet u de volgende koppeling volgen om de volgende pagina met gebruiks gegevens op te halen.

## <a name="c"></a>C\#

Voor het verkrijgen van de Azure-gebruiks records:

1. Haal de klant-ID en de abonnements-ID op.

2. Roep de methode [**IAzureUtilizationCollection. query**](/dotnet/api/microsoft.store.partnercenter.utilization.iazureutilizationcollection.query) aan om een [**ResourceCollection**](/dotnet/api/microsoft.store.partnercenter.models.resourcecollection-1) te retour neren die de gebruiks records bevat.

3. Verkrijg een inventaris van het Azure-gebruik record om de gebruiks pagina's te passeren. Deze stap is vereist omdat de resource verzameling is gewisseld.

- Voor **beeld**: [console test-app](console-test-app.md)
- **Project**: Partner Center SDK-voor beelden
- **Klasse**: GetAzureSubscriptionUtilization.cs

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

IPartner partner = PartnerService.Instance.CreatePartnerOperations(credentials);

// Retrieve the utilization records for the last year in pages of 100 records.
var utilizationRecords = partner.Customers[customerId].Subscriptions[subscriptionId].Utilization.Azure.Query(
    DateTimeOffset.Now.AddYears(-1),
    DateTimeOffset.Now,
    size: 100);

// Create an Azure utilization enumerator which will aid us in traversing the utilization pages.
var utilizationRecordEnumerator = partner.Enumerators.Utilization.Azure.Create(utilizationRecords);

while (utilizationRecordEnumerator.HasValue)
{
    //
    // Insert code here to work with this page.
    //

    // Get the next page.
    utilizationRecordEnumerator.Next();
}
```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Als u Azure-gebruiks records wilt verkrijgen, hebt u eerst een klant-id en een abonnements-id nodig. Vervolgens roept u de functie **IAzureUtilizationCollection. query** aan om een **ResourceCollection** te retour neren die de gebruiks records bevat. Omdat de resource verzameling is gewisseld, moet u een inventaris van het Azure-gebruik record verkrijgen om de gebruiks pagina's te passeren.

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String subscriptionId;

ResourceCollection<AzureUtilizationRecord> utilizationRecords = partnerOperations.getCustomers()
  .byId(customerId).getSubscriptions().byId(subscriptionId)
  .getUtilization().getAzure().query(
      new DateTime().minusYears(1),
      new DateTime(),
      AzureUtilizationGranularity.Daily,
      true,
      100);

// Create an Azure utilization enumerator which will aid us in traversing the utilization pages
IResourceCollectionEnumerator<ResourceCollection<AzureUtilizationRecord>> utilizationRecordEnumerator =
    partnerOperations.getEnumerators().getUtilization().getAzure().create(utilizationRecords);

while (utilizationRecordEnumerator.hasValue())
{
    //
    // Insert code here to work with this page.
    //

    // get the next page
    utilizationRecordEnumerator.next();
}
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Als u Azure-gebruiks records wilt verkrijgen, hebt u eerst een klant-id en een abonnements-id nodig. Vervolgens roept u de [**Get-PartnerCustomerSubscriptionUtilization aan**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscriptionUtilization.md). Met deze opdracht worden alle records geretourneerd die beschikbaar zijn voor de opgegeven periode.

```powershell
# $customerId
# $subscriptionId

Get-PartnerCustomerSubscriptionUtilization -CustomerId $customerId -SubscriptionId $subscriptionId -StartDate (Get-Date).AddDays(-2).ToUniversalTime() -Granularity Hourly -ShowDetails
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode | Aanvraag-URI |
|------- | ----------- |
| **Toevoegen** | *{baseURL}*/v1/Customers/{Customer-Tenant-id}/Subscriptions/{Subscription-id}/utilizations/Azure? begin \_ tijd = {start-time} &eind \_ tijd = {end-time} &granulatie = {granulatie} &details weer geven \_ = {True} |

#### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende pad-en query parameters om de gebruiks gegevens op te halen.

| Naam | Type | Vereist | Beschrijving |
| ---- | ---- | -------- | ----------- |
| klant-Tenant-id | tekenreeks | Yes | Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd. |
| abonnement-id | tekenreeks | Yes | Een teken reeks met een GUID-indeling waarmee het abonnement wordt geïdentificeerd. |
| start_tijd | teken reeks in UTC-notatie voor datum/tijd-offset | Yes | Het begin van het tijds bereik dat aangeeft wanneer het gebruik is gerapporteerd in het facturerings systeem. |
| end_time | teken reeks in UTC-notatie voor datum/tijd-offset | Yes | Het einde van het tijds bereik dat aangeeft wanneer het gebruik is gerapporteerd in het facturerings systeem. |
| granulatie | tekenreeks | No | Hiermee definieert u de granulatie van gebruiks aggregaties. Beschik bare opties zijn: `daily` (standaard) en `hourly` .
| show_details | booleaans | No | Hiermee wordt aangegeven of de details van het gebruik op exemplaar niveau moeten worden opgehaald. De standaardwaarde is `true`. |
| grootte | getal | No | Hiermee geeft u het aantal aggregaties op dat door één API-aanroep wordt geretourneerd. De standaardwaarde is 1000. De maximum waarde is 1000. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

De volgende voorbeeld aanvraag produceert resultaten die vergelijkbaar zijn met wat het afstemmings bestand zal weer geven voor de periode van 7/2-8/1. Deze resultaten komen mogelijk niet exact overeen (Zie de sectie [Azure-gebruiks-API](#azure-utilization-api) voor meer informatie).

In dit voor beeld wordt een aanvraag voor het retour neren van gebruiks gegevens gerapporteerd in het facturerings systeem tussen 7/2 bij 12 uur (UTC) en 8/2 om 12 uur (UTC).

```http
GET https://api.partnercenter.microsoft.com/v1/customers/E499C962-9218-4DBA-8B83-8ADC94F47B9F/subscriptions/FC8F8908-F918-4406-AF13-D5BC0FE41865/utilizations/azure?start_time=2017-07-02T00:00:00-08:00&end_time=2017-08-02T00:00:00-08:00 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een verzameling van [Azure-gebruik record](azure-utilization-record-resources.md) bronnen in de hoofd tekst van het antwoord. Als de Azure-gebruiks gegevens nog niet gereed zijn in een afhankelijk systeem, retourneert deze methode een HTTP-status code 204 met een Retry-After-header.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om de HTTP-status code, het [fout code type](error-codes.md)en aanvullende para meters te lezen.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 2630
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CV: PjuGoYrw806o6A3Y.0
MS-ServerId: 030020525
Date: Fri, 04 Aug 2017 23:48:28 GMT

{
  "totalCount": 2,
  "items": [
    {
      "usageStartTime": "2017-06-07T17:00:00-07:00",
      "usageEndTime": "2017-06-08T17:00:00-07:00",
      "resource": {
        "id": "8767aeb3-6909-4db2-9927-3f51e9a9085e",
        "name": "Storage Admin",
        "category": "Storage",
        "subcategory": "Block Blob",
        "region": "Azure Stack"
      },
      "quantity": 0.217790327034891,
      "unit": "1 GB/Hr",
      "infoFields": {},
      "instanceData": {
        "resourceUri": "/subscriptions/ab7e2384-eeee-489a-a14f-1eb41ddd261d/resourcegroups/system.local/providers/Microsoft.Storage/storageaccounts/srphealthaccount",
        "location": "azurestack",
        "partNumber": "",
        "orderNumber": "",
        "additionalInfo": {
          "azureStack.MeterId": "09F8879E-87E9-4305-A572-4B7BE209F857",
          "azureStack.SubscriptionId": "dbd1aa30-e40d-4436-b465-3a8bc11df027",
          "azureStack.Location": "local",
          "azureStack.EventDateTime": "06/05/2017 06:00:00"
        }
      },
      "attributes": {
        "objectType": "AzureUtilizationRecord"
      }
    },
    {
      "usageStartTime": "2017-06-07T17:00:00-07:00",
      "usageEndTime": "2017-06-08T17:00:00-07:00",
      "resource": {
        "id": "8767aeb3-6909-4db2-9927-3f51e9a9085e",
        "name": "Storage Admin",
        "category": "Storage",
        "subcategory": "Block Blob",
        "region": "Azure Stack"
      },
      "quantity": 0.217790327034891,
      "unit": "1 GB/Hr",
      "infoFields": {},
      "instanceData": {
        "resourceUri": "/subscriptions/ab7e2384-eeee-489a-a14f-1eb41ddd261d/resourcegroups/system.local/providers/Microsoft.Storage/storageaccounts/srphealthaccount",
        "location": "azurestack",
        "partNumber": "",
        "orderNumber": "",
        "additionalInfo": {
          "azureStack.MeterId": "09F8879E-87E9-4305-A572-4B7BE209F857",
          "azureStack.SubscriptionId": "dbd1aa30-e40d-4436-b465-3a8bc11df027",
          "azureStack.Location": "local",
          "azureStack.EventDateTime": "06/05/2017 06:00:00"
        },
        "attributes": {
          "objectType": "AzureUtilizationRecord"
        }
      },

      "links": {
        "self": {
          "uri": "customers/E499C962-9218-4DBA-8B83-8ADC94F47B9F/subscriptions/FC8F8908-F918-4406-AF13-D5BC0FE41865/utilizations/azure?start_time=2017-06-10T00:00:00Z&end_time=2017-07-09T00:00:00Z&granularity=Daily&show_details=True&size=1000",
          "method": "GET",
          "headers": []
        }
      },
      "attributes": {
        "objectType": "Collection"
      }
    }
  ]
}
```
