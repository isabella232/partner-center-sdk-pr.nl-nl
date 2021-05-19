---
title: Kwalificaties van een klant krijgen
description: Meer informatie over het gebruik van asynchrone validatie om de kwalificatie van een klant te krijgen via Partner Center API. Partners kunnen dit gebruiken om Education-klanten te valideren.
ms.date: 05/17/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: df605e4d400d29e14fd0b44bef34f88bbc7ca8b2
ms.sourcegitcommit: 7d59c58ee36b217bd5cac089f918059e9dbb8a62
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2021
ms.locfileid: "110027925"
---
# <a name="get-a-customers-qualification-asynchronously"></a><span data-ttu-id="6f3b9-104">De kwalificatie van een klant asynchroon krijgen</span><span class="sxs-lookup"><span data-stu-id="6f3b9-104">Get a customer's qualification asynchronously</span></span>

<span data-ttu-id="6f3b9-105">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="6f3b9-105">**Applies To**</span></span>

- <span data-ttu-id="6f3b9-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="6f3b9-106">Partner Center</span></span>

<span data-ttu-id="6f3b9-107">De kwalificaties van een klant asynchroon krijgen.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-107">How to get a customer's qualifications asynchronously.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6f3b9-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6f3b9-108">Prerequisites</span></span>

- <span data-ttu-id="6f3b9-109">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6f3b9-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6f3b9-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="6f3b9-111">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6f3b9-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="6f3b9-112">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="6f3b9-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="6f3b9-113">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="6f3b9-114">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="6f3b9-115">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="6f3b9-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="6f3b9-116">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6f3b9-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="6f3b9-117">C\#</span><span class="sxs-lookup"><span data-stu-id="6f3b9-117">C\#</span></span>

<span data-ttu-id="6f3b9-118">Als u de kwalificaties van een klant wilt weten, roept u de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-118">To get a customer's qualifications, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="6f3b9-119">Gebruik vervolgens de eigenschap [**Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) om een [**ICustomerQualification-interface op te**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) halen.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-119">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="6f3b9-120">Roep ten slotte `GetQualifications()` of aan om de `GetQualificationsAsync()` kwalificaties van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-120">Finally, call `GetQualifications()` or `GetQualificationsAsync()` to retrieve the customer's qualifications.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
var customerQualifications = partnerOperations.Customers.ById(customerId).Qualification.GetQualifications();
```

<span data-ttu-id="6f3b9-121">**Voorbeeld:** [consolevoorbeeld-app](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span><span class="sxs-lookup"><span data-stu-id="6f3b9-121">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="6f3b9-122">**Project**: SdkSamples-klasse : GetCustomerQualifications.cs </span><span class="sxs-lookup"><span data-stu-id="6f3b9-122">**Project**: SdkSamples **Class**: GetCustomerQualifications.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="6f3b9-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="6f3b9-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6f3b9-124">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="6f3b9-124">Request syntax</span></span>

| <span data-ttu-id="6f3b9-125">Methode</span><span class="sxs-lookup"><span data-stu-id="6f3b9-125">Method</span></span>  | <span data-ttu-id="6f3b9-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="6f3b9-126">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6f3b9-127">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="6f3b9-127">**GET**</span></span> | <span data-ttu-id="6f3b9-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/kwalificaties HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6f3b9-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/qualifications HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="6f3b9-129">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="6f3b9-129">URI parameter</span></span>

<span data-ttu-id="6f3b9-130">Deze tabel bevat de vereiste queryparameter om alle kwalificaties op te halen.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-130">This table lists the required query parameter to get all the qualification.</span></span>

| <span data-ttu-id="6f3b9-131">Naam</span><span class="sxs-lookup"><span data-stu-id="6f3b9-131">Name</span></span>               | <span data-ttu-id="6f3b9-132">Type</span><span class="sxs-lookup"><span data-stu-id="6f3b9-132">Type</span></span>   | <span data-ttu-id="6f3b9-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="6f3b9-133">Required</span></span> | <span data-ttu-id="6f3b9-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6f3b9-134">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="6f3b9-135">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="6f3b9-135">**customer-tenant-id**</span></span> | <span data-ttu-id="6f3b9-136">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6f3b9-136">string</span></span> | <span data-ttu-id="6f3b9-137">Yes</span><span class="sxs-lookup"><span data-stu-id="6f3b9-137">Yes</span></span>      | <span data-ttu-id="6f3b9-138">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-138">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="6f3b9-139">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="6f3b9-139">Request headers</span></span>

<span data-ttu-id="6f3b9-140">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="6f3b9-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6f3b9-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="6f3b9-141">Request body</span></span>

<span data-ttu-id="6f3b9-142">Geen.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6f3b9-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6f3b9-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a><span data-ttu-id="6f3b9-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="6f3b9-144">REST response</span></span>

<span data-ttu-id="6f3b9-145">Als dit lukt, retourneert deze methode een verzameling kwalificaties in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-145">If successful, this method returns a collection of qualifications in the response body.</span></span>  <span data-ttu-id="6f3b9-146">Hieronder vindt u voorbeelden van de **GET-aanroep** van een klant met de kwalificatie **voor** het onderwijs.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-146">Below are examples of the **GET** call on a customer with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6f3b9-147">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="6f3b9-147">Response success and error codes</span></span>

<span data-ttu-id="6f3b9-148">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6f3b9-149">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="6f3b9-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6f3b9-150">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="6f3b9-150">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-examples"></a><span data-ttu-id="6f3b9-151">Antwoordvoorbeelden</span><span class="sxs-lookup"><span data-stu-id="6f3b9-151">Response examples</span></span>

#### <a name="approved"></a><span data-ttu-id="6f3b9-152">Goedgekeurd</span><span class="sxs-lookup"><span data-stu-id="6f3b9-152">Approved</span></span>

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

#### <a name="in-review"></a><span data-ttu-id="6f3b9-153">Wordt gecontroleerd</span><span class="sxs-lookup"><span data-stu-id="6f3b9-153">In Review</span></span>

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

#### <a name="denied"></a><span data-ttu-id="6f3b9-154">Geweigerd</span><span class="sxs-lookup"><span data-stu-id="6f3b9-154">Denied</span></span>

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

#### <a name="state-owned-entity-samples"></a><span data-ttu-id="6f3b9-155">Voorbeelden van entiteiten die eigendom zijn van de staat</span><span class="sxs-lookup"><span data-stu-id="6f3b9-155">State Owned Entity Samples</span></span>

<span data-ttu-id="6f3b9-156">**Voorbeeld van entiteit in staats-eigendom via POST**</span><span class="sxs-lookup"><span data-stu-id="6f3b9-156">**State Owned Entity via POST sample**</span></span>

```csharp

