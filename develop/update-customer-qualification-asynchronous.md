---
title: Kwalificaties van een klant bijwerken
description: Hiermee worden de kwalificaties van een klant asynchroon bijgewerkt, met inbegrip van het adres dat aan het profiel is gekoppeld.
ms.date: 03/23/2021
ms.service: partner-dashboard
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 7606eeaac4df158ec0fad6ffd4e565bb250f448e
ms.sourcegitcommit: bbdb5f7c9ddd42c2fc4eaadbb67d61aeeae805ca
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/24/2021
ms.locfileid: "105030603"
---
# <a name="update-a-customers-qualifications-asynchronously"></a><span data-ttu-id="502df-103">De kwalificaties van een klant asynchroon bijwerken</span><span class="sxs-lookup"><span data-stu-id="502df-103">Update a customer's qualifications asynchronously</span></span>

<span data-ttu-id="502df-104">Hiermee worden de kwalificaties van een klant asynchroon bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="502df-104">Updates a customer's qualifications asynchronously.</span></span>

<span data-ttu-id="502df-105">Een partner kan de kwalificaties van een klant asynchroon bijwerken om "Education" of "GovernmentCommunityCloud" te zijn.</span><span class="sxs-lookup"><span data-stu-id="502df-105">A partner can update a customer's qualifications asynchronously to be "Education" or "GovernmentCommunityCloud".</span></span> <span data-ttu-id="502df-106">Andere waarden ' none ' en ' non profit ' kunnen niet worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="502df-106">Other values, "None" and "Nonprofit", cannot be set.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="502df-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="502df-107">Prerequisites</span></span>

- <span data-ttu-id="502df-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="502df-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="502df-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="502df-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="502df-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="502df-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="502df-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="502df-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="502df-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="502df-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="502df-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="502df-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="502df-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="502df-114">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="502df-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="502df-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="502df-116">C\#</span><span class="sxs-lookup"><span data-stu-id="502df-116">C\#</span></span>

<span data-ttu-id="502df-117">Als u de kwalificatie van een klant voor ' opleidingen ' wilt maken, maakt u eerst een-object dat het kwalificatie type vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="502df-117">To create a customer's qualification for "Education", first create an object representing the qualification type.</span></span> <span data-ttu-id="502df-118">Vervolgens roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id.</span><span class="sxs-lookup"><span data-stu-id="502df-118">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="502df-119">Gebruik vervolgens de [**Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) -eigenschap om een [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) -interface op te halen.</span><span class="sxs-lookup"><span data-stu-id="502df-119">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="502df-120">Roep ten slotte `CreateQualifications()` `CreateQualificationsAsync()` het object kwalificatie type aan als een invoer parameter.</span><span class="sxs-lookup"><span data-stu-id="502df-120">Finally, call `CreateQualifications()` or `CreateQualificationsAsync()` with the qualification type object as an input parameter.</span></span>

``` csharp
var qualificationType = { Qualification = "education" };
var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(qualificationType);
```

