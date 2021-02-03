---
title: Een lijst met producten ophalen (per land)
description: U kunt de product Resource gebruiken om een verzameling producten te verkrijgen op basis van het klant land.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: ea239aa008a5b7c33740e9c4697c3795908415cd
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767410"
---
# <a name="get-a-list-of-products-by-country"></a><span data-ttu-id="bba2b-103">Een lijst met producten ophalen (per land)</span><span class="sxs-lookup"><span data-stu-id="bba2b-103">Get a list of products (by country)</span></span>

<span data-ttu-id="bba2b-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="bba2b-104">**Applies to:**</span></span>

- <span data-ttu-id="bba2b-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="bba2b-105">Partner Center</span></span>
- <span data-ttu-id="bba2b-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="bba2b-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="bba2b-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="bba2b-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="bba2b-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="bba2b-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="bba2b-109">U kunt de volgende methoden gebruiken om een verzameling producten te verkrijgen die beschikbaar zijn in een bepaald land.</span><span class="sxs-lookup"><span data-stu-id="bba2b-109">You can use the following methods to get a collection of products available in a particular country.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bba2b-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="bba2b-110">Prerequisites</span></span>

- <span data-ttu-id="bba2b-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bba2b-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="bba2b-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="bba2b-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="bba2b-113">Een land.</span><span class="sxs-lookup"><span data-stu-id="bba2b-113">A country.</span></span>

## <a name="c"></a><span data-ttu-id="bba2b-114">C\#</span><span class="sxs-lookup"><span data-stu-id="bba2b-114">C\#</span></span>

<span data-ttu-id="bba2b-115">Een lijst met producten ophalen:</span><span class="sxs-lookup"><span data-stu-id="bba2b-115">To get a list of products:</span></span>

1. <span data-ttu-id="bba2b-116">Gebruik de verzameling **IAggregatePartner. Products** om het land te selecteren met behulp van de methode **ByCountry ()** .</span><span class="sxs-lookup"><span data-stu-id="bba2b-116">Use your **IAggregatePartner.Products** collection to select the country by using the **ByCountry()** method.</span></span>

2. <span data-ttu-id="bba2b-117">Selecteer de catalogus weergave met de methode **ByTargetView ()** .</span><span class="sxs-lookup"><span data-stu-id="bba2b-117">Select the catalog view using the **ByTargetView()** method.</span></span>

3. <span data-ttu-id="bba2b-118">Beschrijving Selecteer het reserverings bereik met de methode **ByReservationScope ()** .</span><span class="sxs-lookup"><span data-stu-id="bba2b-118">(Optional) Select the reservation scope using the **ByReservationScope()** method.</span></span>

4. <span data-ttu-id="bba2b-119">Beschrijving Selecteer het doel segment met de methode **ByTargetSegment ()** .</span><span class="sxs-lookup"><span data-stu-id="bba2b-119">(Optional) Select the target segment using the **ByTargetSegment()** method.</span></span>

5. <span data-ttu-id="bba2b-120">Roep de methode **Get ()** of **GetAsync ()** aan om de verzameling te retour neren.</span><span class="sxs-lookup"><span data-stu-id="bba2b-120">Call the **Get()** or **GetAsync()** method to return the collection.</span></span>

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

## <a name="java"></a><span data-ttu-id="bba2b-121">Java</span><span class="sxs-lookup"><span data-stu-id="bba2b-121">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="bba2b-122">Een lijst met producten ophalen:</span><span class="sxs-lookup"><span data-stu-id="bba2b-122">To get a list of products:</span></span>

1. <span data-ttu-id="bba2b-123">Gebruik de functie **IAggregatePartner. getProducts** om het land te selecteren met behulp van de functie **byCountry ()** .</span><span class="sxs-lookup"><span data-stu-id="bba2b-123">Use your **IAggregatePartner.getProducts** function to select the country by using the **byCountry()** function.</span></span>

