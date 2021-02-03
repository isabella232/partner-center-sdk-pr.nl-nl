---
title: Een verzameling facturen ophalen
description: Het ophalen van een verzameling van de facturen van de partner.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: f56c3de8dd227f573921e5b969c2217c2f743a21
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767357"
---
# <a name="get-a-collection-of-invoices"></a><span data-ttu-id="d39bd-103">Een verzameling facturen ophalen</span><span class="sxs-lookup"><span data-stu-id="d39bd-103">Get a collection of invoices</span></span>

<span data-ttu-id="d39bd-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="d39bd-104">**Applies To**</span></span>

- <span data-ttu-id="d39bd-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="d39bd-105">Partner Center</span></span>
- <span data-ttu-id="d39bd-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="d39bd-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="d39bd-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="d39bd-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="d39bd-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d39bd-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d39bd-109">Het ophalen van een verzameling van de facturen van de partner.</span><span class="sxs-lookup"><span data-stu-id="d39bd-109">How to retrieve a collection of the partner's invoices.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d39bd-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d39bd-110">Prerequisites</span></span>

- <span data-ttu-id="d39bd-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d39bd-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d39bd-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="d39bd-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="d39bd-113">C\#</span><span class="sxs-lookup"><span data-stu-id="d39bd-113">C\#</span></span>

<span data-ttu-id="d39bd-114">Als u een verzameling van alle beschik bare facturen wilt ophalen, gebruikt u de eigenschap [**facturen**](/dotnet/api/microsoft.store.partnercenter.ipartner.invoices) om een interface te ontvangen voor het factureren van bewerkingen en roept u vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.getasync) aan om de verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="d39bd-114">To get a collection of all available invoices, use the [**Invoices**](/dotnet/api/microsoft.store.partnercenter.ipartner.invoices) property to get an interface to invoice operations, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.getasync) method to retrieve the collection.</span></span>

<span data-ttu-id="d39bd-115">Als u een verzameling facturen wilt ontvangen, roept u eerst de [**BuildIndexedQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery) -methode aan en geeft u de pagina grootte door om een [**IQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) -object te maken.</span><span class="sxs-lookup"><span data-stu-id="d39bd-115">To get a paged collection of invoices, first call the [**BuildIndexedQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery) method and pass it the page size to create an [**IQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) object.</span></span> <span data-ttu-id="d39bd-116">Gebruik vervolgens [**de eigenschap**](/dotnet/api/microsoft.store.partnercenter.ipartner.invoices) invoices om een interface op te halen voor het factureren van bewerkingen en geef vervolgens het IQuery-object door aan de [**query**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.query) -of [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.queryasync) -methode om de aanvraag te verzenden en de eerste pagina op te halen.</span><span class="sxs-lookup"><span data-stu-id="d39bd-116">Next, use the [**Invoices**](/dotnet/api/microsoft.store.partnercenter.ipartner.invoices) property to get an interface to invoice operations, and then pass the IQuery object to the [**Query**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.query) or [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.queryasync) method to send the request and get the first page.</span></span>

<span data-ttu-id="d39bd-117">Gebruik vervolgens de [**opsommings**](/dotnet/api/microsoft.store.partnercenter.ipartner.enumerators) eigenschap om een interface op te halen voor het verzamelen van ondersteunde resource verzameling-inventarisaties en roep vervolgens [**facturen aan. Maak**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) een enumerator voor het door lopen van het verzamelen van facturen.</span><span class="sxs-lookup"><span data-stu-id="d39bd-117">Next, use the [**Enumerators**](/dotnet/api/microsoft.store.partnercenter.ipartner.enumerators) property to get an interface to the collection of supported resource collection enumerators, and then call [**Invoices.Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) to create an enumerator for traversing the collection of invoices.</span></span> <span data-ttu-id="d39bd-118">Ten slotte gebruikt u de enumerator om elke pagina met facturen op te halen en ermee te werken, zoals wordt weer gegeven in het volgende code voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="d39bd-118">Finally, use the enumerator to retrieve and work with each page of invoices as shown in the following code example.</span></span> <span data-ttu-id="d39bd-119">Elke aanroep van de [**volgende**](/dotnet/api/microsoft.store.partnercenter.enumerators.iresourcecollectionenumerator-1.next) -methode verzendt een aanvraag voor de volgende pagina met facturen op basis van de pagina grootte.</span><span class="sxs-lookup"><span data-stu-id="d39bd-119">Each call to the [**Next**](/dotnet/api/microsoft.store.partnercenter.enumerators.iresourcecollectionenumerator-1.next) method sends a request for the next page of invoices based on the page size.</span></span>

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

<span data-ttu-id="d39bd-120">**Zie voor beeld:** [console test-app](console-test-app.md)voor een iets ander voor beeld.</span><span class="sxs-lookup"><span data-stu-id="d39bd-120">For a slightly different example, see **Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="d39bd-121">**Project**: Partner Center SDK-voor beelden **klasse**: GetPagedInvoices.cs</span><span class="sxs-lookup"><span data-stu-id="d39bd-121">**Project**: Partner Center SDK Samples **Class**: GetPagedInvoices.cs</span></span>

