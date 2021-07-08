---
title: Gebruiksrecords van een klant ophalen voor Azure
description: U kunt de API voor Azure-gebruik gebruiken om de gebruiksrecords van het Azure-abonnement van een klant op te halen voor een opgegeven periode.
ms.date: 04/19/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7024bc65976a9b43a62b66c529d271519181ab23
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874921"
---
# <a name="get-a-customers-utilization-records-for-azure"></a><span data-ttu-id="91601-103">Gebruiksrecords van een klant ophalen voor Azure</span><span class="sxs-lookup"><span data-stu-id="91601-103">Get a customer's utilization records for Azure</span></span>

<span data-ttu-id="91601-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="91601-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="91601-105">U kunt de gebruiksrecords van het Azure-abonnement van een klant voor een opgegeven periode op halen met behulp van de API voor Azure-gebruik.</span><span class="sxs-lookup"><span data-stu-id="91601-105">You can get the utilization records of a customer's Azure subscription for a specified time period using the Azure utilization API.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="91601-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="91601-106">Prerequisites</span></span>

- <span data-ttu-id="91601-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="91601-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="91601-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="91601-108">This scenario supports authentication with both standalone app and App+User credentials.</span></span>

- <span data-ttu-id="91601-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="91601-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="91601-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="91601-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="91601-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="91601-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="91601-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="91601-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="91601-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="91601-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="91601-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="91601-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="91601-115">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="91601-115">A subscription identifier.</span></span>

<span data-ttu-id="91601-116">Deze API retourneert dagelijks en elk uur een onaangewaardeerd verbruik voor een willekeurige periode.</span><span class="sxs-lookup"><span data-stu-id="91601-116">This API returns daily and hourly unrated consumption for an arbitrary time span.</span></span> <span data-ttu-id="91601-117">Deze *API wordt echter niet ondersteund voor Azure-plannen.*</span><span class="sxs-lookup"><span data-stu-id="91601-117">However, *this API isn't supported for Azure plans*.</span></span> <span data-ttu-id="91601-118">Als u een Azure-abonnement hebt, bekijkt u de artikelen [Niet-gefactureerde](get-invoice-unbilled-consumption-lineitems.md) verbruiksregelitems ontvangen en In plaats daarvan gefactureerde [verbruiksregelitems](get-invoice-billed-consumption-lineitems.md) ontvangen.</span><span class="sxs-lookup"><span data-stu-id="91601-118">If you have an Azure plan, see the articles [Get invoice unbilled consumption line items](get-invoice-unbilled-consumption-lineitems.md) and [Get invoice billed consumption line items](get-invoice-billed-consumption-lineitems.md) instead.</span></span> <span data-ttu-id="91601-119">In deze artikelen wordt beschreven hoe u een gemiddeld verbruik per dag per meter per resource kunt krijgen.</span><span class="sxs-lookup"><span data-stu-id="91601-119">These articles describe how to get rated consumption at a daily level per meter per resource.</span></span> <span data-ttu-id="91601-120">Dit tariefverbruik is gelijk aan de dagelijkse grain-gegevens die worden geleverd door de Azure-gebruiks-API.</span><span class="sxs-lookup"><span data-stu-id="91601-120">This rate consumption is equivalent to the daily grain data provided by the Azure utilization API.</span></span> <span data-ttu-id="91601-121">U moet de factuur-id gebruiken om gefactureerde gebruiksgegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="91601-121">You'll need to use the invoice identifier to retrieve billed usage data.</span></span> <span data-ttu-id="91601-122">U kunt ook huidige en vorige perioden gebruiken om niet-gebileerde gebruiksschattingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="91601-122">Or, you can use current and previous periods to get unbilled usage estimates.</span></span> <span data-ttu-id="91601-123">Gegevens die per uur worden verzameld en willekeurige *datumbereikfilters worden momenteel niet ondersteund voor abonnementsresources van het Azure-plan*.</span><span class="sxs-lookup"><span data-stu-id="91601-123">*Hourly grain data and arbitrary date range filters aren't currently supported for Azure plan subscription resources*.</span></span>