2. <span data-ttu-id="bba2b-124">Selecteer de catalogus weergave met behulp van de functie **byTargetView ()** .</span><span class="sxs-lookup"><span data-stu-id="bba2b-124">Select the catalog view using the **byTargetView()** function.</span></span>
3. <span data-ttu-id="bba2b-125">Beschrijving Selecteer het doel segment met behulp van de functie **byTargetSegment ()** .</span><span class="sxs-lookup"><span data-stu-id="bba2b-125">(Optional) Select the target segment using the **byTargetSegment()** function.</span></span>

4. <span data-ttu-id="bba2b-126">Roep de functie **Get ()** aan om de verzameling te retour neren.</span><span class="sxs-lookup"><span data-stu-id="bba2b-126">Call the **get()** function to return the collection.</span></span>

```java
// IAggregatePartner partnerOperations;

// Get the products for the specified catalog view.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").get();

// Get the products filtered by target view and target segment.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").byTargetSegment("commercial").get();
```

## <a name="powershell"></a><span data-ttu-id="bba2b-127">PowerShell</span><span class="sxs-lookup"><span data-stu-id="bba2b-127">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="bba2b-128">Een lijst met producten ophalen:</span><span class="sxs-lookup"><span data-stu-id="bba2b-128">To get a list of products:</span></span>

1. <span data-ttu-id="bba2b-129">Voer de opdracht [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) uit.</span><span class="sxs-lookup"><span data-stu-id="bba2b-129">Execute the [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) command.</span></span>

2. <span data-ttu-id="bba2b-130">Selecteer de catalogus door de para meter **Catalog** op te geven.</span><span class="sxs-lookup"><span data-stu-id="bba2b-130">Select the catalog by specifying the **Catalog** parameter.</span></span>
3. <span data-ttu-id="bba2b-131">Beschrijving Selecteer het doel segment door de para meter **segment** op te geven.</span><span class="sxs-lookup"><span data-stu-id="bba2b-131">(Optional) Select the target segment by specifying the **Segment** parameter.</span></span>

```powershell
Get-PartnerProduct -Catalog 'Azure' -Segment 'commercial'
```

## <a name="rest-request"></a><span data-ttu-id="bba2b-132">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="bba2b-132">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="bba2b-133">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="bba2b-133">Request syntax</span></span>

| <span data-ttu-id="bba2b-134">Methode</span><span class="sxs-lookup"><span data-stu-id="bba2b-134">Method</span></span>  | <span data-ttu-id="bba2b-135">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="bba2b-135">Request URI</span></span>                                                                                                                                    |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="bba2b-136">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="bba2b-136">**GET**</span></span> | <span data-ttu-id="bba2b-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/Products? land = {country} &targetView = {targetView} &targetSegment = {TARGETSEGMENT} http/1.1</span><span class="sxs-lookup"><span data-stu-id="bba2b-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/products?country={country}&targetView={targetView}&targetSegment={targetSegment} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="bba2b-138">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="bba2b-138">URI parameters</span></span>

<span data-ttu-id="bba2b-139">Gebruik het volgende pad en de query parameters om een lijst met producten op te halen.</span><span class="sxs-lookup"><span data-stu-id="bba2b-139">Use the following path and query parameters to get a list of products.</span></span>

