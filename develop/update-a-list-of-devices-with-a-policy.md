---
title: Een lijst met apparaten met een beleid bijwerken
description: Een lijst met apparaten bijwerken met een configuratiebeleid voor de opgegeven klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 35b35873eb253b0929bfc01662b0beb9b31d0c6b
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530069"
---
# <a name="update-a-list-of-devices-with-a-policy"></a>Een lijst met apparaten met een beleid bijwerken

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland

Een lijst met apparaten bijwerken met een configuratiebeleid voor de opgegeven klant.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- De beleids-id.

- De apparaat-id's van de apparaten die moeten worden bijgewerkt.

## <a name="c"></a>C\#

Als u een lijst met apparaten met het opgegeven configuratiebeleid wilt bijwerken, instantieert u eerst een [List/dotnet/api/system.collections.generic.list-1) van het type [KeyValuePair/dotnet/api/system.collections.generic.keyvaluepair-2)[**(PolicyCategory,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.policycategory)string) en voegt u het toe te passen beleid toe, zoals wordt weergegeven in het volgende codevoorbeeld. U hebt de beleids-id van het beleid nodig.

Maak vervolgens een [](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) lijst met Apparaatobjecten die moeten worden bijgewerkt met het beleid, met de apparaat-id en de lijst met het toe te passen beleid voor elk apparaat. Vervolgens maakt u een [**DevicePolicyUpdateRequest-object**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicepolicyupdaterequest) en stelt u de eigenschap [**Devices**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) in op de lijst met apparaatobjecten.

Als u de aanvraag voor het bijwerken van het apparaatbeleid wilt verwerken, roept u de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant. Haal vervolgens de eigenschap [**DevicePolicy op**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicepolicy) om een interface op te halen voor bewerkingen voor het verzamelen van apparaten van klanten. Roep ten slotte de [**updatemethode**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.icustomerdevicecollection.update) aan met het object DevicePolicyUpdateRequest om de apparaten bij te werken met het beleid.

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedConfigurationPolicyId;
string selectedDeviceId;

// Indicate the policy to apply to the list of devices.
List<KeyValuePair<PolicyCategory, string>>
    policyToBeAdded = new List<KeyValuePair<PolicyCategory, string>>
{
    new KeyValuePair<PolicyCategory, string>
        (PolicyCategory.OOBE, selectedConfigurationPolicyId)
};

// Create a list of devices to be updated with a policy.
List<Device> devices = new List<Device>
{
    new Device
    {
        Id = selectedDeviceId,
        Policies=policyToBeAdded
    }
};

// Instantiate a DevicePolicyUpdateRequest object.
DevicePolicyUpdateRequest
    devicePolicyUpdateRequest = new DevicePolicyUpdateRequest
{
    Devices = devices
};

// Process the DevicePolicyUpdateRequest.
var trackingLocation =
    partnerOperations.Customers.ById(selectedCustomerId).DevicePolicy.Update(devicePolicyUpdateRequest);
```

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class**: UpdateDevicesPolicy.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode    | Aanvraag-URI                                                                                         |
|-----------|-----------------------------------------------------------------------------------------------------|
| **Patch** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/DevicePolicyUpdates HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende padparameters bij het maken van de aanvraag.

| Naam        | Type   | Vereist | Beschrijving                                           |
|-------------|--------|----------|-------------------------------------------------------|
| customer-id | tekenreeks | Ja      | Een tekenreeks in GUID-indeling die de klant identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

De aanvraag moet een [DevicePolicyUpdateRequest-resource](device-deployment-resources.md#devicepolicyupdaterequest) bevatten.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/DevicePolicyUpdates HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1b658428-5afa-46d4-af86-c9c6af5634e2
MS-CorrelationId: 49b1e7b2-82e7-4403-b63b-8765269b448d
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 363
Expect: 100-continue
Connection: Keep-Alive

{
    "Devices": [{
            "Id": "9993-8627-3608-6844-6369-4361-72",
            "SerialNumber": null,
            "ProductKey": null,
            "HardwareHash": null,
            "Policies": [{
                    "Key": "o_o_b_e",
                    "Value": "15a04610-9229-4e80-94e0-0e826a09c9e2"
                }
            ],
            "CreatedBy": null,
            "UploadedDate": "0001-01-01T00:00:00",
            "AllowedOperations": null,
            "Attributes": {
                "ObjectType": "Device"
            }
        }
    ],
    "Attributes": {
        "ObjectType": "DevicePolicyUpdateRequest"
    }
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat het antwoord een **Location-header** met een URI die kan worden gebruikt om de status van dit batchproces op te halen. Sla deze URI op voor gebruik met andere gerelateerde REST API's.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/batchJobStatus/a15f3996-620a-4404-9f1f-4c2de78de0de
MS-CorrelationId: 49b1e7b2-82e7-4403-b63b-8765269b448d
MS-RequestId: 1b658428-5afa-46d4-af86-c9c6af5634e2
MS-CV: rCXyd8Z/lUSxUd0P.0
MS-ServerId: 020021921
Date: Thu, 28 Sep 2017 21:33:05 GMT
```
