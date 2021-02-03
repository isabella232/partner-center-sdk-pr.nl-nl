---
title: Regel items voor niet-gefactureerde reconciliatie van factuur ophalen
description: U kunt een verzameling van Details over een niet-gefactureerde afstemmings regel voor de opgegeven periode ophalen met behulp van de Partner Center-Api's.
ms.date: 01/27/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: ff69798ddfd91fca817ec0d047bf407f326066c2
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767545"
---
# <a name="get-invoices-unbilled-reconciliation-line-items"></a><span data-ttu-id="7d0c5-103">Regel items voor niet-gefactureerde reconciliatie van factuur ophalen</span><span class="sxs-lookup"><span data-stu-id="7d0c5-103">Get invoice's unbilled reconciliation line items</span></span>

<span data-ttu-id="7d0c5-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="7d0c5-104">**Applies to:**</span></span>

- <span data-ttu-id="7d0c5-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="7d0c5-105">Partner Center</span></span>
- <span data-ttu-id="7d0c5-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="7d0c5-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="7d0c5-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="7d0c5-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="7d0c5-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="7d0c5-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="7d0c5-109">U kunt de volgende methoden gebruiken om een verzameling details te verkrijgen voor niet-gefactureerde factuur regel items (ook wel bekend als open facturerings regel items).</span><span class="sxs-lookup"><span data-stu-id="7d0c5-109">You can use the following methods get a collection of details for unbilled invoice line items (also known as open billing line items).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7d0c5-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7d0c5-110">Prerequisites</span></span>

- <span data-ttu-id="7d0c5-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7d0c5-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7d0c5-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="7d0c5-113">Een factuur-ID.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-113">An invoice identifier.</span></span> <span data-ttu-id="7d0c5-114">Hiermee wordt de factuur aangegeven waarvoor de regel items moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-114">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="7d0c5-115">C\#</span><span class="sxs-lookup"><span data-stu-id="7d0c5-115">C\#</span></span>

<span data-ttu-id="7d0c5-116">Als u de regel items voor de opgegeven factuur wilt ophalen, haalt u het factuur object op:</span><span class="sxs-lookup"><span data-stu-id="7d0c5-116">To get the line items for the specified invoice, retrieve the invoice object:</span></span>

1. <span data-ttu-id="7d0c5-117">Roep de methode [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) aan om een interface te verkrijgen voor het factureren van bewerkingen voor de opgegeven factuur.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-117">Call the [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) method to get an interface to invoice operations for the specified invoice.</span></span>

2. <span data-ttu-id="7d0c5-118">Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) aan om het object invoice op te halen.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-118">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the invoice object.</span></span>

<span data-ttu-id="7d0c5-119">Het object invoice bevat alle informatie voor de opgegeven factuur:</span><span class="sxs-lookup"><span data-stu-id="7d0c5-119">The invoice object contains all of the information for the specified invoice:</span></span>

- <span data-ttu-id="7d0c5-120">**Provider** identificeert de bron van de niet-gefactureerde detail informatie (bijvoorbeeld **eenmalige**).</span><span class="sxs-lookup"><span data-stu-id="7d0c5-120">**Provider** identifies the source of the unbilled detail information (for example, **OneTime**).</span></span>

- <span data-ttu-id="7d0c5-121">**InvoiceLineItemType** Hiermee geeft u het type op (bijvoorbeeld **BillingLineItem**).</span><span class="sxs-lookup"><span data-stu-id="7d0c5-121">**InvoiceLineItemType** specifies the type (for example, **BillingLineItem**).</span></span>

<span data-ttu-id="7d0c5-122">Ophalen van een verzameling regel items die overeenkomen met een **InvoiceDetail** -exemplaar:</span><span class="sxs-lookup"><span data-stu-id="7d0c5-122">To get a collection of line items that correspond to an **InvoiceDetail** instance:</span></span>

1. <span data-ttu-id="7d0c5-123">Geef de BillingProvider en InvoiceLineItemType van het exemplaar door aan de methode [**by**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) .</span><span class="sxs-lookup"><span data-stu-id="7d0c5-123">Pass the instance's BillingProvider and InvoiceLineItemType to the [**By**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) method.</span></span>

