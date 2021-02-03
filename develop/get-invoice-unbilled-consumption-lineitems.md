---
title: Niet-gefactureerde, commerciële verbruikte regel items ophalen
description: U kunt een verzameling van niet-gefactureerde commerciële verbruiks regel items voor een opgegeven factuur ophalen met behulp van de Partner Center-Api's.
ms.date: 01/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 594946db712c28983dd390207fb06c8d9f62f18b
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767487"
---
# <a name="get-invoice-unbilled-commercial-consumption-line-items"></a><span data-ttu-id="71c1b-103">Niet-gefactureerde, commerciële verbruikte regel items ophalen</span><span class="sxs-lookup"><span data-stu-id="71c1b-103">Get invoice unbilled commercial consumption line items</span></span>

<span data-ttu-id="71c1b-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="71c1b-104">**Applies to:**</span></span>

- <span data-ttu-id="71c1b-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="71c1b-105">Partner Center</span></span>

<span data-ttu-id="71c1b-106">Een verzameling van Details over niet-gefactureerde commerciële verbruiks regels ophalen.</span><span class="sxs-lookup"><span data-stu-id="71c1b-106">How to get a collection of unbilled commercial consumption line item details.</span></span>

<span data-ttu-id="71c1b-107">U kunt de volgende methoden gebruiken om een verzameling Details van niet-gefactureerde commerciële verbruiks regel items te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="71c1b-107">You can use the following methods to get a collection of details unbilled commercial consumption line items (also known as open usage line items) programmatically.</span></span>

>[!NOTE]
><span data-ttu-id="71c1b-108">Het dagelijks geclassificeerde gebruik duurt doorgaans 24 uur in het partner centrum of voor toegang via de API.</span><span class="sxs-lookup"><span data-stu-id="71c1b-108">Daily-rated usage normally takes 24 hours to appear in Partner Center or to be accessed through the API.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="71c1b-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="71c1b-109">Prerequisites</span></span>

- <span data-ttu-id="71c1b-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="71c1b-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="71c1b-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="71c1b-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="71c1b-112">Een factuur-ID.</span><span class="sxs-lookup"><span data-stu-id="71c1b-112">An invoice identifier.</span></span> <span data-ttu-id="71c1b-113">Hiermee wordt de factuur aangegeven waarvoor de regel items moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="71c1b-113">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="71c1b-114">C\#</span><span class="sxs-lookup"><span data-stu-id="71c1b-114">C\#</span></span>

<span data-ttu-id="71c1b-115">De regel items voor de opgegeven factuur ophalen:</span><span class="sxs-lookup"><span data-stu-id="71c1b-115">To get the line items for the specified invoice:</span></span>

1. <span data-ttu-id="71c1b-116">Roep de methode [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) aan om een interface te verkrijgen voor het factureren van bewerkingen voor de opgegeven factuur.</span><span class="sxs-lookup"><span data-stu-id="71c1b-116">Call the [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) method to get an interface to invoice operations for the specified invoice.</span></span>

2. <span data-ttu-id="71c1b-117">Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) aan om het object invoice op te halen.</span><span class="sxs-lookup"><span data-stu-id="71c1b-117">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the invoice object.</span></span>

<span data-ttu-id="71c1b-118">Het **object invoice** bevat alle informatie voor de opgegeven factuur.</span><span class="sxs-lookup"><span data-stu-id="71c1b-118">The **invoice object** contains all of the information for the specified invoice.</span></span> <span data-ttu-id="71c1b-119">De **provider** identificeert de bron van de niet-gefactureerde detail informatie (bijvoorbeeld **eenmalige**).</span><span class="sxs-lookup"><span data-stu-id="71c1b-119">The **Provider** identifies the source of the unbilled detail information (for example, **OneTime**).</span></span> <span data-ttu-id="71c1b-120">De **InvoiceLineItemType** geeft het type aan (bijvoorbeeld **UsageLineItem**).</span><span class="sxs-lookup"><span data-stu-id="71c1b-120">The **InvoiceLineItemType** specifies the type (for example, **UsageLineItem**).</span></span>

