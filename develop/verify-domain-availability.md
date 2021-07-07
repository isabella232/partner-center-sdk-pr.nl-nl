---
title: Beschikbaarheid van domein verifiëren
description: Bepalen of een domein beschikbaar is voor gebruik.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e2b8f0438516cc0aff9c4d8159c22de43ec582e4
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530273"
---
# <a name="verify-domain-availability"></a><span data-ttu-id="49040-103">Beschikbaarheid van domein verifiëren</span><span class="sxs-lookup"><span data-stu-id="49040-103">Verify domain availability</span></span>

<span data-ttu-id="49040-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="49040-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="49040-105">Bepalen of een domein beschikbaar is voor gebruik.</span><span class="sxs-lookup"><span data-stu-id="49040-105">How to determine if a domain is available for use.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49040-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="49040-106">Prerequisites</span></span>

- <span data-ttu-id="49040-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="49040-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="49040-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="49040-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="49040-109">Een domein (bijvoorbeeld `contoso.onmicrosoft.com` ).</span><span class="sxs-lookup"><span data-stu-id="49040-109">A domain (for example `contoso.onmicrosoft.com`).</span></span>

## <a name="c"></a><span data-ttu-id="49040-110">C\#</span><span class="sxs-lookup"><span data-stu-id="49040-110">C\#</span></span>

<span data-ttu-id="49040-111">Als u wilt controleren of een domein beschikbaar is, roept u [**eerst IAggregatePartner.Domains**](/dotnet/api/microsoft.store.partnercenter.ipartner.domains) aan om een interface voor domeinbewerkingen te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="49040-111">To verify if a domain is available, first call [**IAggregatePartner.Domains**](/dotnet/api/microsoft.store.partnercenter.ipartner.domains) to obtain an interface to domain operations.</span></span> <span data-ttu-id="49040-112">Roep vervolgens de [**methode ByDomain**](/dotnet/api/microsoft.store.partnercenter.domains.idomaincollection.bydomain) aan met het domein om dit te controleren.</span><span class="sxs-lookup"><span data-stu-id="49040-112">Then call the [**ByDomain**](/dotnet/api/microsoft.store.partnercenter.domains.idomaincollection.bydomain) method with the domain to check.</span></span> <span data-ttu-id="49040-113">Met deze methode wordt een interface opgehaald voor de bewerkingen die beschikbaar zijn voor een specifiek domein.</span><span class="sxs-lookup"><span data-stu-id="49040-113">This method retrieves an interface to the operations available for a specific domain.</span></span> <span data-ttu-id="49040-114">Roep ten slotte de [**methode Exists**](/dotnet/api/microsoft.store.partnercenter.domains.idomain.exists) aan om te zien of het domein al bestaat.</span><span class="sxs-lookup"><span data-stu-id="49040-114">Finally, call the [**Exists**](/dotnet/api/microsoft.store.partnercenter.domains.idomain.exists) method to see if the domain already exists.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// const string domain = "contoso.onmicrosoft.com";

