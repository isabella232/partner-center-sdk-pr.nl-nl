---
title: Een overdracht intrekken
description: Het intrekken van een gemaakte overdracht van abonnementen voor een klant.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 3c15cf09b4e466e178c7afb5f9d324fe1199418e
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445201"
---
# <a name="withdraw-a-transfer"></a><span data-ttu-id="e5944-103">Een overdracht intrekken</span><span class="sxs-lookup"><span data-stu-id="e5944-103">Withdraw a transfer</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e5944-104">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e5944-104">Prerequisites</span></span>

- <span data-ttu-id="e5944-105">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e5944-105">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e5944-106">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="e5944-106">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="e5944-107">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e5944-107">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e5944-108">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="e5944-108">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e5944-109">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="e5944-109">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e5944-110">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="e5944-110">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e5944-111">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="e5944-111">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e5944-112">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e5944-112">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="e5944-113">Een overdrachts-id voor een bestaande overdracht.</span><span class="sxs-lookup"><span data-stu-id="e5944-113">A transfer identifier for an existing transfer.</span></span>

## <a name="rest-request"></a><span data-ttu-id="e5944-114">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e5944-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e5944-115">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e5944-115">Request syntax</span></span>

| <span data-ttu-id="e5944-116">Methode</span><span class="sxs-lookup"><span data-stu-id="e5944-116">Method</span></span>    | <span data-ttu-id="e5944-117">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e5944-117">Request URI</span></span>                                                                                                 |
|-----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e5944-118">**Verwijderen**</span><span class="sxs-lookup"><span data-stu-id="e5944-118">**DELETE**</span></span>| <span data-ttu-id="e5944-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e5944-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span></span>      |

### <a name="uri-parameter"></a><span data-ttu-id="e5944-120">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="e5944-120">URI parameter</span></span>

<span data-ttu-id="e5944-121">Gebruik de volgende padparameter om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="e5944-121">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="e5944-122">Naam</span><span class="sxs-lookup"><span data-stu-id="e5944-122">Name</span></span>            | <span data-ttu-id="e5944-123">Type</span><span class="sxs-lookup"><span data-stu-id="e5944-123">Type</span></span>     | <span data-ttu-id="e5944-124">Vereist</span><span class="sxs-lookup"><span data-stu-id="e5944-124">Required</span></span> | <span data-ttu-id="e5944-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e5944-125">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="e5944-126">**customer-id**</span><span class="sxs-lookup"><span data-stu-id="e5944-126">**customer-id**</span></span> | <span data-ttu-id="e5944-127">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e5944-127">string</span></span>   | <span data-ttu-id="e5944-128">Ja</span><span class="sxs-lookup"><span data-stu-id="e5944-128">Yes</span></span>      | <span data-ttu-id="e5944-129">Een met GUID opgemaakte klant-id die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="e5944-129">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="e5944-130">**transfer-id**</span><span class="sxs-lookup"><span data-stu-id="e5944-130">**transfer-id**</span></span> | <span data-ttu-id="e5944-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e5944-131">string</span></span>   | <span data-ttu-id="e5944-132">Ja</span><span class="sxs-lookup"><span data-stu-id="e5944-132">Yes</span></span>      | <span data-ttu-id="e5944-133">Een met GUID opgemaakte overdrachts-id die de overdracht identificeert.</span><span class="sxs-lookup"><span data-stu-id="e5944-133">A GUID formatted transfer-id that identifies the transfer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="e5944-134">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e5944-134">Request headers</span></span>

<span data-ttu-id="e5944-135">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e5944-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-example"></a><span data-ttu-id="e5944-136">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e5944-136">Request example</span></span>

```http
DELETE /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/transfers/67c5b05b-09b5-47ba-9047-5056fe2afa4f HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: cdf6e25c-7b32-4cc3-d8bc-53e0b37eebd8
MS-CorrelationId: 9041d76d-8915-43a8-8e82-00ca46a1a73d
Connection: keep-alive
```

## <a name="rest-response"></a><span data-ttu-id="e5944-137">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e5944-137">REST response</span></span>

<span data-ttu-id="e5944-138">Als dit lukt, retourneert deze methode Geen inhoud (204).</span><span class="sxs-lookup"><span data-stu-id="e5944-138">If successful, this method returns No Content (204).</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e5944-139">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e5944-139">Response success and error codes</span></span>

<span data-ttu-id="e5944-140">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e5944-140">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e5944-141">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e5944-141">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e5944-142">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="e5944-142">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e5944-143">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e5944-143">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 9041d76d-8915-43a8-8e82-00ca46a1a73d
MS-RequestId: cdf6e25c-7b32-4cc3-d8bc-53e0b37eebd8
Date: Tue, 24 Mar 2020 23:44:06 GMT
```
