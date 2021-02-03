---
title: Factuur ophalen
description: Hiermee wordt een factuur overzicht opgehaald met de factuur-ID.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 42e5201919eea5644da463dfe2584c8d55002083
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767266"
---
# <a name="get-invoice-statement"></a><span data-ttu-id="3e8a3-103">Factuur ophalen</span><span class="sxs-lookup"><span data-stu-id="3e8a3-103">Get invoice statement</span></span>

<span data-ttu-id="3e8a3-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="3e8a3-104">**Applies To**</span></span>

- <span data-ttu-id="3e8a3-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="3e8a3-105">Partner Center</span></span>
- <span data-ttu-id="3e8a3-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="3e8a3-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="3e8a3-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="3e8a3-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="3e8a3-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="3e8a3-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="3e8a3-109">Hiermee wordt een factuur overzicht opgehaald met de factuur-ID.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-109">Retrieves an invoice statement using the invoice ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3e8a3-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3e8a3-110">Prerequisites</span></span>

- <span data-ttu-id="3e8a3-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3e8a3-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="3e8a3-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="3e8a3-113">Een geldige factuur-ID.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-113">A valid Invoice ID.</span></span>

## <a name="c"></a><span data-ttu-id="3e8a3-114">C\#</span><span class="sxs-lookup"><span data-stu-id="3e8a3-114">C\#</span></span>

<span data-ttu-id="3e8a3-115">Als u een factuur overzicht op ID wilt ophalen, gebruikt u uw verzameling **IPartner. facturen** en roept u de methode **ById ()** aan met behulp van de factuur-ID en roept u de methoden **Documents ()** en **statement ()** aan om toegang te krijgen tot het factuur overzicht.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-115">To get an invoice statement by ID, use your **IPartner.Invoices** collection and call the **ById()** method using the invoice ID, then call the **Documents()** and **Statement()** methods to access the invoice statement.</span></span> <span data-ttu-id="3e8a3-116">Roep ten slotte de methoden **Get ()** of **GetAsync ()** aan.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-116">Finally, call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoiceStatement = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Documents.Statement.Get();
```

<span data-ttu-id="3e8a3-117">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="3e8a3-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="3e8a3-118">**Project**: PartnerSDK. FeatureSample- **klasse**: GetInvoiceStatement.cs</span><span class="sxs-lookup"><span data-stu-id="3e8a3-118">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoiceStatement.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="3e8a3-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="3e8a3-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3e8a3-120">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3e8a3-120">Request syntax</span></span>

| <span data-ttu-id="3e8a3-121">Methode</span><span class="sxs-lookup"><span data-stu-id="3e8a3-121">Method</span></span>  | <span data-ttu-id="3e8a3-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="3e8a3-122">Request URI</span></span>                                                                                       |
|---------|---------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3e8a3-123">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="3e8a3-123">**GET**</span></span> | <span data-ttu-id="3e8a3-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/Documents/statement http/1.1</span><span class="sxs-lookup"><span data-stu-id="3e8a3-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/documents/statement HTTP/1.1</span></span>  |

### <a name="uri-parameter"></a><span data-ttu-id="3e8a3-125">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="3e8a3-125">URI parameter</span></span>

<span data-ttu-id="3e8a3-126">Gebruik de volgende query parameter om het factuur overzicht op te halen.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-126">Use the following query parameter to get the invoice statement.</span></span>

| <span data-ttu-id="3e8a3-127">Naam</span><span class="sxs-lookup"><span data-stu-id="3e8a3-127">Name</span></span>       | <span data-ttu-id="3e8a3-128">Type</span><span class="sxs-lookup"><span data-stu-id="3e8a3-128">Type</span></span>       | <span data-ttu-id="3e8a3-129">Vereist</span><span class="sxs-lookup"><span data-stu-id="3e8a3-129">Required</span></span> | <span data-ttu-id="3e8a3-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3e8a3-130">Description</span></span>                                                                                        |
|------------|------------|----------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3e8a3-131">factuur-ID</span><span class="sxs-lookup"><span data-stu-id="3e8a3-131">invoice-id</span></span> | <span data-ttu-id="3e8a3-132">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3e8a3-132">string</span></span>     | <span data-ttu-id="3e8a3-133">Yes</span><span class="sxs-lookup"><span data-stu-id="3e8a3-133">Yes</span></span>      | <span data-ttu-id="3e8a3-134">De waarde is een factuur-ID waarmee de wederverkoper de resultaten voor een bepaalde factuur kan filteren.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-134">The value is an invoice-id that allows the reseller to filter the results for a given invoice.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="3e8a3-135">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="3e8a3-135">Request headers</span></span>

<span data-ttu-id="3e8a3-136">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="3e8a3-136">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3e8a3-137">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="3e8a3-137">Request body</span></span>

<span data-ttu-id="3e8a3-138">Geen</span><span class="sxs-lookup"><span data-stu-id="3e8a3-138">None</span></span>

### <a name="request-example"></a><span data-ttu-id="3e8a3-139">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3e8a3-139">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id>/documents/statement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a><span data-ttu-id="3e8a3-140">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="3e8a3-140">REST response</span></span>

<span data-ttu-id="3e8a3-141">Als dit lukt, retourneert deze methode een [InvoiceStatement](invoice-resources.md#invoicestatement) -resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-141">If successful, this method returns an [InvoiceStatement](invoice-resources.md#invoicestatement) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3e8a3-142">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="3e8a3-142">Response success and error codes</span></span>

<span data-ttu-id="3e8a3-143">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-143">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="3e8a3-144">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-144">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3e8a3-145">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="3e8a3-145">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="3e8a3-146">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="3e8a3-146">Response example</span></span>

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
