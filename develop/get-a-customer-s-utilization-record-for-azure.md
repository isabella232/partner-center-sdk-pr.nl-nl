---
title: Gebruiksrecords van een klant ophalen voor Azure
description: U kunt de API voor Azure-gebruik gebruiken om de gebruiksrecords van het Azure-abonnement van een klant op te halen voor een opgegeven periode.
ms.date: 04/19/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 23c8d18462081c6d6c95c1d969f269cbb3f8754b
ms.sourcegitcommit: abefe11421edc421491f14b257b2408b4f29b669
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/20/2021
ms.locfileid: "107745589"
---
# <a name="get-a-customers-utilization-records-for-azure"></a><span data-ttu-id="15d40-103">Gebruiksrecords van een klant ophalen voor Azure</span><span class="sxs-lookup"><span data-stu-id="15d40-103">Get a customer's utilization records for Azure</span></span>

<span data-ttu-id="15d40-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="15d40-104">**Applies to:**</span></span>

- <span data-ttu-id="15d40-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="15d40-105">Partner Center</span></span>
- <span data-ttu-id="15d40-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="15d40-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="15d40-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="15d40-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="15d40-108">U kunt de gebruiksrecords van het Azure-abonnement van een klant voor een opgegeven periode op halen met behulp van de API voor Azure-gebruik.</span><span class="sxs-lookup"><span data-stu-id="15d40-108">You can get the utilization records of a customer's Azure subscription for a specified time period using the Azure utilization API.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="15d40-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="15d40-109">Prerequisites</span></span>

- <span data-ttu-id="15d40-110">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="15d40-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="15d40-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="15d40-111">This scenario supports authentication with both standalone app and App+User credentials.</span></span>

- <span data-ttu-id="15d40-112">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="15d40-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="15d40-113">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="15d40-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="15d40-114">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="15d40-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="15d40-115">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="15d40-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="15d40-116">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="15d40-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="15d40-117">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="15d40-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="15d40-118">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="15d40-118">A subscription identifier.</span></span>

<span data-ttu-id="15d40-119">Deze API retourneert dagelijks en elk uur een onaangewaardeerd verbruik voor een willekeurige periode.</span><span class="sxs-lookup"><span data-stu-id="15d40-119">This API returns daily and hourly unrated consumption for an arbitrary time span.</span></span> <span data-ttu-id="15d40-120">Deze *API wordt echter niet ondersteund voor Azure-plannen.*</span><span class="sxs-lookup"><span data-stu-id="15d40-120">However, *this API isn't supported for Azure plans*.</span></span> <span data-ttu-id="15d40-121">Als u een Azure-abonnement hebt, bekijkt u de artikelen [Niet-gefactureerde](get-invoice-unbilled-consumption-lineitems.md) verbruiksregelitems ontvangen en In plaats daarvan factuur gefactureerde [verbruiksregelitems](get-invoice-billed-consumption-lineitems.md) ontvangen.</span><span class="sxs-lookup"><span data-stu-id="15d40-121">If you have an Azure plan, see the articles [Get invoice un-billed consumption line items](get-invoice-unbilled-consumption-lineitems.md) and [Get invoice billed consumption line items](get-invoice-billed-consumption-lineitems.md) instead.</span></span> <span data-ttu-id="15d40-122">In deze artikelen wordt beschreven hoe u een gemiddeld verbruik op dagelijks niveau per meter per resource kunt krijgen.</span><span class="sxs-lookup"><span data-stu-id="15d40-122">These articles describe how to get rated consumption at a daily level per meter per resource.</span></span> <span data-ttu-id="15d40-123">Dit tariefverbruik is gelijk aan de dagelijkse grain-gegevens die worden geleverd door de Azure-gebruiks-API.</span><span class="sxs-lookup"><span data-stu-id="15d40-123">This rate consumption is equivalent to the daily grain data provided by the Azure utilization API.</span></span> <span data-ttu-id="15d40-124">U moet de factuur-id gebruiken om gefactureerde gebruiksgegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="15d40-124">You'll need to use the invoice identifier to retrieve billed usage data.</span></span> <span data-ttu-id="15d40-125">U kunt ook huidige en vorige perioden gebruiken om niet-gefactureerde gebruiksschattingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="15d40-125">Or, you can use current and previous periods to get un-billed usage estimates.</span></span> <span data-ttu-id="15d40-126">Gegevens die per uur worden verzameld en willekeurige *datumbereikfilters worden momenteel niet ondersteund voor abonnementsresources van het Azure-plan*.</span><span class="sxs-lookup"><span data-stu-id="15d40-126">*Hourly grain data and arbitrary date range filters aren't currently supported for Azure plan subscription resources*.</span></span>