| <span data-ttu-id="bba2b-140">Naam</span><span class="sxs-lookup"><span data-stu-id="bba2b-140">Name</span></span>                   | <span data-ttu-id="bba2b-141">Type</span><span class="sxs-lookup"><span data-stu-id="bba2b-141">Type</span></span>     | <span data-ttu-id="bba2b-142">Vereist</span><span class="sxs-lookup"><span data-stu-id="bba2b-142">Required</span></span> | <span data-ttu-id="bba2b-143">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bba2b-143">Description</span></span>                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| <span data-ttu-id="bba2b-144">country</span><span class="sxs-lookup"><span data-stu-id="bba2b-144">country</span></span>                | <span data-ttu-id="bba2b-145">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="bba2b-145">string</span></span>   | <span data-ttu-id="bba2b-146">Yes</span><span class="sxs-lookup"><span data-stu-id="bba2b-146">Yes</span></span>      | <span data-ttu-id="bba2b-147">De ID van het land/de regio.</span><span class="sxs-lookup"><span data-stu-id="bba2b-147">The country/region ID.</span></span>                                                  |
| <span data-ttu-id="bba2b-148">targetView</span><span class="sxs-lookup"><span data-stu-id="bba2b-148">targetView</span></span>             | <span data-ttu-id="bba2b-149">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="bba2b-149">string</span></span>   | <span data-ttu-id="bba2b-150">Yes</span><span class="sxs-lookup"><span data-stu-id="bba2b-150">Yes</span></span>      | <span data-ttu-id="bba2b-151">Hiermee wordt de doel weergave van de catalogus geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="bba2b-151">Identifies the target view of the catalog.</span></span> <span data-ttu-id="bba2b-152">De ondersteunde waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="bba2b-152">The supported values are:</span></span> <br/><br/><span data-ttu-id="bba2b-153">**Azure**, inclusief alle Azure-items</span><span class="sxs-lookup"><span data-stu-id="bba2b-153">**Azure**, which includes all Azure items</span></span><br/><br/><span data-ttu-id="bba2b-154">**AzureReservations**, inclusief alle Azure-reserverings items</span><span class="sxs-lookup"><span data-stu-id="bba2b-154">**AzureReservations**, which includes all Azure reservation items</span></span><br/><br/><span data-ttu-id="bba2b-155">**AzureReservationsVM**, dat alle reserve ringen items van virtuele machines (VM) omvat</span><span class="sxs-lookup"><span data-stu-id="bba2b-155">**AzureReservationsVM**, which includes all virtual machine (VM) reservation items</span></span><br/><br/><span data-ttu-id="bba2b-156">**AzureReservationsSQL**, inclusief alle SQL-reserverings items</span><span class="sxs-lookup"><span data-stu-id="bba2b-156">**AzureReservationsSQL**, which includes all SQL reservation items</span></span><br/><br/><span data-ttu-id="bba2b-157">**AzureReservationsCosmosDb**, met alle reserverings items voor de Cosmos-data base</span><span class="sxs-lookup"><span data-stu-id="bba2b-157">**AzureReservationsCosmosDb**, which includes all Cosmos database reservation items</span></span><br/><br/><span data-ttu-id="bba2b-158">**MicrosoftAzure**, die items bevat voor Microsoft Azure-abonnementen (**MS-AZR-0145P**) en Azure-plannen</span><span class="sxs-lookup"><span data-stu-id="bba2b-158">**MicrosoftAzure**, which includes items for Microsoft Azure subscriptions (**MS-AZR-0145P**) and Azure plans</span></span><br/><br/><span data-ttu-id="bba2b-159">**OnlineServices**, dat alle online service-items omvat (inclusief commerciële Marketplace-Producten)</span><span class="sxs-lookup"><span data-stu-id="bba2b-159">**OnlineServices**, which includes all online service items (including commercial marketplace products)</span></span><br/><br/><span data-ttu-id="bba2b-160">**Software**, inclusief alle software-items</span><span class="sxs-lookup"><span data-stu-id="bba2b-160">**Software**, which includes all software items</span></span><br/><br/><span data-ttu-id="bba2b-161">**SoftwareSUSELinux**, dat alle software SuSE Linux-items omvat</span><span class="sxs-lookup"><span data-stu-id="bba2b-161">**SoftwareSUSELinux**, which includes all software SUSE Linux items</span></span><br/><br/><span data-ttu-id="bba2b-162">**SoftwarePerpetual**, inclusief alle permanente software-items</span><span class="sxs-lookup"><span data-stu-id="bba2b-162">**SoftwarePerpetual**, which includes all perpetual software items</span></span><br/><br/><span data-ttu-id="bba2b-163">**SoftwareSubscriptions**, inclusief alle software-abonnements items</span><span class="sxs-lookup"><span data-stu-id="bba2b-163">**SoftwareSubscriptions**, which includes all software subscription items</span></span>    |
| <span data-ttu-id="bba2b-164">targetSegment</span><span class="sxs-lookup"><span data-stu-id="bba2b-164">targetSegment</span></span>          | <span data-ttu-id="bba2b-165">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="bba2b-165">string</span></span>   | <span data-ttu-id="bba2b-166">No</span><span class="sxs-lookup"><span data-stu-id="bba2b-166">No</span></span>       | <span data-ttu-id="bba2b-167">Hiermee wordt het doel segment aangeduid.</span><span class="sxs-lookup"><span data-stu-id="bba2b-167">Identifies the target segment.</span></span> <span data-ttu-id="bba2b-168">De weer gave voor verschillende doel groepen.</span><span class="sxs-lookup"><span data-stu-id="bba2b-168">The view for different target audiences.</span></span> <span data-ttu-id="bba2b-169">De ondersteunde waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="bba2b-169">The supported values are:</span></span> <br/><br/><span data-ttu-id="bba2b-170">**politieke**</span><span class="sxs-lookup"><span data-stu-id="bba2b-170">**commercial**</span></span><br/><span data-ttu-id="bba2b-171">**personeel**</span><span class="sxs-lookup"><span data-stu-id="bba2b-171">**education**</span></span><br/><span data-ttu-id="bba2b-172">**Government**</span><span class="sxs-lookup"><span data-stu-id="bba2b-172">**government**</span></span><br/><span data-ttu-id="bba2b-173">**profit**</span><span class="sxs-lookup"><span data-stu-id="bba2b-173">**nonprofit**</span></span>  |
| <span data-ttu-id="bba2b-174">reservationScope</span><span class="sxs-lookup"><span data-stu-id="bba2b-174">reservationScope</span></span> | <span data-ttu-id="bba2b-175">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="bba2b-175">string</span></span>   | <span data-ttu-id="bba2b-176">No</span><span class="sxs-lookup"><span data-stu-id="bba2b-176">No</span></span> | <span data-ttu-id="bba2b-177">Wanneer u een query uitvoert voor een lijst met producten voor Azure Reservations, geeft `reservationScope=AzurePlan` u een lijst op met producten die van toepassing zijn op Azure-abonnementen.</span><span class="sxs-lookup"><span data-stu-id="bba2b-177">When querying for a list of products for Azure Reservations, specify `reservationScope=AzurePlan` to get a list of products that are applicable to Azure plans.</span></span> <span data-ttu-id="bba2b-178">Sluit deze para meter uit om een lijst met producten voor Azure-reserve ringen op te halen die van toepassing zijn op Microsoft Azure-abonnementen (**MS-AZR-0145P**).</span><span class="sxs-lookup"><span data-stu-id="bba2b-178">Exclude this parameter to get a list of products for Azure reservations, which are applicable to Microsoft Azure (**MS-AZR-0145P**) subscriptions.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="bba2b-179">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="bba2b-179">Request headers</span></span>

