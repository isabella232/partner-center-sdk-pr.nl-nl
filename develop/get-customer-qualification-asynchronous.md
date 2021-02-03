---
title: De kwalificaties van een klant ophalen
description: Meer informatie over hoe u asynchrone validatie kunt gebruiken om de kwalificatie van een klant te verkrijgen via de Partner Center-API. Partners kunnen deze gebruiken om onderwijs klanten te valideren.
ms.date: 01/21/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 130ee276461e3390ac78ac7abd8baeefe6a70d7c
ms.sourcegitcommit: 97f93caa57df6c64fe19868e6b2a0f7937226b51
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/21/2021
ms.locfileid: "98636380"
---
# <a name="get-a-customers-qualification-asynchronously"></a><span data-ttu-id="5a40b-104">De kwalificatie asynchroon van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="5a40b-104">Get a customer's qualification asynchronously</span></span>

<span data-ttu-id="5a40b-105">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="5a40b-105">**Applies To**</span></span>

- <span data-ttu-id="5a40b-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="5a40b-106">Partner Center</span></span>

<span data-ttu-id="5a40b-107">Hoe u de kwalificaties van een klant asynchroon ophaalt.</span><span class="sxs-lookup"><span data-stu-id="5a40b-107">How to get a customer's qualifications asynchronously.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5a40b-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="5a40b-108">Prerequisites</span></span>

- <span data-ttu-id="5a40b-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5a40b-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5a40b-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="5a40b-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="5a40b-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5a40b-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="5a40b-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="5a40b-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="5a40b-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="5a40b-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="5a40b-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="5a40b-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="5a40b-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="5a40b-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="5a40b-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5a40b-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="5a40b-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="5a40b-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5a40b-118">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="5a40b-118">Request syntax</span></span>

| <span data-ttu-id="5a40b-119">Methode</span><span class="sxs-lookup"><span data-stu-id="5a40b-119">Method</span></span>  | <span data-ttu-id="5a40b-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="5a40b-120">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5a40b-121">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="5a40b-121">**GET**</span></span> | <span data-ttu-id="5a40b-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Qualifications http/1.1</span><span class="sxs-lookup"><span data-stu-id="5a40b-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/qualifications HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="5a40b-123">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="5a40b-123">URI parameter</span></span>

<span data-ttu-id="5a40b-124">Deze tabel bevat de vereiste query parameter om alle kwalificaties op te halen.</span><span class="sxs-lookup"><span data-stu-id="5a40b-124">This table lists the required query parameter to get all the qualification.</span></span>

| <span data-ttu-id="5a40b-125">Naam</span><span class="sxs-lookup"><span data-stu-id="5a40b-125">Name</span></span>               | <span data-ttu-id="5a40b-126">Type</span><span class="sxs-lookup"><span data-stu-id="5a40b-126">Type</span></span>   | <span data-ttu-id="5a40b-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="5a40b-127">Required</span></span> | <span data-ttu-id="5a40b-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5a40b-128">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="5a40b-129">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="5a40b-129">**customer-tenant-id**</span></span> | <span data-ttu-id="5a40b-130">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="5a40b-130">string</span></span> | <span data-ttu-id="5a40b-131">Yes</span><span class="sxs-lookup"><span data-stu-id="5a40b-131">Yes</span></span>      | <span data-ttu-id="5a40b-132">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="5a40b-132">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="5a40b-133">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="5a40b-133">Request headers</span></span>

<span data-ttu-id="5a40b-134">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5a40b-134">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5a40b-135">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="5a40b-135">Request body</span></span>

<span data-ttu-id="5a40b-136">Geen.</span><span class="sxs-lookup"><span data-stu-id="5a40b-136">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="5a40b-137">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="5a40b-137">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a><span data-ttu-id="5a40b-138">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="5a40b-138">REST response</span></span>

<span data-ttu-id="5a40b-139">Als deze methode is geslaagd, wordt een verzameling kwalificaties in de antwoord tekst geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="5a40b-139">If successful, this method returns a collection of qualifications in the response body.</span></span>  <span data-ttu-id="5a40b-140">Hieronder vindt u voor beelden van de **Get** -aanroep voor een klant met de **opleidings** kwalificatie.</span><span class="sxs-lookup"><span data-stu-id="5a40b-140">Below are examples of the **GET** call on a customer with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5a40b-141">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="5a40b-141">Response success and error codes</span></span>

<span data-ttu-id="5a40b-142">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="5a40b-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5a40b-143">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="5a40b-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5a40b-144">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="5a40b-144">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-examples"></a><span data-ttu-id="5a40b-145">Antwoord voorbeelden</span><span class="sxs-lookup"><span data-stu-id="5a40b-145">Response examples</span></span>

#### <a name="approved"></a><span data-ttu-id="5a40b-146">Goedgekeurd</span><span class="sxs-lookup"><span data-stu-id="5a40b-146">Approved</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
{
    "qualifications": [
        {
            "qualification": "Education",
            "vettingStatus": "Approved",
        }
    ]
}

```

#### <a name="in-review"></a><span data-ttu-id="5a40b-147">Wordt gecontroleerd</span><span class="sxs-lookup"><span data-stu-id="5a40b-147">In Review</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
{
    "qualifications": [
        {
            "qualification": "Education",
            "vettingStatus": "InReview",
            "vettingCreatedDate": "2020-12-03T10:37:38.885Z" // UTC
        }
    ]
}

```

#### <a name="denied"></a><span data-ttu-id="5a40b-148">Geweigerd</span><span class="sxs-lookup"><span data-stu-id="5a40b-148">Denied</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
{
    "qualifications": [
        {
            "qualification": "Education",
            "vettingStatus": "Denied",
            "vettingReason": "Not an Education Customer", // example Vetting Reason
            "vettingCreatedDate": "2020-12-03T10:37:38.885Z" // UTC
        }
    ]
}

```

## <a name="related-articles"></a><span data-ttu-id="5a40b-149">Verwante artikelen:</span><span class="sxs-lookup"><span data-stu-id="5a40b-149">Related articles</span></span>

- [<span data-ttu-id="5a40b-150">De kwalificaties van een klant bijwerken</span><span class="sxs-lookup"><span data-stu-id="5a40b-150">Update a customer's qualifications</span></span>](update-a-customer-s-qualifications.md)