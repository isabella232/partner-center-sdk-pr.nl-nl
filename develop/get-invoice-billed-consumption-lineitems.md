---
title: Factuur gefactureerde commerciële verbruiks regel items ophalen
description: U kunt een verzameling met de Api's van het partner centrum voor een opgegeven factuur ophalen met behulp van de partners van het factuur regel item voor de prijs van een commerciële verbruik (afgesloten dagelijks beoordeeld artikel).
ms.date: 01/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 1e19792da6a7510bf02dd11b3e77f40a8365be2b
ms.sourcegitcommit: 4ec053c56fd210b174fe657aa7b86faf4e2b5a7c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/29/2021
ms.locfileid: "105730192"
---
# <a name="get-invoice-billed-commercial-consumption-line-items"></a><span data-ttu-id="22846-103">Factuur gefactureerde commerciële verbruiks regel items ophalen</span><span class="sxs-lookup"><span data-stu-id="22846-103">Get invoice billed commercial consumption line items</span></span>

<span data-ttu-id="22846-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="22846-104">**Applies to:**</span></span>

- <span data-ttu-id="22846-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="22846-105">Partner Center</span></span>

<span data-ttu-id="22846-106">U kunt de volgende methoden gebruiken om een verzameling details te verkrijgen voor de factuur regel items voor commerciële consumptie (ook wel gesloten dagelijkse gebruiks regel items genoemd) voor een opgegeven factuur.</span><span class="sxs-lookup"><span data-stu-id="22846-106">You can use the following methods to get a collection of details for commercial consumption invoice line items (also known as closed daily rated usage line items) for a specified invoice.</span></span>

<span data-ttu-id="22846-107">Deze API biedt ook ondersteuning voor **Azure** -provider typen voor Microsoft Azure (MS-AZR-0145P)-abonnementen.</span><span class="sxs-lookup"><span data-stu-id="22846-107">This API also supports **azure** provider types for Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span> <span data-ttu-id="22846-108">Dit betekent dat deze API een neerwaarts compatibele functie is.</span><span class="sxs-lookup"><span data-stu-id="22846-108">This means this API is a backward-compatible feature.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="22846-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="22846-109">Prerequisites</span></span>

- <span data-ttu-id="22846-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="22846-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="22846-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="22846-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="22846-112">Een factuur-ID.</span><span class="sxs-lookup"><span data-stu-id="22846-112">An invoice identifier.</span></span> <span data-ttu-id="22846-113">Hiermee wordt de factuur aangegeven waarvoor de regel items moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22846-113">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="22846-114">C\#</span><span class="sxs-lookup"><span data-stu-id="22846-114">C\#</span></span>

<span data-ttu-id="22846-115">Als u de commerciële regel items voor de opgegeven factuur wilt ophalen, moet u het object invoice ophalen:</span><span class="sxs-lookup"><span data-stu-id="22846-115">To get the commercial line items for the specified invoice, you must retrieve the invoice object:</span></span>

1. <span data-ttu-id="22846-116">Roep de methode [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) aan om een interface te verkrijgen voor het factureren van bewerkingen voor de opgegeven factuur.</span><span class="sxs-lookup"><span data-stu-id="22846-116">Call the [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) method to get an interface to invoice operations for the specified invoice.</span></span>

2. <span data-ttu-id="22846-117">Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) aan om het object invoice op te halen.</span><span class="sxs-lookup"><span data-stu-id="22846-117">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the invoice object.</span></span> <span data-ttu-id="22846-118">Het object invoice bevat alle informatie voor de opgegeven factuur.</span><span class="sxs-lookup"><span data-stu-id="22846-118">The invoice object contains all of the information for the specified invoice.</span></span>

<span data-ttu-id="22846-119">De **provider** identificeert de bron van de gefactureerde detail informatie (bijvoorbeeld **eenmalige**).</span><span class="sxs-lookup"><span data-stu-id="22846-119">The **Provider** identifies the source of the billed detail information (for example, **onetime**).</span></span> <span data-ttu-id="22846-120">De **InvoiceLineItemType** geeft het type aan (bijvoorbeeld **UsageLineItem**).</span><span class="sxs-lookup"><span data-stu-id="22846-120">The **InvoiceLineItemType** specifies the type (for example, **UsageLineItem**).</span></span>

