---
title: Kwalificaties van een klant krijgen
description: Meer informatie over het gebruik van asynchrone validatie om de kwalificatie van een klant te krijgen via Partner Center API. Partners kunnen dit gebruiken om Education-klanten te valideren.
ms.date: 05/17/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 4795b6e1ad008f9d854dc7efbee0c2099aefa609
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446306"
---
# <a name="get-a-customers-qualification-asynchronously"></a><span data-ttu-id="27987-104">De kwalificatie van een klant asynchroon krijgen</span><span class="sxs-lookup"><span data-stu-id="27987-104">Get a customer's qualification asynchronously</span></span>

<span data-ttu-id="27987-105">De kwalificaties van een klant asynchroon krijgen.</span><span class="sxs-lookup"><span data-stu-id="27987-105">How to get a customer's qualifications asynchronously.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="27987-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="27987-106">Prerequisites</span></span>

- <span data-ttu-id="27987-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="27987-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="27987-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="27987-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="27987-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="27987-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="27987-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="27987-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="27987-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="27987-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="27987-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="27987-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="27987-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="27987-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="27987-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="27987-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="27987-115">C\#</span><span class="sxs-lookup"><span data-stu-id="27987-115">C\#</span></span>

<span data-ttu-id="27987-116">Als u de kwalificaties van een klant wilt weten, roept u de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id.</span><span class="sxs-lookup"><span data-stu-id="27987-116">To get a customer's qualifications, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="27987-117">Gebruik vervolgens de eigenschap [**Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) om een [**ICustomerQualification-interface op te**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) halen.</span><span class="sxs-lookup"><span data-stu-id="27987-117">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="27987-118">Roep ten slotte `GetQualifications()` of aan om de `GetQualificationsAsync()` kwalificaties van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="27987-118">Finally, call `GetQualifications()` or `GetQualificationsAsync()` to retrieve the customer's qualifications.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
var customerQualifications = partnerOperations.Customers.ById(customerId).Qualification.GetQualifications();
```

<span data-ttu-id="27987-119">**Voorbeeld:** [consolevoorbeeld-app.](https://github.com/microsoft/Partner-Center-DotNet-Samples)</span><span class="sxs-lookup"><span data-stu-id="27987-119">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="27987-120">**Project:** Klasse SdkSamples: GetCustomerQualifications.cs </span><span class="sxs-lookup"><span data-stu-id="27987-120">**Project**: SdkSamples **Class**: GetCustomerQualifications.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="27987-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="27987-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="27987-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="27987-122">Request syntax</span></span>

| <span data-ttu-id="27987-123">Methode</span><span class="sxs-lookup"><span data-stu-id="27987-123">Method</span></span>  | <span data-ttu-id="27987-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="27987-124">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="27987-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="27987-125">**GET**</span></span> | <span data-ttu-id="27987-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/kwalificaties HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="27987-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/qualifications HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="27987-127">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="27987-127">URI parameter</span></span>

<span data-ttu-id="27987-128">Deze tabel bevat de vereiste queryparameter om alle kwalificaties op te halen.</span><span class="sxs-lookup"><span data-stu-id="27987-128">This table lists the required query parameter to get all the qualification.</span></span>

| <span data-ttu-id="27987-129">Naam</span><span class="sxs-lookup"><span data-stu-id="27987-129">Name</span></span>               | <span data-ttu-id="27987-130">Type</span><span class="sxs-lookup"><span data-stu-id="27987-130">Type</span></span>   | <span data-ttu-id="27987-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="27987-131">Required</span></span> | <span data-ttu-id="27987-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="27987-132">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="27987-133">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="27987-133">**customer-tenant-id**</span></span> | <span data-ttu-id="27987-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="27987-134">string</span></span> | <span data-ttu-id="27987-135">Ja</span><span class="sxs-lookup"><span data-stu-id="27987-135">Yes</span></span>      | <span data-ttu-id="27987-136">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="27987-136">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="27987-137">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="27987-137">Request headers</span></span>

<span data-ttu-id="27987-138">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="27987-138">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="27987-139">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="27987-139">Request body</span></span>

<span data-ttu-id="27987-140">Geen.</span><span class="sxs-lookup"><span data-stu-id="27987-140">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="27987-141">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="27987-141">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a><span data-ttu-id="27987-142">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="27987-142">REST response</span></span>

<span data-ttu-id="27987-143">Als dit lukt, retourneert deze methode een verzameling kwalificaties in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="27987-143">If successful, this method returns a collection of qualifications in the response body.</span></span>  <span data-ttu-id="27987-144">Hieronder vindt u  voorbeelden van de GET-aanroep van een klant met de **kwalificatie Opleiding.**</span><span class="sxs-lookup"><span data-stu-id="27987-144">Below are examples of the **GET** call on a customer with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="27987-145">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="27987-145">Response success and error codes</span></span>

<span data-ttu-id="27987-146">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="27987-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="27987-147">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="27987-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="27987-148">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="27987-148">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-examples"></a><span data-ttu-id="27987-149">Antwoordvoorbeelden</span><span class="sxs-lookup"><span data-stu-id="27987-149">Response examples</span></span>

#### <a name="approved"></a><span data-ttu-id="27987-150">Goedgekeurd</span><span class="sxs-lookup"><span data-stu-id="27987-150">Approved</span></span>

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

#### <a name="in-review"></a><span data-ttu-id="27987-151">Wordt gecontroleerd</span><span class="sxs-lookup"><span data-stu-id="27987-151">In Review</span></span>

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

#### <a name="denied"></a><span data-ttu-id="27987-152">Geweigerd</span><span class="sxs-lookup"><span data-stu-id="27987-152">Denied</span></span>

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

#### <a name="state-owned-entity-samples"></a><span data-ttu-id="27987-153">Voorbeelden van entiteiten die eigendom zijn van de staat</span><span class="sxs-lookup"><span data-stu-id="27987-153">State Owned Entity Samples</span></span>

<span data-ttu-id="27987-154">**Statusentiteit via POST-voorbeeld**</span><span class="sxs-lookup"><span data-stu-id="27987-154">**State Owned Entity via POST sample**</span></span>

```csharp

//SOE
POST {customer_id}/qualifications
{
“qualification”: “StateOwnedEntity”
}

//

```

<span data-ttu-id="27987-155">**Voorbeeld van statusentiteit via Kwalificaties krijgen**</span><span class="sxs-lookup"><span data-stu-id="27987-155">**State Owned Entity via Get Qualifications sample**</span></span>

```csharp

//SOE:
GET {customer_id}/qualifications
[
    {
        “qualification”: “StateOwnedEntity”
    }
]

```

<span data-ttu-id="27987-156">**Entiteit in eigendom van de staat via Kwalificaties krijgen met onderwijs**</span><span class="sxs-lookup"><span data-stu-id="27987-156">**State Owned Entity via Get Qualifications with Education**</span></span>

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

<span data-ttu-id="27987-157">**Entiteit in eigendom van de staat via Kwalificaties krijgen met GCC**</span><span class="sxs-lookup"><span data-stu-id="27987-157">**State Owned Entity via Get Qualifications with GCC**</span></span>

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

## <a name="related-articles"></a><span data-ttu-id="27987-158">Verwante artikelen:</span><span class="sxs-lookup"><span data-stu-id="27987-158">Related articles</span></span>

- [<span data-ttu-id="27987-159">Kwalificaties van een klant bijwerken</span><span class="sxs-lookup"><span data-stu-id="27987-159">Update a customer's qualifications</span></span>](./update-customer-qualification-asynchronous.md)
