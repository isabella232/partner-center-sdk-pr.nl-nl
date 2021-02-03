---
title: De kwalificaties van een klant ophalen
description: Meer informatie over hoe u asynchrone validatie kunt gebruiken om de kwalificatie van een klant te verkrijgen via de Partner Center-API. Partners kunnen deze gebruiken om onderwijs klanten te valideren.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 9f9b9aaddde0d66caf9c7ef32e8fba6d5e3aba36
ms.sourcegitcommit: 0c98496e972aebe10eba23822aa229125bfc035d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767653"
---
# <a name="get-a-customers-qualifications-via-asynchronous-validation"></a><span data-ttu-id="1a58f-104">De kwalificaties van een klant ophalen via asynchrone validatie</span><span class="sxs-lookup"><span data-stu-id="1a58f-104">Get a customer's qualifications via asynchronous validation</span></span>

<span data-ttu-id="1a58f-105">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="1a58f-105">**Applies To**</span></span>

- <span data-ttu-id="1a58f-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="1a58f-106">Partner Center</span></span>

<span data-ttu-id="1a58f-107">Meer informatie over hoe u de kwalificaties van een klant asynchroon kunt verkrijgen via partner Center-Api's.</span><span class="sxs-lookup"><span data-stu-id="1a58f-107">Learn how to get a customer's qualifications asynchronously via Partner Center APIs.</span></span> <span data-ttu-id="1a58f-108">Zie [de kwalificatie van een klant ophalen via synchrone validatie](get-customer-qualification-synchronous.md)voor meer informatie over hoe u dit synchroon kunt doen.</span><span class="sxs-lookup"><span data-stu-id="1a58f-108">To learn how to do this synchronously, see [Get a customer's qualification via synchronous validation](get-customer-qualification-synchronous.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1a58f-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1a58f-109">Prerequisites</span></span>

- <span data-ttu-id="1a58f-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1a58f-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1a58f-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="1a58f-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="1a58f-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1a58f-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="1a58f-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="1a58f-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="1a58f-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="1a58f-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="1a58f-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="1a58f-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="1a58f-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="1a58f-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="1a58f-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1a58f-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="1a58f-118">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="1a58f-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1a58f-119">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1a58f-119">Request syntax</span></span>

| <span data-ttu-id="1a58f-120">Methode</span><span class="sxs-lookup"><span data-stu-id="1a58f-120">Method</span></span>  | <span data-ttu-id="1a58f-121">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="1a58f-121">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1a58f-122">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="1a58f-122">**GET**</span></span> | <span data-ttu-id="1a58f-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Qualifications http/1.1</span><span class="sxs-lookup"><span data-stu-id="1a58f-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/qualifications HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="1a58f-124">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="1a58f-124">URI parameter</span></span>

<span data-ttu-id="1a58f-125">Deze tabel bevat de vereiste query parameter om alle kwalificaties op te halen.</span><span class="sxs-lookup"><span data-stu-id="1a58f-125">This table lists the required query parameter to get all the qualification.</span></span>

| <span data-ttu-id="1a58f-126">Naam</span><span class="sxs-lookup"><span data-stu-id="1a58f-126">Name</span></span>               | <span data-ttu-id="1a58f-127">Type</span><span class="sxs-lookup"><span data-stu-id="1a58f-127">Type</span></span>   | <span data-ttu-id="1a58f-128">Vereist</span><span class="sxs-lookup"><span data-stu-id="1a58f-128">Required</span></span> | <span data-ttu-id="1a58f-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1a58f-129">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="1a58f-130">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="1a58f-130">**customer-tenant-id**</span></span> | <span data-ttu-id="1a58f-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="1a58f-131">string</span></span> | <span data-ttu-id="1a58f-132">Yes</span><span class="sxs-lookup"><span data-stu-id="1a58f-132">Yes</span></span>      | <span data-ttu-id="1a58f-133">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="1a58f-133">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="1a58f-134">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="1a58f-134">Request headers</span></span>

<span data-ttu-id="1a58f-135">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="1a58f-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1a58f-136">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="1a58f-136">Request body</span></span>

<span data-ttu-id="1a58f-137">Geen.</span><span class="sxs-lookup"><span data-stu-id="1a58f-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="1a58f-138">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1a58f-138">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a><span data-ttu-id="1a58f-139">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="1a58f-139">REST response</span></span>

<span data-ttu-id="1a58f-140">Als deze methode is geslaagd, wordt een verzameling kwalificaties in de antwoord tekst geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1a58f-140">If successful, this method returns a collection of qualifications in the response body.</span></span>  <span data-ttu-id="1a58f-141">Hieronder vindt u voor beelden van de **Get** -aanroep voor een klant met de **opleidings** kwalificatie.</span><span class="sxs-lookup"><span data-stu-id="1a58f-141">Below are examples of the **GET** call on a customer with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1a58f-142">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="1a58f-142">Response success and error codes</span></span>

<span data-ttu-id="1a58f-143">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="1a58f-143">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1a58f-144">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="1a58f-144">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1a58f-145">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="1a58f-145">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-examples"></a><span data-ttu-id="1a58f-146">Antwoord voorbeelden</span><span class="sxs-lookup"><span data-stu-id="1a58f-146">Response examples</span></span>

<span data-ttu-id="1a58f-147">In deze sectie vindt u antwoorden die kunnen worden weer gegeven wanneer een klant `vettingStatus` :</span><span class="sxs-lookup"><span data-stu-id="1a58f-147">This section shows responses you might receive when a customer's `vettingStatus` is:</span></span>

- <span data-ttu-id="1a58f-148">Goedgekeurd</span><span class="sxs-lookup"><span data-stu-id="1a58f-148">Approved</span></span>
- <span data-ttu-id="1a58f-149">Wordt gecontroleerd</span><span class="sxs-lookup"><span data-stu-id="1a58f-149">In Review</span></span>
- <span data-ttu-id="1a58f-150">Geweigerd</span><span class="sxs-lookup"><span data-stu-id="1a58f-150">Denied</span></span>

<span data-ttu-id="1a58f-151">**Goedgekeurd** voor beeld:</span><span class="sxs-lookup"><span data-stu-id="1a58f-151">**Approved** example:</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
[
    {
        "qualification": "Education",
        "vettingStatus": "Approved",
    }
]

```

<span data-ttu-id="1a58f-152">**In** dit voor beeld:</span><span class="sxs-lookup"><span data-stu-id="1a58f-152">**In Review** example:</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
[
    {
        "qualification": "Education",
        "vettingStatus": "InReview",
        "vettingCreatedDate": "2020-12-03T10:37:38.885Z" // UTC
    }
]

```

<span data-ttu-id="1a58f-153">Voor beeld van **geweigerd** :</span><span class="sxs-lookup"><span data-stu-id="1a58f-153">**Denied** example:</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
[
    {
        "qualification": "Education",
        "vettingStatus": "Denied",
        "vettingReason": "Not an Education Customer", // example Vetting Reason
        "vettingCreatedDate": "2020-12-03T10:37:38.885Z" // UTC
    }
]

```

## <a name="related-articles"></a><span data-ttu-id="1a58f-154">Verwante artikelen:</span><span class="sxs-lookup"><span data-stu-id="1a58f-154">Related articles</span></span>

- [<span data-ttu-id="1a58f-155">De kwalificaties van een klant bijwerken</span><span class="sxs-lookup"><span data-stu-id="1a58f-155">Update a customer's qualifications</span></span>](update-a-customer-s-qualifications.md)