## <a name="azure-utilization-api"></a><span data-ttu-id="15d40-127">Azure-gebruiks-API</span><span class="sxs-lookup"><span data-stu-id="15d40-127">Azure utilization API</span></span>

<span data-ttu-id="15d40-128">Deze Azure-gebruiks-API biedt toegang tot gebruiksrecords voor een periode die vertegenwoordigt wanneer het gebruik is gerapporteerd in het factureringssysteem.</span><span class="sxs-lookup"><span data-stu-id="15d40-128">This Azure utilization API provides access to utilization records for a time period that represents when the utilization was reported in the billing system.</span></span> <span data-ttu-id="15d40-129">Het biedt toegang tot dezelfde gebruiksgegevens die worden gebruikt om het afstemmingsbestand te maken en te berekenen.</span><span class="sxs-lookup"><span data-stu-id="15d40-129">It provides access to the same utilization data that is used to create and calculate the reconciliation file.</span></span> <span data-ttu-id="15d40-130">Het heeft echter geen kennis van de logica van het afstemmingsbestand van het factureringssysteem.</span><span class="sxs-lookup"><span data-stu-id="15d40-130">However, it does not have knowledge of billing system reconciliation file logic.</span></span> <span data-ttu-id="15d40-131">U mag niet verwachten dat samenvattingsresultaten van afstemmingsbestand exact overeenkomen met het resultaat dat voor dezelfde periode is opgehaald uit deze API.</span><span class="sxs-lookup"><span data-stu-id="15d40-131">You should not expect reconciliation file summary results to match the result retrieved from this API exactly for the same time period.</span></span>

<span data-ttu-id="15d40-132">Het factureringssysteem neemt bijvoorbeeld dezelfde gebruiksgegevens en past regels voor vertraging toe om te bepalen waarvoor rekening wordt gehouden in een afstemmingsbestand.</span><span class="sxs-lookup"><span data-stu-id="15d40-132">For example, the billing system takes the same utilization data and applies lateness rules to determine what is accounted for in a reconciliation file.</span></span> <span data-ttu-id="15d40-133">Wanneer een factureringsperiode wordt gesloten, wordt al het gebruik tot het einde van de dag dat de factureringsperiode eindigt, opgenomen in het afstemmingsbestand.</span><span class="sxs-lookup"><span data-stu-id="15d40-133">When a billing period closes, all usage until the end of the day that the billing period ends is included in the reconciliation file.</span></span> <span data-ttu-id="15d40-134">Te laat gebruik binnen de factureringsperiode die binnen 24 uur na het einde van de factureringsperiode wordt gerapporteerd, wordt in het volgende afstemmingsbestand meegenomen.</span><span class="sxs-lookup"><span data-stu-id="15d40-134">Any late usage within the billing period that is reported within 24 hours after the billing period ends is accounted for in the next reconciliation file.</span></span> <span data-ttu-id="15d40-135">Zie Verbruiksgegevens voor een Azure-abonnement op halen voor de regels voor lateheid van de manier waarop de partner [wordt gefactureerd.](/previous-versions/azure/reference/mt219001(v=azure.100))</span><span class="sxs-lookup"><span data-stu-id="15d40-135">For the lateness rules of how the partner is billed, see [Get consumption data for an Azure subscription](/previous-versions/azure/reference/mt219001(v=azure.100)).</span></span>

<span data-ttu-id="15d40-136">Deze REST API wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="15d40-136">This REST API is paged.</span></span> <span data-ttu-id="15d40-137">Als de nettolading van het antwoord groter is dan één pagina, moet u de volgende koppeling volgen om de volgende pagina met gebruiksrecords op te halen.</span><span class="sxs-lookup"><span data-stu-id="15d40-137">If the response payload is larger than a single page, you must follow the next link to get the next page of utilization records.</span></span>

