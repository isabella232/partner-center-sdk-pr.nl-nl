---
title: Microsoft Partner Network-profiel ophalen
description: Haalt een -object op dat het MPN-profiel van de partner vertegenwoordigt.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 38c12a9a9755b9838b7742d9f38c5cbd52b81210
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548852"
---
# <a name="get-microsoft-partner-network-profile"></a>Microsoft Partner Network-profiel ophalen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Haalt een -object op dat het MPN-profiel van de partner vertegenwoordigt.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

## <a name="c"></a>C\#

Als u een partnernetwerkprofiel wilt ophalen, gebruikt u de verzameling **IAggregatePartner.Profiles** en roept u de **eigenschap MpnProfile aan.** Roep ten slotte de [**methoden Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) of [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) aan.

``` csharp
// IAggregatePartner partnerOperations;

var mpnProfile = partnerOperations.Profiles.MpnProfile.Get();
```

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project**:P artnerCenterSDK.FeaturesSamples-klasse: GetMPNProfile.cs

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Als u een partnernetwerkprofiel wilt op halen, gebruikt u de functie **IAggregatePartner.getProfiles** en roept u de **functie getMpnProfile** aan. Roep ten slotte de **functie get()** aan.

```java
// IAggregatePartner partnerOperations;

MpnProfile mpnProfile = partnerOperations.getProfiles().getMpnProfile().get();
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Voer de opdracht [**Get-PartnerMpnProfile**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerMpnProfile.md) uit om een partnernetwerkprofiel op te halen.

```powershell
Get-PartnerMpnProfile
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                          |
|---------|----------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/mpn HTTP/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/mpn HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 76879323-92d1-437e-90dd-c84dbb9f7dec
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
Connection: Keep-Alive
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een **MPNProfile-object** in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
MS-RequestId: 76879323-92d1-437e-90dd-c84dbb9f7dec
Date: Mon, 21 Mar 2016 05:51:29 GMT

{
    "mpnId":"<mpnID>",
    "profileType":"MpnProfile",
    "links":{
        "self":{
            "uri":"/profiles/mpn",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "objectType":"MpnProfile"
    }
}
```
