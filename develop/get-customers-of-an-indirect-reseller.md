---
title: Klanten van een indirecte reseller ophalen
description: Een lijst met de klanten van een indirecte reseller op te halen.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: e05248b16b803529258de806c25b117f3104ad2a
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446323"
---
# <a name="get-customers-of-an-indirect-reseller"></a><span data-ttu-id="03814-103">Klanten van een indirecte reseller ophalen</span><span class="sxs-lookup"><span data-stu-id="03814-103">Get customers of an indirect reseller</span></span>

<span data-ttu-id="03814-104">Een lijst met de klanten van een indirecte reseller op te halen.</span><span class="sxs-lookup"><span data-stu-id="03814-104">How to get a list of the customers of an indirect reseller.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="03814-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="03814-105">Prerequisites</span></span>

- <span data-ttu-id="03814-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="03814-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="03814-107">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="03814-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="03814-108">De tenant-id van de indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="03814-108">The tenant identifier of the indirect reseller.</span></span>

## <a name="c"></a><span data-ttu-id="03814-109">C\#</span><span class="sxs-lookup"><span data-stu-id="03814-109">C\#</span></span>

<span data-ttu-id="03814-110">Als u een verzameling klanten wilt ophalen die een relatie hebben met de opgegeven indirecte reseller, maakt u eerst een [**SimpleFieldFilter-object**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) om het filter te maken.</span><span class="sxs-lookup"><span data-stu-id="03814-110">To get a collection of customers that have a relationship with the specified indirect reseller, first instantiate a [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) object to create the filter.</span></span> <span data-ttu-id="03814-111">U moet het enumeration-lid [**CustomerSearchField.IndirectReseller**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield) doorgeven dat is geconverteerd naar een tekenreeks en [**FieldFilterOperation.StartsWith**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation) aangeven als het type filterbewerking.</span><span class="sxs-lookup"><span data-stu-id="03814-111">You'll need to pass the [**CustomerSearchField.IndirectReseller**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield) enumeration member converted to a string, and indicate [**FieldFilterOperation.StartsWith**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation) as the type of filter operation.</span></span> <span data-ttu-id="03814-112">U moet ook de tenant-id van de indirecte reseller verstrekken om op te filteren.</span><span class="sxs-lookup"><span data-stu-id="03814-112">You'll also need to provide the tenant identifier of the indirect reseller to filter by.</span></span>

<span data-ttu-id="03814-113">Maak vervolgens een [**iQuery-object**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) om door te geven aan de query door de [**methode BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) aan te roepen en dit door te geven aan het filter.</span><span class="sxs-lookup"><span data-stu-id="03814-113">Next, instantiate an [**iQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) object to pass to the query by calling the [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) method and passing it the filter.</span></span> <span data-ttu-id="03814-114">BuildSimplyQuery is slechts een van de querytypen die worden ondersteund door de [**klasse QueryFactory.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory)</span><span class="sxs-lookup"><span data-stu-id="03814-114">BuildSimplyQuery is just one of the query types supported by the [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) class.</span></span>

<span data-ttu-id="03814-115">Als u het filter wilt uitvoeren en het resultaat wilt krijgen, gebruikt u [**eerst IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) om een interface te krijgen met de klantactiviteiten van de partner.</span><span class="sxs-lookup"><span data-stu-id="03814-115">To execute the filter and get the result, first use [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) to get an interface to the partner's customer operations.</span></span> <span data-ttu-id="03814-116">Roep vervolgens de [**methode Query**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) of [**QueryAsync aan.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync)</span><span class="sxs-lookup"><span data-stu-id="03814-116">Then call the [**Query**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) or [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) method.</span></span>

<span data-ttu-id="03814-117">Als u een enumerator wilt maken voor het doorkruisen van paginaresultaten, moet u de enumerator-factory-interface [](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create)van de klantenverzameling ophalen uit de eigenschap [**IAggregatePartner.Enumerators.Customers**](/dotnet/api/microsoft.store.partnercenter.enumerators.iresourcecollectionenumeratorcontainer.customers) en vervolgens Maken aanroepen, zoals wordt weergegeven in de onderstaande code, en de variabele doorgeven die de klantverzameling bevat.</span><span class="sxs-lookup"><span data-stu-id="03814-117">To create an enumerator for traversing paged results, get the customer collection enumerator factory interface from the [**IAggregatePartner.Enumerators.Customers**](/dotnet/api/microsoft.store.partnercenter.enumerators.iresourcecollectionenumeratorcontainer.customers) property, and then call [**Create**](/dotnet/api/microsoft.store.partnercenter.factory.iresourcecollectionenumeratorfactory-1.create), as shown in the code below, passing the variable that holds the customer collection.</span></span>

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

<span data-ttu-id="03814-118">**Voorbeeld**: [Consoletest-app](console-test-app.md)**Project**: Partnercentrum-SDK Samples **Class:** GetCustomersOfIndirectReseller.cs</span><span class="sxs-lookup"><span data-stu-id="03814-118">**Sample**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: GetCustomersOfIndirectReseller.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="03814-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="03814-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="03814-120">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="03814-120">Request syntax</span></span>

