---
title: Gebruiksrecords van een klant ophalen voor Azure
description: U kunt de Azure-gebruiks API gebruiken om de gebruiks gegevens van het Azure-abonnement van een klant te verkrijgen voor een opgegeven periode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: bcdeb51b04039fd05b923150c85119385c0537e0
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767375"
---
# <a name="get-a-customers-utilization-records-for-azure"></a><span data-ttu-id="f6fa9-103">Gebruiksrecords van een klant ophalen voor Azure</span><span class="sxs-lookup"><span data-stu-id="f6fa9-103">Get a customer's utilization records for Azure</span></span>

<span data-ttu-id="f6fa9-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="f6fa9-104">**Applies to:**</span></span>

- <span data-ttu-id="f6fa9-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="f6fa9-105">Partner Center</span></span>
- <span data-ttu-id="f6fa9-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="f6fa9-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="f6fa9-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="f6fa9-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="f6fa9-108">U kunt de gebruiks gegevens van het Azure-abonnement van een klant voor een opgegeven periode ophalen met behulp van de Azure-gebruiks-API.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-108">You can get the utilization records of a customer's Azure subscription for a specified time period using the Azure utilization API.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f6fa9-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f6fa9-109">Prerequisites</span></span>

- <span data-ttu-id="f6fa9-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f6fa9-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f6fa9-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-111">This scenario supports authentication with both standalone app and App+User credentials.</span></span>

- <span data-ttu-id="f6fa9-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f6fa9-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f6fa9-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f6fa9-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f6fa9-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f6fa9-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="f6fa9-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f6fa9-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f6fa9-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="f6fa9-118">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-118">A subscription identifier.</span></span>

<span data-ttu-id="f6fa9-119">Deze API retourneert dagelijks en niet-geclassificeerd verbruik voor een wille keurige tijds Panne.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-119">This API returns daily and hourly unrated consumption for an arbitrary time span.</span></span> <span data-ttu-id="f6fa9-120">*Deze API wordt echter niet ondersteund voor Azure-abonnementen*.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-120">However, *this API isn't supported for Azure plans*.</span></span> <span data-ttu-id="f6fa9-121">Als u een Azure-abonnement hebt, raadpleegt u de artikelen niet- [gefactureerde verbruiks regel items factureren](get-invoice-unbilled-consumption-lineitems.md) en [factuur verbruik regel items factureren ophalen](get-invoice-billed-consumption-lineitems.md) .</span><span class="sxs-lookup"><span data-stu-id="f6fa9-121">If you have an Azure plan, see the articles [Get invoice unbilled consumption line items](get-invoice-unbilled-consumption-lineitems.md) and [Get invoice billed consumption line items](get-invoice-billed-consumption-lineitems.md) instead.</span></span> <span data-ttu-id="f6fa9-122">In deze artikelen wordt beschreven hoe u het geclassificeerde verbruik op dagelijks niveau per resource kunt ophalen.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-122">These articles describe how to get rated consumption at a daily level per meter per resource.</span></span> <span data-ttu-id="f6fa9-123">Dit aantal is gelijk aan de gegevens van de dagelijks korrel die worden geleverd door de Azure-gebruiks-API.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-123">This rate consumption is equivalent to the daily grain data provided by the Azure utilization API.</span></span> <span data-ttu-id="f6fa9-124">U moet de factuur-ID gebruiken om gefactureerde gebruiks gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-124">You'll need to use the invoice identifier to retrieve billed usage data.</span></span> <span data-ttu-id="f6fa9-125">U kunt ook huidige en vorige Peri Oden gebruiken om niet-gefactureerde gebruik te schatten.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-125">Or, you can use current and previous periods to get unbilled usage estimates.</span></span> <span data-ttu-id="f6fa9-126">*Gevarieerde gegevens en filters voor een wille keurig datum bereik worden momenteel niet ondersteund voor Azure plan-abonnements resources*.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-126">*Hourly grain data and arbitrary date range filters aren't currently supported for Azure plan subscription resources*.</span></span>

## <a name="azure-utilization-api"></a><span data-ttu-id="f6fa9-127">Azure-gebruiks-API</span><span class="sxs-lookup"><span data-stu-id="f6fa9-127">Azure utilization API</span></span>

