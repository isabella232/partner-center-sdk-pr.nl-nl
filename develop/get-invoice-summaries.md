---
title: Factuuroverzichten ophalen
description: U kunt een factuur samenvattingen resource voor elk valuta type gebruiken om het saldo en de totale kosten van periodieke en eenmalige kosten weer te geven.
ms.date: 09/24/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 82cd669117db72e1819d941f48f8ea69b2eddaec
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767166"
---
# <a name="get-invoice-summaries"></a><span data-ttu-id="893fe-103">Factuuroverzichten ophalen</span><span class="sxs-lookup"><span data-stu-id="893fe-103">Get invoice summaries</span></span>

<span data-ttu-id="893fe-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="893fe-104">**Applies to:**</span></span>

- <span data-ttu-id="893fe-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="893fe-105">Partner Center</span></span>
- <span data-ttu-id="893fe-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="893fe-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="893fe-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="893fe-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="893fe-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="893fe-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="893fe-109">U kunt de **InvoiceSummaries** gebruiken om een factuur overzicht op te halen waarin het saldo en de totale kosten van periodieke en eenmalige kosten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="893fe-109">You can use the **InvoiceSummaries** to retrieve an invoice summary which shows the balance and total charges of both recurring and one-time charges.</span></span> <span data-ttu-id="893fe-110">De **InvoiceSummaries** -resource bevat een factuur overzicht voor elk valuta type.</span><span class="sxs-lookup"><span data-stu-id="893fe-110">The **InvoiceSummaries** resource contains an invoice summary for each currency type.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="893fe-111">Vereisten</span><span class="sxs-lookup"><span data-stu-id="893fe-111">Prerequisites</span></span>

- <span data-ttu-id="893fe-112">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="893fe-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="893fe-113">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="893fe-113">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="893fe-114">Een geldige factuur-ID.</span><span class="sxs-lookup"><span data-stu-id="893fe-114">A valid invoice identifier.</span></span>

## <a name="c"></a><span data-ttu-id="893fe-115">C\#</span><span class="sxs-lookup"><span data-stu-id="893fe-115">C\#</span></span>

<span data-ttu-id="893fe-116">Ophalen van een [**InvoiceSummaries**](invoice-resources.md#invoicesummaries) -verzameling die een [**InvoiceSummary**](invoice-resources.md#invoicesummary) bevat voor elk valuta type:</span><span class="sxs-lookup"><span data-stu-id="893fe-116">To retrieve an [**InvoiceSummaries**](invoice-resources.md#invoicesummaries) collection that contains an [**InvoiceSummary**](invoice-resources.md#invoicesummary) for each currency type:</span></span>

1. <span data-ttu-id="893fe-117">Gebruik de verzameling **IAggregatePartner. facturen** om de eigenschap **samen vattingen** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="893fe-117">Use your **IAggregatePartner.Invoices** collection to call the **Summaries** property.</span></span>

2. <span data-ttu-id="893fe-118">Roep de methode **Get () aan** .</span><span class="sxs-lookup"><span data-stu-id="893fe-118">Call the **Get()** method.</span></span>
3. <span data-ttu-id="893fe-119">Als u het saldo van een afzonderlijke [**InvoiceSummary**](invoice-resources.md#invoicesummary)wilt weer geven, opent u de eigenschap **BalanceAmount** voor dat lid van de verzameling.</span><span class="sxs-lookup"><span data-stu-id="893fe-119">To get the balance of an individual [**InvoiceSummary**](invoice-resources.md#invoicesummary), access the **BalanceAmount** property for that member of the collection.</span></span>

``` csharp
// IAggregatePartner scopedPartnerOperations;

// Get the invoice summaries collection.
var invoiceSummaries = scopedPartnerOperations.Invoices.Summaries.Get();

// Display the balance on the first invoice summary in the collection.
Console.Out.WriteLine("Current Account Balance:  {0:C}", invoiceSummaries[0].BalanceAmount);
```

<span data-ttu-id="893fe-120">Zie de volgende voorbeeld code voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="893fe-120">For more information, see the following example code:</span></span>

- <span data-ttu-id="893fe-121">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="893fe-121">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="893fe-122">Project: **PartnerSDK. FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="893fe-122">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="893fe-123">Klasse: **GetInvoiceSummaries.cs**</span><span class="sxs-lookup"><span data-stu-id="893fe-123">Class: **GetInvoiceSummaries.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="893fe-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="893fe-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="893fe-125">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="893fe-125">Request syntax</span></span>

| <span data-ttu-id="893fe-126">Methode</span><span class="sxs-lookup"><span data-stu-id="893fe-126">Method</span></span>  | <span data-ttu-id="893fe-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="893fe-127">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="893fe-128">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="893fe-128">**GET**</span></span> | <span data-ttu-id="893fe-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/summaries http/1.1</span><span class="sxs-lookup"><span data-stu-id="893fe-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/summaries HTTP/1.1</span></span>     |

#### <a name="uri-parameter"></a><span data-ttu-id="893fe-130">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="893fe-130">URI parameter</span></span>

<span data-ttu-id="893fe-131">Geen.</span><span class="sxs-lookup"><span data-stu-id="893fe-131">None.</span></span>

### <a name="request-headers"></a><span data-ttu-id="893fe-132">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="893fe-132">Request headers</span></span>

<span data-ttu-id="893fe-133">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="893fe-133">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="893fe-134">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="893fe-134">Request body</span></span>

<span data-ttu-id="893fe-135">Geen.</span><span class="sxs-lookup"><span data-stu-id="893fe-135">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="893fe-136">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="893fe-136">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/summaries HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="893fe-137">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="893fe-137">REST response</span></span>

<span data-ttu-id="893fe-138">Als dit lukt, retourneert deze methode een [**InvoiceSummaries**](invoice-resources.md#invoicesummaries) -resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="893fe-138">If successful, this method returns an [**InvoiceSummaries**](invoice-resources.md#invoicesummaries) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="893fe-139">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="893fe-139">Response success and error codes</span></span>

<span data-ttu-id="893fe-140">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="893fe-140">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="893fe-141">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="893fe-141">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="893fe-142">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="893fe-142">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="893fe-143">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="893fe-143">Response example</span></span>

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
