---
title: Een lijst met klanten ophalen die zijn gefilterd op basis van een zoekveld
description: Haalt een verzameling klantbronnen op die overeenkomen met een filter. U kunt desgewenst een paginaformaat instellen. U kunt filteren op bedrijfsnaam, domein, indirecte reseller of indirecte cloudoplossingsprovider (CSP).
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 663b8509d8704f9c443796d9fbcf72fb9c5b7fb2
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874955"
---
# <a name="get-a-list-of-customers-filtered-by-a-search-field"></a><span data-ttu-id="04561-105">Een lijst met klanten ophalen die zijn gefilterd op basis van een zoekveld</span><span class="sxs-lookup"><span data-stu-id="04561-105">Get a list of customers filtered by a search field</span></span>

<span data-ttu-id="04561-106">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="04561-106">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="04561-107">Haalt een verzameling [klantbronnen op](customer-resources.md#customer) die overeenkomen met een filter.</span><span class="sxs-lookup"><span data-stu-id="04561-107">Gets a collection of [Customer](customer-resources.md#customer) resources that match a filter.</span></span> <span data-ttu-id="04561-108">U kunt desgewenst een paginaformaat instellen.</span><span class="sxs-lookup"><span data-stu-id="04561-108">You can optionally set a page size.</span></span> <span data-ttu-id="04561-109">U kunt filteren op bedrijfsnaam, domein, indirecte reseller of indirecte cloudoplossingsprovider (CSP).</span><span class="sxs-lookup"><span data-stu-id="04561-109">You can filter by company name, domain, indirect reseller, or indirect cloud solution provider (CSP).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="04561-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="04561-110">Prerequisites</span></span>

- <span data-ttu-id="04561-111">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="04561-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="04561-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="04561-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="04561-113">Een door de gebruiker samengesteld filter.</span><span class="sxs-lookup"><span data-stu-id="04561-113">A user-constructed filter.</span></span>

## <a name="c"></a><span data-ttu-id="04561-114">C\#</span><span class="sxs-lookup"><span data-stu-id="04561-114">C\#</span></span>

<span data-ttu-id="04561-115">Als u een verzameling klanten wilt ophalen die overeenkomen met een filter, moet u eerst een [**SimpleFieldFilter-object**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) maken om het filter te maken.</span><span class="sxs-lookup"><span data-stu-id="04561-115">To get a collection of customers that match a filter, first instantiate a [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) object to create the filter.</span></span> <span data-ttu-id="04561-116">U moet een tekenreeks doorgeven die [**customerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield)bevat en het type filterbewerking als [**FieldFilterOperation.StartsWith aangeven.**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation)</span><span class="sxs-lookup"><span data-stu-id="04561-116">You'll need to pass a string that contains the [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield), and indicate the type of filter operation as [**FieldFilterOperation.StartsWith**](/dotnet/api/microsoft.store.partnercenter.models.query.fieldfilteroperation).</span></span> <span data-ttu-id="04561-117">Dat is de enige veldfilterbewerking die wordt ondersteund door het eindpunt van de klant.</span><span class="sxs-lookup"><span data-stu-id="04561-117">That's the only field filter operation supported by the customers end point.</span></span> <span data-ttu-id="04561-118">U moet ook de tekenreeks verstrekken om op te filteren.</span><span class="sxs-lookup"><span data-stu-id="04561-118">You'll also need to provide the string to filter by.</span></span>

<span data-ttu-id="04561-119">Maak vervolgens een [**iQuery-object**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) om door te geven aan de query door de [**methode BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) aan te roepen en dit door te geven aan het filter.</span><span class="sxs-lookup"><span data-stu-id="04561-119">Next, instantiate an [**iQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.iquery) object to pass to the query by calling the [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) method and passing it the filter.</span></span> <span data-ttu-id="04561-120">BuildSimplyQuery is slechts een van de querytypen die wordt ondersteund door de [**klasse QueryFactory.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory)</span><span class="sxs-lookup"><span data-stu-id="04561-120">BuildSimplyQuery is just one of the query types supported by the [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) class.</span></span>

<span data-ttu-id="04561-121">Als u ten slotte het filter wilt uitvoeren en het resultaat wilt krijgen, gebruikt u [**eerst IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) om een interface te krijgen met de klantbewerkingen van de partner.</span><span class="sxs-lookup"><span data-stu-id="04561-121">Finally, to execute the filter and get the result, first use [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) to get an interface to the partner's customer operations.</span></span> <span data-ttu-id="04561-122">Roep vervolgens de [**methode Query**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) of [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) aan.</span><span class="sxs-lookup"><span data-stu-id="04561-122">Then call the [**Query**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) or [**QueryAsync**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) method.</span></span>

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

<span data-ttu-id="04561-123">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="04561-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="04561-124">**Project:** Partnercentrum-SDK Samples **Class:** FilterCustomers.cs</span><span class="sxs-lookup"><span data-stu-id="04561-124">**Project**: Partner Center SDK Samples **Class**: FilterCustomers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="04561-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="04561-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="04561-126">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="04561-126">Request syntax</span></span>

| <span data-ttu-id="04561-127">Methode</span><span class="sxs-lookup"><span data-stu-id="04561-127">Method</span></span>  | <span data-ttu-id="04561-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="04561-128">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="04561-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="04561-129">**GET**</span></span> | <span data-ttu-id="04561-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size}&filter={filter} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="04561-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size}&filter={filter} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="04561-131">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="04561-131">URI parameters</span></span>

