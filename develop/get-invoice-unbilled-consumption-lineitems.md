---
title: Niet-gefactureerde regelitems voor commercieel verbruik van facturen ontvangen
description: U kunt een verzameling niet-gefactureerde regelitemgegevens voor commercieel verbruik ophalen voor een opgegeven factuur met behulp van Partner Center API's.
ms.date: 01/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f7c74bedfd6412fc5954ed2ddc1388936e418fa3
ms.sourcegitcommit: 722992eea6f8ea366dc088e5dd1ee63c17d56f61
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224765"
---
# <a name="get-invoice-unbilled-commercial-consumption-line-items"></a><span data-ttu-id="7b128-103">Niet-gefactureerde regelitems voor commercieel verbruik van facturen ontvangen</span><span class="sxs-lookup"><span data-stu-id="7b128-103">Get invoice unbilled commercial consumption line items</span></span>

<span data-ttu-id="7b128-104">Informatie over het ophalen van een verzameling niet-gebillede regelitemdes voor commercieel verbruik.</span><span class="sxs-lookup"><span data-stu-id="7b128-104">How to get a collection of unbilled commercial consumption line item details.</span></span>

<span data-ttu-id="7b128-105">U kunt de volgende methoden gebruiken om programmatisch een verzameling niet-gebillede regelitems voor commercieel verbruik (ook wel bekend als regelitems voor open gebruik) op te halen.</span><span class="sxs-lookup"><span data-stu-id="7b128-105">You can use the following methods to get a collection of details unbilled commercial consumption line items (also known as open usage line items) programmatically.</span></span>

>[!NOTE]
><span data-ttu-id="7b128-106">Normaal gesproken duurt het 24 uur voordat het dagelijks beoordeelde gebruik wordt weergegeven in Partner Center of om te worden geopend via de API.</span><span class="sxs-lookup"><span data-stu-id="7b128-106">Daily-rated usage normally takes 24 hours to appear in Partner Center or to be accessed through the API.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7b128-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7b128-107">Prerequisites</span></span>

- <span data-ttu-id="7b128-108">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="7b128-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7b128-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="7b128-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="7b128-110">C\#</span><span class="sxs-lookup"><span data-stu-id="7b128-110">C\#</span></span>

<span data-ttu-id="7b128-111">De regelitems voor de opgegeven factuur op te halen:</span><span class="sxs-lookup"><span data-stu-id="7b128-111">To get the line items for the specified invoice:</span></span>

1. <span data-ttu-id="7b128-112">Roep de [**ById-methode**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) aan om een interface op te halen voor factuurbewerkingen voor de opgegeven factuur.</span><span class="sxs-lookup"><span data-stu-id="7b128-112">Call the [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) method to get an interface to invoice operations for the specified invoice.</span></span>

2. <span data-ttu-id="7b128-113">Roep de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) om het factuurobject op te halen.</span><span class="sxs-lookup"><span data-stu-id="7b128-113">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the invoice object.</span></span>

<span data-ttu-id="7b128-114">Het **factuurobject** bevat alle informatie voor de opgegeven factuur.</span><span class="sxs-lookup"><span data-stu-id="7b128-114">The **invoice object** contains all of the information for the specified invoice.</span></span> <span data-ttu-id="7b128-115">De **provider** identificeert de bron van de niet-gebileerde details (bijvoorbeeld **OneTime**).</span><span class="sxs-lookup"><span data-stu-id="7b128-115">The **Provider** identifies the source of the unbilled detail information (for example, **OneTime**).</span></span> <span data-ttu-id="7b128-116">**InvoiceLineItemType geeft** het type op (bijvoorbeeld **UsageLineItem).**</span><span class="sxs-lookup"><span data-stu-id="7b128-116">The **InvoiceLineItemType** specifies the type (for example, **UsageLineItem**).</span></span>

