---
title: Factuuroverzichten ophalen
description: U kunt een factuurresource met samenvattingen voor elk valutatype gebruiken om het saldo en de totale kosten van zowel terugkerende als eenmalige kosten weer te geven.
ms.date: 09/24/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: fb6ff839c56c7b0b77a9904abf05d95ca0500b00
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549107"
---
# <a name="get-invoice-summaries"></a><span data-ttu-id="843cc-103">Factuuroverzichten ophalen</span><span class="sxs-lookup"><span data-stu-id="843cc-103">Get invoice summaries</span></span>

<span data-ttu-id="843cc-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="843cc-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="843cc-105">U kunt de **InvoiceSummaries gebruiken** om een factuuroverzicht op te halen met het saldo en de totale kosten van zowel terugkerende als eenmalige kosten.</span><span class="sxs-lookup"><span data-stu-id="843cc-105">You can use the **InvoiceSummaries** to retrieve an invoice summary that shows the balance and total charges of both recurring and one-time charges.</span></span> <span data-ttu-id="843cc-106">De **resource InvoiceSummaries** bevat een factuuroverzicht voor elk valutatype.</span><span class="sxs-lookup"><span data-stu-id="843cc-106">The **InvoiceSummaries** resource contains an invoice summary for each currency type.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="843cc-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="843cc-107">Prerequisites</span></span>

- <span data-ttu-id="843cc-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="843cc-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="843cc-109">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="843cc-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="843cc-110">Een geldige factuur-id.</span><span class="sxs-lookup"><span data-stu-id="843cc-110">A valid invoice identifier.</span></span>

## <a name="c"></a><span data-ttu-id="843cc-111">C\#</span><span class="sxs-lookup"><span data-stu-id="843cc-111">C\#</span></span>

