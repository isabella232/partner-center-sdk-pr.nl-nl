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
# <a name="get-invoice-receipt-statement"></a><span data-ttu-id="e88e6-103">Ontvangstoverzicht van facturen ophalen</span><span class="sxs-lookup"><span data-stu-id="e88e6-103">Get invoice receipt statement</span></span>

<span data-ttu-id="e88e6-104">Haalt een factuurbevestigingsoverzicht op met behulp van de factuur-id en de ontvangstbewijs-id.</span><span class="sxs-lookup"><span data-stu-id="e88e6-104">Retrieves an invoice receipt statement using invoice ID and the receipt ID.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e88e6-105">Deze functie is alleen van toepassing op btw-ontvangsten in Taiwan.</span><span class="sxs-lookup"><span data-stu-id="e88e6-105">This feature is only applicable to Taiwan tax receipts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e88e6-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e88e6-106">Prerequisites</span></span>

- <span data-ttu-id="e88e6-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e88e6-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e88e6-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="e88e6-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="e88e6-109">Een geldige factuur-id en een bijbehorend ontvangstbewijs-id.</span><span class="sxs-lookup"><span data-stu-id="e88e6-109">A valid Invoice ID and a corresponding receipt ID.</span></span>

## <a name="c"></a><span data-ttu-id="e88e6-110">C\#</span><span class="sxs-lookup"><span data-stu-id="e88e6-110">C\#</span></span>

<span data-ttu-id="e88e6-111">Als u een factuurbevestigingsoverzicht per id wilt ophalen, vanaf Partnercentrum-SDK v1.12.0, gebruikt u de verzameling **IPartner.Invoices** en roept u de **methode ById()** aan met behulp van de factuur-id, roept u vervolgens de ontvangstenverzameling aan, roept u **ById()** aan en roept u vervolgens de methoden **Documents()** en **Statement()** aan om toegang te krijgen tot de factuurbevestigingsinrekening. </span><span class="sxs-lookup"><span data-stu-id="e88e6-111">To get an invoice receipt statement by ID, starting with Partner Center SDK v1.12.0, use your **IPartner.Invoices** collection and call the **ById()** method using the invoice ID, then call the **Receipts** collection and call **ById()** then call the **Documents()** and **Statement()** methods to access the invoice receipt statement.</span></span> <span data-ttu-id="e88e6-112">Roep ten slotte de **methoden Get()** of **GetAsync()** aan.</span><span class="sxs-lookup"><span data-stu-id="e88e6-112">Finally, call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoiceStatement = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Receipts.ById(selectedReceipt).Documents.Statement.Get();
```

<span data-ttu-id="e88e6-113">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="e88e6-113">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="e88e6-114">**Project:** PartnerSDK.FeatureSample-klasse: GetInvoiceReceiptStatement.cs </span><span class="sxs-lookup"><span data-stu-id="e88e6-114">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoiceReceiptStatement.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="e88e6-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e88e6-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e88e6-116">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e88e6-116">Request syntax</span></span>

| <span data-ttu-id="e88e6-117">Methode</span><span class="sxs-lookup"><span data-stu-id="e88e6-117">Method</span></span>  | <span data-ttu-id="e88e6-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e88e6-118">Request URI</span></span>                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e88e6-119">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e88e6-119">**GET**</span></span> | <span data-ttu-id="e88e6-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/receipts/{receipt-id}/documents/statement HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e88e6-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/receipts/{receipt-id}/documents/statement HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="e88e6-121">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="e88e6-121">URI parameter</span></span>

<span data-ttu-id="e88e6-122">Gebruik de volgende queryparameter om de factuurbevestigingsverklaring op te halen.</span><span class="sxs-lookup"><span data-stu-id="e88e6-122">Use the following query parameter to get the invoice receipt statement.</span></span>

| <span data-ttu-id="e88e6-123">Naam</span><span class="sxs-lookup"><span data-stu-id="e88e6-123">Name</span></span>       | <span data-ttu-id="e88e6-124">Type</span><span class="sxs-lookup"><span data-stu-id="e88e6-124">Type</span></span>   | <span data-ttu-id="e88e6-125">Vereist</span><span class="sxs-lookup"><span data-stu-id="e88e6-125">Required</span></span> | <span data-ttu-id="e88e6-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e88e6-126">Description</span></span>                                                                                    |
|------------|--------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e88e6-127">factuur-id</span><span class="sxs-lookup"><span data-stu-id="e88e6-127">invoice-id</span></span> | <span data-ttu-id="e88e6-128">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e88e6-128">string</span></span> | <span data-ttu-id="e88e6-129">Ja</span><span class="sxs-lookup"><span data-stu-id="e88e6-129">Yes</span></span>      | <span data-ttu-id="e88e6-130">De waarde is een factuur-id waarmee de reseller de resultaten voor een bepaalde factuur kan filteren.</span><span class="sxs-lookup"><span data-stu-id="e88e6-130">The value is an invoice-id that allows the reseller to filter the results for a given invoice.</span></span> |
| <span data-ttu-id="e88e6-131">receipt-id</span><span class="sxs-lookup"><span data-stu-id="e88e6-131">receipt-id</span></span> | <span data-ttu-id="e88e6-132">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e88e6-132">string</span></span> | <span data-ttu-id="e88e6-133">Ja</span><span class="sxs-lookup"><span data-stu-id="e88e6-133">Yes</span></span>      | <span data-ttu-id="e88e6-134">De waarde is een ontvangstbewijs-id waarmee de reseller de ontvangstbewijzen voor een bepaalde factuur kan filteren.</span><span class="sxs-lookup"><span data-stu-id="e88e6-134">The value is a receipt-id that allows the reseller to filter the receipts for a given invoice.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e88e6-135">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e88e6-135">Request headers</span></span>

<span data-ttu-id="e88e6-136">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e88e6-136">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e88e6-137">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e88e6-137">Request body</span></span>

<span data-ttu-id="e88e6-138">Geen</span><span class="sxs-lookup"><span data-stu-id="e88e6-138">None</span></span>

### <a name="request-example"></a><span data-ttu-id="e88e6-139">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e88e6-139">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id>/receipts/<receipt-id>/documents/statement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a><span data-ttu-id="e88e6-140">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e88e6-140">REST response</span></span>

<span data-ttu-id="e88e6-141">Als dit lukt, retourneert deze methode een PDF-stroom in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="e88e6-141">If successful, this method returns a pdf stream in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e88e6-142">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e88e6-142">Response success and error codes</span></span>

<span data-ttu-id="e88e6-143">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e88e6-143">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e88e6-144">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e88e6-144">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e88e6-145">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="e88e6-145">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e88e6-146">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e88e6-146">Response example</span></span>

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