<span data-ttu-id="7b128-117">In de volgende voorbeeldcode wordt een **foreach-lus** gebruikt om de **verzameling InvoiceLineItems te** verwerken.</span><span class="sxs-lookup"><span data-stu-id="7b128-117">The following example code uses a **foreach** loop to process the **InvoiceLineItems** collection.</span></span> <span data-ttu-id="7b128-118">Voor elk **InvoiceLineItemType** wordt een afzonderlijke verzameling regelitems opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7b128-118">A separate collection of line items is retrieved for each **InvoiceLineItemType**.</span></span>

<span data-ttu-id="7b128-119">Een verzameling regelitems ophalen die overeenkomen met een **InvoiceDetail-exemplaar:**</span><span class="sxs-lookup"><span data-stu-id="7b128-119">To get a collection of line items that correspond to an **InvoiceDetail** instance:</span></span>

1. <span data-ttu-id="7b128-120">Geef de **BillingProvider** en **InvoiceLineItemType** van het exemplaar door aan de [**methode By.**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by)</span><span class="sxs-lookup"><span data-stu-id="7b128-120">Pass the instance's **BillingProvider** and **InvoiceLineItemType** to the [**By**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) method.</span></span>

2. <span data-ttu-id="7b128-121">Roep de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) om de bijbehorende regelitems op te halen.</span><span class="sxs-lookup"><span data-stu-id="7b128-121">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the associated line items.</span></span>
3. <span data-ttu-id="7b128-122">Maak een enumerator om de verzameling te doorlopen, zoals wordt weergegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="7b128-122">Create an enumerator to traverse the collection as shown in the following example.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string curencyCode;
// string period;
// int pageMaxSizeReconLineItems = 2000;

// all the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

var seekBasedResourceCollection = scopedPartnerOperations.Invoices.ById("unbilled").By("onetime", "usagelineitems", curencyCode, period, pageMaxSizeReconLineItems).Get();

var fetchNext = true;

ConsoleKeyInfo keyInfo;

