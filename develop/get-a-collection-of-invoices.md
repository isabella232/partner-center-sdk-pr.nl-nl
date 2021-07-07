---
title: Een verzameling facturen ophalen
description: Een verzameling van de facturen van de partner ophalen.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: 7698d85df3341ae4cbff0377bd0a1bb47cd36740
ms.sourcegitcommit: d20e7d572fee09a83a4b23a92da7ff09cfebe75a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111906439"
---
# <a name="get-a-collection-of-invoices"></a><span data-ttu-id="0248d-103">Een verzameling facturen ophalen</span><span class="sxs-lookup"><span data-stu-id="0248d-103">Get a collection of invoices</span></span>

<span data-ttu-id="0248d-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="0248d-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="0248d-105">Een verzameling van de facturen van de partner ophalen.</span><span class="sxs-lookup"><span data-stu-id="0248d-105">How to retrieve a collection of the partner's invoices.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0248d-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0248d-106">Prerequisites</span></span>

- <span data-ttu-id="0248d-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0248d-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="0248d-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="0248d-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="0248d-109">C\#</span><span class="sxs-lookup"><span data-stu-id="0248d-109">C\#</span></span>

<span data-ttu-id="0248d-110">Als u een verzameling van alle beschikbare facturen wilt ophalen, gebruikt u de eigenschap [**Facturen**](/dotnet/api/microsoft.store.partnercenter.ipartner.invoices) om een interface voor factuurbewerkingen op te halen en roept u vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.getasync) aan om de verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="0248d-110">To get a collection of all available invoices, use the [**Invoices**](/dotnet/api/microsoft.store.partnercenter.ipartner.invoices) property to get an interface to invoice operations, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.getasync) method to retrieve the collection.</span></span>

<span data-ttu-id="0248d-111">Als u een verzameling facturen met pagina's wilt ophalen, roept u eerst de [**methode BuildIndexedQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery) aan en geef deze de paginagrootte door om een [**IQuery-object te**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) maken.</span><span class="sxs-lookup"><span data-stu-id="0248d-111">To get a paged collection of invoices, first call the [**BuildIndexedQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery) method and pass it the page size to create an [**IQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) object.</span></span> <span data-ttu-id="0248d-112">Gebruik vervolgens de eigenschap [**Facturen**](/dotnet/api/microsoft.store.partnercenter.ipartner.invoices) om een interface voor factuurbewerkingen op te halen en geef vervolgens het IQuery-object door aan de [**query-**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.query) of [**QueryAsync-methode**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.queryasync) om de aanvraag te verzenden en de eerste pagina op te halen.</span><span class="sxs-lookup"><span data-stu-id="0248d-112">Next, use the [**Invoices**](/dotnet/api/microsoft.store.partnercenter.ipartner.invoices) property to get an interface to invoice operations, and then pass the IQuery object to the [**Query**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.query) or [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.queryasync) method to send the request and get the first page.</span></span>

<span data-ttu-id="0248d-113">Gebruik vervolgens de eigenschap [**Enumerators**](/dotnet/api/microsoft.store.partnercenter.ipartner.enumerators) om een interface op te halen voor de verzameling ondersteunde enumerators voor resourceverzamelingen en roep vervolgens [**Invoices.Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) aan om een enumerator te maken voor het doorlopen van de verzameling facturen.</span><span class="sxs-lookup"><span data-stu-id="0248d-113">Next, use the [**Enumerators**](/dotnet/api/microsoft.store.partnercenter.ipartner.enumerators) property to get an interface to the collection of supported resource collection enumerators, and then call [**Invoices.Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) to create an enumerator for traversing the collection of invoices.</span></span> <span data-ttu-id="0248d-114">Gebruik ten slotte de -enumerator om elke pagina met facturen op te halen en te gebruiken, zoals wordt weergegeven in het volgende codevoorbeeld.</span><span class="sxs-lookup"><span data-stu-id="0248d-114">Finally, use the enumerator to retrieve and work with each page of invoices as shown in the following code example.</span></span> <span data-ttu-id="0248d-115">Elke aanroep van de [**methode Next**](/dotnet/api/microsoft.store.partnercenter.enumerators.iresourcecollectionenumerator-1.next) verzendt een aanvraag voor de volgende pagina met facturen op basis van de paginagrootte.</span><span class="sxs-lookup"><span data-stu-id="0248d-115">Each call to the [**Next**](/dotnet/api/microsoft.store.partnercenter.enumerators.iresourcecollectionenumerator-1.next) method sends a request for the next page of invoices based on the page size.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// int invoicePageSize;

// Is this an unpaged or paged request?
bool isUnpaged = (this.invoicePageSize <= 0);