### <a name="scenario--partner-a-has-transferred-billing-ownership-of-azure-legacy-subscription-145p-to-partner-b"></a><span data-ttu-id="15d40-138">Scenario: Partner A heeft het eigendom van de facturering van het Azure Legacy-abonnement (145P) overgedragen naar partner B</span><span class="sxs-lookup"><span data-stu-id="15d40-138">Scenario : Partner A has transferred billing ownership of Azure Legacy Subscription (145P) to Partner B</span></span>

<span data-ttu-id="15d40-139">Als een partner het eigendom van facturering van een verouderd Azure-abonnement overboekt naar een andere partner, moeten ze, wanneer de nieuwe partner de Gebruiks-API aanroept voor het overgedragen abonnement, de commerce-abonnements-id (die wordt weer in het Partner Center-account) gebruiken in plaats van de Azure-rechten-id.</span><span class="sxs-lookup"><span data-stu-id="15d40-139">If a partner transfers billing ownership of an Azure legacy subscription to another partner, when new the new partner calls Utilization API for transferred subscription they have to use Commerce Subscription ID (which shows up in their Partner Center account) rather than the Azure Entitlement ID.</span></span> <span data-ttu-id="15d40-140">De Azure-rechten-id wordt alleen voor partner B weergegeven wanneer deze namens (AOBO) beheerder zijn van de Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="15d40-140">Azure Entitlement ID appears for Partner B only when they are Admin on behalf of (AOBO) to Customer's Azure portal.</span></span> 

<span data-ttu-id="15d40-141">Als u de Utilization-API voor het overgedragen abonnement wilt aanroepen, moet de nieuwe partner de commerce-abonnements-id gebruiken.</span><span class="sxs-lookup"><span data-stu-id="15d40-141">To successfully call the Utilization API for the transferred subscription, the new partner needs to use the Commerce Subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="15d40-142">C\#</span><span class="sxs-lookup"><span data-stu-id="15d40-142">C\#</span></span>

<span data-ttu-id="15d40-143">De Azure-gebruiksrecords verkrijgen:</span><span class="sxs-lookup"><span data-stu-id="15d40-143">To obtain the Azure Utilization Records:</span></span>

1. <span data-ttu-id="15d40-144">Haal de klant-id en abonnements-id op.</span><span class="sxs-lookup"><span data-stu-id="15d40-144">Get the customer ID and subscription ID.</span></span>

2. <span data-ttu-id="15d40-145">Roep de [**methode IAzureUtilizationCollection.Query**](/dotnet/api/microsoft.store.partnercenter.utilization.iazureutilizationcollection.query) aan om een [**ResourceCollection**](/dotnet/api/microsoft.store.partnercenter.models.resourcecollection-1) te retourneren die de gebruiksrecords bevat.</span><span class="sxs-lookup"><span data-stu-id="15d40-145">Call the [**IAzureUtilizationCollection.Query**](/dotnet/api/microsoft.store.partnercenter.utilization.iazureutilizationcollection.query) method to return a [**ResourceCollection**](/dotnet/api/microsoft.store.partnercenter.models.resourcecollection-1) that contains the utilization records.</span></span>

3. <span data-ttu-id="15d40-146">Een Azure-gebruiksrecord-enumerator verkrijgen om de gebruikspagina's te doorlopen.</span><span class="sxs-lookup"><span data-stu-id="15d40-146">Obtain an Azure utilization record enumerator to traverse the utilization pages.</span></span> <span data-ttu-id="15d40-147">Deze stap is vereist, omdat de resourceverzameling wordt gepaginad.</span><span class="sxs-lookup"><span data-stu-id="15d40-147">This step is required, because the resource collection is paged.</span></span>

