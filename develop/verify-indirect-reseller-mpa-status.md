---
title: De handtekeningstatus van een indirecte reseller Microsoft Partner-overeenkomst controleren
description: U kunt de AgreementStatus-API gebruiken om te controleren of een indirecte reseller de Microsoft Partner-overeenkomst.
ms.date: 07/24/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f83acc61624a72354c390905b1250bc021dd39aa
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529831"
---
# <a name="verify-an-indirect-resellers-microsoft-partner-agreement-signing-status"></a>De handtekeningstatus van een indirecte reseller Microsoft Partner-overeenkomst controleren

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud for US Government

U kunt controleren of een indirecte reseller de Microsoft Partner-overeenkomst heeft ondertekend met behulp van de Microsoft Partner Network-id (PGA/PLA) of de tenant-id van Cloud Solution Provider (CSP) (Microsoft ID). U kunt een van deze id's gebruiken om de status van Microsoft Partner-overeenkomst te controleren met behulp van de **AgreementStatus-API.**

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- De MPN-id (PGA/PLA) of de CSP-tenant-id (Microsoft-id) van de indirecte reseller. *U moet een van deze twee id's gebruiken.*

## <a name="c"></a>C\#

De handtekeningstatus van Microsoft Partner-overeenkomst indirecte reseller op te halen:

1. Gebruik de **verzameling IAggregatePartner.Compliance** om de eigenschap **AgreementSignatureStatus aan te** roepen.

2. Roep de [**methode Get()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.get) of [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.getasync) aan.

``` csharp
// IAggregatePartner partnerOperations;

var agreementSignatureStatusByMpnId = partnerOperations.Compliance.AgreementSignatureStatus.Get(mpnId:"Enter MPN Id (PGA/PLA)");

var agreementSignatureStatusByTenantId = partnerOperations.Compliance.AgreementSignatureStatus.Get(tenantId: "Enter Tenant Id");
```

- Voorbeeld: **[Consoletest-app](console-test-app.md)**
- Project: **PartnerCenterSDK.FeaturesSamples**
- Klasse: **GetAgreementSignatureStatus.cs**

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode | Aanvraag-URI |
| ------ | ----------- |
| **Toevoegen** | *[{baseURL}](partner-center-rest-urls.md)*/v1/compliance/{ProgramName}/agreementstatus?mpnId={MpnId}&tenantId={TenantId} |

#### <a name="uri-parameters"></a>URI-parameters

U moet een van de volgende twee queryparameters opgeven om de partner te identificeren. Als u geen van deze twee queryparameters opvraagt, ontvangt u de **foutmelding 400 (Foute** aanvraag).

| Naam | Type | Vereist | Beschrijving |
| ---- | ---- | -------- | ----------- |
| **MpnId** | int | Nee | Een Microsoft Partner Network-id (PGA/PLA) die de indirecte reseller identificeert. |
| **Tenant-ID** | GUID | Nee | Een Microsoft-id die het CSP-account van de indirecte reseller identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center REST.](headers.md)

### <a name="request-examples"></a>Voorbeelden van aanvragen

#### <a name="request-using-mpn-id-pgapla"></a>Aanvraag met MPN-id (PGA/PLA)

Met de volgende voorbeeldaanvraag wordt de handtekeningstatus van de indirecte reseller Microsoft Partner-overeenkomst met behulp van de id van Microsoft Partner Network indirecte reseller.

```http
GET https://api.partnercenter.microsoft.com/v1/compliance/csp/agreementstatus?mpnid=1234567 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

#### <a name="request-using-csp-tenant-id"></a>Aanvragen met behulp van CSP-tenant-id

Met de volgende voorbeeldaanvraag wordt de ondertekeningsstatus van de indirecte reseller Microsoft Partner-overeenkomst met behulp van de CSP-tenant-id (Microsoft-id) van de indirecte reseller.

```http
GET https://api.partnercenter.microsoft.com/v1/compliance/csp/agreementstatus?tenantId=a2898e3a-06ca-454e-a0d0-c73b0ee36bba HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>REST-antwoord

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie voor de volledige lijst Partner Center [REST-fout](error-codes.md).

### <a name="response-example-success"></a>Voorbeeld van antwoord (geslaagd)

In het volgende voorbeeld wordt met succes een antwoord gegeven of de indirecte reseller de Microsoft Partner-overeenkomst.

