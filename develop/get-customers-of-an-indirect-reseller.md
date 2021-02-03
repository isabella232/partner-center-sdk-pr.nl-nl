---
title: Klanten van een indirecte reseller ophalen
description: Een lijst met klanten van een indirecte wederverkoper ophalen.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: e4219f544a74bb3f34ec3aefe08cf18eed77fd42
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767490"
---
# <a name="get-customers-of-an-indirect-reseller"></a><span data-ttu-id="24c42-103">Klanten van een indirecte reseller ophalen</span><span class="sxs-lookup"><span data-stu-id="24c42-103">Get customers of an indirect reseller</span></span>

<span data-ttu-id="24c42-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="24c42-104">**Applies To**</span></span>

- <span data-ttu-id="24c42-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="24c42-105">Partner Center</span></span>

<span data-ttu-id="24c42-106">Een lijst met klanten van een indirecte wederverkoper ophalen.</span><span class="sxs-lookup"><span data-stu-id="24c42-106">How to get a list of the customers of an indirect reseller.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="24c42-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="24c42-107">Prerequisites</span></span>

- <span data-ttu-id="24c42-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="24c42-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="24c42-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="24c42-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="24c42-110">De Tenant-id van de indirecte wederverkoper.</span><span class="sxs-lookup"><span data-stu-id="24c42-110">The tenant identifier of the indirect reseller.</span></span>

## <a name="c"></a><span data-ttu-id="24c42-111">C\#</span><span class="sxs-lookup"><span data-stu-id="24c42-111">C\#</span></span>

<span data-ttu-id="24c42-112">Als u een verzameling klanten wilt ophalen die een relatie hebben met de opgegeven indirecte wederverkoper, moet u eerst een [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) -object instantiëren om het filter te maken.</span><span class="sxs-lookup"><span data-stu-id="24c42-112">To get a collection of customers that have a relationship with the specified indirect reseller, first instantiate a [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) object to create the filter.</span></span> <span data-ttu-id="24c42-113">U moet het [**CustomerSearchField. IndirectReseller**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield) -opsommings onderdeel dat is geconverteerd naar een teken reeks door geven en [**FieldFilterOperation. StartsWith**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation) aangeven als het type filter bewerking.</span><span class="sxs-lookup"><span data-stu-id="24c42-113">You'll need to pass the [**CustomerSearchField.IndirectReseller**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield) enumeration member converted to a string, and indicate [**FieldFilterOperation.StartsWith**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation) as the type of filter operation.</span></span> <span data-ttu-id="24c42-114">U moet ook de Tenant-id van de indirecte wederverkoper opgeven om te filteren op.</span><span class="sxs-lookup"><span data-stu-id="24c42-114">You'll also need to provide the tenant identifier of the indirect reseller to filter by.</span></span>

<span data-ttu-id="24c42-115">Instantiër vervolgens een [**iQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) -object om door te geven aan de query door de methode [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) aan te roepen en het filter door te geven.</span><span class="sxs-lookup"><span data-stu-id="24c42-115">Next, instantiate an [**iQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) object to pass to the query by calling the [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) method and passing it the filter.</span></span> <span data-ttu-id="24c42-116">BuildSimplyQuery is slechts een van de typen query's die worden ondersteund door de klasse [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) .</span><span class="sxs-lookup"><span data-stu-id="24c42-116">BuildSimplyQuery is just one of the query types supported by the [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) class.</span></span>

<span data-ttu-id="24c42-117">Als u het filter wilt uitvoeren en het resultaat wilt ontvangen, moet u eerst [**IAggregatePartner. klanten**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) gebruiken om een interface te verkrijgen voor de klant activiteiten van de partner.</span><span class="sxs-lookup"><span data-stu-id="24c42-117">To execute the filter and get the result, first use [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) to get an interface to the partner's customer operations.</span></span> <span data-ttu-id="24c42-118">Roep vervolgens de methode [**query**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) of [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) aan.</span><span class="sxs-lookup"><span data-stu-id="24c42-118">Then call the [**Query**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) or [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) method.</span></span>

