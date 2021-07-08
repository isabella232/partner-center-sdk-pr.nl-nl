---
title: Een lijst met klanten ophalen
description: Een verzameling resources ophalen die alle klanten van een partner vertegenwoordigen.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 840c9d1a61451763d37a19639f99b12f1deb7521
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874343"
---
# <a name="get-a-list-of-customers"></a><span data-ttu-id="aad40-103">Een lijst met klanten ophalen</span><span class="sxs-lookup"><span data-stu-id="aad40-103">Get a list of customers</span></span>

<span data-ttu-id="aad40-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="aad40-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="aad40-105">In dit artikel wordt beschreven hoe u een verzameling resources ophaalt die alle klanten van een partner vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="aad40-105">This article describes how to get a collection of resources that represents all of a partner's customers.</span></span>

> [!TIP]
> <span data-ttu-id="aad40-106">U kunt deze bewerking ook uitvoeren in het Partner Center dashboard.</span><span class="sxs-lookup"><span data-stu-id="aad40-106">You can also perform this operation in the Partner Center dashboard.</span></span> <span data-ttu-id="aad40-107">Selecteer op de hoofdpagina onder **Klantbeheer** de optie **Klanten weergeven.**</span><span class="sxs-lookup"><span data-stu-id="aad40-107">On the main page, under **Customer management**, select **View Customers**.</span></span> <span data-ttu-id="aad40-108">Of selecteer klanten op de **zijbalk.**</span><span class="sxs-lookup"><span data-stu-id="aad40-108">Or, on the sidebar, select **Customers**.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aad40-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="aad40-109">Prerequisites</span></span>

- <span data-ttu-id="aad40-110">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="aad40-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="aad40-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="aad40-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="aad40-112">C\#</span><span class="sxs-lookup"><span data-stu-id="aad40-112">C\#</span></span>

<span data-ttu-id="aad40-113">Een lijst met alle klanten op te halen:</span><span class="sxs-lookup"><span data-stu-id="aad40-113">To get a list of all customers:</span></span>

1. <span data-ttu-id="aad40-114">Gebruik de [**verzameling IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) om een **IPartner-object te** maken.</span><span class="sxs-lookup"><span data-stu-id="aad40-114">Use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection to create an **IPartner** object.</span></span>

2. <span data-ttu-id="aad40-115">Haal de klantenlijst op met behulp van [**de methoden Query()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) of [**QueryAsync().**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync)</span><span class="sxs-lookup"><span data-stu-id="aad40-115">Retrieve the customer list using the [**Query()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) or [**QueryAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) methods.</span></span> <span data-ttu-id="aad40-116">(Zie de klasse [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) voor instructies over het maken van een query.)</span><span class="sxs-lookup"><span data-stu-id="aad40-116">(For instructions on creating a query, see the [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) class.)</span></span>

``` csharp
// IAggregatePartner partnerOperations;

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// read customers into chunks of 40s
var customersBatch = scopedPartnerOperations.Customers.Query(QueryFactory.Instance.BuildIndexedQuery(40));
var customersEnumerator = scopedPartnerOperations.Enumerators.Customers.Create(customersBatch);
```

<span data-ttu-id="aad40-117">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="aad40-117">For an example, see the following:</span></span>

- <span data-ttu-id="aad40-118">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="aad40-118">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="aad40-119">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="aad40-119">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="aad40-120">Klasse: **CustomerPaging.cs**</span><span class="sxs-lookup"><span data-stu-id="aad40-120">Class: **CustomerPaging.cs**</span></span>

## <a name="java"></a><span data-ttu-id="aad40-121">Java</span><span class="sxs-lookup"><span data-stu-id="aad40-121">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="aad40-122">Een lijst met alle klanten op te halen:</span><span class="sxs-lookup"><span data-stu-id="aad40-122">To get a list of all customers:</span></span>

1. <span data-ttu-id="aad40-123">Gebruik de functie [**IAggregatePartner.getCustomers**] om een verwijzing naar de klantbewerkingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="aad40-123">Use the [**IAggregatePartner.getCustomers**] function to get a reference to the customer operations.</span></span>

2. <span data-ttu-id="aad40-124">Haal de klantenlijst op met behulp van de **functie query().**</span><span class="sxs-lookup"><span data-stu-id="aad40-124">Retrieve the customer list using the **query()** function.</span></span>

```java
// Query the customers, get the first page if a page size was set, otherwise get all customers
SeekBasedResourceCollection<Customer> customersPage = partnerOperations.getCustomers().query(QueryFactory.getInstance().buildIndexedQuery(40));

// Create a customer enumerator which will aid us in traversing the customer pages
IResourceCollectionEnumerator<SeekBasedResourceCollection<Customer>> customersEnumerator =
    partnerOperations.getEnumerators().getCustomers().create( customersPage );

int pageNumber = 1;

while (customersEnumerator.hasValue())
{
    /*
     * Use the customersEnumerator.getCurrent() function to
     * access the current page of customers.
     */

    // Get the next page of customers
    customersEnumerator.next();
}
```

