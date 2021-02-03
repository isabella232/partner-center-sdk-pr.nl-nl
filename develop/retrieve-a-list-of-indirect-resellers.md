---
title: Een lijst met indirecte resellers ophalen
description: Een lijst met de indirecte wederverkopers van de aangemelde partner ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e53237b97fa26d3a987f0ee7de491084b596af4a
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767523"
---
# <a name="retrieve-a-list-of-indirect-resellers"></a><span data-ttu-id="120c7-103">Een lijst met indirecte resellers ophalen</span><span class="sxs-lookup"><span data-stu-id="120c7-103">Retrieve a list of indirect resellers</span></span>

<span data-ttu-id="120c7-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="120c7-104">**Applies To**</span></span>

- <span data-ttu-id="120c7-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="120c7-105">Partner Center</span></span>

<span data-ttu-id="120c7-106">Een lijst met de indirecte wederverkopers van de aangemelde partner ophalen.</span><span class="sxs-lookup"><span data-stu-id="120c7-106">How to retrieve a list of the signed-in partner's indirect resellers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="120c7-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="120c7-107">Prerequisites</span></span>

- <span data-ttu-id="120c7-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="120c7-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="120c7-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="120c7-109">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="120c7-110">C\#</span><span class="sxs-lookup"><span data-stu-id="120c7-110">C\#</span></span>