<span data-ttu-id="71c1b-121">De volgende voorbeeld code gebruikt een **foreach** -lus om de **InvoiceLineItems** -verzameling te verwerken.</span><span class="sxs-lookup"><span data-stu-id="71c1b-121">The following example code uses a **foreach** loop to process the **InvoiceLineItems** collection.</span></span> <span data-ttu-id="71c1b-122">Voor elke **InvoiceLineItemType** wordt een afzonderlijke verzameling regel items opgehaald.</span><span class="sxs-lookup"><span data-stu-id="71c1b-122">A separate collection of line items is retrieved for each **InvoiceLineItemType**.</span></span>

<span data-ttu-id="71c1b-123">Ophalen van een verzameling regel items die overeenkomen met een **InvoiceDetail** -exemplaar:</span><span class="sxs-lookup"><span data-stu-id="71c1b-123">To get a collection of line items that correspond to an **InvoiceDetail** instance:</span></span>

1. <span data-ttu-id="71c1b-124">Geef de **BillingProvider** en **InvoiceLineItemType** van het exemplaar door aan de methode [**by**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) .</span><span class="sxs-lookup"><span data-stu-id="71c1b-124">Pass the instance's **BillingProvider** and **InvoiceLineItemType** to the [**By**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) method.</span></span>

2. <span data-ttu-id="71c1b-125">Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) aan om de gekoppelde regel items op te halen.</span><span class="sxs-lookup"><span data-stu-id="71c1b-125">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the associated line items.</span></span>
3. <span data-ttu-id="71c1b-126">Maak een enumerator om door de verzameling te bladeren, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="71c1b-126">Create an enumerator to traverse the collection as shown in the following example.</span></span>

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

<span data-ttu-id="71c1b-127">Zie voor een vergelijkbaar voor beeld:</span><span class="sxs-lookup"><span data-stu-id="71c1b-127">For a similar example, see:</span></span>

- <span data-ttu-id="71c1b-128">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="71c1b-128">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="71c1b-129">Project: **Partner Center SDK** -voor beelden</span><span class="sxs-lookup"><span data-stu-id="71c1b-129">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="71c1b-130">Klasse: **GetUnBilledConsumptionReconLineItemsPaging.cs**</span><span class="sxs-lookup"><span data-stu-id="71c1b-130">Class: **GetUnBilledConsumptionReconLineItemsPaging.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="71c1b-131">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="71c1b-131">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="71c1b-132">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="71c1b-132">Request syntax</span></span>

<span data-ttu-id="71c1b-133">U kunt de volgende syntaxis voor uw REST-aanvraag gebruiken, afhankelijk van uw use-case.</span><span class="sxs-lookup"><span data-stu-id="71c1b-133">You can use the following syntaxes for your REST request, depending on your use case.</span></span> <span data-ttu-id="71c1b-134">Zie de beschrijvingen voor elke syntaxis voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="71c1b-134">For more information, see the descriptions for each syntax.</span></span>

 | <span data-ttu-id="71c1b-135">Methode</span><span class="sxs-lookup"><span data-stu-id="71c1b-135">Method</span></span>  | <span data-ttu-id="71c1b-136">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="71c1b-136">Request URI</span></span>         | <span data-ttu-id="71c1b-137">Beschrijving van de syntaxis use case</span><span class="sxs-lookup"><span data-stu-id="71c1b-137">Description of syntax use case</span></span> |                                                                                                                                            |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="71c1b-138">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="71c1b-138">**GET**</span></span> | <span data-ttu-id="71c1b-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems? provider = eenmalige&invoicelineitemtype = usagelineitems&CurrencyCode = {currencycode} &periode = {period} http/1.1</span><span class="sxs-lookup"><span data-stu-id="71c1b-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period} HTTP/1.1</span></span>                              | <span data-ttu-id="71c1b-140">Gebruik deze syntaxis om een volledige lijst van elk regel item voor de opgegeven factuur te retour neren.</span><span class="sxs-lookup"><span data-stu-id="71c1b-140">Use this syntax to return a full list of every line item for the given invoice.</span></span> |
