---
title: Een configuratiebeleid bijwerken voor de opgegeven klant
description: Het opgegeven configuratiebeleid voor de opgegeven klant bijwerken.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 5e008f41a44f2b7cf3ddfd705505175c69bbad38
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530226"
---
# <a name="update-a-configuration-policy-for-the-specified-customer"></a>Een configuratiebeleid bijwerken voor de opgegeven klant

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland

Het opgegeven configuratiebeleid voor de opgegeven klant bijwerken.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- De beleids-id.

## <a name="c"></a>C\#

Als u een bestaand configuratiebeleid voor de opgegeven klant wilt bijwerken, maakt u een nieuw [**ConfigurationPolicy-object,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) zoals wordt weergegeven in het volgende codefragment. De waarden in dit nieuwe object vervangen de bijbehorende waarden in het bestaande object. Roep vervolgens de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant. Roep vervolgens de [**methode ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) aan met de beleids-id om een interface op te halen voor configuratiebeleidsbewerkingen voor het opgegeven beleid. Roep ten slotte de [**methode Patch**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patch) of [**PatchAsync aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patchasync) om het configuratiebeleid bij te werken.

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

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class**: UpdateConfigurationPolicy.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende padparameters bij het maken van de aanvraag.

| Naam        | Type   | Vereist | Beschrijving                                                   |
|-------------|--------|----------|---------------------------------------------------------------|
| customer-id | tekenreeks | Ja      | Een tekenreeks in GUID-indeling die de klant identificeert.         |
| policy-id   | tekenreeks | Ja      | Een tekenreeks met GUID-indeling die het bij te werken beleid identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

De aanvraag body moet een object bevatten dat de beleidsgegevens verstrekt.

| Naam            | Type             | Vereist | Bijgewerkt | Beschrijving                                                                                                                                              |
|-----------------|------------------|----------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| id              | tekenreeks           | Ja      | Nee        | De tekenreeks in GUID-indeling die het beleid identificeert.                                                                                                    |
| naam            | tekenreeks           | Ja      | Ja       | De gebruiksvriendelijke naam van het beleid.                                                                                                                         |
| category        | tekenreeks           | Ja      | Nee        | De beleidscategorie.                                                                                                                                     |
| beschrijving     | tekenreeks           | Nee       | Ja       | De beschrijving van het beleid.                                                                                                                                  |
| toegewezen apparaten | getal           | Nee       | Nee        | Het aantal apparaten.                                                                                                                                   |
| policySettings  | tekenreeksmatrix | Ja      | Ja       | De beleidsinstellingen: "none","remove \_ oem \_ preinstalls","oobe \_ user not local \_ \_ \_ admin","skip \_ express \_ settings","skip \_ oem \_ registration,"skip \_ eula". |

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

Als dit lukt, bevat de antwoord-body de [ConfigurationPolicy-resource](device-deployment-resources.md#configurationpolicy) voor het nieuwe beleid.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

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
