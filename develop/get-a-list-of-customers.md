---
title: Een lijst met klanten ophalen
description: Hoe u een verzameling resources kunt ophalen die alle klanten van een partner vertegenwoordigen.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 2dd8469458809ab38b6d6081adc91d6d1184d2d0
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767471"
---
# <a name="get-a-list-of-customers"></a><span data-ttu-id="cad5b-103">Een lijst met klanten ophalen</span><span class="sxs-lookup"><span data-stu-id="cad5b-103">Get a list of customers</span></span>

<span data-ttu-id="cad5b-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="cad5b-104">**Applies to:**</span></span>

- <span data-ttu-id="cad5b-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="cad5b-105">Partner Center</span></span>
- <span data-ttu-id="cad5b-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="cad5b-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="cad5b-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="cad5b-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="cad5b-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="cad5b-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="cad5b-109">In dit artikel wordt beschreven hoe u een verzameling resources kunt ophalen die alle klanten van een partner vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="cad5b-109">This article describes how to get a collection of resources that represents all of a partner's customers.</span></span>

> [!TIP]
> <span data-ttu-id="cad5b-110">U kunt deze bewerking ook uitvoeren in het dash board van partner Center.</span><span class="sxs-lookup"><span data-stu-id="cad5b-110">You can also perform this operation in the Partner Center dashboard.</span></span> <span data-ttu-id="cad5b-111">Selecteer op de hoofd pagina onder **klant beheer** de optie **klanten weer geven**.</span><span class="sxs-lookup"><span data-stu-id="cad5b-111">On the main page, under **Customer management**, select **View Customers**.</span></span> <span data-ttu-id="cad5b-112">U kunt ook op de zijbalk **klanten** selecteren.</span><span class="sxs-lookup"><span data-stu-id="cad5b-112">Or, on the sidebar, select **Customers**.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cad5b-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cad5b-113">Prerequisites</span></span>

- <span data-ttu-id="cad5b-114">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cad5b-114">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cad5b-115">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="cad5b-115">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="cad5b-116">C\#</span><span class="sxs-lookup"><span data-stu-id="cad5b-116">C\#</span></span>

<span data-ttu-id="cad5b-117">Een lijst met alle klanten ophalen:</span><span class="sxs-lookup"><span data-stu-id="cad5b-117">To get a list of all customers:</span></span>

1. <span data-ttu-id="cad5b-118">Gebruik de verzameling [**IAggregatePartner. Customs**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) om een **IPartner** -object te maken.</span><span class="sxs-lookup"><span data-stu-id="cad5b-118">Use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection to create an **IPartner** object.</span></span>

2. <span data-ttu-id="cad5b-119">Haal de klanten lijst op met behulp van de methoden [**query ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) of [**QueryAsync ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) .</span><span class="sxs-lookup"><span data-stu-id="cad5b-119">Retrieve the customer list using the [**Query()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.query) or [**QueryAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.queryasync) methods.</span></span> <span data-ttu-id="cad5b-120">(Zie de [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) -klasse voor instructies over het maken van een query.)</span><span class="sxs-lookup"><span data-stu-id="cad5b-120">(For instructions on creating a query, see the [**QueryFactory**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory) class.)</span></span>

``` csharp
// IAggregatePartner partnerOperations;

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// read customers into chunks of 40s
var customersBatch = scopedPartnerOperations.Customers.Query(QueryFactory.Instance.BuildIndexedQuery(40));
var customersEnumerator = scopedPartnerOperations.Enumerators.Customers.Create(customersBatch);
```

<span data-ttu-id="cad5b-121">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="cad5b-121">For an example, see the following:</span></span>

- <span data-ttu-id="cad5b-122">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="cad5b-122">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="cad5b-123">Project: **PartnerSDK. FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="cad5b-123">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="cad5b-124">Klasse: **CustomerPaging.cs**</span><span class="sxs-lookup"><span data-stu-id="cad5b-124">Class: **CustomerPaging.cs**</span></span>

## <a name="java"></a><span data-ttu-id="cad5b-125">Java</span><span class="sxs-lookup"><span data-stu-id="cad5b-125">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="cad5b-126">Een lijst met alle klanten ophalen:</span><span class="sxs-lookup"><span data-stu-id="cad5b-126">To get a list of all customers:</span></span>

