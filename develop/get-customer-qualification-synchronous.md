---
title: De kwalificatie van een klant ophalen
description: Meer informatie over hoe u synchrone validatie kunt gebruiken om de kwalificatie van een klant te verkrijgen via de Partner Center-API. Partners kunnen deze gebruiken om onderwijs klanten te valideren.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 82812091be9c13d64ac183c37461e3b63b2ec294
ms.sourcegitcommit: 0c98496e972aebe10eba23822aa229125bfc035d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767652"
---
# <a name="get-a-customers-qualification-via-synchronous-validation"></a><span data-ttu-id="82165-104">De kwalificatie van een klant ophalen via synchrone validatie</span><span class="sxs-lookup"><span data-stu-id="82165-104">Get a customer's qualification via synchronous validation</span></span>

<span data-ttu-id="82165-105">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="82165-105">**Applies To**</span></span>

- <span data-ttu-id="82165-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="82165-106">Partner Center</span></span>

<span data-ttu-id="82165-107">Meer informatie over hoe u de kwalificatie van een klant synchroon kunt verkrijgen via partner Center-Api's.</span><span class="sxs-lookup"><span data-stu-id="82165-107">Learn how to get a customer's qualification synchronously via Partner Center APIs.</span></span> <span data-ttu-id="82165-108">Zie [de kwalificatie van een klant ophalen via asynchrone validatie](get-customer-qualification-asynchronous.md)voor meer informatie over hoe u dit asynchroon kunt doen.</span><span class="sxs-lookup"><span data-stu-id="82165-108">To learn how to do this asynchronously, see [Get a customer's qualification via asynchronous validation](get-customer-qualification-asynchronous.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="82165-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="82165-109">Prerequisites</span></span>

- <span data-ttu-id="82165-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="82165-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="82165-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="82165-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="82165-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="82165-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="82165-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="82165-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="82165-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="82165-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="82165-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="82165-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="82165-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="82165-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="82165-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="82165-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="82165-118">C\#</span><span class="sxs-lookup"><span data-stu-id="82165-118">C\#</span></span>

<span data-ttu-id="82165-119">Als u de kwalificatie van een klant wilt ophalen, roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id.</span><span class="sxs-lookup"><span data-stu-id="82165-119">To get a customer's qualification, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="82165-120">Gebruik vervolgens de [**Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) -eigenschap om een [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) -interface op te halen.</span><span class="sxs-lookup"><span data-stu-id="82165-120">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="82165-121">Roep tot slot [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) aan om de kwalificatie van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="82165-121">Finally, call [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) to retrieve the customer's qualification.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

var customerQualification = partnerOperations.Customers.ById(customerId).Qualification.Get();
```

## <a name="rest-request"></a><span data-ttu-id="82165-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="82165-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="82165-123">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="82165-123">Request syntax</span></span>

| <span data-ttu-id="82165-124">Methode</span><span class="sxs-lookup"><span data-stu-id="82165-124">Method</span></span>  | <span data-ttu-id="82165-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="82165-125">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="82165-126">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="82165-126">**GET**</span></span> | <span data-ttu-id="82165-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Qualification http/1.1</span><span class="sxs-lookup"><span data-stu-id="82165-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/qualification HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="82165-128">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="82165-128">URI parameter</span></span>

<span data-ttu-id="82165-129">Deze tabel bevat de vereiste query parameter om alle kwalificaties op te halen.</span><span class="sxs-lookup"><span data-stu-id="82165-129">This table lists the required query parameter to get all the qualification.</span></span>

| <span data-ttu-id="82165-130">Naam</span><span class="sxs-lookup"><span data-stu-id="82165-130">Name</span></span>               | <span data-ttu-id="82165-131">Type</span><span class="sxs-lookup"><span data-stu-id="82165-131">Type</span></span>   | <span data-ttu-id="82165-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="82165-132">Required</span></span> | <span data-ttu-id="82165-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="82165-133">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="82165-134">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="82165-134">**customer-tenant-id**</span></span> | <span data-ttu-id="82165-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="82165-135">string</span></span> | <span data-ttu-id="82165-136">Yes</span><span class="sxs-lookup"><span data-stu-id="82165-136">Yes</span></span>      | <span data-ttu-id="82165-137">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="82165-137">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="82165-138">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="82165-138">Request headers</span></span>

<span data-ttu-id="82165-139">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="82165-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="82165-140">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="82165-140">Request body</span></span>

<span data-ttu-id="82165-141">Geen.</span><span class="sxs-lookup"><span data-stu-id="82165-141">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="82165-142">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="82165-142">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualification HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a><span data-ttu-id="82165-143">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="82165-143">REST response</span></span>

<span data-ttu-id="82165-144">Als dit lukt, retourneert deze methode een kwalificatie waarde in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="82165-144">If successful, this method returns a qualification value in the response body.</span></span>  <span data-ttu-id="82165-145">Hieronder volgt een voor beeld van het **ophalen** van een klant met de **opleidings** kwalificatie.</span><span class="sxs-lookup"><span data-stu-id="82165-145">Below is an example of the **GET** call on a customer with the **education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="82165-146">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="82165-146">Response success and error codes</span></span>

<span data-ttu-id="82165-147">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="82165-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="82165-148">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="82165-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="82165-149">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="82165-149">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="82165-150">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="82165-150">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

    "education"

```

## <a name="related-articles"></a><span data-ttu-id="82165-151">Verwante artikelen:</span><span class="sxs-lookup"><span data-stu-id="82165-151">Related articles</span></span>

- [<span data-ttu-id="82165-152">De kwalificatie van een klant bijwerken</span><span class="sxs-lookup"><span data-stu-id="82165-152">Update a customer's qualification</span></span>](update-a-customer-s-qualification.md)
