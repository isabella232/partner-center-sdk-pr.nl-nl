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
# <a name="get-invoice-receipt-statement"></a><span data-ttu-id="5f30d-103">Ontvangstoverzicht van facturen ophalen</span><span class="sxs-lookup"><span data-stu-id="5f30d-103">Get invoice receipt statement</span></span>

<span data-ttu-id="5f30d-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="5f30d-104">**Applies To**</span></span>

- <span data-ttu-id="5f30d-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="5f30d-105">Partner Center</span></span>

<span data-ttu-id="5f30d-106">Hiermee wordt een factuur ontvangst verklaring opgehaald met behulp van de factuur-ID en de ontvangst-ID.</span><span class="sxs-lookup"><span data-stu-id="5f30d-106">Retrieves an invoice receipt statement using invoice ID and the receipt ID.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5f30d-107">Deze functie is alleen van toepassing op de fiscale betalings bewijzen van Taiwan.</span><span class="sxs-lookup"><span data-stu-id="5f30d-107">This feature is only applicable to Taiwan tax receipts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5f30d-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="5f30d-108">Prerequisites</span></span>

- <span data-ttu-id="5f30d-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5f30d-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5f30d-110">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5f30d-110">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="5f30d-111">Een geldige factuur-ID en een bijbehorende ontvangst-ID.</span><span class="sxs-lookup"><span data-stu-id="5f30d-111">A valid Invoice ID and a corresponding receipt ID.</span></span>

## <a name="c"></a><span data-ttu-id="5f30d-112">C\#</span><span class="sxs-lookup"><span data-stu-id="5f30d-112">C\#</span></span>

<span data-ttu-id="5f30d-113">Als u een factuur ontvangstbewijs verklaring per ID wilt ontvangen, begint u met de Partner Center SDK v 1.12.0, gebruikt u uw **IPartner. facturen** -verzameling en roept u de methode **ById ()** aan  met behulp van de factuur-ID. Vervolgens roept u de verzameling ontvangsten **aan en roept** u **ById (** **) aan** om toegang te krijgen tot het factuur ontvangstbewijs overzicht.</span><span class="sxs-lookup"><span data-stu-id="5f30d-113">To get an invoice receipt statement by ID, starting with Partner Center SDK v1.12.0, use your **IPartner.Invoices** collection and call the **ById()** method using the invoice ID, then call the **Receipts** collection and call **ById()** then call the **Documents()** and **Statement()** methods to access the invoice receipt statement.</span></span> <span data-ttu-id="5f30d-114">Roep ten slotte de methoden **Get ()** of **GetAsync ()** aan.</span><span class="sxs-lookup"><span data-stu-id="5f30d-114">Finally, call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoiceStatement = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Receipts.ById(selectedReceipt).Documents.Statement.Get();
```

<span data-ttu-id="5f30d-115">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="5f30d-115">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="5f30d-116">**Project**: PartnerSDK. FeatureSample- **klasse**: GetInvoiceReceiptStatement.cs</span><span class="sxs-lookup"><span data-stu-id="5f30d-116">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoiceReceiptStatement.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="5f30d-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="5f30d-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5f30d-118">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="5f30d-118">Request syntax</span></span>

| <span data-ttu-id="5f30d-119">Methode</span><span class="sxs-lookup"><span data-stu-id="5f30d-119">Method</span></span>  | <span data-ttu-id="5f30d-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="5f30d-120">Request URI</span></span>                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5f30d-121">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="5f30d-121">**GET**</span></span> | <span data-ttu-id="5f30d-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/Receipts/{Receipt-id}/Documents/statement http/1.1</span><span class="sxs-lookup"><span data-stu-id="5f30d-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/receipts/{receipt-id}/documents/statement HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="5f30d-123">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="5f30d-123">URI parameter</span></span>

<span data-ttu-id="5f30d-124">Gebruik de volgende query parameter om het factuur ontvangst overzicht op te halen.</span><span class="sxs-lookup"><span data-stu-id="5f30d-124">Use the following query parameter to get the invoice receipt statement.</span></span>

| <span data-ttu-id="5f30d-125">Naam</span><span class="sxs-lookup"><span data-stu-id="5f30d-125">Name</span></span>       | <span data-ttu-id="5f30d-126">Type</span><span class="sxs-lookup"><span data-stu-id="5f30d-126">Type</span></span>   | <span data-ttu-id="5f30d-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="5f30d-127">Required</span></span> | <span data-ttu-id="5f30d-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5f30d-128">Description</span></span>                                                                                    |
|------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5f30d-129">factuur-ID</span><span class="sxs-lookup"><span data-stu-id="5f30d-129">invoice-id</span></span> | <span data-ttu-id="5f30d-130">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="5f30d-130">string</span></span> | <span data-ttu-id="5f30d-131">Yes</span><span class="sxs-lookup"><span data-stu-id="5f30d-131">Yes</span></span>      | <span data-ttu-id="5f30d-132">De waarde is een factuur-ID waarmee de wederverkoper de resultaten voor een bepaalde factuur kan filteren.</span><span class="sxs-lookup"><span data-stu-id="5f30d-132">The value is an invoice-id that allows the reseller to filter the results for a given invoice.</span></span> |
| <span data-ttu-id="5f30d-133">ontvangst-id</span><span class="sxs-lookup"><span data-stu-id="5f30d-133">receipt-id</span></span> | <span data-ttu-id="5f30d-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="5f30d-134">string</span></span> | <span data-ttu-id="5f30d-135">Yes</span><span class="sxs-lookup"><span data-stu-id="5f30d-135">Yes</span></span>      | <span data-ttu-id="5f30d-136">De waarde is een ontvangst-id waarmee de wederverkoper de ontvangsten voor een bepaalde factuur kan filteren.</span><span class="sxs-lookup"><span data-stu-id="5f30d-136">The value is a receipt-id that allows the reseller to filter the receipts for a given invoice.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="5f30d-137">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="5f30d-137">Request headers</span></span>

<span data-ttu-id="5f30d-138">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5f30d-138">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5f30d-139">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="5f30d-139">Request body</span></span>

<span data-ttu-id="5f30d-140">Geen</span><span class="sxs-lookup"><span data-stu-id="5f30d-140">None</span></span>

### <a name="request-example"></a><span data-ttu-id="5f30d-141">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="5f30d-141">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id>/receipts/<receipt-id>/documents/statement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a><span data-ttu-id="5f30d-142">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="5f30d-142">REST response</span></span>

<span data-ttu-id="5f30d-143">Als dit lukt, retourneert deze methode een PDF-stroom in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="5f30d-143">If successful, this method returns a pdf stream in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5f30d-144">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="5f30d-144">Response success and error codes</span></span>

<span data-ttu-id="5f30d-145">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="5f30d-145">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5f30d-146">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="5f30d-146">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5f30d-147">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="5f30d-147">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="5f30d-148">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="5f30d-148">Response example</span></span>

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