1. <span data-ttu-id="cad5b-127">Gebruik de functie [**IAggregatePartner. getCustomers**] om een verwijzing naar de klant bewerkingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="cad5b-127">Use the [**IAggregatePartner.getCustomers**] function to get a reference to the customer operations.</span></span>

2. <span data-ttu-id="cad5b-128">Haal de klanten lijst op met behulp van de functie **query ()** .</span><span class="sxs-lookup"><span data-stu-id="cad5b-128">Retrieve the customer list using the **query()** function.</span></span>

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

## <a name="powershell"></a><span data-ttu-id="cad5b-129">PowerShell</span><span class="sxs-lookup"><span data-stu-id="cad5b-129">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="cad5b-130">Voer de opdracht [**Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) zonder para meters uit om een volledige lijst met klanten te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="cad5b-130">Execute the [**Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) command with no parameters to get a complete list of customers.</span></span>

```powershell
Get-PartnerCustomer
```

## <a name="rest-request"></a><span data-ttu-id="cad5b-131">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="cad5b-131">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cad5b-132">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cad5b-132">Request syntax</span></span>

| <span data-ttu-id="cad5b-133">Methode</span><span class="sxs-lookup"><span data-stu-id="cad5b-133">Method</span></span>  | <span data-ttu-id="cad5b-134">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="cad5b-134">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="cad5b-135">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="cad5b-135">**GET**</span></span> | <span data-ttu-id="cad5b-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers? grootte = {size} http/1.1</span><span class="sxs-lookup"><span data-stu-id="cad5b-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers?size={size} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="cad5b-137">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="cad5b-137">URI parameter</span></span>

<span data-ttu-id="cad5b-138">Gebruik de volgende query parameter om een lijst met klanten op te halen.</span><span class="sxs-lookup"><span data-stu-id="cad5b-138">Use the following query parameter to get a list of customers.</span></span>

| <span data-ttu-id="cad5b-139">Naam</span><span class="sxs-lookup"><span data-stu-id="cad5b-139">Name</span></span>     | <span data-ttu-id="cad5b-140">Type</span><span class="sxs-lookup"><span data-stu-id="cad5b-140">Type</span></span>    | <span data-ttu-id="cad5b-141">Vereist</span><span class="sxs-lookup"><span data-stu-id="cad5b-141">Required</span></span> | <span data-ttu-id="cad5b-142">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cad5b-142">Description</span></span>                                        |
|----------|---------|----------|----------------------------------------------------|
| <span data-ttu-id="cad5b-143">**size**</span><span class="sxs-lookup"><span data-stu-id="cad5b-143">**size**</span></span> | <span data-ttu-id="cad5b-144">**int**</span><span class="sxs-lookup"><span data-stu-id="cad5b-144">**int**</span></span> | <span data-ttu-id="cad5b-145">J</span><span class="sxs-lookup"><span data-stu-id="cad5b-145">Y</span></span>        | <span data-ttu-id="cad5b-146">Het aantal resultaten dat tegelijk moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cad5b-146">The number of results to be displayed at one time.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="cad5b-147">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="cad5b-147">Request headers</span></span>

<span data-ttu-id="cad5b-148">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="cad5b-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cad5b-149">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="cad5b-149">Request body</span></span>

<span data-ttu-id="cad5b-150">Geen.</span><span class="sxs-lookup"><span data-stu-id="cad5b-150">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="cad5b-151">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cad5b-151">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers?size=40 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
```

## <a name="rest-response"></a><span data-ttu-id="cad5b-152">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="cad5b-152">REST response</span></span>

<span data-ttu-id="cad5b-153">Als dit lukt, retourneert deze methode een verzameling [klant](customer-resources.md#customer) resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="cad5b-153">If successful, this method returns a collection of [Customer](customer-resources.md#customer) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cad5b-154">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="cad5b-154">Response success and error codes</span></span>

<span data-ttu-id="cad5b-155">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="cad5b-155">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cad5b-156">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="cad5b-156">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="cad5b-157">Zie [fout codes](error-codes.md)voor een volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="cad5b-157">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="cad5b-158">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="cad5b-158">Response example</span></span>

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
