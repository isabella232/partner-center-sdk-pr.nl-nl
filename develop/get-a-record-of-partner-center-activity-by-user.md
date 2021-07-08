---
title: Een record van Partnercentrum-activiteiten ophalen
description: Het ophalen van een record van bewerkingen, zoals uitgevoerd door een partnergebruiker of -toepassing, gedurende een bepaalde periode.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: aec933d4b681d99080619505792bde56bdd25580
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873968"
---
# <a name="get-a-record-of-partner-center-activity"></a><span data-ttu-id="a9710-103">Een record van Partnercentrum-activiteiten ophalen</span><span class="sxs-lookup"><span data-stu-id="a9710-103">Get a record of Partner Center activity</span></span>

<span data-ttu-id="a9710-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="a9710-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="a9710-105">In dit artikel wordt beschreven hoe u een record kunt ophalen van bewerkingen die gedurende een bepaalde periode door een partnergebruiker of toepassing zijn uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a9710-105">This article describes how to retrieve a record of operations that was performed by a partner user or application over a period of time.</span></span>

<span data-ttu-id="a9710-106">Gebruik deze API om controlerecords op te halen voor de afgelopen 30 dagen vanaf de huidige datum, of voor een datumbereik dat is opgegeven door de begindatum en/of einddatum op te neemt.</span><span class="sxs-lookup"><span data-stu-id="a9710-106">Use this API to retrieve audit records for the previous 30 days from the current date, or for a date range specified by including the start date and/or the end date.</span></span> <span data-ttu-id="a9710-107">Houd er echter rekening mee dat om prestatieredenen de beschikbaarheid van gegevens in het activiteitenlogboek is beperkt tot de afgelopen 90 dagen.</span><span class="sxs-lookup"><span data-stu-id="a9710-107">Note, however, that for performance reasons activity log data availability is limited to the previous 90 days.</span></span> <span data-ttu-id="a9710-108">Aanvragen met een begindatum die langer is dan 90 dagen vóór de huidige datum, ontvangen een uitzondering met een slechte aanvraag (foutcode: 400) en een geschikt bericht.</span><span class="sxs-lookup"><span data-stu-id="a9710-108">Requests with a start date greater than 90 days prior to the current date will receive a bad request exception (error code: 400) and an appropriate message.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a9710-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a9710-109">Prerequisites</span></span>

- <span data-ttu-id="a9710-110">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a9710-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a9710-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="a9710-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="a9710-112">C\#</span><span class="sxs-lookup"><span data-stu-id="a9710-112">C\#</span></span>

<span data-ttu-id="a9710-113">Als u een record met Partner Center wilt ophalen, moet u eerst het datumbereik bepalen voor de records die u wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="a9710-113">To retrieve a record of Partner Center operations, first establish the date range for the records you want to retrieve.</span></span> <span data-ttu-id="a9710-114">In het volgende codevoorbeeld wordt alleen een begindatum gebruikt, maar u kunt ook een einddatum opnemen.</span><span class="sxs-lookup"><span data-stu-id="a9710-114">The following code example only uses a start date, but you can also include an end date.</span></span> <span data-ttu-id="a9710-115">Zie de Query-methode voor [**meer**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) informatie.</span><span class="sxs-lookup"><span data-stu-id="a9710-115">For more information, see the [**Query**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) method.</span></span> <span data-ttu-id="a9710-116">Maak vervolgens de variabelen die u nodig hebt voor het type filter dat u wilt toepassen en wijs de juiste waarden toe.</span><span class="sxs-lookup"><span data-stu-id="a9710-116">Next, create the variables you need for the type of filter you want to apply, and assign the appropriate values.</span></span> <span data-ttu-id="a9710-117">Als u bijvoorbeeld wilt filteren op bedrijfsnaamsubtekenreeks, maakt u een variabele om de subtekenreeks op te nemen.</span><span class="sxs-lookup"><span data-stu-id="a9710-117">For example, to filter by company name substring, create a variable to hold the substring.</span></span> <span data-ttu-id="a9710-118">Als u wilt filteren op klant-id, maakt u een variabele voor de id.</span><span class="sxs-lookup"><span data-stu-id="a9710-118">To filter by customer ID, create a variable to hold the ID.</span></span>

