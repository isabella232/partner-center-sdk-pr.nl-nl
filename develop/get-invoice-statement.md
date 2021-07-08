---
title: Factuur ophalen
description: Hiermee haalt u een factuuroverzicht op met behulp van de factuur-id.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: f0324916eb2efd9244530a53b1d7bb4abc0c8e6e
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549124"
---
# <a name="get-invoice-statement"></a>Factuur ophalen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.

- Een geldige factuur-id.

## <a name="c"></a>C\#

Als u een factuuroverzicht op id wilt ophalen, gebruikt u de verzameling **IPartner.Invoices** en roept u de methode **ById()** aan met behulp van de factuur-id. Roep vervolgens de methoden **Documents()** en **Statement()** aan om toegang te krijgen tot de factuurverklaring. Roep ten slotte de **methoden Get()** of **GetAsync()** aan.

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoiceStatement = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Documents.Statement.Get();
```

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project:** PartnerSDK.FeatureSample **Class:** GetInvoiceStatement.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                       |
|---------|---------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/documents/statement HTTP/1.1  |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om de factuuroverzicht op te halen.

| Naam       | Type       | Vereist | Beschrijving                                                                                        |
|------------|------------|----------|----------------------------------------------------------------------------------------------------|
| invoice-id | tekenreeks     | Ja      | De waarde is een factuur-id waarmee de reseller de resultaten voor een bepaalde factuur kan filteren. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id>/documents/statement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een [InvoiceStatement-resource](invoice-resources.md#invoicestatement) in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 219753
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
Date: Thu, 24 Mar 2016 05:21:01 GMT

{
    _content    {System.Net.Http.ByteArrayContent}    System.Net.Http.HttpContent {System.Net.Http.ByteArrayContent}
    _content    {byte[219753]}    byte[]
    _headers    {Content-Type: application/pdf Content-Disposition: attachment; filename=Invoice_G000024132.pdf}
}
```
