---
title: Regelitems van facturen ophalen
description: U kunt een verzameling van factuur regel items (gesloten facturerings regel items) voor een opgegeven factuur ophalen met behulp van de Partner Center-Api's.
ms.date: 01/27/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 085397f3dc36468e411cec71e0dc9ae2cc364673
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767485"
---
# <a name="get-invoice-line-items"></a><span data-ttu-id="e1e79-103">Regelitems van facturen ophalen</span><span class="sxs-lookup"><span data-stu-id="e1e79-103">Get invoice line items</span></span>

<span data-ttu-id="e1e79-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="e1e79-104">**Applies to:**</span></span>

- <span data-ttu-id="e1e79-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e1e79-105">Partner Center</span></span>
- <span data-ttu-id="e1e79-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="e1e79-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="e1e79-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="e1e79-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="e1e79-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e1e79-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e1e79-109">U kunt de volgende methoden gebruiken om de details van een verzameling van factuur regel items (ook wel gesloten facturerings regel items genoemd) voor een opgegeven factuur op te halen.</span><span class="sxs-lookup"><span data-stu-id="e1e79-109">You can use the following methods to get a collection details for of invoice line items (also known as closed billing line items) for a specified invoice.</span></span>

<span data-ttu-id="e1e79-110">*Met uitzonde ring van oplossingen voor fouten, wordt deze API niet meer bijgewerkt.*</span><span class="sxs-lookup"><span data-stu-id="e1e79-110">*Except for bug fixes, this API is no longer being updated.*</span></span> <span data-ttu-id="e1e79-111">U moet uw toepassingen bijwerken om de **eenmalige** -API in plaats van **Marketplace** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="e1e79-111">You should update your applications to call the **onetime** API instead of **marketplace**.</span></span> <span data-ttu-id="e1e79-112">De **eenmalige** -API biedt extra functionaliteit en blijft worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="e1e79-112">The **onetime** API provides additional functionality, and will continue to be updated.</span></span>

<span data-ttu-id="e1e79-113">U moet **eenmalige** gebruiken om een query uit te zoeken naar alle commerciële verbruikte regel items in plaats van **Marketplace**.</span><span class="sxs-lookup"><span data-stu-id="e1e79-113">You should use **onetime** to query all commercial consumption line items instead of **marketplace**.</span></span> <span data-ttu-id="e1e79-114">U kunt ook de koppelingen volgen in de aanroep van de ramings koppelingen.</span><span class="sxs-lookup"><span data-stu-id="e1e79-114">Or, you can follow the links in the estimate links call.</span></span>

<span data-ttu-id="e1e79-115">Deze API biedt ook ondersteuning voor de **provider** typen **Azure** en **Office** voor Microsoft Azure (MS-AZR-0145P)-abonnementen en kantoor aanbiedingen, waardoor de API-functie achterwaarts compatibel is.</span><span class="sxs-lookup"><span data-stu-id="e1e79-115">This API also supports the **provider** types of **azure** and **office** for Microsoft Azure (MS-AZR-0145P) subscriptions and Office offers, which makes the API feature backward compatible.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e1e79-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e1e79-116">Prerequisites</span></span>

- <span data-ttu-id="e1e79-117">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e1e79-117">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e1e79-118">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="e1e79-118">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="e1e79-119">Een factuur-ID.</span><span class="sxs-lookup"><span data-stu-id="e1e79-119">An invoice identifier.</span></span> <span data-ttu-id="e1e79-120">Hiermee wordt de factuur aangegeven waarvoor de regel items moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e1e79-120">This identifies the invoice for which to retrieve the line items.</span></span>

## <a name="c"></a><span data-ttu-id="e1e79-121">C\#</span><span class="sxs-lookup"><span data-stu-id="e1e79-121">C\#</span></span>

<span data-ttu-id="e1e79-122">De regel items voor de opgegeven factuur ophalen:</span><span class="sxs-lookup"><span data-stu-id="e1e79-122">To get the line items for the specified invoice:</span></span>

1. <span data-ttu-id="e1e79-123">Roep de methode [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) aan om een interface te verkrijgen voor het factureren van bewerkingen voor de opgegeven factuur.</span><span class="sxs-lookup"><span data-stu-id="e1e79-123">Call the [**ById**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicecollection.byid) method to get an interface to invoice operations for the specified invoice.</span></span>

2. <span data-ttu-id="e1e79-124">Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) aan om het object invoice op te halen.</span><span class="sxs-lookup"><span data-stu-id="e1e79-124">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.getasync) method to retrieve the invoice object.</span></span> <span data-ttu-id="e1e79-125">Het object invoice bevat alle informatie voor de opgegeven factuur.</span><span class="sxs-lookup"><span data-stu-id="e1e79-125">The invoice object contains all of the information for the specified invoice.</span></span>
3. <span data-ttu-id="e1e79-126">Gebruik de eigenschap [**InvoiceDetails**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoice.invoicedetails) van het factuur object om toegang te krijgen tot een verzameling [**InvoiceDetail**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail) -objecten, die elk een [**BillingProvider**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail.billingprovider) en een [**InvoiceLineItemType**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail.invoicelineitemtype)bevatten.</span><span class="sxs-lookup"><span data-stu-id="e1e79-126">Use the invoice object's [**InvoiceDetails**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoice.invoicedetails) property to get access to a collection of [**InvoiceDetail**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail) objects, each of which contains a [**BillingProvider**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail.billingprovider) and an [**InvoiceLineItemType**](/dotnet/api/microsoft.store.partnercenter.models.invoices.invoicedetail.invoicelineitemtype).</span></span> <span data-ttu-id="e1e79-127">De **BillingProvider** identificeert de bron van de detail gegevens over de factuur (zoals **Office**, **Azure**, **eenmalige**) en de **InvoiceLineItemType** geeft het type aan (bijvoorbeeld **BillingLineItem**).</span><span class="sxs-lookup"><span data-stu-id="e1e79-127">The **BillingProvider** identifies the source of the invoice detail information (such as **Office**, **Azure**, **OneTime**), and the **InvoiceLineItemType** specifies the type (for example, **BillingLineItem**).</span></span>

<span data-ttu-id="e1e79-128">De volgende voorbeeld code gebruikt een **foreach** -lus om de **InvoiceDetails** -verzameling te verwerken.</span><span class="sxs-lookup"><span data-stu-id="e1e79-128">The following example code uses a **foreach** loop to process the **InvoiceDetails** collection.</span></span> <span data-ttu-id="e1e79-129">Er wordt een afzonderlijke verzameling regel items opgehaald voor elk **InvoiceDetail** -exemplaar.</span><span class="sxs-lookup"><span data-stu-id="e1e79-129">A separate collection of line items is retrieved for each **InvoiceDetail** instance.</span></span>