<span data-ttu-id="a9710-119">In het volgende voorbeeld wordt voorbeeldcode verstrekt om te filteren op een bedrijfsnaamsubtekenreeks, klant-id of resourcetype.</span><span class="sxs-lookup"><span data-stu-id="a9710-119">In the following example, sample code is provided to filter by a company name substring, customer ID, or resource type.</span></span> <span data-ttu-id="a9710-120">Kies een optie en maak commentaar van de andere.</span><span class="sxs-lookup"><span data-stu-id="a9710-120">Choose one and comment out the others.</span></span> <span data-ttu-id="a9710-121">In elk geval instantieert u eerst een [**SimpleFieldFilter-object**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) met behulp van de standaard [**constructor om**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter.-ctor) het filter te maken.</span><span class="sxs-lookup"><span data-stu-id="a9710-121">In each case, you first instantiate a [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) object using its default [**constructor**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter.-ctor) to create the filter.</span></span> <span data-ttu-id="a9710-122">U moet een tekenreeks doorgeven die het veld bevat dat moet worden gezocht en de juiste operator om toe te passen, zoals wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="a9710-122">You'll need to pass a string that contains the field to search, and the appropriate operator to apply, as shown.</span></span> <span data-ttu-id="a9710-123">U moet ook de tekenreeks verstrekken om op te filteren.</span><span class="sxs-lookup"><span data-stu-id="a9710-123">You also must provide the string to filter by.</span></span>

<span data-ttu-id="a9710-124">Gebruik vervolgens de eigenschap [**AuditRecords**](/dotnet/api/microsoft.store.partnercenter.ipartner.auditrecords) om een interface op te halen voor het controleren van recordbewerkingen en roep de methode [**Query**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) of [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.queryasync) aan om het filter uit te voeren en de verzameling [**auditrecords**](/dotnet/api/microsoft.store.partnercenter.models.auditing.auditrecord) op te halen die de eerste pagina van het resultaat vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="a9710-124">Next, use the [**AuditRecords**](/dotnet/api/microsoft.store.partnercenter.ipartner.auditrecords) property to get an interface to audit record operations, and call the [**Query**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) or [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.queryasync) method to execute the filter and get the collection of [**AuditRecord's**](/dotnet/api/microsoft.store.partnercenter.models.auditing.auditrecord) that represent the first page of the result.</span></span> <span data-ttu-id="a9710-125">Geef de methode door aan de begindatum, een optionele einddatum die hier niet wordt gebruikt in het voorbeeld en een [**IQuery-object**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) dat een query op een entiteit vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a9710-125">Pass the method the start date, an optional end date not used in the example here, and an [**IQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) object that represents a query on an entity.</span></span> <span data-ttu-id="a9710-126">Het IQuery-object wordt gemaakt door het hierboven gemaakte filter door te geven aan de [**BuildSimpleQuery-methode van**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) [**QueryFactory.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory)</span><span class="sxs-lookup"><span data-stu-id="a9710-126">The IQuery object is created by passing the filter created above to the [**QueryFactory's**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) method.</span></span>

<span data-ttu-id="a9710-127">Zodra u de eerste pagina met items hebt, gebruikt u de methode [**Enumerators.AuditRecords.Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) om een enumerator te maken die u kunt gebruiken om de resterende pagina's te controleren.</span><span class="sxs-lookup"><span data-stu-id="a9710-127">Once you have the initial page of items, use the [**Enumerators.AuditRecords.Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) method to create an enumerator that you can use to iterate through the remaining pages.</span></span>