<span data-ttu-id="04561-132">Gebruik de volgende queryparameters.</span><span class="sxs-lookup"><span data-stu-id="04561-132">Use the following query parameters.</span></span>

| <span data-ttu-id="04561-133">Naam</span><span class="sxs-lookup"><span data-stu-id="04561-133">Name</span></span>   | <span data-ttu-id="04561-134">Type</span><span class="sxs-lookup"><span data-stu-id="04561-134">Type</span></span>   | <span data-ttu-id="04561-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="04561-135">Required</span></span> | <span data-ttu-id="04561-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="04561-136">Description</span></span>                                                                    |
|--------|--------|----------|--------------------------------------------------------------------------------|
| <span data-ttu-id="04561-137">grootte</span><span class="sxs-lookup"><span data-stu-id="04561-137">size</span></span>   | <span data-ttu-id="04561-138">int</span><span class="sxs-lookup"><span data-stu-id="04561-138">int</span></span>    | <span data-ttu-id="04561-139">Nee</span><span class="sxs-lookup"><span data-stu-id="04561-139">No</span></span>       | <span data-ttu-id="04561-140">Het aantal resultaten dat in één keer moet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="04561-140">The number of results to be displayed at one time.</span></span> <span data-ttu-id="04561-141">Deze parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="04561-141">This parameter is optional.</span></span> |
| <span data-ttu-id="04561-142">filter</span><span class="sxs-lookup"><span data-stu-id="04561-142">filter</span></span> | <span data-ttu-id="04561-143">filter</span><span class="sxs-lookup"><span data-stu-id="04561-143">filter</span></span> | <span data-ttu-id="04561-144">Ja</span><span class="sxs-lookup"><span data-stu-id="04561-144">Yes</span></span>      | <span data-ttu-id="04561-145">Het filter dat moet worden toegepast op klanten.</span><span class="sxs-lookup"><span data-stu-id="04561-145">The filter to apply to customers.</span></span> <span data-ttu-id="04561-146">Dit moet een gecodeerde tekenreeks zijn.</span><span class="sxs-lookup"><span data-stu-id="04561-146">This must be an encoded string.</span></span>              |

### <a name="filter-syntax"></a><span data-ttu-id="04561-147">Filtersyntaxis</span><span class="sxs-lookup"><span data-stu-id="04561-147">Filter Syntax</span></span>

