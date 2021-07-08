---
title: Een lijst met producten ophalen (per land)
description: U kunt de productresource gebruiken om een verzameling producten per klantland op te halen.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 1258727ecbe7c5cc332624577fa8a355e28e3717
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874207"
---
# <a name="get-a-list-of-products-by-country"></a><span data-ttu-id="18b53-103">Een lijst met producten ophalen (per land)</span><span class="sxs-lookup"><span data-stu-id="18b53-103">Get a list of products (by country)</span></span>

<span data-ttu-id="18b53-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="18b53-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="18b53-105">U kunt de volgende methoden gebruiken om een verzameling producten op te halen die beschikbaar zijn in een bepaald land.</span><span class="sxs-lookup"><span data-stu-id="18b53-105">You can use the following methods to get a collection of products available in a particular country.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="18b53-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="18b53-106">Prerequisites</span></span>

- <span data-ttu-id="18b53-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="18b53-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="18b53-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="18b53-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="18b53-109">Een land.</span><span class="sxs-lookup"><span data-stu-id="18b53-109">A country.</span></span>

## <a name="c"></a><span data-ttu-id="18b53-110">C\#</span><span class="sxs-lookup"><span data-stu-id="18b53-110">C\#</span></span>

<span data-ttu-id="18b53-111">Een lijst met producten op te halen:</span><span class="sxs-lookup"><span data-stu-id="18b53-111">To get a list of products:</span></span>

1. <span data-ttu-id="18b53-112">Gebruik de **verzameling IAggregatePartner.Products om** het land te selecteren met behulp van de **methode ByCountry().**</span><span class="sxs-lookup"><span data-stu-id="18b53-112">Use your **IAggregatePartner.Products** collection to select the country by using the **ByCountry()** method.</span></span>

2. <span data-ttu-id="18b53-113">Selecteer de catalogusweergave met behulp van de **methode ByTargetView().**</span><span class="sxs-lookup"><span data-stu-id="18b53-113">Select the catalog view using the **ByTargetView()** method.</span></span>

3. <span data-ttu-id="18b53-114">(Optioneel) Selecteer het reserveringsbereik met behulp **van de methode ByReservationScope().**</span><span class="sxs-lookup"><span data-stu-id="18b53-114">(Optional) Select the reservation scope using the **ByReservationScope()** method.</span></span>

4. <span data-ttu-id="18b53-115">(Optioneel) Selecteer het doelsegment met behulp van **de methode ByTargetSegment().**</span><span class="sxs-lookup"><span data-stu-id="18b53-115">(Optional) Select the target segment using the **ByTargetSegment()** method.</span></span>

5. <span data-ttu-id="18b53-116">Roep de **methode Get()** of **GetAsync()** aan om de verzameling te retourneren.</span><span class="sxs-lookup"><span data-stu-id="18b53-116">Call the **Get()** or **GetAsync()** method to return the collection.</span></span>

```csharp
IAggregatePartner partnerOperations;

// Get the products for the specified catalog view.
ResourceCollection<Products> products = partnerOperations.Products.ByCountry("US").ByTargetView("MicrosoftAzure").Get();

// Get the products filtered by target view and target segment.
ResourceCollection<Products> products = partnerOperations.Products.ByCountry("US").ByTargetView("MicrosoftAzure").ByTargetSegment("commercial").Get();

// Get the products for Azure reservations which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions only.
ResourceCollection<Product> products = partnerOperations.Products.ByCountry("US").ByTargetView("AzureReservations").Get();

// Get the products for Azure reservations which are applicable to Azure plans only.
ResourceCollection<Product> products = partnerOperations.Products.ByCountry("US").ByTargetView("AzureReservations").ByReservationScope("AzurePlan").Get();

```

## <a name="java"></a><span data-ttu-id="18b53-117">Java</span><span class="sxs-lookup"><span data-stu-id="18b53-117">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="18b53-118">Een lijst met producten op te halen:</span><span class="sxs-lookup"><span data-stu-id="18b53-118">To get a list of products:</span></span>

