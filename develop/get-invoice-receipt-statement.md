---
title: Ontvangstoverzicht van facturen ophalen
description: Haalt een factuurbevestigingsoverzicht op met behulp van de factuur-id en de ontvangstbewijs-id.
ms.date: 02/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: dcac4c8f0b881409dcad3560eefb82d4bb5e877a
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446126"
---
# <a name="get-invoice-receipt-statement"></a>Ontvangstoverzicht van facturen ophalen

Haalt een factuurbevestigingsoverzicht op met behulp van de factuur-id en de ontvangstbewijs-id.

> [!IMPORTANT]
> Deze functie is alleen van toepassing op btw-ontvangsten in Taiwan.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een geldige factuur-id en een bijbehorend ontvangstbewijs-id.

## <a name="c"></a>C\#

Als u een factuurbevestigingsoverzicht per id wilt ophalen, vanaf Partnercentrum-SDK v1.12.0, gebruikt u de verzameling **IPartner.Invoices** en roept u de **methode ById()** aan met behulp van de factuur-id, roept u vervolgens de ontvangstenverzameling aan, roept u **ById()** aan en roept u vervolgens de methoden **Documents()** en **Statement()** aan om toegang te krijgen tot de factuurbevestigingsinrekening.  Roep ten slotte de **methoden Get()** of **GetAsync()** aan.

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoiceStatement = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Receipts.ById(selectedReceipt).Documents.Statement.Get();
```

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project:** PartnerSDK.FeatureSample-klasse: GetInvoiceReceiptStatement.cs 

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/receipts/{receipt-id}/documents/statement HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om de factuurbevestigingsverklaring op te halen.

| Naam       | Type   | Vereist | Beschrijving                                                                                    |
|------------|--------|-----------------------------------------------------------------------------------------------------------|
| factuur-id | tekenreeks | Ja      | De waarde is een factuur-id waarmee de reseller de resultaten voor een bepaalde factuur kan filteren. |
| receipt-id | tekenreeks | Ja      | De waarde is een ontvangstbewijs-id waarmee de reseller de ontvangstbewijzen voor een bepaalde factuur kan filteren. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id>/receipts/<receipt-id>/documents/statement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een PDF-stroom in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 195556
Content-Type: application/pdf
MS-CorrelationId: a1d6ab41-5a30-4643-898b-b30d65d3a0a1
MS-RequestId: cc1ba6db-ab26-404a-9196-712b6395f518
Date: Tue, 05 Feb 2019 04:08:23 GMT

{
    _content    {System.Net.Http.ByteArrayContent}    System.Net.Http.HttpContent {System.Net.Http.ByteArrayContent}
    _content    {byte[195556]}    byte[]
    _headers    {Content-Type: application/pdf Content-Disposition: attachment; filename=E-Tax-8602768.pdf}
}
```