<span data-ttu-id="04561-148">U moet de filterparameter samenstellen als een reeks door komma's gescheiden sleutel-waardeparen.</span><span class="sxs-lookup"><span data-stu-id="04561-148">You must compose the filter parameter as a series of comma separated, key-value pairs.</span></span> <span data-ttu-id="04561-149">Elke sleutel en waarde moeten afzonderlijk worden aangehaald en gescheiden door een dubbele punt.</span><span class="sxs-lookup"><span data-stu-id="04561-149">Each key and value must be individually quoted and separated by a colon.</span></span> <span data-ttu-id="04561-150">Het volledige filter moet worden gecodeerd.</span><span class="sxs-lookup"><span data-stu-id="04561-150">The entire filter must be encoded.</span></span>

<span data-ttu-id="04561-151">Een niet-gecodeerd voorbeeld ziet er als volgende uit:</span><span class="sxs-lookup"><span data-stu-id="04561-151">An unencoded example looks like this:</span></span>

```http
?filter{"Field":"CompanyName","Value":"cont","Operator":"starts_with"}
```

<span data-ttu-id="04561-152">In de volgende tabel worden de vereiste sleutel-waardeparen beschreven:</span><span class="sxs-lookup"><span data-stu-id="04561-152">The following table describes the required key-value pairs:</span></span>

| <span data-ttu-id="04561-153">Sleutel</span><span class="sxs-lookup"><span data-stu-id="04561-153">Key</span></span>      | <span data-ttu-id="04561-154">Waarde</span><span class="sxs-lookup"><span data-stu-id="04561-154">Value</span></span>                                                                                                                    |
|----------|--------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="04561-155">Veld</span><span class="sxs-lookup"><span data-stu-id="04561-155">Field</span></span>    | <span data-ttu-id="04561-156">Het veld dat moet worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="04561-156">The field to filter.</span></span> <span data-ttu-id="04561-157">De geldige waarden vindt u in [**CustomerSearchField.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield)</span><span class="sxs-lookup"><span data-stu-id="04561-157">The valid values can be found in [**CustomerSearchField**](/dotnet/api/microsoft.store.partnercenter.models.customers.customersearchfield).</span></span> |
| <span data-ttu-id="04561-158">Waarde</span><span class="sxs-lookup"><span data-stu-id="04561-158">Value</span></span>    | <span data-ttu-id="04561-159">De waarde om op te filteren.</span><span class="sxs-lookup"><span data-stu-id="04561-159">The value to filter by.</span></span> <span data-ttu-id="04561-160">Het geval van de waarde wordt genegeerd.</span><span class="sxs-lookup"><span data-stu-id="04561-160">The case of the value is ignored.</span></span>                                                                |
| <span data-ttu-id="04561-161">Operator</span><span class="sxs-lookup"><span data-stu-id="04561-161">Operator</span></span> | <span data-ttu-id="04561-162">De operator die moet worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="04561-162">The operator to apply.</span></span> <span data-ttu-id="04561-163">De enige ondersteunde waarde voor dit klantscenario is 'begint \_ met'.</span><span class="sxs-lookup"><span data-stu-id="04561-163">The only supported value for this customer scenario is "starts\_with".</span></span>                            |

### <a name="request-headers"></a><span data-ttu-id="04561-164">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="04561-164">Request headers</span></span>

<span data-ttu-id="04561-165">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="04561-165">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="04561-166">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="04561-166">Request body</span></span>

<span data-ttu-id="04561-167">Geen.</span><span class="sxs-lookup"><span data-stu-id="04561-167">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="04561-168">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="04561-168">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="04561-169">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="04561-169">REST response</span></span>

<span data-ttu-id="04561-170">Als dit lukt, retourneert deze methode een verzameling overeenkomende [Klantresources](customer-resources.md#customer) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="04561-170">If successful, this method returns a collection of matching [Customer](customer-resources.md#customer) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="04561-171">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="04561-171">Response success and error codes</span></span>

<span data-ttu-id="04561-172">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="04561-172">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="04561-173">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="04561-173">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="04561-174">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="04561-174">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="04561-175">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="04561-175">Response example</span></span>

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
