---
title: Beschikbaarheid van domein verifiëren
description: Bepalen of een domein beschikbaar is voor gebruik.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 84edb5b7510642ec44dad3d4f92349e40eb10b24
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767463"
---
# <a name="verify-domain-availability"></a><span data-ttu-id="2efda-103">Beschikbaarheid van domein verifiëren</span><span class="sxs-lookup"><span data-stu-id="2efda-103">Verify domain availability</span></span>

<span data-ttu-id="2efda-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="2efda-104">**Applies To**</span></span>

- <span data-ttu-id="2efda-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="2efda-105">Partner Center</span></span>
- <span data-ttu-id="2efda-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="2efda-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="2efda-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="2efda-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="2efda-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2efda-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2efda-109">Bepalen of een domein beschikbaar is voor gebruik.</span><span class="sxs-lookup"><span data-stu-id="2efda-109">How to determine if a domain is available for use.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2efda-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2efda-110">Prerequisites</span></span>

- <span data-ttu-id="2efda-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2efda-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2efda-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="2efda-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="2efda-113">Een domein (bijvoorbeeld `contoso.onmicrosoft.com` ).</span><span class="sxs-lookup"><span data-stu-id="2efda-113">A domain (for example `contoso.onmicrosoft.com`).</span></span>

## <a name="c"></a><span data-ttu-id="2efda-114">C\#</span><span class="sxs-lookup"><span data-stu-id="2efda-114">C\#</span></span>

<span data-ttu-id="2efda-115">Als u wilt controleren of er een domein beschikbaar is, roept u [**IAggregatePartner. domains**](/dotnet/api/microsoft.store.partnercenter.ipartner.domains) aan om een interface voor domein bewerkingen te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="2efda-115">To verify if a domain is available, first call [**IAggregatePartner.Domains**](/dotnet/api/microsoft.store.partnercenter.ipartner.domains) to obtain an interface to domain operations.</span></span> <span data-ttu-id="2efda-116">Roep vervolgens de methode [**ByDomain**](/dotnet/api/microsoft.store.partnercenter.domains.idomaincollection.bydomain) aan met het te controleren domein.</span><span class="sxs-lookup"><span data-stu-id="2efda-116">Then call the [**ByDomain**](/dotnet/api/microsoft.store.partnercenter.domains.idomaincollection.bydomain) method with the domain to check.</span></span> <span data-ttu-id="2efda-117">Met deze methode wordt een interface opgehaald voor de bewerkingen die beschikbaar zijn voor een specifiek domein.</span><span class="sxs-lookup"><span data-stu-id="2efda-117">This method retrieves an interface to the operations available for a specific domain.</span></span> <span data-ttu-id="2efda-118">Roep tot slot de methode [**Exists**](/dotnet/api/microsoft.store.partnercenter.domains.idomain.exists) aan om te zien of het domein al bestaat.</span><span class="sxs-lookup"><span data-stu-id="2efda-118">Finally, call the [**Exists**](/dotnet/api/microsoft.store.partnercenter.domains.idomain.exists) method to see if the domain already exists.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// const string domain = "contoso.onmicrosoft.com";

