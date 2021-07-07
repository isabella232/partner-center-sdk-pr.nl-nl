---
title: Licenties toewijzen aan een gebruiker
description: Meer informatie over het toewijzen van licenties aan een klantgebruiker via Partner Center API's, zoals het gebruik van C- of \# REST API's.
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 88ce0f185b0b043c4a7862b7f9808fb8805d40b9
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974366"
---
# <a name="assign-licenses-to-a-user-via-partner-center-apis"></a>Licenties toewijzen aan een gebruiker via Partner Center API's

Licenties toewijzen aan een klantgebruiker.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een gebruikers-id van de klant. Deze id identificeert de gebruiker aan wie de licentie moet worden toegewezen.

- Een product-SKU-id die het product voor de licentie identificeert.

## <a name="assigning-licenses-through-code"></a>Licenties toewijzen via code

Wanneer u licenties toewijst aan een gebruiker, moet u kiezen uit de verzameling geabonneerde SKU's van de klant. Nadat u de producten hebt geïdentificeerd die u wilt toewijzen, moet u de product-SKU-id voor elk product verkrijgen om de toewijzingen te kunnen maken. Elk [**SubscribedSku-exemplaar**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku) bevat een [**eigenschap ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku.productsku) van waaruit u kunt verwijzen naar het [**ProductSku-object**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku) en de id [**kunt op halen.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku.id)

Een licentietoewijzingsaanvraag moet licenties uit één licentiegroep bevatten. U kunt bijvoorbeeld geen licenties van [**Group1**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid) en **Group2** toewijzen in dezelfde aanvraag. Een poging om licenties van meer dan één groep in één aanvraag toe te wijzen, mislukt met een passende fout. Zie Get [a list of available licenses by license group (Een](get-a-list-of-available-licenses-by-license-group.md)lijst met beschikbare licenties per licentiegroep verkrijgen) voor meer informatie over welke licenties beschikbaar zijn per licentiegroep.

Hier volgen de stappen voor het toewijzen van licenties via code:

1. Instantieer een [**LicenseAssignment-object.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) U gebruikt dit object om de product-SKU en serviceplannen op te geven die u wilt toewijzen.

    ``` csharp
    LicenseAssignment license = new LicenseAssignment();
    ```

2. Vul de objecteigenschappen in zoals hieronder wordt weergegeven. In deze code wordt ervan uit gegaan dat u al de product-SKU-id hebt en dat alle beschikbare serviceplannen worden toegewezen (dat wil zeggen, geen van de abonnementen wordt uitgesloten).

    ```csharp
    license.SkuId = selectedProductSkuId;
    license.ExcludedPlans = null;
    ```

3. Als u niet de product-SKU-id hebt, moet u de verzameling geabonneerde SKU's ophalen en de product-SKU-id ophalen van een van deze SKU's. Hier ziet u een voorbeeld als u de naam van de product-SKU kent.

    ```csharp
    var customerSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get();
    var sku = customerSubscribedSkus.Items.Where(n => n.ProductSku.Name == "Office 365 Enterprise E3").First();
    license.SkuId = sku.ProductSku.Id;
    license.ExcludedPlans = null;
    ```

4. Vervolgens maakt u een nieuwe lijst van het type [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment)en voegt u het licentieobject toe. U kunt meer dan één licentie toewijzen door elke licentie afzonderlijk aan de lijst toe te voegen. De licenties die in deze lijst zijn opgenomen, moeten van dezelfde licentiegroep zijn.

    ```csharp
    List<LicenseAssignment> licenseList = new List<LicenseAssignment>();
    licenseList.Add(license);
    ```

5. Maak een [**LicenseUpdate-exemplaar**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) en wijs de lijst met licentietoewijzingen toe aan [**de eigenschap LicensesToAssign.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign)

    ```csharp
    LicenseUpdate updateLicense = new LicenseUpdate();
    updateLicense.LicensesToAssign = licenseList;
    ```

6. Roep de [**methode Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) aan en geef het licentie-updateobject door zoals hieronder wordt weergegeven om de licenties toe te wijzen.

    ```csharp
    var assignLicense = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).LicenseUpdates.Create(updateLicense);
    ```

## <a name="c"></a>C\#

