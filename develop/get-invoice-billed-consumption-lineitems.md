---
title: Gefactureerde commerciële verbruiksregelitems ontvangen
description: U kunt een verzameling factuurregelitem voor commercieel verbruik (gesloten dagelijks beoordeeld gebruiksregelitem) voor een opgegeven factuur ophalen met behulp van de Partner Center API's.
ms.date: 01/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 1406938b16e5a363a73c36ef0338eb5fc4305279
ms.sourcegitcommit: 89aefbff6dbe740b6f27a888492ffc2e5f98b1e9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/24/2021
ms.locfileid: "110325442"
---
# <a name="get-invoice-billed-commercial-consumption-line-items"></a><span data-ttu-id="a831a-103">Gefactureerde commerciële verbruiksregelitems ontvangen</span><span class="sxs-lookup"><span data-stu-id="a831a-103">Get invoice billed commercial consumption line items</span></span>

<span data-ttu-id="a831a-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="a831a-104">**Applies to:**</span></span>

- <span data-ttu-id="a831a-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="a831a-105">Partner Center</span></span>

<span data-ttu-id="a831a-106">U kunt de volgende methoden gebruiken om een verzameling gegevens op te halen voor factuurregelitems voor commercieel verbruik (ook wel gesloten, dagelijks beoordeelde gebruikslijnitems genoemd) voor een opgegeven factuur.</span><span class="sxs-lookup"><span data-stu-id="a831a-106">You can use the following methods to get a collection of details for commercial consumption invoice line items (also known as closed daily rated usage line items) for a specified invoice.</span></span>


## <a name="prerequisites"></a><span data-ttu-id="a831a-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a831a-107">Prerequisites</span></span>

- <span data-ttu-id="a831a-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a831a-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a831a-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="a831a-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="a831a-110">Een factuur-id.</span><span class="sxs-lookup"><span data-stu-id="a831a-110">An invoice identifier.</span></span> <span data-ttu-id="a831a-111">Hiermee wordt de factuur geïdentificeerd waarvoor de regelitems moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a831a-111">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="a831a-112">C\#</span><span class="sxs-lookup"><span data-stu-id="a831a-112">C\#</span></span>

<span data-ttu-id="a831a-113">Als u de commerciële regelitems voor de opgegeven factuur wilt ophalen, moet u het factuurobject ophalen:</span><span class="sxs-lookup"><span data-stu-id="a831a-113">To get the commercial line items for the specified invoice, you must retrieve the invoice object:</span></span>

1. <span data-ttu-id="a831a-114">Roep de [**ById-methode**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) aan om een interface voor factuurbewerkingen voor de opgegeven factuur op te halen.</span><span class="sxs-lookup"><span data-stu-id="a831a-114">Call the [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) method to get an interface to invoice operations for the specified invoice.</span></span>

2. <span data-ttu-id="a831a-115">Roep de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) om het factuurobject op te halen.</span><span class="sxs-lookup"><span data-stu-id="a831a-115">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the invoice object.</span></span> <span data-ttu-id="a831a-116">Het factuurobject bevat alle informatie voor de opgegeven factuur.</span><span class="sxs-lookup"><span data-stu-id="a831a-116">The invoice object contains all of the information for the specified invoice.</span></span>

<span data-ttu-id="a831a-117">De **provider** identificeert de bron van de gefactureerde details (bijvoorbeeld **een keer**).</span><span class="sxs-lookup"><span data-stu-id="a831a-117">The **Provider** identifies the source of the billed detail information (for example, **onetime**).</span></span> <span data-ttu-id="a831a-118">Met **InvoiceLineItemType** wordt het type opgegeven (bijvoorbeeld **UsageLineItem).**</span><span class="sxs-lookup"><span data-stu-id="a831a-118">The **InvoiceLineItemType** specifies the type (for example, **UsageLineItem**).</span></span>

<span data-ttu-id="a831a-119">In de volgende voorbeeldcode wordt een **foreach-lus** gebruikt om de verzameling regelitems te verwerken.</span><span class="sxs-lookup"><span data-stu-id="a831a-119">The following example code uses a **foreach** loop to process the line items collection.</span></span> <span data-ttu-id="a831a-120">Voor elk **InvoiceLineItemType** wordt een afzonderlijke verzameling regelitems opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a831a-120">A separate collection of line items is retrieved for each **InvoiceLineItemType**.</span></span>

