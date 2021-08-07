---
title: Ontvangstoverzicht van facturen ophalen
description: Hiermee wordt een factuurbevestigingsoverzicht opgehaald met behulp van de factuur-id en de ontvangst-id.
ms.date: 02/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ed47eadb377a94363b46cbc5508e5377cee005007698df9077d085705c7b9d08
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115990729"
---
# <a name="get-invoice-receipt-statement"></a>Ontvangstoverzicht van facturen ophalen

Hiermee wordt een factuurbevestigingsoverzicht opgehaald met behulp van de factuur-id en de ontvangst-id.

> [!IMPORTANT]
> Deze functie is alleen van toepassing op btw-ontvangsten in Taiwan.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.

- Een geldige factuur-id en een bijbehorende ontvangstbewijs-id.

## <a name="c"></a>C\#

Als u een factuurbevestigingsoverzicht per id wilt ophalen, te beginnen met Partnercentrum-SDK v1.12.0, gebruikt u de  verzameling **IPartner.Invoices** en roept u de **methode ById()** aan met behulp van de factuur-id, roept u de ontvangstverzameling aan en roept u **vervolgens ById()** aan en roept u de methoden **Documents()** en **Statement()** aan om toegang te krijgen tot de factuurafrekening. Roep ten slotte de **methoden Get()** of **GetAsync()** aan.

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoiceStatement = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Receipts.ById(selectedReceipt).Documents.Statement.Get();
```

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project:** PartnerSDK.FeatureSample-klasse: GetInvoiceReceiptStatement.cs 

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/receipts/{receipt-id}/documents/statement HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om de factuurafrekening op te halen.

| Naam       | Type   | Vereist | Beschrijving                                                                                    |
|------------|--------|-----------------------------------------------------------------------------------------------------------|
| invoice-id | tekenreeks | Yes      | De waarde is een factuur-id waarmee de reseller de resultaten voor een bepaalde factuur kan filteren. |
| receipt-id | tekenreeks | Yes      | De waarde is een ontvangstbewijs-id waarmee de reseller de ontvangstbewijzen voor een bepaalde factuur kan filteren. |

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

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

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