<span data-ttu-id="e1e79-130">Ophalen van een verzameling regel items die overeenkomen met een **InvoiceDetail** -exemplaar:</span><span class="sxs-lookup"><span data-stu-id="e1e79-130">To get a collection of line items that correspond to an **InvoiceDetail** instance:</span></span>

1. <span data-ttu-id="e1e79-131">Geef de **BillingProvider** en **InvoiceLineItemType** van het exemplaar door aan de methode [**by**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) .</span><span class="sxs-lookup"><span data-stu-id="e1e79-131">Pass the instance's **BillingProvider** and **InvoiceLineItemType** to the [**By**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoice.by) method.</span></span>

2. <span data-ttu-id="e1e79-132">Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicelineitemcollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicelineitemcollection.getasync) aan om de gekoppelde regel items op te halen.</span><span class="sxs-lookup"><span data-stu-id="e1e79-132">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicelineitemcollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.invoices.iinvoicelineitemcollection.getasync) method to retrieve the associated line items.</span></span>
3. <span data-ttu-id="e1e79-133">Maak een enumerator om door de verzameling te bladeren, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="e1e79-133">Create an enumerator to traverse the collection as shown in the following example.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// int invoicePageSize;
// string invoiceId;

// Retrieve the invoice.
var invoiceOperations = partnerOperations.Invoices.ById(invoiceId);
var invoice = invoiceOperations.Get();

