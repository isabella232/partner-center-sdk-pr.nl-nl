---
title: Een lijst met klanten ophalen die zijn gefilterd op basis van een zoekveld
description: Hiermee wordt een verzameling klant resources opgehaald die overeenkomen met een filter. U kunt desgewenst een pagina grootte instellen. U kunt filteren op bedrijfs naam, domein, indirecte wederverkoper of indirecte Cloud Solution Provider (CSP).
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: aad9524dbe2c9edbbd7c1d50da7a448f6872fcb9
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767386"
---
# <a name="get-a-list-of-customers-filtered-by-a-search-field"></a><span data-ttu-id="64e7d-105">Een lijst met klanten ophalen die zijn gefilterd op basis van een zoekveld</span><span class="sxs-lookup"><span data-stu-id="64e7d-105">Get a list of customers filtered by a search field</span></span>

<span data-ttu-id="64e7d-106">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="64e7d-106">**Applies To**</span></span>

- <span data-ttu-id="64e7d-107">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="64e7d-107">Partner Center</span></span>
- <span data-ttu-id="64e7d-108">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="64e7d-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="64e7d-109">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="64e7d-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="64e7d-110">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="64e7d-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="64e7d-111">Hiermee wordt een verzameling [klant](customer-resources.md#customer) resources opgehaald die overeenkomen met een filter.</span><span class="sxs-lookup"><span data-stu-id="64e7d-111">Gets a collection of [Customer](customer-resources.md#customer) resources that match a filter.</span></span> <span data-ttu-id="64e7d-112">U kunt desgewenst een pagina grootte instellen.</span><span class="sxs-lookup"><span data-stu-id="64e7d-112">You can optionally set a page size.</span></span> <span data-ttu-id="64e7d-113">U kunt filteren op bedrijfs naam, domein, indirecte wederverkoper of indirecte Cloud Solution Provider (CSP).</span><span class="sxs-lookup"><span data-stu-id="64e7d-113">You can filter by company name, domain, indirect reseller, or indirect cloud solution provider (CSP).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="64e7d-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="64e7d-114">Prerequisites</span></span>

- <span data-ttu-id="64e7d-115">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="64e7d-115">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="64e7d-116">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="64e7d-116">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="64e7d-117">Een door de gebruiker samengesteld filter.</span><span class="sxs-lookup"><span data-stu-id="64e7d-117">A user-constructed filter.</span></span>

## <a name="c"></a><span data-ttu-id="64e7d-118">C\#</span><span class="sxs-lookup"><span data-stu-id="64e7d-118">C\#</span></span>

<span data-ttu-id="64e7d-119">Als u een verzameling klanten wilt ophalen die overeenkomen met een filter, moet u eerst een [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) -object instantiëren om het filter te maken.</span><span class="sxs-lookup"><span data-stu-id="64e7d-119">To get a collection of customers that match a filter, first instantiate a [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) object to create the filter.</span></span> <span data-ttu-id="64e7d-120">U moet een teken reeks door geven die de [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield)bevat en het type filter bewerking aangeven als [**FieldFilterOperation. StartsWith**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation).</span><span class="sxs-lookup"><span data-stu-id="64e7d-120">You'll need to pass a string that contains the [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield), and indicate the type of filter operation as [**FieldFilterOperation.StartsWith**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation).</span></span> <span data-ttu-id="64e7d-121">Dat is de enige veld Filter bewerking die wordt ondersteund door het eind punt van de klant.</span><span class="sxs-lookup"><span data-stu-id="64e7d-121">That's the only field filter operation supported by the customers end point.</span></span> <span data-ttu-id="64e7d-122">U moet ook de teken reeks opgeven waarop u wilt filteren.</span><span class="sxs-lookup"><span data-stu-id="64e7d-122">You'll also need to provide the string to filter by.</span></span>

