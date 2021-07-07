---
title: De kwalificatie van een klant ophalen
description: Meer informatie over het gebruik van synchrone validatie om de kwalificatie van een klant op te halen via Partner Center API. Partners kunnen dit gebruiken om Education-klanten te valideren.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: d215ddb105efe3acd1182c4ff4bb25b045b121f0
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446340"
---
# <a name="get-a-customers-qualification-via-synchronous-validation"></a><span data-ttu-id="4a3e5-104">De kwalificatie van een klant via synchrone validatie</span><span class="sxs-lookup"><span data-stu-id="4a3e5-104">Get a customer's qualification via synchronous validation</span></span>

<span data-ttu-id="4a3e5-105">Leer hoe u de kwalificatie van een klant synchroon kunt krijgen via Partner Center API's.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-105">Learn how to get a customer's qualification synchronously via Partner Center APIs.</span></span> <span data-ttu-id="4a3e5-106">Zie De kwalificatie van een klant krijgen via asynchrone validatie voor meer informatie over hoe u [dit asynchroon kunt doen.](get-customer-qualification-asynchronous.md)</span><span class="sxs-lookup"><span data-stu-id="4a3e5-106">To learn how to do this asynchronously, see [Get a customer's qualification via asynchronous validation](get-customer-qualification-asynchronous.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4a3e5-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4a3e5-107">Prerequisites</span></span>

- <span data-ttu-id="4a3e5-108">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="4a3e5-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4a3e5-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="4a3e5-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4a3e5-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="4a3e5-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="4a3e5-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="4a3e5-112">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="4a3e5-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="4a3e5-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="4a3e5-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="4a3e5-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4a3e5-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="4a3e5-116">C\#</span><span class="sxs-lookup"><span data-stu-id="4a3e5-116">C\#</span></span>

<span data-ttu-id="4a3e5-117">Als u de kwalificatie van een klant wilt krijgen, roept u de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-117">To get a customer's qualification, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="4a3e5-118">Gebruik vervolgens de [**eigenschap Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) om een [**ICustomerQualification-interface op te**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) halen.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-118">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="4a3e5-119">Roep tot slot [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) of [**GetAsync aan om**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) de kwalificatie van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-119">Finally, call [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) to retrieve the customer's qualification.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

var customerQualification = partnerOperations.Customers.ById(customerId).Qualification.Get();
```

## <a name="rest-request"></a><span data-ttu-id="4a3e5-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="4a3e5-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4a3e5-121">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="4a3e5-121">Request syntax</span></span>

| <span data-ttu-id="4a3e5-122">Methode</span><span class="sxs-lookup"><span data-stu-id="4a3e5-122">Method</span></span>  | <span data-ttu-id="4a3e5-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="4a3e5-123">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4a3e5-124">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="4a3e5-124">**GET**</span></span> | <span data-ttu-id="4a3e5-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/kwalificatie HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4a3e5-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/qualification HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="4a3e5-126">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="4a3e5-126">URI parameter</span></span>

<span data-ttu-id="4a3e5-127">Deze tabel bevat de vereiste queryparameter om alle kwalificaties op te halen.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-127">This table lists the required query parameter to get all the qualification.</span></span>

| <span data-ttu-id="4a3e5-128">Naam</span><span class="sxs-lookup"><span data-stu-id="4a3e5-128">Name</span></span>               | <span data-ttu-id="4a3e5-129">Type</span><span class="sxs-lookup"><span data-stu-id="4a3e5-129">Type</span></span>   | <span data-ttu-id="4a3e5-130">Vereist</span><span class="sxs-lookup"><span data-stu-id="4a3e5-130">Required</span></span> | <span data-ttu-id="4a3e5-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4a3e5-131">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="4a3e5-132">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="4a3e5-132">**customer-tenant-id**</span></span> | <span data-ttu-id="4a3e5-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4a3e5-133">string</span></span> | <span data-ttu-id="4a3e5-134">Ja</span><span class="sxs-lookup"><span data-stu-id="4a3e5-134">Yes</span></span>      | <span data-ttu-id="4a3e5-135">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-135">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4a3e5-136">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="4a3e5-136">Request headers</span></span>

<span data-ttu-id="4a3e5-137">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="4a3e5-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4a3e5-138">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="4a3e5-138">Request body</span></span>

<span data-ttu-id="4a3e5-139">Geen.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-139">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="4a3e5-140">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4a3e5-140">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualification HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a><span data-ttu-id="4a3e5-141">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="4a3e5-141">REST response</span></span>

<span data-ttu-id="4a3e5-142">Als dit lukt, retourneert deze methode een kwalificatiewaarde in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-142">If successful, this method returns a qualification value in the response body.</span></span>  <span data-ttu-id="4a3e5-143">Hieronder vindt u een voorbeeld van de **GET-aanroep** van een klant met de **kwalificatie voor** het onderwijs.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-143">Below is an example of the **GET** call on a customer with the **education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4a3e5-144">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="4a3e5-144">Response success and error codes</span></span>

<span data-ttu-id="4a3e5-145">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-145">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4a3e5-146">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="4a3e5-146">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4a3e5-147">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="4a3e5-147">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4a3e5-148">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="4a3e5-148">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

    "education"

```

## <a name="related-articles"></a><span data-ttu-id="4a3e5-149">Verwante artikelen:</span><span class="sxs-lookup"><span data-stu-id="4a3e5-149">Related articles</span></span>

- [<span data-ttu-id="4a3e5-150">De kwalificatie van een klant bijwerken</span><span class="sxs-lookup"><span data-stu-id="4a3e5-150">Update a customer's qualification</span></span>](./update-customer-qualification-synchronous.md)