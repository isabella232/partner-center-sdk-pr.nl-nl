---
title: Ontvangstoverzicht van facturen ophalen
description: Hiermee wordt een factuur ontvangst verklaring opgehaald met behulp van de factuur-ID en de ontvangst-ID.
ms.date: 02/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 96cef11d6778de2d9bf28e466d88a39f9415727d
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767165"
---
# <a name="get-invoice-receipt-statement"></a>Ontvangstoverzicht van facturen ophalen

**Van toepassing op**

- Partnercentrum

Hiermee wordt een factuur ontvangst verklaring opgehaald met behulp van de factuur-ID en de ontvangst-ID.

> [!IMPORTANT]
> Deze functie is alleen van toepassing op de fiscale betalings bewijzen van Taiwan.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een geldige factuur-ID en een bijbehorende ontvangst-ID.

## <a name="c"></a>C\#

Als u een factuur ontvangstbewijs verklaring per ID wilt ontvangen, begint u met de Partner Center SDK v 1.12.0, gebruikt u uw **IPartner. facturen** -verzameling en roept u de methode **ById ()** aan  met behulp van de factuur-ID. Vervolgens roept u de verzameling ontvangsten **aan en roept** u **ById (** **) aan** om toegang te krijgen tot het factuur ontvangstbewijs overzicht. Roep ten slotte de methoden **Get ()** of **GetAsync ()** aan.

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoiceStatement = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Receipts.ById(selectedReceipt).Documents.Statement.Get();
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: PartnerSDK. FeatureSample- **klasse**: GetInvoiceReceiptStatement.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/Receipts/{Receipt-id}/Documents/statement http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende query parameter om het factuur ontvangst overzicht op te halen.

| Naam       | Type   | Vereist | Beschrijving                                                                                    |
|------------|--------|-----------------------------------------------------------------------------------------------------------|
| factuur-ID | tekenreeks | Yes      | De waarde is een factuur-ID waarmee de wederverkoper de resultaten voor een bepaalde factuur kan filteren. |
| ontvangst-id | tekenreeks | Yes      | De waarde is een ontvangst-id waarmee de wederverkoper de ontvangsten voor een bepaalde factuur kan filteren. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als dit lukt, retourneert deze methode een PDF-stroom in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

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
