---
title: Een record van Partnercentrum-activiteiten ophalen
description: Het ophalen van een record van bewerkingen, zoals uitgevoerd door een partner gebruiker of toepassing, gedurende een bepaalde periode.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 2f37eae8bb96c1c1e7008e8c566b085e25d8807d
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767438"
---
# <a name="get-a-record-of-partner-center-activity"></a><span data-ttu-id="ac8f0-103">Een record van Partnercentrum-activiteiten ophalen</span><span class="sxs-lookup"><span data-stu-id="ac8f0-103">Get a record of Partner Center activity</span></span>

<span data-ttu-id="ac8f0-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="ac8f0-104">**Applies To**</span></span>

- <span data-ttu-id="ac8f0-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="ac8f0-105">Partner Center</span></span>
- <span data-ttu-id="ac8f0-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="ac8f0-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="ac8f0-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="ac8f0-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="ac8f0-108">In dit artikel wordt beschreven hoe u een record kunt ophalen van bewerkingen die gedurende een bepaalde periode zijn uitgevoerd door een partner gebruiker of-toepassing.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-108">This article describes how to retrieve a record of operations that was performed by a partner user or application over a period of time.</span></span>

<span data-ttu-id="ac8f0-109">Gebruik deze API om controle records op te halen voor de afgelopen 30 dagen vanaf de huidige datum of voor een datum bereik dat is opgegeven met inbegrip van de begin datum en/of de eind datum.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-109">Use this API to retrieve audit records for the previous 30 days from the current date, or for a date range specified by including the start date and/or the end date.</span></span> <span data-ttu-id="ac8f0-110">Houd er echter rekening mee dat de beschik baarheid van het activiteiten logboek voor de prestaties beperkt is tot de vorige 90 dagen.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-110">Note, however, that for performance reasons activity log data availability is limited to the previous 90 days.</span></span> <span data-ttu-id="ac8f0-111">Aanvragen met een begin datum die groter is dan 90 dagen vóór de huidige datum worden een ongeldige aanvraag uitzondering ontvangen (fout code: 400) en een geschikt bericht.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-111">Requests with a start date greater than 90 days prior to the current date will receive a bad request exception (error code: 400) and an appropriate message.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ac8f0-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ac8f0-112">Prerequisites</span></span>

- <span data-ttu-id="ac8f0-113">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ac8f0-113">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ac8f0-114">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-114">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="ac8f0-115">C\#</span><span class="sxs-lookup"><span data-stu-id="ac8f0-115">C\#</span></span>

<span data-ttu-id="ac8f0-116">Als u een record van partner Center-bewerkingen wilt ophalen, moet u eerst het datum bereik instellen voor de records die u wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-116">To retrieve a record of Partner Center operations, first establish the date range for the records you want to retrieve.</span></span> <span data-ttu-id="ac8f0-117">In het volgende code voorbeeld wordt alleen een begin datum gebruikt, maar u kunt ook een eind datum toevoegen.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-117">The following code example only uses a start date, but you can also include an end date.</span></span> <span data-ttu-id="ac8f0-118">Zie de [**query**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) methode voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-118">For more information, see the [**Query**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) method.</span></span> <span data-ttu-id="ac8f0-119">Maak vervolgens de variabelen die u nodig hebt voor het type filter dat u wilt Toep assen en wijs de juiste waarden toe.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-119">Next, create the variables you need for the type of filter you want to apply, and assign the appropriate values.</span></span> <span data-ttu-id="ac8f0-120">Als u bijvoorbeeld wilt filteren op subtekenreeks bedrijfs naam, maakt u een variabele voor de subtekenreeks.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-120">For example, to filter by company name substring, create a variable to hold the substring.</span></span> <span data-ttu-id="ac8f0-121">Als u wilt filteren op klant-ID, maakt u een variabele om de ID op te slaan.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-121">To filter by customer ID, create a variable to hold the ID.</span></span>

