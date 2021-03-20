---
title: De ondertekening status van de micro soft partner overeenkomst van een indirecte wederverkoper verifiëren
description: U kunt de AgreementStatus-API gebruiken om te controleren of een indirecte wederverkoper de micro soft-partner overeenkomst heeft ondertekend.
ms.date: 07/24/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: fa9480424eccc933bc9c28c3879a195fbd5f2bb1
ms.sourcegitcommit: 717e483a6eec23607b4e31ddfaa3e2691f3043e6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104711889"
---
# <a name="verify-an-indirect-resellers-microsoft-partner-agreement-signing-status"></a>De ondertekening status van de micro soft partner overeenkomst van een indirecte wederverkoper verifiëren

**Van toepassing op:**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud for US Government

U kunt controleren of een indirecte wederverkoper de micro soft-partner overeenkomst heeft ondertekend met behulp van hun Microsoft Partner Network (MPN)-ID (PGA/PLA) of de Tenant-ID van de Cloud Solution Provider (CSP) (micro soft-ID). U kunt een van deze id's gebruiken om de status van de micro soft Partner Agreement Sign te controleren met behulp van de **AgreementStatus** -API.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- De MPN-ID (PGA/PLA) of de CSP-Tenant-ID (micro soft-ID) van de indirecte wederverkoper. *U moet een van deze twee id's gebruiken.*

## <a name="c"></a>C\#

De handtekening status van de micro soft-partner overeenkomst van een indirecte wederverkoper ophalen:

1. Gebruik uw verzameling **IAggregatePartner. compliance** om de eigenschap **AgreementSignatureStatus** aan te roepen.

2. Roep de methode [**Get ()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.compliance.iagreementsignaturestatus.getasync) aan.

``` csharp
// IAggregatePartner partnerOperations;

var agreementSignatureStatusByMpnId = partnerOperations.Compliance.AgreementSignatureStatus.Get(mpnId:"Enter MPN Id (PGA/PLA)");

var agreementSignatureStatusByTenantId = partnerOperations.Compliance.AgreementSignatureStatus.Get(tenantId: "Enter Tenant Id");
```

- Voor beeld: **[console test-app](console-test-app.md)**
- Project: **PartnerCenterSDK. FeaturesSamples**
- Klasse: **GetAgreementSignatureStatus. cs**

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode | Aanvraag-URI |
| ------ | ----------- |
| **Toevoegen** | *[{baseURL}](partner-center-rest-urls.md)*/v1/compliance/{ProgramName}/agreementstatus? mpnId = {mpnId} &tenantId = {tenantId} |

#### <a name="uri-parameters"></a>URI-para meters

U moet een van de volgende twee query parameters opgeven om de partner te identificeren. Als u niet een van deze twee query parameters opgeeft, ontvangt u een fout melding van **400 (ongeldige aanvraag)** .

| Naam | Type | Vereist | Beschrijving |
| ---- | ---- | -------- | ----------- |
| **MpnId** | int | Nee | Een Microsoft Partner Network-ID (PGA/PLA) waarmee de indirecte wederverkoper wordt geïdentificeerd. |
| **Tenant-ID** | GUID | Nee | Een micro soft-ID waarmee het CSP-account van de indirecte wederverkoper wordt geïdentificeerd. |

### <a name="request-headers"></a>Aanvraagheaders

Zie de REST van het [Partner Center](headers.md)voor meer informatie.

### <a name="request-examples"></a>Aanvraag voorbeelden

#### <a name="request-using-mpn-id-pgapla"></a>Aanvraag met behulp van MPN-ID (PGA/PLA)

In het volgende voor beeld wordt de ID van de micro soft-partner overeenkomst voor de indirecte wederverkoper opgehaald met behulp van de beMicrosoft Partner Networkcode van de indirecte wederverkoper.