```csharp
// IAggregatePartner partnerOperations;

var startDate = new DateTime(DateTime.Now.Year, DateTime.Now.Month, 01);

// First perform the query, then get the enumerator. Choose one of the following and comment out the other two.

// To retrieve audit records by company name substring (for example "bri" matches "Fabrikam, Inc.").
var searchSubstring="bri";
var filter = new SimpleFieldFilter(AuditRecordSearchField.CompanyName.ToString(), FieldFilterOperation.Substring, searchSubstring);
var auditRecordsPage = partnerOperations.AuditRecords.Query(startDate.Date, query: QueryFactory.Instance.BuildSimpleQuery(filter));

// To retrieve audit records by customer ID.
var customerId="0c39d6d5-c70d-4c55-bc02-f620844f3fd1";
var filter = new SimpleFieldFilter(AuditRecordSearchField.CustomerId.ToString(), FieldFilterOperation.Equals, customerId);
var auditRecordsPage = partnerOperations.AuditRecords.Query(startDate.Date, query: QueryFactory.Instance.BuildSimpleQuery(filter));

// To retrieve audit records by resource type.
int resourceTypeInt = 3; // Subscription Resource.
string searchField = Enum.GetName(typeof(ResourceType), resourceTypeInt);
var filter = new SimpleFieldFilter(AuditRecordSearchField.ResourceType.ToString(), FieldFilterOperation.Equals, searchField);
var auditRecordsPage = partnerOperations.AuditRecords.Query(startDate.Date, query: QueryFactory.Instance.BuildSimpleQuery(filter));

var auditRecordEnumerator = partnerOperations.Enumerators.AuditRecords.Create(auditRecordsPage);

int pageNumber = 1;
while (auditRecordEnumerator.HasValue)
{
    // Work with the current page.
    foreach (var c in auditRecordEnumerator.Current.Items)
    {
        // Display some info, such as operation type, operation date, and operation status.
        Console.WriteLine(string.Format("{0} {1} {2}.", c.OperationType, c.OperationDate, c.OperationStatus));
    }

    // Get the next page of audit records.
    auditRecordEnumerator.Next();
}
```

<span data-ttu-id="a9710-128">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="a9710-128">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="a9710-129">**Project:** Partnercentrum-SDK **map Samples:** Controle</span><span class="sxs-lookup"><span data-stu-id="a9710-129">**Project**: Partner Center SDK Samples **Folder**: Auditing</span></span>

## <a name="rest-request"></a><span data-ttu-id="a9710-130">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="a9710-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a9710-131">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="a9710-131">Request syntax</span></span>

| <span data-ttu-id="a9710-132">Methode</span><span class="sxs-lookup"><span data-stu-id="a9710-132">Method</span></span>  | <span data-ttu-id="a9710-133">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="a9710-133">Request URI</span></span>                                                                                                                                                                                    |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a9710-134">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="a9710-134">**GET**</span></span> | <span data-ttu-id="a9710-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a9710-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate} HTTP/1.1</span></span>                                                                                                     |
| <span data-ttu-id="a9710-136">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="a9710-136">**GET**</span></span> | <span data-ttu-id="a9710-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a9710-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate} HTTP/1.1</span></span>                                                                                   |
| <span data-ttu-id="a9710-138">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="a9710-138">**GET**</span></span> | <span data-ttu-id="a9710-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"CompanyName","Value":"{searchSubstring}","Operator":"substring"} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a9710-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"CompanyName","Value":"{searchSubstring}","Operator":"substring"} HTTP/1.1</span></span> |
| <span data-ttu-id="a9710-140">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="a9710-140">**GET**</span></span> | <span data-ttu-id="a9710-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"CustomerId","Value":"{customerId}","Operator":"equals"} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a9710-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"CustomerId","Value":"{customerId}","Operator":"equals"} HTTP/1.1</span></span>          |
| <span data-ttu-id="a9710-142">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="a9710-142">**GET**</span></span> | <span data-ttu-id="a9710-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"ResourceType","Value":"{resourceType}","Operator":"equals"} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a9710-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"ResourceType","Value":"{resourceType}","Operator":"equals"} HTTP/1.1</span></span>      |

### <a name="uri-parameter"></a><span data-ttu-id="a9710-144">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="a9710-144">URI parameter</span></span>

<span data-ttu-id="a9710-145">Gebruik de volgende queryparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="a9710-145">Use the following query parameters when creating the request.</span></span>