<span data-ttu-id="24c42-119">Als u een enumerator wilt maken voor het door geven van de resultaten van pagina's, haalt u de Factory-interface van de inventarisatie verzameling van de klant op uit de eigenschap [**IAggregatePartner. inventarisaties. klanten**](/dotnet/api/microsoft.store.partnercenter.enumerators.iresourcecollectionenumeratorcontainer.customers) en roept u [**Create maken**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create)aan, zoals wordt weer gegeven in de onderstaande code, waarbij de variabele wordt door gegeven die de klant verzameling bevat.</span><span class="sxs-lookup"><span data-stu-id="24c42-119">To create an enumerator for traversing paged results, get the customer collection enumerator factory interface from the [**IAggregatePartner.Enumerators.Customers**](/dotnet/api/microsoft.store.partnercenter.enumerators.iresourcecollectionenumeratorcontainer.customers) property, and then call [**Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create), as shown in the code below, passing the variable that holds the customer collection.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string indirectResellerId;

// Create a filter.
var filter = new SimpleFieldFilter(
    CustomerSearchField.IndirectReseller.ToString(),
    FieldFilterOperation.StartsWith,
    indirectResellerId);

// Create an iQuery object to pass to the Query method.
var myQuery = QueryFactory.Instance.BuildSimpleQuery(filter);

// Get the collection of matching customers.
var customersPage = partnerOperations.Customers.Query(myQuery);

// Create a customer enumerator for traversing the customer pages.
var customersEnumerator = partnerOperations.Enumerators.Customers.Create(customersPage);
int pageNumber = 1;