```http
GET https://api.partnercenter.microsoft.com/v1/compliance/csp/agreementstatus?mpnid=1234567 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

#### <a name="request-using-csp-tenant-id"></a>Aanvraag met de Tenant-ID van CSP

In het volgende voor beeld wordt de ID van de micro soft Partner Agreement Sign van de indirecte wederverkoper opgehaald met behulp van de CSP-Tenant van de indirecte wederverkoper (micro soft-ID).

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

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example-success"></a>Voor beeld van antwoord (geslaagd)

Het volgende voor beeld van een antwoord geeft aan of de indirecte wederverkoper de micro soft-partner overeenkomst heeft ondertekend.

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

### <a name="response-examples-failure"></a>Voor beelden van antwoorden (fout)

U ontvangt mogelijk antwoorden die vergelijkbaar zijn met de volgende voor beelden wanneer de handtekening status van de micro soft-partner overeenkomst van de indirecte wederverkoper niet kan worden geretourneerd.

#### <a name="non-guid-formatted-csp-tenant-id"></a>Niet-GUID geformatteerde CSP-Tenant-ID

Het volgende voor beeld van een antwoord wordt geretourneerd wanneer de CSP-Tenant-ID die u aan de API hebt door gegeven, geen GUID is.

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

#### <a name="non-numeric-mpn-id"></a>Niet-numerieke MPN-ID

Het volgende voor beeld van een antwoord wordt geretourneerd wanneer de MPN-ID (PGA/PLA) die u aan de API hebt door gegeven, niet numeriek is.

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

#### <a name="no-mpn-id-or-csp-tenant-id"></a>Geen MPN-ID of CSP-Tenant-ID

Het volgende voor beeld van een antwoord wordt geretourneerd wanneer u een MPN-ID (PGA/PLA) of CSP-Tenant-ID niet hebt door gegeven aan de API. U moet een van de twee ID-typen door geven aan de API.

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

#### <a name="both-mpn-id-and-csp-tenant-id-passed"></a>Zowel de MPN-ID als de CSP-Tenant-ID zijn door gegeven

Het volgende voor beeld van een antwoord wordt geretourneerd wanneer u zowel de MPN-ID (PGA/PLA) als de CSP-Tenant-ID door geven aan de API. U moet *slechts één* van de twee id-typen door geven aan de API.

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

#### <a name="csp-indirect-reseller-mpn-id-pgapla-is-either-invalid-or-not-migrated-from-partner-membership-center-to-partner-center"></a>De MPN-id (PGA/PLA) van de CSP indirecte dealer is ongeldig of niet gemigreerd van het partner lidmaatschaps centrum naar het partner centrum

Het volgende voor beeld van een antwoord wordt geretourneerd wanneer een door gegeven indirecte wederverkoper MPN-ID (PGA/PLA) ongeldig is of niet is gemigreerd van het Partner Membership Center naar het partner centrum. [Meer informatie](https://partner.microsoft.com/resources/detail/migrate-pmc-pc-mpa-guide-pptx)

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

#### <a name="csp-indirect-provider-region-and-csp-indirect-reseller-region-does-not-match"></a>De SSP-regio en de CSP indirecte wederverkoper-regio komen niet overeen

Het volgende voor beeld van een antwoord wordt geretourneerd wanneer de regio van de indirecte reseller MPN-ID (PGA/PLA) niet overeenkomt met de regio van de indirecte provider. Meer [informatie](/partner-center/mpa-indirect-provider-faq) over CSP-regio's.

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

#### <a name="csp-indirect-reseller-account-exists-in-partner-center-but-hasnt-signed-the-mpa"></a>Het account voor de indirecte dealer van CSP bestaat in het partner centrum, maar heeft de MPA niet ondertekend

Het volgende voor beeld van een antwoord wordt geretourneerd wanneer het CSP indirecte reseller-account in het partner centrum de MPA niet heeft ondertekend. [Meer informatie](/partner-center/mpa-indirect-provider-faq)

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

#### <a name="no-csp-indirect-reseller-account-is-associated-with-the-given-mpn-id"></a>Er is geen indirect-dealer account voor CSP gekoppeld aan de opgegeven MPN-ID

Het volgende voor beeld van een antwoord wordt geretourneerd wanneer het partner centrum de MPN-ID (PGA/PLA) kan herkennen die in de aanvraag is gegeven, maar er geen CSP-registratie is gekoppeld aan de opgegeven MPN-ID (PGA/PLA). [Meer informatie](/partner-center/mpa-indirect-provider-faq)

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

#### <a name="invalid-tenant-id"></a>Ongeldige Tenant-ID

Het volgende voor beeld van een antwoord wordt geretourneerd wanneer het partner centrum geen account vindt dat is gekoppeld aan de Tenant-ID die in de aanvraag is door gegeven.

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

#### <a name="no-mpa-found-with-the-given-tenant-id"></a>Er is geen MPA gevonden met de opgegeven Tenant-ID

Het volgende voor beeld van een antwoord wordt geretourneerd wanneer in het partner centrum geen MPA-hand tekening met de opgegeven Tenant-ID is gevonden. [Meer informatie](/partner-center/mpa-indirect-provider-faq)

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