<span data-ttu-id="64e7d-123">Instantiër vervolgens een [**iQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) -object om door te geven aan de query door de methode [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) aan te roepen en het filter door te geven.</span><span class="sxs-lookup"><span data-stu-id="64e7d-123">Next, instantiate an [**iQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) object to pass to the query by calling the [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) method and passing it the filter.</span></span> <span data-ttu-id="64e7d-124">BuildSimplyQuery is slechts een van de typen query's die worden ondersteund door de klasse [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) .</span><span class="sxs-lookup"><span data-stu-id="64e7d-124">BuildSimplyQuery is just one of the query types supported by the [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) class.</span></span>

<span data-ttu-id="64e7d-125">Ten slotte, om het filter uit te voeren en het resultaat te verkrijgen, moet u eerst [**IAggregatePartner. klanten**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) gebruiken om een interface te verkrijgen voor de klant activiteiten van de partner.</span><span class="sxs-lookup"><span data-stu-id="64e7d-125">Finally, to execute the filter and get the result, first use [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) to get an interface to the partner's customer operations.</span></span> <span data-ttu-id="64e7d-126">Roep vervolgens de methode [**query**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) of [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) aan.</span><span class="sxs-lookup"><span data-stu-id="64e7d-126">Then call the [**Query**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) or [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) method.</span></span>

``` csharp
IAggregatePartner partnerOperations;

// Specify the partial string to filter by (to match Contoso).
string searchPrefix = "cont"

// Create a simple field filter.
var fieldFilter = new SimpleFieldFilter(
    CustomerSearchField.CompanyName.ToString(),
    FieldFilterOperation.StartsWith,
    searchPrefix);

// Create an iQuery object to pass to the Query method.
var myQuery = QueryFactory.Instance.BuildSimpleQuery(fieldFilter);

// Get the collection of matching customers.
var customers = partnerOperations.Customers.Query(myQuery);
```

<span data-ttu-id="64e7d-127">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="64e7d-127">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="64e7d-128">**Project**: Partner Center SDK-voor beelden **klasse**: FilterCustomers.cs</span><span class="sxs-lookup"><span data-stu-id="64e7d-128">**Project**: Partner Center SDK Samples **Class**: FilterCustomers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="64e7d-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="64e7d-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="64e7d-130">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="64e7d-130">Request syntax</span></span>

| <span data-ttu-id="64e7d-131">Methode</span><span class="sxs-lookup"><span data-stu-id="64e7d-131">Method</span></span>  | <span data-ttu-id="64e7d-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="64e7d-132">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="64e7d-133">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="64e7d-133">**GET**</span></span> | <span data-ttu-id="64e7d-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers? grootte = {size} &filter = {filter} http/1.1</span><span class="sxs-lookup"><span data-stu-id="64e7d-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size}&filter={filter} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="64e7d-135">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="64e7d-135">URI parameters</span></span>

<span data-ttu-id="64e7d-136">Gebruik de volgende query parameters.</span><span class="sxs-lookup"><span data-stu-id="64e7d-136">Use the following query parameters.</span></span>

