---
title: De kwalificatie van een klant bijwerken
description: Meer informatie over het bijwerken van de kwalificaties van een klant via synchrone screening of hebben, met inbegrip van het adres dat aan het profiel is gekoppeld.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 7faab68d20c698f5b040a76f4776dbdf14180640
ms.sourcegitcommit: 0c98496e972aebe10eba23822aa229125bfc035d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767657"
---
# <a name="update-a-customers-qualification-via-synchronous-validation"></a><span data-ttu-id="e2ab5-103">De kwalificatie van een klant bijwerken via synchrone validatie</span><span class="sxs-lookup"><span data-stu-id="e2ab5-103">Update a customer's qualification via synchronous validation</span></span>

<span data-ttu-id="e2ab5-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="e2ab5-104">**Applies To**</span></span>

- <span data-ttu-id="e2ab5-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e2ab5-105">Partner Center</span></span>

<span data-ttu-id="e2ab5-106">Meer informatie over hoe u de kwalificaties van een klant synchroon kunt bijwerken via partner Center-Api's.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-106">Learn how to update a customer's qualifications synchronously via Partner Center APIs.</span></span> <span data-ttu-id="e2ab5-107">Zie [de kwalificatie van een klant bijwerken via asynchrone validatie](update-customer-qualification-asynchronous.md)voor meer informatie over hoe u dit asynchroon kunt doen.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-107">To learn how to do this asynchronously, see [Update a customer's qualification via asynchronous validation](update-customer-qualification-asynchronous.md).</span></span>

<span data-ttu-id="e2ab5-108">Een partner kan de kwalificatie van een klant zo bijwerken dat deze ' Education ' of ' GovernmentCommunityCloud ' is.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-108">A partner can update a customer's qualification to be "Education" or "GovernmentCommunityCloud".</span></span> <span data-ttu-id="e2ab5-109">Andere waarden ' none ' en ' non profit ' kunnen niet worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-109">Other values, "None" and "Nonprofit", cannot be set.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e2ab5-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e2ab5-110">Prerequisites</span></span>

- <span data-ttu-id="e2ab5-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e2ab5-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e2ab5-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="e2ab5-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e2ab5-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e2ab5-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e2ab5-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e2ab5-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e2ab5-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="e2ab5-117">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e2ab5-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e2ab5-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="e2ab5-119">C\#</span><span class="sxs-lookup"><span data-stu-id="e2ab5-119">C\#</span></span>

<span data-ttu-id="e2ab5-120">Als u de kwalificatie van een klant wilt bijwerken naar ' Education ', roept u **[Update/DotNet/API/Microsoft. Store. partnercenter. kwalificatie. icustomerqualification. update)** aan voor een bestaande  [**klant**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer).</span><span class="sxs-lookup"><span data-stu-id="e2ab5-120">To update a customer's qualification to "Education", call **[Update/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification.update)** on an existing  [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer).</span></span>

``` csharp
// CustomerQualification is an enum

var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.Education);
```

<span data-ttu-id="e2ab5-121">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="e2ab5-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="e2ab5-122">**Project**: PartnerSDK. FeatureSamples- **klasse**: CustomerQualificationOperations.cs</span><span class="sxs-lookup"><span data-stu-id="e2ab5-122">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerQualificationOperations.cs</span></span>

<span data-ttu-id="e2ab5-123">Het bijwerken van de kwalificatie van een klant naar **GovernmentCommunityCloud** op een bestaande klant zonder een kwalificatie.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-123">To update a customer's qualification to **GovernmentCommunityCloud** on an existing customer without a qualification.</span></span>  <span data-ttu-id="e2ab5-124">De partner is ook vereist voor het toevoegen van de [**ValidationCode**](utility-resources.md#validationcode)van de klant.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-124">The partner is also are required to include the customer's [**ValidationCode**](utility-resources.md#validationcode).</span></span>

``` csharp
// CustomerQualification is an enum
// GCC validation is type ValidationCode

var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.GovernmentCommunityCloud, gccValidation);
```

## <a name="rest-request"></a><span data-ttu-id="e2ab5-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e2ab5-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e2ab5-126">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e2ab5-126">Request syntax</span></span>