| <span data-ttu-id="a9710-146">Naam</span><span class="sxs-lookup"><span data-stu-id="a9710-146">Name</span></span>      | <span data-ttu-id="a9710-147">Type</span><span class="sxs-lookup"><span data-stu-id="a9710-147">Type</span></span>   | <span data-ttu-id="a9710-148">Vereist</span><span class="sxs-lookup"><span data-stu-id="a9710-148">Required</span></span> | <span data-ttu-id="a9710-149">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a9710-149">Description</span></span>                                                                                                                                                                                                                |
|-----------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a9710-150">Startdate</span><span class="sxs-lookup"><span data-stu-id="a9710-150">startDate</span></span> | <span data-ttu-id="a9710-151">date</span><span class="sxs-lookup"><span data-stu-id="a9710-151">date</span></span>   | <span data-ttu-id="a9710-152">Nee</span><span class="sxs-lookup"><span data-stu-id="a9710-152">No</span></span>       | <span data-ttu-id="a9710-153">De begindatum in de indeling yyyy-mm-dd.</span><span class="sxs-lookup"><span data-stu-id="a9710-153">The start date in yyyy-mm-dd format.</span></span> <span data-ttu-id="a9710-154">Als er geen is opgegeven, wordt de resultatenset standaard ingesteld op 30 dagen vóór de aanvraagdatum.</span><span class="sxs-lookup"><span data-stu-id="a9710-154">If none is provided, the result set will default to 30 days prior to the request date.</span></span> <span data-ttu-id="a9710-155">Deze parameter is optioneel wanneer een filter wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a9710-155">This parameter is optional when a filter is supplied.</span></span>                                          |
| <span data-ttu-id="a9710-156">Enddate</span><span class="sxs-lookup"><span data-stu-id="a9710-156">endDate</span></span>   | <span data-ttu-id="a9710-157">date</span><span class="sxs-lookup"><span data-stu-id="a9710-157">date</span></span>   | <span data-ttu-id="a9710-158">Nee</span><span class="sxs-lookup"><span data-stu-id="a9710-158">No</span></span>       | <span data-ttu-id="a9710-159">De einddatum in de indeling yyyy-mm-dd.</span><span class="sxs-lookup"><span data-stu-id="a9710-159">The end date in yyyy-mm-dd format.</span></span> <span data-ttu-id="a9710-160">Deze parameter is optioneel wanneer een filter wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a9710-160">This parameter is optional when a filter is supplied.</span></span> <span data-ttu-id="a9710-161">Wanneer de einddatum wordt weggelaten of ingesteld op null, retourneert de aanvraag het maximumvenster of gebruikt vandaag als de einddatum, wat kleiner is.</span><span class="sxs-lookup"><span data-stu-id="a9710-161">When the end date is omitted or set to null, the request returns the max window or uses today as the end date, whichever is less.</span></span> |
| <span data-ttu-id="a9710-162">filter</span><span class="sxs-lookup"><span data-stu-id="a9710-162">filter</span></span>    | <span data-ttu-id="a9710-163">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="a9710-163">string</span></span> | <span data-ttu-id="a9710-164">No</span><span class="sxs-lookup"><span data-stu-id="a9710-164">No</span></span>       | <span data-ttu-id="a9710-165">Het filter dat moet worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="a9710-165">The filter to apply.</span></span> <span data-ttu-id="a9710-166">Deze parameter moet een gecodeerde tekenreeks zijn.</span><span class="sxs-lookup"><span data-stu-id="a9710-166">This parameter must be an encoded string.</span></span> <span data-ttu-id="a9710-167">Deze parameter is optioneel wanneer de begindatum of einddatum wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="a9710-167">This parameter is optional when the start date or end date are supplied.</span></span>                                                                                              |