| <span data-ttu-id="64e7d-137">Naam</span><span class="sxs-lookup"><span data-stu-id="64e7d-137">Name</span></span>   | <span data-ttu-id="64e7d-138">Type</span><span class="sxs-lookup"><span data-stu-id="64e7d-138">Type</span></span>   | <span data-ttu-id="64e7d-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="64e7d-139">Required</span></span> | <span data-ttu-id="64e7d-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="64e7d-140">Description</span></span>                                                                    |
|--------|--------|----------|--------------------------------------------------------------------------------|
| <span data-ttu-id="64e7d-141">grootte</span><span class="sxs-lookup"><span data-stu-id="64e7d-141">size</span></span>   | <span data-ttu-id="64e7d-142">int</span><span class="sxs-lookup"><span data-stu-id="64e7d-142">int</span></span>    | <span data-ttu-id="64e7d-143">No</span><span class="sxs-lookup"><span data-stu-id="64e7d-143">No</span></span>       | <span data-ttu-id="64e7d-144">Het aantal resultaten dat tegelijk moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="64e7d-144">The number of results to be displayed at one time.</span></span> <span data-ttu-id="64e7d-145">Deze parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="64e7d-145">This parameter is optional.</span></span> |
| <span data-ttu-id="64e7d-146">filter</span><span class="sxs-lookup"><span data-stu-id="64e7d-146">filter</span></span> | <span data-ttu-id="64e7d-147">filter</span><span class="sxs-lookup"><span data-stu-id="64e7d-147">filter</span></span> | <span data-ttu-id="64e7d-148">Yes</span><span class="sxs-lookup"><span data-stu-id="64e7d-148">Yes</span></span>      | <span data-ttu-id="64e7d-149">Het filter dat op klanten moet worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="64e7d-149">The filter to apply to customers.</span></span> <span data-ttu-id="64e7d-150">Dit moet een gecodeerde teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="64e7d-150">This must be an encoded string.</span></span>              |

### <a name="filter-syntax"></a><span data-ttu-id="64e7d-151">Filter syntaxis</span><span class="sxs-lookup"><span data-stu-id="64e7d-151">Filter Syntax</span></span>

<span data-ttu-id="64e7d-152">U moet de filter parameter opstellen als een reeks door komma's gescheiden, sleutel-waardeparen.</span><span class="sxs-lookup"><span data-stu-id="64e7d-152">You must compose the filter parameter as a series of comma separated, key-value pairs.</span></span> <span data-ttu-id="64e7d-153">Elke sleutel en waarde moeten afzonderlijk worden genoteerd en gescheiden door een dubbele punt.</span><span class="sxs-lookup"><span data-stu-id="64e7d-153">Each key and value must be individually quoted and separated by a colon.</span></span> <span data-ttu-id="64e7d-154">Het volledige filter moet zijn gecodeerd.</span><span class="sxs-lookup"><span data-stu-id="64e7d-154">The entire filter must be encoded.</span></span>

<span data-ttu-id="64e7d-155">Een niet-gecodeerd voor beeld ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="64e7d-155">An unencoded example looks like this:</span></span>

```http
?filter{"Field":"CompanyName","Value":"cont","Operator":"starts_with"}
```

<span data-ttu-id="64e7d-156">In de volgende tabel worden de vereiste sleutel-waardeparen beschreven:</span><span class="sxs-lookup"><span data-stu-id="64e7d-156">The following table describes the required key-value pairs:</span></span>

| <span data-ttu-id="64e7d-157">Sleutel</span><span class="sxs-lookup"><span data-stu-id="64e7d-157">Key</span></span>      | <span data-ttu-id="64e7d-158">Waarde</span><span class="sxs-lookup"><span data-stu-id="64e7d-158">Value</span></span>                                                                                                                    |
|----------|--------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="64e7d-159">Veld</span><span class="sxs-lookup"><span data-stu-id="64e7d-159">Field</span></span>    | <span data-ttu-id="64e7d-160">Het veld dat moet worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="64e7d-160">The field to filter.</span></span> <span data-ttu-id="64e7d-161">U kunt de geldige waarden vinden in [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield).</span><span class="sxs-lookup"><span data-stu-id="64e7d-161">The valid values can be found in [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield).</span></span> |
| <span data-ttu-id="64e7d-162">Waarde</span><span class="sxs-lookup"><span data-stu-id="64e7d-162">Value</span></span>    | <span data-ttu-id="64e7d-163">De waarde waarop moet worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="64e7d-163">The value to filter by.</span></span> <span data-ttu-id="64e7d-164">Het geval van de waarde wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="64e7d-164">The case of the value is ignored.</span></span>                                                                |
| <span data-ttu-id="64e7d-165">Operator</span><span class="sxs-lookup"><span data-stu-id="64e7d-165">Operator</span></span> | <span data-ttu-id="64e7d-166">De operator die moet worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="64e7d-166">The operator to apply.</span></span> <span data-ttu-id="64e7d-167">De enige ondersteunde waarde voor dit klant scenario is "begint \_ met".</span><span class="sxs-lookup"><span data-stu-id="64e7d-167">The only supported value for this customer scenario is "starts\_with".</span></span>                            |