## <a name="azure-utilization-api"></a><span data-ttu-id="91601-124">Api voor Azure-gebruik</span><span class="sxs-lookup"><span data-stu-id="91601-124">Azure utilization API</span></span>

<span data-ttu-id="91601-125">Deze API voor Azure-gebruik biedt toegang tot gebruiksrecords voor een periode die vertegenwoordigt wanneer het gebruik is gerapporteerd in het factureringssysteem.</span><span class="sxs-lookup"><span data-stu-id="91601-125">This Azure utilization API provides access to utilization records for a time period that represents when the utilization was reported in the billing system.</span></span> <span data-ttu-id="91601-126">Het biedt toegang tot dezelfde gebruiksgegevens die worden gebruikt om het afstemmingsbestand te maken en te berekenen.</span><span class="sxs-lookup"><span data-stu-id="91601-126">It provides access to the same utilization data that is used to create and calculate the reconciliation file.</span></span> <span data-ttu-id="91601-127">Het heeft echter geen kennis van bestandslogica voor factureringssysteemafstemming.</span><span class="sxs-lookup"><span data-stu-id="91601-127">However, it does not have knowledge of billing system reconciliation file logic.</span></span> <span data-ttu-id="91601-128">U mag niet verwachten dat samenvattingsresultaten van afstemmingsbestand exact overeenkomen met het resultaat dat is opgehaald uit deze API voor dezelfde periode.</span><span class="sxs-lookup"><span data-stu-id="91601-128">You should not expect reconciliation file summary results to match the result retrieved from this API exactly for the same time period.</span></span>

<span data-ttu-id="91601-129">Het factureringssysteem neemt bijvoorbeeld dezelfde gebruiksgegevens en past lateheidsregels toe om te bepalen waarvoor rekening wordt gehouden in een afstemmingsbestand.</span><span class="sxs-lookup"><span data-stu-id="91601-129">For example, the billing system takes the same utilization data and applies lateness rules to determine what is accounted for in a reconciliation file.</span></span> <span data-ttu-id="91601-130">Wanneer een factureringsperiode wordt gesloten, wordt al het gebruik tot het einde van de dag dat de factureringsperiode eindigt, opgenomen in het afstemmingsbestand.</span><span class="sxs-lookup"><span data-stu-id="91601-130">When a billing period closes, all usage until the end of the day that the billing period ends is included in the reconciliation file.</span></span> <span data-ttu-id="91601-131">Laat gebruik binnen de factureringsperiode die binnen 24 uur na het einde van de factureringsperiode wordt gerapporteerd, wordt verantwoord in het volgende afstemmingsbestand.</span><span class="sxs-lookup"><span data-stu-id="91601-131">Any late usage within the billing period that is reported within 24 hours after the billing period ends is accounted for in the next reconciliation file.</span></span> <span data-ttu-id="91601-132">Zie Verbruiksgegevens voor een Azure-abonnement op halen voor de regels voor lateheid van de manier waarop de partner [wordt gefactureerd.](/previous-versions/azure/reference/mt219001(v=azure.100))</span><span class="sxs-lookup"><span data-stu-id="91601-132">For the lateness rules of how the partner is billed, see [Get consumption data for an Azure subscription](/previous-versions/azure/reference/mt219001(v=azure.100)).</span></span>

<span data-ttu-id="91601-133">Dit REST API pagina's.</span><span class="sxs-lookup"><span data-stu-id="91601-133">This REST API is paged.</span></span> <span data-ttu-id="91601-134">Als de nettolading van het antwoord groter is dan één pagina, moet u de volgende koppeling volgen om de volgende pagina met gebruiksrecords op te halen.</span><span class="sxs-lookup"><span data-stu-id="91601-134">If the response payload is larger than a single page, you must follow the next link to get the next page of utilization records.</span></span>

### <a name="scenario-partner-a-has-transferred-billing-ownership-of-azure-legacy-subscription-145p-to-partner-b"></a><span data-ttu-id="91601-135">Scenario: Partner A heeft het eigendom van de facturering van het verouderde Azure-abonnement (145P) overgedragen aan partner B</span><span class="sxs-lookup"><span data-stu-id="91601-135">Scenario: Partner A has transferred billing ownership of Azure Legacy Subscription (145P) to Partner B</span></span>