| <span data-ttu-id="71c1b-141">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="71c1b-141">**GET**</span></span> | <span data-ttu-id="71c1b-142">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems? provider = eenmalige&invoicelineitemtype = usagelineitems&CurrencyCode = {currencycode} &periode = {period} &grootte = {size} http/1.1</span><span class="sxs-lookup"><span data-stu-id="71c1b-142">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period}&size={size} HTTP/1.1</span></span>  | <span data-ttu-id="71c1b-143">Gebruik deze syntaxis voor grote facturen.</span><span class="sxs-lookup"><span data-stu-id="71c1b-143">Use this syntax for large invoices.</span></span> <span data-ttu-id="71c1b-144">Gebruik deze syntaxis met een opgegeven grootte en een offset op basis van 0 om een pagina lijst met regel items te retour neren.</span><span class="sxs-lookup"><span data-stu-id="71c1b-144">Use this syntax with a specified size and 0-based offset to return a paged list of line items.</span></span> |
| <span data-ttu-id="71c1b-145">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="71c1b-145">**GET**</span></span> | <span data-ttu-id="71c1b-146">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems? provider = eenmalige&invoicelineitemtype = usagelineitems&CurrencyCode = {currencycode} &periode = {period} &grootte = {size} &SeekOperation = Next</span><span class="sxs-lookup"><span data-stu-id="71c1b-146">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=usagelineitems&currencycode={currencycode}&period={period}&size={size}&seekOperation=Next</span></span>                               | <span data-ttu-id="71c1b-147">Gebruik deze syntaxis om de volgende pagina van regel items voor reconciliatie te verkrijgen met `seekOperation = "Next"` .</span><span class="sxs-lookup"><span data-stu-id="71c1b-147">Use this syntax to get the next page of reconciliation line items using `seekOperation = "Next"`.</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="71c1b-148">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="71c1b-148">URI parameters</span></span>

<span data-ttu-id="71c1b-149">Gebruik de volgende URI en query parameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="71c1b-149">Use the following URI and query parameters when creating the request.</span></span>