| <span data-ttu-id="e2ab5-127">Methode</span><span class="sxs-lookup"><span data-stu-id="e2ab5-127">Method</span></span>  | <span data-ttu-id="e2ab5-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e2ab5-128">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e2ab5-129">**PUT**</span><span class="sxs-lookup"><span data-stu-id="e2ab5-129">**PUT**</span></span> | <span data-ttu-id="e2ab5-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer_ID}/Qualification? code = {VALIDATIONCODE} http/1.1</span><span class="sxs-lookup"><span data-stu-id="e2ab5-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/qualification?code={validationCode} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="e2ab5-131">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="e2ab5-131">URI parameter</span></span>

<span data-ttu-id="e2ab5-132">Gebruik de volgende query parameter om de kwalificatie bij te werken.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-132">Use the following query parameter to update the qualification.</span></span>

| <span data-ttu-id="e2ab5-133">Naam</span><span class="sxs-lookup"><span data-stu-id="e2ab5-133">Name</span></span>                   | <span data-ttu-id="e2ab5-134">Type</span><span class="sxs-lookup"><span data-stu-id="e2ab5-134">Type</span></span> | <span data-ttu-id="e2ab5-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="e2ab5-135">Required</span></span> | <span data-ttu-id="e2ab5-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e2ab5-136">Description</span></span>                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e2ab5-137">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="e2ab5-137">**customer-tenant-id**</span></span> | <span data-ttu-id="e2ab5-138">GUID</span><span class="sxs-lookup"><span data-stu-id="e2ab5-138">GUID</span></span> | <span data-ttu-id="e2ab5-139">Yes</span><span class="sxs-lookup"><span data-stu-id="e2ab5-139">Yes</span></span>      | <span data-ttu-id="e2ab5-140">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-140">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="e2ab5-141">**validationCode**</span><span class="sxs-lookup"><span data-stu-id="e2ab5-141">**validationCode**</span></span>     | <span data-ttu-id="e2ab5-142">int</span><span class="sxs-lookup"><span data-stu-id="e2ab5-142">int</span></span>  | <span data-ttu-id="e2ab5-143">No</span><span class="sxs-lookup"><span data-stu-id="e2ab5-143">No</span></span>       | <span data-ttu-id="e2ab5-144">Alleen nodig voor de cloud van de community.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-144">Only needed for Government Community Cloud.</span></span>                                                                                                            |

### <a name="request-headers"></a><span data-ttu-id="e2ab5-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e2ab5-145">Request headers</span></span>

<span data-ttu-id="e2ab5-146">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e2ab5-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e2ab5-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e2ab5-147">Request body</span></span>

<span data-ttu-id="e2ab5-148">De waarde van het gehele getal uit de Enum van de [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) .</span><span class="sxs-lookup"><span data-stu-id="e2ab5-148">The integer value from the [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) enum.</span></span>

### <a name="request-example"></a><span data-ttu-id="e2ab5-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e2ab5-149">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualification?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

```

## <a name="rest-response"></a><span data-ttu-id="e2ab5-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e2ab5-150">REST response</span></span>

<span data-ttu-id="e2ab5-151">Als dit lukt, retourneert deze methode de bijgewerkte [**Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) -eigenschap in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-151">If successful, this method returns updated [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e2ab5-152">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="e2ab5-152">Response success and error codes</span></span>

<span data-ttu-id="e2ab5-153">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e2ab5-154">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e2ab5-155">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="e2ab5-155">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e2ab5-156">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e2ab5-156">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 14
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
"governmentcommunitycloud"
```

## <a name="related-articles"></a><span data-ttu-id="e2ab5-157">Verwante artikelen:</span><span class="sxs-lookup"><span data-stu-id="e2ab5-157">Related articles</span></span>

- [<span data-ttu-id="e2ab5-158">De kwalificatie van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="e2ab5-158">Get a customer's qualification</span></span>](get-a-customer-s-qualification.md)
- [<span data-ttu-id="e2ab5-159">De validatiecodes van een partner ophalen</span><span class="sxs-lookup"><span data-stu-id="e2ab5-159">Get a partner's validation codes</span></span>](get-a-partner-s-validation-codes.md)