//SOE
POST {customer_id}/qualifications
{
“qualification”: “StateOwnedEntity”
}

//

```

<span data-ttu-id="6f3b9-157">**Voorbeeld van statusentiteit via Kwalificaties krijgen**</span><span class="sxs-lookup"><span data-stu-id="6f3b9-157">**State Owned Entity via Get Qualifications sample**</span></span>

```csharp

//SOE:
GET {customer_id}/qualifications
[
    {
        “qualification”: “StateOwnedEntity”
    }
]

```

<span data-ttu-id="6f3b9-158">**Entiteit in eigendom van de staat via Kwalificaties krijgen met onderwijs**</span><span class="sxs-lookup"><span data-stu-id="6f3b9-158">**State Owned Entity via Get Qualifications with Education**</span></span>

```csharp

GET {customer_id}/qualifications
[
    {
        “qualification”: “Education”,
        “vettingStatus”: “Approved”
    },
{
        “qualification”: “StateOwnedEntity”
    }
]

```

<span data-ttu-id="6f3b9-159">**Entiteit in eigendom van de staat via kwalificaties met GCC**</span><span class="sxs-lookup"><span data-stu-id="6f3b9-159">**State Owned Entity via Get Qualifications with GCC**</span></span>

```csharp

GET {customer_id}/qualifications
[
    {
        “qualification”: “GovernmentCommunityCloud”,
        “vettingStatus”: “Approved”,
        “vettingCreateDate”: “2021-05-06T19:59:56.6832021+00:00”
    },
{
        “qualification”: “StateOwnedEntity”
    }
]

```

## <a name="related-articles"></a><span data-ttu-id="6f3b9-160">Verwante artikelen:</span><span class="sxs-lookup"><span data-stu-id="6f3b9-160">Related articles</span></span>

- [<span data-ttu-id="6f3b9-161">Kwalificaties van een klant bijwerken</span><span class="sxs-lookup"><span data-stu-id="6f3b9-161">Update a customer's qualifications</span></span>](./update-customer-qualification-asynchronous.md)