while (customersEnumerator.HasValue)
{
    // Work with the current page.
     foreach (var c in customersEnumerator.Current.Items)
    {
        // Display customer tenant identifier and company name.
        Console.WriteLine(string.Format("{0} - {1}.",c.Id,c.CompanyProfile.CompanyName));
    }
    // Get the next page of customers.
    customersEnumerator.Next();
}
```

<span data-ttu-id="24c42-120">Voor **beeld**: [console test app](console-test-app.md)**project**: Partner Center SDK samples **klasse**: GetCustomersOfIndirectReseller.cs</span><span class="sxs-lookup"><span data-stu-id="24c42-120">**Sample**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: GetCustomersOfIndirectReseller.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="24c42-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="24c42-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="24c42-122">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="24c42-122">Request syntax</span></span>

| <span data-ttu-id="24c42-123">Methode</span><span class="sxs-lookup"><span data-stu-id="24c42-123">Method</span></span>  | <span data-ttu-id="24c42-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="24c42-124">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="24c42-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="24c42-125">**GET**</span></span> | <span data-ttu-id="24c42-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers? grootte = {size}? filter = {filter} http/1.1</span><span class="sxs-lookup"><span data-stu-id="24c42-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size}?filter={filter} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="24c42-127">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="24c42-127">URI parameter</span></span>

<span data-ttu-id="24c42-128">Gebruik de volgende query parameters om de aanvraag te maken.</span><span class="sxs-lookup"><span data-stu-id="24c42-128">Use the following query parameters to create the request.</span></span>

| <span data-ttu-id="24c42-129">Naam</span><span class="sxs-lookup"><span data-stu-id="24c42-129">Name</span></span>   | <span data-ttu-id="24c42-130">Type</span><span class="sxs-lookup"><span data-stu-id="24c42-130">Type</span></span>   | <span data-ttu-id="24c42-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="24c42-131">Required</span></span> | <span data-ttu-id="24c42-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="24c42-132">Description</span></span>                                                                                                                                                                                                                                                                                   |
|--------|--------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="24c42-133">grootte</span><span class="sxs-lookup"><span data-stu-id="24c42-133">size</span></span>   | <span data-ttu-id="24c42-134">int</span><span class="sxs-lookup"><span data-stu-id="24c42-134">int</span></span>    | <span data-ttu-id="24c42-135">No</span><span class="sxs-lookup"><span data-stu-id="24c42-135">No</span></span>       | <span data-ttu-id="24c42-136">Het aantal resultaten dat tegelijk moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="24c42-136">The number of results to be displayed at one time.</span></span> <span data-ttu-id="24c42-137">Deze parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="24c42-137">This parameter is optional.</span></span>                                                                                                                                                                                                                |
| <span data-ttu-id="24c42-138">filter</span><span class="sxs-lookup"><span data-stu-id="24c42-138">filter</span></span> | <span data-ttu-id="24c42-139">filter</span><span class="sxs-lookup"><span data-stu-id="24c42-139">filter</span></span> | <span data-ttu-id="24c42-140">Yes</span><span class="sxs-lookup"><span data-stu-id="24c42-140">Yes</span></span>      | <span data-ttu-id="24c42-141">De query die de zoek opdracht filtert.</span><span class="sxs-lookup"><span data-stu-id="24c42-141">The query that filters the search.</span></span> <span data-ttu-id="24c42-142">Als u klanten wilt ophalen voor een bepaalde indirecte wederverkoper, moet u de id van de indirecte wederverkoper invoegen en de volgende teken reeks opnemen en coderen: {"veld": "IndirectReseller", "waarde": "{indirect wederverkoper-id}", "operator": "begint \_ met"}.</span><span class="sxs-lookup"><span data-stu-id="24c42-142">To retrieve customers for a specified indirect reseller, you must insert the indirect reseller identifier and include and encode the following string: {"Field":"IndirectReseller","Value":"{indirect reseller identifier}","Operator":"starts\_with"}.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="24c42-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="24c42-143">Request headers</span></span>

<span data-ttu-id="24c42-144">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="24c42-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="24c42-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="24c42-145">Request body</span></span>

<span data-ttu-id="24c42-146">Geen.</span><span class="sxs-lookup"><span data-stu-id="24c42-146">None.</span></span>

### <a name="request-example-encoded"></a><span data-ttu-id="24c42-147">Voor beeld van aanvraag (gecodeerd)</span><span class="sxs-lookup"><span data-stu-id="24c42-147">Request example (encoded)</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=0&filter=%7B%22Field%22%3A%22IndirectReseller%22%2C%22Value%22%3A%22484e548c-f5f3-4528-93a9-c16c6373cb59%22%2C%22Operator%22%3A%22starts_with%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

### <a name="request-example-decoded"></a><span data-ttu-id="24c42-148">Voor beeld van aanvraag (gedecodeerd)</span><span class="sxs-lookup"><span data-stu-id="24c42-148">Request example (decoded)</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=0&filter={"Field":"IndirectReseller","Value":"484e548c-f5f3-4528-93a9-c16c6373cb59","Operator":"starts_with"} HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="24c42-149">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="24c42-149">REST response</span></span>

<span data-ttu-id="24c42-150">Als dit lukt, bevat de antwoord tekst informatie over de klanten van de reseller.</span><span class="sxs-lookup"><span data-stu-id="24c42-150">If successful, the response body contains information about the reseller's customers.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="24c42-151">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="24c42-151">Response success and error codes</span></span>

<span data-ttu-id="24c42-152">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="24c42-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="24c42-153">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="24c42-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="24c42-154">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="24c42-154">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="24c42-155">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="24c42-155">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2273
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CV: XI2/vIHmIEGVlGL9.0
MS-ServerId: 101112012
Date: Tue, 11 Apr 2017 23:31:28 GMT

{
    "totalCount": 2,
    "items": [{
            "id": "53eb21cb-6b2d-4ee5-9e92-27dfc927e93c",
            "companyProfile": {
                "tenantId": "53eb21cb-6b2d-4ee5-9e92-27dfc927e93c",
                "domain": "FourthCoffee137.onmicrosoft.com",
                "companyName": "FourthCoffee137",
                "links": {
                    "self": {
                        "uri": "/customers/53eb21cb-6b2d-4ee5-9e92-27dfc927e93c/profiles/company",
                        "method": "GET",
                        "headers": []
                    }
                },
                "attributes": {
                    "objectType": "CustomerCompanyProfile"
                }
            },
            "relationshipToPartner": "reseller",
            "links": {
                "self": {
                    "uri": "/customers/53eb21cb-6b2d-4ee5-9e92-27dfc927e93c",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }, {
            "id": "3dfe847b-cad9-4fc1-86d3-cf16c2790087",
            "companyProfile": {
                "tenantId": "3dfe847b-cad9-4fc1-86d3-cf16c2790087",
                "domain": "WingtipToys1254789149.onmicrosoft.com",
                "companyName": "Wingtip Toys1254789149",
                "links": {
                    "self": {
                        "uri": "/customers/3dfe847b-cad9-4fc1-86d3-cf16c2790087/profiles/company",
                        "method": "GET",
                        "headers": []
                    }
                },
                "attributes": {
                    "objectType": "CustomerCompanyProfile"
                }
            },
            "relationshipToPartner": "reseller",
            "links": {
                "self": {
                    "uri": "/customers/3dfe847b-cad9-4fc1-86d3-cf16c2790087",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        },
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