| <span data-ttu-id="03814-121">Methode</span><span class="sxs-lookup"><span data-stu-id="03814-121">Method</span></span>  | <span data-ttu-id="03814-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="03814-122">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="03814-123">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="03814-123">**GET**</span></span> | <span data-ttu-id="03814-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size}?filter={filter} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="03814-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size}?filter={filter} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="03814-125">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="03814-125">URI parameter</span></span>

<span data-ttu-id="03814-126">Gebruik de volgende queryparameters om de aanvraag te maken.</span><span class="sxs-lookup"><span data-stu-id="03814-126">Use the following query parameters to create the request.</span></span>

| <span data-ttu-id="03814-127">Naam</span><span class="sxs-lookup"><span data-stu-id="03814-127">Name</span></span>   | <span data-ttu-id="03814-128">Type</span><span class="sxs-lookup"><span data-stu-id="03814-128">Type</span></span>   | <span data-ttu-id="03814-129">Vereist</span><span class="sxs-lookup"><span data-stu-id="03814-129">Required</span></span> | <span data-ttu-id="03814-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="03814-130">Description</span></span>                                                                                                                                                                                                                                                                                   |
|--------|--------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="03814-131">grootte</span><span class="sxs-lookup"><span data-stu-id="03814-131">size</span></span>   | <span data-ttu-id="03814-132">int</span><span class="sxs-lookup"><span data-stu-id="03814-132">int</span></span>    | <span data-ttu-id="03814-133">Nee</span><span class="sxs-lookup"><span data-stu-id="03814-133">No</span></span>       | <span data-ttu-id="03814-134">Het aantal resultaten dat in één keer moet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="03814-134">The number of results to be displayed at one time.</span></span> <span data-ttu-id="03814-135">Deze parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="03814-135">This parameter is optional.</span></span>                                                                                                                                                                                                                |
| <span data-ttu-id="03814-136">filter</span><span class="sxs-lookup"><span data-stu-id="03814-136">filter</span></span> | <span data-ttu-id="03814-137">filter</span><span class="sxs-lookup"><span data-stu-id="03814-137">filter</span></span> | <span data-ttu-id="03814-138">Ja</span><span class="sxs-lookup"><span data-stu-id="03814-138">Yes</span></span>      | <span data-ttu-id="03814-139">De query die de zoekopdracht filtert.</span><span class="sxs-lookup"><span data-stu-id="03814-139">The query that filters the search.</span></span> <span data-ttu-id="03814-140">Als u klanten wilt ophalen voor een opgegeven indirecte reseller, moet u de indirecte reseller-id invoegen en de volgende tekenreeks opnemen en coderen: {"Field":"IndirectReseller","Value":"{indirect reseller identifier}","Operator":"begint \_ met"}.</span><span class="sxs-lookup"><span data-stu-id="03814-140">To retrieve customers for a specified indirect reseller, you must insert the indirect reseller identifier and include and encode the following string: {"Field":"IndirectReseller","Value":"{indirect reseller identifier}","Operator":"starts\_with"}.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="03814-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="03814-141">Request headers</span></span>

<span data-ttu-id="03814-142">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="03814-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="03814-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="03814-143">Request body</span></span>

<span data-ttu-id="03814-144">Geen.</span><span class="sxs-lookup"><span data-stu-id="03814-144">None.</span></span>

### <a name="request-example-encoded"></a><span data-ttu-id="03814-145">Voorbeeld van aanvraag (gecodeerd)</span><span class="sxs-lookup"><span data-stu-id="03814-145">Request example (encoded)</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=0&filter=%7B%22Field%22%3A%22IndirectReseller%22%2C%22Value%22%3A%22484e548c-f5f3-4528-93a9-c16c6373cb59%22%2C%22Operator%22%3A%22starts_with%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

### <a name="request-example-decoded"></a><span data-ttu-id="03814-146">Voorbeeld van aanvraag (gedecodeerd)</span><span class="sxs-lookup"><span data-stu-id="03814-146">Request example (decoded)</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=0&filter={"Field":"IndirectReseller","Value":"484e548c-f5f3-4528-93a9-c16c6373cb59","Operator":"starts_with"} HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: aa04fb9d-c6b6-4754-8a6a-86e00cdd5ccb
MS-CorrelationId: b4e67a78-0692-45d1-b408-04b9178a8ac6
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="03814-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="03814-147">REST response</span></span>

<span data-ttu-id="03814-148">Als dit lukt, bevat de antwoord-body informatie over de klanten van de reseller.</span><span class="sxs-lookup"><span data-stu-id="03814-148">If successful, the response body contains information about the reseller's customers.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="03814-149">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="03814-149">Response success and error codes</span></span>

<span data-ttu-id="03814-150">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="03814-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="03814-151">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="03814-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="03814-152">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="03814-152">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="03814-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="03814-153">Response example</span></span>

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
