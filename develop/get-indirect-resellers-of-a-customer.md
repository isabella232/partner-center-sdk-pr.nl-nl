---
title: Indirecte resellers van een klant ophalen
description: Een lijst op te halen met de indirecte resellers die een relatie hebben met een opgegeven klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 8697c40c22d5c19979c066b8d3a1de733e211f71
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446238"
---
# <a name="get-indirect-resellers-of-a-customer"></a><span data-ttu-id="ca093-103">Indirecte resellers van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="ca093-103">Get indirect resellers of a customer</span></span>

<span data-ttu-id="ca093-104">Een lijst op te halen met de indirecte resellers die een relatie hebben met een opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="ca093-104">How to get a list of the indirect resellers that have a relationship with a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ca093-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ca093-105">Prerequisites</span></span>

- <span data-ttu-id="ca093-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ca093-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ca093-107">Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="ca093-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="ca093-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ca093-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="ca093-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="ca093-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="ca093-110">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="ca093-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="ca093-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="ca093-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="ca093-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="ca093-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="ca093-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ca093-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="ca093-114">C\#</span><span class="sxs-lookup"><span data-stu-id="ca093-114">C\#</span></span>

<span data-ttu-id="ca093-115">Als u een lijst met indirecte resellers wilt ophalen met wie de opgegeven klant een relatie heeft, haalt u eerst een interface op met klantverzamelingsbewerkingen voor de specifieke klant van de [**eigenschap partnerOperations.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships) door de klant-id op te geven om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="ca093-115">To retrieve a list of indirect resellers with whom the specified customer has a relationship, first get an interface to customer collection operations for the specific customer from the [**partnerOperations.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships) property by providing the customer ID to identify the customer.</span></span> <span data-ttu-id="ca093-116">Roep vervolgens de [**methode Relationships.Get**](/dotnet/api/microsoft.store.partnercenter.relationships.icustomerrelationshipcollection.get) of [**Get \_ Async**](/dotnet/api/microsoft.store.partnercenter.relationships.icustomerrelationshipcollection.getasync) aan om de lijst met indirecte resellers op te halen.</span><span class="sxs-lookup"><span data-stu-id="ca093-116">Then call the [**Relationships.Get**](/dotnet/api/microsoft.store.partnercenter.relationships.icustomerrelationshipcollection.get) or [**Get\_Async**](/dotnet/api/microsoft.store.partnercenter.relationships.icustomerrelationshipcollection.getasync) method to get the list of indirect resellers.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

 var indirectResellers = partnerOperations.Customers[customerId].Relationships.Get();
```

<span data-ttu-id="ca093-117">**Voorbeeld**: [Consoletest-app](console-test-app.md)**Project:** Partnercentrum-SDK Voorbeelden **Klasse**: GetIndirectResellersOfCustomer.cs</span><span class="sxs-lookup"><span data-stu-id="ca093-117">**Sample**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: GetIndirectResellersOfCustomer.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="ca093-118">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="ca093-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ca093-119">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="ca093-119">Request syntax</span></span>

| <span data-ttu-id="ca093-120">Methode</span><span class="sxs-lookup"><span data-stu-id="ca093-120">Method</span></span>  | <span data-ttu-id="ca093-121">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="ca093-121">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="ca093-122">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ca093-122">**GET**</span></span> | <span data-ttu-id="ca093-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/relationships HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ca093-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/relationships HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="ca093-124">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="ca093-124">URI parameter</span></span>

<span data-ttu-id="ca093-125">Gebruik de volgende padparameter om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="ca093-125">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="ca093-126">Naam</span><span class="sxs-lookup"><span data-stu-id="ca093-126">Name</span></span>        | <span data-ttu-id="ca093-127">Type</span><span class="sxs-lookup"><span data-stu-id="ca093-127">Type</span></span>   | <span data-ttu-id="ca093-128">Vereist</span><span class="sxs-lookup"><span data-stu-id="ca093-128">Required</span></span> | <span data-ttu-id="ca093-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ca093-129">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="ca093-130">customer-id</span><span class="sxs-lookup"><span data-stu-id="ca093-130">customer-id</span></span> | <span data-ttu-id="ca093-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ca093-131">string</span></span> | <span data-ttu-id="ca093-132">Ja</span><span class="sxs-lookup"><span data-stu-id="ca093-132">Yes</span></span>      | <span data-ttu-id="ca093-133">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="ca093-133">A GUID formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ca093-134">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ca093-134">Request headers</span></span>

<span data-ttu-id="ca093-135">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="ca093-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ca093-136">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="ca093-136">Request body</span></span>

<span data-ttu-id="ca093-137">Geen.</span><span class="sxs-lookup"><span data-stu-id="ca093-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="ca093-138">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ca093-138">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/relationships HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c9251710-5a30-4cd3-891a-c42d550af9a8
MS-CorrelationId: a96f326c-a392-44f4-bcfe-43152a756ba8
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="ca093-139">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="ca093-139">REST response</span></span>

<span data-ttu-id="ca093-140">Als dit lukt, bevat de antwoord-body een verzameling [PartnerRelationship-resources](relationships-resources.md) om de resellers te identificeren.</span><span class="sxs-lookup"><span data-stu-id="ca093-140">If successful, the response body contains a collection of [PartnerRelationship](relationships-resources.md) resources to identify the resellers.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ca093-141">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="ca093-141">Response success and error codes</span></span>

<span data-ttu-id="ca093-142">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="ca093-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ca093-143">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="ca093-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ca093-144">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="ca093-144">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ca093-145">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="ca093-145">Response example</span></span>

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