<span data-ttu-id="bba2b-180">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="bba2b-180">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="bba2b-181">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="bba2b-181">Request body</span></span>

<span data-ttu-id="bba2b-182">Geen.</span><span class="sxs-lookup"><span data-stu-id="bba2b-182">None.</span></span>

### <a name="request-examples"></a><span data-ttu-id="bba2b-183">Aanvraag voorbeelden</span><span class="sxs-lookup"><span data-stu-id="bba2b-183">Request examples</span></span>

#### <a name="products-by-country"></a><span data-ttu-id="bba2b-184">Producten op land</span><span class="sxs-lookup"><span data-stu-id="bba2b-184">Products by country</span></span>

<span data-ttu-id="bba2b-185">Volg dit voor beeld om een lijst met producten te verkrijgen per land voor Microsoft Azure (MS-AZR-0145P) en Azure-abonnementen.</span><span class="sxs-lookup"><span data-stu-id="bba2b-185">Follow this example to get a list of products by country for Microsoft Azure (MS-AZR-0145P) subscriptions and Azure plans.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=MicrosoftAzure HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-azure-plan"></a><span data-ttu-id="bba2b-186">Azure VM-reserve ringen (Azure-abonnement)</span><span class="sxs-lookup"><span data-stu-id="bba2b-186">Azure VM reservations (Azure plan)</span></span>