<span data-ttu-id="843cc-112">Een verzameling [**InvoiceSummaries**](invoice-resources.md#invoicesummaries) ophalen die een [**InvoiceSummary**](invoice-resources.md#invoicesummary) bevat voor elk valutatype:</span><span class="sxs-lookup"><span data-stu-id="843cc-112">To retrieve an [**InvoiceSummaries**](invoice-resources.md#invoicesummaries) collection that contains an [**InvoiceSummary**](invoice-resources.md#invoicesummary) for each currency type:</span></span>

1. <span data-ttu-id="843cc-113">Gebruik de **verzameling IAggregatePartner.Invoices** om de eigenschap **Samenvattingen aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="843cc-113">Use your **IAggregatePartner.Invoices** collection to call the **Summaries** property.</span></span>

2. <span data-ttu-id="843cc-114">Roep de **methode Get()** aan.</span><span class="sxs-lookup"><span data-stu-id="843cc-114">Call the **Get()** method.</span></span>
3. <span data-ttu-id="843cc-115">Als u het saldo van een afzonderlijke [**InvoiceSummary**](invoice-resources.md#invoicesummary)wilt ophalen, gaat u naar de **eigenschap BalanceAmount** voor dat lid van de verzameling.</span><span class="sxs-lookup"><span data-stu-id="843cc-115">To get the balance of an individual [**InvoiceSummary**](invoice-resources.md#invoicesummary), access the **BalanceAmount** property for that member of the collection.</span></span>

``` csharp
// IAggregatePartner scopedPartnerOperations;

// Get the invoice summaries collection.
var invoiceSummaries = scopedPartnerOperations.Invoices.Summaries.Get();

// Display the balance on the first invoice summary in the collection.
Console.Out.WriteLine("Current Account Balance:  {0:C}", invoiceSummaries[0].BalanceAmount);
```

<span data-ttu-id="843cc-116">Zie de volgende voorbeeldcode voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="843cc-116">For more information, see the following example code:</span></span>

- <span data-ttu-id="843cc-117">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="843cc-117">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="843cc-118">Project: **PartnerSDK.FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="843cc-118">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="843cc-119">Klasse: **GetInvoiceSummaries.cs**</span><span class="sxs-lookup"><span data-stu-id="843cc-119">Class: **GetInvoiceSummaries.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="843cc-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="843cc-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="843cc-121">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="843cc-121">Request syntax</span></span>

| <span data-ttu-id="843cc-122">Methode</span><span class="sxs-lookup"><span data-stu-id="843cc-122">Method</span></span>  | <span data-ttu-id="843cc-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="843cc-123">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="843cc-124">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="843cc-124">**GET**</span></span> | <span data-ttu-id="843cc-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/summaries HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="843cc-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/summaries HTTP/1.1</span></span>     |

#### <a name="uri-parameter"></a><span data-ttu-id="843cc-126">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="843cc-126">URI parameter</span></span>

<span data-ttu-id="843cc-127">Geen.</span><span class="sxs-lookup"><span data-stu-id="843cc-127">None.</span></span>

### <a name="request-headers"></a><span data-ttu-id="843cc-128">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="843cc-128">Request headers</span></span>

<span data-ttu-id="843cc-129">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="843cc-129">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="843cc-130">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="843cc-130">Request body</span></span>

<span data-ttu-id="843cc-131">Geen.</span><span class="sxs-lookup"><span data-stu-id="843cc-131">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="843cc-132">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="843cc-132">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/summaries HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="843cc-133">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="843cc-133">REST response</span></span>

<span data-ttu-id="843cc-134">Als dit lukt, retourneert deze methode een [**resource InvoiceSummaries**](invoice-resources.md#invoicesummaries) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="843cc-134">If successful, this method returns an [**InvoiceSummaries**](invoice-resources.md#invoicesummaries) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="843cc-135">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="843cc-135">Response success and error codes</span></span>

<span data-ttu-id="843cc-136">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="843cc-136">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="843cc-137">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="843cc-137">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="843cc-138">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="843cc-138">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="843cc-139">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="843cc-139">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 256
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
Date: Thu, 24 Mar 2016 05:21:01 GMT

{
    "totalCount": 3,
    "items": [
        {
            "balanceAmount": 751094.39,
            "currencyCode": "GBP",
            "currencySymbol": "£",
            "accountingDate": "2018-03-16T00:00:00",
            "firstInvoiceCreationDate": "2017-01-21T00:00:00Z",
            "lastPaymentDate": "2017-01-01T12:00:00Z",
            "lastPaymentAmount": 1000,
            "latestInvoiceDate": "2018-03-16T00:00:00",
            "details": [
                {
                    "invoiceType": "Recurring",
                    "summary": {
                        "balanceAmount": 202955.87,
                        "currencyCode": "GBP",
                        "currencySymbol": "£",
                        "accountingDate": "2017-02-27T00:00:00Z",
                        "firstInvoiceCreationDate": "2017-01-21T00:00:00Z",
                        "lastPaymentDate": "2017-01-01T12:00:00Z",
                        "lastPaymentAmount": 1000,
                        "latestInvoiceDate": "0001-01-01T00:00:00",
                        "attributes": {
                            "objectType": "InvoiceSummary"
                        }
                    }
                },
                {
                    "invoiceType": "OneTime",
                    "summary": {
                        "balanceAmount": 548138.52,
                        "currencyCode": "GBP",
                        "currencySymbol": "£",
                        "accountingDate": "2018-03-16T00:00:00",
                        "firstInvoiceCreationDate": "2018-03-16T00:00:00",
                        "lastPaymentDate": "0001-01-01T00:00:00",
                        "lastPaymentAmount": 0,
                        "latestInvoiceDate": "2018-03-16T00:00:00",
                        "attributes": {
                            "objectType": "InvoiceSummary"
                        }
                    }
                }
            ],
            "links": {
                "self": {
                    "uri": "/invoices/summary",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "InvoiceSummary"
            }
        },
        {
            "balanceAmount": 1230.33,
            "currencyCode": "CHF",
            "currencySymbol": "CHF",
            "accountingDate": "2018-03-16T00:00:00",
            "firstInvoiceCreationDate": "2018-03-16T00:00:00",
            "lastPaymentDate": "0001-01-01T00:00:00",
            "lastPaymentAmount": 0,
            "latestInvoiceDate": "2018-03-16T00:00:00",
            "details": [
                {
                    "invoiceType": "OneTime",
                    "summary": {
                        "balanceAmount": 1230.33,
                        "currencyCode": "CHF",
                        "currencySymbol": "CHF",
                        "accountingDate": "2018-03-16T00:00:00",
                        "firstInvoiceCreationDate": "2018-03-16T00:00:00",
                        "lastPaymentDate": "0001-01-01T00:00:00",
                        "lastPaymentAmount": 0,
                        "latestInvoiceDate": "2018-03-16T00:00:00",
                        "attributes": {
                            "objectType": "InvoiceSummary"
                        }
                    }
                }
            ],
            "links": {
                "self": {
                    "uri": "/invoices/summary",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "InvoiceSummary"
            }
        },
        {
            "balanceAmount": 1001.12,
            "currencyCode": "EUR",
            "currencySymbol": "€",
            "accountingDate": "2018-03-16T00:00:00",
            "firstInvoiceCreationDate": "2018-03-16T00:00:00",
            "lastPaymentDate": "0001-01-01T00:00:00",
            "lastPaymentAmount": 0,
            "latestInvoiceDate": "2018-03-16T00:00:00",
            "details": [
                {
                    "invoiceType": "OneTime",
                    "summary": {
                        "balanceAmount": 1001.12,
                        "currencyCode": "EUR",
                        "currencySymbol": "€",
                        "accountingDate": "2018-03-16T00:00:00",
                        "firstInvoiceCreationDate": "2018-03-16T00:00:00",
                        "lastPaymentDate": "0001-01-01T00:00:00",
                        "lastPaymentAmount": 0,
                        "latestInvoiceDate": "2018-03-16T00:00:00",
                        "attributes": {
                            "objectType": "InvoiceSummary"
                        }
                    }
                }
            ],
            "links": {
                "self": {
                    "uri": "/invoices/summary",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "InvoiceSummary"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/summaries",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