<span data-ttu-id="ac8f0-122">In het volgende voor beeld wordt de voorbeeld code verschaft om te filteren op een subtekenreeks van een bedrijfs naam, een klant-ID of een resource type.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-122">In the following example, sample code is provided to filter by a company name substring, customer ID, or resource type.</span></span> <span data-ttu-id="ac8f0-123">U kunt een opmerking kiezen en de andere opmerkingen toevoegen.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-123">Choose one and comment out the others.</span></span> <span data-ttu-id="ac8f0-124">In elk geval maakt u eerst een [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) -object met behulp van de standaard [**constructor**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter.-ctor) om het filter te maken.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-124">In each case, you first instantiate a [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) object using its default [**constructor**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter.-ctor) to create the filter.</span></span> <span data-ttu-id="ac8f0-125">U moet een teken reeks door geven die het veld bevat waarop moet worden gezocht en de toepasselijke operator die u wilt Toep assen, zoals wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-125">You'll need to pass a string that contains the field to search, and the appropriate operator to apply, as shown.</span></span> <span data-ttu-id="ac8f0-126">U moet ook de teken reeks opgeven waarop moet worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-126">You also must provide the string to filter by.</span></span>

<span data-ttu-id="ac8f0-127">Gebruik vervolgens de eigenschap [**AuditRecords**](/dotnet/api/microsoft.store.partnercenter.ipartner.auditrecords) om een interface op te halen voor het controleren van record bewerkingen en roep de methode [**query**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) of [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.queryasync) aan om het filter uit te voeren en de verzameling van [**AuditRecord**](/dotnet/api/microsoft.store.partnercenter.models.auditing.auditrecord) te verkrijgen die de eerste pagina van het resultaat voor stelt.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-127">Next, use the [**AuditRecords**](/dotnet/api/microsoft.store.partnercenter.ipartner.auditrecords) property to get an interface to audit record operations, and call the [**Query**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.query) or [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.auditrecords.iauditrecordscollection.queryasync) method to execute the filter and get the collection of [**AuditRecord's**](/dotnet/api/microsoft.store.partnercenter.models.auditing.auditrecord) that represent the first page of the result.</span></span> <span data-ttu-id="ac8f0-128">Geef de methode de start datum, een optionele eind datum die niet in het voor beeld wordt gebruikt en een [**IQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) -object dat een query op een entiteit vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-128">Pass the method the start date, an optional end date not used in the example here, and an [**IQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) object that represents a query on an entity.</span></span> <span data-ttu-id="ac8f0-129">Het IQuery-object wordt gemaakt door het hierboven gemaakte filter door te geven aan de [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) -methode [**van QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) .</span><span class="sxs-lookup"><span data-stu-id="ac8f0-129">The IQuery object is created by passing the filter created above to the [**QueryFactory's**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) method.</span></span>

<span data-ttu-id="ac8f0-130">Wanneer u de eerste pagina van de items hebt, gebruikt u de methode [**enumerats. AuditRecords. Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) om een enumerator te maken die u kunt gebruiken om de resterende pagina's te herhalen.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-130">Once you have the initial page of items, use the [**Enumerators.AuditRecords.Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create) method to create an enumerator that you can use to iterate through the remaining pages.</span></span>

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

<span data-ttu-id="ac8f0-131">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="ac8f0-131">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="ac8f0-132">**Project**: Partner Center SDK-voor beelden **map**: controleren</span><span class="sxs-lookup"><span data-stu-id="ac8f0-132">**Project**: Partner Center SDK Samples **Folder**: Auditing</span></span>

## <a name="rest-request"></a><span data-ttu-id="ac8f0-133">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="ac8f0-133">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ac8f0-134">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ac8f0-134">Request syntax</span></span>

| <span data-ttu-id="ac8f0-135">Methode</span><span class="sxs-lookup"><span data-stu-id="ac8f0-135">Method</span></span>  | <span data-ttu-id="ac8f0-136">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="ac8f0-136">Request URI</span></span>                                                                                                                                                                                    |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ac8f0-137">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ac8f0-137">**GET**</span></span> | <span data-ttu-id="ac8f0-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords? start date = {start date} http/1.1</span><span class="sxs-lookup"><span data-stu-id="ac8f0-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate} HTTP/1.1</span></span>                                                                                                     |
| <span data-ttu-id="ac8f0-139">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ac8f0-139">**GET**</span></span> | <span data-ttu-id="ac8f0-140">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords? start date = {start date} &EndDate = {ENDDATE} http/1.1</span><span class="sxs-lookup"><span data-stu-id="ac8f0-140">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate} HTTP/1.1</span></span>                                                                                   |
| <span data-ttu-id="ac8f0-141">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ac8f0-141">**GET**</span></span> | <span data-ttu-id="ac8f0-142">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords? start date = {start date} &EndDate = {endDate} &filter = {"veld:" CompanyName "," waarde ":" {searchSubstring} "," operator ":" subtekenreeks "} http/1.1</span><span class="sxs-lookup"><span data-stu-id="ac8f0-142">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"CompanyName","Value":"{searchSubstring}","Operator":"substring"} HTTP/1.1</span></span> |
| <span data-ttu-id="ac8f0-143">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ac8f0-143">**GET**</span></span> | <span data-ttu-id="ac8f0-144">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords? start date = {start date} &EndDate = {endDate} &filter = {"veld": "KlantId", "waarde": "{KlantId}", "operator": "is gelijk aan"} http/1.1</span><span class="sxs-lookup"><span data-stu-id="ac8f0-144">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"CustomerId","Value":"{customerId}","Operator":"equals"} HTTP/1.1</span></span>          |
| <span data-ttu-id="ac8f0-145">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ac8f0-145">**GET**</span></span> | <span data-ttu-id="ac8f0-146">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords? start date = {start date} &EndDate = {endDate} &filter = {"veld:" resource type "," waarde ":" {resource type} "," operator ":" is gelijk aan "} http/1.1</span><span class="sxs-lookup"><span data-stu-id="ac8f0-146">[*{baseURL}*](partner-center-rest-urls.md)/v1/auditrecords?startDate={startDate}&endDate={endDate}&filter={"Field":"ResourceType","Value":"{resourceType}","Operator":"equals"} HTTP/1.1</span></span>      |