2. <span data-ttu-id="7d0c5-124">Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) aan om de gekoppelde regel items op te halen.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-124">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the associated line items.</span></span>

3. <span data-ttu-id="7d0c5-125">Maak een enumerator om door de verzameling te bladeren.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-125">Create an enumerator to traverse the collection.</span></span> <span data-ttu-id="7d0c5-126">Zie de volgende voorbeeld code voor een voor beeld.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-126">For an example, see the following sample code.</span></span>

<span data-ttu-id="7d0c5-127">De volgende voorbeeld code gebruikt een **foreach** -lus om de **InvoiceLineItems** -verzameling te verwerken.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-127">The following sample code uses a **foreach** loop to process the **InvoiceLineItems** collection.</span></span> <span data-ttu-id="7d0c5-128">Voor elke **InvoiceLineItemType** wordt een afzonderlijke verzameling regel items opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-128">A separate collection of line items is retrieved for each **InvoiceLineItemType**.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string currencyCode;
// string period;
// int pageMaxSizeReconLineItems = 2000;

// all the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

var seekBasedResourceCollection = scopedPartnerOperations.Invoices.ById("unbilled").By("onetime", "billinglineitems", currencyCode, period, pageMaxSizeReconLineItems).Get();

var fetchNext = true;

ConsoleKeyInfo keyInfo;