### <a name="filter-syntax"></a><span data-ttu-id="a9710-168">Filtersyntaxis</span><span class="sxs-lookup"><span data-stu-id="a9710-168">Filter syntax</span></span>
<span data-ttu-id="a9710-169">U moet de filterparameter opstellen als een reeks door komma's gescheiden sleutel-waardeparen.</span><span class="sxs-lookup"><span data-stu-id="a9710-169">You must compose the filter parameter as a series of comma separated, key-value pairs.</span></span> <span data-ttu-id="a9710-170">Elke sleutel en waarde moeten afzonderlijk worden aangehaald en gescheiden door een dubbele punt.</span><span class="sxs-lookup"><span data-stu-id="a9710-170">Each key and value must be individually quoted and separated by a colon.</span></span> <span data-ttu-id="a9710-171">Het hele filter moet worden gecodeerd.</span><span class="sxs-lookup"><span data-stu-id="a9710-171">The entire filter must be encoded.</span></span>

<span data-ttu-id="a9710-172">Een niet-gecodeerd voorbeeld ziet er als volgende uit:</span><span class="sxs-lookup"><span data-stu-id="a9710-172">An unencoded example looks like this:</span></span>

```
?filter{"Field":"CompanyName","Value":"bri","Operator":"substring"}
```

<span data-ttu-id="a9710-173">In de volgende tabel worden de vereiste sleutel-waardeparen beschreven:</span><span class="sxs-lookup"><span data-stu-id="a9710-173">The following table describes the required key-value pairs:</span></span>

