---
title: Kwalificaties van een klant bijwerken
description: Meer informatie over het bijwerken van de kwalificaties van een klant via asynchrone screening of hebben, met inbegrip van het adres dat aan het profiel is gekoppeld.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 703585eeaba93b6d7a510a3174a78a28f22e1510
ms.sourcegitcommit: 717e483a6eec23607b4e31ddfaa3e2691f3043e6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104711930"
---
# <a name="update-a-customers-qualifications-asynchronously"></a><span data-ttu-id="e56cf-103">De kwalificaties van een klant asynchroon bijwerken</span><span class="sxs-lookup"><span data-stu-id="e56cf-103">Update a customer's qualifications asynchronously</span></span>

<span data-ttu-id="e56cf-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="e56cf-104">**Applies To**</span></span>

- <span data-ttu-id="e56cf-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e56cf-105">Partner Center</span></span>

<span data-ttu-id="e56cf-106">Meer informatie over hoe u de kwalificaties van een klant asynchroon bijwerkt via partner Center-Api's.</span><span class="sxs-lookup"><span data-stu-id="e56cf-106">Learn how to update a customer's qualifications asynchronously via Partner Center APIs.</span></span> <span data-ttu-id="e56cf-107">Zie [de kwalificatie van een klant bijwerken via synchrone validatie](update-customer-qualification-synchronous.md)voor meer informatie over hoe u dit synchroon kunt doen.</span><span class="sxs-lookup"><span data-stu-id="e56cf-107">To learn how to do this synchronously, see [Update a customer's qualification via synchronous validation](update-customer-qualification-synchronous.md).</span></span>

<span data-ttu-id="e56cf-108">Een partner kan de kwalificaties van een klant asynchroon bijwerken om "Education" of "GovernmentCommunityCloud" te zijn.</span><span class="sxs-lookup"><span data-stu-id="e56cf-108">A partner can update a customer's qualifications asynchronously to be "Education" or "GovernmentCommunityCloud".</span></span> <span data-ttu-id="e56cf-109">Andere waarden ' none ' en ' non profit ' kunnen niet worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="e56cf-109">Other values, "None" and "Nonprofit", cannot be set.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e56cf-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e56cf-110">Prerequisites</span></span>

- <span data-ttu-id="e56cf-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e56cf-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e56cf-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="e56cf-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="e56cf-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e56cf-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e56cf-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="e56cf-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e56cf-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="e56cf-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e56cf-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="e56cf-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e56cf-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="e56cf-117">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e56cf-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e56cf-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="e56cf-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e56cf-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e56cf-120">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e56cf-120">Request syntax</span></span>

| <span data-ttu-id="e56cf-121">Methode</span><span class="sxs-lookup"><span data-stu-id="e56cf-121">Method</span></span>  | <span data-ttu-id="e56cf-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e56cf-122">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e56cf-123">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="e56cf-123">**POST**</span></span> | <span data-ttu-id="e56cf-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer_ID}/Qualifications? code = {VALIDATIONCODE} http/1.1</span><span class="sxs-lookup"><span data-stu-id="e56cf-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/qualifications?code={validationCode} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="e56cf-125">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="e56cf-125">URI parameter</span></span>

<span data-ttu-id="e56cf-126">Gebruik de volgende query parameter om de kwalificatie bij te werken.</span><span class="sxs-lookup"><span data-stu-id="e56cf-126">Use the following query parameter to update the qualification.</span></span>

| <span data-ttu-id="e56cf-127">Naam</span><span class="sxs-lookup"><span data-stu-id="e56cf-127">Name</span></span>                   | <span data-ttu-id="e56cf-128">Type</span><span class="sxs-lookup"><span data-stu-id="e56cf-128">Type</span></span> | <span data-ttu-id="e56cf-129">Vereist</span><span class="sxs-lookup"><span data-stu-id="e56cf-129">Required</span></span> | <span data-ttu-id="e56cf-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e56cf-130">Description</span></span>                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e56cf-131">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="e56cf-131">**customer-tenant-id**</span></span> | <span data-ttu-id="e56cf-132">GUID</span><span class="sxs-lookup"><span data-stu-id="e56cf-132">GUID</span></span> | <span data-ttu-id="e56cf-133">Ja</span><span class="sxs-lookup"><span data-stu-id="e56cf-133">Yes</span></span>      | <span data-ttu-id="e56cf-134">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="e56cf-134">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="e56cf-135">**validationCode**</span><span class="sxs-lookup"><span data-stu-id="e56cf-135">**validationCode**</span></span>     | <span data-ttu-id="e56cf-136">int</span><span class="sxs-lookup"><span data-stu-id="e56cf-136">int</span></span>  | <span data-ttu-id="e56cf-137">Nee</span><span class="sxs-lookup"><span data-stu-id="e56cf-137">No</span></span>       | <span data-ttu-id="e56cf-138">Alleen nodig voor de cloud van de community.</span><span class="sxs-lookup"><span data-stu-id="e56cf-138">Only needed for Government Community Cloud.</span></span>                                                                                                            |

### <a name="request-headers"></a><span data-ttu-id="e56cf-139">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e56cf-139">Request headers</span></span>

<span data-ttu-id="e56cf-140">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e56cf-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e56cf-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e56cf-141">Request body</span></span>

<span data-ttu-id="e56cf-142">De waarde van het gehele getal uit de Enum van de [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) .</span><span class="sxs-lookup"><span data-stu-id="e56cf-142">The integer value from the [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) enum.</span></span>

### <a name="request-example"></a><span data-ttu-id="e56cf-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e56cf-143">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

```

## <a name="rest-response"></a><span data-ttu-id="e56cf-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e56cf-144">REST response</span></span>

<span data-ttu-id="e56cf-145">Als dit lukt, retourneert deze methode een object kwalificaties in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="e56cf-145">If successful, this method returns a qualifications object in the response body.</span></span> <span data-ttu-id="e56cf-146">Hieronder volgt een voor beeld van de **post** -oproep voor een klant (met een eerdere kwalificatie van **geen**) met de **opleidings** kwalificatie.</span><span class="sxs-lookup"><span data-stu-id="e56cf-146">Below is an example of the **POST** call on a customer (with a previous qualification of **None**) with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e56cf-147">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="e56cf-147">Response success and error codes</span></span>

<span data-ttu-id="e56cf-148">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="e56cf-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e56cf-149">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e56cf-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e56cf-150">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="e56cf-150">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e56cf-151">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e56cf-151">Response example</span></span>

```http
HTTP/1.1 201 CREATED
Content-Length: 29
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
{
    "qualification": "Education",
    "vettingStatus": "InReview",
    "vettingCreateDate": "2020-12-04T20:54:24Z" // UTC
}
```

## <a name="related-articles"></a><span data-ttu-id="e56cf-152">Verwante artikelen:</span><span class="sxs-lookup"><span data-stu-id="e56cf-152">Related articles</span></span>

- [<span data-ttu-id="e56cf-153">De kwalificaties van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="e56cf-153">Get a customer's qualifications</span></span>](./get-customer-qualification-asynchronous.md)
- [<span data-ttu-id="e56cf-154">De validatiecodes van een partner ophalen</span><span class="sxs-lookup"><span data-stu-id="e56cf-154">Get a partner's validation codes</span></span>](get-a-partner-s-validation-codes.md)