## <a name="powershell"></a><span data-ttu-id="aad40-125">PowerShell</span><span class="sxs-lookup"><span data-stu-id="aad40-125">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="aad40-126">Voer de [**opdracht Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) zonder parameters uit om een volledige lijst met klanten op te halen.</span><span class="sxs-lookup"><span data-stu-id="aad40-126">Execute the [**Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) command with no parameters to get a complete list of customers.</span></span>

```powershell
Get-PartnerCustomer
```

## <a name="rest-request"></a><span data-ttu-id="aad40-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="aad40-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="aad40-128">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="aad40-128">Request syntax</span></span>

| <span data-ttu-id="aad40-129">Methode</span><span class="sxs-lookup"><span data-stu-id="aad40-129">Method</span></span>  | <span data-ttu-id="aad40-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="aad40-130">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="aad40-131">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="aad40-131">**GET**</span></span> | <span data-ttu-id="aad40-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="aad40-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="aad40-133">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="aad40-133">URI parameter</span></span>

<span data-ttu-id="aad40-134">Gebruik de volgende queryparameter om een lijst met klanten op te halen.</span><span class="sxs-lookup"><span data-stu-id="aad40-134">Use the following query parameter to get a list of customers.</span></span>

| <span data-ttu-id="aad40-135">Naam</span><span class="sxs-lookup"><span data-stu-id="aad40-135">Name</span></span>     | <span data-ttu-id="aad40-136">Type</span><span class="sxs-lookup"><span data-stu-id="aad40-136">Type</span></span>    | <span data-ttu-id="aad40-137">Vereist</span><span class="sxs-lookup"><span data-stu-id="aad40-137">Required</span></span> | <span data-ttu-id="aad40-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="aad40-138">Description</span></span>                                        |
|----------|---------|----------|----------------------------------------------------|
| <span data-ttu-id="aad40-139">**Grootte**</span><span class="sxs-lookup"><span data-stu-id="aad40-139">**size**</span></span> | <span data-ttu-id="aad40-140">**int**</span><span class="sxs-lookup"><span data-stu-id="aad40-140">**int**</span></span> | <span data-ttu-id="aad40-141">J</span><span class="sxs-lookup"><span data-stu-id="aad40-141">Y</span></span>        | <span data-ttu-id="aad40-142">Het aantal resultaten dat in één keer moet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="aad40-142">The number of results to be displayed at one time.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="aad40-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="aad40-143">Request headers</span></span>

<span data-ttu-id="aad40-144">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="aad40-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="aad40-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="aad40-145">Request body</span></span>

<span data-ttu-id="aad40-146">Geen.</span><span class="sxs-lookup"><span data-stu-id="aad40-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="aad40-147">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="aad40-147">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=40 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
```

## <a name="rest-response"></a><span data-ttu-id="aad40-148">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="aad40-148">REST response</span></span>

<span data-ttu-id="aad40-149">Als dit lukt, retourneert deze methode een verzameling [Klantresources](customer-resources.md#customer) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="aad40-149">If successful, this method returns a collection of [Customer](customer-resources.md#customer) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="aad40-150">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="aad40-150">Response success and error codes</span></span>

<span data-ttu-id="aad40-151">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="aad40-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="aad40-152">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="aad40-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="aad40-153">Zie Foutcodes voor een [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="aad40-153">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="aad40-154">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="aad40-154">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 15650
Content-Type: application/json
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
Date: Fri, 20 Nov 2015 01:08:23 GMT

{
    "totalCount": 2,
    "items": [{
        "id": "b44bb1fb-c595-45b0-9e09-d657365580bf",
        "companyProfile": {
            "tenantId": "<guid>",
            "domain": "domain",
            "companyName": "companyName",
            "attributes": {
                "objectType": "CustomerCompanyProfile"
            }
        },
        "relationshipToPartner": "reseller",
        "attributes": {
            "objectType": "Customer"
        }
    },
    {
        "id": "45c44870-ef77-4fdd-b6fe-3dacb075cff2",
        "companyProfile": {
            "tenantId": "<guid>",
            "domain": "domain",
            "companyName": "companyName",
            "attributes": {
                "objectType": "CustomerCompanyProfile"
            }
        },
        "relationshipToPartner": "reseller",
        "attributes": {
            "objectType": "Customer"
        }
    }],
    "links": {
        "self": {
            "uri": "/v1/customers?size=40",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
