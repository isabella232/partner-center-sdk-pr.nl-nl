---
title: Gebruiksrecords van een klant ophalen voor Azure
description: U kunt de API voor Azure-gebruik gebruiken om de gebruiksrecords van het Azure-abonnement van een klant op te halen voor een opgegeven periode.
ms.date: 04/19/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7024bc65976a9b43a62b66c529d271519181ab23
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874921"
---
# <a name="get-a-customers-utilization-records-for-azure"></a>Gebruiksrecords van een klant ophalen voor Azure

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

U kunt de gebruiksrecords van het Azure-abonnement van een klant voor een opgegeven periode op halen met behulp van de API voor Azure-gebruik.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een abonnements-id.

Deze API retourneert dagelijks en elk uur een onaangewaardeerd verbruik voor een willekeurige periode. Deze *API wordt echter niet ondersteund voor Azure-plannen.* Als u een Azure-abonnement hebt, bekijkt u de artikelen [Niet-gefactureerde](get-invoice-unbilled-consumption-lineitems.md) verbruiksregelitems ontvangen en In plaats daarvan gefactureerde [verbruiksregelitems](get-invoice-billed-consumption-lineitems.md) ontvangen. In deze artikelen wordt beschreven hoe u een gemiddeld verbruik per dag per meter per resource kunt krijgen. Dit tariefverbruik is gelijk aan de dagelijkse grain-gegevens die worden geleverd door de Azure-gebruiks-API. U moet de factuur-id gebruiken om gefactureerde gebruiksgegevens op te halen. U kunt ook huidige en vorige perioden gebruiken om niet-gebileerde gebruiksschattingen op te halen. Gegevens die per uur worden verzameld en willekeurige *datumbereikfilters worden momenteel niet ondersteund voor abonnementsresources van het Azure-plan*.

## <a name="azure-utilization-api"></a>Api voor Azure-gebruik

Deze API voor Azure-gebruik biedt toegang tot gebruiksrecords voor een periode die vertegenwoordigt wanneer het gebruik is gerapporteerd in het factureringssysteem. Het biedt toegang tot dezelfde gebruiksgegevens die worden gebruikt om het afstemmingsbestand te maken en te berekenen. Het heeft echter geen kennis van bestandslogica voor factureringssysteemafstemming. U mag niet verwachten dat samenvattingsresultaten van afstemmingsbestand exact overeenkomen met het resultaat dat is opgehaald uit deze API voor dezelfde periode.

Het factureringssysteem neemt bijvoorbeeld dezelfde gebruiksgegevens en past lateheidsregels toe om te bepalen waarvoor rekening wordt gehouden in een afstemmingsbestand. Wanneer een factureringsperiode wordt gesloten, wordt al het gebruik tot het einde van de dag dat de factureringsperiode eindigt, opgenomen in het afstemmingsbestand. Laat gebruik binnen de factureringsperiode die binnen 24 uur na het einde van de factureringsperiode wordt gerapporteerd, wordt verantwoord in het volgende afstemmingsbestand. Zie Verbruiksgegevens voor een Azure-abonnement op halen voor de regels voor lateheid van de manier waarop de partner [wordt gefactureerd.](/previous-versions/azure/reference/mt219001(v=azure.100))

Dit REST API pagina's. Als de nettolading van het antwoord groter is dan één pagina, moet u de volgende koppeling volgen om de volgende pagina met gebruiksrecords op te halen.

### <a name="scenario-partner-a-has-transferred-billing-ownership-of-azure-legacy-subscription-145p-to-partner-b"></a>Scenario: Partner A heeft het eigendom van de facturering van het verouderde Azure-abonnement (145P) overgedragen aan partner B

Als een partner het eigendom van facturering van een verouderd Azure-abonnement overboekt naar een andere partner, moet de nieuwe partner de Utilization-API voor overgedragen abonnementen aanroepen om de commerce-abonnements-id (die wordt weer te geven in het Partner Center-account) te gebruiken in plaats van de Azure-rechten-id. De Azure-rechten-id wordt alleen voor partner B weergegeven wanneer deze namens (AOBO) beheerder zijn voor de klant Azure Portal. 

Om de utilization-API voor het overgedragen abonnement aan te roepen, moet de nieuwe partner de commerce-abonnements-id gebruiken.

## <a name="c"></a>C\#

De Azure-gebruiksrecords verkrijgen:

1. Haal de klant-id en abonnements-id op.