| <span data-ttu-id="71c1b-150">Naam</span><span class="sxs-lookup"><span data-stu-id="71c1b-150">Name</span></span>                   | <span data-ttu-id="71c1b-151">Type</span><span class="sxs-lookup"><span data-stu-id="71c1b-151">Type</span></span>   | <span data-ttu-id="71c1b-152">Vereist</span><span class="sxs-lookup"><span data-stu-id="71c1b-152">Required</span></span> | <span data-ttu-id="71c1b-153">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="71c1b-153">Description</span></span>                                                                     |
|------------------------|--------|----------|---------------------------------------------------------------------------------|
| <span data-ttu-id="71c1b-154">providers</span><span class="sxs-lookup"><span data-stu-id="71c1b-154">provider</span></span>               | <span data-ttu-id="71c1b-155">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="71c1b-155">string</span></span> | <span data-ttu-id="71c1b-156">Yes</span><span class="sxs-lookup"><span data-stu-id="71c1b-156">Yes</span></span>      | <span data-ttu-id="71c1b-157">De provider: '**eenmalige**'.</span><span class="sxs-lookup"><span data-stu-id="71c1b-157">The provider: "**OneTime**".</span></span>                                                |
| <span data-ttu-id="71c1b-158">factuur-regel-item-type</span><span class="sxs-lookup"><span data-stu-id="71c1b-158">invoice-line-item-type</span></span> | <span data-ttu-id="71c1b-159">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="71c1b-159">string</span></span> | <span data-ttu-id="71c1b-160">Yes</span><span class="sxs-lookup"><span data-stu-id="71c1b-160">Yes</span></span>      | <span data-ttu-id="71c1b-161">Het type factuur Details: "**UsageLineItems**", "**UsageLineItems**".</span><span class="sxs-lookup"><span data-stu-id="71c1b-161">The type of invoice detail: "**UsageLineItems**", "**UsageLineItems**".</span></span>               |
| <span data-ttu-id="71c1b-162">currencyCode</span><span class="sxs-lookup"><span data-stu-id="71c1b-162">currencyCode</span></span>           | <span data-ttu-id="71c1b-163">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="71c1b-163">string</span></span> | <span data-ttu-id="71c1b-164">Yes</span><span class="sxs-lookup"><span data-stu-id="71c1b-164">Yes</span></span>      | <span data-ttu-id="71c1b-165">De valuta code voor de niet-gefactureerde regel items.</span><span class="sxs-lookup"><span data-stu-id="71c1b-165">The currency code for the unbilled line items.</span></span>                                  |
| <span data-ttu-id="71c1b-166">period</span><span class="sxs-lookup"><span data-stu-id="71c1b-166">period</span></span>                 | <span data-ttu-id="71c1b-167">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="71c1b-167">string</span></span> | <span data-ttu-id="71c1b-168">Yes</span><span class="sxs-lookup"><span data-stu-id="71c1b-168">Yes</span></span>      | <span data-ttu-id="71c1b-169">De periode voor niet-gefactureerde afstemming (bijvoorbeeld: **huidige**, **vorige**).</span><span class="sxs-lookup"><span data-stu-id="71c1b-169">The period for unbilled recon (for example: **current**, **previous**).</span></span><br/><br/><span data-ttu-id="71c1b-170">**Vorige** : als de facturerings cyclus 01/01/2020 – 01/31/2020 dan is, is de kans groot dat uw factuur wordt gegenereerd tussen 02/06/2020 en 02/08/2020 UTC-tijd.</span><span class="sxs-lookup"><span data-stu-id="71c1b-170">**Previous** – if the billing cycle is 01/01/2020 – 01/31/2020 then, most likely that your invoice is generated between 02/06/2020 and 02/08/2020 UTC time.</span></span> <span data-ttu-id="71c1b-171">Als u de niet-gefactureerde gebruiks gegevens van de facturerings cyclus (01/01/2020 – 01/31/2020) wilt opvragen op elke tijd tussen 02/01/2020 en de door de factuur gegenereerde datum (tussen 02/06/2020 en 02/08/2020 UTC-tijd), moet u de periode als ' eerder ' kiezen.</span><span class="sxs-lookup"><span data-stu-id="71c1b-171">If you need to query your unbilled usage data of the billing cycle (01/01/2020 – 01/31/2020) on any time between 02/01/2020 and the invoice-generated date (which is between 02/06/2020 and 02/08/2020 UTC time), then, you need to choose Period as "Previous".</span></span><br/><br/><span data-ttu-id="71c1b-172">**Huidige** – als de facturerings cyclus 01/01/2020 – 01/31/2020 is, is de kans groot dat uw factuur wordt gegenereerd tussen 02/06/2020 en 02/08/2020 UTC-tijd.</span><span class="sxs-lookup"><span data-stu-id="71c1b-172">**Current** – if the billing cycle is 01/01/2020 – 01/31/2020 then, most likely that your invoice is generated between 02/06/2020 and 02/08/2020 UTC time.</span></span> <span data-ttu-id="71c1b-173">Als u uw niet-gefactureerde gebruiks gegevens van de facturerings cyclus (01/01/2020 – 01/31/2020) wilt doorzoeken op elke tijd tussen 01/01/2020 en 01/31/2020 die binnen uw facturerings cyclus valt, moet u periode kiezen als ' Huidig '.</span><span class="sxs-lookup"><span data-stu-id="71c1b-173">If you need to query your unbilled usage data of the billing cycle (01/01/2020 – 01/31/2020) on any time between 01/01/2020 and 01/31/2020 which is within your billing cycle, then, you need to choose Period as "Current".</span></span> |
| <span data-ttu-id="71c1b-174">grootte</span><span class="sxs-lookup"><span data-stu-id="71c1b-174">size</span></span>                   | <span data-ttu-id="71c1b-175">getal</span><span class="sxs-lookup"><span data-stu-id="71c1b-175">number</span></span> | <span data-ttu-id="71c1b-176">No</span><span class="sxs-lookup"><span data-stu-id="71c1b-176">No</span></span>       | <span data-ttu-id="71c1b-177">Het maximum aantal items dat moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="71c1b-177">The maximum number of items to return.</span></span> <span data-ttu-id="71c1b-178">De standaard grootte is 2000.</span><span class="sxs-lookup"><span data-stu-id="71c1b-178">The default size is 2000.</span></span>                    |
| <span data-ttu-id="71c1b-179">seekOperation</span><span class="sxs-lookup"><span data-stu-id="71c1b-179">seekOperation</span></span>          | <span data-ttu-id="71c1b-180">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="71c1b-180">string</span></span> | <span data-ttu-id="71c1b-181">No</span><span class="sxs-lookup"><span data-stu-id="71c1b-181">No</span></span>       | <span data-ttu-id="71c1b-182">Stel `seekOperation=Next` deze waarde in om de volgende pagina met lijn items voor afstemming weer te geven.</span><span class="sxs-lookup"><span data-stu-id="71c1b-182">Set `seekOperation=Next` to get the next page of reconciliation line items.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="71c1b-183">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="71c1b-183">Request headers</span></span>

<span data-ttu-id="71c1b-184">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="71c1b-184">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="71c1b-185">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="71c1b-185">Request body</span></span>