<span data-ttu-id="f6fa9-128">Deze Azure-gebruiks-API biedt toegang tot gebruiks records voor een tijds periode die aangeeft wanneer het gebruik is gerapporteerd in het facturerings systeem.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-128">This Azure utilization API provides access to utilization records for a time period that represents when the utilization was reported in the billing system.</span></span> <span data-ttu-id="f6fa9-129">Het biedt toegang tot dezelfde gebruiks gegevens die worden gebruikt voor het maken en berekenen van het afstemmings bestand.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-129">It provides access to the same utilization data that is used to create and calculate the reconciliation file.</span></span> <span data-ttu-id="f6fa9-130">Het heeft echter geen kennis van de logica voor het afstemmen van het facturerings systeem.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-130">However, it does not have knowledge of billing system reconciliation file logic.</span></span> <span data-ttu-id="f6fa9-131">U mag geen samen vatting van de resultaten van een afstemmings bestand verwachten dat overeenkomt met het resultaat dat is opgehaald uit deze API precies voor dezelfde periode.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-131">You should not expect reconciliation file summary results to match the result retrieved from this API exactly for the same time period.</span></span>

<span data-ttu-id="f6fa9-132">Het facturerings systeem neemt bijvoorbeeld dezelfde gebruiks gegevens op en past de regels voor de achterstand toe om te bepalen wat er in een afstemmings bestand is verwerkt.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-132">For example, the billing system takes the same utilization data and applies lateness rules to determine what is accounted for in a reconciliation file.</span></span> <span data-ttu-id="f6fa9-133">Wanneer een facturerings periode wordt gesloten, wordt alle gebruik tot het eind van de dag waarop de facturerings periode eindigt, opgenomen in het afstemmings bestand.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-133">When a billing period closes, all usage until the end of the day that the billing period ends is included in the reconciliation file.</span></span> <span data-ttu-id="f6fa9-134">Een vertraagd gebruik binnen de facturerings periode die binnen 24 uur na het einde van de facturerings periode wordt gerapporteerd, wordt in het volgende afstemmings bestand verwerkt.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-134">Any late usage within the billing period that is reported within 24 hours after the billing period ends is accounted for in the next reconciliation file.</span></span> <span data-ttu-id="f6fa9-135">Zie [verbruiks gegevens ophalen voor een Azure-abonnement](/previous-versions/azure/reference/mt219001(v=azure.100))voor de regels voor de achterstand van hoe de partner wordt gefactureerd.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-135">For the lateness rules of how the partner is billed, see [Get consumption data for an Azure subscription](/previous-versions/azure/reference/mt219001(v=azure.100)).</span></span>

<span data-ttu-id="f6fa9-136">Deze REST API is gewisseld.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-136">This REST API is paged.</span></span> <span data-ttu-id="f6fa9-137">Als de reactie lading groter is dan één pagina, moet u de volgende koppeling volgen om de volgende pagina met gebruiks gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-137">If the response payload is larger than a single page, you must follow the next link to get the next page of utilization records.</span></span>

## <a name="c"></a><span data-ttu-id="f6fa9-138">C\#</span><span class="sxs-lookup"><span data-stu-id="f6fa9-138">C\#</span></span>

<span data-ttu-id="f6fa9-139">Voor het verkrijgen van de Azure-gebruiks records:</span><span class="sxs-lookup"><span data-stu-id="f6fa9-139">To obtain the Azure Utilization Records:</span></span>

1. <span data-ttu-id="f6fa9-140">Haal de klant-ID en de abonnements-ID op.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-140">Get the customer ID and subscription ID.</span></span>

2. <span data-ttu-id="f6fa9-141">Roep de methode [**IAzureUtilizationCollection. query**](/dotnet/api/microsoft.store.partnercenter.utilization.iazureutilizationcollection.query) aan om een [**ResourceCollection**](/dotnet/api/microsoft.store.partnercenter.models.resourcecollection-1) te retour neren die de gebruiks records bevat.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-141">Call the [**IAzureUtilizationCollection.Query**](/dotnet/api/microsoft.store.partnercenter.utilization.iazureutilizationcollection.query) method to return a [**ResourceCollection**](/dotnet/api/microsoft.store.partnercenter.models.resourcecollection-1) that contains the utilization records.</span></span>

3. <span data-ttu-id="f6fa9-142">Verkrijg een inventaris van het Azure-gebruik record om de gebruiks pagina's te passeren.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-142">Obtain an Azure utilization record enumerator to traverse the utilization pages.</span></span> <span data-ttu-id="f6fa9-143">Deze stap is vereist omdat de resource verzameling is gewisseld.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-143">This step is required, because the resource collection is paged.</span></span>

