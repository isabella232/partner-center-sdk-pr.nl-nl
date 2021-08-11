---
title: Indirecte reseller verwijderen in sandbox
description: Bevat informatie over het verwijderen van indirecte sandbox-resellers en het inschakelen van end-to-end testen met behulp van API's.
ms.date: 5/24/2021
ms.author: vijvala
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 708fedd4e34b2242aae6e6e0ac673ce77524d448dcee4a05877d37b5266e44c8
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994928"
---
# <a name="delete-indirect-reseller-in-sandbox"></a>Indirecte reseller verwijderen in sandbox

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland

In dit document ziet u hoe u indirecte Sandbox-providers verwijdert en end-to-end-tests inschakelen met behulp van API's.

> [!Important]
> In dit document worden functies beschreven die alleen zijn toegestaan in de Sandbox-omgeving voor indirecte modelervaringen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.

## <a name="sandbox-indirect-provider--delete-sandbox-indirect-reseller"></a>Indirecte sandboxprovider : indirecte sandbox-reseller verwijderen 

Deze functie is alleen beschikbaar in de sandbox en biedt indirecte sandboxproviders de mogelijkheid om indirecte sandbox-resellers te maken.

1. Vereisten voor het verwijderen van een indirecte sandbox-reseller
    1. De abonnementen voor elke klant van de indirecte sandbox-reseller opschorten
    2. Alle klanten van indirecte reseller verwijderen
2. Limiet van vijf indirecte sandbox-resellers die zijn toegestaan per indirecte sandboxprovider. Zodra de indirecte sandbox-reseller is verwijderd, wordt het quotum opnieuw ingesteld.

## <a name="delete-sandbox-indirect-reseller-through-api"></a>Indirecte sandbox-reseller verwijderen via API

### <a name="rest-request"></a>REST-aanvraag

#### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode | Aanvraag-URI                                                                             |
|------------|-------------------------------------------------------------------------------------|
| **Verwijderen** | [*{baseURL}*](partner-center-rest-urls.md)/v1 sandboxIndirectReseller/{resellerId} |

#### <a name="request-headers"></a>Aanvraagheaders

- Deze API is idempotent (deze levert geen ander resultaat op als u deze meerdere keren aanroept)
- Een aanvraag-id en correlatie-id zijn vereist
- Zie REST Partner Center headers [voor meer informatie](headers.md)

### <a name="request-example"></a>Voorbeeld van aanvraag

Verwijderen https://api.partnercenter.microsoft.com/v1/sandboxIndirectReseller/{resellerID}

```http
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

####  <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
Date: Wed, 16 Feb 2021 00:43:02 GMT
```

#### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en andere informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).

Deze methode retourneert de volgende status en foutcodes:

| HTTP-statuscode                     | Foutcode     | Beschrijving                                      |
|--------------------------------------|----------------|--------------------------------------------------|
| 401                                  | 6002           | Niet-geautoriseerd token of geen tipprovideraccount |
| 403                                  | 6003           | Sandbox-IR verwijderen is niet toegestaan                 |
| 403                                  | 6004           | Een sandbox-IR-bewerking maken die niet is toegestaan          |
| 409                                  | 1003           | Conflict tijdens maken van tenant                   |