| <span data-ttu-id="a9710-174">Sleutel</span><span class="sxs-lookup"><span data-stu-id="a9710-174">Key</span></span>                 | <span data-ttu-id="a9710-175">Waarde</span><span class="sxs-lookup"><span data-stu-id="a9710-175">Value</span></span>                             |
|:--------------------|:----------------------------------|
| <span data-ttu-id="a9710-176">Veld</span><span class="sxs-lookup"><span data-stu-id="a9710-176">Field</span></span>               | <span data-ttu-id="a9710-177">Het veld dat moet worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="a9710-177">The field to filter.</span></span> <span data-ttu-id="a9710-178">De ondersteunde waarden vindt u in [Aanvraagsyntaxis.](get-a-record-of-partner-center-activity-by-user.md#rest-request)</span><span class="sxs-lookup"><span data-stu-id="a9710-178">The supported values can be found in [Request syntax](get-a-record-of-partner-center-activity-by-user.md#rest-request).</span></span>                                         |
| <span data-ttu-id="a9710-179">Waarde</span><span class="sxs-lookup"><span data-stu-id="a9710-179">Value</span></span>               | <span data-ttu-id="a9710-180">De waarde die moet worden gefilterd op.</span><span class="sxs-lookup"><span data-stu-id="a9710-180">The value to filter by.</span></span> <span data-ttu-id="a9710-181">Het geval van de waarde wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="a9710-181">The case of the value is ignored.</span></span> <span data-ttu-id="a9710-182">De volgende waardeparameters worden ondersteund, zoals wordt weergegeven in [Aanvraagsyntaxis:](get-a-record-of-partner-center-activity-by-user.md#rest-request)</span><span class="sxs-lookup"><span data-stu-id="a9710-182">The following value parameters are supported as shown in [Request syntax](get-a-record-of-partner-center-activity-by-user.md#rest-request):</span></span><br/><br/>                                                                <span data-ttu-id="a9710-183">*searchSubstring:* vervang door de naam van het bedrijf.</span><span class="sxs-lookup"><span data-stu-id="a9710-183">*searchSubstring* - Replace with the name of the company.</span></span> <span data-ttu-id="a9710-184">U kunt een subtekenreeks invoeren die overeen komt met een deel van de bedrijfsnaam (komt bijvoorbeeld `bri` overeen met `Fabrikam, Inc` ).</span><span class="sxs-lookup"><span data-stu-id="a9710-184">You can enter a substring to match part of the company name (for example, `bri` will match `Fabrikam, Inc`).</span></span><br/><span data-ttu-id="a9710-185">**Voorbeeld:**`"Value":"bri"`</span><span class="sxs-lookup"><span data-stu-id="a9710-185">**Example:** `"Value":"bri"`</span></span><br/><br/>                                                                <span data-ttu-id="a9710-186">*customerId:* vervang door een tekenreeks met GUID-indeling die de klant-id vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="a9710-186">*customerId* - Replace with a GUID formatted string that represents the customer identifier.</span></span><br/><span data-ttu-id="a9710-187">**Voorbeeld:**`"Value":"0c39d6d5-c70d-4c55-bc02-f620844f3fd1"`</span><span class="sxs-lookup"><span data-stu-id="a9710-187">**Example:** `"Value":"0c39d6d5-c70d-4c55-bc02-f620844f3fd1"`</span></span><br/><br/>                                                                                        <span data-ttu-id="a9710-188">*resourceType:* vervang door het type resource waarvoor controlerecords moeten worden opgehaald (bijvoorbeeld Abonnement).</span><span class="sxs-lookup"><span data-stu-id="a9710-188">*resourceType* - Replace with the type of resource for which to retrieve audit records (for example, Subscription).</span></span> <span data-ttu-id="a9710-189">De beschikbare resourcetypen worden gedefinieerd in [ResourceType](/dotnet/api/microsoft.store.partnercenter.models.auditing.resourcetype).</span><span class="sxs-lookup"><span data-stu-id="a9710-189">The available resource types are defined in [ResourceType](/dotnet/api/microsoft.store.partnercenter.models.auditing.resourcetype).</span></span><br/><span data-ttu-id="a9710-190">**Voorbeeld:**`"Value":"Subscription"`</span><span class="sxs-lookup"><span data-stu-id="a9710-190">**Example:** `"Value":"Subscription"`</span></span>                                 |
| <span data-ttu-id="a9710-191">Operator</span><span class="sxs-lookup"><span data-stu-id="a9710-191">Operator</span></span>          | <span data-ttu-id="a9710-192">De operator die moet worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="a9710-192">The operator to apply.</span></span> <span data-ttu-id="a9710-193">De ondersteunde operators vindt u in [Aanvraagsyntaxis.](get-a-record-of-partner-center-activity-by-user.md#rest-request)</span><span class="sxs-lookup"><span data-stu-id="a9710-193">The supported operators can be found in [Request syntax](get-a-record-of-partner-center-activity-by-user.md#rest-request).</span></span>   |

### <a name="request-headers"></a><span data-ttu-id="a9710-194">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="a9710-194">Request headers</span></span>

- <span data-ttu-id="a9710-195">Zie [Parter Center REST-headers voor meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="a9710-195">For more information, see [Parter Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a9710-196">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="a9710-196">Request body</span></span>

<span data-ttu-id="a9710-197">Geen.</span><span class="sxs-lookup"><span data-stu-id="a9710-197">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="a9710-198">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="a9710-198">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/auditrecords?startDate=6/1/2017%2012:00:00%20AM&filter=%7B%22Field%22:%22CustomerId%22,%22Value%22:%220c39d6d5-c70d-4c55-bc02-f620844f3fd1%22,%22Operator%22:%22equals%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 127facaa-e389-41f8-8bb7-1d1af99db893
MS-CorrelationId: de9c2ccc-40dd-4186-9660-65b9b64c3d14
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="a9710-199">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="a9710-199">REST response</span></span>

<span data-ttu-id="a9710-200">Als dit lukt, retourneert deze methode een reeks activiteiten die voldoen aan de filters.</span><span class="sxs-lookup"><span data-stu-id="a9710-200">If successful, this method returns a set of activities that meet the filters.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a9710-201">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="a9710-201">Response success and error codes</span></span>

<span data-ttu-id="a9710-202">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="a9710-202">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a9710-203">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="a9710-203">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a9710-204">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="a9710-204">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="a9710-205">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="a9710-205">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2859
Content-Type: application/json; charset=utf-8
MS-CorrelationId: de9c2ccc-40dd-4186-9660-65b9b64c3d14
MS-RequestId: 127facaa-e389-41f8-8bb7-1d1af99db893
MS-CV: 4xDKynq/zE2im0wj.0
MS-ServerId: 030011719
Date: Tue, 27 Jun 2017 22:19:46 GMT

{
    "totalCount": 2,
    "items": [{
            "partnerId": "3b33e682-00c3-41ee-9dd2-a548adf56438",
            "customerId": "0c39d6d5-c70d-4c55-bc02-f620844f3fd1",
            "customerName": "Relecloud",
            "userPrincipalName": "admin@domain.onmicrosoft.com",
            "resourceType": "order",
            "resourceNewValue": "{\"Id\":\"d51a052e-043c-4a2a-aa37-2bb938cef6c1\",\"ReferenceCustomerId\":\"0c39d6d5-c70d-4c55-bc02-f620844f3fd1\",\"BillingCycle\":\"none\",\"LineItems\":[{\"LineItemNumber\":0,\"OfferId\":\"C0BD2E08-11AC-4836-BDC7-3712E744922F\",\"SubscriptionId\":\"488745B5-2086-4912-802C-6ABB9F7C3638\",\"ParentSubscriptionId\":null,\"FriendlyName\":\"Office 365 Business Premium Trial\",\"Quantity\":25,\"PartnerIdOnRecord\":null,\"Links\":{\"Subscription\":{\"Uri\":\"/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/488745B5-2086-4912-802C-6ABB9F7C3638\",\"Method\":\"GET\",\"Headers\":[]}}}],\"CreationDate\":\"2017-06-15T15:56:04.077-07:00\",\"Links\":{\"Self\":{\"Uri\":\"/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/orders/d51a052e-043c-4a2a-aa37-2bb938cef6c1\",\"Method\":\"GET\",\"Headers\":[]}},\"Attributes\":{\"Etag\":\"eyJpZCI6ImQ1MWEwNTJlLTA0M2MtNGEyYS1hYTM3LTJiYjkzOGNlZjZjMSIsInZlcnNpb24iOjF9\",\"ObjectType\":\"Order\"}}",
            "operationType": "create_order",
            "operationDate": "2017-06-15T22:56:05.0589308Z",
            "operationStatus": "succeeded",
            "customizedData": [{
                    "key": "OrderId",
                    "value": "d51a052e-043c-4a2a-aa37-2bb938cef6c1"
                }, {
                    "key": "BillingCycle",
                    "value": "None"
                }, {
                    "key": "OfferId-0",
                    "value": "C0BD2E08-11AC-4836-BDC7-3712E744922F"
                }, {
                    "key": "SubscriptionId-0",
                    "value": "488745B5-2086-4912-802C-6ABB9F7C3638"
                }, {
                    "key": "SubscriptionName-0",
                    "value": "Office 365 Business Premium Trial"
                }, {
                    "key": "Quantity-0",
                    "value": "25"
                }, {
                    "key": "PartnerOnRecord-0",
                    "value": null
                }
            ],
            "attributes": {
                "objectType": "AuditRecord"
            }
        }, {
            "partnerId": "3b33e682-00c3-41ee-9dd2-a548adf56438",
            "customerId": "0c39d6d5-c70d-4c55-bc02-f620844f3fd1",
            "customerName": "Relecloud",
            "userPrincipalName": "admin@domain.onmicrosoft.com",
            "applicationId": "Partner Center Native App",
            "resourceType": "license",
            "resourceNewValue": "{\"LicensesToAssign\":[{\"ExcludedPlans\":null,\"SkuId\":\"efccb6f7-5641-4e0e-bd10-b4976e1bf68e\"}],\"LicensesToRemove\":null,\"LicenseWarnings\":[],\"Attributes\":{\"ObjectType\":\"LicenseUpdate\"}}",
            "operationType": "update_customer_user_licenses",
            "operationDate": "2017-06-01T20:09:07.0450483Z",
            "operationStatus": "succeeded",
            "customizedData": [{
                    "key": "CustomerUserId",
                    "value": "482e2152-4b49-48ec-b715-823365ce3d4c"
                }, {
                    "key": "AddedLicenseSkuId",
                    "value": "efccb6f7-5641-4e0e-bd10-b4976e1bf68e"
                }
            ],
            "attributes": {
                "objectType": "AuditRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/auditrecords?startDate=2017-06-01&size=500&filter=%7B%22Field%22%3A%22CustomerId%22%2C%22Value%22%3A%220c39d6d5-c70d-4c55-bc02-f620844f3fd1%22%2C%22Operator%22%3A%22equals%22%7D",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```