- <span data-ttu-id="f6fa9-144">Voor **beeld**: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="f6fa9-144">**Sample**: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="f6fa9-145">**Project**: Partner Center SDK-voor beelden</span><span class="sxs-lookup"><span data-stu-id="f6fa9-145">**Project**: Partner Center SDK Samples</span></span>
- <span data-ttu-id="f6fa9-146">**Klasse**: GetAzureSubscriptionUtilization.cs</span><span class="sxs-lookup"><span data-stu-id="f6fa9-146">**Class**: GetAzureSubscriptionUtilization.cs</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

IPartner partner = PartnerService.Instance.CreatePartnerOperations(credentials);

// Retrieve the utilization records for the last year in pages of 100 records.
var utilizationRecords = partner.Customers[customerId].Subscriptions[subscriptionId].Utilization.Azure.Query(
    DateTimeOffset.Now.AddYears(-1),
    DateTimeOffset.Now,
    size: 100);

// Create an Azure utilization enumerator which will aid us in traversing the utilization pages.
var utilizationRecordEnumerator = partner.Enumerators.Utilization.Azure.Create(utilizationRecords);

while (utilizationRecordEnumerator.HasValue)
{
    //
    // Insert code here to work with this page.
    //

    // Get the next page.
    utilizationRecordEnumerator.Next();
}
```

## <a name="java"></a><span data-ttu-id="f6fa9-147">Java</span><span class="sxs-lookup"><span data-stu-id="f6fa9-147">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="f6fa9-148">Als u Azure-gebruiks records wilt verkrijgen, hebt u eerst een klant-id en een abonnements-id nodig.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-148">To obtain the Azure Utilization Records, you first need a customer identifier and a subscription identifier.</span></span> <span data-ttu-id="f6fa9-149">Vervolgens roept u de functie **IAzureUtilizationCollection. query** aan om een **ResourceCollection** te retour neren die de gebruiks records bevat.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-149">You then call the **IAzureUtilizationCollection.query** function to return a **ResourceCollection** that contains the utilization records.</span></span> <span data-ttu-id="f6fa9-150">Omdat de resource verzameling is gewisseld, moet u een inventaris van het Azure-gebruik record verkrijgen om de gebruiks pagina's te passeren.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-150">Because the resource collection is paged, you must then obtain an Azure utilization record enumerator to traverse the utilization pages.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String subscriptionId;

ResourceCollection<AzureUtilizationRecord> utilizationRecords = partnerOperations.getCustomers()
  .byId(customerId).getSubscriptions().byId(subscriptionId)
  .getUtilization().getAzure().query(
      new DateTime().minusYears(1),
      new DateTime(),
      AzureUtilizationGranularity.Daily,
      true,
      100);

// Create an Azure utilization enumerator which will aid us in traversing the utilization pages
IResourceCollectionEnumerator<ResourceCollection<AzureUtilizationRecord>> utilizationRecordEnumerator =
    partnerOperations.getEnumerators().getUtilization().getAzure().create(utilizationRecords);

while (utilizationRecordEnumerator.hasValue())
{
    //
    // Insert code here to work with this page.
    //

    // get the next page
    utilizationRecordEnumerator.next();
}
```

## <a name="powershell"></a><span data-ttu-id="f6fa9-151">PowerShell</span><span class="sxs-lookup"><span data-stu-id="f6fa9-151">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="f6fa9-152">Als u Azure-gebruiks records wilt verkrijgen, hebt u eerst een klant-id en een abonnements-id nodig.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-152">To obtain the Azure Utilization Records, you first need a customer identifier and a subscription identifier.</span></span> <span data-ttu-id="f6fa9-153">Vervolgens roept u de [**Get-PartnerCustomerSubscriptionUtilization aan**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscriptionUtilization.md).</span><span class="sxs-lookup"><span data-stu-id="f6fa9-153">You then call the [**Get-PartnerCustomerSubscriptionUtilization**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscriptionUtilization.md).</span></span> <span data-ttu-id="f6fa9-154">Met deze opdracht worden alle records geretourneerd die beschikbaar zijn voor de opgegeven periode.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-154">This command will return all records available for the specified period of time.</span></span>

```powershell
# $customerId
# $subscriptionId

Get-PartnerCustomerSubscriptionUtilization -CustomerId $customerId -SubscriptionId $subscriptionId -StartDate (Get-Date).AddDays(-2).ToUniversalTime() -Granularity Hourly -ShowDetails
```