bool result = partnerOperations.Domains.ByDomain(domain).Exists();
```

<span data-ttu-id="49040-115">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="49040-115">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="49040-116">**Project**: Partnercentrum-SDK Samples **Class**: CheckDomainAvailability.cs</span><span class="sxs-lookup"><span data-stu-id="49040-116">**Project**: Partner Center SDK Samples **Class**: CheckDomainAvailability.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="49040-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="49040-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="49040-118">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="49040-118">Request syntax</span></span>

| <span data-ttu-id="49040-119">Methode</span><span class="sxs-lookup"><span data-stu-id="49040-119">Method</span></span>   | <span data-ttu-id="49040-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="49040-120">Request URI</span></span>                                                              |
|----------|--------------------------------------------------------------------------|
| <span data-ttu-id="49040-121">**Hoofd**</span><span class="sxs-lookup"><span data-stu-id="49040-121">**HEAD**</span></span> | <span data-ttu-id="49040-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/domains/{domain} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="49040-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/domains/{domain} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="49040-123">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="49040-123">URI parameter</span></span>

<span data-ttu-id="49040-124">Gebruik de volgende queryparameter om de beschikbaarheid van domeinen te controleren.</span><span class="sxs-lookup"><span data-stu-id="49040-124">Use the following query parameter to verify domain availability.</span></span>

| <span data-ttu-id="49040-125">Naam</span><span class="sxs-lookup"><span data-stu-id="49040-125">Name</span></span>       | <span data-ttu-id="49040-126">Type</span><span class="sxs-lookup"><span data-stu-id="49040-126">Type</span></span>       | <span data-ttu-id="49040-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="49040-127">Required</span></span> | <span data-ttu-id="49040-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="49040-128">Description</span></span>                                   |
|------------|------------|----------|-----------------------------------------------|
| <span data-ttu-id="49040-129">**Domein**</span><span class="sxs-lookup"><span data-stu-id="49040-129">**domain**</span></span> | <span data-ttu-id="49040-130">**tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="49040-130">**string**</span></span> | <span data-ttu-id="49040-131">J</span><span class="sxs-lookup"><span data-stu-id="49040-131">Y</span></span>        | <span data-ttu-id="49040-132">Een tekenreeks die het te controleren domein identificeert.</span><span class="sxs-lookup"><span data-stu-id="49040-132">A string that identifies the domain to check.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="49040-133">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="49040-133">Request headers</span></span>

<span data-ttu-id="49040-134">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="49040-134">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="49040-135">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="49040-135">Request body</span></span>

<span data-ttu-id="49040-136">Geen</span><span class="sxs-lookup"><span data-stu-id="49040-136">None</span></span>

### <a name="request-example"></a><span data-ttu-id="49040-137">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="49040-137">Request example</span></span>

```http
HEAD https://api.partnercenter.microsoft.com/v1/domains/contoso.onmicrosoft.com HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: cf5b00d6-9240-431c-a973-cc06c904e5bf
MS-CorrelationId: ec57501a-a4c3-45ee-ab2b-da4250545fc9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="49040-138">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="49040-138">REST response</span></span>

<span data-ttu-id="49040-139">Als het domein bestaat, is het niet beschikbaar voor gebruik en wordt de antwoordstatuscode 200 OK geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="49040-139">If the domain exists, it isn't available for use and a response status code 200 OK is returned.</span></span> <span data-ttu-id="49040-140">Als het domein niet wordt gevonden, is het beschikbaar voor gebruik en wordt de antwoordstatuscode 404 Niet gevonden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="49040-140">If the domain isn't found, it's available for use and a response status code 404 Not Found is returned.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="49040-141">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="49040-141">Response success and error codes</span></span>

<span data-ttu-id="49040-142">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="49040-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="49040-143">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="49040-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="49040-144">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="49040-144">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example-for-when-the-domain-is-already-in-use"></a><span data-ttu-id="49040-145">Voorbeeld van een reactie wanneer het domein al in gebruik is</span><span class="sxs-lookup"><span data-stu-id="49040-145">Response example for when the domain is already in use</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 0
MS-CorrelationId: ec57501a-a4c3-45ee-ab2b-da4250545fc9
MS-RequestId: cf5b00d6-9240-431c-a973-cc06c904e5bf
MS-CV: 7UXAHds8J0mNUCSp.0
MS-ServerId: 201022015
Date: Tue, 31 Jan 2017 22:22:35 GMT
```

### <a name="response-example-for-when-the-domain-is-available"></a><span data-ttu-id="49040-146">Voorbeeld van een reactie wanneer het domein beschikbaar is</span><span class="sxs-lookup"><span data-stu-id="49040-146">Response example for when the domain is available</span></span>

```http
HTTP/1.1 404 Not Found
Content-Length: 0
MS-CorrelationId: 54770745-17f0-433c-bd7b-0265e5b38f98
MS-RequestId: 1169a4cd-3be7-4e29-9cb3-0f78ffa2e91e
MS-CV: RRmc+bEw9U2e97CC.0
MS-ServerId: 202010406
Date: Tue, 31 Jan 2017 22:36:01 GMT
```