1. <span data-ttu-id="18b53-119">Gebruik de **functie IAggregatePartner.getProducts** om het land te selecteren met behulp van de **functie byCountry().**</span><span class="sxs-lookup"><span data-stu-id="18b53-119">Use your **IAggregatePartner.getProducts** function to select the country by using the **byCountry()** function.</span></span>

2. <span data-ttu-id="18b53-120">Selecteer de catalogusweergave met behulp van **de functie byTargetView().**</span><span class="sxs-lookup"><span data-stu-id="18b53-120">Select the catalog view using the **byTargetView()** function.</span></span>
3. <span data-ttu-id="18b53-121">(Optioneel) Selecteer het doelsegment met behulp van **de functie byTargetSegment().**</span><span class="sxs-lookup"><span data-stu-id="18b53-121">(Optional) Select the target segment using the **byTargetSegment()** function.</span></span>

4. <span data-ttu-id="18b53-122">Roep de **functie get()** aan om de verzameling te retourneren.</span><span class="sxs-lookup"><span data-stu-id="18b53-122">Call the **get()** function to return the collection.</span></span>

```java
// IAggregatePartner partnerOperations;

// Get the products for the specified catalog view.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").get();

// Get the products filtered by target view and target segment.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").byTargetSegment("commercial").get();
```

## <a name="powershell"></a><span data-ttu-id="18b53-123">PowerShell</span><span class="sxs-lookup"><span data-stu-id="18b53-123">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="18b53-124">Een lijst met producten op te halen:</span><span class="sxs-lookup"><span data-stu-id="18b53-124">To get a list of products:</span></span>

1. <span data-ttu-id="18b53-125">Voer de [**opdracht Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) uit.</span><span class="sxs-lookup"><span data-stu-id="18b53-125">Execute the [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) command.</span></span>

2. <span data-ttu-id="18b53-126">Selecteer de catalogus door de parameter **Catalog op te** geven.</span><span class="sxs-lookup"><span data-stu-id="18b53-126">Select the catalog by specifying the **Catalog** parameter.</span></span>
3. <span data-ttu-id="18b53-127">(Optioneel) Selecteer het doelsegment door de **parameter Segment op te** geven.</span><span class="sxs-lookup"><span data-stu-id="18b53-127">(Optional) Select the target segment by specifying the **Segment** parameter.</span></span>

```powershell
Get-PartnerProduct -Catalog 'Azure' -Segment 'commercial'
```

## <a name="rest-request"></a><span data-ttu-id="18b53-128">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="18b53-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="18b53-129">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="18b53-129">Request syntax</span></span>

| <span data-ttu-id="18b53-130">Methode</span><span class="sxs-lookup"><span data-stu-id="18b53-130">Method</span></span>  | <span data-ttu-id="18b53-131">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="18b53-131">Request URI</span></span>                                                                                                                                    |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="18b53-132">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="18b53-132">**GET**</span></span> | <span data-ttu-id="18b53-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/products?country={country}&targetView={targetView}&targetSegment={targetSegment} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="18b53-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/products?country={country}&targetView={targetView}&targetSegment={targetSegment} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="18b53-134">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="18b53-134">URI parameters</span></span>

<span data-ttu-id="18b53-135">Gebruik het volgende pad en de queryparameters om een lijst met producten op te halen.</span><span class="sxs-lookup"><span data-stu-id="18b53-135">Use the following path and query parameters to get a list of products.</span></span>