## <a name="rest-request"></a><span data-ttu-id="f6fa9-155">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="f6fa9-155">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f6fa9-156">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="f6fa9-156">Request syntax</span></span>

| <span data-ttu-id="f6fa9-157">Methode</span><span class="sxs-lookup"><span data-stu-id="f6fa9-157">Method</span></span> | <span data-ttu-id="f6fa9-158">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="f6fa9-158">Request URI</span></span> |
|------- | ----------- |
| <span data-ttu-id="f6fa9-159">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="f6fa9-159">**GET**</span></span> | <span data-ttu-id="f6fa9-160">*{baseURL}*/v1/Customers/{Customer-Tenant-id}/Subscriptions/{Subscription-id}/utilizations/Azure? begin \_ tijd = {start-time} &eind \_ tijd = {end-time} &granulatie = {granulatie} &details weer geven \_ = {True}</span><span class="sxs-lookup"><span data-stu-id="f6fa9-160">*{baseURL}*/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/utilizations/azure?start\_time={start-time}&end\_time={end-time}&granularity={granularity}&show\_details={True}</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="f6fa9-161">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="f6fa9-161">URI parameters</span></span>

<span data-ttu-id="f6fa9-162">Gebruik de volgende pad-en query parameters om de gebruiks gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-162">Use the following path and query parameters to get the utilization records.</span></span>

| <span data-ttu-id="f6fa9-163">Naam</span><span class="sxs-lookup"><span data-stu-id="f6fa9-163">Name</span></span> | <span data-ttu-id="f6fa9-164">Type</span><span class="sxs-lookup"><span data-stu-id="f6fa9-164">Type</span></span> | <span data-ttu-id="f6fa9-165">Vereist</span><span class="sxs-lookup"><span data-stu-id="f6fa9-165">Required</span></span> | <span data-ttu-id="f6fa9-166">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f6fa9-166">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="f6fa9-167">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="f6fa9-167">customer-tenant-id</span></span> | <span data-ttu-id="f6fa9-168">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="f6fa9-168">string</span></span> | <span data-ttu-id="f6fa9-169">Yes</span><span class="sxs-lookup"><span data-stu-id="f6fa9-169">Yes</span></span> | <span data-ttu-id="f6fa9-170">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-170">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="f6fa9-171">abonnement-id</span><span class="sxs-lookup"><span data-stu-id="f6fa9-171">subscription-id</span></span> | <span data-ttu-id="f6fa9-172">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="f6fa9-172">string</span></span> | <span data-ttu-id="f6fa9-173">Yes</span><span class="sxs-lookup"><span data-stu-id="f6fa9-173">Yes</span></span> | <span data-ttu-id="f6fa9-174">Een teken reeks met een GUID-indeling waarmee het abonnement wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-174">A GUID-formatted string that identifies the subscription.</span></span> |
| <span data-ttu-id="f6fa9-175">start_tijd</span><span class="sxs-lookup"><span data-stu-id="f6fa9-175">start_time</span></span> | <span data-ttu-id="f6fa9-176">teken reeks in UTC-notatie voor datum/tijd-offset</span><span class="sxs-lookup"><span data-stu-id="f6fa9-176">string in UTC date-time offset format</span></span> | <span data-ttu-id="f6fa9-177">Yes</span><span class="sxs-lookup"><span data-stu-id="f6fa9-177">Yes</span></span> | <span data-ttu-id="f6fa9-178">Het begin van het tijds bereik dat aangeeft wanneer het gebruik is gerapporteerd in het facturerings systeem.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-178">The start of the time range that represents when the utilization was reported in the billing system.</span></span> |
| <span data-ttu-id="f6fa9-179">end_time</span><span class="sxs-lookup"><span data-stu-id="f6fa9-179">end_time</span></span> | <span data-ttu-id="f6fa9-180">teken reeks in UTC-notatie voor datum/tijd-offset</span><span class="sxs-lookup"><span data-stu-id="f6fa9-180">string in UTC date-time offset format</span></span> | <span data-ttu-id="f6fa9-181">Yes</span><span class="sxs-lookup"><span data-stu-id="f6fa9-181">Yes</span></span> | <span data-ttu-id="f6fa9-182">Het einde van het tijds bereik dat aangeeft wanneer het gebruik is gerapporteerd in het facturerings systeem.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-182">The end of the time range that represents when the utilization was reported in the billing system.</span></span> |
| <span data-ttu-id="f6fa9-183">granulatie</span><span class="sxs-lookup"><span data-stu-id="f6fa9-183">granularity</span></span> | <span data-ttu-id="f6fa9-184">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="f6fa9-184">string</span></span> | <span data-ttu-id="f6fa9-185">No</span><span class="sxs-lookup"><span data-stu-id="f6fa9-185">No</span></span> | <span data-ttu-id="f6fa9-186">Hiermee definieert u de granulatie van gebruiks aggregaties.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-186">Defines the granularity of usage aggregations.</span></span> <span data-ttu-id="f6fa9-187">Beschik bare opties zijn: `daily` (standaard) en `hourly` .</span><span class="sxs-lookup"><span data-stu-id="f6fa9-187">Available options are: `daily` (default) and `hourly`.</span></span>
| <span data-ttu-id="f6fa9-188">show_details</span><span class="sxs-lookup"><span data-stu-id="f6fa9-188">show_details</span></span> | <span data-ttu-id="f6fa9-189">booleaans</span><span class="sxs-lookup"><span data-stu-id="f6fa9-189">boolean</span></span> | <span data-ttu-id="f6fa9-190">No</span><span class="sxs-lookup"><span data-stu-id="f6fa9-190">No</span></span> | <span data-ttu-id="f6fa9-191">Hiermee wordt aangegeven of de details van het gebruik op exemplaar niveau moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-191">Specifies whether to get the instance-level usage details.</span></span> <span data-ttu-id="f6fa9-192">De standaardwaarde is `true`.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-192">The default is `true`.</span></span> |
| <span data-ttu-id="f6fa9-193">grootte</span><span class="sxs-lookup"><span data-stu-id="f6fa9-193">size</span></span> | <span data-ttu-id="f6fa9-194">getal</span><span class="sxs-lookup"><span data-stu-id="f6fa9-194">number</span></span> | <span data-ttu-id="f6fa9-195">No</span><span class="sxs-lookup"><span data-stu-id="f6fa9-195">No</span></span> | <span data-ttu-id="f6fa9-196">Hiermee geeft u het aantal aggregaties op dat door één API-aanroep wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-196">Specifies the number of aggregations returned by a single API call.</span></span> <span data-ttu-id="f6fa9-197">De standaardwaarde is 1000.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-197">The default is 1000.</span></span> <span data-ttu-id="f6fa9-198">De maximum waarde is 1000.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-198">The max is 1000.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="f6fa9-199">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="f6fa9-199">Request headers</span></span>