<span data-ttu-id="91601-136">Als een partner het eigendom van facturering van een verouderd Azure-abonnement overboekt naar een andere partner, moet de nieuwe partner de Utilization-API voor overgedragen abonnementen aanroepen om de commerce-abonnements-id (die wordt weer te geven in het Partner Center-account) te gebruiken in plaats van de Azure-rechten-id.</span><span class="sxs-lookup"><span data-stu-id="91601-136">If a partner transfers billing ownership of an Azure legacy subscription to another partner, when new the new partner calls Utilization API for transferred subscription they have to use Commerce Subscription ID (which shows up in their Partner Center account) rather than the Azure Entitlement ID.</span></span> <span data-ttu-id="91601-137">De Azure-rechten-id wordt alleen voor partner B weergegeven wanneer deze namens (AOBO) beheerder zijn voor de klant Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="91601-137">Azure Entitlement ID appears for Partner B only when they are Admin on behalf of (AOBO) to Customer's Azure portal.</span></span> 

<span data-ttu-id="91601-138">Om de utilization-API voor het overgedragen abonnement aan te roepen, moet de nieuwe partner de commerce-abonnements-id gebruiken.</span><span class="sxs-lookup"><span data-stu-id="91601-138">To successfully call the Utilization API for the transferred subscription, the new partner needs to use the Commerce Subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="91601-139">C\#</span><span class="sxs-lookup"><span data-stu-id="91601-139">C\#</span></span>

<span data-ttu-id="91601-140">De Azure-gebruiksrecords verkrijgen:</span><span class="sxs-lookup"><span data-stu-id="91601-140">To obtain the Azure Utilization Records:</span></span>

1. <span data-ttu-id="91601-141">Haal de klant-id en abonnements-id op.</span><span class="sxs-lookup"><span data-stu-id="91601-141">Get the customer ID and subscription ID.</span></span>

2. <span data-ttu-id="91601-142">Roep de [**methode IAzureUtilizationCollection.Query**](/dotnet/api/microsoft.store.partnercenter.utilization.iazureutilizationcollection.query) aan om een [**ResourceCollection**](/dotnet/api/microsoft.store.partnercenter.models.resourcecollection-1) te retourneren die de gebruiksrecords bevat.</span><span class="sxs-lookup"><span data-stu-id="91601-142">Call the [**IAzureUtilizationCollection.Query**](/dotnet/api/microsoft.store.partnercenter.utilization.iazureutilizationcollection.query) method to return a [**ResourceCollection**](/dotnet/api/microsoft.store.partnercenter.models.resourcecollection-1) that contains the utilization records.</span></span>

3. <span data-ttu-id="91601-143">Een Azure-gebruiksrecord-enumerator verkrijgen om de gebruikspagina's te doorlopen.</span><span class="sxs-lookup"><span data-stu-id="91601-143">Obtain an Azure utilization record enumerator to traverse the utilization pages.</span></span> <span data-ttu-id="91601-144">Deze stap is vereist, omdat de resourceverzameling wordt gepaginad.</span><span class="sxs-lookup"><span data-stu-id="91601-144">This step is required, because the resource collection is paged.</span></span>