bool result = partnerOperations.Domains.ByDomain(domain).Exists();
```

<span data-ttu-id="2efda-119">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="2efda-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="2efda-120">**Project**: Partner Center SDK-voor beelden **klasse**: CheckDomainAvailability.cs</span><span class="sxs-lookup"><span data-stu-id="2efda-120">**Project**: Partner Center SDK Samples **Class**: CheckDomainAvailability.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="2efda-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="2efda-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2efda-122">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2efda-122">Request syntax</span></span>

| <span data-ttu-id="2efda-123">Methode</span><span class="sxs-lookup"><span data-stu-id="2efda-123">Method</span></span>   | <span data-ttu-id="2efda-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="2efda-124">Request URI</span></span>                                                              |
|----------|--------------------------------------------------------------------------|
| <span data-ttu-id="2efda-125">**HOREN**</span><span class="sxs-lookup"><span data-stu-id="2efda-125">**HEAD**</span></span> | <span data-ttu-id="2efda-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/domains/{Domain} http/1.1</span><span class="sxs-lookup"><span data-stu-id="2efda-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/domains/{domain} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="2efda-127">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="2efda-127">URI parameter</span></span>

<span data-ttu-id="2efda-128">Gebruik de volgende query parameter om de beschik baarheid van het domein te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="2efda-128">Use the following query parameter to verify domain availability.</span></span>

| <span data-ttu-id="2efda-129">Naam</span><span class="sxs-lookup"><span data-stu-id="2efda-129">Name</span></span>       | <span data-ttu-id="2efda-130">Type</span><span class="sxs-lookup"><span data-stu-id="2efda-130">Type</span></span>       | <span data-ttu-id="2efda-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="2efda-131">Required</span></span> | <span data-ttu-id="2efda-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2efda-132">Description</span></span>                                   |
|------------|------------|----------|-----------------------------------------------|
| <span data-ttu-id="2efda-133">**domeinen**</span><span class="sxs-lookup"><span data-stu-id="2efda-133">**domain**</span></span> | <span data-ttu-id="2efda-134">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="2efda-134">**string**</span></span> | <span data-ttu-id="2efda-135">J</span><span class="sxs-lookup"><span data-stu-id="2efda-135">Y</span></span>        | <span data-ttu-id="2efda-136">Een teken reeks waarmee het te controleren domein wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="2efda-136">A string that identifies the domain to check.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="2efda-137">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="2efda-137">Request headers</span></span>

<span data-ttu-id="2efda-138">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2efda-138">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2efda-139">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="2efda-139">Request body</span></span>

<span data-ttu-id="2efda-140">Geen</span><span class="sxs-lookup"><span data-stu-id="2efda-140">None</span></span>

### <a name="request-example"></a><span data-ttu-id="2efda-141">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2efda-141">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="2efda-142">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="2efda-142">REST response</span></span>

<span data-ttu-id="2efda-143">Als het domein bestaat, kan het niet worden gebruikt en wordt de antwoord status code 200 OK geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2efda-143">If the domain exists, it isn't available for use and a response status code 200 OK is returned.</span></span> <span data-ttu-id="2efda-144">Als het domein niet wordt gevonden, is het beschikbaar voor gebruik en wordt de antwoord status code 404 niet gevonden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2efda-144">If the domain isn't found, it's available for use and a response status code 404 Not Found is returned.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2efda-145">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="2efda-145">Response success and error codes</span></span>

<span data-ttu-id="2efda-146">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="2efda-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2efda-147">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="2efda-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2efda-148">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="2efda-148">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example-for-when-the-domain-is-already-in-use"></a><span data-ttu-id="2efda-149">Antwoord voorbeeld voor wanneer het domein al in gebruik is</span><span class="sxs-lookup"><span data-stu-id="2efda-149">Response example for when the domain is already in use</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 0
MS-CorrelationId: ec57501a-a4c3-45ee-ab2b-da4250545fc9
MS-RequestId: cf5b00d6-9240-431c-a973-cc06c904e5bf
MS-CV: 7UXAHds8J0mNUCSp.0
MS-ServerId: 201022015
Date: Tue, 31 Jan 2017 22:22:35 GMT
```

### <a name="response-example-for-when-the-domain-is-available"></a><span data-ttu-id="2efda-150">Antwoord voorbeeld voor wanneer het domein beschikbaar is</span><span class="sxs-lookup"><span data-stu-id="2efda-150">Response example for when the domain is available</span></span>

```http
HTTP/1.1 404 Not Found
Content-Length: 0
MS-CorrelationId: 54770745-17f0-433c-bd7b-0265e5b38f98
MS-RequestId: 1169a4cd-3be7-4e29-9cb3-0f78ffa2e91e
MS-CV: RRmc+bEw9U2e97CC.0
MS-ServerId: 202010406
Date: Tue, 31 Jan 2017 22:36:01 GMT
```
