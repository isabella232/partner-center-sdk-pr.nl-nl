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
# <a name="get-invoice-statement"></a><span data-ttu-id="9f9fd-103">Factuur ophalen</span><span class="sxs-lookup"><span data-stu-id="9f9fd-103">Get invoice statement</span></span>

<span data-ttu-id="9f9fd-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="9f9fd-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9f9fd-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9f9fd-105">Prerequisites</span></span>

- <span data-ttu-id="9f9fd-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9f9fd-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9f9fd-107">Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="9f9fd-108">Een geldige factuur-id.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-108">A valid Invoice ID.</span></span>

## <a name="c"></a><span data-ttu-id="9f9fd-109">C\#</span><span class="sxs-lookup"><span data-stu-id="9f9fd-109">C\#</span></span>

<span data-ttu-id="9f9fd-110">Als u een factuuroverzicht op id wilt ophalen, gebruikt u de verzameling **IPartner.Invoices** en roept u de methode **ById()** aan met behulp van de factuur-id. Roep vervolgens de methoden **Documents()** en **Statement()** aan om toegang te krijgen tot de factuurverklaring.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-110">To get an invoice statement by ID, use your **IPartner.Invoices** collection and call the **ById()** method using the invoice ID, then call the **Documents()** and **Statement()** methods to access the invoice statement.</span></span> <span data-ttu-id="9f9fd-111">Roep ten slotte de **methoden Get()** of **GetAsync()** aan.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-111">Finally, call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoiceStatement = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Documents.Statement.Get();
```

<span data-ttu-id="9f9fd-112">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="9f9fd-112">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="9f9fd-113">**Project:** PartnerSDK.FeatureSample **Class:** GetInvoiceStatement.cs</span><span class="sxs-lookup"><span data-stu-id="9f9fd-113">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoiceStatement.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="9f9fd-114">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="9f9fd-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9f9fd-115">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="9f9fd-115">Request syntax</span></span>

| <span data-ttu-id="9f9fd-116">Methode</span><span class="sxs-lookup"><span data-stu-id="9f9fd-116">Method</span></span>  | <span data-ttu-id="9f9fd-117">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="9f9fd-117">Request URI</span></span>                                                                                       |
|---------|---------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9f9fd-118">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="9f9fd-118">**GET**</span></span> | <span data-ttu-id="9f9fd-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/documents/statement HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="9f9fd-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/documents/statement HTTP/1.1</span></span>  |

### <a name="uri-parameter"></a><span data-ttu-id="9f9fd-120">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="9f9fd-120">URI parameter</span></span>

<span data-ttu-id="9f9fd-121">Gebruik de volgende queryparameter om de factuuroverzicht op te halen.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-121">Use the following query parameter to get the invoice statement.</span></span>

| <span data-ttu-id="9f9fd-122">Naam</span><span class="sxs-lookup"><span data-stu-id="9f9fd-122">Name</span></span>       | <span data-ttu-id="9f9fd-123">Type</span><span class="sxs-lookup"><span data-stu-id="9f9fd-123">Type</span></span>       | <span data-ttu-id="9f9fd-124">Vereist</span><span class="sxs-lookup"><span data-stu-id="9f9fd-124">Required</span></span> | <span data-ttu-id="9f9fd-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9f9fd-125">Description</span></span>                                                                                        |
|------------|------------|----------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9f9fd-126">invoice-id</span><span class="sxs-lookup"><span data-stu-id="9f9fd-126">invoice-id</span></span> | <span data-ttu-id="9f9fd-127">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9f9fd-127">string</span></span>     | <span data-ttu-id="9f9fd-128">Ja</span><span class="sxs-lookup"><span data-stu-id="9f9fd-128">Yes</span></span>      | <span data-ttu-id="9f9fd-129">De waarde is een factuur-id waarmee de reseller de resultaten voor een bepaalde factuur kan filteren.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-129">The value is an invoice-id that allows the reseller to filter the results for a given invoice.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9f9fd-130">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="9f9fd-130">Request headers</span></span>

<span data-ttu-id="9f9fd-131">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="9f9fd-131">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9f9fd-132">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="9f9fd-132">Request body</span></span>

<span data-ttu-id="9f9fd-133">Geen</span><span class="sxs-lookup"><span data-stu-id="9f9fd-133">None</span></span>

### <a name="request-example"></a><span data-ttu-id="9f9fd-134">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9f9fd-134">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id>/documents/statement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a><span data-ttu-id="9f9fd-135">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="9f9fd-135">REST response</span></span>

<span data-ttu-id="9f9fd-136">Als dit lukt, retourneert deze methode een [InvoiceStatement-resource](invoice-resources.md#invoicestatement) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-136">If successful, this method returns an [InvoiceStatement](invoice-resources.md#invoicestatement) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9f9fd-137">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="9f9fd-137">Response success and error codes</span></span>

<span data-ttu-id="9f9fd-138">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-138">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9f9fd-139">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="9f9fd-139">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9f9fd-140">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="9f9fd-140">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9f9fd-141">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="9f9fd-141">Response example</span></span>

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