- <span data-ttu-id="91601-145">**Voorbeeld:** [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="91601-145">**Sample**: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="91601-146">**Project:** Partnercentrum-SDK Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="91601-146">**Project**: Partner Center SDK Samples</span></span>
- <span data-ttu-id="91601-147">**Klasse**: GetAzureSubscriptionUtilization.cs</span><span class="sxs-lookup"><span data-stu-id="91601-147">**Class**: GetAzureSubscriptionUtilization.cs</span></span>

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

## <a name="java"></a><span data-ttu-id="91601-148">Java</span><span class="sxs-lookup"><span data-stu-id="91601-148">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="91601-149">Als u de Azure-gebruiksrecords wilt verkrijgen, hebt u eerst een klant-id en een abonnements-id nodig.</span><span class="sxs-lookup"><span data-stu-id="91601-149">To obtain the Azure Utilization Records, you first need a customer identifier and a subscription identifier.</span></span> <span data-ttu-id="91601-150">Vervolgens roept u de **functie IAzureUtilizationCollection.query** aan om een **ResourceCollection** te retourneren die de gebruiksrecords bevat.</span><span class="sxs-lookup"><span data-stu-id="91601-150">You then call the **IAzureUtilizationCollection.query** function to return a **ResourceCollection** that contains the utilization records.</span></span> <span data-ttu-id="91601-151">Omdat de resourceverzameling wordt gepaginad, moet u vervolgens een Azure-gebruiksrecord-enumerator verkrijgen om de gebruikspagina's te doorlopen.</span><span class="sxs-lookup"><span data-stu-id="91601-151">Because the resource collection is paged, you must then obtain an Azure utilization record enumerator to traverse the utilization pages.</span></span>

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

## <a name="powershell"></a><span data-ttu-id="91601-152">PowerShell</span><span class="sxs-lookup"><span data-stu-id="91601-152">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="91601-153">Als u de Azure-gebruiksrecords wilt verkrijgen, hebt u eerst een klant-id en een abonnements-id nodig.</span><span class="sxs-lookup"><span data-stu-id="91601-153">To obtain the Azure Utilization Records, you first need a customer identifier and a subscription identifier.</span></span> <span data-ttu-id="91601-154">Vervolgens roept u [**get-PartnerCustomerSubscriptionUtilization aan.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscriptionUtilization.md)</span><span class="sxs-lookup"><span data-stu-id="91601-154">You then call the [**Get-PartnerCustomerSubscriptionUtilization**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscriptionUtilization.md).</span></span> <span data-ttu-id="91601-155">Deze opdracht retourneert alle records die beschikbaar zijn voor de opgegeven periode.</span><span class="sxs-lookup"><span data-stu-id="91601-155">This command will return all records available for the specified period of time.</span></span>

```powershell
# $customerId
# $subscriptionId

Get-PartnerCustomerSubscriptionUtilization -CustomerId $customerId -SubscriptionId $subscriptionId -StartDate (Get-Date).AddDays(-2).ToUniversalTime() -Granularity Hourly -ShowDetails
```

## <a name="rest-request"></a><span data-ttu-id="91601-156">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="91601-156">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="91601-157">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="91601-157">Request syntax</span></span>

| <span data-ttu-id="91601-158">Methode</span><span class="sxs-lookup"><span data-stu-id="91601-158">Method</span></span> | <span data-ttu-id="91601-159">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="91601-159">Request URI</span></span> |
|------- | ----------- |
| <span data-ttu-id="91601-160">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="91601-160">**GET**</span></span> | <span data-ttu-id="91601-161">*{baseURL}*/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/utilizations/azure?start \_ time={start-time}&end \_ time={end-time}&granularity={granularity}&show \_ details={True}</span><span class="sxs-lookup"><span data-stu-id="91601-161">*{baseURL}*/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/utilizations/azure?start\_time={start-time}&end\_time={end-time}&granularity={granularity}&show\_details={True}</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="91601-162">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="91601-162">URI parameters</span></span>

<span data-ttu-id="91601-163">Gebruik het volgende pad en de queryparameters om de gebruiksrecords op te halen.</span><span class="sxs-lookup"><span data-stu-id="91601-163">Use the following path and query parameters to get the utilization records.</span></span>

| <span data-ttu-id="91601-164">Naam</span><span class="sxs-lookup"><span data-stu-id="91601-164">Name</span></span> | <span data-ttu-id="91601-165">Type</span><span class="sxs-lookup"><span data-stu-id="91601-165">Type</span></span> | <span data-ttu-id="91601-166">Vereist</span><span class="sxs-lookup"><span data-stu-id="91601-166">Required</span></span> | <span data-ttu-id="91601-167">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="91601-167">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="91601-168">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="91601-168">customer-tenant-id</span></span> | <span data-ttu-id="91601-169">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="91601-169">string</span></span> | <span data-ttu-id="91601-170">Ja</span><span class="sxs-lookup"><span data-stu-id="91601-170">Yes</span></span> | <span data-ttu-id="91601-171">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="91601-171">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="91601-172">subscription-id</span><span class="sxs-lookup"><span data-stu-id="91601-172">subscription-id</span></span> | <span data-ttu-id="91601-173">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="91601-173">string</span></span> | <span data-ttu-id="91601-174">Ja</span><span class="sxs-lookup"><span data-stu-id="91601-174">Yes</span></span> | <span data-ttu-id="91601-175">Een tekenreeks in GUID-indeling die het abonnement identificeert.</span><span class="sxs-lookup"><span data-stu-id="91601-175">A GUID-formatted string that identifies the subscription.</span></span> |
| <span data-ttu-id="91601-176">start_tijd</span><span class="sxs-lookup"><span data-stu-id="91601-176">start_time</span></span> | <span data-ttu-id="91601-177">tekenreeks in UTC-datum/tijd-offsetnotatie</span><span class="sxs-lookup"><span data-stu-id="91601-177">string in UTC date-time offset format</span></span> | <span data-ttu-id="91601-178">Ja</span><span class="sxs-lookup"><span data-stu-id="91601-178">Yes</span></span> | <span data-ttu-id="91601-179">Het begin van het tijdsbereik dat vertegenwoordigt wanneer het gebruik is gerapporteerd in het factureringssysteem.</span><span class="sxs-lookup"><span data-stu-id="91601-179">The start of the time range that represents when the utilization was reported in the billing system.</span></span> |
| <span data-ttu-id="91601-180">end_time</span><span class="sxs-lookup"><span data-stu-id="91601-180">end_time</span></span> | <span data-ttu-id="91601-181">tekenreeks in UTC-datum/tijd-offsetnotatie</span><span class="sxs-lookup"><span data-stu-id="91601-181">string in UTC date-time offset format</span></span> | <span data-ttu-id="91601-182">Ja</span><span class="sxs-lookup"><span data-stu-id="91601-182">Yes</span></span> | <span data-ttu-id="91601-183">Het einde van het tijdsbereik dat vertegenwoordigt wanneer het gebruik is gerapporteerd in het factureringssysteem.</span><span class="sxs-lookup"><span data-stu-id="91601-183">The end of the time range that represents when the utilization was reported in the billing system.</span></span> |
| <span data-ttu-id="91601-184">Granulariteit</span><span class="sxs-lookup"><span data-stu-id="91601-184">granularity</span></span> | <span data-ttu-id="91601-185">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="91601-185">string</span></span> | <span data-ttu-id="91601-186">No</span><span class="sxs-lookup"><span data-stu-id="91601-186">No</span></span> | <span data-ttu-id="91601-187">Definieert de granulariteit van gebruiksaggregaties.</span><span class="sxs-lookup"><span data-stu-id="91601-187">Defines the granularity of usage aggregations.</span></span> <span data-ttu-id="91601-188">Beschikbare opties zijn: `daily` (standaard) en `hourly` .</span><span class="sxs-lookup"><span data-stu-id="91601-188">Available options are: `daily` (default) and `hourly`.</span></span>
| <span data-ttu-id="91601-189">show_details</span><span class="sxs-lookup"><span data-stu-id="91601-189">show_details</span></span> | <span data-ttu-id="91601-190">booleaans</span><span class="sxs-lookup"><span data-stu-id="91601-190">boolean</span></span> | <span data-ttu-id="91601-191">Nee</span><span class="sxs-lookup"><span data-stu-id="91601-191">No</span></span> | <span data-ttu-id="91601-192">Hiermee geeft u op of de gebruiksgegevens op exemplaarniveau moeten worden op halen.</span><span class="sxs-lookup"><span data-stu-id="91601-192">Specifies whether to get the instance-level usage details.</span></span> <span data-ttu-id="91601-193">De standaardwaarde is `true`.</span><span class="sxs-lookup"><span data-stu-id="91601-193">The default is `true`.</span></span> |
| <span data-ttu-id="91601-194">grootte</span><span class="sxs-lookup"><span data-stu-id="91601-194">size</span></span> | <span data-ttu-id="91601-195">getal</span><span class="sxs-lookup"><span data-stu-id="91601-195">number</span></span> | <span data-ttu-id="91601-196">Nee</span><span class="sxs-lookup"><span data-stu-id="91601-196">No</span></span> | <span data-ttu-id="91601-197">Hiermee geeft u het aantal aggregaties op dat wordt geretourneerd door één API-aanroep.</span><span class="sxs-lookup"><span data-stu-id="91601-197">Specifies the number of aggregations returned by a single API call.</span></span> <span data-ttu-id="91601-198">De standaardwaarde is 1000.</span><span class="sxs-lookup"><span data-stu-id="91601-198">The default is 1000.</span></span> <span data-ttu-id="91601-199">Het maximum is 1000.</span><span class="sxs-lookup"><span data-stu-id="91601-199">The max is 1000.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="91601-200">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="91601-200">Request headers</span></span>

<span data-ttu-id="91601-201">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="91601-201">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="91601-202">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="91601-202">Request body</span></span>

<span data-ttu-id="91601-203">Geen</span><span class="sxs-lookup"><span data-stu-id="91601-203">None</span></span>

### <a name="request-example"></a><span data-ttu-id="91601-204">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="91601-204">Request example</span></span>

<span data-ttu-id="91601-205">De volgende voorbeeldaanvraag produceert resultaten die vergelijkbaar zijn met wat het afstemmingsbestand laat zien voor de periode 7/2 - 8/1.</span><span class="sxs-lookup"><span data-stu-id="91601-205">The following example request produces results similar to what the reconciliation file will show for the period 7/2 - 8/1.</span></span> <span data-ttu-id="91601-206">Deze resultaten komen mogelijk niet exact overeen (zie de sectie [Azure utilization API](#azure-utilization-api) voor meer informatie).</span><span class="sxs-lookup"><span data-stu-id="91601-206">These results may not match exactly (see the section [Azure utilization API](#azure-utilization-api) for details).</span></span>

<span data-ttu-id="91601-207">Deze voorbeeldaanvraag retourneert gebruiksgegevens die zijn gerapporteerd in het factureringssysteem tussen 7/2 om 12:00 uur (UTC) en 8/2 om 12:00 uur (UTC).</span><span class="sxs-lookup"><span data-stu-id="91601-207">This example request returns utilization data reported in the billing system between 7/2 at 12 AM (UTC) and 8/2 at 12 AM (UTC).</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/E499C962-9218-4DBA-8B83-8ADC94F47B9F/subscriptions/FC8F8908-F918-4406-AF13-D5BC0FE41865/utilizations/azure?start_time=2017-07-02T00:00:00-08:00&end_time=2017-08-02T00:00:00-08:00 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="91601-208">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="91601-208">REST response</span></span>

<span data-ttu-id="91601-209">Als dit lukt, retourneert deze methode een verzameling [Azure Utilization Record-resources](azure-utilization-record-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="91601-209">If successful, this method returns a collection of [Azure Utilization Record](azure-utilization-record-resources.md) resources in the response body.</span></span> <span data-ttu-id="91601-210">Als de Azure-gebruiksgegevens nog niet gereed zijn in een afhankelijk systeem, retourneert deze methode een HTTP-statuscode 204 met een Retry-After header.</span><span class="sxs-lookup"><span data-stu-id="91601-210">If the Azure utilization data isn't yet ready in a dependent system, this method returns an HTTP Status Code 204 with a Retry-After header.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="91601-211">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="91601-211">Response success and error codes</span></span>

<span data-ttu-id="91601-212">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="91601-212">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="91601-213">Gebruik een hulpprogramma voor netwerk traceer om de HTTP-statuscode, [het foutcodetype](error-codes.md)en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="91601-213">Use a network trace tool to read the HTTP status code, [error code type](error-codes.md), and additional parameters.</span></span>

### <a name="response-example"></a><span data-ttu-id="91601-214">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="91601-214">Response example</span></span>

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