<span data-ttu-id="a831a-121">Een verzameling regelitems ophalen die overeenkomen met een **InvoiceDetail-exemplaar:**</span><span class="sxs-lookup"><span data-stu-id="a831a-121">To get a collection of line items that correspond to an **InvoiceDetail** instance:</span></span>

1. <span data-ttu-id="a831a-122">Geef de **BillingProvider** en **InvoiceLineItemType** van het exemplaar door aan de [**methode By.**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by)</span><span class="sxs-lookup"><span data-stu-id="a831a-122">Pass the instance's **BillingProvider** and **InvoiceLineItemType** to the [**By**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) method.</span></span>

2. <span data-ttu-id="a831a-123">Roep de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) om de bijbehorende regelitems op te halen.</span><span class="sxs-lookup"><span data-stu-id="a831a-123">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the associated line items.</span></span>
3. <span data-ttu-id="a831a-124">Maak een enumerator om de verzameling te doorlopen, zoals wordt weergegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="a831a-124">Create an enumerator to traverse the collection as shown in the following example.</span></span>

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

<span data-ttu-id="a831a-125">Zie het volgende voor een vergelijkbaar voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a831a-125">For a similar example, see the following:</span></span>

- <span data-ttu-id="a831a-126">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="a831a-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="a831a-127">Project: **Partnercentrum-SDK Samples**</span><span class="sxs-lookup"><span data-stu-id="a831a-127">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="a831a-128">Klasse: **GetBilledConsumptionReconLineItemsPaging.cs**</span><span class="sxs-lookup"><span data-stu-id="a831a-128">Class: **GetBilledConsumptionReconLineItemsPaging.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="a831a-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="a831a-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a831a-130">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="a831a-130">Request syntax</span></span>

<span data-ttu-id="a831a-131">Gebruik de eerste syntaxis om een volledige lijst van elk regelitem voor de opgegeven factuur te retourneren.</span><span class="sxs-lookup"><span data-stu-id="a831a-131">Use the first syntax to return a full list of every line item for the given invoice.</span></span> <span data-ttu-id="a831a-132">Gebruik voor grote facturen de tweede syntaxis met een opgegeven grootte en offset op basis van 0 om een lijst met regelitems met pagina's te retourneren.</span><span class="sxs-lookup"><span data-stu-id="a831a-132">For large invoices, use the second syntax with a specified size and 0-based offset to return a paged list of line items.</span></span> <span data-ttu-id="a831a-133">Gebruik de derde syntaxis om de volgende pagina met recon line-items op te halen met behulp van `seekOperation = "Next"` .</span><span class="sxs-lookup"><span data-stu-id="a831a-133">Use the third syntax to get the next page of recon line items using `seekOperation = "Next"`.</span></span>

| <span data-ttu-id="a831a-134">Methode</span><span class="sxs-lookup"><span data-stu-id="a831a-134">Method</span></span>  | <span data-ttu-id="a831a-135">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="a831a-135">Request URI</span></span>                                                                                                                                                     |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a831a-136">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="a831a-136">**GET**</span></span> | <span data-ttu-id="a831a-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a831a-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode} HTTP/1.1</span></span>                              |
| <span data-ttu-id="a831a-138">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="a831a-138">**GET**</span></span> | <span data-ttu-id="a831a-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&size={size} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a831a-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&size={size} HTTP/1.1</span></span>  |
| <span data-ttu-id="a831a-140">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="a831a-140">**GET**</span></span> | <span data-ttu-id="a831a-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&size={size}&seekOperation=Next</span><span class="sxs-lookup"><span data-stu-id="a831a-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&size={size}&seekOperation=Next</span></span>                               |

#### <a name="uri-parameters"></a><span data-ttu-id="a831a-142">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="a831a-142">URI parameters</span></span>

<span data-ttu-id="a831a-143">Gebruik de volgende URI en queryparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="a831a-143">Use the following URI and query parameters when creating the request.</span></span>