- <span data-ttu-id="15d40-148">**Voorbeeld:** [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="15d40-148">**Sample**: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="15d40-149">**Project**: Partnercentrum-SDK samples</span><span class="sxs-lookup"><span data-stu-id="15d40-149">**Project**: Partner Center SDK Samples</span></span>
- <span data-ttu-id="15d40-150">**Klasse**: GetAzureSubscriptionUtilization.cs</span><span class="sxs-lookup"><span data-stu-id="15d40-150">**Class**: GetAzureSubscriptionUtilization.cs</span></span>

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

## <a name="java"></a><span data-ttu-id="15d40-151">Java</span><span class="sxs-lookup"><span data-stu-id="15d40-151">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="15d40-152">Als u de Azure-gebruiksrecords wilt verkrijgen, hebt u eerst een klant-id en een abonnements-id nodig.</span><span class="sxs-lookup"><span data-stu-id="15d40-152">To obtain the Azure Utilization Records, you first need a customer identifier and a subscription identifier.</span></span> <span data-ttu-id="15d40-153">Vervolgens roept u de **functie IAzureUtilizationCollection.query** aan om een **ResourceCollection** te retourneren die de gebruiksrecords bevat.</span><span class="sxs-lookup"><span data-stu-id="15d40-153">You then call the **IAzureUtilizationCollection.query** function to return a **ResourceCollection** that contains the utilization records.</span></span> <span data-ttu-id="15d40-154">Omdat de resourceverzameling wordt gepaginad, moet u vervolgens een Azure-gebruiksrecord-enumerator verkrijgen om de gebruikspagina's te doorlopen.</span><span class="sxs-lookup"><span data-stu-id="15d40-154">Because the resource collection is paged, you must then obtain an Azure utilization record enumerator to traverse the utilization pages.</span></span>

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

## <a name="powershell"></a><span data-ttu-id="15d40-155">PowerShell</span><span class="sxs-lookup"><span data-stu-id="15d40-155">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="15d40-156">Als u de Azure-gebruiksrecords wilt verkrijgen, hebt u eerst een klant-id en een abonnements-id nodig.</span><span class="sxs-lookup"><span data-stu-id="15d40-156">To obtain the Azure Utilization Records, you first need a customer identifier and a subscription identifier.</span></span> <span data-ttu-id="15d40-157">Vervolgens roept u [**get-PartnerCustomerSubscriptionUtilization aan.**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscriptionUtilization.md)</span><span class="sxs-lookup"><span data-stu-id="15d40-157">You then call the [**Get-PartnerCustomerSubscriptionUtilization**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscriptionUtilization.md).</span></span> <span data-ttu-id="15d40-158">Deze opdracht retourneert alle records die beschikbaar zijn voor de opgegeven periode.</span><span class="sxs-lookup"><span data-stu-id="15d40-158">This command will return all records available for the specified period of time.</span></span>

```powershell
# $customerId
# $subscriptionId

Get-PartnerCustomerSubscriptionUtilization -CustomerId $customerId -SubscriptionId $subscriptionId -StartDate (Get-Date).AddDays(-2).ToUniversalTime() -Granularity Hourly -ShowDetails
```

## <a name="rest-request"></a><span data-ttu-id="15d40-159">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="15d40-159">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="15d40-160">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="15d40-160">Request syntax</span></span>

| <span data-ttu-id="15d40-161">Methode</span><span class="sxs-lookup"><span data-stu-id="15d40-161">Method</span></span> | <span data-ttu-id="15d40-162">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="15d40-162">Request URI</span></span> |
|------- | ----------- |
| <span data-ttu-id="15d40-163">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="15d40-163">**GET**</span></span> | <span data-ttu-id="15d40-164">*{baseURL}*/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/utilizations/azure?start \_ time={start-time}&end \_ time={end-time}&granularity={granularity}&show \_ details={True}</span><span class="sxs-lookup"><span data-stu-id="15d40-164">*{baseURL}*/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/utilizations/azure?start\_time={start-time}&end\_time={end-time}&granularity={granularity}&show\_details={True}</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="15d40-165">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="15d40-165">URI parameters</span></span>

<span data-ttu-id="15d40-166">Gebruik het volgende pad en de queryparameters om de gebruiksrecords op te halen.</span><span class="sxs-lookup"><span data-stu-id="15d40-166">Use the following path and query parameters to get the utilization records.</span></span>

| <span data-ttu-id="15d40-167">Naam</span><span class="sxs-lookup"><span data-stu-id="15d40-167">Name</span></span> | <span data-ttu-id="15d40-168">Type</span><span class="sxs-lookup"><span data-stu-id="15d40-168">Type</span></span> | <span data-ttu-id="15d40-169">Vereist</span><span class="sxs-lookup"><span data-stu-id="15d40-169">Required</span></span> | <span data-ttu-id="15d40-170">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="15d40-170">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="15d40-171">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="15d40-171">customer-tenant-id</span></span> | <span data-ttu-id="15d40-172">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="15d40-172">string</span></span> | <span data-ttu-id="15d40-173">Yes</span><span class="sxs-lookup"><span data-stu-id="15d40-173">Yes</span></span> | <span data-ttu-id="15d40-174">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="15d40-174">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="15d40-175">subscription-id</span><span class="sxs-lookup"><span data-stu-id="15d40-175">subscription-id</span></span> | <span data-ttu-id="15d40-176">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="15d40-176">string</span></span> | <span data-ttu-id="15d40-177">Yes</span><span class="sxs-lookup"><span data-stu-id="15d40-177">Yes</span></span> | <span data-ttu-id="15d40-178">Een tekenreeks in GUID-indeling die het abonnement identificeert.</span><span class="sxs-lookup"><span data-stu-id="15d40-178">A GUID-formatted string that identifies the subscription.</span></span> |
| <span data-ttu-id="15d40-179">start_tijd</span><span class="sxs-lookup"><span data-stu-id="15d40-179">start_time</span></span> | <span data-ttu-id="15d40-180">tekenreeks in UTC-datum/tijd-offsetnotatie</span><span class="sxs-lookup"><span data-stu-id="15d40-180">string in UTC date-time offset format</span></span> | <span data-ttu-id="15d40-181">Yes</span><span class="sxs-lookup"><span data-stu-id="15d40-181">Yes</span></span> | <span data-ttu-id="15d40-182">Het begin van het tijdsbereik dat vertegenwoordigt wanneer het gebruik is gerapporteerd in het factureringssysteem.</span><span class="sxs-lookup"><span data-stu-id="15d40-182">The start of the time range that represents when the utilization was reported in the billing system.</span></span> |
| <span data-ttu-id="15d40-183">end_time</span><span class="sxs-lookup"><span data-stu-id="15d40-183">end_time</span></span> | <span data-ttu-id="15d40-184">tekenreeks in UTC-datum/tijd-offsetnotatie</span><span class="sxs-lookup"><span data-stu-id="15d40-184">string in UTC date-time offset format</span></span> | <span data-ttu-id="15d40-185">Yes</span><span class="sxs-lookup"><span data-stu-id="15d40-185">Yes</span></span> | <span data-ttu-id="15d40-186">Het einde van het tijdsbereik dat vertegenwoordigt wanneer het gebruik is gerapporteerd in het factureringssysteem.</span><span class="sxs-lookup"><span data-stu-id="15d40-186">The end of the time range that represents when the utilization was reported in the billing system.</span></span> |
| <span data-ttu-id="15d40-187">Granulariteit</span><span class="sxs-lookup"><span data-stu-id="15d40-187">granularity</span></span> | <span data-ttu-id="15d40-188">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="15d40-188">string</span></span> | <span data-ttu-id="15d40-189">No</span><span class="sxs-lookup"><span data-stu-id="15d40-189">No</span></span> | <span data-ttu-id="15d40-190">Definieert de granulariteit van gebruiksaggregaties.</span><span class="sxs-lookup"><span data-stu-id="15d40-190">Defines the granularity of usage aggregations.</span></span> <span data-ttu-id="15d40-191">Beschikbare opties zijn: `daily` (standaard) en `hourly` .</span><span class="sxs-lookup"><span data-stu-id="15d40-191">Available options are: `daily` (default) and `hourly`.</span></span>
| <span data-ttu-id="15d40-192">show_details</span><span class="sxs-lookup"><span data-stu-id="15d40-192">show_details</span></span> | <span data-ttu-id="15d40-193">booleaans</span><span class="sxs-lookup"><span data-stu-id="15d40-193">boolean</span></span> | <span data-ttu-id="15d40-194">No</span><span class="sxs-lookup"><span data-stu-id="15d40-194">No</span></span> | <span data-ttu-id="15d40-195">Hiermee geeft u op of u de gebruiksgegevens op instantieniveau wilt op halen.</span><span class="sxs-lookup"><span data-stu-id="15d40-195">Specifies whether to get the instance-level usage details.</span></span> <span data-ttu-id="15d40-196">De standaardwaarde is `true`.</span><span class="sxs-lookup"><span data-stu-id="15d40-196">The default is `true`.</span></span> |
| <span data-ttu-id="15d40-197">grootte</span><span class="sxs-lookup"><span data-stu-id="15d40-197">size</span></span> | <span data-ttu-id="15d40-198">getal</span><span class="sxs-lookup"><span data-stu-id="15d40-198">number</span></span> | <span data-ttu-id="15d40-199">No</span><span class="sxs-lookup"><span data-stu-id="15d40-199">No</span></span> | <span data-ttu-id="15d40-200">Hiermee geeft u het aantal aggregaties op dat wordt geretourneerd door één API-aanroep.</span><span class="sxs-lookup"><span data-stu-id="15d40-200">Specifies the number of aggregations returned by a single API call.</span></span> <span data-ttu-id="15d40-201">De standaardwaarde is 1000.</span><span class="sxs-lookup"><span data-stu-id="15d40-201">The default is 1000.</span></span> <span data-ttu-id="15d40-202">Het maximum is 1000.</span><span class="sxs-lookup"><span data-stu-id="15d40-202">The max is 1000.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="15d40-203">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="15d40-203">Request headers</span></span>

<span data-ttu-id="15d40-204">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="15d40-204">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="15d40-205">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="15d40-205">Request body</span></span>

<span data-ttu-id="15d40-206">Geen</span><span class="sxs-lookup"><span data-stu-id="15d40-206">None</span></span>

### <a name="request-example"></a><span data-ttu-id="15d40-207">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="15d40-207">Request example</span></span>

<span data-ttu-id="15d40-208">De volgende voorbeeldaanvraag produceert resultaten die vergelijkbaar zijn met wat het afstemmingsbestand laat zien voor de periode 7/2 - 8/1.</span><span class="sxs-lookup"><span data-stu-id="15d40-208">The following example request produces results similar to what the reconciliation file will show for the period 7/2 - 8/1.</span></span> <span data-ttu-id="15d40-209">Deze resultaten komen mogelijk niet exact overeen (zie de sectie [Api voor Azure-gebruik](#azure-utilization-api) voor meer informatie).</span><span class="sxs-lookup"><span data-stu-id="15d40-209">These results may not match exactly (see the section [Azure utilization API](#azure-utilization-api) for details).</span></span>

<span data-ttu-id="15d40-210">Deze voorbeeldaanvraag retourneert gebruiksgegevens die zijn gerapporteerd in het factureringssysteem tussen 7/2 om 12:00 uur (UTC) en 8/2 om 12:00 uur (UTC).</span><span class="sxs-lookup"><span data-stu-id="15d40-210">This example request returns utilization data reported in the billing system between 7/2 at 12 AM (UTC) and 8/2 at 12 AM (UTC).</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/E499C962-9218-4DBA-8B83-8ADC94F47B9F/subscriptions/FC8F8908-F918-4406-AF13-D5BC0FE41865/utilizations/azure?start_time=2017-07-02T00:00:00-08:00&end_time=2017-08-02T00:00:00-08:00 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="15d40-211">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="15d40-211">REST response</span></span>

<span data-ttu-id="15d40-212">Als dit lukt, retourneert deze methode een verzameling [Azure Utilization Record-resources](azure-utilization-record-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="15d40-212">If successful, this method returns a collection of [Azure Utilization Record](azure-utilization-record-resources.md) resources in the response body.</span></span> <span data-ttu-id="15d40-213">Als de Azure-gebruiksgegevens nog niet gereed zijn in een afhankelijk systeem, retourneert deze methode een HTTP-statuscode 204 met een Retry-After header.</span><span class="sxs-lookup"><span data-stu-id="15d40-213">If the Azure utilization data isn't yet ready in a dependent system, this method returns an HTTP Status Code 204 with a Retry-After header.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="15d40-214">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="15d40-214">Response success and error codes</span></span>

<span data-ttu-id="15d40-215">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="15d40-215">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="15d40-216">Gebruik een hulpprogramma voor netwerk traceer om de HTTP-statuscode, [het foutcodetype](error-codes.md)en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="15d40-216">Use a network trace tool to read the HTTP status code, [error code type](error-codes.md), and additional parameters.</span></span>

### <a name="response-example"></a><span data-ttu-id="15d40-217">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="15d40-217">Response example</span></span>

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