<span data-ttu-id="71c1b-186">Geen.</span><span class="sxs-lookup"><span data-stu-id="71c1b-186">None.</span></span>

## <a name="rest-response"></a><span data-ttu-id="71c1b-187">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="71c1b-187">REST response</span></span>

<span data-ttu-id="71c1b-188">Als dit is gelukt, bevat het antwoord het verzamelen van regel items.</span><span class="sxs-lookup"><span data-stu-id="71c1b-188">If successful, the response contains the collection of line item details.</span></span>

<span data-ttu-id="71c1b-189">*Voor de **ChargeType** van het regel item wordt de **gekochte** waarde toegewezen aan **Nieuw** en de **terugbetaling** van de waarde wordt toegewezen om te **Annuleren**.*</span><span class="sxs-lookup"><span data-stu-id="71c1b-189">*For the line item **ChargeType**, the value **Purchase** is mapped to **New** and the value **Refund** is mapped to **Cancel**.*</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="71c1b-190">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="71c1b-190">Response success and error codes</span></span>

<span data-ttu-id="71c1b-191">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="71c1b-191">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="71c1b-192">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="71c1b-192">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="71c1b-193">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="71c1b-193">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

## <a name="request-response-examples"></a><span data-ttu-id="71c1b-194">Aanvraag-antwoord voorbeelden</span><span class="sxs-lookup"><span data-stu-id="71c1b-194">Request-response examples</span></span>

### <a name="request-response-example-1"></a><span data-ttu-id="71c1b-195">Aanvraag-antwoord-voor beeld 1</span><span class="sxs-lookup"><span data-stu-id="71c1b-195">Request-response example 1</span></span>

<span data-ttu-id="71c1b-196">De volgende details zijn van toepassing op dit voor beeld:</span><span class="sxs-lookup"><span data-stu-id="71c1b-196">The following details apply to this example:</span></span>

- <span data-ttu-id="71c1b-197">**Provider**: **eenmalige**</span><span class="sxs-lookup"><span data-stu-id="71c1b-197">**Provider**: **OneTime**</span></span>
- <span data-ttu-id="71c1b-198">**InvoiceLineItemType**: **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="71c1b-198">**InvoiceLineItemType**: **UsageLineItems**</span></span>
- <span data-ttu-id="71c1b-199">**Periode**: **vorige**</span><span class="sxs-lookup"><span data-stu-id="71c1b-199">**Period**: **Previous**</span></span>

#### <a name="request-example-1"></a><span data-ttu-id="71c1b-200">Voor beeld 1 aanvragen</span><span class="sxs-lookup"><span data-stu-id="71c1b-200">Request example 1</span></span>

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

### <a name="response-example-1"></a><span data-ttu-id="71c1b-201">Antwoord voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="71c1b-201">Response example 1</span></span>

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

### <a name="request-response-example-2"></a><span data-ttu-id="71c1b-202">Aanvraag-antwoord-voor beeld 2</span><span class="sxs-lookup"><span data-stu-id="71c1b-202">Request-response example 2</span></span>

<span data-ttu-id="71c1b-203">De volgende details zijn van toepassing op dit voor beeld:</span><span class="sxs-lookup"><span data-stu-id="71c1b-203">The following details apply to this example:</span></span>

- <span data-ttu-id="71c1b-204">**Provider**: **eenmalige**</span><span class="sxs-lookup"><span data-stu-id="71c1b-204">**Provider**: **OneTime**</span></span>
- <span data-ttu-id="71c1b-205">**InvoiceLineItemType**: **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="71c1b-205">**InvoiceLineItemType**: **UsageLineItems**</span></span>
- <span data-ttu-id="71c1b-206">**Periode**: **vorige**</span><span class="sxs-lookup"><span data-stu-id="71c1b-206">**Period**: **Previous**</span></span>
- <span data-ttu-id="71c1b-207">**SeekOperation**: **volgende**</span><span class="sxs-lookup"><span data-stu-id="71c1b-207">**SeekOperation**: **Next**</span></span>

#### <a name="request-example-2"></a><span data-ttu-id="71c1b-208">Voor beeld 2 aanvragen</span><span class="sxs-lookup"><span data-stu-id="71c1b-208">Request example 2</span></span>

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

#### <a name="response-example-2"></a><span data-ttu-id="71c1b-209">Antwoord voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="71c1b-209">Response example 2</span></span>

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
            "rateOfPartnerEarnedCredit": 0,
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