| <span data-ttu-id="a831a-144">Naam</span><span class="sxs-lookup"><span data-stu-id="a831a-144">Name</span></span>                   | <span data-ttu-id="a831a-145">Type</span><span class="sxs-lookup"><span data-stu-id="a831a-145">Type</span></span>   | <span data-ttu-id="a831a-146">Vereist</span><span class="sxs-lookup"><span data-stu-id="a831a-146">Required</span></span> | <span data-ttu-id="a831a-147">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a831a-147">Description</span></span>                                                       |
|------------------------|--------|----------|-------------------------------------------------------------------|
| <span data-ttu-id="a831a-148">factuur-id</span><span class="sxs-lookup"><span data-stu-id="a831a-148">invoice-id</span></span>             | <span data-ttu-id="a831a-149">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="a831a-149">string</span></span> | <span data-ttu-id="a831a-150">Yes</span><span class="sxs-lookup"><span data-stu-id="a831a-150">Yes</span></span>      | <span data-ttu-id="a831a-151">Een tekenreeks die de factuur identificeert.</span><span class="sxs-lookup"><span data-stu-id="a831a-151">A string that identifies the invoice.</span></span>                             |
| <span data-ttu-id="a831a-152">Provider</span><span class="sxs-lookup"><span data-stu-id="a831a-152">provider</span></span>               | <span data-ttu-id="a831a-153">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="a831a-153">string</span></span> | <span data-ttu-id="a831a-154">Yes</span><span class="sxs-lookup"><span data-stu-id="a831a-154">Yes</span></span>      | <span data-ttu-id="a831a-155">De provider: 'OneTime'.</span><span class="sxs-lookup"><span data-stu-id="a831a-155">The provider: "OneTime".</span></span>                                  |
| <span data-ttu-id="a831a-156">invoice-line-item-type</span><span class="sxs-lookup"><span data-stu-id="a831a-156">invoice-line-item-type</span></span> | <span data-ttu-id="a831a-157">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="a831a-157">string</span></span> | <span data-ttu-id="a831a-158">Yes</span><span class="sxs-lookup"><span data-stu-id="a831a-158">Yes</span></span>      | <span data-ttu-id="a831a-159">Het type factuurdetails: UsageLineItems.</span><span class="sxs-lookup"><span data-stu-id="a831a-159">The type of invoice detail: "UsageLineItems".</span></span> |
| <span data-ttu-id="a831a-160">currencyCode</span><span class="sxs-lookup"><span data-stu-id="a831a-160">currencyCode</span></span>           | <span data-ttu-id="a831a-161">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="a831a-161">string</span></span> | <span data-ttu-id="a831a-162">Yes</span><span class="sxs-lookup"><span data-stu-id="a831a-162">Yes</span></span>      | <span data-ttu-id="a831a-163">De valutacode voor de gefactureerde regelitems.</span><span class="sxs-lookup"><span data-stu-id="a831a-163">The currency code for the billed line items.</span></span>                    |
| <span data-ttu-id="a831a-164">period</span><span class="sxs-lookup"><span data-stu-id="a831a-164">period</span></span>                 | <span data-ttu-id="a831a-165">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="a831a-165">string</span></span> | <span data-ttu-id="a831a-166">Yes</span><span class="sxs-lookup"><span data-stu-id="a831a-166">Yes</span></span>      | <span data-ttu-id="a831a-167">De periode voor gefactureerde recon.</span><span class="sxs-lookup"><span data-stu-id="a831a-167">The period for billed recon.</span></span> <span data-ttu-id="a831a-168">voorbeeld: current, previous.</span><span class="sxs-lookup"><span data-stu-id="a831a-168">example: current, previous.</span></span>        |
| <span data-ttu-id="a831a-169">grootte</span><span class="sxs-lookup"><span data-stu-id="a831a-169">size</span></span>                   | <span data-ttu-id="a831a-170">getal</span><span class="sxs-lookup"><span data-stu-id="a831a-170">number</span></span> | <span data-ttu-id="a831a-171">No</span><span class="sxs-lookup"><span data-stu-id="a831a-171">No</span></span>       | <span data-ttu-id="a831a-172">Het maximum aantal items dat moet worden retourneren.</span><span class="sxs-lookup"><span data-stu-id="a831a-172">The maximum number of items to return.</span></span> <span data-ttu-id="a831a-173">De standaardgrootte is 2000</span><span class="sxs-lookup"><span data-stu-id="a831a-173">Default size is 2000</span></span>       |
| <span data-ttu-id="a831a-174">zoekoperation</span><span class="sxs-lookup"><span data-stu-id="a831a-174">seekOperation</span></span>          | <span data-ttu-id="a831a-175">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="a831a-175">string</span></span> | <span data-ttu-id="a831a-176">No</span><span class="sxs-lookup"><span data-stu-id="a831a-176">No</span></span>       | <span data-ttu-id="a831a-177">Stel seekOperation = Volgende in om de volgende pagina met recon line-items op te halen.</span><span class="sxs-lookup"><span data-stu-id="a831a-177">Set seekOperation=Next to get the next page of recon line items.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="a831a-178">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="a831a-178">Request headers</span></span>

