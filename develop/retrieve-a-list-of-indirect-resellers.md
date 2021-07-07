---
title: Een lijst met indirecte resellers ophalen
description: Een lijst ophalen van de indirecte resellers van de aangemelde partner.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 58f5c3378b5b941fdc9dafcf28f5efbc58c29c7c
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446561"
---
# <a name="retrieve-a-list-of-indirect-resellers"></a><span data-ttu-id="20a66-103">Een lijst met indirecte resellers ophalen</span><span class="sxs-lookup"><span data-stu-id="20a66-103">Retrieve a list of indirect resellers</span></span>

<span data-ttu-id="20a66-104">Een lijst ophalen van de indirecte resellers van de aangemelde partner.</span><span class="sxs-lookup"><span data-stu-id="20a66-104">How to retrieve a list of the signed-in partner's indirect resellers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="20a66-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="20a66-105">Prerequisites</span></span>

- <span data-ttu-id="20a66-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="20a66-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="20a66-107">Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="20a66-107">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="20a66-108">C\#</span><span class="sxs-lookup"><span data-stu-id="20a66-108">C\#</span></span>

<span data-ttu-id="20a66-109">Als u een lijst wilt ophalen met indirecte resellers met wie de aangemelde partner een relatie heeft, haalt u eerst een interface op met bewerkingen voor het verzamelen van relaties van de [**eigenschap partnerOperations.Relationships.**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships)</span><span class="sxs-lookup"><span data-stu-id="20a66-109">To retrieve a list of indirect resellers with whom the signed-in partner has a relationship, first get an interface to relationship collection operations from the [**partnerOperations.Relationships**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships) property.</span></span> <span data-ttu-id="20a66-110">Roep vervolgens de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.get) of [**Get \_ Async**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.getasync) aan, waarbij een lid van de Enumeration [**PartnerRelationshipType**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype) wordt doorgeven om het relatietype te identificeren.</span><span class="sxs-lookup"><span data-stu-id="20a66-110">Then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.get) or [**Get\_Async**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.getasync) method, passing a member of the [**PartnerRelationshipType**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype) enumeration to identify the relationship type.</span></span> <span data-ttu-id="20a66-111">Als u indirecte resellers wilt ophalen, moet u IsIndirectCloudSolutionProviderOf gebruiken.</span><span class="sxs-lookup"><span data-stu-id="20a66-111">To retrieve indirect resellers, you must use IsIndirectCloudSolutionProviderOf.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var indirectResellers = partnerOperations.Relationships.Get(PartnerRelationshipType.IsIndirectCloudSolutionProviderOf);
```

<span data-ttu-id="20a66-112">**Voorbeeld**: [Consoletest-app](console-test-app.md)**Project**: Partnercentrum-SDK Samples **Class:** GetIndirectResellers.cs</span><span class="sxs-lookup"><span data-stu-id="20a66-112">**Sample**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: GetIndirectResellers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="20a66-113">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="20a66-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="20a66-114">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="20a66-114">Request syntax</span></span>

| <span data-ttu-id="20a66-115">Methode</span><span class="sxs-lookup"><span data-stu-id="20a66-115">Method</span></span>  | <span data-ttu-id="20a66-116">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="20a66-116">Request URI</span></span>                                                                                                                |
|---------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="20a66-117">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="20a66-117">**GET**</span></span> | <span data-ttu-id="20a66-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/relationships?relatietype=IsIndirectCloudSolutionProviderOf \_ HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="20a66-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/relationships?relationship\_type=IsIndirectCloudSolutionProviderOf HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="20a66-119">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="20a66-119">URI parameter</span></span>

<span data-ttu-id="20a66-120">Gebruik de volgende queryparameter om het relatietype te identificeren.</span><span class="sxs-lookup"><span data-stu-id="20a66-120">Use the following query parameter to identify the relationship type.</span></span>

| <span data-ttu-id="20a66-121">Naam</span><span class="sxs-lookup"><span data-stu-id="20a66-121">Name</span></span>               | <span data-ttu-id="20a66-122">Type</span><span class="sxs-lookup"><span data-stu-id="20a66-122">Type</span></span>    | <span data-ttu-id="20a66-123">Vereist</span><span class="sxs-lookup"><span data-stu-id="20a66-123">Required</span></span>  | <span data-ttu-id="20a66-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="20a66-124">Description</span></span>                         |
|--------------------|---------|-----------|-------------------------------------|
| <span data-ttu-id="20a66-125">relationship_type</span><span class="sxs-lookup"><span data-stu-id="20a66-125">relationship_type</span></span>  | <span data-ttu-id="20a66-126">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="20a66-126">string</span></span>  | <span data-ttu-id="20a66-127">Ja</span><span class="sxs-lookup"><span data-stu-id="20a66-127">Yes</span></span>       | <span data-ttu-id="20a66-128">De waarde is de tekenreeksweergave van een van de lidnamen in [PartnerRelationshipType](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype).</span><span class="sxs-lookup"><span data-stu-id="20a66-128">The value is the string representation of one of the member names found in [PartnerRelationshipType](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype).</span></span><br/><br/> <span data-ttu-id="20a66-129">Als de partner is aangemeld als provider en u een lijst wilt krijgen van de indirecte resellers met wie ze een relatie tot stand hebben gebracht, gebruikt u IsIndirectCloudSolutionProviderOf.</span><span class="sxs-lookup"><span data-stu-id="20a66-129">If the partner is signed in as a provider and you want to get a list of the indirect resellers with whom they have established a relationship, use IsIndirectCloudSolutionProviderOf.</span></span><br/><br/> <span data-ttu-id="20a66-130">Als de partner is aangemeld als een reseller en u een lijst wilt krijgen met de indirecte providers met wie ze een relatie hebben gemaakt, gebruikt u IsIndirectResellerOf.</span><span class="sxs-lookup"><span data-stu-id="20a66-130">If the partner is signed in as a reseller and you want to get a list of the indirect providers with whom they have established a relationship, use IsIndirectResellerOf.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="20a66-131">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="20a66-131">Request headers</span></span>

<span data-ttu-id="20a66-132">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="20a66-132">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="20a66-133">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="20a66-133">Request body</span></span>

<span data-ttu-id="20a66-134">Geen.</span><span class="sxs-lookup"><span data-stu-id="20a66-134">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="20a66-135">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="20a66-135">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/relationships?relationship_type=IsIndirectCloudSolutionProviderOf HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 144391a4-fb06-41ae-b684-3308ce4706bd
MS-CorrelationId: 72524ef8-81aa-4141-a049-45a4fece5d84
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="20a66-136">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="20a66-136">REST response</span></span>

<span data-ttu-id="20a66-137">Als dit lukt, bevat de antwoord-body een verzameling [PartnerRelationship-resources](relationships-resources.md) om de resellers te identificeren.</span><span class="sxs-lookup"><span data-stu-id="20a66-137">If successful, the response body contains a collection of [PartnerRelationship](relationships-resources.md) resources to identify the resellers.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="20a66-138">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="20a66-138">Response success and error codes</span></span>

<span data-ttu-id="20a66-139">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="20a66-139">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="20a66-140">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="20a66-140">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="20a66-141">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="20a66-141">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="20a66-142">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="20a66-142">Response example</span></span>

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