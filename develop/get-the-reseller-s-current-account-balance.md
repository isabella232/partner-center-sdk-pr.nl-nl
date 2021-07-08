---
title: Het huidige accountsaldo van de partner ophalen
description: Hiermee wordt het huidige rekeningsaldo van de partner opgehaald. Een overzicht van het saldo en de totale kosten van een factuur voor zowel terugkerende als eenmalige kosten.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a04ab63482ec9d06e2fe47d2b6ce1bc6a5fd5f27
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548495"
---
# <a name="get-the-partners-current-account-balance"></a><span data-ttu-id="05a29-104">Het huidige accountsaldo van de partner ophalen</span><span class="sxs-lookup"><span data-stu-id="05a29-104">Get the partner's current account balance</span></span>

<span data-ttu-id="05a29-105">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="05a29-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="05a29-106">Hiermee wordt het huidige rekeningsaldo van de partner opgehaald.</span><span class="sxs-lookup"><span data-stu-id="05a29-106">Retrieves the partner's current account balance.</span></span> <span data-ttu-id="05a29-107">Een overzicht van het saldo en de totale kosten van een factuur voor zowel terugkerende als eenmalige kosten.</span><span class="sxs-lookup"><span data-stu-id="05a29-107">A summary of the balance and total charges of an invoice for both recurring and one-time charges.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="05a29-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="05a29-108">Prerequisites</span></span>

- <span data-ttu-id="05a29-109">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="05a29-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="05a29-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="05a29-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="05a29-111">C\#</span><span class="sxs-lookup"><span data-stu-id="05a29-111">C\#</span></span>

<span data-ttu-id="05a29-112">Als u het saldo van uw account wilt ophalen, gebruikt u de **verzameling IAggregatePartner.Invoices** en roept u vervolgens de eigenschap **Samenvatting** aan.</span><span class="sxs-lookup"><span data-stu-id="05a29-112">To retrieve your account balance, use your **IAggregatePartner.Invoices** collection, and then call the **Summary** property.</span></span> <span data-ttu-id="05a29-113">Roep vervolgens de **functie Get** aan en roep ten slotte de eigenschap **BalanceAmount** aan.</span><span class="sxs-lookup"><span data-stu-id="05a29-113">Then call the **Get** function, and finally call the **BalanceAmount** property.</span></span>

``` csharp
// IAggregatePartner scopedPartnerOperations;

var invoiceSummary = scopedPartnerOperations.Invoices.Summary.Get();

Console.Out.WriteLine("Current Account Balance:  {0:C}", invoiceSummary.BalanceAmount);
```

<span data-ttu-id="05a29-114">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="05a29-114">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="05a29-115">**Project**: PartnerSDK.FeatureSample-klasse: GetInvoiceSummary.cs </span><span class="sxs-lookup"><span data-stu-id="05a29-115">**Project**: PartnerSDK.FeatureSample **Class**: GetInvoiceSummary.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="05a29-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="05a29-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="05a29-117">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="05a29-117">Request syntax</span></span>

| <span data-ttu-id="05a29-118">Methode</span><span class="sxs-lookup"><span data-stu-id="05a29-118">Method</span></span>  | <span data-ttu-id="05a29-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="05a29-119">Request URI</span></span>                                                              |
|---------|--------------------------------------------------------------------------|
| <span data-ttu-id="05a29-120">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="05a29-120">**GET**</span></span> | <span data-ttu-id="05a29-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/summary HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="05a29-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/summary HTTP/1.1</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="05a29-122">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="05a29-122">Request headers</span></span>

<span data-ttu-id="05a29-123">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="05a29-123">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="05a29-124">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="05a29-124">Request body</span></span>

<span data-ttu-id="05a29-125">Geen</span><span class="sxs-lookup"><span data-stu-id="05a29-125">None</span></span>

### <a name="request-example"></a><span data-ttu-id="05a29-126">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="05a29-126">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/summary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="05a29-127">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="05a29-127">REST response</span></span>

<span data-ttu-id="05a29-128">Als dit lukt, retourneert deze methode een [InvoiceSummary-resource](invoice-resources.md#invoicesummary) in het antwoord.</span><span class="sxs-lookup"><span data-stu-id="05a29-128">If successful, this method returns an [InvoiceSummary](invoice-resources.md#invoicesummary) resource in the response.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="05a29-129">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="05a29-129">Response success and error codes</span></span>

<span data-ttu-id="05a29-130">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="05a29-130">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="05a29-131">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="05a29-131">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="05a29-132">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="05a29-132">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="05a29-133">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="05a29-133">Response example</span></span>

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