var itemNumber = 1;
while (fetchNext)
{
    Console.Out.WriteLine("\tLine items count: " + seekBasedResourceCollection.Items.Count());

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
            seekBasedResourceCollection = scopedPartnerOperations.Invoices.ById("unbilled").By("onetime", "usagelineitems", curencyCode, period, pageMaxSizeReconLineItems).Seek(seekBasedResourceCollection.ContinuationToken, SeekOperation.Next);
        }
    }
}
```

<span data-ttu-id="7b128-123">Zie voor een vergelijkbaar voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7b128-123">For a similar example, see:</span></span>

- <span data-ttu-id="7b128-124">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="7b128-124">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="7b128-125">Project: **Partnercentrum-SDK Voorbeelden**</span><span class="sxs-lookup"><span data-stu-id="7b128-125">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="7b128-126">Klasse: **GetUnBilledConsumptionReconLineItemsPaging.cs**</span><span class="sxs-lookup"><span data-stu-id="7b128-126">Class: **GetUnBilledConsumptionReconLineItemsPaging.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="7b128-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="7b128-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7b128-128">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="7b128-128">Request syntax</span></span>

<span data-ttu-id="7b128-129">U kunt de volgende syntaxis gebruiken voor uw REST-aanvraag, afhankelijk van uw use-case.</span><span class="sxs-lookup"><span data-stu-id="7b128-129">You can use the following syntaxes for your REST request, depending on your use case.</span></span> <span data-ttu-id="7b128-130">Zie de beschrijvingen voor elke syntaxis voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7b128-130">For more information, see the descriptions for each syntax.</span></span>

| <span data-ttu-id="7b128-131">Methode</span><span class="sxs-lookup"><span data-stu-id="7b128-131">Method</span></span>  | <span data-ttu-id="7b128-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="7b128-132">Request URI</span></span>                                                                                                                                                                                              | <span data-ttu-id="7b128-133">Beschrijving van gebruikscase voor syntaxis</span><span class="sxs-lookup"><span data-stu-id="7b128-133">Description of syntax use case</span></span>                                                                                                     |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7b128-134">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7b128-134">**GET**</span></span> | <span data-ttu-id="7b128-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7b128-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period} HTTP/1.1</span></span>                       | <span data-ttu-id="7b128-136">Gebruik deze syntaxis om een volledige lijst met alle regelitem voor de opgegeven factuur te retourneren.</span><span class="sxs-lookup"><span data-stu-id="7b128-136">Use this syntax to return a full list of every line item for the given invoice.</span></span>                                                    |
| <span data-ttu-id="7b128-137">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7b128-137">**GET**</span></span> | <span data-ttu-id="7b128-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period}&size={size} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7b128-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period}&size={size} HTTP/1.1</span></span>           | <span data-ttu-id="7b128-139">Gebruik deze syntaxis voor grote facturen.</span><span class="sxs-lookup"><span data-stu-id="7b128-139">Use this syntax for large invoices.</span></span> <span data-ttu-id="7b128-140">Gebruik deze syntaxis met een opgegeven grootte en offset op basis van 0 om een lijst met pagina's met regelitems te retourneren.</span><span class="sxs-lookup"><span data-stu-id="7b128-140">Use this syntax with a specified size and 0-based offset to return a paged list of line items.</span></span> |
| <span data-ttu-id="7b128-141">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7b128-141">**GET**</span></span> | <span data-ttu-id="7b128-142">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period}&size={size}&seekOperation=Next</span><span class="sxs-lookup"><span data-stu-id="7b128-142">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period}&size={size}&seekOperation=Next</span></span> | <span data-ttu-id="7b128-143">Gebruik deze syntaxis om de volgende pagina met afstemmingsregelitems op te halen met behulp van `seekOperation = "Next"` .</span><span class="sxs-lookup"><span data-stu-id="7b128-143">Use this syntax to get the next page of reconciliation line items using `seekOperation = "Next"`.</span></span>                                  |

#### <a name="uri-parameters"></a><span data-ttu-id="7b128-144">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="7b128-144">URI parameters</span></span>

<span data-ttu-id="7b128-145">Gebruik de volgende URI en queryparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="7b128-145">Use the following URI and query parameters when creating the request.</span></span>

| <span data-ttu-id="7b128-146">Naam</span><span class="sxs-lookup"><span data-stu-id="7b128-146">Name</span></span>                   | <span data-ttu-id="7b128-147">Type</span><span class="sxs-lookup"><span data-stu-id="7b128-147">Type</span></span>   | <span data-ttu-id="7b128-148">Vereist</span><span class="sxs-lookup"><span data-stu-id="7b128-148">Required</span></span> | <span data-ttu-id="7b128-149">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7b128-149">Description</span></span>                                                                                                                                                                                                                                |
|------------------------|--------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7b128-150">Provider</span><span class="sxs-lookup"><span data-stu-id="7b128-150">provider</span></span>               | <span data-ttu-id="7b128-151">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7b128-151">string</span></span> | <span data-ttu-id="7b128-152">Yes</span><span class="sxs-lookup"><span data-stu-id="7b128-152">Yes</span></span>      | <span data-ttu-id="7b128-153">De provider:**OneTime.**</span><span class="sxs-lookup"><span data-stu-id="7b128-153">The provider: "**OneTime**".</span></span>                                                                                                                                                                                                               |
| <span data-ttu-id="7b128-154">invoice-line-item-type</span><span class="sxs-lookup"><span data-stu-id="7b128-154">invoice-line-item-type</span></span> | <span data-ttu-id="7b128-155">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7b128-155">string</span></span> | <span data-ttu-id="7b128-156">Yes</span><span class="sxs-lookup"><span data-stu-id="7b128-156">Yes</span></span>      | <span data-ttu-id="7b128-157">Het type factuurdetails: "**UsageLineItems**", "**UsageLineItems**".</span><span class="sxs-lookup"><span data-stu-id="7b128-157">The type of invoice detail: "**UsageLineItems**", "**UsageLineItems**".</span></span>                                                                                                                                                                    |
| <span data-ttu-id="7b128-158">currencyCode</span><span class="sxs-lookup"><span data-stu-id="7b128-158">currencyCode</span></span>           | <span data-ttu-id="7b128-159">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7b128-159">string</span></span> | <span data-ttu-id="7b128-160">Yes</span><span class="sxs-lookup"><span data-stu-id="7b128-160">Yes</span></span>      | <span data-ttu-id="7b128-161">De valutacode voor de niet-gebillede regelitems.</span><span class="sxs-lookup"><span data-stu-id="7b128-161">The currency code for the unbilled line items.</span></span>                                                                                                                                                                                             |
| <span data-ttu-id="7b128-162">period</span><span class="sxs-lookup"><span data-stu-id="7b128-162">period</span></span>                 | <span data-ttu-id="7b128-163">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7b128-163">string</span></span> | <span data-ttu-id="7b128-164">Yes</span><span class="sxs-lookup"><span data-stu-id="7b128-164">Yes</span></span>      | <span data-ttu-id="7b128-165">De periode voor niet-gebillede recon (bijvoorbeeld: **huidige**, **vorige**).</span><span class="sxs-lookup"><span data-stu-id="7b128-165">The period for unbilled recon (for example: **current**, **previous**).</span></span> <span data-ttu-id="7b128-166">Stel dat u in januari een query moet uitvoeren op uw niet-gefactureerde gebruiksgegevens van de factureringscyclus (01-01-2020 – 31-01-2020), kies de periode **'Huidig',** anders **'Vorige'.**</span><span class="sxs-lookup"><span data-stu-id="7b128-166">Suppose you need to query your unbilled usage data of the billing cycle (01/01/2020 – 01/31/2020) in January, choose period as **"Current,"** else **"Previous."**</span></span> |
| <span data-ttu-id="7b128-167">grootte</span><span class="sxs-lookup"><span data-stu-id="7b128-167">size</span></span>                   | <span data-ttu-id="7b128-168">getal</span><span class="sxs-lookup"><span data-stu-id="7b128-168">number</span></span> | <span data-ttu-id="7b128-169">No</span><span class="sxs-lookup"><span data-stu-id="7b128-169">No</span></span>       | <span data-ttu-id="7b128-170">Het maximum aantal items dat moet worden retourneren.</span><span class="sxs-lookup"><span data-stu-id="7b128-170">The maximum number of items to return.</span></span> <span data-ttu-id="7b128-171">De standaardgrootte is 2000.</span><span class="sxs-lookup"><span data-stu-id="7b128-171">The default size is 2000.</span></span>                                                                                                                                                                           |
| <span data-ttu-id="7b128-172">zoekoperation</span><span class="sxs-lookup"><span data-stu-id="7b128-172">seekOperation</span></span>          | <span data-ttu-id="7b128-173">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7b128-173">string</span></span> | <span data-ttu-id="7b128-174">No</span><span class="sxs-lookup"><span data-stu-id="7b128-174">No</span></span>       | <span data-ttu-id="7b128-175">Stel `seekOperation=Next` in om de volgende pagina met afstemmingsregelitems op te halen.</span><span class="sxs-lookup"><span data-stu-id="7b128-175">Set `seekOperation=Next` to get the next page of reconciliation line items.</span></span>                                                                                                                                                                |

### <a name="request-headers"></a><span data-ttu-id="7b128-176">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="7b128-176">Request headers</span></span>

<span data-ttu-id="7b128-177">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="7b128-177">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7b128-178">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="7b128-178">Request body</span></span>

<span data-ttu-id="7b128-179">Geen.</span><span class="sxs-lookup"><span data-stu-id="7b128-179">None.</span></span>

## <a name="rest-response"></a><span data-ttu-id="7b128-180">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="7b128-180">REST response</span></span>

<span data-ttu-id="7b128-181">Als dit lukt, bevat het antwoord de verzameling regelitemdetails.</span><span class="sxs-lookup"><span data-stu-id="7b128-181">If successful, the response contains the collection of line item details.</span></span>

<span data-ttu-id="7b128-182">*Voor het regelitem **ChargeType** wordt de waarde **Aankoop** aan **Nieuw** en de waarde **Restitutie** is aan **Annuleren.***</span><span class="sxs-lookup"><span data-stu-id="7b128-182">*For the line item **ChargeType**, the value **Purchase** is mapped to **New** and the value **Refund** is mapped to **Cancel**.*</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7b128-183">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="7b128-183">Response success and error codes</span></span>

<span data-ttu-id="7b128-184">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="7b128-184">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7b128-185">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="7b128-185">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7b128-186">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="7b128-186">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

## <a name="request-response-examples"></a><span data-ttu-id="7b128-187">Voorbeelden van aanvraag-antwoord</span><span class="sxs-lookup"><span data-stu-id="7b128-187">Request-response examples</span></span>

### <a name="request-response-example-1"></a><span data-ttu-id="7b128-188">Voorbeeld van aanvraag-antwoord 1</span><span class="sxs-lookup"><span data-stu-id="7b128-188">Request-response example 1</span></span>

<span data-ttu-id="7b128-189">De volgende details zijn van toepassing op dit voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7b128-189">The following details apply to this example:</span></span>

- <span data-ttu-id="7b128-190">**Provider:** **OneTime**</span><span class="sxs-lookup"><span data-stu-id="7b128-190">**Provider**: **OneTime**</span></span>
- <span data-ttu-id="7b128-191">**InvoiceLineItemType:** **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="7b128-191">**InvoiceLineItemType**: **UsageLineItems**</span></span>
- <span data-ttu-id="7b128-192">**Periode:** **vorige**</span><span class="sxs-lookup"><span data-stu-id="7b128-192">**Period**: **Previous**</span></span>

#### <a name="request-example-1"></a><span data-ttu-id="7b128-193">Aanvraagvoorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="7b128-193">Request example 1</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1//invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

### <a name="response-example-1"></a><span data-ttu-id="7b128-194">Antwoordvoorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="7b128-194">Response example 1</span></span>

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
            "partnerId": "00083575-bbd0-54de-b2ad-0f5b0e927d71",
            "partnerName": "MTBC",
            "customerId": "",
            "customerName": "",
            "customerDomainName": "",
            "invoiceNumber": "",
            "productId": "",
            "skuId": "",
            "availabilityId": "",
            "skuName": "VM-Series Next-Generation Firewall (Bundle 2 PAYG)",
            "productName": "VM-Series Next Generation Firewall",
            "publisherName": "Test Alto Networks, Inc.",
            "publisherId": "",
            "subscriptionId": "12345678-04d9-421c-baf8-e3b8dd62ddba",
            "subscriptionDescription": "Pay-As-You-Go",
            "chargeStartDate": "2019-01-01T00:00:00Z",
            "chargeEndDate": "2019-02-01T00:00:00Z",
            "usageDate": "2019-01-01T00:00:00Z",
            "meterType": "1 Compute Hour - 4core",
            "meterCategory": "Virtual Machine Licenses",
            "meterId": "4core",
            "meterSubCategory": "VM-Series Next Generation Firewall",
            "meterName": "VM-Series Next Generation Firewall - VM-Series Next-Generation Firewall (Bundle 2 PAYG) - 4 Core Hours",
            "meterRegion": "",
            "unitOfMeasure": "1 Hour",
            "resourceLocation": "EASTUS",
            "consumedService": "Microsoft.Compute",
            "resourceGroup": "ECH-PAN-RG",
            "resourceUri": "/subscriptions/12345678-04d9-421c-baf8-e3b8dd62ddba/resourceGroups/ECH-PAN-RG/providers/Microsoft.Compute/virtualMachines/echpanfw",
            "tags": "",
            "additionalInfo": "{  \"ImageType\": null,  \"ServiceType\": \"Standard_D3_v2\",  \"VMName\": null,  \"VMProperties\": null,  \"UsageType\": \"ComputeHR_SW\"}",
            "serviceInfo1": "",
            "serviceInfo2": "",
            "customerCountry": "",
            "mpnId": "1234567",
            "resellerMpnId": "",
            "chargeType": "",
            "unitPrice": 1.2799888920023,
            "quantity": 24.0,
            "unitType": "",
            "billingPreTaxTotal": 30.7197334080551,
            "billingCurrency": "USD",
            "pricingPreTaxTotal": 30.7197334080551,
            "pricingCurrency": "USD",
            "entitlementId": "1234547f-b249-4edd-9319-637862d8c0b4",
            "entitlementDescription": "Partner Subscription",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "effectiveUnitPrice": 0,
            "rateOfPartnerEarnedCredit": 0,
            "rateOfCredit": 0,
            "creditType": "Credit Not Applied",
            "invoiceLineItemType": "usage_line_items",
            "billingProvider": "marketplace",
            "attributes": {
                "objectType": "DailyRatedUsageLineItem"
            }
         },
         {
            "partnerId": "00083575-bbd0-54de-b2ad-0f5b0e927d71",
            "partnerName": "MTBC",
            "customerId": "",
            "customerName": "",
            "customerDomainName": "",
            "invoiceNumber": "",
            "productId": "",
            "skuId": "",
            "availabilityId": "",
            "skuName": "VM-Series Next-Generation Firewall (Bundle 2 PAYG)",
            "productName": "VM-Series Next Generation Firewall",
            "publisherName": "Test Alto Networks, Inc.",
            "publisherId": "",
            "subscriptionId": "12345678-04d9-421c-baf8-e3b8dd62ddba",
            "subscriptionDescription": "Pay-As-You-Go",
            "chargeStartDate": "2019-01-01T00:00:00Z",
            "chargeEndDate": "2019-02-01T00:00:00Z",
            "usageDate": "2019-01-02T00:00:00Z",
            "meterType": "1 Compute Hour - 4core",
            "meterCategory": "Virtual Machine Licenses",
            "meterId": "4core",
            "meterSubCategory": "VM-Series Next Generation Firewall",
            "meterName": "VM-Series Next Generation Firewall - VM-Series Next-Generation Firewall (Bundle 2 PAYG) - 4 Core Hours",
            "meterRegion": "",
            "unitOfMeasure": "1 Hour",
            "resourceLocation": "EASTUS",
            "consumedService": "Microsoft.Compute",
            "resourceGroup": "ECH-PAN-RG",
            "resourceUri": "/subscriptions/12345678-04d9-421c-baf8-e3b8dd62ddba/resourceGroups/ECH-PAN-RG/providers/Microsoft.Compute/virtualMachines/echpanfw",
            "tags": "",
            "additionalInfo": "{  \"ImageType\": null,  \"ServiceType\": \"Standard_D3_v2\",  \"VMName\": null,  \"VMProperties\": null,  \"UsageType\": \"ComputeHR_SW\"}",
            "serviceInfo1": "",
            "serviceInfo2": "",
            "customerCountry": "",
            "mpnId": "1234567",
            "resellerMpnId": "",
            "chargeType": "",
            "unitPrice": 1.2799888920023,
            "quantity": 24.0,
            "unitType": "",
            "billingPreTaxTotal": 30.7197334080551,
            "billingCurrency": "USD",
            "pricingPreTaxTotal": 30.7197334080551,
            "pricingCurrency": "USD",
            "entitlementId": "31cdf47f-b249-4edd-9319-637862d12345",
            "entitlementDescription": "Partner Subscription",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "effectiveUnitPrice": 0,
            "rateOfPartnerEarnedCredit": 0,
            "rateOfCredit": 1,
            "creditType": "Azure Credit Applied",
            "invoiceLineItemTypce": "usage_line_items",
            "billingProvider": "marketplace",
            "attributes": {
                "objectType": "DailyRatedUsageLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000&seekOperation=Next",
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

### <a name="request-response-example-2"></a><span data-ttu-id="7b128-195">Voorbeeld 2 van aanvraag-antwoord</span><span class="sxs-lookup"><span data-stu-id="7b128-195">Request-response example 2</span></span>

<span data-ttu-id="7b128-196">De volgende details zijn van toepassing op dit voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7b128-196">The following details apply to this example:</span></span>

- <span data-ttu-id="7b128-197">**Provider:** **OneTime**</span><span class="sxs-lookup"><span data-stu-id="7b128-197">**Provider**: **OneTime**</span></span>
- <span data-ttu-id="7b128-198">**InvoiceLineItemType:** **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="7b128-198">**InvoiceLineItemType**: **UsageLineItems**</span></span>
- <span data-ttu-id="7b128-199">**Periode:** **vorige**</span><span class="sxs-lookup"><span data-stu-id="7b128-199">**Period**: **Previous**</span></span>
- <span data-ttu-id="7b128-200">**Zoekoperation:** **volgende**</span><span class="sxs-lookup"><span data-stu-id="7b128-200">**SeekOperation**: **Next**</span></span>

#### <a name="request-example-2"></a><span data-ttu-id="7b128-201">Aanvraagvoorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="7b128-201">Request example 2</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/unbilled/lineitems?provider=onetime&invoiceLineItemType=usagelineitems&currencyCode=usd&period=previous&size=2000&seekoperation=next HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-ContinuationToken: d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7
MS-RequestId: 1234ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda031234
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-2"></a><span data-ttu-id="7b128-202">Antwoordvoorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="7b128-202">Response example 2</span></span>

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
            "partnerId": "00083575-bbd0-54de-b2ad-0f5b0e927d71",
            "partnerName": "MTBC",
            "customerId": "",
            "customerName": "",
            "customerDomainName": "",
            "invoiceNumber": "",
            "productId": "",
            "skuId": "",
            "availabilityId": "",
            "skuName": "VM-Series Next-Generation Firewall (Bundle 2 PAYG)",
            "productName": "VM-Series Next Generation Firewall",
            "publisherName": "Test Alto Networks, Inc.",
            "publisherId": "",
            "subscriptionId": "12345678-04d9-421c-baf8-e3b8dd62ddba",
            "subscriptionDescription": "Pay-As-You-Go",
            "chargeStartDate": "2019-01-01T00:00:00Z",
            "chargeEndDate": "2019-02-01T00:00:00Z",
            "usageDate": "2019-01-02T00:00:00Z",
            "meterType": "1 Compute Hour - 4core",
            "meterCategory": "Virtual Machine Licenses",
            "meterId": "4core",
            "meterSubCategory": "VM-Series Next Generation Firewall",
            "meterName": "VM-Series Next Generation Firewall - VM-Series Next-Generation Firewall (Bundle 2 PAYG) - 4 Core Hours",
            "meterRegion": "",
            "unitOfMeasure": "1 Hour",
            "resourceLocation": "EASTUS",
            "consumedService": "Microsoft.Compute",
            "resourceGroup": "ECH-PAN-RG",
            "resourceUri": "/subscriptions/12345678-04d9-421c-baf8-e3b8dd62ddba/resourceGroups/ECH-PAN-RG/providers/Microsoft.Compute/virtualMachines/echpanfw",
            "tags": "",
            "additionalInfo": "{  \"ImageType\": null,  \"ServiceType\": \"Standard_D3_v2\",  \"VMName\": null,  \"VMProperties\": null,  \"UsageType\": \"ComputeHR_SW\"}",
            "serviceInfo1": "",
            "serviceInfo2": "",
            "customerCountry": "",
            "mpnId": "1234567",
            "resellerMpnId": "",
            "chargeType": "",
            "unitPrice": 1.2799888920023,
            "quantity": 24.0,
            "unitType": "",
            "billingPreTaxTotal": 30.7197334080551,
            "billingCurrency": "USD",
            "pricingPreTaxTotal": 30.7197334080551,
            "pricingCurrency": "USD",
            "entitlementId": "31cdf47f-b249-4edd-9319-637862d8c0b4",
            "entitlementDescription": "Partner Subscription",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-08-01T00:00:00Z",
            "effectiveUnitPrice": 0,
            "rateOfPartnerEarnedCredit": 0.15,
            "rateOfCredit": 0.15,
            "creditType": "Partner Earned Credit Applied",
            "invoiceLineItemType": "usage_line_items",
            "billingProvider": "marketplace",
            "attributes": {
                "objectType": "DailyRatedUsageLineItem"
            }
        }
    ],
    "links": {
        "self": {
             "uri": "/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode=usd&period=previous&size=2000",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
