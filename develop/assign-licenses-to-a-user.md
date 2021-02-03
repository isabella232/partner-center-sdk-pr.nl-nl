---
title: Licenties toewijzen aan een gebruiker
description: Meer informatie over het toewijzen van licenties aan een klant gebruiker via partner Center Api's, zoals het gebruik van C- \# of rest-api's.
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6eb0b953b9157e48074415bb3207e2946cfb2ab4
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2020
ms.locfileid: "97767597"
---
# <a name="assign-licenses-to-a-user-via-partner-center-apis"></a>Licenties toewijzen aan een gebruiker via partner Center-Api's

**Van toepassing op:**

- Partnercentrum

Licenties toewijzen aan een klant gebruiker.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- De gebruikers-id van de klant. Deze ID geeft aan aan welke gebruiker de licentie moet worden toegewezen.

- Een product-SKU-id waarmee het product voor de licentie wordt geïdentificeerd.

## <a name="assigning-licenses-through-code"></a>Licenties toewijzen via code

Wanneer u licenties aan een gebruiker toewijst, moet u kiezen uit de verzameling van geabonneerde Sku's van de klant. Nadat u de producten hebt geïdentificeerd die u wilt toewijzen, moet u de product-SKU-ID voor elk product verkrijgen om de toewijzingen te kunnen maken. Elk [**SubscribedSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku) -exemplaar bevat een [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.subscribedsku.productsku) -eigenschap van waaruit u kunt verwijzen naar het [**ProductSku**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku) -object en de [**id**](/dotnet/api/microsoft.store.partnercenter.models.licenses.productsku.id)ophalen.

Een aanvraag voor licentie toewijzing moet licenties van één licentie groep bevatten. U kunt bijvoorbeeld geen licenties toewijzen van [**Group1**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid) en **group2** in dezelfde aanvraag. Een poging om licenties toe te wijzen vanuit meer dan één groep in één aanvraag, mislukt met de juiste fout. Zie [een lijst met beschik bare licenties per licentie groep ophalen](get-a-list-of-available-licenses-by-license-group.md)voor meer informatie over de licenties die beschikbaar zijn per licentie groep.

Hier volgen de stappen voor het toewijzen van licenties via code:

1. Een [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) -object instantiëren. U gebruikt dit object om op te geven welke product-SKU en service plannen u wilt toewijzen.

    ``` csharp
    LicenseAssignment license = new LicenseAssignment();
    ```

2. Vul de object eigenschappen in zoals hieronder wordt weer gegeven. In deze code wordt ervan uitgegaan dat u de product-SKU-ID al hebt, en dat alle beschik bare service plannen worden toegewezen (dat wil zeggen, geen wordt uitgesloten).

    ```csharp
    license.SkuId = selectedProductSkuId;
    license.ExcludedPlans = null;
    ```

3. Als u de product-SKU-ID niet hebt, moet u de verzameling geabonneerde Sku's ophalen en de product-SKU-ID ophalen. Hier volgt een voor beeld als u de naam van de product-SKU kent.

    ```csharp
    var customerSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get();
    var sku = customerSubscribedSkus.Items.Where(n => n.ProductSku.Name == "Office 365 Enterprise E3").First();
    license.SkuId = sku.ProductSku.Id;
    license.ExcludedPlans = null;
    ```

4. Vervolgens maakt u een nieuwe lijst van het type [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment)en voegt u het licentie object toe. U kunt meer dan één licentie toewijzen door elk afzonderlijk toe te voegen aan de lijst. De licenties die in deze lijst zijn opgenomen, moeten afkomstig zijn uit dezelfde licentie groep.

    ```csharp
    List<LicenseAssignment> licenseList = new List<LicenseAssignment>();
    licenseList.Add(license);
    ```

5. Maak een [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) -exemplaar en wijs de lijst met licentie toewijzingen toe aan de eigenschap [**LicensesToAssign**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign) .

    ```csharp
    LicenseUpdate updateLicense = new LicenseUpdate();
    updateLicense.LicensesToAssign = licenseList;
    ```

6. Roep de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) aan en geef het object licentie update door, zoals hieronder wordt weer gegeven, om de licenties toe te wijzen.

    ```csharp
    var assignLicense = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).LicenseUpdates.Create(updateLicense);
    ```

## <a name="c"></a>C\#

Als u een licentie wilt toewijzen aan een klant gebruiker, maakt u eerst een [**LicenseAssignment**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment) -object en vult u de eigenschappen [**skuId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.skuid) en [**ExcludedPlans**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseassignment.excludedplans) in. U gebruikt dit object om de product-SKU op te geven die moet worden toegewezen en service plannen die moeten worden uitgesloten. Vervolgens maakt u een nieuwe lijst van het type **LicenseAssignment** en voegt u het licentie object toe aan de lijst. Maak vervolgens een [**LicenseUpdate**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate) -exemplaar en wijs de lijst met licentie toewijzingen toe aan de eigenschap [**LicensesToAssign**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licenseupdate.licensestoassign) .

Gebruik vervolgens de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren en de [**gebruikers. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) -methode met de gebruikers-id om de gebruiker te identificeren. Haal vervolgens een interface op voor het bijwerken van klant licenties voor gebruikers via de eigenschap [**LicenseUpdates**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.licenseupdates) .

Roep tot slot de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruserlicenseupdates.createasync) aan en geef het licentie-update object door om de licentie toe te wijzen.

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

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: CustomerUserAssignLicenses.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode   | Aanvraag-URI                                                                                                    |
|----------|----------------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/users/{user-id}/licenseupdates http/1.1 |

#### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende para meters om de klant en gebruiker te identificeren.

| Naam        | Type   | Vereist | Beschrijving                                       |
|-------------|--------|----------|---------------------------------------------------|
| klant-id | tekenreeks | Yes      | Een ID met de GUID-indeling waarmee de klant wordt geïdentificeerd. |
| user-id     | tekenreeks | Yes      | Een ID met de GUID-indeling waarmee de gebruiker wordt geïdentificeerd.     |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Neem een [LicenseUpdate](license-resources.md#licenseupdate) -resource op in de aanvraag tekst die aangeeft welke licenties moeten worden toegewezen.

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

Als dit lukt, wordt een HTTP-antwoord status code 201 geretourneerd en de antwoord tekst bevat een [LicenseUpdate](license-resources.md#licenseupdate) -resource met de licentie gegevens.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example-success"></a>Voor beeld van antwoord (geslaagd)

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

### <a name="response-example-license-isnt-available"></a>Antwoord voorbeeld (licentie is niet beschikbaar)

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