### <a name="uri-parameter"></a><span data-ttu-id="ac8f0-147">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="ac8f0-147">URI parameter</span></span>

<span data-ttu-id="ac8f0-148">Gebruik de volgende query parameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-148">Use the following query parameters when creating the request.</span></span>

| <span data-ttu-id="ac8f0-149">Naam</span><span class="sxs-lookup"><span data-stu-id="ac8f0-149">Name</span></span>      | <span data-ttu-id="ac8f0-150">Type</span><span class="sxs-lookup"><span data-stu-id="ac8f0-150">Type</span></span>   | <span data-ttu-id="ac8f0-151">Vereist</span><span class="sxs-lookup"><span data-stu-id="ac8f0-151">Required</span></span> | <span data-ttu-id="ac8f0-152">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ac8f0-152">Description</span></span>                                                                                                                                                                                                                |
|-----------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ac8f0-153">Begin</span><span class="sxs-lookup"><span data-stu-id="ac8f0-153">startDate</span></span> | <span data-ttu-id="ac8f0-154">date</span><span class="sxs-lookup"><span data-stu-id="ac8f0-154">date</span></span>   | <span data-ttu-id="ac8f0-155">No</span><span class="sxs-lookup"><span data-stu-id="ac8f0-155">No</span></span>       | <span data-ttu-id="ac8f0-156">De begin datum in de indeling jjjj-mm-dd.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-156">The start date in yyyy-mm-dd format.</span></span> <span data-ttu-id="ac8f0-157">Als er geen is opgegeven, wordt de resultatenset standaard ingesteld op 30 dagen vóór de aanvraag datum.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-157">If none is provided, the result set will default to 30 days prior to the request date.</span></span> <span data-ttu-id="ac8f0-158">Deze para meter is optioneel wanneer een filter wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-158">This parameter is optional when a filter is supplied.</span></span>                                          |
| <span data-ttu-id="ac8f0-159">endDate</span><span class="sxs-lookup"><span data-stu-id="ac8f0-159">endDate</span></span>   | <span data-ttu-id="ac8f0-160">date</span><span class="sxs-lookup"><span data-stu-id="ac8f0-160">date</span></span>   | <span data-ttu-id="ac8f0-161">No</span><span class="sxs-lookup"><span data-stu-id="ac8f0-161">No</span></span>       | <span data-ttu-id="ac8f0-162">De eind datum in de indeling jjjj-mm-dd.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-162">The end date in yyyy-mm-dd format.</span></span> <span data-ttu-id="ac8f0-163">Deze para meter is optioneel wanneer een filter wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-163">This parameter is optional when a filter is supplied.</span></span> <span data-ttu-id="ac8f0-164">Wanneer de eind datum wordt wegge laten of op NULL wordt ingesteld, retourneert de aanvraag het maximum venster of wordt het vandaag als eind datum gebruikt, afhankelijk van wat kleiner is.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-164">When the end date is omitted or set to null, the request returns the max window or uses today as the end date, whichever is less.</span></span> |
| <span data-ttu-id="ac8f0-165">filter</span><span class="sxs-lookup"><span data-stu-id="ac8f0-165">filter</span></span>    | <span data-ttu-id="ac8f0-166">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ac8f0-166">string</span></span> | <span data-ttu-id="ac8f0-167">No</span><span class="sxs-lookup"><span data-stu-id="ac8f0-167">No</span></span>       | <span data-ttu-id="ac8f0-168">Het filter dat moet worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-168">The filter to apply.</span></span> <span data-ttu-id="ac8f0-169">Deze para meter moet een gecodeerde teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-169">This parameter must be an encoded string.</span></span> <span data-ttu-id="ac8f0-170">Deze para meter is optioneel wanneer de begin-of eind datum wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-170">This parameter is optional when the start date or end date are supplied.</span></span>                                                                                              |

