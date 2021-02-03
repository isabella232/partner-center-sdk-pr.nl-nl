---
title: Factuur op ID ophalen
description: Haalt een opgegeven factuur op met behulp van de factuur-ID.
ms.date: 06/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 17880265d06e8e5eaacc5470d83c49defd10ad51
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767167"
---
# <a name="get-invoice-by-id"></a><span data-ttu-id="408fd-103">Factuur op ID ophalen</span><span class="sxs-lookup"><span data-stu-id="408fd-103">Get invoice by ID</span></span>

<span data-ttu-id="408fd-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="408fd-104">**Applies to:**</span></span>

- <span data-ttu-id="408fd-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="408fd-105">Partner Center</span></span>
- <span data-ttu-id="408fd-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="408fd-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="408fd-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="408fd-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="408fd-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="408fd-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="408fd-109">Haalt een opgegeven factuur op met behulp van de factuur-ID.</span><span class="sxs-lookup"><span data-stu-id="408fd-109">Retrieves a given invoice using the invoice ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="408fd-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="408fd-110">Prerequisites</span></span>

- <span data-ttu-id="408fd-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="408fd-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="408fd-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="408fd-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="408fd-113">Een geldige factuur-ID.</span><span class="sxs-lookup"><span data-stu-id="408fd-113">A valid Invoice ID.</span></span>

## <a name="c"></a><span data-ttu-id="408fd-114">C\#</span><span class="sxs-lookup"><span data-stu-id="408fd-114">C\#</span></span>

<span data-ttu-id="408fd-115">Een factuur op basis van de ID ophalen:</span><span class="sxs-lookup"><span data-stu-id="408fd-115">To get an invoice by ID:</span></span>

1. <span data-ttu-id="408fd-116">Gebruik uw verzameling **IPartner. facturen** en roep de methode **ById ()** aan.</span><span class="sxs-lookup"><span data-stu-id="408fd-116">Use your **IPartner.Invoices** collection and call the **ById()** method.</span></span>

2. <span data-ttu-id="408fd-117">Roep de methoden **Get ()** of **GetAsync ()** aan.</span><span class="sxs-lookup"><span data-stu-id="408fd-117">Call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoice = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Get();
```

<span data-ttu-id="408fd-118">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="408fd-118">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="408fd-119">**Project**: PartnerSDK. FeatureSample- **klasse**: GetInvoice.cs</span><span class="sxs-lookup"><span data-stu-id="408fd-119">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoice.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="408fd-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="408fd-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="408fd-121">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="408fd-121">Request syntax</span></span>

| <span data-ttu-id="408fd-122">Methode</span><span class="sxs-lookup"><span data-stu-id="408fd-122">Method</span></span>  | <span data-ttu-id="408fd-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="408fd-123">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="408fd-124">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="408fd-124">**GET**</span></span> | <span data-ttu-id="408fd-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID} http/1.1</span><span class="sxs-lookup"><span data-stu-id="408fd-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="408fd-126">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="408fd-126">URI parameter</span></span>

<span data-ttu-id="408fd-127">Gebruik de volgende query parameter om de factuur op te halen.</span><span class="sxs-lookup"><span data-stu-id="408fd-127">Use the following query parameter to get the invoice.</span></span>

| <span data-ttu-id="408fd-128">Naam</span><span class="sxs-lookup"><span data-stu-id="408fd-128">Name</span></span>           | <span data-ttu-id="408fd-129">Type</span><span class="sxs-lookup"><span data-stu-id="408fd-129">Type</span></span>       | <span data-ttu-id="408fd-130">Vereist</span><span class="sxs-lookup"><span data-stu-id="408fd-130">Required</span></span> | <span data-ttu-id="408fd-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="408fd-131">Description</span></span>                                                                                        |
|----------------|------------|----------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="408fd-132">**factuur-ID**</span><span class="sxs-lookup"><span data-stu-id="408fd-132">**invoice-id**</span></span> | <span data-ttu-id="408fd-133">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="408fd-133">**string**</span></span> | <span data-ttu-id="408fd-134">Yes</span><span class="sxs-lookup"><span data-stu-id="408fd-134">Yes</span></span>      | <span data-ttu-id="408fd-135">De waarde is een **factuur-ID** waarmee de wederverkoper de resultaten voor een bepaalde factuur kan filteren.</span><span class="sxs-lookup"><span data-stu-id="408fd-135">The value is an **invoice-id** that allows the reseller to filter the results for a given invoice.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="408fd-136">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="408fd-136">Request headers</span></span>

<span data-ttu-id="408fd-137">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="408fd-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="408fd-138">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="408fd-138">Request body</span></span>

<span data-ttu-id="408fd-139">Geen</span><span class="sxs-lookup"><span data-stu-id="408fd-139">None</span></span>

### <a name="request-example"></a><span data-ttu-id="408fd-140">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="408fd-140">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a><span data-ttu-id="408fd-141">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="408fd-141">REST response</span></span>

<span data-ttu-id="408fd-142">Als dit lukt, retourneert deze methode een [factuur](invoice-resources.md#invoice) resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="408fd-142">If successful, this method returns an [Invoice](invoice-resources.md#invoice) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="408fd-143">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="408fd-143">Response success and error codes</span></span>

<span data-ttu-id="408fd-144">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="408fd-144">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="408fd-145">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="408fd-145">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="408fd-146">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="408fd-146">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="408fd-147">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="408fd-147">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 676
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
Date: Thu, 24 Mar 2016 05:22:14 GMT

{
    "id": "G000024135",
    "invoiceDate": "2018-02-08T22:40:37.5897767Z",
    "billingPeriodStartDate": "2018-02-01T22:40:37.5897767Z",
    "billingPeriodEndDate": "2018-02-28T22:40:37.5897767Z",
    "totalCharges": 2076.63,
    "paidAmount": 0,
    "currencyCode": "USD",
    "currencySymbol": "$",
    "pdfDownloadLink": "/invoices/G000024135/documents/statement",
    "taxReceipts": [
        {
            "id": "123456",
            "taxReceiptPdfDownloadLink": "/invoices/G000024135/receipts/123456/documents/statement"
        }
    ],
    "invoiceDetails": [
        {
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "links": {
                "self": {
                    "uri": "/invoices/OneTime-G000024135/lineitems/OneTime/BillingLineItems",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "InvoiceDetail"
            }
        }
    ],
    "documentType": "invoice",
    "invoiceType": "OneTime",
    "links": {
        "self": {
            "uri": "/invoices/OneTime-G000024135",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Invoice"
    }
}
```