<span data-ttu-id="f6fa9-200">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="f6fa9-200">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f6fa9-201">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="f6fa9-201">Request body</span></span>

<span data-ttu-id="f6fa9-202">Geen</span><span class="sxs-lookup"><span data-stu-id="f6fa9-202">None</span></span>

### <a name="request-example"></a><span data-ttu-id="f6fa9-203">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="f6fa9-203">Request example</span></span>

<span data-ttu-id="f6fa9-204">De volgende voorbeeld aanvraag produceert resultaten die vergelijkbaar zijn met wat het afstemmings bestand zal weer geven voor de periode van 7/2-8/1.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-204">The following example request produces results similar to what the reconciliation file will show for the period 7/2 - 8/1.</span></span> <span data-ttu-id="f6fa9-205">Deze resultaten komen mogelijk niet exact overeen (Zie de sectie [Azure-gebruiks-API](#azure-utilization-api) voor meer informatie).</span><span class="sxs-lookup"><span data-stu-id="f6fa9-205">These results may not match exactly (see the section [Azure utilization API](#azure-utilization-api) for details).</span></span>

<span data-ttu-id="f6fa9-206">In dit voor beeld wordt een aanvraag voor het retour neren van gebruiks gegevens gerapporteerd in het facturerings systeem tussen 7/2 bij 12 uur (UTC) en 8/2 om 12 uur (UTC).</span><span class="sxs-lookup"><span data-stu-id="f6fa9-206">This example request returns utilization data reported in the billing system between 7/2 at 12 AM (UTC) and 8/2 at 12 AM (UTC).</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/E499C962-9218-4DBA-8B83-8ADC94F47B9F/subscriptions/FC8F8908-F918-4406-AF13-D5BC0FE41865/utilizations/azure?start_time=2017-07-02T00:00:00-08:00&end_time=2017-08-02T00:00:00-08:00 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="f6fa9-207">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="f6fa9-207">REST response</span></span>

