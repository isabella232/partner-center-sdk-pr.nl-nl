---
title: Factuur op id ontvangen
description: Hiermee haalt u een bepaalde factuur op met behulp van de factuur-id.
ms.date: 06/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: c888786a6b6ca941629bb7aac95227021c37a7fc
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549158"
---
# <a name="get-invoice-by-id"></a><span data-ttu-id="4d5e8-103">Factuur op id ontvangen</span><span class="sxs-lookup"><span data-stu-id="4d5e8-103">Get invoice by ID</span></span>

<span data-ttu-id="4d5e8-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="4d5e8-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="4d5e8-105">Hiermee haalt u een bepaalde factuur op met behulp van de factuur-id.</span><span class="sxs-lookup"><span data-stu-id="4d5e8-105">Retrieves a given invoice using the invoice ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4d5e8-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4d5e8-106">Prerequisites</span></span>

- <span data-ttu-id="4d5e8-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4d5e8-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4d5e8-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="4d5e8-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="4d5e8-109">Een geldige factuur-id.</span><span class="sxs-lookup"><span data-stu-id="4d5e8-109">A valid Invoice ID.</span></span>

## <a name="c"></a><span data-ttu-id="4d5e8-110">C\#</span><span class="sxs-lookup"><span data-stu-id="4d5e8-110">C\#</span></span>

<span data-ttu-id="4d5e8-111">Een factuur op id ontvangen:</span><span class="sxs-lookup"><span data-stu-id="4d5e8-111">To get an invoice by ID:</span></span>

1. <span data-ttu-id="4d5e8-112">Gebruik de **verzameling IPartner.Invoices en** roep de **methode ById()** aan.</span><span class="sxs-lookup"><span data-stu-id="4d5e8-112">Use your **IPartner.Invoices** collection and call the **ById()** method.</span></span>

2. <span data-ttu-id="4d5e8-113">Roep de **methoden Get()** of **GetAsync()** aan.</span><span class="sxs-lookup"><span data-stu-id="4d5e8-113">Call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IPartner scopedPartnerOperations;
// string selectedInvoiceId;

var invoice = scopedPartnerOperations.Invoices.ById(selectedInvoiceId).Get();
```

<span data-ttu-id="4d5e8-114">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="4d5e8-114">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="4d5e8-115">**Project:** PartnerSDK.FeatureSample-klasse: GetInvoice.cs </span><span class="sxs-lookup"><span data-stu-id="4d5e8-115">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoice.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="4d5e8-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="4d5e8-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4d5e8-117">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="4d5e8-117">Request syntax</span></span>

| <span data-ttu-id="4d5e8-118">Methode</span><span class="sxs-lookup"><span data-stu-id="4d5e8-118">Method</span></span>  | <span data-ttu-id="4d5e8-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="4d5e8-119">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="4d5e8-120">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="4d5e8-120">**GET**</span></span> | <span data-ttu-id="4d5e8-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4d5e8-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="4d5e8-122">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="4d5e8-122">URI parameter</span></span>

<span data-ttu-id="4d5e8-123">Gebruik de volgende queryparameter om de factuur op te halen.</span><span class="sxs-lookup"><span data-stu-id="4d5e8-123">Use the following query parameter to get the invoice.</span></span>

| <span data-ttu-id="4d5e8-124">Naam</span><span class="sxs-lookup"><span data-stu-id="4d5e8-124">Name</span></span>           | <span data-ttu-id="4d5e8-125">Type</span><span class="sxs-lookup"><span data-stu-id="4d5e8-125">Type</span></span>       | <span data-ttu-id="4d5e8-126">Vereist</span><span class="sxs-lookup"><span data-stu-id="4d5e8-126">Required</span></span> | <span data-ttu-id="4d5e8-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4d5e8-127">Description</span></span>                                                                                        |
|----------------|------------|----------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4d5e8-128">**factuur-id**</span><span class="sxs-lookup"><span data-stu-id="4d5e8-128">**invoice-id**</span></span> | <span data-ttu-id="4d5e8-129">**Tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="4d5e8-129">**string**</span></span> | <span data-ttu-id="4d5e8-130">Ja</span><span class="sxs-lookup"><span data-stu-id="4d5e8-130">Yes</span></span>      | <span data-ttu-id="4d5e8-131">De waarde is een **factuur-id** waarmee de reseller de resultaten voor een bepaalde factuur kan filteren.</span><span class="sxs-lookup"><span data-stu-id="4d5e8-131">The value is an **invoice-id** that allows the reseller to filter the results for a given invoice.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4d5e8-132">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="4d5e8-132">Request headers</span></span>

<span data-ttu-id="4d5e8-133">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="4d5e8-133">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4d5e8-134">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="4d5e8-134">Request body</span></span>

<span data-ttu-id="4d5e8-135">Geen</span><span class="sxs-lookup"><span data-stu-id="4d5e8-135">None</span></span>

### <a name="request-example"></a><span data-ttu-id="4d5e8-136">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4d5e8-136">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/<invoice-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8ac25aa5-9537-4b6d-b782-aa0c8e979e99
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
```

## <a name="rest-response"></a><span data-ttu-id="4d5e8-137">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="4d5e8-137">REST response</span></span>

<span data-ttu-id="4d5e8-138">Als dit lukt, retourneert deze methode een [factuurresource](invoice-resources.md#invoice) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="4d5e8-138">If successful, this method returns an [Invoice](invoice-resources.md#invoice) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4d5e8-139">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="4d5e8-139">Response success and error codes</span></span>

<span data-ttu-id="4d5e8-140">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="4d5e8-140">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4d5e8-141">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="4d5e8-141">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4d5e8-142">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="4d5e8-142">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4d5e8-143">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="4d5e8-143">Response example</span></span>

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