<span data-ttu-id="120c7-111">Als u een lijst wilt ophalen met de indirecte wederverkopers met wie de aangemelde partner een relatie heeft, moet u eerst een interface voor het verzamelen van relaties ophalen uit de eigenschap [**partnerOperations. relationships**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships) .</span><span class="sxs-lookup"><span data-stu-id="120c7-111">To retrieve a list of indirect resellers with whom the signed-in partner has a relationship, first get an interface to relationship collection operations from the [**partnerOperations.Relationships**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships) property.</span></span> <span data-ttu-id="120c7-112">Roep vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.get) of [**Get \_ async**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.getasync) aan, waarbij een lid van de [**PartnerRelationshipType**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype) -inventarisatie wordt door gegeven om het relatie type te identificeren.</span><span class="sxs-lookup"><span data-stu-id="120c7-112">Then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.get) or [**Get\_Async**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.getasync) method, passing a member of the [**PartnerRelationshipType**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype) enumeration to identify the relationship type.</span></span> <span data-ttu-id="120c7-113">Als u indirecte wederverkopers wilt ophalen, moet u IsIndirectCloudSolutionProviderOf gebruiken.</span><span class="sxs-lookup"><span data-stu-id="120c7-113">To retrieve indirect resellers, you must use IsIndirectCloudSolutionProviderOf.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var indirectResellers = partnerOperations.Relationships.Get(PartnerRelationshipType.IsIndirectCloudSolutionProviderOf);
```

<span data-ttu-id="120c7-114">Voor **beeld**: [console test app](console-test-app.md)**project**: Partner Center SDK samples **klasse**: GetIndirectResellers.cs</span><span class="sxs-lookup"><span data-stu-id="120c7-114">**Sample**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: GetIndirectResellers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="120c7-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="120c7-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="120c7-116">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="120c7-116">Request syntax</span></span>

| <span data-ttu-id="120c7-117">Methode</span><span class="sxs-lookup"><span data-stu-id="120c7-117">Method</span></span>  | <span data-ttu-id="120c7-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="120c7-118">Request URI</span></span>                                                                                                                |
|---------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="120c7-119">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="120c7-119">**GET**</span></span> | <span data-ttu-id="120c7-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/relationships? Relationship \_ type = IsIndirectCloudSolutionProviderOf http/1.1</span><span class="sxs-lookup"><span data-stu-id="120c7-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/relationships?relationship\_type=IsIndirectCloudSolutionProviderOf HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="120c7-121">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="120c7-121">URI parameter</span></span>

<span data-ttu-id="120c7-122">Gebruik de volgende query parameter om het relatie type te identificeren.</span><span class="sxs-lookup"><span data-stu-id="120c7-122">Use the following query parameter to identify the relationship type.</span></span>

| <span data-ttu-id="120c7-123">Naam</span><span class="sxs-lookup"><span data-stu-id="120c7-123">Name</span></span>               | <span data-ttu-id="120c7-124">Type</span><span class="sxs-lookup"><span data-stu-id="120c7-124">Type</span></span>    | <span data-ttu-id="120c7-125">Vereist</span><span class="sxs-lookup"><span data-stu-id="120c7-125">Required</span></span>  | <span data-ttu-id="120c7-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="120c7-126">Description</span></span>                         |
|--------------------|---------|-----------|-------------------------------------|
| <span data-ttu-id="120c7-127">relationship_type</span><span class="sxs-lookup"><span data-stu-id="120c7-127">relationship_type</span></span>  | <span data-ttu-id="120c7-128">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="120c7-128">string</span></span>  | <span data-ttu-id="120c7-129">Yes</span><span class="sxs-lookup"><span data-stu-id="120c7-129">Yes</span></span>       | <span data-ttu-id="120c7-130">De waarde is de teken reeks representatie van een van de lidnamen gevonden in [PartnerRelationshipType](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype).</span><span class="sxs-lookup"><span data-stu-id="120c7-130">The value is the string representation of one of the member names found in [PartnerRelationshipType](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype).</span></span><br/><br/> <span data-ttu-id="120c7-131">Als de partner is aangemeld als provider en u een lijst wilt weer geven met de indirecte wederverkopers met wie ze een relatie tot stand hebben gebracht, gebruikt u IsIndirectCloudSolutionProviderOf.</span><span class="sxs-lookup"><span data-stu-id="120c7-131">If the partner is signed in as a provider and you want to get a list of the indirect resellers with whom they have established a relationship, use IsIndirectCloudSolutionProviderOf.</span></span><br/><br/> <span data-ttu-id="120c7-132">Als de partner is aangemeld als wederverkoper en u een lijst wilt krijgen met de indirecte providers met wie ze een relatie tot stand hebben gebracht, gebruikt u IsIndirectResellerOf.</span><span class="sxs-lookup"><span data-stu-id="120c7-132">If the partner is signed in as a reseller and you want to get a list of the indirect providers with whom they have established a relationship, use IsIndirectResellerOf.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="120c7-133">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="120c7-133">Request headers</span></span>

<span data-ttu-id="120c7-134">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="120c7-134">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="120c7-135">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="120c7-135">Request body</span></span>

<span data-ttu-id="120c7-136">Geen.</span><span class="sxs-lookup"><span data-stu-id="120c7-136">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="120c7-137">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="120c7-137">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/relationships?relationship_type=IsIndirectCloudSolutionProviderOf HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 144391a4-fb06-41ae-b684-3308ce4706bd
MS-CorrelationId: 72524ef8-81aa-4141-a049-45a4fece5d84
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="120c7-138">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="120c7-138">REST response</span></span>

<span data-ttu-id="120c7-139">Als dit lukt, bevat de antwoord tekst een verzameling [PartnerRelationship](relationships-resources.md) -resources om de wederverkopers te identificeren.</span><span class="sxs-lookup"><span data-stu-id="120c7-139">If successful, the response body contains a collection of [PartnerRelationship](relationships-resources.md) resources to identify the resellers.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="120c7-140">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="120c7-140">Response success and error codes</span></span>

<span data-ttu-id="120c7-141">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="120c7-141">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="120c7-142">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="120c7-142">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="120c7-143">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="120c7-143">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="120c7-144">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="120c7-144">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 298
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 72524ef8-81aa-4141-a049-45a4fece5d84
MS-RequestId: 144391a4-fb06-41ae-b684-3308ce4706bd
MS-CV: b21Ll1miM0yFMPQQ.0
MS-ServerId: 030020643
Date: Wed, 05 Apr 2017 21:08:44 GMT

{
    "totalCount": 2,
    "items": [{
            "id": "484e548c-f5f3-4528-93a9-c16c6373cb59",
            "name": "First Up Consultants",
            "relationshipType": "is_indirect_cloud_solution_provider_of",
            "state": "Active",
            "mpnId": "4847383",
            "location": "US",
            "attributes": {
                "objectType": "PartnerRelationship"
            }
        }, {
            "id": "b01b1487-b36e-4e6d-9b5e-0b58974c4b28",
            "name": "ReleCloud",
            "relationshipType": "is_indirect_cloud_solution_provider_of",
            "state": "Active",
            "mpnId": "4847433",
            "location": "BR",
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