<span data-ttu-id="a831a-179">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="a831a-179">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a831a-180">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="a831a-180">Request body</span></span>

<span data-ttu-id="a831a-181">Geen.</span><span class="sxs-lookup"><span data-stu-id="a831a-181">None.</span></span>

## <a name="rest-response"></a><span data-ttu-id="a831a-182">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="a831a-182">REST response</span></span>

<span data-ttu-id="a831a-183">Als dit lukt, bevat het antwoord de verzameling regelitemdetails.</span><span class="sxs-lookup"><span data-stu-id="a831a-183">If successful, the response contains the collection of line item details.</span></span>

<span data-ttu-id="a831a-184">Voor het regelitem **ChargeType** wordt de waarde **Aankoop** aan **Nieuw.**</span><span class="sxs-lookup"><span data-stu-id="a831a-184">For the line item **ChargeType**, the value **Purchase** is mapped to **New**.</span></span> <span data-ttu-id="a831a-185">De waarde **Restitutie** wordt aan **Annuleren toebetaald.**</span><span class="sxs-lookup"><span data-stu-id="a831a-185">The value **Refund** is mapped to **Cancel**.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a831a-186">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="a831a-186">Response success and error codes</span></span>

<span data-ttu-id="a831a-187">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="a831a-187">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a831a-188">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="a831a-188">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a831a-189">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="a831a-189">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

## <a name="rest-examples"></a><span data-ttu-id="a831a-190">REST-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="a831a-190">REST examples</span></span>

### <a name="request-response-example-1"></a><span data-ttu-id="a831a-191">Voorbeeld van aanvraag-antwoord 1</span><span class="sxs-lookup"><span data-stu-id="a831a-191">Request-response example 1</span></span>

<span data-ttu-id="a831a-192">De details voor dit voorbeeld van een REST-aanvraag en -antwoord zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="a831a-192">The details for this example REST request and response are as follows:</span></span>

- <span data-ttu-id="a831a-193">**Provider:** **OneTime**</span><span class="sxs-lookup"><span data-stu-id="a831a-193">**Provider**: **OneTime**</span></span>
- <span data-ttu-id="a831a-194">**InvoiceLineItemType:** **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="a831a-194">**InvoiceLineItemType**: **UsageLineItems**</span></span>
- <span data-ttu-id="a831a-195">**Periode:** **vorige**</span><span class="sxs-lookup"><span data-stu-id="a831a-195">**Period**: **Previous**</span></span>

#### <a name="request-example-1"></a><span data-ttu-id="a831a-196">Aanvraagvoorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="a831a-196">Request example 1</span></span>

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

#### <a name="response-example-1"></a><span data-ttu-id="a831a-197">Antwoordvoorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="a831a-197">Response example 1</span></span>

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

### <a name="request-response-example-2"></a><span data-ttu-id="a831a-198">Voorbeeld 2 van aanvraag-antwoord</span><span class="sxs-lookup"><span data-stu-id="a831a-198">Request-response example 2</span></span>

<span data-ttu-id="a831a-199">De details voor dit voorbeeld van een REST-aanvraag en -antwoord zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="a831a-199">The details for this example REST request and response are as follows:</span></span>

- <span data-ttu-id="a831a-200">**Provider:** **OneTime**</span><span class="sxs-lookup"><span data-stu-id="a831a-200">**Provider**: **OneTime**</span></span>
- <span data-ttu-id="a831a-201">**InvoiceLineItemType:** **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="a831a-201">**InvoiceLineItemType**: **UsageLineItems**</span></span>
- <span data-ttu-id="a831a-202">**Periode:** **vorige**</span><span class="sxs-lookup"><span data-stu-id="a831a-202">**Period**: **Previous**</span></span>
- <span data-ttu-id="a831a-203">**Zoekoperation:** **volgende**</span><span class="sxs-lookup"><span data-stu-id="a831a-203">**SeekOperation**: **Next**</span></span>

#### <a name="request-example-2"></a><span data-ttu-id="a831a-204">Aanvraagvoorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="a831a-204">Request example 2</span></span>

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

## <a name="response-example-2"></a><span data-ttu-id="a831a-205">Antwoordvoorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="a831a-205">Response example 2</span></span>

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