Als u een licentie wilt toewijzen aan een klantgebruiker, maakt u eerst een [**LicenseAssignment-object**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) en vult u de [**eigenschappen Skuid**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.skuid) en [**ExcludedPlans**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.excludedplans) in. U gebruikt dit object om de product-SKU op te geven die moet worden toegewezen en om serviceplannen uit te sluiten. Vervolgens maakt u een nieuwe lijst van het type **LicenseAssignment** en voegt u het licentieobject toe aan de lijst. Maak vervolgens een [**LicenseUpdate-exemplaar**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) en wijs de lijst met licentietoewijzingen toe aan [**de eigenschap LicensesToAssign.**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign)

Gebruik vervolgens de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren en de [**methode Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) met de gebruikers-id om de gebruiker te identificeren. Haal vervolgens een interface op voor updatebewerkingen voor gebruikerslicenties van de klant [**via de eigenschap LicenseUpdates.**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenseupdates)

Roep ten slotte de [**methode Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) aan en geef het licentie-updateobject door om de licentie toe te wijzen.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerUserId;
// string selectedCustomerId;
// string selectedProductSkuId;

// Instantiate and populate a LicenseAssignment object.
LicenseAssignment license = new LicenseAssignment();
license.SkuId = selectedProductSkuId;
license.ExcludedPlans = null;

// Instantiate a list of licenses to assign and add the license to it.
List<LicenseAssignment> licenseList = new List<LicenseAssignment>();
licenseList.Add(license);

// Instantiate a LicenseUpdate object and add the list of licenses to assign.
LicenseUpdate updateLicense = new LicenseUpdate();
updateLicense.LicensesToAssign = licenseList;

// Update the user licenses.
var assignLicense = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).LicenseUpdates.Create(updateLicense);
```

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class**: CustomerUserAssignLicenses.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                    |
|----------|----------------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users/{user-id}/licenseupdates HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende padparameters om de klant en gebruiker te identificeren.

| Naam        | Type   | Vereist | Beschrijving                                       |
|-------------|--------|----------|---------------------------------------------------|
| customer-id | tekenreeks | Ja      | Een id met GUID-indeling die de klant identificeert. |
| user-id     | tekenreeks | Ja      | Een id met GUID-indeling die de gebruiker identificeert.     |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Neem een [LicenseUpdate-resource](license-resources.md#licenseupdate) op in de aanvraag body waarin de licenties worden opgegeven die moeten worden toegewezen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/users/554526aa-cf5e-46fa-95df-98dbc55d8a1e/licenseupdates HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a37d3009-665d-4e12-b76e-1aa10cf80140
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 183
Expect: 100-continue

{
    "LicensesToAssign": [{
            "ExcludedPlans": null,
            "SkuId": "f8a1db68-be16-40ed-86d5-cb42ce701560"
        }
    ],
    "LicensesToRemove": null,
    "LicenseWarnings": null,
    "Attributes": {
        "ObjectType": "LicenseUpdate"
    }
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, wordt de HTTP-antwoordstatuscode 201 geretourneerd en bevat de antwoord-body een [LicenseUpdate-resource](license-resources.md#licenseupdate) met de licentiegegevens.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example-success"></a>Voorbeeld van antwoord (geslaagd)

```http
HTTP/1.1 201 Created
Content-Length: 139
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
MS-RequestId: a37d3009-665d-4e12-b76e-1aa10cf80140
MS-CV: 5AnzcZQrvUqCq3kd.0
MS-ServerId: 030020525
Date: Thu, 20 Apr 2017 21:50:39 GMT

{
    "licensesToAssign": [{
            "skuId": "f8a1db68-be16-40ed-86d5-cb42ce701560"
        }
    ],
    "licenseWarnings": [],
    "attributes": {
        "objectType": "LicenseUpdate"
    }
}
```

### <a name="response-example-license-isnt-available"></a>Voorbeeld van antwoord (licentie is niet beschikbaar)

```http
HTTP/1.1 400 Bad Request
Content-Length: 341
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c73c9570-c352-459e-98a3-dafe4bd8c821
MS-RequestId: f4f3b748-8b22-4d07-a5a1-dceb32824192
MS-CV: 5npA0K22CUmWPOzB.0
MS-ServerId: 102030524
Date: Thu, 20 Apr 2017 22:12:36 GMT

{
    "code": 60012,
    "description": "We&#39;re sorry, it looks like you've run out of licenses. Buy more licenses, and then try again.",
    "data": ["LicenseQuotaExceededException : Subscription with Account 0c39d6d5-c70d-4c55-bc02-f620844f3fd1 and SKU f8a1db68-be16-40ed-86d5-cb42ce701560 does not have any available licenses left."],
    "source": "PartnerFD"
}
```