```http
HTTP/1.1 200 OK
Content-Length: 29
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: jn3r+1wpE06nCt/0.0
MS-ServerId: 0000005B
Date: Tue, 15 Oct 2019 12:44:34 GMT
Connection: close
{
    "isAgreementSigned": true
}
```

### <a name="response-examples-failure"></a>Antwoordvoorbeelden (fout)

Mogelijk ontvangt u antwoorden die vergelijkbaar zijn met de volgende voorbeelden wanneer de ondertekeningsstatus van de indirecte reseller-Microsoft Partner-overeenkomst niet kan worden geretourneerd.

#### <a name="non-guid-formatted-csp-tenant-id"></a>Tenant-id zonder GUID-indeling

Het volgende voorbeeld van een antwoord wordt geretourneerd wanneer de CSP-tenant-id die u aan de API hebt doorgegeven, geen GUID is.

```http
HTTP/1.1 400 Bad Request
Content-Length: 105
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: rbuZl5lbAkyq8WGK.0
MS-ServerId: 00000055
Date: Wed, 16 Oct 2019 08:55:23 GMT
Connection: close
{
    "code": 2000,
    "description": "Tenant Id must be a GUID.",
    "data": [],
    "source": "PartnerApiServiceControllers"
}
```

#### <a name="non-numeric-mpn-id"></a>Niet-numerieke MPN-id

Het volgende voorbeeld van een antwoord wordt geretourneerd wanneer de MPN-id (PGA/PLA) die u aan de API hebt doorgegeven, niet-numeriek is.

```http
HTTP/1.1 400 Bad Request
Content-Length: 103
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: cP5JiS4sv0GJxlJ9.0
MS-ServerId: 0000005B
Date: Wed, 16 Oct 2019 08:58:45 GMT
Connection: close
{
    "code": 2000,
    "description": "MPN Id must be numeric.",
    "data": [],
    "source": "PartnerApiServiceControllers"
}
```

#### <a name="no-mpn-id-or-csp-tenant-id"></a>Geen MPN-id of CSP-tenant-id

Het volgende voorbeeld van een antwoord wordt geretourneerd wanneer u geen MPN-id (PGA/PLA) of CSP-tenant-id aan de API hebt doorgegeven. U moet een van de twee id-typen doorgeven aan de API.

```http
HTTP/1.1 400 Bad Request
Content-Length: 114
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: hEV736v4qk6joDMR.0
MS-ServerId: 00000055
Date: Wed, 16 Oct 2019 09:00:30 GMT
Connection: close
{
    "code": 2001,
    "description": "Both MPN Id and Tenant Id cannot be empty.",
    "data": [],
    "source": "ComplianceController"
}
```

#### <a name="both-mpn-id-and-csp-tenant-id-passed"></a>Zowel MPN-id als CSP-tenant-id doorgegeven

Het volgende voorbeeld van een antwoord wordt geretourneerd wanneer u zowel de MPN-id (PGA/PLA) als de CSP-tenant-id door geeft aan de API. U hoeft slechts *één van de* twee id-typen door te geven aan de API.

```http
HTTP/1.1 400 Bad Request
Content-Length: 119
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: WTsLWK5UlUW9sZjH.0
MS-ServerId: 0000005B
Date: Wed, 16 Oct 2019 09:02:30 GMT
Connection: close
{
    "code": 2000,
    "description": "Both MPN Id and Tenant Id should not be passed.",
    "data": [],
    "source": "ComplianceController"
}
```

#### <a name="csp-indirect-reseller-mpn-id-pgapla-is-either-invalid-or-not-migrated-from-partner-membership-center-to-partner-center"></a>CSP Indirect Reseller MPN-id (PGA/PLA) is ongeldig of niet gemigreerd van Partner Membership Center naar Partner Center

