---
title: De kwalificaties van een klant ophalen
description: Meer informatie over hoe u asynchrone validatie kunt gebruiken om de kwalificatie van een klant te verkrijgen via de Partner Center-API. Partners kunnen deze gebruiken om onderwijs klanten te valideren.
ms.date: 01/21/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 09801792c059873b9f6b842e99286eda09d38b1a
ms.sourcegitcommit: bbdb5f7c9ddd42c2fc4eaadbb67d61aeeae805ca
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/24/2021
ms.locfileid: "105030562"
---
# <a name="get-a-customers-qualification-asynchronously"></a><span data-ttu-id="f6330-104">De kwalificatie asynchroon van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="f6330-104">Get a customer's qualification asynchronously</span></span>

<span data-ttu-id="f6330-105">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="f6330-105">**Applies To**</span></span>

- <span data-ttu-id="f6330-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="f6330-106">Partner Center</span></span>

<span data-ttu-id="f6330-107">Hoe u de kwalificaties van een klant asynchroon ophaalt.</span><span class="sxs-lookup"><span data-stu-id="f6330-107">How to get a customer's qualifications asynchronously.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f6330-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f6330-108">Prerequisites</span></span>

- <span data-ttu-id="f6330-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f6330-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f6330-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="f6330-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="f6330-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f6330-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f6330-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="f6330-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f6330-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="f6330-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f6330-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="f6330-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f6330-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="f6330-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f6330-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f6330-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="f6330-117">C\#</span><span class="sxs-lookup"><span data-stu-id="f6330-117">C\#</span></span>

<span data-ttu-id="f6330-118">Als u de kwalificaties van een klant wilt ophalen, roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id.</span><span class="sxs-lookup"><span data-stu-id="f6330-118">To get a customer's qualifications, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="f6330-119">Gebruik vervolgens de [**Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) -eigenschap om een [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) -interface op te halen.</span><span class="sxs-lookup"><span data-stu-id="f6330-119">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="f6330-120">Roep ten slotte `GetQualifications()` `GetQualificationsAsync()` de kwalificaties van de klant aan of op te halen.</span><span class="sxs-lookup"><span data-stu-id="f6330-120">Finally, call `GetQualifications()` or `GetQualificationsAsync()` to retrieve the customer's qualifications.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
var customerQualifications = partnerOperations.Customers.ById(customerId).Qualification.GetQualifications();
```

<span data-ttu-id="f6330-121">Voor **beeld**: console-voor [beeld-app](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span><span class="sxs-lookup"><span data-stu-id="f6330-121">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="f6330-122">**Project**: SdkSamples- **klasse**: GetCustomerQualifications. cs</span><span class="sxs-lookup"><span data-stu-id="f6330-122">**Project**: SdkSamples **Class**: GetCustomerQualifications.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="f6330-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="f6330-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f6330-124">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="f6330-124">Request syntax</span></span>

| <span data-ttu-id="f6330-125">Methode</span><span class="sxs-lookup"><span data-stu-id="f6330-125">Method</span></span>  | <span data-ttu-id="f6330-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="f6330-126">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f6330-127">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="f6330-127">**GET**</span></span> | <span data-ttu-id="f6330-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Qualifications http/1.1</span><span class="sxs-lookup"><span data-stu-id="f6330-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/qualifications HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="f6330-129">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="f6330-129">URI parameter</span></span>

<span data-ttu-id="f6330-130">Deze tabel bevat de vereiste query parameter om alle kwalificaties op te halen.</span><span class="sxs-lookup"><span data-stu-id="f6330-130">This table lists the required query parameter to get all the qualification.</span></span>

| <span data-ttu-id="f6330-131">Naam</span><span class="sxs-lookup"><span data-stu-id="f6330-131">Name</span></span>               | <span data-ttu-id="f6330-132">Type</span><span class="sxs-lookup"><span data-stu-id="f6330-132">Type</span></span>   | <span data-ttu-id="f6330-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="f6330-133">Required</span></span> | <span data-ttu-id="f6330-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f6330-134">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="f6330-135">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="f6330-135">**customer-tenant-id**</span></span> | <span data-ttu-id="f6330-136">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="f6330-136">string</span></span> | <span data-ttu-id="f6330-137">Ja</span><span class="sxs-lookup"><span data-stu-id="f6330-137">Yes</span></span>      | <span data-ttu-id="f6330-138">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="f6330-138">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="f6330-139">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="f6330-139">Request headers</span></span>

<span data-ttu-id="f6330-140">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="f6330-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f6330-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="f6330-141">Request body</span></span>

<span data-ttu-id="f6330-142">Geen.</span><span class="sxs-lookup"><span data-stu-id="f6330-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="f6330-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="f6330-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a><span data-ttu-id="f6330-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="f6330-144">REST response</span></span>

<span data-ttu-id="f6330-145">Als deze methode is geslaagd, wordt een verzameling kwalificaties in de antwoord tekst geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f6330-145">If successful, this method returns a collection of qualifications in the response body.</span></span>  <span data-ttu-id="f6330-146">Hieronder vindt u voor beelden van de **Get** -aanroep voor een klant met de **opleidings** kwalificatie.</span><span class="sxs-lookup"><span data-stu-id="f6330-146">Below are examples of the **GET** call on a customer with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f6330-147">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="f6330-147">Response success and error codes</span></span>

<span data-ttu-id="f6330-148">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="f6330-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f6330-149">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="f6330-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f6330-150">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="f6330-150">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-examples"></a><span data-ttu-id="f6330-151">Antwoord voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f6330-151">Response examples</span></span>

#### <a name="approved"></a><span data-ttu-id="f6330-152">Goedgekeurd</span><span class="sxs-lookup"><span data-stu-id="f6330-152">Approved</span></span>

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

#### <a name="in-review"></a><span data-ttu-id="f6330-153">Wordt gecontroleerd</span><span class="sxs-lookup"><span data-stu-id="f6330-153">In Review</span></span>

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

#### <a name="denied"></a><span data-ttu-id="f6330-154">Geweigerd</span><span class="sxs-lookup"><span data-stu-id="f6330-154">Denied</span></span>

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

## <a name="related-articles"></a><span data-ttu-id="f6330-155">Verwante artikelen:</span><span class="sxs-lookup"><span data-stu-id="f6330-155">Related articles</span></span>

- [<span data-ttu-id="f6330-156">Kwalificaties van een klant bijwerken</span><span class="sxs-lookup"><span data-stu-id="f6330-156">Update a customer's qualifications</span></span>](./update-customer-qualification-asynchronous.md)