> [!NOTE] 
> <span data-ttu-id="d39bd-122">Dezelfde API wordt gebruikt voor alle moderne commerciële aankopen, evenals 145p-en Office-licenties.</span><span class="sxs-lookup"><span data-stu-id="d39bd-122">The same API is used for all modern commercial purchases as well as 145p and Office licenses.</span></span> <span data-ttu-id="d39bd-123">Grootte en verschuiving worden alleen overwogen voor verouderde facturen.</span><span class="sxs-lookup"><span data-stu-id="d39bd-123">Size and offset are only considered for legacy invoices.</span></span> <span data-ttu-id="d39bd-124">Voor alle moderne commerciële aankopen wordt PageSize & Offset genegeerd.</span><span class="sxs-lookup"><span data-stu-id="d39bd-124">For all modern commercial purchases, pagesize & offset will be ignored.</span></span>

## <a name="rest-request"></a><span data-ttu-id="d39bd-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="d39bd-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d39bd-126">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d39bd-126">Request syntax</span></span>

| <span data-ttu-id="d39bd-127">Methode</span><span class="sxs-lookup"><span data-stu-id="d39bd-127">Method</span></span>  | <span data-ttu-id="d39bd-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="d39bd-128">Request URI</span></span>                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="d39bd-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="d39bd-129">**GET**</span></span> | <span data-ttu-id="d39bd-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices? grootte = {size} &offset = {offset} http/1.1</span><span class="sxs-lookup"><span data-stu-id="d39bd-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices?size={size}&offset={offset} HTTP/1.1</span></span>  |

### <a name="uri-parameters"></a><span data-ttu-id="d39bd-131">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="d39bd-131">URI parameters</span></span>

<span data-ttu-id="d39bd-132">Gebruik de volgende query parameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="d39bd-132">Use the following query parameters when creating the request.</span></span>

| <span data-ttu-id="d39bd-133">Naam</span><span class="sxs-lookup"><span data-stu-id="d39bd-133">Name</span></span>   | <span data-ttu-id="d39bd-134">Type</span><span class="sxs-lookup"><span data-stu-id="d39bd-134">Type</span></span> | <span data-ttu-id="d39bd-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="d39bd-135">Required</span></span> | <span data-ttu-id="d39bd-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d39bd-136">Description</span></span>                                                                            |
|--------|------|----------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="d39bd-137">grootte</span><span class="sxs-lookup"><span data-stu-id="d39bd-137">size</span></span>   | <span data-ttu-id="d39bd-138">int</span><span class="sxs-lookup"><span data-stu-id="d39bd-138">int</span></span>  | <span data-ttu-id="d39bd-139">No</span><span class="sxs-lookup"><span data-stu-id="d39bd-139">No</span></span>       | <span data-ttu-id="d39bd-140">Het aantal factuur resources dat moet worden geretourneerd in het antwoord.</span><span class="sxs-lookup"><span data-stu-id="d39bd-140">The number of invoice resources to return in the response.</span></span> <span data-ttu-id="d39bd-141">Deze parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="d39bd-141">This parameter is optional.</span></span> |
| <span data-ttu-id="d39bd-142">offset</span><span class="sxs-lookup"><span data-stu-id="d39bd-142">offset</span></span> | <span data-ttu-id="d39bd-143">int</span><span class="sxs-lookup"><span data-stu-id="d39bd-143">int</span></span>  | <span data-ttu-id="d39bd-144">No</span><span class="sxs-lookup"><span data-stu-id="d39bd-144">No</span></span>       | <span data-ttu-id="d39bd-145">De op nul gebaseerde index van de eerste factuur die moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d39bd-145">The zero-based index of the first invoice to return.</span></span>                                   |

### <a name="request-headers"></a><span data-ttu-id="d39bd-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="d39bd-146">Request headers</span></span>

<span data-ttu-id="d39bd-147">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d39bd-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d39bd-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="d39bd-148">Request body</span></span>

<span data-ttu-id="d39bd-149">Geen</span><span class="sxs-lookup"><span data-stu-id="d39bd-149">None</span></span>

### <a name="request-example"></a><span data-ttu-id="d39bd-150">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d39bd-150">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="d39bd-151">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="d39bd-151">REST response</span></span>

<span data-ttu-id="d39bd-152">Als dit lukt, bevat de antwoord tekst de verzameling van [factuur](invoice-resources.md#invoice) resources.</span><span class="sxs-lookup"><span data-stu-id="d39bd-152">If successful, the response body contains the collection of [Invoice](invoice-resources.md#invoice) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d39bd-153">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="d39bd-153">Response success and error codes</span></span>

<span data-ttu-id="d39bd-154">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="d39bd-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d39bd-155">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="d39bd-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d39bd-156">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="d39bd-156">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d39bd-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="d39bd-157">Response example</span></span>

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