2. Roep de [**methode IAzureUtilizationCollection.Query**](/dotnet/api/microsoft.store.partnercenter.utilization.iazureutilizationcollection.query) aan om een [**ResourceCollection**](/dotnet/api/microsoft.store.partnercenter.models.resourcecollection-1) te retourneren die de gebruiksrecords bevat.

3. Een Azure-gebruiksrecord-enumerator verkrijgen om de gebruikspagina's te doorlopen. Deze stap is vereist, omdat de resourceverzameling wordt gepaginad.

- **Voorbeeld:** [Consoletest-app](console-test-app.md)
- **Project:** Partnercentrum-SDK Voorbeelden
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

Als u de Azure-gebruiksrecords wilt verkrijgen, hebt u eerst een klant-id en een abonnements-id nodig. Vervolgens roept u de **functie IAzureUtilizationCollection.query** aan om een **ResourceCollection** te retourneren die de gebruiksrecords bevat. Omdat de resourceverzameling wordt gepaginad, moet u vervolgens een Azure-gebruiksrecord-enumerator verkrijgen om de gebruikspagina's te doorlopen.

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

Als u de Azure-gebruiksrecords wilt verkrijgen, hebt u eerst een klant-id en een abonnements-id nodig. Vervolgens roept u [**get-PartnerCustomerSubscriptionUtilization aan.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscriptionUtilization.md) Deze opdracht retourneert alle records die beschikbaar zijn voor de opgegeven periode.

```powershell
# $customerId
# $subscriptionId

Get-PartnerCustomerSubscriptionUtilization -CustomerId $customerId -SubscriptionId $subscriptionId -StartDate (Get-Date).AddDays(-2).ToUniversalTime() -Granularity Hourly -ShowDetails
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode | Aanvraag-URI |
|------- | ----------- |
| **Toevoegen** | *{baseURL}*/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/utilizations/azure?start \_ time={start-time}&end \_ time={end-time}&granularity={granularity}&show \_ details={True} |

#### <a name="uri-parameters"></a>URI-parameters

Gebruik het volgende pad en de queryparameters om de gebruiksrecords op te halen.

| Naam | Type | Vereist | Beschrijving |
| ---- | ---- | -------- | ----------- |
| customer-tenant-id | tekenreeks | Ja | Een tekenreeks in GUID-indeling die de klant identificeert. |
| subscription-id | tekenreeks | Ja | Een tekenreeks in GUID-indeling die het abonnement identificeert. |
| start_tijd | tekenreeks in UTC-datum/tijd-offsetnotatie | Ja | Het begin van het tijdsbereik dat vertegenwoordigt wanneer het gebruik is gerapporteerd in het factureringssysteem. |
| end_time | tekenreeks in UTC-datum/tijd-offsetnotatie | Ja | Het einde van het tijdsbereik dat vertegenwoordigt wanneer het gebruik is gerapporteerd in het factureringssysteem. |
| Granulariteit | tekenreeks | No | Definieert de granulariteit van gebruiksaggregaties. Beschikbare opties zijn: `daily` (standaard) en `hourly` .
| show_details | booleaans | Nee | Hiermee geeft u op of de gebruiksgegevens op exemplaarniveau moeten worden op halen. De standaardwaarde is `true`. |
| grootte | getal | Nee | Hiermee geeft u het aantal aggregaties op dat wordt geretourneerd door één API-aanroep. De standaardwaarde is 1000. Het maximum is 1000. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

De volgende voorbeeldaanvraag produceert resultaten die vergelijkbaar zijn met wat het afstemmingsbestand laat zien voor de periode 7/2 - 8/1. Deze resultaten komen mogelijk niet exact overeen (zie de sectie [Azure utilization API](#azure-utilization-api) voor meer informatie).

Deze voorbeeldaanvraag retourneert gebruiksgegevens die zijn gerapporteerd in het factureringssysteem tussen 7/2 om 12:00 uur (UTC) en 8/2 om 12:00 uur (UTC).

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

Als dit lukt, retourneert deze methode een verzameling [Azure Utilization Record-resources](azure-utilization-record-resources.md) in de antwoord-body. Als de Azure-gebruiksgegevens nog niet gereed zijn in een afhankelijk systeem, retourneert deze methode een HTTP-statuscode 204 met een Retry-After header.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om de HTTP-statuscode, [het foutcodetype](error-codes.md)en aanvullende parameters te lezen.

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
