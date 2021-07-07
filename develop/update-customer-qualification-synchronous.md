---
title: De kwalificatie van een klant bijwerken
description: Meer informatie over het bijwerken van de kwalificaties van een klant via synchrone screening of controle, met inbegrip van het adres dat is gekoppeld aan het profiel.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 5047743afdef02033d9494e3d8c16c9ab96b3fe9
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446646"
---
# <a name="update-a-customers-qualification-via-synchronous-validation"></a><span data-ttu-id="377ed-103">De kwalificatie van een klant bijwerken via synchrone validatie</span><span class="sxs-lookup"><span data-stu-id="377ed-103">Update a customer's qualification via synchronous validation</span></span>

<span data-ttu-id="377ed-104">Meer informatie over het synchroon bijwerken van de kwalificaties van een klant via Partner Center API's.</span><span class="sxs-lookup"><span data-stu-id="377ed-104">Learn how to update a customer's qualifications synchronously via Partner Center APIs.</span></span> <span data-ttu-id="377ed-105">Zie Kwalificatie van een klant bijwerken via asynchrone validatie voor meer informatie over hoe u [dit asynchroon kunt doen.](update-customer-qualification-asynchronous.md)</span><span class="sxs-lookup"><span data-stu-id="377ed-105">To learn how to do this asynchronously, see [Update a customer's qualification via asynchronous validation](update-customer-qualification-asynchronous.md).</span></span>

<span data-ttu-id="377ed-106">Een partner kan de kwalificatie van een klant bijwerken naar Education of GovernmentCommunityCloud.</span><span class="sxs-lookup"><span data-stu-id="377ed-106">A partner can update a customer's qualification to be "Education" or "GovernmentCommunityCloud".</span></span> <span data-ttu-id="377ed-107">Andere waarden, 'Geen' en 'Non-non-profit', kunnen niet worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="377ed-107">Other values, "None" and "Nonprofit", cannot be set.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="377ed-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="377ed-108">Prerequisites</span></span>

- <span data-ttu-id="377ed-109">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="377ed-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="377ed-110">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="377ed-110">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="377ed-111">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="377ed-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="377ed-112">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="377ed-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="377ed-113">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="377ed-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="377ed-114">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="377ed-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="377ed-115">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="377ed-115">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="377ed-116">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="377ed-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="377ed-117">C\#</span><span class="sxs-lookup"><span data-stu-id="377ed-117">C\#</span></span>

<span data-ttu-id="377ed-118">Als u de kwalificatie van een klant wilt bijwerken naar Education, roept u **[Update/dotnet/api/microsoft.store.partnercenter.kwalificatie.edtomerqualification.update)** aan bij een bestaande [**klant.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer)</span><span class="sxs-lookup"><span data-stu-id="377ed-118">To update a customer's qualification to "Education", call **[Update/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification.update)** on an existing  [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer).</span></span>

``` csharp
// CustomerQualification is an enum

var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.Education);
```

<span data-ttu-id="377ed-119">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="377ed-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="377ed-120">**Project:** Klasse PartnerSDK.FeatureSamples: CustomerQualificationOperations.cs </span><span class="sxs-lookup"><span data-stu-id="377ed-120">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerQualificationOperations.cs</span></span>

<span data-ttu-id="377ed-121">Als u de kwalificatie van een klant wilt bijwerken naar **GovernmentCommunityCloud** voor een bestaande klant zonder kwalificatie, moet de partner de [**ValidationCode van de klant opnemen.**](utility-resources.md#validationcode)</span><span class="sxs-lookup"><span data-stu-id="377ed-121">To update a customer's qualification to **GovernmentCommunityCloud** on an existing customer without a qualification, the partner is required to include the customer's [**ValidationCode**](utility-resources.md#validationcode).</span></span>

``` csharp
// CustomerQualification is an enum
// GCC validation is type ValidationCode

var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.GovernmentCommunityCloud, gccValidation);
```

## <a name="rest-request"></a><span data-ttu-id="377ed-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="377ed-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="377ed-123">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="377ed-123">Request syntax</span></span>

| <span data-ttu-id="377ed-124">Methode</span><span class="sxs-lookup"><span data-stu-id="377ed-124">Method</span></span>  | <span data-ttu-id="377ed-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="377ed-125">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="377ed-126">**PUT**</span><span class="sxs-lookup"><span data-stu-id="377ed-126">**PUT**</span></span> | <span data-ttu-id="377ed-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/kwalificatie?code={validationCode} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="377ed-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/qualification?code={validationCode} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="377ed-128">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="377ed-128">URI parameter</span></span>

<span data-ttu-id="377ed-129">Gebruik de volgende queryparameter om de kwalificatie bij te werken.</span><span class="sxs-lookup"><span data-stu-id="377ed-129">Use the following query parameter to update the qualification.</span></span>

| <span data-ttu-id="377ed-130">Naam</span><span class="sxs-lookup"><span data-stu-id="377ed-130">Name</span></span>                   | <span data-ttu-id="377ed-131">Type</span><span class="sxs-lookup"><span data-stu-id="377ed-131">Type</span></span> | <span data-ttu-id="377ed-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="377ed-132">Required</span></span> | <span data-ttu-id="377ed-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="377ed-133">Description</span></span>                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="377ed-134">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="377ed-134">**customer-tenant-id**</span></span> | <span data-ttu-id="377ed-135">GUID</span><span class="sxs-lookup"><span data-stu-id="377ed-135">GUID</span></span> | <span data-ttu-id="377ed-136">Ja</span><span class="sxs-lookup"><span data-stu-id="377ed-136">Yes</span></span>      | <span data-ttu-id="377ed-137">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="377ed-137">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="377ed-138">**validationCode**</span><span class="sxs-lookup"><span data-stu-id="377ed-138">**validationCode**</span></span>     | <span data-ttu-id="377ed-139">int</span><span class="sxs-lookup"><span data-stu-id="377ed-139">int</span></span>  | <span data-ttu-id="377ed-140">Nee</span><span class="sxs-lookup"><span data-stu-id="377ed-140">No</span></span>       | <span data-ttu-id="377ed-141">Alleen nodig voor Government Community Cloud.</span><span class="sxs-lookup"><span data-stu-id="377ed-141">Only needed for Government Community Cloud.</span></span>                                                                                                            |

### <a name="request-headers"></a><span data-ttu-id="377ed-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="377ed-142">Request headers</span></span>

<span data-ttu-id="377ed-143">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="377ed-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="377ed-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="377ed-144">Request body</span></span>

<span data-ttu-id="377ed-145">De gehele waarde uit de [**enum CustomerQualification.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification)</span><span class="sxs-lookup"><span data-stu-id="377ed-145">The integer value from the [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) enum.</span></span>

### <a name="request-example"></a><span data-ttu-id="377ed-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="377ed-146">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualification?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

```

## <a name="rest-response"></a><span data-ttu-id="377ed-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="377ed-147">REST response</span></span>

<span data-ttu-id="377ed-148">Als dit lukt, retourneert deze methode de [**bijgewerkte eigenschap Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="377ed-148">If successful, this method returns updated [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="377ed-149">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="377ed-149">Response success and error codes</span></span>

<span data-ttu-id="377ed-150">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="377ed-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="377ed-151">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="377ed-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="377ed-152">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="377ed-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="377ed-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="377ed-153">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 14
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
"governmentcommunitycloud"
```

## <a name="related-articles"></a><span data-ttu-id="377ed-154">Verwante artikelen:</span><span class="sxs-lookup"><span data-stu-id="377ed-154">Related articles</span></span>

- [<span data-ttu-id="377ed-155">De kwalificatie van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="377ed-155">Get a customer's qualification</span></span>](./get-customer-qualification-synchronous.md)
- [<span data-ttu-id="377ed-156">De validatiecodes van een partner ophalen</span><span class="sxs-lookup"><span data-stu-id="377ed-156">Get a partner's validation codes</span></span>](get-a-partner-s-validation-codes.md)
