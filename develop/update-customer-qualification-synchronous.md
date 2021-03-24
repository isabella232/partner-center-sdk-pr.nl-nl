---
title: De kwalificatie van een klant bijwerken
description: Meer informatie over het bijwerken van de kwalificaties van een klant via synchrone screening of hebben, met inbegrip van het adres dat aan het profiel is gekoppeld.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 0ffe6d1a236a8a07e1ff71163e7639ef1f3437e1
ms.sourcegitcommit: bbdb5f7c9ddd42c2fc4eaadbb67d61aeeae805ca
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/24/2021
ms.locfileid: "105030586"
---
# <a name="update-a-customers-qualification-via-synchronous-validation"></a><span data-ttu-id="40b70-103">De kwalificatie van een klant bijwerken via synchrone validatie</span><span class="sxs-lookup"><span data-stu-id="40b70-103">Update a customer's qualification via synchronous validation</span></span>

<span data-ttu-id="40b70-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="40b70-104">**Applies To**</span></span>

- <span data-ttu-id="40b70-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="40b70-105">Partner Center</span></span>

<span data-ttu-id="40b70-106">Meer informatie over hoe u de kwalificaties van een klant synchroon kunt bijwerken via partner Center-Api's.</span><span class="sxs-lookup"><span data-stu-id="40b70-106">Learn how to update a customer's qualifications synchronously via Partner Center APIs.</span></span> <span data-ttu-id="40b70-107">Zie [de kwalificatie van een klant bijwerken via asynchrone validatie](update-customer-qualification-asynchronous.md)voor meer informatie over hoe u dit asynchroon kunt doen.</span><span class="sxs-lookup"><span data-stu-id="40b70-107">To learn how to do this asynchronously, see [Update a customer's qualification via asynchronous validation](update-customer-qualification-asynchronous.md).</span></span>

<span data-ttu-id="40b70-108">Een partner kan de kwalificatie van een klant zo bijwerken dat deze ' Education ' of ' GovernmentCommunityCloud ' is.</span><span class="sxs-lookup"><span data-stu-id="40b70-108">A partner can update a customer's qualification to be "Education" or "GovernmentCommunityCloud".</span></span> <span data-ttu-id="40b70-109">Andere waarden ' none ' en ' non profit ' kunnen niet worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="40b70-109">Other values, "None" and "Nonprofit", cannot be set.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="40b70-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="40b70-110">Prerequisites</span></span>

- <span data-ttu-id="40b70-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="40b70-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="40b70-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="40b70-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="40b70-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="40b70-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="40b70-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="40b70-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="40b70-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="40b70-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="40b70-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="40b70-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="40b70-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="40b70-117">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="40b70-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="40b70-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="40b70-119">C\#</span><span class="sxs-lookup"><span data-stu-id="40b70-119">C\#</span></span>

<span data-ttu-id="40b70-120">Als u de kwalificatie van een klant wilt bijwerken naar ' Education ', roept u **[Update/DotNet/API/Microsoft. Store. partnercenter. kwalificatie. icustomerqualification. update)** aan voor een bestaande  [**klant**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer).</span><span class="sxs-lookup"><span data-stu-id="40b70-120">To update a customer's qualification to "Education", call **[Update/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification.update)** on an existing  [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer).</span></span>

``` csharp
// CustomerQualification is an enum

var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.Education);
```

<span data-ttu-id="40b70-121">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="40b70-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="40b70-122">**Project**: PartnerSDK. FeatureSamples- **klasse**: CustomerQualificationOperations. cs</span><span class="sxs-lookup"><span data-stu-id="40b70-122">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerQualificationOperations.cs</span></span>

<span data-ttu-id="40b70-123">Als u de kwalificatie van een klant wilt bijwerken naar **GovernmentCommunityCloud** op een bestaande klant zonder kwalificatie, moet de partner de [**ValidationCode**](utility-resources.md#validationcode)van de klant bevatten.</span><span class="sxs-lookup"><span data-stu-id="40b70-123">To update a customer's qualification to **GovernmentCommunityCloud** on an existing customer without a qualification, the partner is required to include the customer's [**ValidationCode**](utility-resources.md#validationcode).</span></span>

``` csharp
// CustomerQualification is an enum
// GCC validation is type ValidationCode

var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.GovernmentCommunityCloud, gccValidation);
```

## <a name="rest-request"></a><span data-ttu-id="40b70-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="40b70-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="40b70-125">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="40b70-125">Request syntax</span></span>

| <span data-ttu-id="40b70-126">Methode</span><span class="sxs-lookup"><span data-stu-id="40b70-126">Method</span></span>  | <span data-ttu-id="40b70-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="40b70-127">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="40b70-128">**PUT**</span><span class="sxs-lookup"><span data-stu-id="40b70-128">**PUT**</span></span> | <span data-ttu-id="40b70-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer_ID}/Qualification? code = {VALIDATIONCODE} http/1.1</span><span class="sxs-lookup"><span data-stu-id="40b70-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/qualification?code={validationCode} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="40b70-130">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="40b70-130">URI parameter</span></span>

<span data-ttu-id="40b70-131">Gebruik de volgende query parameter om de kwalificatie bij te werken.</span><span class="sxs-lookup"><span data-stu-id="40b70-131">Use the following query parameter to update the qualification.</span></span>

| <span data-ttu-id="40b70-132">Naam</span><span class="sxs-lookup"><span data-stu-id="40b70-132">Name</span></span>                   | <span data-ttu-id="40b70-133">Type</span><span class="sxs-lookup"><span data-stu-id="40b70-133">Type</span></span> | <span data-ttu-id="40b70-134">Vereist</span><span class="sxs-lookup"><span data-stu-id="40b70-134">Required</span></span> | <span data-ttu-id="40b70-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="40b70-135">Description</span></span>                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="40b70-136">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="40b70-136">**customer-tenant-id**</span></span> | <span data-ttu-id="40b70-137">GUID</span><span class="sxs-lookup"><span data-stu-id="40b70-137">GUID</span></span> | <span data-ttu-id="40b70-138">Ja</span><span class="sxs-lookup"><span data-stu-id="40b70-138">Yes</span></span>      | <span data-ttu-id="40b70-139">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="40b70-139">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="40b70-140">**validationCode**</span><span class="sxs-lookup"><span data-stu-id="40b70-140">**validationCode**</span></span>     | <span data-ttu-id="40b70-141">int</span><span class="sxs-lookup"><span data-stu-id="40b70-141">int</span></span>  | <span data-ttu-id="40b70-142">Nee</span><span class="sxs-lookup"><span data-stu-id="40b70-142">No</span></span>       | <span data-ttu-id="40b70-143">Alleen nodig voor de cloud van de community.</span><span class="sxs-lookup"><span data-stu-id="40b70-143">Only needed for Government Community Cloud.</span></span>                                                                                                            |

### <a name="request-headers"></a><span data-ttu-id="40b70-144">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="40b70-144">Request headers</span></span>

<span data-ttu-id="40b70-145">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="40b70-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="40b70-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="40b70-146">Request body</span></span>

<span data-ttu-id="40b70-147">De waarde van het gehele getal uit de Enum van de [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) .</span><span class="sxs-lookup"><span data-stu-id="40b70-147">The integer value from the [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) enum.</span></span>

### <a name="request-example"></a><span data-ttu-id="40b70-148">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="40b70-148">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualification?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

```

## <a name="rest-response"></a><span data-ttu-id="40b70-149">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="40b70-149">REST response</span></span>

<span data-ttu-id="40b70-150">Als dit lukt, retourneert deze methode de bijgewerkte [**Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) -eigenschap in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="40b70-150">If successful, this method returns updated [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="40b70-151">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="40b70-151">Response success and error codes</span></span>

<span data-ttu-id="40b70-152">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="40b70-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="40b70-153">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="40b70-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="40b70-154">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="40b70-154">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="40b70-155">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="40b70-155">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 14
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
"governmentcommunitycloud"
```

## <a name="related-articles"></a><span data-ttu-id="40b70-156">Verwante artikelen:</span><span class="sxs-lookup"><span data-stu-id="40b70-156">Related articles</span></span>

- [<span data-ttu-id="40b70-157">De kwalificatie van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="40b70-157">Get a customer's qualification</span></span>](./get-customer-qualification-synchronous.md)
- [<span data-ttu-id="40b70-158">De validatiecodes van een partner ophalen</span><span class="sxs-lookup"><span data-stu-id="40b70-158">Get a partner's validation codes</span></span>](get-a-partner-s-validation-codes.md)
