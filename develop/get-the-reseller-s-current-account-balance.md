---
title: Het huidige accountsaldo van de partner ophalen
description: Haalt het huidige account saldo van de partner op. Een samen vatting van het saldo en de totale kosten van een factuur voor zowel terugkerende als eenmalige kosten.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 110da433faa6ff4d3d068c6d68a6f497f4a2721a
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767276"
---
# <a name="get-the-partners-current-account-balance"></a><span data-ttu-id="93943-104">Het huidige accountsaldo van de partner ophalen</span><span class="sxs-lookup"><span data-stu-id="93943-104">Get the partner's current account balance</span></span>

<span data-ttu-id="93943-105">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="93943-105">**Applies To**</span></span>

- <span data-ttu-id="93943-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="93943-106">Partner Center</span></span>
- <span data-ttu-id="93943-107">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="93943-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="93943-108">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="93943-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="93943-109">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="93943-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="93943-110">Haalt het huidige account saldo van de partner op.</span><span class="sxs-lookup"><span data-stu-id="93943-110">Retrieves the partner's current account balance.</span></span> <span data-ttu-id="93943-111">Een samen vatting van het saldo en de totale kosten van een factuur voor zowel terugkerende als eenmalige kosten.</span><span class="sxs-lookup"><span data-stu-id="93943-111">A summary of the balance and total charges of an invoice for both recurring and one-time charges.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="93943-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="93943-112">Prerequisites</span></span>

- <span data-ttu-id="93943-113">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="93943-113">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="93943-114">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="93943-114">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="93943-115">C\#</span><span class="sxs-lookup"><span data-stu-id="93943-115">C\#</span></span>

<span data-ttu-id="93943-116">Als u uw account saldo wilt ophalen, gebruikt u de verzameling **IAggregatePartner. facturen** en roept u de **samenvattings** eigenschap aan.</span><span class="sxs-lookup"><span data-stu-id="93943-116">To retrieve your account balance, use your **IAggregatePartner.Invoices** collection, and then call the **Summary** property.</span></span> <span data-ttu-id="93943-117">Roep vervolgens de **Get** -functie aan en roep uiteindelijk de eigenschap **BalanceAmount** aan.</span><span class="sxs-lookup"><span data-stu-id="93943-117">Then call the **Get** function, and finally call the **BalanceAmount** property.</span></span>

``` csharp
// IAggregatePartner scopedPartnerOperations;

var invoiceSummary = scopedPartnerOperations.Invoices.Summary.Get();

Console.Out.WriteLine("Current Account Balance:  {0:C}", invoiceSummary.BalanceAmount);
```

<span data-ttu-id="93943-118">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="93943-118">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="93943-119">**Project**: PartnerSDK. FeatureSample- **klasse**: GetInvoiceSummary.cs</span><span class="sxs-lookup"><span data-stu-id="93943-119">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoiceSummary.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="93943-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="93943-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="93943-121">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="93943-121">Request syntax</span></span>

| <span data-ttu-id="93943-122">Methode</span><span class="sxs-lookup"><span data-stu-id="93943-122">Method</span></span>  | <span data-ttu-id="93943-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="93943-123">Request URI</span></span>                                                              |
|---------|--------------------------------------------------------------------------|
| <span data-ttu-id="93943-124">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="93943-124">**GET**</span></span> | <span data-ttu-id="93943-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/Summary http/1.1</span><span class="sxs-lookup"><span data-stu-id="93943-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/summary HTTP/1.1</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="93943-126">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="93943-126">Request headers</span></span>

<span data-ttu-id="93943-127">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="93943-127">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="93943-128">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="93943-128">Request body</span></span>

<span data-ttu-id="93943-129">Geen</span><span class="sxs-lookup"><span data-stu-id="93943-129">None</span></span>

### <a name="request-example"></a><span data-ttu-id="93943-130">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="93943-130">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/summary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="93943-131">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="93943-131">REST response</span></span>

<span data-ttu-id="93943-132">Als dit lukt, retourneert deze methode een [InvoiceSummary](invoice-resources.md#invoicesummary) -resource in het antwoord.</span><span class="sxs-lookup"><span data-stu-id="93943-132">If successful, this method returns an [InvoiceSummary](invoice-resources.md#invoicesummary) resource in the response.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="93943-133">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="93943-133">Response success and error codes</span></span>

<span data-ttu-id="93943-134">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="93943-134">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="93943-135">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="93943-135">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="93943-136">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="93943-136">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="93943-137">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="93943-137">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 256
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
Date: Thu, 24 Mar 2016 05:21:01 GMT

{
    "balanceAmount": 751094.39,
    "currencyCode": "USD",
    "currencySymbol": "$",
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
                "currencyCode": "USD",
                "currencySymbol": "$",
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
                "currencyCode": "USD",
                "currencySymbol": "$",
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
```