var itemNumber = 1;
while (fetchNext)
{
    Console.Out.WriteLine("\tLine line items count: " + seekBasedResourceCollection.Items.Count());

    seekBasedResourceCollection.Items.ToList().ForEach(item =>
    {
        // Instance of type OneTimeInvoiceLineItem
        if (item is OneTimeInvoiceLineItem)
        {
            Type t = typeof(OneTimeInvoiceLineItem);
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
            seekBasedResourceCollection = scopedPartnerOperations.Invoices.ById("unbilled").By("onetime", "billinglineitems", currencyCode, period, pageMaxSizeReconLineItems).Seek(seekBasedResourceCollection.ContinuationToken, SeekOperation.Next);
        }
    }
}
```

<span data-ttu-id="7d0c5-129">Zie voor een vergelijkbaar voor beeld:</span><span class="sxs-lookup"><span data-stu-id="7d0c5-129">For a similar example, see:</span></span>

- <span data-ttu-id="7d0c5-130">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="7d0c5-130">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="7d0c5-131">Project: **Partner Center SDK** -voor beelden</span><span class="sxs-lookup"><span data-stu-id="7d0c5-131">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="7d0c5-132">Klasse: **GetUnBilledReconLineItemsPaging.cs**</span><span class="sxs-lookup"><span data-stu-id="7d0c5-132">Class: **GetUnBilledReconLineItemsPaging.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="7d0c5-133">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="7d0c5-133">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7d0c5-134">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7d0c5-134">Request syntax</span></span>

<span data-ttu-id="7d0c5-135">U kunt de volgende syntaxis voor uw REST-aanvraag gebruiken, afhankelijk van uw use-case.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-135">You can use the following syntaxes for your REST request, depending on your use case.</span></span> <span data-ttu-id="7d0c5-136">Zie de beschrijvingen voor elke syntaxis voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-136">For more information, see the descriptions for each syntax.</span></span>

 | <span data-ttu-id="7d0c5-137">Methode</span><span class="sxs-lookup"><span data-stu-id="7d0c5-137">Method</span></span>  | <span data-ttu-id="7d0c5-138">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="7d0c5-138">Request URI</span></span>            | <span data-ttu-id="7d0c5-139">Beschrijving van de syntaxis use case</span><span class="sxs-lookup"><span data-stu-id="7d0c5-139">Description of syntax use case</span></span>                                                                                |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7d0c5-140">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7d0c5-140">**GET**</span></span> | <span data-ttu-id="7d0c5-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems? provider = eenmalige&invoicelineitemtype = billinglineitems&CurrencyCode = {currencycode} &periode = {period} http/1.1</span><span class="sxs-lookup"><span data-stu-id="7d0c5-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period} HTTP/1.1</span></span>                              | <span data-ttu-id="7d0c5-142">Gebruik deze syntaxis om een volledige lijst van elk regel item voor de opgegeven factuur te retour neren.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-142">Use this syntax to return a full list of every line item for the given invoice.</span></span> |
| <span data-ttu-id="7d0c5-143">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7d0c5-143">**GET**</span></span> | <span data-ttu-id="7d0c5-144">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems? provider = eenmalige&invoicelineitemtype = billinglineitems&CurrencyCode = {currencycode} &periode = {period} &grootte = {size} http/1.1</span><span class="sxs-lookup"><span data-stu-id="7d0c5-144">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period}&size={size} HTTP/1.1</span></span>  | <span data-ttu-id="7d0c5-145">Voor grote facturen gebruikt u deze syntaxis met een opgegeven grootte en een offset op basis van 0 om een pagina lijst met regel items te retour neren.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-145">For large invoices, use this syntax with a specified size and 0-based offset to return a paged list of line items.</span></span> |
| <span data-ttu-id="7d0c5-146">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7d0c5-146">**GET**</span></span> | <span data-ttu-id="7d0c5-147">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems? provider = eenmalige&invoicelineitemtype = billinglineitems&CurrencyCode = {currencycode} &periode = {period} &grootte = {size} &SeekOperation = Next</span><span class="sxs-lookup"><span data-stu-id="7d0c5-147">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode={currencycode}&period={period}&size={size}&seekOperation=Next</span></span>                               | <span data-ttu-id="7d0c5-148">Gebruik deze syntaxis om de volgende pagina van regel items voor reconciliatie te verkrijgen met `seekOperation = "Next"` .</span><span class="sxs-lookup"><span data-stu-id="7d0c5-148">Use this syntax to get the next page of reconciliation line items using `seekOperation = "Next"`.</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="7d0c5-149">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="7d0c5-149">URI parameters</span></span>

<span data-ttu-id="7d0c5-150">Gebruik de volgende URI en query parameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-150">Use the following URI and query parameters when creating the request.</span></span>

| <span data-ttu-id="7d0c5-151">Naam</span><span class="sxs-lookup"><span data-stu-id="7d0c5-151">Name</span></span>                   | <span data-ttu-id="7d0c5-152">Type</span><span class="sxs-lookup"><span data-stu-id="7d0c5-152">Type</span></span>   | <span data-ttu-id="7d0c5-153">Vereist</span><span class="sxs-lookup"><span data-stu-id="7d0c5-153">Required</span></span> | <span data-ttu-id="7d0c5-154">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7d0c5-154">Description</span></span>                                                                     |
|------------------------|--------|----------|---------------------------------------------------------------------------------|
| <span data-ttu-id="7d0c5-155">factuur-ID</span><span class="sxs-lookup"><span data-stu-id="7d0c5-155">invoice-id</span></span>             | <span data-ttu-id="7d0c5-156">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7d0c5-156">string</span></span> | <span data-ttu-id="7d0c5-157">Yes</span><span class="sxs-lookup"><span data-stu-id="7d0c5-157">Yes</span></span>      | <span data-ttu-id="7d0c5-158">Een teken reeks waarmee de factuur wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-158">A string that identifies the invoice.</span></span> <span data-ttu-id="7d0c5-159">Gebruik ' niet gefactureerd ' om niet-gefactureerde schattingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-159">Use 'unbilled' to get unbilled estimates.</span></span> |
| <span data-ttu-id="7d0c5-160">providers</span><span class="sxs-lookup"><span data-stu-id="7d0c5-160">provider</span></span>               | <span data-ttu-id="7d0c5-161">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7d0c5-161">string</span></span> | <span data-ttu-id="7d0c5-162">Yes</span><span class="sxs-lookup"><span data-stu-id="7d0c5-162">Yes</span></span>      | <span data-ttu-id="7d0c5-163">De provider: ' eenmalige '.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-163">The provider: "OneTime".</span></span>                                                |
| <span data-ttu-id="7d0c5-164">factuur-regel-item-type</span><span class="sxs-lookup"><span data-stu-id="7d0c5-164">invoice-line-item-type</span></span> | <span data-ttu-id="7d0c5-165">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7d0c5-165">string</span></span> | <span data-ttu-id="7d0c5-166">Yes</span><span class="sxs-lookup"><span data-stu-id="7d0c5-166">Yes</span></span>      | <span data-ttu-id="7d0c5-167">Het type factuur Details: "BillingLineItems".</span><span class="sxs-lookup"><span data-stu-id="7d0c5-167">The type of invoice detail: "BillingLineItems".</span></span>               |
| <span data-ttu-id="7d0c5-168">hasPartnerEarnedCredit</span><span class="sxs-lookup"><span data-stu-id="7d0c5-168">hasPartnerEarnedCredit</span></span> | <span data-ttu-id="7d0c5-169">booleaans</span><span class="sxs-lookup"><span data-stu-id="7d0c5-169">bool</span></span>   | <span data-ttu-id="7d0c5-170">No</span><span class="sxs-lookup"><span data-stu-id="7d0c5-170">No</span></span>       | <span data-ttu-id="7d0c5-171">De waarde die aangeeft of de regel items moeten worden geretourneerd waarvoor het tegoed van de partner is toegepast.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-171">The value indicating if to return the line items with partner earned credit applied.</span></span> <span data-ttu-id="7d0c5-172">Opmerking: deze para meter wordt alleen toegepast wanneer het provider type eenmalige is en InvoiceLineItemType is ingesteld op UsageLineItems.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-172">Note: this parameter will be only applied when provider type is OneTime and InvoiceLineItemType is UsageLineItems.</span></span>
| <span data-ttu-id="7d0c5-173">currencyCode</span><span class="sxs-lookup"><span data-stu-id="7d0c5-173">currencyCode</span></span>           | <span data-ttu-id="7d0c5-174">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7d0c5-174">string</span></span> | <span data-ttu-id="7d0c5-175">Yes</span><span class="sxs-lookup"><span data-stu-id="7d0c5-175">Yes</span></span>      | <span data-ttu-id="7d0c5-176">De valuta code voor de niet-gefactureerde regel items.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-176">The currency code for the unbilled line items.</span></span>                                  |
| <span data-ttu-id="7d0c5-177">period</span><span class="sxs-lookup"><span data-stu-id="7d0c5-177">period</span></span>                 | <span data-ttu-id="7d0c5-178">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7d0c5-178">string</span></span> | <span data-ttu-id="7d0c5-179">Yes</span><span class="sxs-lookup"><span data-stu-id="7d0c5-179">Yes</span></span>      | <span data-ttu-id="7d0c5-180">De periode voor niet-gefactureerde afstemming.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-180">The period for unbilled recon.</span></span> <span data-ttu-id="7d0c5-181">voor beeld: huidige, vorige.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-181">example: current, previous.</span></span>                      |
| <span data-ttu-id="7d0c5-182">grootte</span><span class="sxs-lookup"><span data-stu-id="7d0c5-182">size</span></span>                   | <span data-ttu-id="7d0c5-183">getal</span><span class="sxs-lookup"><span data-stu-id="7d0c5-183">number</span></span> | <span data-ttu-id="7d0c5-184">No</span><span class="sxs-lookup"><span data-stu-id="7d0c5-184">No</span></span>       | <span data-ttu-id="7d0c5-185">Het maximum aantal items dat moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-185">The maximum number of items to return.</span></span> <span data-ttu-id="7d0c5-186">De standaard grootte is 2000</span><span class="sxs-lookup"><span data-stu-id="7d0c5-186">Default size is 2000</span></span>                     |
| <span data-ttu-id="7d0c5-187">seekOperation</span><span class="sxs-lookup"><span data-stu-id="7d0c5-187">seekOperation</span></span>          | <span data-ttu-id="7d0c5-188">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7d0c5-188">string</span></span> | <span data-ttu-id="7d0c5-189">No</span><span class="sxs-lookup"><span data-stu-id="7d0c5-189">No</span></span>       | <span data-ttu-id="7d0c5-190">Stel seekOperation = volgende in om de volgende pagina van de afstemmings regel items op te halen.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-190">Set seekOperation=Next to get the next page of recon line items.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="7d0c5-191">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="7d0c5-191">Request headers</span></span>

<span data-ttu-id="7d0c5-192">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="7d0c5-192">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7d0c5-193">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="7d0c5-193">Request body</span></span>

<span data-ttu-id="7d0c5-194">Geen.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-194">None.</span></span>

## <a name="rest-response"></a><span data-ttu-id="7d0c5-195">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="7d0c5-195">REST response</span></span>

<span data-ttu-id="7d0c5-196">Als dit is gelukt, bevat het antwoord het verzamelen van regel items.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-196">If successful, the response contains the collection of line item details.</span></span>

<span data-ttu-id="7d0c5-197">*Voor de **ChargeType** van het regel item wordt de **gekochte** waarde toegewezen aan **Nieuw** en de **terugbetaling** van de waarde wordt toegewezen om te **Annuleren**.*</span><span class="sxs-lookup"><span data-stu-id="7d0c5-197">*For the line item **ChargeType**, the value **Purchase** is mapped to **New** and the value **Refund** is mapped to **Cancel**.*</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7d0c5-198">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="7d0c5-198">Response success and error codes</span></span>

<span data-ttu-id="7d0c5-199">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-199">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7d0c5-200">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-200">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7d0c5-201">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-201">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="request-response-examples"></a><span data-ttu-id="7d0c5-202">Aanvraag-antwoord voorbeelden</span><span class="sxs-lookup"><span data-stu-id="7d0c5-202">Request-response examples</span></span>

#### <a name="request-response-example-1"></a><span data-ttu-id="7d0c5-203">Aanvraag-antwoord-voor beeld 1</span><span class="sxs-lookup"><span data-stu-id="7d0c5-203">Request-response example 1</span></span>

<span data-ttu-id="7d0c5-204">De volgende details zijn van toepassing op dit voor beeld:</span><span class="sxs-lookup"><span data-stu-id="7d0c5-204">The following details apply to this example:</span></span>

- <span data-ttu-id="7d0c5-205">Provider: **eenmalige**</span><span class="sxs-lookup"><span data-stu-id="7d0c5-205">Provider: **OneTime**</span></span>
- <span data-ttu-id="7d0c5-206">InvoiceLineItemType: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="7d0c5-206">InvoiceLineItemType: **BillingLineItems**</span></span>
- <span data-ttu-id="7d0c5-207">Periode: **vorige**</span><span class="sxs-lookup"><span data-stu-id="7d0c5-207">Period: **Previous**</span></span>

#### <a name="request-example-1"></a><span data-ttu-id="7d0c5-208">Voor beeld 1 aanvragen</span><span class="sxs-lookup"><span data-stu-id="7d0c5-208">Request example 1</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1//invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode=usd&period=previous&size=2000 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-1"></a><span data-ttu-id="7d0c5-209">Antwoord voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="7d0c5-209">Response example 1</span></span>

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
            "partnerId": "0c924e8d-4852-4692-a4d7-7dd0dc09ad80",
            "customerId": "org:d7f565f5-5367-492f-a465-9e2057c5e3c3",
            "customerName": "TEST_TEST_GTM1",
            "customerDomainName": "TESTTESTGTM1.ccsctp.net",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "1234567",
            "resellerMpnId": 0,
            "orderId": "HJVtMZMkgQ2miuCiNv0RSr51zQDans0m1",
            "orderDate": "2019-02-04T17:59:52.9460102Z",
            "productId": "DZH318Z0BXWC",
            "skuId": "0002",
            "availabilityId": "DZH318Z0BP8B",
            "productName": "Test WAF-as-a-Service",
            "skuName": "Test WaaS - Medium Plan",
            "chargeType": "New",
            "unitPrice": 820,
            "effectiveUnitPrice": 820,
            "unitType": "",
            "quantity": 1,
            "subtotal": 820,
            "taxTotal": 0,
            "totalForCustomer": 0,
            "currency": "USD",
            "publisherName": "Test Networks, Inc.",
            "publisherId": "21223810",
            "subscriptionDescription": "",
            "subscriptionId": "12345678-9cf0-4a1f-9514-7fcc7fe9d1fe",
            "chargeStartDate": "2019-02-04T09:22:40.1767993-08:00",
            "chargeEndDate": "2019-03-03T09:22:40.1767993-08:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "123456ad566",
            "priceAdjustmentDescription": "[\"15.0% Partner earned credit for services managed\"]",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "billableQuantity": 3.1618,
            "meterDescription": "Bandwidth - Data Transfer In (GB) - Zone 2",
            "reservationOrderId": "883d475b-0000-1234-0000-8818752f1234",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        },
        {
            "partnerId": "0c924e8d-4852-4692-a4d7-7dd0dc09ad80",
            "customerId": "org:d7f565f5-5367-492f-a465-9e2057c5e3c3",
            "customerName": "TEST_TEST_GTM1",
            "customerDomainName": "TESTTESTGTM1.ccsctp.net",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "1234567",
            "resellerMpnId": 0,
            "orderId": "Oi2kwDPEOyGEFUkESk3QR4XSxcpvwp1x1",
            "orderDate": "2019-02-04T17:59:53.1628078Z",
            "productId": "DZH318Z0BXWC",
            "skuId": "0005",
            "availabilityId": "DZH318Z0BH9R",
            "productName": "Test WAF-as-a-Service",
            "skuName": "Test WaaS - Large Plan",
            "chargeType": "New",
            "unitPrice": 2598,
            "effectiveUnitPrice": 2598,
            "unitType": "",
            "quantity": 1,
            "subtotal": 2598,
            "taxTotal": 0,
            "totalForCustomer": 0,
            "currency": "USD",
            "publisherName": "Test Networks, Inc.",
            "publisherId": "21223810",
            "subscriptionDescription": "",
            "subscriptionId": "12345678-28db-48c2-8c30-04d7c9455746",
            "chargeStartDate": "2019-02-04T09:22:34.6455294-08:00",
            "chargeEndDate": "2019-03-03T09:22:34.6455294-08:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "123456ad566",
            "priceAdjustmentDescription": "[\"15.0% Partner earned credit for services managed\",\"100.0% Tier 1 Discount\"]",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "billableQuantity": 0.737083,
            "meterDescription": "",
            "reservationOrderId": "883d475b-0000-2222-0000-8818752f1234",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode=usd&period=previous&size=2000&seekOperation=Next",
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

### <a name="request-response-example-2"></a><span data-ttu-id="7d0c5-210">Aanvraag-antwoord-voor beeld 2</span><span class="sxs-lookup"><span data-stu-id="7d0c5-210">Request-response example 2</span></span>

<span data-ttu-id="7d0c5-211">De volgende details zijn van toepassing op dit voor beeld:</span><span class="sxs-lookup"><span data-stu-id="7d0c5-211">The following details apply to this example:</span></span>

- <span data-ttu-id="7d0c5-212">Provider: **eenmalige**</span><span class="sxs-lookup"><span data-stu-id="7d0c5-212">Provider: **OneTime**</span></span>
- <span data-ttu-id="7d0c5-213">InvoiceLineItemType: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="7d0c5-213">InvoiceLineItemType: **BillingLineItems**</span></span>
- <span data-ttu-id="7d0c5-214">Periode: **vorige**</span><span class="sxs-lookup"><span data-stu-id="7d0c5-214">Period: **Previous**</span></span>
- <span data-ttu-id="7d0c5-215">SeekOperation: **volgende**</span><span class="sxs-lookup"><span data-stu-id="7d0c5-215">SeekOperation: **Next**</span></span>

#### <a name="request-example-2"></a><span data-ttu-id="7d0c5-216">Voor beeld 2 aanvragen</span><span class="sxs-lookup"><span data-stu-id="7d0c5-216">Request example 2</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/unbilled/lineitems?provider=onetime&invoiceLineItemType=billinglineitems&currencyCode=usd&period=previous&size=2000&seekoperation=next HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-ContinuationToken: d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-2"></a><span data-ttu-id="7d0c5-217">Antwoord voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="7d0c5-217">Response example 2</span></span>

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
            "partnerId": "0c924e8d-4852-4692-a4d7-7dd0dc09ad80",
            "customerId": "org:d7f565f5-5367-492f-a465-9e2057c5e3c3",
            "customerName": "TEST_TEST_GTM1",
            "customerDomainName": "TESTTESTGTM1.ccsctp.net",
            "customerCountry": "US",
            "invoiceNumber": "",
            "mpnId": "1234567",
            "resellerMpnId": 0,
            "orderId": "Oi2kwDPEOyGEFUkESk3QR4XSxcpvwp1x1",
            "orderDate": "2019-02-04T17:59:53.1628078Z",
            "productId": "DZH318Z0BXWC",
            "skuId": "0005",
            "availabilityId": "DZH318Z0BH9R",
            "productName": "Test WAF-as-a-Service",
            "skuName": "Test WaaS - Large Plan",
            "chargeType": "New",
            "unitPrice": 2598,
            "effectiveUnitPrice": 2598,
            "unitType": "",
            "quantity": 1,
            "subtotal": 2598,
            "taxTotal": 0,
            "totalForCustomer": 0,
            "currency": "USD",
            "publisherName": "Test Networks, Inc.",
            "publisherId": "21223810",
            "subscriptionDescription": "",
            "subscriptionId": "12345678-28db-48c2-8c30-04d7c9455746",
            "chargeStartDate": "2019-02-04T09:22:34.6455294-08:00",
            "chargeEndDate": "2019-03-03T09:22:34.6455294-08:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "123456ad566",
            "priceAdjustmentDescription": "[\"15.0% Partner earned credit for services managed\",\"100.0% Tier 1 Discount\"]",
            "discountDetails": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "billableQuantity": 0.737083,
            "meterDescription": "",
            "reservationOrderId": ""
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        }
    ],
    "links": {
        "self": {
             "uri": "/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

#### <a name="request-example-3"></a><span data-ttu-id="7d0c5-218">Voor beeld 3 aanvragen</span><span class="sxs-lookup"><span data-stu-id="7d0c5-218">Request example 3</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/unbilled/lineitems?provider=OneTime&invoiceLineItemType=UsageLineItems&currencyCode=usd&period=previous&size=2000&seekoperation=next HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-ContinuationToken: d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-3"></a><span data-ttu-id="7d0c5-219">Antwoord voorbeeld 3</span><span class="sxs-lookup"><span data-stu-id="7d0c5-219">Response example 3</span></span>

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
            "partnerId": "0c924e8d-4852-4692-a4d7-7dd0dc09ad80",
            "PartnerName": "testPartner",
            "customerId": "org:d7f565f5-5367-492f-a465-9e2057c5e3c3",
            "customerName": "TEST_TEST_GTM1",
            "customerDomainName": "TESTTESTGTM1.ccsctp.net",
            "invoiceNumber": "T11ETHHDDD",
            "productId": "DZH318Z0BXWC",
            "skuId": "0005",
            "availabilityId": "DZH318Z0BH9R",
            "productName": "Test WAF-as-a-Service",
            "publisherId": "21223810",
            "subscriptionId": "12345678-28db-48c2-8c30-04d7c9455746",
            "subscriptionDescription": "sub description",
            "chargeStartDate": "2019-02-04T09:22:34.6455294-08:00",
            "chargeEndDate": "2019-03-03T09:22:34.6455294-08:00",
            "UsageDate": "2019-02-07T09:22:34.6455294-08:00",
            "MeterType": "type",
            "MeterCategory": "category",
            "MeterId": "21312312312-fdsfsd",
            "MeterSubCategory": "subcategory",
            "MeterName": "meter name",
            "MeterRegion": "meter region",
            "UnitOfMeasure": "11",
            "skuName": "Test WaaS - Large Plan",
            "publisherName": "Test Networks, Inc.",
            "chargeType": "New",
            "unitPrice": 2598,
            "effectiveUnitPrice": 2598,
            "unitType": "",
            "quantity": 1,
            "subtotal": 2598,
            "taxTotal": 0,
            "totalForCustomer": 0,
            "currency": "USD",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "123456ad566",
            "discountDetails": "",
            "providerSource": "All",
            "RateOfPartnerEarnedCredit": 0.15,
            "IsPartnerEarnedCreditApplied": true,
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        }
    ],
    "links": {
        "self": {
             "uri": "/invoices/unbilled/lineitems?provider=all&invoicelineitemtype=billinglineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