### <a name="request-headers"></a><span data-ttu-id="64e7d-168">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="64e7d-168">Request headers</span></span>

<span data-ttu-id="64e7d-169">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="64e7d-169">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="64e7d-170">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="64e7d-170">Request body</span></span>

<span data-ttu-id="64e7d-171">Geen.</span><span class="sxs-lookup"><span data-stu-id="64e7d-171">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="64e7d-172">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="64e7d-172">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=0&filter=%7B%22Field%22%3A%22CompanyName%22%2C%22Value%22%3A%22Cont%22%2C%22Operator%22%3A%22starts_with%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 5ce66de5-eea9-486f-a11c-c852aa3d1502
MS-CorrelationId: a2a912ee-d595-47e2-97ae-1b0ae1efa13d
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="64e7d-173">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="64e7d-173">REST response</span></span>

<span data-ttu-id="64e7d-174">Als dit lukt, retourneert deze methode een verzameling overeenkomende [klant](customer-resources.md#customer) resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="64e7d-174">If successful, this method returns a collection of matching [Customer](customer-resources.md#customer) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="64e7d-175">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="64e7d-175">Response success and error codes</span></span>

<span data-ttu-id="64e7d-176">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="64e7d-176">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="64e7d-177">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="64e7d-177">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="64e7d-178">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="64e7d-178">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="64e7d-179">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="64e7d-179">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1839
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a2a912ee-d595-47e2-97ae-1b0ae1efa13d
MS-RequestId: dfeda56c-1af5-43fc-a9c0-346b9e85dc96
MS-CV: n0lMNyJtaUC802pO.0
MS-ServerId: 202010223
Date: Fri, 24 Feb 2017 22:08:20 GMT

{
    "totalCount": 3,
    "items": [{
            "id": "c5757d70-06f3-4f23-8367-5a9e55019f94",
            "companyProfile": {
                "tenantId": "c5757d70-06f3-4f23-8367-5a9e55019f94",
                "domain": "contoso190.onmicrosoft.com",
                "companyName": "Contoso190",
                "links": {
                    "self": {
                        "uri": "/customers/c5757d70-06f3-4f23-8367-5a9e55019f94/profiles/company",
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
                    "uri": "/customers/c5757d70-06f3-4f23-8367-5a9e55019f94",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }, {
            "id": "7b26b357-9ca3-48b8-a58e-4febe2662a5d",
            "companyProfile": {
                "tenantId": "7b26b357-9ca3-48b8-a58e-4febe2662a5d",
                "domain": "ContosoCorpCo.onmicrosoft.com",
                "companyName": "Contoso",
                "links": {
                    "self": {
                        "uri": "/customers/7b26b357-9ca3-48b8-a58e-4febe2662a5d/profiles/company",
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
                    "uri": "/customers/7b26b357-9ca3-48b8-a58e-4febe2662a5d",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }, {
            "id": "bfbd6ef0-311f-47ec-bbd7-0fcb7846661b",
            "companyProfile": {
                "tenantId": "bfbd6ef0-311f-47ec-bbd7-0fcb7846661b",
                "domain": "contosocorpdemo.onmicrosoft.com",
                "companyName": "Contoso",
                "links": {
                    "self": {
                        "uri": "/customers/bfbd6ef0-311f-47ec-bbd7-0fcb7846661b/profiles/company",
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
                    "uri": "/customers/bfbd6ef0-311f-47ec-bbd7-0fcb7846661b",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Customer"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers?size=0&filter=%7B%22Field%22%3A%22Domain%22%2C%22Value%22%3A%22cont%22%2C%22Operator%22%3A%22starts_with%22%7D",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