Het volgende voorbeeld antwoord wordt geretourneerd wanneer indirecte reseller MPN ID (PGA/PLA) doorgegeven ongeldig is of niet wordt gemigreerd van Partner Membership Center naar Partner Center. [Meer informatie](https://partner.microsoft.com/resources/detail/migrate-pmc-pc-mpa-guide-pptx)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2200,
    "description": "MPN Id 123456 is either invalid or not yet migrated to Partner Center. Please advise your reseller to migrate the reseller MPN ID to Partner Center to continue with this order.",
    "data": [
        "https://partner.microsoft.com/resources/detail/migrate-pmc-pc-mpa-guide-pptx"
    ],
    "source": "PartnerFD"
}
```

#### <a name="csp-indirect-provider-region-and-csp-indirect-reseller-region-does-not-match"></a>CSP Indirect Provider regio en CSP Indirect Reseller komen niet overeen

Het volgende voorbeeld antwoord wordt geretourneerd wanneer de regio van de indirecte reseller MPN ID (PGA/PLA) komt niet overeen met de regio van de indirecte provider. [Meer informatie over](/partner-center/mpa-indirect-provider-faq) CSP-regio's.

```http
HTTP/1.1 400 Bad Request
Content-Length: 119
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: WTsLWK5UlUW9sZjH.0
MS-ServerId: 0000005B
Date: Wed, 16 Oct 2019 09:02:30 GMT
Connection: close
{
    "code": 2201,
    "description": "The CSP region of the MPN ID 1234567 doesn’t match the CSP region from where you are placing the order. Provide the MPN ID for the CSP region where you are placing the order.",
    "data": [
        "https://docs.microsoft.com/partner-center/mpa-indirect-provider-faq" 
    ],
    "source": "PartnerFD"
}
```

#### <a name="csp-indirect-reseller-account-exists-in-partner-center-but-hasnt-signed-the-mpa"></a>CSP Indirect Reseller account bestaat in Partner Center maar heeft de MPA niet ondertekend

Het volgende voorbeeld wordt geretourneerd wanneer CSP Indirect Reseller account in Partner Center MPA niet heeft ondertekend. [Meer informatie](/partner-center/mpa-indirect-provider-faq)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2203,
    "description": "MPN Id 123456 has not signed Microsoft Partner Agreement (MPA) for the CSP region where the order is being placed. Please advise your reseller to sign MPA to continue with the order.",
    "data": [
        "https://docs.microsoft.com/partner-center/mpa-indirect-provider-faq"
    ],
    "source": "PartnerFD"
}
```

#### <a name="no-csp-indirect-reseller-account-is-associated-with-the-given-mpn-id"></a>Er CSP Indirect Reseller account gekoppeld aan de opgegeven MPN-id

Het volgende voorbeeld wordt geretourneerd wanneer Partner Center de MPN-id (PGA/PLA) kan herkennen die is doorgegeven in de aanvraag, maar er geen CSP-inschrijving is gekoppeld aan de opgegeven MPN-id (PGA/PLA). [Meer informatie](/partner-center/mpa-indirect-provider-faq)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2204,
    "description": "MPN Id 123456 is not associated with a CSP Indirect Reseller account in Partner Center. Please advise your reseller to enroll into the CSP program as an indirect reseller in Partner Center.",
    "data": [
        "https://docs.microsoft.com/partner-center/mpa-indirect-provider-faq"
    ],
    "source": "PartnerFD"
}
```

#### <a name="invalid-tenant-id"></a>Ongeldige tenant-id

Het volgende voorbeeld wordt geretourneerd wanneer Partner Center geen account vindt dat is gekoppeld aan de tenant-id die in de aanvraag is doorgegeven.

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2205,
    "description": "Partner Center doesn't find any account associated to the Tenant ID 12345678-ACBD-1234-ABCD-123456789ABC",
    "data": [],
    "source": "PartnerFD"
}
```

#### <a name="no-mpa-found-with-the-given-tenant-id"></a>Er is geen MPA gevonden met de opgegeven tenant-id

Het volgende voorbeeld wordt geretourneerd wanneer Partner Center MPA-handtekening met de opgegeven tenant-id niet kan vinden. [Meer informatie](/partner-center/mpa-indirect-provider-faq)

```http
HTTP/1.1 400 Bad Request
Content-Length: 321
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9240230a-413f-4880-acbd-96d59a165474
MS-RequestId: 92caacb1-8c9e-49af-8f85-83f271c85056
MS-CV: V8eVMXvaBE6LHyq6.0
MS-ServerId: 0000005B
Date: Fri, 24 Jul 2020 11:56:46 GMT
Connection: close
{
    "code": 2206,
    "description": "Parnter Center Account associated to Tenant Id 12345678-ACBD-1234-ABCD-123456789ABC hasn't signed the agreement",
    "data": [
        "https://docs.microsoft.com/partner-center/mpa-indirect-provider-faq"
    ],
    "source": "PartnerFD"
}
```