### <a name="filter-syntax"></a><span data-ttu-id="ac8f0-171">Filter syntaxis</span><span class="sxs-lookup"><span data-stu-id="ac8f0-171">Filter syntax</span></span>
<span data-ttu-id="ac8f0-172">U moet de filter parameter opstellen als een reeks door komma's gescheiden, sleutel-waardeparen.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-172">You must compose the filter parameter as a series of comma separated, key-value pairs.</span></span> <span data-ttu-id="ac8f0-173">Elke sleutel en waarde moeten afzonderlijk worden genoteerd en gescheiden door een dubbele punt.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-173">Each key and value must be individually quoted and separated by a colon.</span></span> <span data-ttu-id="ac8f0-174">Het volledige filter moet zijn gecodeerd.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-174">The entire filter must be encoded.</span></span>

<span data-ttu-id="ac8f0-175">Een niet-gecodeerd voor beeld ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="ac8f0-175">An unencoded example looks like this:</span></span>

```
?filter{"Field":"CompanyName","Value":"bri","Operator":"substring"}
```

<span data-ttu-id="ac8f0-176">In de volgende tabel worden de vereiste sleutel-waardeparen beschreven:</span><span class="sxs-lookup"><span data-stu-id="ac8f0-176">The following table describes the required key-value pairs:</span></span>