<span data-ttu-id="f6fa9-208">Als dit lukt, retourneert deze methode een verzameling van [Azure-gebruik record](azure-utilization-record-resources.md) bronnen in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-208">If successful, this method returns a collection of [Azure Utilization Record](azure-utilization-record-resources.md) resources in the response body.</span></span> <span data-ttu-id="f6fa9-209">Als de Azure-gebruiks gegevens nog niet gereed zijn in een afhankelijk systeem, retourneert deze methode een HTTP-status code 204 met een Retry-After-header.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-209">If the Azure utilization data isn't yet ready in a dependent system, this method returns an HTTP Status Code 204 with a Retry-After header.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f6fa9-210">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="f6fa9-210">Response success and error codes</span></span>

<span data-ttu-id="f6fa9-211">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-211">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f6fa9-212">Gebruik een hulp programma voor netwerk tracering om de HTTP-status code, het [fout code type](error-codes.md)en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="f6fa9-212">Use a network trace tool to read the HTTP status code, [error code type](error-codes.md), and additional parameters.</span></span>

### <a name="response-example"></a><span data-ttu-id="f6fa9-213">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="f6fa9-213">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2630
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CV: PjuGoYrw806o6A3Y.0
MS-ServerId: 030020525
Date: Fri, 04 Aug 2017 23:48:28 GMT

{
  "totalCount": 2,
  "items": [
    {
      "usageStartTime": "2017-06-07T17:00:00-07:00",
      "usageEndTime": "2017-06-08T17:00:00-07:00",
      "resource": {
        "id": "8767aeb3-6909-4db2-9927-3f51e9a9085e",
        "name": "Storage Admin",
        "category": "Storage",
        "subcategory": "Block Blob",
        "region": "Azure Stack"
      },
      "quantity": 0.217790327034891,
      "unit": "1 GB/Hr",
      "infoFields": {},
      "instanceData": {
        "resourceUri": "/subscriptions/ab7e2384-eeee-489a-a14f-1eb41ddd261d/resourcegroups/system.local/providers/Microsoft.Storage/storageaccounts/srphealthaccount",
        "location": "azurestack",
        "partNumber": "",
        "orderNumber": "",
        "additionalInfo": {
          "azureStack.MeterId": "09F8879E-87E9-4305-A572-4B7BE209F857",
          "azureStack.SubscriptionId": "dbd1aa30-e40d-4436-b465-3a8bc11df027",
          "azureStack.Location": "local",
          "azureStack.EventDateTime": "06/05/2017 06:00:00"
        }
      },
      "attributes": {
        "objectType": "AzureUtilizationRecord"
      }
    },
    {
      "usageStartTime": "2017-06-07T17:00:00-07:00",
      "usageEndTime": "2017-06-08T17:00:00-07:00",
      "resource": {
        "id": "8767aeb3-6909-4db2-9927-3f51e9a9085e",
        "name": "Storage Admin",
        "category": "Storage",
        "subcategory": "Block Blob",
        "region": "Azure Stack"
      },
      "quantity": 0.217790327034891,
      "unit": "1 GB/Hr",
      "infoFields": {},
      "instanceData": {
        "resourceUri": "/subscriptions/ab7e2384-eeee-489a-a14f-1eb41ddd261d/resourcegroups/system.local/providers/Microsoft.Storage/storageaccounts/srphealthaccount",
        "location": "azurestack",
        "partNumber": "",
        "orderNumber": "",
        "additionalInfo": {
          "azureStack.MeterId": "09F8879E-87E9-4305-A572-4B7BE209F857",
          "azureStack.SubscriptionId": "dbd1aa30-e40d-4436-b465-3a8bc11df027",
          "azureStack.Location": "local",
          "azureStack.EventDateTime": "06/05/2017 06:00:00"
        },
        "attributes": {
          "objectType": "AzureUtilizationRecord"
        }
      },

      "links": {
        "self": {
          "uri": "customers/E499C962-9218-4DBA-8B83-8ADC94F47B9F/subscriptions/FC8F8908-F918-4406-AF13-D5BC0FE41865/utilizations/azure?start_time=2017-06-10T00:00:00Z&end_time=2017-07-09T00:00:00Z&granularity=Daily&show_details=True&size=1000",
          "method": "GET",
          "headers": []
        }
      },
      "attributes": {
        "objectType": "Collection"
      }
    }
  ]
}
```