<span data-ttu-id="22846-121">De volgende voorbeeld code gebruikt een **foreach** -lus om de verzameling van regel items te verwerken.</span><span class="sxs-lookup"><span data-stu-id="22846-121">The following example code uses a **foreach** loop to process the line items collection.</span></span> <span data-ttu-id="22846-122">Voor elke **InvoiceLineItemType** wordt een afzonderlijke verzameling regel items opgehaald.</span><span class="sxs-lookup"><span data-stu-id="22846-122">A separate collection of line items is retrieved for each **InvoiceLineItemType**.</span></span>

<span data-ttu-id="22846-123">Ophalen van een verzameling regel items die overeenkomen met een **InvoiceDetail** -exemplaar:</span><span class="sxs-lookup"><span data-stu-id="22846-123">To get a collection of line items that correspond to an **InvoiceDetail** instance:</span></span>

1. <span data-ttu-id="22846-124">Geef de **BillingProvider** en **InvoiceLineItemType** van het exemplaar door aan de methode [**by**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) .</span><span class="sxs-lookup"><span data-stu-id="22846-124">Pass the instance's **BillingProvider** and **InvoiceLineItemType** to the [**By**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) method.</span></span>

2. <span data-ttu-id="22846-125">Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) aan om de gekoppelde regel items op te halen.</span><span class="sxs-lookup"><span data-stu-id="22846-125">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the associated line items.</span></span>
3. <span data-ttu-id="22846-126">Maak een enumerator om door de verzameling te bladeren, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="22846-126">Create an enumerator to traverse the collection as shown in the following example.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string invoiceId;
// string curencyCode;
// string period;
// int pageMaxSizeReconLineItems = 2000;

// all the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

var seekBasedResourceCollection = scopedPartnerOperations.Invoices.ById(invoiceId).By("onetime", "usagelineitems", curencyCode, period, pageMaxSizeReconLineItems).Get();

var fetchNext = true;

ConsoleKeyInfo keyInfo;

