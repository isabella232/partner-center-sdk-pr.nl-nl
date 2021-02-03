---
title: Indirecte resellers van een klant ophalen
description: Een lijst met de indirecte wederverkopers ophalen die een relatie hebben met een opgegeven klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: d69abf9530548f110820ca04fefb698e0e37556c
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767491"
---
# <a name="get-indirect-resellers-of-a-customer"></a><span data-ttu-id="3a619-103">Indirecte resellers van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="3a619-103">Get indirect resellers of a customer</span></span>

<span data-ttu-id="3a619-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="3a619-104">**Applies To**</span></span>

- <span data-ttu-id="3a619-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="3a619-105">Partner Center</span></span>

<span data-ttu-id="3a619-106">Een lijst met de indirecte wederverkopers ophalen die een relatie hebben met een opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="3a619-106">How to get a list of the indirect resellers that have a relationship with a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a619-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3a619-107">Prerequisites</span></span>

- <span data-ttu-id="3a619-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3a619-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="3a619-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="3a619-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="3a619-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3a619-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="3a619-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="3a619-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="3a619-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="3a619-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="3a619-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="3a619-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="3a619-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="3a619-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="3a619-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3a619-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="3a619-116">C\#</span><span class="sxs-lookup"><span data-stu-id="3a619-116">C\#</span></span>

<span data-ttu-id="3a619-117">Als u een lijst wilt ophalen met de indirecte wederverkopers waarmee de opgegeven klant een relatie heeft, kunt u eerst een interface voor klant verzamelings bewerkingen voor de specifieke klant ophalen uit de eigenschap [**partnerOperations. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships) door de klant-id op te geven om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="3a619-117">To retrieve a list of indirect resellers with whom the specified customer has a relationship, first get an interface to customer collection operations for the specific customer from the [**partnerOperations.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships) property by providing the customer ID to identify the customer.</span></span> <span data-ttu-id="3a619-118">Roep vervolgens de [**relaties aan. ophalen**](/dotnet/api/microsoft.store.partnercenter.relationships.icustomerrelationshipcollection.get) of ophalen van de methode [**\_ async**](/dotnet/api/microsoft.store.partnercenter.relationships.icustomerrelationshipcollection.getasync) om de lijst met indirecte wederverkopers op te halen.</span><span class="sxs-lookup"><span data-stu-id="3a619-118">Then call the [**Relationships.Get**](/dotnet/api/microsoft.store.partnercenter.relationships.icustomerrelationshipcollection.get) or [**Get\_Async**](/dotnet/api/microsoft.store.partnercenter.relationships.icustomerrelationshipcollection.getasync) method to get the list of indirect resellers.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

 var indirectResellers = partnerOperations.Customers[customerId].Relationships.Get();
```

<span data-ttu-id="3a619-119">Voor **beeld**: [console test app](console-test-app.md)**project**: Partner Center SDK samples **klasse**: GetIndirectResellersOfCustomer.cs</span><span class="sxs-lookup"><span data-stu-id="3a619-119">**Sample**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: GetIndirectResellersOfCustomer.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="3a619-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="3a619-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3a619-121">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3a619-121">Request syntax</span></span>

| <span data-ttu-id="3a619-122">Methode</span><span class="sxs-lookup"><span data-stu-id="3a619-122">Method</span></span>  | <span data-ttu-id="3a619-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="3a619-123">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="3a619-124">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="3a619-124">**GET**</span></span> | <span data-ttu-id="3a619-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/relationships http/1.1</span><span class="sxs-lookup"><span data-stu-id="3a619-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/relationships HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="3a619-126">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="3a619-126">URI parameter</span></span>

<span data-ttu-id="3a619-127">Gebruik de volgende para meter voor het identificeren van de klant.</span><span class="sxs-lookup"><span data-stu-id="3a619-127">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="3a619-128">Naam</span><span class="sxs-lookup"><span data-stu-id="3a619-128">Name</span></span>        | <span data-ttu-id="3a619-129">Type</span><span class="sxs-lookup"><span data-stu-id="3a619-129">Type</span></span>   | <span data-ttu-id="3a619-130">Vereist</span><span class="sxs-lookup"><span data-stu-id="3a619-130">Required</span></span> | <span data-ttu-id="3a619-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3a619-131">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="3a619-132">klant-id</span><span class="sxs-lookup"><span data-stu-id="3a619-132">customer-id</span></span> | <span data-ttu-id="3a619-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3a619-133">string</span></span> | <span data-ttu-id="3a619-134">Yes</span><span class="sxs-lookup"><span data-stu-id="3a619-134">Yes</span></span>      | <span data-ttu-id="3a619-135">Een teken reeks met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="3a619-135">A GUID formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="3a619-136">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="3a619-136">Request headers</span></span>

<span data-ttu-id="3a619-137">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="3a619-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3a619-138">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="3a619-138">Request body</span></span>

<span data-ttu-id="3a619-139">Geen.</span><span class="sxs-lookup"><span data-stu-id="3a619-139">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="3a619-140">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3a619-140">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/relationships HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c9251710-5a30-4cd3-891a-c42d550af9a8
MS-CorrelationId: a96f326c-a392-44f4-bcfe-43152a756ba8
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="3a619-141">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="3a619-141">REST response</span></span>

<span data-ttu-id="3a619-142">Als dit lukt, bevat de antwoord tekst een verzameling [PartnerRelationship](relationships-resources.md) -resources om de wederverkopers te identificeren.</span><span class="sxs-lookup"><span data-stu-id="3a619-142">If successful, the response body contains a collection of [PartnerRelationship](relationships-resources.md) resources to identify the resellers.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3a619-143">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="3a619-143">Response success and error codes</span></span>

<span data-ttu-id="3a619-144">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="3a619-144">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="3a619-145">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="3a619-145">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3a619-146">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="3a619-146">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="3a619-147">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="3a619-147">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 264
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a96f326c-a392-44f4-bcfe-43152a756ba8
MS-RequestId: c9251710-5a30-4cd3-891a-c42d550af9a8
MS-CV: plJP3ufU0UqXMeuh.0
MS-ServerId: 020021921
Date: Fri, 07 Apr 2017 23:42:11 GMT

{
    "totalCount": 1,
    "items": [{
            "id": "484e548c-f5f3-4528-93a9-c16c6373cb59",
            "name": "First Up Consultants",
            "relationshipType": "is_indirect_cloud_solution_provider_of",
            "mpnId": "4847383",
            "attributes": {
                "objectType": "PartnerRelationship"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
