---
title: Een configuratiebeleid bijwerken voor de opgegeven klant
description: Het opgegeven configuratie beleid voor de opgegeven klant bijwerken.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 42c57a92020723415b4621e9f9d7c5c3278bfb77
ms.sourcegitcommit: 970031473b2e8cd3d08c6c097949c057a51df3ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505336"
---
# <a name="update-a-configuration-policy-for-the-specified-customer"></a>Een configuratiebeleid bijwerken voor de opgegeven klant

**Van toepassing op**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland

Het opgegeven configuratie beleid voor de opgegeven klant bijwerken.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- De beleids-id.

## <a name="c"></a>C\#

Als u een bestaand configuratie beleid voor de opgegeven klant wilt bijwerken, moet u een nieuw [**ConfigurationPolicy**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) -object instantiëren, zoals wordt weer gegeven in het volgende code fragment. De waarden in dit nieuwe object vervangen de overeenkomende waarden in het bestaande object. Vervolgens roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant. Vervolgens roept u de methode [**ConfigurationPolicies. ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) aan met de beleids-id om een interface op te halen voor configuratie beleids bewerkingen voor het opgegeven beleid. Roep ten slotte de [**patch**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patch) -of [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patchasync) -methode aan om het configuratie beleid bij te werken.

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedConfigurationPolicyId;

ConfigurationPolicy configPolicyToBeUpdated = new ConfigurationPolicy()
{
    Name= "Test Config Policy",
    Id = selectedConfigurationPolicyId,
    PolicySettings = new List<PolicySettingsType>() {
        PolicySettingsType.OobeUserNotLocalAdmin,
        PolicySettingsType.RemoveOemPreinstalls }
};

ConfigurationPolicy updatedConfigurationPolicy =
    partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.ById(selectedConfigurationPolicyId).Patch(configPolicyToBeUpdated);
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: UpdateConfigurationPolicy.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/policies/{Policy-id} http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende Path-para meters bij het maken van de aanvraag.

| Naam        | Type   | Vereist | Beschrijving                                                   |
|-------------|--------|----------|---------------------------------------------------------------|
| klant-id | tekenreeks | Ja      | Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.         |
| beleid-id   | tekenreeks | Ja      | Een teken reeks met een GUID-indeling die het beleid identificeert dat moet worden bijgewerkt. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

De aanvraag tekst moet een object bevatten dat de beleids gegevens levert.

| Naam            | Type             | Vereist | Worden bijgewerkt | Beschrijving                                                                                                                                              |
|-----------------|------------------|----------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| id              | tekenreeks           | Ja      | Nee        | De teken reeks met de GUID-indeling waarmee het beleid wordt geïdentificeerd.                                                                                                    |
| naam            | tekenreeks           | Ja      | Ja       | De beschrijvende naam van het beleid.                                                                                                                         |
| category        | tekenreeks           | Ja      | Nee        | De beleids categorie.                                                                                                                                     |
| beschrijving     | tekenreeks           | Nee       | Ja       | De beschrijving van het beleid.                                                                                                                                  |
| devicesAssigned | getal           | Nee       | Nee        | Het aantal apparaten.                                                                                                                                   |
| policySettings  | tekenreeksmatrix | Ja      | Ja       | De beleids instellingen: ' geen ', ' \_ OEM- \_ voor installatie verwijderen ', ' OOBE- \_ gebruiker \_ niet \_ lokale \_ beheerder ', ' Skip \_ Express Settings ', ' overs laan van \_ \_ OEM \_ -registratie, ' EULA overs Laan \_ '. |

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/policies/56edf752-ee77-4fd8-b7f5-df1f74a3a9ac HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Content-Length: 256
Content-Type: application/json
Host: api.partnercenter.microsoft.com

{
    "id": "56edf752-ee77-4fd8-b7f5-df1f74a3a9ac",
    "name": "Windows test policy",
    "category": "o_o_b_e",
    "description": "Test policy creation from API",
    "devicesAssigned": 0,
    "policySettings": ["skip_express_settings"]
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord tekst de [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) -resource voor het nieuwe beleid.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 421
Content-Type: application/json; charset=utf-8
MS-CorrelationId: f9fd5973-6ad8-4585-aadc-f2b0443fe27b
MS-RequestId: cb1fa1f3-1381-45d9-99c5-511e5d3efa7c
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:10:29 GMT

{
    "id": "56edf752-ee77-4fd8-b7f5-df1f74a3a9ac",
    "name": "Windows test policy",
    "category": "o_o_b_e",
    "description": "Test policy creation from API",
    "devicesAssigned": 0,
    "policySettings": ["skip_express_settings"],
    "createdDate": "2017-01-01T00:00:00",
    "lastModifiedDate": "2017-07-25T18:10:15",
    "attributes": {
        "objectType": "ConfigurationPolicy"
    }
}
```