| <span data-ttu-id="ac8f0-177">Sleutel</span><span class="sxs-lookup"><span data-stu-id="ac8f0-177">Key</span></span>                 | <span data-ttu-id="ac8f0-178">Waarde</span><span class="sxs-lookup"><span data-stu-id="ac8f0-178">Value</span></span>                             |
|:--------------------|:----------------------------------|
| <span data-ttu-id="ac8f0-179">Veld</span><span class="sxs-lookup"><span data-stu-id="ac8f0-179">Field</span></span>               | <span data-ttu-id="ac8f0-180">Het veld dat moet worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-180">The field to filter.</span></span> <span data-ttu-id="ac8f0-181">De ondersteunde waarden zijn te vinden in de [aanvraag syntaxis](get-a-record-of-partner-center-activity-by-user.md#rest-request).</span><span class="sxs-lookup"><span data-stu-id="ac8f0-181">The supported values can be found in [Request syntax](get-a-record-of-partner-center-activity-by-user.md#rest-request).</span></span>                                         |
| <span data-ttu-id="ac8f0-182">Waarde</span><span class="sxs-lookup"><span data-stu-id="ac8f0-182">Value</span></span>               | <span data-ttu-id="ac8f0-183">De waarde waarop moet worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-183">The value to filter by.</span></span> <span data-ttu-id="ac8f0-184">Het geval van de waarde wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-184">The case of the value is ignored.</span></span> <span data-ttu-id="ac8f0-185">De volgende waarde-para meters worden ondersteund, zoals wordt weer gegeven in de [aanvraag syntaxis](get-a-record-of-partner-center-activity-by-user.md#rest-request):</span><span class="sxs-lookup"><span data-stu-id="ac8f0-185">The following value parameters are supported as shown in [Request syntax](get-a-record-of-partner-center-activity-by-user.md#rest-request):</span></span><br/><br/>                                                                <span data-ttu-id="ac8f0-186">*searchSubstring* : Vervang door de naam van het bedrijf.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-186">*searchSubstring* - Replace with the name of the company.</span></span> <span data-ttu-id="ac8f0-187">U kunt een subtekenreeks invoeren die overeenkomt met een deel van de bedrijfs naam (bijvoorbeeld komt `bri` overeen met `Fabrikam, Inc` ).</span><span class="sxs-lookup"><span data-stu-id="ac8f0-187">You can enter a substring to match part of the company name (for example, `bri` will match `Fabrikam, Inc`).</span></span><br/><span data-ttu-id="ac8f0-188">**Voor beeld:**`"Value":"bri"`</span><span class="sxs-lookup"><span data-stu-id="ac8f0-188">**Example:** `"Value":"bri"`</span></span><br/><br/>                                                                <span data-ttu-id="ac8f0-189">*KlantId* -vervangen door een teken reeks met een GUID-indeling die de klant-id vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-189">*customerId* - Replace with a GUID formatted string that represents the customer identifier.</span></span><br/><span data-ttu-id="ac8f0-190">**Voor beeld:**`"Value":"0c39d6d5-c70d-4c55-bc02-f620844f3fd1"`</span><span class="sxs-lookup"><span data-stu-id="ac8f0-190">**Example:** `"Value":"0c39d6d5-c70d-4c55-bc02-f620844f3fd1"`</span></span><br/><br/>                                                                                        <span data-ttu-id="ac8f0-191">*resource* type: Vervang door het type resource waarvoor controle records moeten worden opgehaald (bijvoorbeeld abonnement).</span><span class="sxs-lookup"><span data-stu-id="ac8f0-191">*resourceType* - Replace with the type of resource for which to retrieve audit records (for example, Subscription).</span></span> <span data-ttu-id="ac8f0-192">De beschik bare resource typen worden gedefinieerd in [resource type](/dotnet/api/microsoft.store.partnercenter.models.auditing.resourcetype).</span><span class="sxs-lookup"><span data-stu-id="ac8f0-192">The available resource types are defined in [ResourceType](/dotnet/api/microsoft.store.partnercenter.models.auditing.resourcetype).</span></span><br/><span data-ttu-id="ac8f0-193">**Voor beeld:**`"Value":"Subscription"`</span><span class="sxs-lookup"><span data-stu-id="ac8f0-193">**Example:** `"Value":"Subscription"`</span></span>                                 |
| <span data-ttu-id="ac8f0-194">Operator</span><span class="sxs-lookup"><span data-stu-id="ac8f0-194">Operator</span></span>          | <span data-ttu-id="ac8f0-195">De operator die moet worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-195">The operator to apply.</span></span> <span data-ttu-id="ac8f0-196">De ondersteunde Opera tors zijn te vinden in de [aanvraag syntaxis](get-a-record-of-partner-center-activity-by-user.md#rest-request).</span><span class="sxs-lookup"><span data-stu-id="ac8f0-196">The supported operators can be found in [Request syntax](get-a-record-of-partner-center-activity-by-user.md#rest-request).</span></span>   |

### <a name="request-headers"></a><span data-ttu-id="ac8f0-197">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ac8f0-197">Request headers</span></span>

- <span data-ttu-id="ac8f0-198">Zie [rest-headers Centers](headers.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-198">See [Parter Center REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="ac8f0-199">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="ac8f0-199">Request body</span></span>

<span data-ttu-id="ac8f0-200">Geen.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-200">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="ac8f0-201">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ac8f0-201">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="ac8f0-202">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="ac8f0-202">REST response</span></span>

<span data-ttu-id="ac8f0-203">Als dit lukt, retourneert deze methode een set activiteiten die aan de filters voldoen.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-203">If successful, this method returns a set of activities that meet the filters.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ac8f0-204">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="ac8f0-204">Response success and error codes</span></span>

<span data-ttu-id="ac8f0-205">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-205">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ac8f0-206">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-206">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ac8f0-207">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="ac8f0-207">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ac8f0-208">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="ac8f0-208">Response example</span></span>

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