| <span data-ttu-id="18b53-136">Naam</span><span class="sxs-lookup"><span data-stu-id="18b53-136">Name</span></span>                   | <span data-ttu-id="18b53-137">Type</span><span class="sxs-lookup"><span data-stu-id="18b53-137">Type</span></span>     | <span data-ttu-id="18b53-138">Vereist</span><span class="sxs-lookup"><span data-stu-id="18b53-138">Required</span></span> | <span data-ttu-id="18b53-139">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="18b53-139">Description</span></span>                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| <span data-ttu-id="18b53-140">country</span><span class="sxs-lookup"><span data-stu-id="18b53-140">country</span></span>                | <span data-ttu-id="18b53-141">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="18b53-141">string</span></span>   | <span data-ttu-id="18b53-142">Ja</span><span class="sxs-lookup"><span data-stu-id="18b53-142">Yes</span></span>      | <span data-ttu-id="18b53-143">De land-/regio-id.</span><span class="sxs-lookup"><span data-stu-id="18b53-143">The country/region ID.</span></span>                                                  |
| <span data-ttu-id="18b53-144">targetView</span><span class="sxs-lookup"><span data-stu-id="18b53-144">targetView</span></span>             | <span data-ttu-id="18b53-145">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="18b53-145">string</span></span>   | <span data-ttu-id="18b53-146">Ja</span><span class="sxs-lookup"><span data-stu-id="18b53-146">Yes</span></span>      | <span data-ttu-id="18b53-147">Identificeert de doelweergave van de catalogus.</span><span class="sxs-lookup"><span data-stu-id="18b53-147">Identifies the target view of the catalog.</span></span> <span data-ttu-id="18b53-148">De ondersteunde waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="18b53-148">The supported values are:</span></span> <br/><br/><span data-ttu-id="18b53-149">**Azure,** dat alle Azure-items bevat</span><span class="sxs-lookup"><span data-stu-id="18b53-149">**Azure**, which includes all Azure items</span></span><br/><br/><span data-ttu-id="18b53-150">**AzureReservations,** dat alle Azure-reserveringsitems bevat</span><span class="sxs-lookup"><span data-stu-id="18b53-150">**AzureReservations**, which includes all Azure reservation items</span></span><br/><br/><span data-ttu-id="18b53-151">**AzureReservationsVM,** dat alle reserveringsitems voor virtuele machines (VM's) bevat</span><span class="sxs-lookup"><span data-stu-id="18b53-151">**AzureReservationsVM**, which includes all virtual machine (VM) reservation items</span></span><br/><br/><span data-ttu-id="18b53-152">**AzureReservationsSQL,** dat alle SQL reserveringsitems bevat</span><span class="sxs-lookup"><span data-stu-id="18b53-152">**AzureReservationsSQL**, which includes all SQL reservation items</span></span><br/><br/><span data-ttu-id="18b53-153">**AzureReservationsCosmosDb,** dat alle reserveringsitems voor de Cosmos-database bevat</span><span class="sxs-lookup"><span data-stu-id="18b53-153">**AzureReservationsCosmosDb**, which includes all Cosmos database reservation items</span></span><br/><br/><span data-ttu-id="18b53-154">**MicrosoftAzure,** dat items bevat voor Microsoft Azure -abonnementen (**MS-AZR-0145P**) en Azure-abonnementen</span><span class="sxs-lookup"><span data-stu-id="18b53-154">**MicrosoftAzure**, which includes items for Microsoft Azure subscriptions (**MS-AZR-0145P**) and Azure plans</span></span><br/><br/><span data-ttu-id="18b53-155">**OnlineServices,** met alle onlineservice-items (inclusief producten op de commerciële marketplace)</span><span class="sxs-lookup"><span data-stu-id="18b53-155">**OnlineServices**, which includes all online service items (including commercial marketplace products)</span></span><br/><br/><span data-ttu-id="18b53-156">**Software**, die alle software-items bevat</span><span class="sxs-lookup"><span data-stu-id="18b53-156">**Software**, which includes all software items</span></span><br/><br/><span data-ttu-id="18b53-157">**SoftwareSUSELinux,** dat alle software-SUSE Linux-items bevat</span><span class="sxs-lookup"><span data-stu-id="18b53-157">**SoftwareSUSELinux**, which includes all software SUSE Linux items</span></span><br/><br/><span data-ttu-id="18b53-158">**SoftwarePerpetual,** dat alle permanente software-items bevat</span><span class="sxs-lookup"><span data-stu-id="18b53-158">**SoftwarePerpetual**, which includes all perpetual software items</span></span><br/><br/><span data-ttu-id="18b53-159">**SoftwareAbonnementen,** die alle softwareabonnementitems bevat</span><span class="sxs-lookup"><span data-stu-id="18b53-159">**SoftwareSubscriptions**, which includes all software subscription items</span></span>    |
| <span data-ttu-id="18b53-160">targetSegment</span><span class="sxs-lookup"><span data-stu-id="18b53-160">targetSegment</span></span>          | <span data-ttu-id="18b53-161">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="18b53-161">string</span></span>   | <span data-ttu-id="18b53-162">No</span><span class="sxs-lookup"><span data-stu-id="18b53-162">No</span></span>       | <span data-ttu-id="18b53-163">Identificeert het doelsegment.</span><span class="sxs-lookup"><span data-stu-id="18b53-163">Identifies the target segment.</span></span> <span data-ttu-id="18b53-164">De weergave voor verschillende doelgroepen.</span><span class="sxs-lookup"><span data-stu-id="18b53-164">The view for different target audiences.</span></span> <span data-ttu-id="18b53-165">De ondersteunde waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="18b53-165">The supported values are:</span></span> <br/><br/><span data-ttu-id="18b53-166">**Commerciële**</span><span class="sxs-lookup"><span data-stu-id="18b53-166">**commercial**</span></span><br/><span data-ttu-id="18b53-167">**Onderwijs**</span><span class="sxs-lookup"><span data-stu-id="18b53-167">**education**</span></span><br/><span data-ttu-id="18b53-168">**Regering**</span><span class="sxs-lookup"><span data-stu-id="18b53-168">**government**</span></span><br/><span data-ttu-id="18b53-169">**Non-profit**</span><span class="sxs-lookup"><span data-stu-id="18b53-169">**nonprofit**</span></span>  |
| <span data-ttu-id="18b53-170">reservationScope</span><span class="sxs-lookup"><span data-stu-id="18b53-170">reservationScope</span></span> | <span data-ttu-id="18b53-171">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="18b53-171">string</span></span>   | <span data-ttu-id="18b53-172">No</span><span class="sxs-lookup"><span data-stu-id="18b53-172">No</span></span> | <span data-ttu-id="18b53-173">Wanneer u een query uitvoert voor een lijst met producten voor Azure-reserveringen, geeft u op om een lijst met producten op te halen die van `reservationScope=AzurePlan` toepassing zijn op Azure-abonnementen.</span><span class="sxs-lookup"><span data-stu-id="18b53-173">When querying for a list of products for Azure Reservations, specify `reservationScope=AzurePlan` to get a list of products that are applicable to Azure plans.</span></span> <span data-ttu-id="18b53-174">Sluit deze parameter uit om een lijst met producten voor Azure-reserveringen op te halen die van toepassing zijn op Microsoft Azure **(MS-AZR-0145P)-abonnementen.**</span><span class="sxs-lookup"><span data-stu-id="18b53-174">Exclude this parameter to get a list of products for Azure reservations, which are applicable to Microsoft Azure (**MS-AZR-0145P**) subscriptions.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="18b53-175">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="18b53-175">Request headers</span></span>

<span data-ttu-id="18b53-176">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="18b53-176">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="18b53-177">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="18b53-177">Request body</span></span>

<span data-ttu-id="18b53-178">Geen.</span><span class="sxs-lookup"><span data-stu-id="18b53-178">None.</span></span>

### <a name="request-examples"></a><span data-ttu-id="18b53-179">Voorbeelden van aanvragen</span><span class="sxs-lookup"><span data-stu-id="18b53-179">Request examples</span></span>

#### <a name="products-by-country"></a><span data-ttu-id="18b53-180">Producten per land</span><span class="sxs-lookup"><span data-stu-id="18b53-180">Products by country</span></span>

<span data-ttu-id="18b53-181">Volg dit voorbeeld om een lijst met producten per land op te halen voor Microsoft Azure-abonnementen (MS-AZR-0145P) en Azure-abonnementen.</span><span class="sxs-lookup"><span data-stu-id="18b53-181">Follow this example to get a list of products by country for Microsoft Azure (MS-AZR-0145P) subscriptions and Azure plans.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=MicrosoftAzure HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-azure-plan"></a><span data-ttu-id="18b53-182">Azure VM-reserveringen (Azure-plan)</span><span class="sxs-lookup"><span data-stu-id="18b53-182">Azure VM reservations (Azure plan)</span></span>

<span data-ttu-id="18b53-183">Volg dit voorbeeld om een lijst met producten per land op te halen voor Azure VM-reserveringen die van toepassing zijn op Azure-plannen.</span><span class="sxs-lookup"><span data-stu-id="18b53-183">Follow this example to get a list of products by country for Azure VM reservations that are applicable to Azure plans.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureAzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="18b53-184">Azure VM-reserveringen voor Microsoft Azure -abonnementen (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="18b53-184">Azure VM reservations for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="18b53-185">Volg dit voorbeeld om een lijst met producten per land op te halen voor Azure VM-reserveringen die van toepassing zijn op Microsoft Azure-abonnementen (MS-AZR-0145P).</span><span class="sxs-lookup"><span data-stu-id="18b53-185">Follow this example to get a list of products by country for Azure VM reservations that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="18b53-186">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="18b53-186">REST response</span></span>

<span data-ttu-id="18b53-187">Als dit lukt, bevat de antwoord-body een verzameling [**productresources.**](product-resources.md#product)</span><span class="sxs-lookup"><span data-stu-id="18b53-187">If successful, the response body contains a collection of [**Product**](product-resources.md#product) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="18b53-188">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="18b53-188">Response success and error codes</span></span>

<span data-ttu-id="18b53-189">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="18b53-189">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="18b53-190">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="18b53-190">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="18b53-191">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="18b53-191">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="18b53-192">Deze methode retourneert de volgende foutcodes:</span><span class="sxs-lookup"><span data-stu-id="18b53-192">This method returns the following error codes:</span></span>

| <span data-ttu-id="18b53-193">HTTP-statuscode</span><span class="sxs-lookup"><span data-stu-id="18b53-193">HTTP Status Code</span></span>     | <span data-ttu-id="18b53-194">Foutcode</span><span class="sxs-lookup"><span data-stu-id="18b53-194">Error code</span></span>   | <span data-ttu-id="18b53-195">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="18b53-195">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="18b53-196">403</span><span class="sxs-lookup"><span data-stu-id="18b53-196">403</span></span>                  | <span data-ttu-id="18b53-197">400030</span><span class="sxs-lookup"><span data-stu-id="18b53-197">400030</span></span>       | <span data-ttu-id="18b53-198">Toegang tot het aangevraagde targetSegment is niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="18b53-198">Access to the requested targetSegment is not allowed.</span></span>                                                     |
| <span data-ttu-id="18b53-199">403</span><span class="sxs-lookup"><span data-stu-id="18b53-199">403</span></span>                  | <span data-ttu-id="18b53-200">400036</span><span class="sxs-lookup"><span data-stu-id="18b53-200">400036</span></span>       | <span data-ttu-id="18b53-201">Toegang tot de aangevraagde targetView is niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="18b53-201">Access to the requested targetView is not allowed.</span></span>                                                        |

### <a name="response-example"></a><span data-ttu-id="18b53-202">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="18b53-202">Response example</span></span>

```http
{
    "totalCount": 19,
    "items": [
        {
            "id": "DZH318Z0BQ3Q",
            "title": "Virtual Machines DSv2 Series",
            "description": "Dsv2-series instances are the latest generation of D-series instances that will carry more powerful CPUs which are on average about 35% faster than D-series instances, and carry the same memory and disk configurations as the D-series. Dsv2-series instances are based on the latest generation 2.4 GHz Intel Xeon® E5-2673 v3 (Haswell) processor, and with Intel Turbo Boost Technology 2.0 can go to 3.2 GHz.",
            "productType": {
                "id": "Azure",
                "displayName": "Azure",
                "subType": {
                "id": "VirtualMachines",
                "displayName": "VirtualMachines"
                }
            },
            "isMicrosoftProduct": true,
            "publisherName": "Microsoft",
            "links": {
                "skus": {
                    "uri": "/products/DZH318Z0BQ3Q/skus?country=US",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/products/DZH318Z0BQ3Q?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        },
        ...
    ],
    "links": {
        "self": {
            "uri": "/products?country=US&targetView=Azure",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