<span data-ttu-id="502df-121">Voor **beeld**: console-voor [beeld-app](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span><span class="sxs-lookup"><span data-stu-id="502df-121">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="502df-122">**Project**: SdkSamples- **klasse**: CreateCustomerQualification. cs</span><span class="sxs-lookup"><span data-stu-id="502df-122">**Project**: SdkSamples **Class**: CreateCustomerQualification.cs</span></span>

<span data-ttu-id="502df-123">Als u de kwalificatie van een klant wilt bijwerken naar **GovernmentCommunityCloud** op een bestaande klant zonder kwalificatie, moet de partner ook de [**ValidationCode**](utility-resources.md#validationcode)van de klant bevatten.</span><span class="sxs-lookup"><span data-stu-id="502df-123">To update a customer's qualification to **GovernmentCommunityCloud** on an existing customer without a qualification, the partner is also required to include the customer's [**ValidationCode**](utility-resources.md#validationcode).</span></span> <span data-ttu-id="502df-124">Maak eerst een object dat het kwalificatie type vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="502df-124">First, create an object representing the qualification type.</span></span> <span data-ttu-id="502df-125">Vervolgens roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id.</span><span class="sxs-lookup"><span data-stu-id="502df-125">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="502df-126">Gebruik vervolgens de [**Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) -eigenschap om een [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) -interface op te halen.</span><span class="sxs-lookup"><span data-stu-id="502df-126">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="502df-127">Roep ten slotte `CreateQualifications()` `CreateQualificationsAsync()` het object kwalificatie type en de validatie code aan als invoer parameters.</span><span class="sxs-lookup"><span data-stu-id="502df-127">Finally, call `CreateQualifications()` or `CreateQualificationsAsync()` with the qualification type object and the validation code as input parameters.</span></span>

``` csharp
// GCC validation is type ValidationCode
var qualificationType = { Qualification = "GovernmentCommunityCloud" };
var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(qualificationType, gccValidation);
```

<span data-ttu-id="502df-128">Voor **beeld**: console-voor [beeld-app](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span><span class="sxs-lookup"><span data-stu-id="502df-128">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="502df-129">**Project**: SdkSamples- **klasse**: CreateCustomerQualificationWithGCC. cs</span><span class="sxs-lookup"><span data-stu-id="502df-129">**Project**: SdkSamples **Class**: CreateCustomerQualificationWithGCC.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="502df-130">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="502df-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="502df-131">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="502df-131">Request syntax</span></span>

| <span data-ttu-id="502df-132">Methode</span><span class="sxs-lookup"><span data-stu-id="502df-132">Method</span></span>  | <span data-ttu-id="502df-133">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="502df-133">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="502df-134">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="502df-134">**POST**</span></span> | <span data-ttu-id="502df-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer_ID}/Qualifications? code = {VALIDATIONCODE} http/1.1</span><span class="sxs-lookup"><span data-stu-id="502df-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/qualifications?code={validationCode} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="502df-136">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="502df-136">URI parameter</span></span>

<span data-ttu-id="502df-137">Gebruik de volgende query parameter om de kwalificatie bij te werken.</span><span class="sxs-lookup"><span data-stu-id="502df-137">Use the following query parameter to update the qualification.</span></span>

| <span data-ttu-id="502df-138">Naam</span><span class="sxs-lookup"><span data-stu-id="502df-138">Name</span></span>                   | <span data-ttu-id="502df-139">Type</span><span class="sxs-lookup"><span data-stu-id="502df-139">Type</span></span> | <span data-ttu-id="502df-140">Vereist</span><span class="sxs-lookup"><span data-stu-id="502df-140">Required</span></span> | <span data-ttu-id="502df-141">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="502df-141">Description</span></span>                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="502df-142">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="502df-142">**customer-tenant-id**</span></span> | <span data-ttu-id="502df-143">GUID</span><span class="sxs-lookup"><span data-stu-id="502df-143">GUID</span></span> | <span data-ttu-id="502df-144">Ja</span><span class="sxs-lookup"><span data-stu-id="502df-144">Yes</span></span>      | <span data-ttu-id="502df-145">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="502df-145">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="502df-146">**validationCode**</span><span class="sxs-lookup"><span data-stu-id="502df-146">**validationCode**</span></span>     | <span data-ttu-id="502df-147">int</span><span class="sxs-lookup"><span data-stu-id="502df-147">int</span></span>  | <span data-ttu-id="502df-148">Nee</span><span class="sxs-lookup"><span data-stu-id="502df-148">No</span></span>       | <span data-ttu-id="502df-149">Alleen nodig voor de cloud van de community.</span><span class="sxs-lookup"><span data-stu-id="502df-149">Only needed for Government Community Cloud.</span></span>                                                                                                            |

### <a name="request-headers"></a><span data-ttu-id="502df-150">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="502df-150">Request headers</span></span>

<span data-ttu-id="502df-151">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="502df-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="502df-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="502df-152">Request body</span></span>

<span data-ttu-id="502df-153">In deze tabel wordt het kwalificatie object in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="502df-153">This table describes the qualification object in the request body.</span></span>

<span data-ttu-id="502df-154">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="502df-154">Property</span></span> | <span data-ttu-id="502df-155">Type</span><span class="sxs-lookup"><span data-stu-id="502df-155">Type</span></span> | <span data-ttu-id="502df-156">Vereist</span><span class="sxs-lookup"><span data-stu-id="502df-156">Required</span></span> | <span data-ttu-id="502df-157">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="502df-157">Description</span></span>
-------- | ---- | -------- | -----------
<span data-ttu-id="502df-158">Kwalificatie</span><span class="sxs-lookup"><span data-stu-id="502df-158">Qualification</span></span> | <span data-ttu-id="502df-159">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="502df-159">string</span></span> | <span data-ttu-id="502df-160">Ja</span><span class="sxs-lookup"><span data-stu-id="502df-160">Yes</span></span> | <span data-ttu-id="502df-161">De teken reeks waarde van de Enum van [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) .</span><span class="sxs-lookup"><span data-stu-id="502df-161">The string value from the [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) enum.</span></span>

### <a name="request-example"></a><span data-ttu-id="502df-162">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="502df-162">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

{
    "Qualification": "Education"
}

```

## <a name="rest-response"></a><span data-ttu-id="502df-163">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="502df-163">REST response</span></span>

<span data-ttu-id="502df-164">Als dit lukt, retourneert deze methode een object kwalificaties in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="502df-164">If successful, this method returns a qualifications object in the response body.</span></span> <span data-ttu-id="502df-165">Hieronder volgt een voor beeld van de **post** -oproep voor een klant (met een eerdere kwalificatie van **geen**) met de **opleidings** kwalificatie.</span><span class="sxs-lookup"><span data-stu-id="502df-165">Below is an example of the **POST** call on a customer (with a previous qualification of **None**) with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="502df-166">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="502df-166">Response success and error codes</span></span>

<span data-ttu-id="502df-167">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="502df-167">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="502df-168">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="502df-168">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="502df-169">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="502df-169">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="502df-170">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="502df-170">Response example</span></span>

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

## <a name="related-articles"></a><span data-ttu-id="502df-171">Verwante artikelen:</span><span class="sxs-lookup"><span data-stu-id="502df-171">Related articles</span></span>

- [<span data-ttu-id="502df-172">De kwalificaties van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="502df-172">Get a customer's qualifications</span></span>](./get-customer-qualification-asynchronous.md)
- [<span data-ttu-id="502df-173">De validatiecodes van een partner ophalen</span><span class="sxs-lookup"><span data-stu-id="502df-173">Get a partner's validation codes</span></span>](get-a-partner-s-validation-codes.md)
