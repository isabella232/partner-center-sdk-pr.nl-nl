---
title: Een overdracht intrekken
description: Een gemaakte overdracht van abonnementen voor een klant intrekken.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a9e1e2a33d21fc1338a36b8ac96b528e70b61c86
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767162"
---
# <a name="withdraw-a-transfer"></a><span data-ttu-id="cc655-103">Een overdracht intrekken</span><span class="sxs-lookup"><span data-stu-id="cc655-103">Withdraw a transfer</span></span>

<span data-ttu-id="cc655-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="cc655-104">**Applies to:**</span></span>

- <span data-ttu-id="cc655-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="cc655-105">Partner Center</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cc655-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cc655-106">Prerequisites</span></span>

- <span data-ttu-id="cc655-107">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cc655-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cc655-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="cc655-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="cc655-109">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cc655-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="cc655-110">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="cc655-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="cc655-111">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="cc655-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="cc655-112">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="cc655-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="cc655-113">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="cc655-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="cc655-114">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cc655-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="cc655-115">Een overdrachts-id voor een bestaande overdracht.</span><span class="sxs-lookup"><span data-stu-id="cc655-115">A transfer identifier for an existing transfer.</span></span>

## <a name="rest-request"></a><span data-ttu-id="cc655-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="cc655-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cc655-117">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cc655-117">Request syntax</span></span>

| <span data-ttu-id="cc655-118">Methode</span><span class="sxs-lookup"><span data-stu-id="cc655-118">Method</span></span>    | <span data-ttu-id="cc655-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="cc655-119">Request URI</span></span>                                                                                                 |
|-----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="cc655-120">**VERWIJDERD**</span><span class="sxs-lookup"><span data-stu-id="cc655-120">**DELETE**</span></span>| <span data-ttu-id="cc655-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/transfers/{Transfer-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="cc655-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span></span>      |

### <a name="uri-parameter"></a><span data-ttu-id="cc655-122">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="cc655-122">URI parameter</span></span>

<span data-ttu-id="cc655-123">Gebruik de volgende para meter voor het identificeren van de klant.</span><span class="sxs-lookup"><span data-stu-id="cc655-123">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="cc655-124">Naam</span><span class="sxs-lookup"><span data-stu-id="cc655-124">Name</span></span>            | <span data-ttu-id="cc655-125">Type</span><span class="sxs-lookup"><span data-stu-id="cc655-125">Type</span></span>     | <span data-ttu-id="cc655-126">Vereist</span><span class="sxs-lookup"><span data-stu-id="cc655-126">Required</span></span> | <span data-ttu-id="cc655-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cc655-127">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="cc655-128">**klant-id**</span><span class="sxs-lookup"><span data-stu-id="cc655-128">**customer-id**</span></span> | <span data-ttu-id="cc655-129">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="cc655-129">string</span></span>   | <span data-ttu-id="cc655-130">Yes</span><span class="sxs-lookup"><span data-stu-id="cc655-130">Yes</span></span>      | <span data-ttu-id="cc655-131">Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="cc655-131">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="cc655-132">**overdracht-id**</span><span class="sxs-lookup"><span data-stu-id="cc655-132">**transfer-id**</span></span> | <span data-ttu-id="cc655-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="cc655-133">string</span></span>   | <span data-ttu-id="cc655-134">Yes</span><span class="sxs-lookup"><span data-stu-id="cc655-134">Yes</span></span>      | <span data-ttu-id="cc655-135">Een door de GUID geformatteerde overdracht-id waarmee de overdracht wordt aangeduid.</span><span class="sxs-lookup"><span data-stu-id="cc655-135">A GUID formatted transfer-id that identifies the transfer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="cc655-136">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="cc655-136">Request headers</span></span>

<span data-ttu-id="cc655-137">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="cc655-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-example"></a><span data-ttu-id="cc655-138">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cc655-138">Request example</span></span>

```http
DELETE /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/transfers/67c5b05b-09b5-47ba-9047-5056fe2afa4f HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: cdf6e25c-7b32-4cc3-d8bc-53e0b37eebd8
MS-CorrelationId: 9041d76d-8915-43a8-8e82-00ca46a1a73d
Connection: keep-alive
```

## <a name="rest-response"></a><span data-ttu-id="cc655-139">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="cc655-139">REST response</span></span>

<span data-ttu-id="cc655-140">Als dit lukt, retourneert deze methode geen inhoud (204).</span><span class="sxs-lookup"><span data-stu-id="cc655-140">If successful, this method returns No Content (204).</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cc655-141">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="cc655-141">Response success and error codes</span></span>

<span data-ttu-id="cc655-142">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="cc655-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cc655-143">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="cc655-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="cc655-144">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="cc655-144">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="cc655-145">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="cc655-145">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 9041d76d-8915-43a8-8e82-00ca46a1a73d
MS-RequestId: cdf6e25c-7b32-4cc3-d8bc-53e0b37eebd8
Date: Tue, 24 Mar 2020 23:44:06 GMT
```