var itemNumber = 1;
while (fetchNext)
{
    Console.Out.WriteLine("\tLine line items count: " + seekBasedResourceCollection.Items.Count());

    seekBasedResourceCollection.Items.ToList().ForEach(item =>
    {
        // Instance of type DailyRatedUsageLineItem
        if (item is DailyRatedUsageLineItem)
        {
            Type t = typeof(DailyRatedUsageLineItem);
            PropertyInfo[] properties = t.GetProperties();

            foreach (PropertyInfo property in properties)
            {
                // Insert code here to work with the line item properties
            }
        }
        itemNumber++;
    });

    Console.Out.WriteLine("\tPress any key to fetch next data. Press the Escape (Esc) key to quit: \n");
    keyInfo = Console.ReadKey();

    if (keyInfo.Key == ConsoleKey.Escape)
    {
        break;
    }

    fetchNext = !string.IsNullOrWhiteSpace(seekBasedResourceCollection.ContinuationToken);

    if (fetchNext)
    {
        if (seekBasedResourceCollection.Links.Next.Headers != null && seekBasedResourceCollection.Links.Next.Headers.Any())
        {
            seekBasedResourceCollection = scopedPartnerOperations.Invoices.ById(invoiceId).By("onetime", "usagelineitems", curencyCode, period, pageMaxSizeReconLineItems).Seek(seekBasedResourceCollection.ContinuationToken, SeekOperation.Next);
        }
    }
}
```

<span data-ttu-id="22846-127">Voor een vergelijkbaar voor beeld raadpleegt u het volgende:</span><span class="sxs-lookup"><span data-stu-id="22846-127">For a similar example, see the following:</span></span>

- <span data-ttu-id="22846-128">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="22846-128">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="22846-129">Project: **Partner Center SDK** -voor beelden</span><span class="sxs-lookup"><span data-stu-id="22846-129">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="22846-130">Klasse: **GetBilledConsumptionReconLineItemsPaging. cs**</span><span class="sxs-lookup"><span data-stu-id="22846-130">Class: **GetBilledConsumptionReconLineItemsPaging.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="22846-131">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="22846-131">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="22846-132">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="22846-132">Request syntax</span></span>

<span data-ttu-id="22846-133">Gebruik de eerste syntaxis om een volledige lijst van elk regel item voor de opgegeven factuur te retour neren.</span><span class="sxs-lookup"><span data-stu-id="22846-133">Use the first syntax to return a full list of every line item for the given invoice.</span></span> <span data-ttu-id="22846-134">Gebruik voor grote facturen de tweede syntaxis met een opgegeven grootte en een offset op basis van 0 om een pagina lijst met regel items te retour neren.</span><span class="sxs-lookup"><span data-stu-id="22846-134">For large invoices, use the second syntax with a specified size and 0-based offset to return a paged list of line items.</span></span> <span data-ttu-id="22846-135">Gebruik de derde syntaxis om de volgende pagina van afstemmings regel items te verkrijgen met `seekOperation = "Next"` .</span><span class="sxs-lookup"><span data-stu-id="22846-135">Use the third syntax to get the next page of recon line items using `seekOperation = "Next"`.</span></span>

| <span data-ttu-id="22846-136">Methode</span><span class="sxs-lookup"><span data-stu-id="22846-136">Method</span></span>  | <span data-ttu-id="22846-137">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="22846-137">Request URI</span></span>                                                                                                                                                     |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="22846-138">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="22846-138">**GET**</span></span> | <span data-ttu-id="22846-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems? provider = eenmalige&invoicelineitemtype = usagelineitems&CurrencyCode = {CURRENCYCODE} http/1.1</span><span class="sxs-lookup"><span data-stu-id="22846-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode} HTTP/1.1</span></span>                              |
| <span data-ttu-id="22846-140">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="22846-140">**GET**</span></span> | <span data-ttu-id="22846-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems? provider = eenmalige&invoicelineitemtype = usagelineitems&CurrencyCode = {currencycode} &grootte = {size} http/1.1</span><span class="sxs-lookup"><span data-stu-id="22846-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&size={size} HTTP/1.1</span></span>  |
| <span data-ttu-id="22846-142">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="22846-142">**GET**</span></span> | <span data-ttu-id="22846-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems? provider = eenmalige&invoicelineitemtype = usagelineitems&CurrencyCode = {currencycode} &grootte = {size} &SeekOperation = volgende</span><span class="sxs-lookup"><span data-stu-id="22846-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&size={size}&seekOperation=Next</span></span>                               |

#### <a name="uri-parameters"></a><span data-ttu-id="22846-144">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="22846-144">URI parameters</span></span>

<span data-ttu-id="22846-145">Gebruik de volgende URI en query parameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="22846-145">Use the following URI and query parameters when creating the request.</span></span>

| <span data-ttu-id="22846-146">Naam</span><span class="sxs-lookup"><span data-stu-id="22846-146">Name</span></span>                   | <span data-ttu-id="22846-147">Type</span><span class="sxs-lookup"><span data-stu-id="22846-147">Type</span></span>   | <span data-ttu-id="22846-148">Vereist</span><span class="sxs-lookup"><span data-stu-id="22846-148">Required</span></span> | <span data-ttu-id="22846-149">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="22846-149">Description</span></span>                                                       |
|------------------------|--------|----------|-------------------------------------------------------------------|
| <span data-ttu-id="22846-150">factuur-ID</span><span class="sxs-lookup"><span data-stu-id="22846-150">invoice-id</span></span>             | <span data-ttu-id="22846-151">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="22846-151">string</span></span> | <span data-ttu-id="22846-152">Ja</span><span class="sxs-lookup"><span data-stu-id="22846-152">Yes</span></span>      | <span data-ttu-id="22846-153">Een teken reeks waarmee de factuur wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="22846-153">A string that identifies the invoice.</span></span>                             |
| <span data-ttu-id="22846-154">providers</span><span class="sxs-lookup"><span data-stu-id="22846-154">provider</span></span>               | <span data-ttu-id="22846-155">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="22846-155">string</span></span> | <span data-ttu-id="22846-156">Ja</span><span class="sxs-lookup"><span data-stu-id="22846-156">Yes</span></span>      | <span data-ttu-id="22846-157">De provider: ' eenmalige '.</span><span class="sxs-lookup"><span data-stu-id="22846-157">The provider: "OneTime".</span></span>                                  |
| <span data-ttu-id="22846-158">factuur-regel-item-type</span><span class="sxs-lookup"><span data-stu-id="22846-158">invoice-line-item-type</span></span> | <span data-ttu-id="22846-159">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="22846-159">string</span></span> | <span data-ttu-id="22846-160">Ja</span><span class="sxs-lookup"><span data-stu-id="22846-160">Yes</span></span>      | <span data-ttu-id="22846-161">Het type factuur Details: "UsageLineItems".</span><span class="sxs-lookup"><span data-stu-id="22846-161">The type of invoice detail: "UsageLineItems".</span></span> |
| <span data-ttu-id="22846-162">currencyCode</span><span class="sxs-lookup"><span data-stu-id="22846-162">currencyCode</span></span>           | <span data-ttu-id="22846-163">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="22846-163">string</span></span> | <span data-ttu-id="22846-164">Ja</span><span class="sxs-lookup"><span data-stu-id="22846-164">Yes</span></span>      | <span data-ttu-id="22846-165">De valuta code voor de gefactureerde regel items.</span><span class="sxs-lookup"><span data-stu-id="22846-165">The currency code for the billed line items.</span></span>                    |
| <span data-ttu-id="22846-166">period</span><span class="sxs-lookup"><span data-stu-id="22846-166">period</span></span>                 | <span data-ttu-id="22846-167">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="22846-167">string</span></span> | <span data-ttu-id="22846-168">Ja</span><span class="sxs-lookup"><span data-stu-id="22846-168">Yes</span></span>      | <span data-ttu-id="22846-169">De periode voor gefactureerde afstemming.</span><span class="sxs-lookup"><span data-stu-id="22846-169">The period for billed recon.</span></span> <span data-ttu-id="22846-170">voor beeld: huidige, vorige.</span><span class="sxs-lookup"><span data-stu-id="22846-170">example: current, previous.</span></span>        |
| <span data-ttu-id="22846-171">grootte</span><span class="sxs-lookup"><span data-stu-id="22846-171">size</span></span>                   | <span data-ttu-id="22846-172">getal</span><span class="sxs-lookup"><span data-stu-id="22846-172">number</span></span> | <span data-ttu-id="22846-173">Nee</span><span class="sxs-lookup"><span data-stu-id="22846-173">No</span></span>       | <span data-ttu-id="22846-174">Het maximum aantal items dat moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="22846-174">The maximum number of items to return.</span></span> <span data-ttu-id="22846-175">De standaard grootte is 2000</span><span class="sxs-lookup"><span data-stu-id="22846-175">Default size is 2000</span></span>       |
| <span data-ttu-id="22846-176">seekOperation</span><span class="sxs-lookup"><span data-stu-id="22846-176">seekOperation</span></span>          | <span data-ttu-id="22846-177">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="22846-177">string</span></span> | <span data-ttu-id="22846-178">No</span><span class="sxs-lookup"><span data-stu-id="22846-178">No</span></span>       | <span data-ttu-id="22846-179">Stel seekOperation = volgende in om de volgende pagina van de afstemmings regel items op te halen.</span><span class="sxs-lookup"><span data-stu-id="22846-179">Set seekOperation=Next to get the next page of recon line items.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="22846-180">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="22846-180">Request headers</span></span>

<span data-ttu-id="22846-181">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="22846-181">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="22846-182">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="22846-182">Request body</span></span>

<span data-ttu-id="22846-183">Geen.</span><span class="sxs-lookup"><span data-stu-id="22846-183">None.</span></span>

## <a name="rest-response"></a><span data-ttu-id="22846-184">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="22846-184">REST response</span></span>

<span data-ttu-id="22846-185">Als dit is gelukt, bevat het antwoord het verzamelen van regel items.</span><span class="sxs-lookup"><span data-stu-id="22846-185">If successful, the response contains the collection of line item details.</span></span>

<span data-ttu-id="22846-186">Voor de **ChargeType** van het regel item wordt de **gekochte** waarde toegewezen aan **Nieuw**.</span><span class="sxs-lookup"><span data-stu-id="22846-186">For the line item **ChargeType**, the value **Purchase** is mapped to **New**.</span></span> <span data-ttu-id="22846-187">De **terugbetaling** van de waarde is toegewezen aan **Annuleren**.</span><span class="sxs-lookup"><span data-stu-id="22846-187">The value **Refund** is mapped to **Cancel**.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="22846-188">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="22846-188">Response success and error codes</span></span>

<span data-ttu-id="22846-189">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="22846-189">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="22846-190">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="22846-190">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="22846-191">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="22846-191">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

## <a name="rest-examples"></a><span data-ttu-id="22846-192">REST-voor beelden</span><span class="sxs-lookup"><span data-stu-id="22846-192">REST examples</span></span>

### <a name="request-response-example-1"></a><span data-ttu-id="22846-193">Aanvraag-antwoord-voor beeld 1</span><span class="sxs-lookup"><span data-stu-id="22846-193">Request-response example 1</span></span>

<span data-ttu-id="22846-194">De Details voor dit voor beeld van de REST-aanvraag en het-antwoord zijn:</span><span class="sxs-lookup"><span data-stu-id="22846-194">The details for this example REST request and response are as follows:</span></span>

- <span data-ttu-id="22846-195">**Provider**: **eenmalige**</span><span class="sxs-lookup"><span data-stu-id="22846-195">**Provider**: **OneTime**</span></span>
- <span data-ttu-id="22846-196">**InvoiceLineItemType**: **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="22846-196">**InvoiceLineItemType**: **UsageLineItems**</span></span>
- <span data-ttu-id="22846-197">**Periode**: **vorige**</span><span class="sxs-lookup"><span data-stu-id="22846-197">**Period**: **Previous**</span></span>

#### <a name="request-example-1"></a><span data-ttu-id="22846-198">Voor beeld 1 aanvragen</span><span class="sxs-lookup"><span data-stu-id="22846-198">Request example 1</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/T000001234/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-1"></a><span data-ttu-id="22846-199">Antwoord voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="22846-199">Response example 1</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Wed, 20 Feb 2019 19:59:27 GMT

{
    "totalCount": 2,
    "items": [
        {
            "partnerId": "2b8940db-5089-539c-e757-520ed1d1bc88",
            "partnerName": "",
            "customerId": "",
            "customerName": "",
            "customerDomainName": "",
            "invoiceNumber": "T000001234",
            "productId": "",
            "skuId": "",
            "availabilityId": "",
            "skuName": "Test Test on Windows 2012 R2 (WebHost)",
            "productName": "Test Test on Windows",
            "publisherName": "Test",
            "publisherId": "28503520",
            "subscriptionId": "12345678-9d62-4a85-8fd0-91a87c261bc4",
            "subscriptionDescription": "Subscription 10",
            "chargeStartDate": "2018-11-01T00:00:00Z",
            "chargeEndDate": "2018-12-01T00:00:00Z",
            "usageDate": "2018-11-13T00:00:00Z",
            "meterType": "1 Compute Hour - 1core",
            "meterCategory": "Virtual Machine Licenses",
            "meterId": "1core",
            "meterSubCategory": "Test Test on Windows",
            "meterName": "Test Test on Windows - Test Test on Windows 2012 R2 (WebHost) - 1 Core Hours",
            "meterRegion": "",
            "unitOfMeasure": "1 Hour",
            "resourceLocation": "EASTUS2",
            "consumedService": "Microsoft.Compute",
            "resourceGroup": "TestWINRG",
            "resourceUri": "/subscriptions/12345678-9d62-4a85-8fd0-91a87c261bc4/resourceGroups/TestWINRG/providers/Microsoft.Compute/virtualMachines/testWinTest",
            "tags": "",
            "additionalInfo": "{  \"ImageType\": null,  \"ServiceType\": \"Standard_B1s\",  \"VMName\": null,  \"VMProperties\": null,  \"UsageType\": \"ComputeHR_SW\"}",
            "serviceInfo1": "",
            "serviceInfo2": "",
            "customerCountry": "",
            "mpnId": "1234567",
            "resellerMpnId": "",
            "chargeType": "new",
            "unitPrice": 0.0209496384791679,
            "quantity": 23.200004,
            "unitType": "1 Hour",
            "billingPreTaxTotal": 0.486031696515249,
            "billingCurrency": "USD",
            "pricingPreTaxTotal": 0.486031696515249,
            "pricingCurrency": "USD",
            "creditType": "Credit Not Applied",
            "invoiceLineItemType": "usage_line_items",
            "billingProvider": "marketplace",
            "attributes": {
                "objectType": "DailyRatedUsageLineItem"
            }
        },
        {
            "partnerId": "2b8940db-5089-539c-e757-520ed1d1bc88",
            "partnerName": "",
            "customerId": "",
            "customerName": "",
            "customerDomainName": "",
            "invoiceNumber": "T000001234",
            "productId": "",
            "skuId": "",
            "availabilityId": "",
            "skuName": "Test Test on Ubuntu 16.04 (WebHost)",
            "productName": "Test Test on Linux",
            "publisherName": "Test",
            "publisherId": "28503520",
            "subscriptionId": "12345678-9d62-4a85-8fd0-91a87c261bc4",
            "subscriptionDescription": "Subscription 10",
            "chargeStartDate": "2018-11-01T00:00:00Z",
            "chargeEndDate": "2018-12-01T00:00:00Z",
            "usageDate": "2018-11-13T00:00:00Z",
            "meterType": "1 Compute Hour - 1core",
            "meterCategory": "Virtual Machine Licenses",
            "meterId": "1core",
            "meterSubCategory": "Test Test on Linux",
            "meterName": "Test Test on Linux - Test Test on Ubuntu 16.04 (WebHost) - 1 Core Hours",
            "meterRegion": "",
            "unitOfMeasure": "1 Hour",
            "resourceLocation": "EASTUS",
            "consumedService": "Microsoft.Compute",
            "resourceGroup": "TESTRG",
            "resourceUri": "/subscriptions/12345678-9d62-4a85-8fd0-91a87c261bc4/resourceGroups/TestRG/providers/Microsoft.Compute/virtualMachines/testUbuntuTest",
            "tags": "",
            "additionalInfo": "{  \"ImageType\": null,  \"ServiceType\": \"Standard_B1s\",  \"VMName\": null,  \"VMProperties\": null,  \"UsageType\": \"ComputeHR_SW\"}",
            "serviceInfo1": "",
            "serviceInfo2": "",
            "customerCountry": "",
            "mpnId": "1234567",
            "resellerMpnId": "",
            "chargeType": "new",
            "unitPrice": 0.0209951014286867,
            "quantity": 23.350007,
            "unitType": "1 Hour",
            "billingPreTaxTotal": 0.490235765325545,
            "billingCurrency": "USD",
            "pricingPreTaxTotal": 0.490235765325545,
            "pricingCurrency": "USD",
            "entitlementId": "66bada28-271e-4b7a-aaf5-c0ead6312345",
            "entitlementDescription": "Partner Subscription",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "effectiveUnitPrice": 0.1999968000511991808131,
            "rateOfPartnerEarnedCredit": 0,
            "rateOfCredit": 1,
            "creditType": "Azure Credit Applied",
            "invoiceLineItemType": "usage_line_items",
            "billingProvider": "marketplace",
            "attributes": {
                "objectType": "DailyRatedUsageLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/T000001234/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/T000001234/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000&seekOperation=Next",
            "method": "GET",
            "headers": [
                {
                    "key": "MS-ContinuationToken",
                    "value": "AQAAAA=="
                }
            ]
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-2"></a><span data-ttu-id="22846-200">Aanvraag-antwoord-voor beeld 2</span><span class="sxs-lookup"><span data-stu-id="22846-200">Request-response example 2</span></span>

<span data-ttu-id="22846-201">De Details voor dit voor beeld van de REST-aanvraag en het-antwoord zijn:</span><span class="sxs-lookup"><span data-stu-id="22846-201">The details for this example REST request and response are as follows:</span></span>

- <span data-ttu-id="22846-202">**Provider**: **eenmalige**</span><span class="sxs-lookup"><span data-stu-id="22846-202">**Provider**: **OneTime**</span></span>
- <span data-ttu-id="22846-203">**InvoiceLineItemType**: **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="22846-203">**InvoiceLineItemType**: **UsageLineItems**</span></span>
- <span data-ttu-id="22846-204">**Periode**: **vorige**</span><span class="sxs-lookup"><span data-stu-id="22846-204">**Period**: **Previous**</span></span>
- <span data-ttu-id="22846-205">**SeekOperation**: **volgende**</span><span class="sxs-lookup"><span data-stu-id="22846-205">**SeekOperation**: **Next**</span></span>

#### <a name="request-example-2"></a><span data-ttu-id="22846-206">Voor beeld 2 aanvragen</span><span class="sxs-lookup"><span data-stu-id="22846-206">Request example 2</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/T000001234/lineitems?provider=onetime&invoiceLineItemType=usagelineitems&currencyCode=usd&period=previous&size=2000&seekoperation=next HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-ContinuationToken: d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

## <a name="response-example-2"></a><span data-ttu-id="22846-207">Antwoord voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="22846-207">Response example 2</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Wed, 20 Feb 2019 19:59:27 GMT

{
    "totalCount": 1,
    "items": [
          {
            "partnerId": "2b8940db-5089-539c-e757-520ed1d1bc88",
            "partnerName": "",
            "customerId": "",
            "customerName": "",
            "customerDomainName": "",
            "invoiceNumber": "T000001234",
            "productId": "",
            "skuId": "",
            "availabilityId": "",
            "skuName": "Test Test on Windows 2012 R2 (WebHost)",
            "productName": "Test Test on Windows",
            "publisherName": "Test",
            "publisherId": "28503520",
            "subscriptionId": "12345678-9d62-4a85-8fd0-91a87c261bc4",
            "subscriptionDescription": "Subscription 10",
            "chargeStartDate": "2018-11-01T00:00:00Z",
            "chargeEndDate": "2018-12-01T00:00:00Z",
            "usageDate": "2018-11-13T00:00:00Z",
            "meterType": "1 Compute Hour - 1core",
            "meterCategory": "Virtual Machine Licenses",
            "meterId": "1core",
            "meterSubCategory": "Test Test on Windows",
            "meterName": "Test Test on Windows - Test Test on Windows 2012 R2 (WebHost) - 1 Core Hours",
            "meterRegion": "",
            "unitOfMeasure": "1 Hour",
            "resourceLocation": "EASTUS2",
            "consumedService": "Microsoft.Compute",
            "resourceGroup": "TestWINRG",
            "resourceUri": "/subscriptions/12345678-9d62-4a85-8fd0-91a87c261bc4/resourceGroups/TestWINRG/providers/Microsoft.Compute/virtualMachines/testWinTest",
            "tags": "",
            "additionalInfo": "{  \"ImageType\": null,  \"ServiceType\": \"Standard_B1s\",  \"VMName\": null,  \"VMProperties\": null,  \"UsageType\": \"ComputeHR_SW\"}",
            "serviceInfo1": "",
            "serviceInfo2": "",
            "customerCountry": "",
            "mpnId": "1234567",
            "resellerMpnId": "",
            "chargeType": "new",
            "unitPrice": 0.0209496384791679,
            "quantity": 23.200004,
            "unitType": "1 Hour",
            "billingPreTaxTotal": 0.486031696515249,
            "billingCurrency": "USD",
            "pricingPreTaxTotal": 0.486031696515249,
            "pricingCurrency": "USD",
            "entitlementId": "66bada28-271e-4b7a-aaf5-c0ead6312345",
            "entitlementDescription": "Partner Subscription",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "effectiveUnitPrice": 0.1835431430074643112595,
            "rateOfPartnerEarnedCredit": 0.15,
            "rateOfCredit": 0.15,
            "creditType": "Partner Earned Credit Applied",
            "attributes": {
                "objectType": "DailyRatedUsageLineItem"
            }
        }
    ],
    "links": {
        "self": {
             "uri": "/invoices/T000001234/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