// If the scenario is unpaged, get all the invoices, otherwise get the first page.
var invoicesPage = (isUnpaged)
                 ? partnerOperations.Invoices.Get()
                 : partnerOperations.Invoices.Query(QueryFactory.Instance.BuildIndexedQuery(this.invoicePageSize));

// Create an invoice enumerator for traversing the invoice pages.
var invoicesEnumerator = partnerOperations.Enumerators.Invoices.Create(invoicesPage);
int lineCounter = 1;

while (invoicesEnumerator.HasValue)
{
    // Print the current invoice results page.
    var invoices = invoicesEnumerator.Current.Items;

    foreach (var i in invoices)
    {
        Console.WriteLine(String.Format("{0,3}. {1}  {2}  {3,16:C2}",
            lineCounter++,
            i.Id,
            i.InvoiceDate.ToString("yyyy&#39;-&#39;MM&#39;-&#39;dd&#39;T&#39;HH&#39;:&#39;mm&#39;:&#39;ss&#39;Z&#39;"),
            i.TotalCharges));
    }

    Console.WriteLine();
    Console.Write("Press any key to retrieve the next invoices page");
    Console.ReadKey();

    // Get the next page of invoices.
    invoicesEnumerator.Next();
}
```

<span data-ttu-id="0248d-116">Zie Sample **:** Console test app (Voorbeeld: [consoletest-app) voor](console-test-app.md)een iets ander voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="0248d-116">For a slightly different example, see **Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="0248d-117">**Project**: Partnercentrum-SDK Samples **Class**: GetPagedInvoices.cs</span><span class="sxs-lookup"><span data-stu-id="0248d-117">**Project**: Partner Center SDK Samples **Class**: GetPagedInvoices.cs</span></span>

> [!NOTE] 
> <span data-ttu-id="0248d-118">Dezelfde API wordt gebruikt voor alle moderne commerciële aankopen, evenals 145p- en Office licenties.</span><span class="sxs-lookup"><span data-stu-id="0248d-118">The same API is used for all modern commercial purchases as well as 145p and Office licenses.</span></span> <span data-ttu-id="0248d-119">Grootte en offset worden alleen in aanmerking genomen voor verouderde facturen.</span><span class="sxs-lookup"><span data-stu-id="0248d-119">Size and offset are only considered for legacy invoices.</span></span> <span data-ttu-id="0248d-120">Voor alle moderne commerciële aankopen worden pagina's & offset genegeerd.</span><span class="sxs-lookup"><span data-stu-id="0248d-120">For all modern commercial purchases, pagesize & offset will be ignored.</span></span>

## <a name="rest-request"></a><span data-ttu-id="0248d-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="0248d-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0248d-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="0248d-122">Request syntax</span></span>

| <span data-ttu-id="0248d-123">Methode</span><span class="sxs-lookup"><span data-stu-id="0248d-123">Method</span></span>  | <span data-ttu-id="0248d-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="0248d-124">Request URI</span></span>                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="0248d-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="0248d-125">**GET**</span></span> | <span data-ttu-id="0248d-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices?size={size}&offset={offset} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="0248d-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices?size={size}&offset={offset} HTTP/1.1</span></span>  |

### <a name="uri-parameters"></a><span data-ttu-id="0248d-127">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="0248d-127">URI parameters</span></span>

<span data-ttu-id="0248d-128">Gebruik de volgende queryparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="0248d-128">Use the following query parameters when creating the request.</span></span>

| <span data-ttu-id="0248d-129">Naam</span><span class="sxs-lookup"><span data-stu-id="0248d-129">Name</span></span>   | <span data-ttu-id="0248d-130">Type</span><span class="sxs-lookup"><span data-stu-id="0248d-130">Type</span></span> | <span data-ttu-id="0248d-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="0248d-131">Required</span></span> | <span data-ttu-id="0248d-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0248d-132">Description</span></span>                                                                            |
|--------|------|----------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="0248d-133">grootte</span><span class="sxs-lookup"><span data-stu-id="0248d-133">size</span></span>   | <span data-ttu-id="0248d-134">int</span><span class="sxs-lookup"><span data-stu-id="0248d-134">int</span></span>  | <span data-ttu-id="0248d-135">Nee</span><span class="sxs-lookup"><span data-stu-id="0248d-135">No</span></span>       | <span data-ttu-id="0248d-136">Het aantal factuurresources dat in het antwoord moet worden retourneerd.</span><span class="sxs-lookup"><span data-stu-id="0248d-136">The number of invoice resources to return in the response.</span></span> <span data-ttu-id="0248d-137">Deze parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="0248d-137">This parameter is optional.</span></span> |
| <span data-ttu-id="0248d-138">offset</span><span class="sxs-lookup"><span data-stu-id="0248d-138">offset</span></span> | <span data-ttu-id="0248d-139">int</span><span class="sxs-lookup"><span data-stu-id="0248d-139">int</span></span>  | <span data-ttu-id="0248d-140">Nee</span><span class="sxs-lookup"><span data-stu-id="0248d-140">No</span></span>       | <span data-ttu-id="0248d-141">De op nul gebaseerde index van de eerste factuur die moet worden teruggefactureerd.</span><span class="sxs-lookup"><span data-stu-id="0248d-141">The zero-based index of the first invoice to return.</span></span>                                   |

### <a name="request-headers"></a><span data-ttu-id="0248d-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="0248d-142">Request headers</span></span>

<span data-ttu-id="0248d-143">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="0248d-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="0248d-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="0248d-144">Request body</span></span>

<span data-ttu-id="0248d-145">Geen</span><span class="sxs-lookup"><span data-stu-id="0248d-145">None</span></span>

### <a name="request-example"></a><span data-ttu-id="0248d-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="0248d-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices?size=200&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="0248d-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="0248d-147">REST response</span></span>

<span data-ttu-id="0248d-148">Als dit lukt, bevat de antwoord-body de verzameling [factuurresources.](invoice-resources.md#invoice)</span><span class="sxs-lookup"><span data-stu-id="0248d-148">If successful, the response body contains the collection of [Invoice](invoice-resources.md#invoice) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0248d-149">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="0248d-149">Response success and error codes</span></span>

<span data-ttu-id="0248d-150">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="0248d-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0248d-151">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="0248d-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0248d-152">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="0248d-152">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="0248d-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="0248d-153">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 256
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57eb2ca7-755f-450f-9187-eae1e75a0114
MS-RequestId: a45e6643-1caf-4429-8f90-07c03d85bc2b
Date: Thu, 24 Mar 2016 05:21:01 GMT
{
    "totalCount": 2,
    "items": [
        {
            "id": "D02005YFHI",
            "invoiceDate": "2017-01-21T00:00:00Z",
            "totalCharges": 24606.35,
            "paidAmount": 1000,
            "currencyCode": "GBP",
            "currencySymbol": "£",
            "pdfDownloadLink": "/invoices/D02005YFHI/documents/statement",
            "taxReceipts": [
                {
                    "id": "123456",
                    "taxReceiptPdfDownloadLink": "/invoices/D02005YFHI/receipts/123456/documents/statement"
                }
            ],
            "invoiceDetails": [
                {
                    "invoiceLineItemType": "billing_line_items",
                    "billingProvider": "office",
                    "links": {
                        "self": {
                            "uri": "/invoices/Recurring-D02005YFHI/lineitems/Office/BillingLineItems",
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
            "invoiceType": "Recurring",
            "links": {
                "self": {
                    "uri": "/invoices/Recurring-D02005YFHI",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Invoice"
            }
        },
        {
            "id": "G000024130",
            "invoiceDate": "2018-02-08T01:22:47.603895Z",
            "totalCharges": 586366,
            "paidAmount": 0,
            "currencyCode": "CHF",
            "currencySymbol": "CHF",
            "pdfDownloadLink": "/invoices/G000024130/documents/statement",
            "taxReceipts": [
                {
                    "id": "234567",
                    "taxReceiptPdfDownloadLink": "/invoices/G000024130/receipts/234567/documents/statement"
                }
            ],
            "invoiceDetails": [
                {
                    "invoiceLineItemType": "billing_line_items",
                    "billingProvider": "one_time",
                    "links": {
                        "self": {
                            "uri": "/invoices/OneTime-G000024130/lineitems/OneTime/BillingLineItems",
                            "method": "GET",
                            "headers": []
                        }
                    },
                    "attributes": {
                        "objectType": "InvoiceDetail"
                    }
                }
            ],
            "amendments": [
                {
                    "id": "G000024131",
                    "invoiceDate": "2018-02-08T18:44:37.5381456Z",
                    "totalCharges": 107661.12,
                    "paidAmount": 0,
                    "currencyCode": "CHF",
                    "currencySymbol": "CHF",
                    "invoiceDetails": [
                        {
                            "invoiceLineItemType": "billing_line_items",
                            "billingProvider": "one_time",
                            "attributes": {
                                "objectType": "InvoiceDetail"
                            }
                        }
                    ],
                    "documentType": "adjustment_note",
                    "amendsOf": "G000024130",
                    "invoiceType": "OneTime",
                    "attributes": {
                        "objectType": "Invoice"
                    }
                }
            ],
            "documentType": "void_note",
            "invoiceType": "OneTime",
            "links": {
                "self": {
                    "uri": "/invoices/OneTime-G000024130",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Invoice"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices?size=2&offset=0",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices?size=2&offset=2",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