<span data-ttu-id="bba2b-187">Volg dit voor beeld om een lijst met producten te verkrijgen per land voor Azure VM-reserve ringen die van toepassing zijn op Azure-abonnementen.</span><span class="sxs-lookup"><span data-stu-id="bba2b-187">Follow this example to get a list of products by country for Azure VM reservations that are applicable to Azure plans.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureAzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="bba2b-188">Azure VM-reserve ringen voor Microsoft Azure-abonnementen (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="bba2b-188">Azure VM reservations for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="bba2b-189">Volg dit voor beeld om een lijst met producten te verkrijgen per land voor Azure VM-reserve ringen die van toepassing zijn op Microsoft Azure-abonnementen (MS-AZR-0145P).</span><span class="sxs-lookup"><span data-stu-id="bba2b-189">Follow this example to get a list of products by country for Azure VM reservations that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="bba2b-190">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="bba2b-190">REST response</span></span>

<span data-ttu-id="bba2b-191">Als dit lukt, bevat de antwoord tekst een verzameling [**product**](product-resources.md#product) resources.</span><span class="sxs-lookup"><span data-stu-id="bba2b-191">If successful, the response body contains a collection of [**Product**](product-resources.md#product) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="bba2b-192">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="bba2b-192">Response success and error codes</span></span>

<span data-ttu-id="bba2b-193">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="bba2b-193">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="bba2b-194">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="bba2b-194">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="bba2b-195">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="bba2b-195">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="bba2b-196">Deze methode retourneert de volgende fout codes:</span><span class="sxs-lookup"><span data-stu-id="bba2b-196">This method returns the following error codes:</span></span>

| <span data-ttu-id="bba2b-197">HTTP-status code</span><span class="sxs-lookup"><span data-stu-id="bba2b-197">HTTP Status Code</span></span>     | <span data-ttu-id="bba2b-198">Foutcode</span><span class="sxs-lookup"><span data-stu-id="bba2b-198">Error code</span></span>   | <span data-ttu-id="bba2b-199">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bba2b-199">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="bba2b-200">403</span><span class="sxs-lookup"><span data-stu-id="bba2b-200">403</span></span>                  | <span data-ttu-id="bba2b-201">400030</span><span class="sxs-lookup"><span data-stu-id="bba2b-201">400030</span></span>       | <span data-ttu-id="bba2b-202">Toegang tot de aangevraagde targetSegment is niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="bba2b-202">Access to the requested targetSegment is not allowed.</span></span>                                                     |
| <span data-ttu-id="bba2b-203">403</span><span class="sxs-lookup"><span data-stu-id="bba2b-203">403</span></span>                  | <span data-ttu-id="bba2b-204">400036</span><span class="sxs-lookup"><span data-stu-id="bba2b-204">400036</span></span>       | <span data-ttu-id="bba2b-205">Toegang tot de aangevraagde targetView is niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="bba2b-205">Access to the requested targetView is not allowed.</span></span>                                                        |

### <a name="response-example"></a><span data-ttu-id="bba2b-206">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="bba2b-206">Response example</span></span>

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