foreach (var invoiceDetail in invoice.InvoiceDetails)
{
    Console.WriteLine(string.Format("Getting invoice line item for product {0} and line item type {1}",
        invoiceDetail.BillingProvider,
        invoiceDetail.InvoiceLineItemType));

    // Is this an unpaged or paged request?
    bool isUnPaged = (this.invoicePageSize <= 0);

    // If the scenario is unpaged, get all the invoice line items, otherwise get the first page.
    var invoiceLineItemsCollection =
        (isUnPaged)
        ? invoiceOperations.By(invoiceDetail.BillingProvider, invoiceDetail.InvoiceLineItemType).Get()
        : invoiceOperations.By(invoiceDetail.BillingProvider, invoiceDetail.InvoiceLineItemType).Get(this.invoicePageSize, 0);

    // Create an enumerator for traversing the line items collection.
    var invoiceLineItemEnumerator =
        partnerOperations.Enumerators.InvoiceLineItems.Create(invoiceLineItemsCollection);

    while (invoiceLineItemEnumerator.HasValue)
    {
        // invoiceLineItemEnumerator.Current contains a collection
        // of line items.
        Console.WriteLine(String.Format("invoiceLineItemEnumerator.Current has {0} line items.",
            invoiceLineItemEnumerator.Current.TotalCount));
        //
        // Insert code here to work with the line items.
        //
        Console.WriteLine();
        Console.Write("Press any key to retrieve the next invoice line items page");
        Console.ReadKey();

        // Get the next list of invoice line items.
        invoiceLineItemEnumerator.Next();
    }
}
```

<span data-ttu-id="e1e79-134">Voor een vergelijkbaar voor beeld raadpleegt u het volgende:</span><span class="sxs-lookup"><span data-stu-id="e1e79-134">For a similar example, see the following:</span></span>

- <span data-ttu-id="e1e79-135">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="e1e79-135">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="e1e79-136">Project: **Partner Center SDK** -voor beelden</span><span class="sxs-lookup"><span data-stu-id="e1e79-136">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="e1e79-137">Klasse: **GetInvoiceLineItems.cs**</span><span class="sxs-lookup"><span data-stu-id="e1e79-137">Class: **GetInvoiceLineItems.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="e1e79-138">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e1e79-138">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e1e79-139">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e1e79-139">Request syntax</span></span>

<span data-ttu-id="e1e79-140">Maak uw aanvraag met behulp van de juiste syntaxis voor de facturerings provider in uw scenario.</span><span class="sxs-lookup"><span data-stu-id="e1e79-140">Make your request using the appropriate syntax for the billing provider in your scenario.</span></span>

#### <a name="office"></a><span data-ttu-id="e1e79-141">Office</span><span class="sxs-lookup"><span data-stu-id="e1e79-141">Office</span></span>

<span data-ttu-id="e1e79-142">De volgende syntaxis is van toepassing wanneer de facturerings provider **Office** is.</span><span class="sxs-lookup"><span data-stu-id="e1e79-142">The following syntax applies when the billing provider is **Office**.</span></span>

| <span data-ttu-id="e1e79-143">Methode</span><span class="sxs-lookup"><span data-stu-id="e1e79-143">Method</span></span>  | <span data-ttu-id="e1e79-144">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e1e79-144">Request URI</span></span>                                                                                                                                                     |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e1e79-145">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e1e79-145">**GET**</span></span> | <span data-ttu-id="e1e79-146">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems? provider = Office&invoicelineitemtype = billinglineitems&grootte = {size} &offset = {offset} http/1.1</span><span class="sxs-lookup"><span data-stu-id="e1e79-146">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=office&invoicelineitemtype=billinglineitems&size={size}&offset={offset} HTTP/1.1</span></span>                               |

#### <a name="microsoft-azure-ms-azr-0145p-subscription"></a><span data-ttu-id="e1e79-147">Microsoft Azure-abonnement (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="e1e79-147">Microsoft Azure (MS-AZR-0145P) subscription</span></span>

<span data-ttu-id="e1e79-148">De volgende syntaxis is van toepassing wanneer de facturerings provider een Microsoft Azure-abonnement (MS-AZR-0145P) heeft.</span><span class="sxs-lookup"><span data-stu-id="e1e79-148">The following syntaxes apply when the billing provider has a Microsoft Azure (MS-AZR-0145P) subscription.</span></span>

| <span data-ttu-id="e1e79-149">Methode</span><span class="sxs-lookup"><span data-stu-id="e1e79-149">Method</span></span>  | <span data-ttu-id="e1e79-150">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e1e79-150">Request URI</span></span>                                                                                                                                                     |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e1e79-151">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e1e79-151">**GET**</span></span> | <span data-ttu-id="e1e79-152">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems? provider = Azure&invoicelineitemtype = billinglineitems&grootte = {size} &offset = {offset} http/1.1</span><span class="sxs-lookup"><span data-stu-id="e1e79-152">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=azure&invoicelineitemtype=billinglineitems&size={size}&offset={offset} HTTP/1.1</span></span>  |
| <span data-ttu-id="e1e79-153">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e1e79-153">**GET**</span></span> | <span data-ttu-id="e1e79-154">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems? provider = Azure&invoicelineitemtype = usagelineitems&grootte = {size} &offset = {offset} http/1.1</span><span class="sxs-lookup"><span data-stu-id="e1e79-154">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=azure&invoicelineitemtype=usagelineitems&size={size}&offset={offset} HTTP/1.1</span></span>  |

##### <a name="onetime"></a><span data-ttu-id="e1e79-155">Eenmalige</span><span class="sxs-lookup"><span data-stu-id="e1e79-155">OneTime</span></span>

<span data-ttu-id="e1e79-156">De volgende syntaxis is van toepassing wanneer de facturerings provider **eenmalige** is.</span><span class="sxs-lookup"><span data-stu-id="e1e79-156">The following syntaxes apply when the billing provider is **OneTime**.</span></span> <span data-ttu-id="e1e79-157">Dit omvat kosten voor Azure-reserve ringen,-software, Azure-abonnementen en commerciële Marketplace-producten.</span><span class="sxs-lookup"><span data-stu-id="e1e79-157">This includes charges for Azure reservations, software, Azure plans, and commercial marketplace products.</span></span>

| <span data-ttu-id="e1e79-158">Methode</span><span class="sxs-lookup"><span data-stu-id="e1e79-158">Method</span></span>  | <span data-ttu-id="e1e79-159">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e1e79-159">Request URI</span></span>                                                                                                                                                     |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e1e79-160">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e1e79-160">**GET**</span></span> | <span data-ttu-id="e1e79-161">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems? provider = eenmalige&invoicelineitemtype = billinglineitems&grootte = {size} http/1.1</span><span class="sxs-lookup"><span data-stu-id="e1e79-161">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=billinglineitems&size={size} HTTP/1.1</span></span>  |
| <span data-ttu-id="e1e79-162">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e1e79-162">**GET**</span></span> | <span data-ttu-id="e1e79-163">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems/onetime/billinglineitems&grootte = {size}? SeekOperation = Next</span><span class="sxs-lookup"><span data-stu-id="e1e79-163">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems/onetime/billinglineitems&size={size}?seekOperation=Next</span></span>                           |

#### <a name="previous-syntaxes"></a><span data-ttu-id="e1e79-164">Vorige syntaxis</span><span class="sxs-lookup"><span data-stu-id="e1e79-164">Previous syntaxes</span></span>

<span data-ttu-id="e1e79-165">Als u de volgende syntaxis gebruikt, moet u ervoor zorgen dat u de juiste syntaxis gebruikt voor uw use-case.</span><span class="sxs-lookup"><span data-stu-id="e1e79-165">If you are using the following syntaxes, be sure to use the appropriate syntax for your use case.</span></span>

<span data-ttu-id="e1e79-166">*Met uitzonde ring van oplossingen voor fouten, wordt deze API niet meer bijgewerkt.*</span><span class="sxs-lookup"><span data-stu-id="e1e79-166">*Except for bug fixes, this API is no longer being updated.*</span></span> <span data-ttu-id="e1e79-167">U moet uw toepassingen bijwerken om de **eenmalige** -API in plaats van **Marketplace** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="e1e79-167">You should update your applications to call the **onetime** API instead of **marketplace**.</span></span> <span data-ttu-id="e1e79-168">De **eenmalige** -API biedt extra functionaliteit en blijft worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="e1e79-168">The **onetime** API provides additional functionality, and will continue to be updated.</span></span>

<span data-ttu-id="e1e79-169">U moet **eenmalige** gebruiken om een query uit te zoeken naar alle commerciële verbruikte regel items in plaats van **Marketplace**.</span><span class="sxs-lookup"><span data-stu-id="e1e79-169">You should use **onetime** to query all commercial consumption line items instead of **marketplace**.</span></span> <span data-ttu-id="e1e79-170">U kunt ook de koppelingen volgen in de aanroep van de ramings koppelingen.</span><span class="sxs-lookup"><span data-stu-id="e1e79-170">Or, you can follow the links in the estimate links call.</span></span>

| <span data-ttu-id="e1e79-171">Methode</span><span class="sxs-lookup"><span data-stu-id="e1e79-171">Method</span></span> | <span data-ttu-id="e1e79-172">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e1e79-172">Request URI</span></span> | <span data-ttu-id="e1e79-173">Beschrijving van de syntaxis use case</span><span class="sxs-lookup"><span data-stu-id="e1e79-173">Description of syntax use case</span></span> |
| ------ | ----------- | -------------------------------- |
| <span data-ttu-id="e1e79-174">GET</span><span class="sxs-lookup"><span data-stu-id="e1e79-174">GET</span></span> | <span data-ttu-id="e1e79-175">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems/{billing-provider}/{invoice-line-item-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e1e79-175">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems/{billing-provider}/{invoice-line-item-type} HTTP/1.1</span></span>                              | <span data-ttu-id="e1e79-176">U kunt deze syntaxis gebruiken om een volledige lijst te retour neren van elk regel item voor de betreffende factuur.</span><span class="sxs-lookup"><span data-stu-id="e1e79-176">You can use this syntax to return a full list of every line item for the given invoice.</span></span> |
| <span data-ttu-id="e1e79-177">GET</span><span class="sxs-lookup"><span data-stu-id="e1e79-177">GET</span></span> | <span data-ttu-id="e1e79-178">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems/{billing-provider}/{invoice-line-item-type}? grootte = {size} &offset = {offset} http/1.1</span><span class="sxs-lookup"><span data-stu-id="e1e79-178">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems/{billing-provider}/{invoice-line-item-type}?size={size}&offset={offset} HTTP/1.1</span></span>  | <span data-ttu-id="e1e79-179">Voor grote facturen kunt u deze syntaxis gebruiken met een opgegeven grootte en een offset op basis van 0 om een pagina lijst met regel items te retour neren.</span><span class="sxs-lookup"><span data-stu-id="e1e79-179">For large invoices, you can use this syntax with a specified size and 0-based offset to return a paged list of line items.</span></span> |
| <span data-ttu-id="e1e79-180">GET</span><span class="sxs-lookup"><span data-stu-id="e1e79-180">GET</span></span> | <span data-ttu-id="e1e79-181">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{Invoice-ID}/lineitems/OneTime/{invoice-line-item-type}? SeekOperation = volgende</span><span class="sxs-lookup"><span data-stu-id="e1e79-181">[*{baseURL}*](partner-center-rest-urls.md)/v1/invoices/{invoice-id}/lineitems/OneTime/{invoice-line-item-type}?seekOperation=Next</span></span>                               | <span data-ttu-id="e1e79-182">U kunt deze syntaxis gebruiken voor een factuur met de waarde **eenmalige** van de facturerings provider en stel **SeekOperation** in op **volgende** om de volgende pagina van factuur regel items weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e1e79-182">You can use this syntax for an invoice with a billing-provider value of **OneTime** and set **seekOperation** to **Next** to get the next page of invoice line items.</span></span> |

##### <a name="uri-parameters"></a><span data-ttu-id="e1e79-183">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="e1e79-183">URI parameters</span></span>

<span data-ttu-id="e1e79-184">Gebruik de volgende URI en query parameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="e1e79-184">Use the following URI and query parameters when creating the request.</span></span>

| <span data-ttu-id="e1e79-185">Naam</span><span class="sxs-lookup"><span data-stu-id="e1e79-185">Name</span></span>                   | <span data-ttu-id="e1e79-186">Type</span><span class="sxs-lookup"><span data-stu-id="e1e79-186">Type</span></span>   | <span data-ttu-id="e1e79-187">Vereist</span><span class="sxs-lookup"><span data-stu-id="e1e79-187">Required</span></span> | <span data-ttu-id="e1e79-188">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e1e79-188">Description</span></span>                                                       |
|------------------------|--------|----------|-------------------------------------------------------------------|
| <span data-ttu-id="e1e79-189">factuur-ID</span><span class="sxs-lookup"><span data-stu-id="e1e79-189">invoice-id</span></span>             | <span data-ttu-id="e1e79-190">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e1e79-190">string</span></span> | <span data-ttu-id="e1e79-191">Yes</span><span class="sxs-lookup"><span data-stu-id="e1e79-191">Yes</span></span>      | <span data-ttu-id="e1e79-192">Een teken reeks waarmee de factuur wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="e1e79-192">A string that identifies the invoice.</span></span>                             |
| <span data-ttu-id="e1e79-193">facturering-provider</span><span class="sxs-lookup"><span data-stu-id="e1e79-193">billing-provider</span></span>       | <span data-ttu-id="e1e79-194">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e1e79-194">string</span></span> | <span data-ttu-id="e1e79-195">Yes</span><span class="sxs-lookup"><span data-stu-id="e1e79-195">Yes</span></span>      | <span data-ttu-id="e1e79-196">De facturerings provider: ' Office ', ' Azure ', ' eenmalige '.</span><span class="sxs-lookup"><span data-stu-id="e1e79-196">The billing provider: "Office", "Azure", "OneTime".</span></span>               |
| <span data-ttu-id="e1e79-197">factuur-regel-item-type</span><span class="sxs-lookup"><span data-stu-id="e1e79-197">invoice-line-item-type</span></span> | <span data-ttu-id="e1e79-198">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e1e79-198">string</span></span> | <span data-ttu-id="e1e79-199">Yes</span><span class="sxs-lookup"><span data-stu-id="e1e79-199">Yes</span></span>      | <span data-ttu-id="e1e79-200">Het type factuur Details: "BillingLineItems", "UsageLineItems".</span><span class="sxs-lookup"><span data-stu-id="e1e79-200">The type of invoice detail: "BillingLineItems", "UsageLineItems".</span></span> |
| <span data-ttu-id="e1e79-201">grootte</span><span class="sxs-lookup"><span data-stu-id="e1e79-201">size</span></span>                   | <span data-ttu-id="e1e79-202">getal</span><span class="sxs-lookup"><span data-stu-id="e1e79-202">number</span></span> | <span data-ttu-id="e1e79-203">No</span><span class="sxs-lookup"><span data-stu-id="e1e79-203">No</span></span>       | <span data-ttu-id="e1e79-204">Het maximum aantal items dat moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e1e79-204">The maximum number of items to return.</span></span> <span data-ttu-id="e1e79-205">Standaard maximale grootte = 2000</span><span class="sxs-lookup"><span data-stu-id="e1e79-205">Default max size = 2000</span></span>    |
| <span data-ttu-id="e1e79-206">offset</span><span class="sxs-lookup"><span data-stu-id="e1e79-206">offset</span></span>                 | <span data-ttu-id="e1e79-207">getal</span><span class="sxs-lookup"><span data-stu-id="e1e79-207">number</span></span> | <span data-ttu-id="e1e79-208">No</span><span class="sxs-lookup"><span data-stu-id="e1e79-208">No</span></span>       | <span data-ttu-id="e1e79-209">De op nul gebaseerde index van het eerste regel item dat moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e1e79-209">The zero-based index of the first line item to return.</span></span>            |
| <span data-ttu-id="e1e79-210">seekOperation</span><span class="sxs-lookup"><span data-stu-id="e1e79-210">seekOperation</span></span>          | <span data-ttu-id="e1e79-211">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e1e79-211">string</span></span> | <span data-ttu-id="e1e79-212">No</span><span class="sxs-lookup"><span data-stu-id="e1e79-212">No</span></span>       | <span data-ttu-id="e1e79-213">Als **facturering-provider** gelijk is aan **eenmalige**, stelt u **seekOperation** gelijk aan **volgende** in om de volgende pagina van factuur regel items weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e1e79-213">If **billing-provider** equals **OneTime**, set **seekOperation** equal to **Next** to get the next page of invoice line items.</span></span> |
| <span data-ttu-id="e1e79-214">hasPartnerEarnedCredit</span><span class="sxs-lookup"><span data-stu-id="e1e79-214">hasPartnerEarnedCredit</span></span> | <span data-ttu-id="e1e79-215">booleaans</span><span class="sxs-lookup"><span data-stu-id="e1e79-215">bool</span></span> | <span data-ttu-id="e1e79-216">No</span><span class="sxs-lookup"><span data-stu-id="e1e79-216">No</span></span> | <span data-ttu-id="e1e79-217">De waarde die aangeeft of de regel items moeten worden geretourneerd waarvoor het tegoed van de partner is toegepast.</span><span class="sxs-lookup"><span data-stu-id="e1e79-217">The value indicating if to return the line items with partner earned credit applied.</span></span> <span data-ttu-id="e1e79-218">Opmerking: deze para meter wordt alleen toegepast wanneer het facturerings provider type eenmalige is en InvoiceLineItemType is ingesteld op UsageLineItems.</span><span class="sxs-lookup"><span data-stu-id="e1e79-218">Note: this parameter will be only applied when billing provider type is OneTime and InvoiceLineItemType is UsageLineItems.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e1e79-219">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e1e79-219">Request headers</span></span>

<span data-ttu-id="e1e79-220">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e1e79-220">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e1e79-221">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e1e79-221">Request body</span></span>

<span data-ttu-id="e1e79-222">Geen.</span><span class="sxs-lookup"><span data-stu-id="e1e79-222">None.</span></span>

## <a name="rest-response"></a><span data-ttu-id="e1e79-223">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e1e79-223">REST response</span></span>

<span data-ttu-id="e1e79-224">Als dit is gelukt, bevat het antwoord het verzamelen van regel items.</span><span class="sxs-lookup"><span data-stu-id="e1e79-224">If successful, the response contains the collection of line item details.</span></span>

<span data-ttu-id="e1e79-225">*Voor de **ChargeType** van het regel item wordt de **gekochte** waarde toegewezen aan **Nieuw**. De **terugbetaling** van de waarde is toegewezen aan **Annuleren**.*</span><span class="sxs-lookup"><span data-stu-id="e1e79-225">*For the line item **ChargeType**, the value **Purchase** is mapped to **New**. The value **Refund** is mapped to **Cancel**.*</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e1e79-226">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="e1e79-226">Response success and error codes</span></span>

<span data-ttu-id="e1e79-227">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="e1e79-227">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e1e79-228">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e1e79-228">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e1e79-229">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="e1e79-229">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="rest-request-response-examples"></a><span data-ttu-id="e1e79-230">REST-aanvraag-antwoord voorbeelden</span><span class="sxs-lookup"><span data-stu-id="e1e79-230">REST request-response examples</span></span>

### <a name="request-response-example-1"></a><span data-ttu-id="e1e79-231">Aanvraag-antwoord-voor beeld 1</span><span class="sxs-lookup"><span data-stu-id="e1e79-231">Request-response example 1</span></span>

<span data-ttu-id="e1e79-232">In dit voor beeld zijn de volgende details:</span><span class="sxs-lookup"><span data-stu-id="e1e79-232">In this example, the details are as follows:</span></span>

- <span data-ttu-id="e1e79-233">**BillingProvider**: **Office**</span><span class="sxs-lookup"><span data-stu-id="e1e79-233">**BillingProvider**: **Office**</span></span>
- <span data-ttu-id="e1e79-234">**InvoiceLineItemType**: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="e1e79-234">**InvoiceLineItemType**: **BillingLineItems**</span></span>

#### <a name="request-example-1"></a><span data-ttu-id="e1e79-235">Voor beeld 1 aanvragen</span><span class="sxs-lookup"><span data-stu-id="e1e79-235">Request example 1</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/1234000000/lineitems?provider=Office&nvoicelineitemtype=BillingLineItems&size=2&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-1"></a><span data-ttu-id="e1e79-236">Antwoord voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="e1e79-236">Response example 1</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

{
    "totalCount": 2,
    "items": [{
            "partnerId": "3b33e682-00c3-41ee-9dd2-a548adf56438",
            "customerId": "74221236-D09C-4870-AC1D-33E155E9AEBE",
            "customerName": "TSTAGIN1CUST190",
            "mpnId": 4391507,
            "tier2MpnId": -1,
            "orderId": "567735045559164136",
            "subscriptionId": "4KIKawEAAAAAAAEA",
            "syndicationPartnerSubscriptionNumber": "1F58ACD7-FE51-4705-9567-D009C9ADA150",
            "offerId": "AAA5B3F0-0EE2-431B-A42F-3F18F3C6D540",
            "durableOfferId": "2F707C7C-2433-49A5-A437-9CA7CF40D3EB",
            "offerName": "EXCHANGE ONLINE (PLAN 2)",
            "domainName": "TStagin1Cust190.onmicrosoft.com",
            "billingCycleType": "MONTHLY",
            "subscriptionName": "EXCHANGE ONLINE (PLAN 2)",
            "subscriptionDescription": "EXCHANGE ONLINE (PLAN 2)",
            "subscriptionStartDate": "2017-05-12T00:00:00",
            "subscriptionEndDate": "2018-06-10T00:00:00",
            "chargeStartDate": "2017-05-12T00:00:00",
            "chargeEndDate": "2017-06-09T00:00:00",
            "chargeType": "New",
            "unitPrice": 0.0,
            "quantity": 3,
            "amount": 0.0,
            "totalOtherDiscount": 0.0,
            "subtotal": 0.0,
            "tax": 0.0,
            "totalForCustomer": 0.0,
            "currency": "USD",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "office",
            "attributes": {
                "objectType": "LicenseBasedLineItem"
            }
        }, {
            "partnerId": "3b33e682-00c3-41ee-9dd2-a548adf56438",
            "customerId": "74221236-D09C-4870-AC1D-33E155E9AEBE",
            "customerName": "TSTAGIN1CUST190",
            "mpnId": 4391507,
            "tier2MpnId": -1,
            "orderId": "567735045564795186",
            "subscriptionId": "Ik4YawEAAAAAAAEA",
            "syndicationPartnerSubscriptionNumber": "D8A8F773-9D3E-4244-8797-3182075F09FA",
            "offerId": "618B53FE-9B99-428B-9745-F706AEAF3979",
            "durableOfferId": "69C67983-CF78-4102-83F6-3E5FD246864F",
            "offerName": "SHAREPOINT ONLINE (PLAN 2)",
            "domainName": "TStagin1Cust190.onmicrosoft.com",
            "billingCycleType": "MONTHLY",
            "subscriptionName": "SHAREPOINT ONLINE (PLAN 2)",
            "subscriptionDescription": "SHAREPOINT ONLINE (PLAN 2)",
            "subscriptionStartDate": "2017-05-13T00:00:00",
            "subscriptionEndDate": "2018-06-10T00:00:00",
            "chargeStartDate": "2017-05-13T00:00:00",
            "chargeEndDate": "2017-06-09T00:00:00",
            "chargeType": "New",
            "unitPrice": 0.0,
            "quantity": 1,
            "amount": 0.0,
            "totalOtherDiscount": 0.0,
            "subtotal": 0.0,
            "tax": 0.0,
            "totalForCustomer": 0.0,
            "currency": "USD",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "office",
            "attributes": {
                "objectType": "LicenseBasedLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/1234000000/lineitems?provider=Office&nvoicelineitemtype=BillingLineItems&size=2&offset=0",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/1234000000/lineitems?provider=Office&nvoicelineitemtype=BillingLineItems&size=2&offset=",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-2"></a><span data-ttu-id="e1e79-237">Aanvraag-antwoord-voor beeld 2</span><span class="sxs-lookup"><span data-stu-id="e1e79-237">Request-response example 2</span></span>

<span data-ttu-id="e1e79-238">In het volgende voor beeld ziet u de volgende informatie:</span><span class="sxs-lookup"><span data-stu-id="e1e79-238">In the following example, the details are as follows:</span></span>

- <span data-ttu-id="e1e79-239">**BillingProvider**: **Azure**</span><span class="sxs-lookup"><span data-stu-id="e1e79-239">**BillingProvider**: **Azure**</span></span>
- <span data-ttu-id="e1e79-240">**InvoiceLineItemType**: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="e1e79-240">**InvoiceLineItemType**: **BillingLineItems**</span></span>

#### <a name="request-example-2"></a><span data-ttu-id="e1e79-241">Voor beeld 2 aanvragen</span><span class="sxs-lookup"><span data-stu-id="e1e79-241">Request example 2</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=BillingLineItems&size=2&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-2"></a><span data-ttu-id="e1e79-242">Antwoord voorbeeld 2</span><span class="sxs-lookup"><span data-stu-id="e1e79-242">Response example 2</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

{
    "totalCount": 2,
    "items": [
        {
            "detailLineItemId": 1,
            "sku": "7UD-00001",
            "includedQuantity": 0,
            "overageQuantity": 745,
            "listPrice": 0.085,
            "currency": "USD",
            "pretaxCharges": 63.33,
            "taxAmount": 6.34,
            "postTaxTotal": 69.67,
            "pretaxEffectiveRate": 0.08500671,
            "postTaxEffectiveRate": 0.09351677,
            "chargeType": "Assess usage fee for current cycle",
            "invoiceLineItemType": "billing_line_items",
            "partnerId": "1F5CCB06-8E36-4A74-A74C-FCAA9E000000",
            "partnerName": "TEST_TEST_Big foot consulting",
            "partnerBillableAccountId": "1010578050",
            "customerId": "65726577-c208-40fd-9735-8c85ac000000",
            "domainName": "600test.onmicrosoft.com",
            "customerCompanyName": "601 tests",
            "mpnId": 4390934,
            "tier2MpnId": -1,
            "invoiceNumber": "1234000000",
            "subscriptionId": "87f4b92f-a490-485e-ad34-5b70cb000000",
            "subscriptionName": "Microsoft Azure",
            "subscriptionDescription": "Microsoft Azure",
            "billingCycleType": "Monthly",
            "orderId": "568297985427000000",
            "serviceName": "Azure App Service",
            "serviceType": "Standard Plan",
            "resourceGuid": "505db374-df8a-44df-9d8c-13c14b61dee1",
            "resourceName": "S1",
            "region": "",
            "consumedQuantity": 745,
            "chargeStartDate": "2019-08-02T00:00:00",
            "chargeEndDate": "2019-09-01T00:00:00",
            "unit": "1 Hour",
            "billingProvider": "azure",
            "attributes": {
                "objectType": "UsageBasedLineItem"
            }
        },
        {
            "detailLineItemId": 1,
            "sku": "7UD-00001",
            "includedQuantity": 0,
            "overageQuantity": 0.000882,
            "listPrice": 0.0383,
            "currency": "USD",
            "pretaxCharges": 0,
            "taxAmount": 0,
            "postTaxTotal": 0,
            "pretaxEffectiveRate": 0,
            "postTaxEffectiveRate": 0,
            "chargeType": "Assess usage fee for current cycle",
            "invoiceLineItemType": "billing_line_items",
            "partnerId": "1F5CCB06-8E36-4A74-A74C-FCAA9E87E26A",
            "partnerName": "TEST_TEST_Big foot consulting",
            "partnerBillableAccountId": "1010578050",
            "customerId": "65726577-c208-40fd-9735-8c85ac9cac68",
            "domainName": "600test.onmicrosoft.com",
            "customerCompanyName": "601 tests",
            "mpnId": 4390934,
            "tier2MpnId": -1,
            "invoiceNumber": "1234000000",
            "subscriptionId": "87f4b92f-a490-485e-ad34-5b70cb000000",
            "subscriptionName": "Microsoft Azure",
            "subscriptionDescription": "Microsoft Azure",
            "billingCycleType": "Monthly",
            "orderId": "568297985427000000",
            "serviceName": "Storage",
            "serviceType": "Standard Page Blob",
            "resourceGuid": "d23a5753-ff85-4ddf-af28-8cc5cf2d3882",
            "resourceName": "LRS Data Stored",
            "region": "",
            "consumedQuantity": 0.000882,
            "chargeStartDate": "2019-08-02T00:00:00",
            "chargeEndDate": "2019-09-01T00:00:00",
            "unit": "1 GB/Month",
            "billingProvider": "azure",
            "attributes": {
                "objectType": "UsageBasedLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=BillingLineItems&size=2&offset=0",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=BillingLineItems&size=2&offset=2",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-3"></a><span data-ttu-id="e1e79-243">Aanvraag-antwoord-voor beeld 3</span><span class="sxs-lookup"><span data-stu-id="e1e79-243">Request-response example 3</span></span>

<span data-ttu-id="e1e79-244">In het volgende voor beeld ziet u de volgende informatie:</span><span class="sxs-lookup"><span data-stu-id="e1e79-244">In the following example, the details are as follows:</span></span>

- <span data-ttu-id="e1e79-245">**BillingProvider**: **Azure**</span><span class="sxs-lookup"><span data-stu-id="e1e79-245">**BillingProvider**: **Azure**</span></span>
- <span data-ttu-id="e1e79-246">**InvoiceLineItemType**: **UsageLineItems**</span><span class="sxs-lookup"><span data-stu-id="e1e79-246">**InvoiceLineItemType**: **UsageLineItems**</span></span>

#### <a name="request-example-3"></a><span data-ttu-id="e1e79-247">Voor beeld 3 aanvragen</span><span class="sxs-lookup"><span data-stu-id="e1e79-247">Request example 3</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=UsageLineItems&size=2&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-3"></a><span data-ttu-id="e1e79-248">Antwoord voorbeeld 3</span><span class="sxs-lookup"><span data-stu-id="e1e79-248">Response example 3</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

{
    "totalCount": 2,
    "items": [
        {
            "customerBillableAccount": "1439508127",
            "usageDate": "2019-08-05T00:00:00",
            "invoiceLineItemType": "usage_line_items",
            "partnerId": "1F5CCB06-8E36-4A74-A74C-FCAA9E000000",
            "partnerName": "TEST_TEST_BIG FOOT CONSULTING",
            "partnerBillableAccountId": "1010578050",
            "customerId": "9E9B71BA-3442-458B-B519-E1CCF72FBB54",
            "domainName": "test600.onmicrosoft.com",
            "customerCompanyName": "600 TEST",
            "mpnId": 4390934,
            "tier2MpnId": -1,
            "invoiceNumber": "1234000000",
            "subscriptionId": "F9BA6DA0-6DAC-4F88-B623-313C9B9C117A",
            "subscriptionName": "MICROSOFT AZURE",
            "subscriptionDescription": "MICROSOFT AZURE",
            "billingCycleType": "MONTHLY",
            "orderId": "568297985577171353",
            "serviceName": "STORAGE",
            "serviceType": "STANDARD PAGE BLOB",
            "resourceGuid": "9CC63CF8-6593-410A-B0E7-26A4EF71E8B3",
            "resourceName": "DISK DELETE OPERATIONS",
            "region": "",
            "consumedQuantity": 2.9616,
            "chargeStartDate": "2019-08-05T00:00:00",
            "chargeEndDate": "2019-09-04T00:00:00",
            "unit": "10K",
            "billingProvider": "azure",
            "attributes": {
                "objectType": "DailyUsageLineItem"
            }
        },
        {
            "customerBillableAccount": "1307536861",
            "usageDate": "2019-08-10T00:00:00",
            "invoiceLineItemType": "usage_line_items",
            "partnerId": "1F5CCB06-8E36-4A74-A74C-FCAA9E000000",
            "partnerName": "TEST_TEST_BIG FOOT CONSULTING",
            "partnerBillableAccountId": "1010578050",
            "customerId": "EB53B7BD-267E-440E-B3C0-8F0B40000000",
            "domainName": "brandontest.onmicrosoft.com",
            "customerCompanyName": "BRANDON'S TEST",
            "mpnId": 4390934,
            "tier2MpnId": -1,
            "invoiceNumber": "1234000000",
            "subscriptionId": "62D22561-AB15-41E5-AD59-99025C000000",
            "subscriptionName": "MICROSOFT AZURE",
            "subscriptionDescription": "MICROSOFT AZURE",
            "billingCycleType": "MONTHLY",
            "orderId": "568297985605838583",
            "serviceName": "VIRTUAL MACHINES",
            "serviceType": "D/DS SERIES WINDOWS",
            "resourceGuid": "62C64B6C-4033-4E20-AB33-9E81271AC12A",
            "resourceName": "D1/DS1",
            "region": "US WEST",
            "consumedQuantity": 24,
            "chargeStartDate": "2019-08-05T00:00:00",
            "chargeEndDate": "2019-09-04T00:00:00",
            "unit": "1 HOUR",
            "billingProvider": "azure",
            "attributes": {
                "objectType": "DailyUsageLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=UsageLineItems&size=2&offset=0",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/1234000000/lineitems?provider=Azure&invoicelineitemtype=UsageLineItems&size=2&offset=2",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-4"></a><span data-ttu-id="e1e79-249">Aanvraag-antwoord-voor beeld 4</span><span class="sxs-lookup"><span data-stu-id="e1e79-249">Request-response example 4</span></span>

<span data-ttu-id="e1e79-250">In het volgende voor beeld ziet u de volgende informatie:</span><span class="sxs-lookup"><span data-stu-id="e1e79-250">In the following example, the details are as follows:</span></span>

- <span data-ttu-id="e1e79-251">**BillingProvider**: **eenmalige**</span><span class="sxs-lookup"><span data-stu-id="e1e79-251">**BillingProvider**: **OneTime**</span></span>
- <span data-ttu-id="e1e79-252">**InvoiceLineItemType**: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="e1e79-252">**InvoiceLineItemType**: **BillingLineItems**</span></span>

#### <a name="request-example-4"></a><span data-ttu-id="e1e79-253">Voor beeld 4 aanvragen</span><span class="sxs-lookup"><span data-stu-id="e1e79-253">Request example 4</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/G000024135/lineitems/OneTime/BillingLineItems?size=2&offset=0 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-4"></a><span data-ttu-id="e1e79-254">Antwoord voorbeeld 4</span><span class="sxs-lookup"><span data-stu-id="e1e79-254">Response example 4</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

 {
    "continuationToken": "d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7",
    "totalCount": 2,
    "items": [
        {
            "partnerId": "6480d686-cfb4-424d-a945-6b9b9f000000",
            "customerId": "org:9060d13d-c5ed-482e-b059-a15a38000000",
            "customerName": "recipientCustomerName",
            "customerDomainName": "recipientCustomerDomain",
            "invoiceNumber": "1234000000",
            "quoteId": "abcd12345678",
            "mpnId": "4870137",
            "resellerMpnId": 0,
            "orderId": "QDOx5ZN3YR9uYhm4M1MGQJ_0nievUOrx1",
            "orderDate": "2018-02-08T22:31:42.9397946Z",
            "productId": "productid",
            "skuId": "skuid",
            "availabilityId": "availabilityid",
            "productName": "TEST PRODUCT",
            "skuName": "TEST SKU TITLE",
            "chargeType": "New",
            "unitPrice": 431.8,
            "effectiveUnitPrice": 496.07,
            "unitType": "Seats",
            "quantity": 1,
            "subtotal": 431.8,
            "taxTotal": 38.87,
            "totalForCustomer": 470.67,
            "currency": "USD",
            "providerName": "Test Networks Inc",
            "providerId": "12343810",
            "subscriptionDescription": "",
            "subscriptionId": "281e26fe-9ce7-415b-911c-f39232000000",
            "subscriptionStartDate": "2019-01-03T19:53:55.1292512+00:00",
            "subscriptionEndDate": "2019-02-02T19:53:55.1292512+00:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "1234278124b8",
            "priceAdjustmentDescription": "[\"100.0% Tier 1 Discount\"]",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-09-30T23:59:59Z",
            "billableQuantity": 0.0159369774,
            "meterDescription": "Bandwidth - Data Transfer In (GB) - Zone 2",
            "billingFrequency": "Monthly",
            "reservationOrderId": "883d475b-0000-2222-0000-8818752f1234",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        },
        {
            "partnerId": "6480d686-cfb4-424d-a945-6b9b9f4badc2",
            "customerId": "org:9060d13d-c5ed-482e-b059-a15a38cbb28e",
            "customerName": "recipientCustomerName",
            "customerDomainName": "recipientCustomerDomain",
            "invoiceNumber": "1234000000",
            "quoteId": "abcd12345678",
            "mpnId": "4870137",
            "resellerMpnId": 0,
            "orderId": "QDOx5ZN3YR9uYhm4M1MGQJ_0nievUOrx1",
            "orderDate": "2018-02-08T22:31:42.9397946Z",
            "productId": "productid",
            "skuId": "skuid",
            "availabilityId": "availabilityid",
            "productName": "TEST PRODUCT",
            "skuName": "TEST SKU TITLE",
            "chargeType": "New",
            "unitPrice": 26.35,
            "effectiveUnitPrice": 496.07,
            "unitType": "1 Hour",
            "quantity": 1,
            "subtotal": 26.35,
            "taxTotal": 2.37,
            "totalForCustomer": 28.72,
            "currency": "USD",
            "providerName": "Test Networks Inc",
            "providerId": "12343810",
            "subscriptionDescription": "",
            "subscriptionId": "281e26fe-9ce7-415b-911c-f39232ea904a",
            "subscriptionStartDate": "2019-01-03T19:53:55.1292512+00:00",
            "subscriptionEndDate": "2019-02-02T19:53:55.1292512+00:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "1234578124b8",
            "priceAdjustmentDescription": "[\"100.0% Tier 1 Discount\"]",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-09-30T23:59:59Z",
            "billableQuantity": 0.0130687981,
            "meterDescription": "Bandwidth - Data Transfer In (GB) - Zone 2",
            "reservationOrderId": "",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/G000024135/lineitems?provider=OneTime&nvoicelineitemtype=BillingLineItems&size=2",
            "method": "GET",
            "headers": []
        },
        "next": {
            "uri": "/invoices/G000024135/lineitems?provider=OneTime&nvoicelineitemtype=BillingLineItems&size=2?seekOperation=Next",
            "method": "GET",
            "headers": [
                {
                    "key": "MS-ContinuationToken",
                    "value": "d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7"
                }
            ]
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

### <a name="request-response-example-5"></a><span data-ttu-id="e1e79-255">Aanvraag-antwoord-voor beeld 5</span><span class="sxs-lookup"><span data-stu-id="e1e79-255">Request-response example 5</span></span>

<span data-ttu-id="e1e79-256">In het volgende voor beeld wordt er gepagineerd met behulp van een vervolg token.</span><span class="sxs-lookup"><span data-stu-id="e1e79-256">In the following example, there is paging using a continuation token.</span></span> <span data-ttu-id="e1e79-257">De details zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="e1e79-257">The details are as follows:</span></span>

- <span data-ttu-id="e1e79-258">**BillingProvider**: **eenmalige**</span><span class="sxs-lookup"><span data-stu-id="e1e79-258">**BillingProvider**: **OneTime**</span></span>
- <span data-ttu-id="e1e79-259">**InvoiceLineItemType**: **BillingLineItems**</span><span class="sxs-lookup"><span data-stu-id="e1e79-259">**InvoiceLineItemType**: **BillingLineItems**</span></span>
- <span data-ttu-id="e1e79-260">**SeekOperation**: **volgende**</span><span class="sxs-lookup"><span data-stu-id="e1e79-260">**SeekOperation**: **Next**</span></span>

#### <a name="request-example-5"></a><span data-ttu-id="e1e79-261">Voor beeld 5 aanvragen</span><span class="sxs-lookup"><span data-stu-id="e1e79-261">Request example 5</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/invoices/G000024135/lineitems/OneTime/BillingLineItems?seekOperation=Next HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-ContinuationToken: d19617b8-fbe5-4684-a5d8-0230972fb0cf,0705c4a9-39f7-4261-ba6d-53e24a9ce47d_a4ayc/80/OGda4BO/1o/V0etpOqiLx1JwB5S3beHW0s=,0d81c700-98b4-4b13-9129-ffd5620f72e7
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

#### <a name="response-example-5"></a><span data-ttu-id="e1e79-262">Antwoord voorbeeld 5</span><span class="sxs-lookup"><span data-stu-id="e1e79-262">Response example 5</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2484
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5e612512-4345-4bb0-866e-47aeda03fe54
MS-RequestId: 1eb2ecb8-37af-45f4-a1a1-358de3ca2b9e
MS-CV: bpqyomePDUqrSSYC.0
MS-ServerId: 202010406
Date: Thu, 07 Sep 2017 23:31:09 GMT

{
    "totalCount": 1,
    "items": [
        {
            "partnerId": "6480d686-cfb4-424d-a945-6b9b9f000000",
            "customerId": "org:9060d13d-c5ed-482e-b059-a15a38000000",
            "customerName": "recipientCustomerName",
            "customerDomainName": "recipientCustomerDomain",
            "invoiceNumber": "1234000000",
            "quoteId": "abcd12345678",
            "mpnId": "4870137",
            "resellerMpnId": 0,
            "orderId": "NeqT31Kziwf8gkCXM9YQToWTqU-9Jbm81",
            "orderDate": "2018-02-08T22:31:47.1751688Z",
            "productId": "DZH318Z0BQ3P",
            "skuId": "001F",
            "availabilityId": "DZH318Z0DR0H",
            "productName": "Reserved VM Instance, Standard_D1, AP East, 3 years",
            "skuName": "D Series",
            "chargeType": "New",
            "unitPrice": 1447,
            "effectiveUnitPrice": 496.07,
            "unitType": "Seats",
            "quantity": 1,
            "subtotal": 1447,
            "taxTotal": 130.24,
            "totalForCustomer": 1577.24,
            "currency": "USD",
            "providerName": "Test Networks Inc",
            "providerId": "12343810",
            "subscriptionDescription": "",
            "subscriptionId": "281e26fe-9ce7-415b-911c-f39232000000",
            "subscriptionStartDate": "2019-01-03T19:53:55.1292512+00:00",
            "subscriptionEndDate": "2019-02-02T19:53:55.1292512+00:00",
            "termAndBillingCycle": "1 Month Subscription",
            "alternateId": "1234568124b8",
            "priceAdjustmentDescription": "",
            "pricingCurrency": "USD",
            "pcToBCExchangeRate": 1,
            "pcToBCExchangeRateDate": "2019-09-30T23:59:59Z",
            "billableQuantity": 0.0130687981,
            "meterDescription": "Bandwidth - Data Transfer In (GB) - Zone 2",
            "reservationOrderId": "",
            "billingFrequency": "Monthly",
            "invoiceLineItemType": "billing_line_items",
            "billingProvider": "one_time",
            "attributes": {
                "objectType": "OneTimeInvoiceLineItem"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/invoices/G000024135/lineitems?provider=OneTime&nvoicelineitemtype=BillingLineItems&size=2",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
