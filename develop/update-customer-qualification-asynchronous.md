---
title: Kwalificaties van een klant bijwerken
description: Hiermee worden de kwalificaties van een klant asynchroon bijgewerkt, inclusief het adres dat aan het profiel is gekoppeld.
ms.date: 03/23/2021
ms.service: partner-dashboard
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: d7dd3593894ce91ddc7b96d604b80153d41d3a67
ms.sourcegitcommit: 51237e7e98d71a7e0590b4d6a4034b6409542126
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2021
ms.locfileid: "113572094"
---
# <a name="update-a-customers-qualifications-asynchronously"></a><span data-ttu-id="11295-103">De kwalificaties van een klant asynchroon bijwerken</span><span class="sxs-lookup"><span data-stu-id="11295-103">Update a customer's qualifications asynchronously</span></span>

<span data-ttu-id="11295-104">Werkt de kwalificaties van een klant asynchroon bij.</span><span class="sxs-lookup"><span data-stu-id="11295-104">Updates a customer's qualifications asynchronously.</span></span>

<span data-ttu-id="11295-105">Een partner kan de kwalificaties van een klant asynchroon bijwerken naar Education of GovernmentCommunityCloud.</span><span class="sxs-lookup"><span data-stu-id="11295-105">A partner can update a customer's qualifications asynchronously to be "Education" or "GovernmentCommunityCloud".</span></span> <span data-ttu-id="11295-106">Andere waarden, Geen en Non-profitorganisatie, kunnen niet worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="11295-106">Other values, "None" and "Nonprofit", cannot be set.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="11295-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="11295-107">Prerequisites</span></span>

- <span data-ttu-id="11295-108">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="11295-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="11295-109">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="11295-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="11295-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="11295-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="11295-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="11295-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="11295-112">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="11295-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="11295-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="11295-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="11295-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="11295-114">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="11295-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="11295-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="11295-116">C\#</span><span class="sxs-lookup"><span data-stu-id="11295-116">C\#</span></span>

<span data-ttu-id="11295-117">Als u de kwalificatie van een klant voor Education wilt maken, maakt u eerst een object dat het kwalificatietype vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="11295-117">To create a customer's qualification for "Education", first create an object representing the qualification type.</span></span> <span data-ttu-id="11295-118">Roep vervolgens de [**methode IAggregatePartner.Customers.ById aan**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id.</span><span class="sxs-lookup"><span data-stu-id="11295-118">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="11295-119">Gebruik vervolgens de [**eigenschap Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) om een [**ICustomerQualification-interface op te**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) halen.</span><span class="sxs-lookup"><span data-stu-id="11295-119">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="11295-120">Roep ten slotte `CreateQualifications()` of aan met het `CreateQualificationsAsync()` kwalificatietypeobject als invoerparameter.</span><span class="sxs-lookup"><span data-stu-id="11295-120">Finally, call `CreateQualifications()` or `CreateQualificationsAsync()` with the qualification type object as an input parameter.</span></span>

``` csharp
var qualificationToCreate = "education";    // can also be "StateOwnedEntity" or "GovernmentCommunityCloud". See GCC example below.
var qualificationType = { Qualification = qualificationToCreate };
var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(qualificationType);
```

<span data-ttu-id="11295-121">**Voorbeeld:** [Consolevoorbeeld-app.](https://github.com/microsoft/Partner-Center-DotNet-Samples)</span><span class="sxs-lookup"><span data-stu-id="11295-121">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="11295-122">**Project:** SdkSamples-klasse: CreateCustomerQualification.cs </span><span class="sxs-lookup"><span data-stu-id="11295-122">**Project**: SdkSamples **Class**: CreateCustomerQualification.cs</span></span>

<span data-ttu-id="11295-123">Als u de kwalificatie van een klant wilt bijwerken naar **GovernmentCommunityCloud** voor een bestaande klant zonder kwalificatie, moet de partner ook de ValidationCode van de klant [**opnemen.**](utility-resources.md#validationcode)</span><span class="sxs-lookup"><span data-stu-id="11295-123">To update a customer's qualification to **GovernmentCommunityCloud** on an existing customer without a qualification, the partner is also required to include the customer's [**ValidationCode**](utility-resources.md#validationcode).</span></span> <span data-ttu-id="11295-124">Maak eerst een -object dat het kwalificatietype vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="11295-124">First, create an object representing the qualification type.</span></span> <span data-ttu-id="11295-125">Roep vervolgens de [**methode IAggregatePartner.Customers.ById aan**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id.</span><span class="sxs-lookup"><span data-stu-id="11295-125">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="11295-126">Gebruik vervolgens de [**eigenschap Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) om een [**ICustomerQualification-interface op te**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) halen.</span><span class="sxs-lookup"><span data-stu-id="11295-126">Then use the [**Qualification**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) property to retrieve a [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) interface.</span></span> <span data-ttu-id="11295-127">Roep ten slotte `CreateQualifications()` of aan met het `CreateQualificationsAsync()` kwalificatietypeobject en de validatiecode als invoerparameters.</span><span class="sxs-lookup"><span data-stu-id="11295-127">Finally, call `CreateQualifications()` or `CreateQualificationsAsync()` with the qualification type object and the validation code as input parameters.</span></span>

``` csharp
// GCC validation is type ValidationCode
var qualificationType = { Qualification = "GovernmentCommunityCloud" };
var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(qualificationType, gccValidation);
```

<span data-ttu-id="11295-128">**Voorbeeld:** [Consolevoorbeeld-app.](https://github.com/microsoft/Partner-Center-DotNet-Samples)</span><span class="sxs-lookup"><span data-stu-id="11295-128">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="11295-129">**Project:** SdkSamples-klasse : CreateCustomerQualificationWithGCC.cs</span><span class="sxs-lookup"><span data-stu-id="11295-129">**Project**: SdkSamples **Class**: CreateCustomerQualificationWithGCC.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="11295-130">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="11295-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="11295-131">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="11295-131">Request syntax</span></span>

| <span data-ttu-id="11295-132">Methode</span><span class="sxs-lookup"><span data-stu-id="11295-132">Method</span></span>  | <span data-ttu-id="11295-133">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="11295-133">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="11295-134">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="11295-134">**POST**</span></span> | <span data-ttu-id="11295-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/kwalificaties?code={validationCode} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="11295-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/qualifications?code={validationCode} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="11295-136">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="11295-136">URI parameter</span></span>

<span data-ttu-id="11295-137">Gebruik de volgende queryparameter om de kwalificatie bij te werken.</span><span class="sxs-lookup"><span data-stu-id="11295-137">Use the following query parameter to update the qualification.</span></span>

| <span data-ttu-id="11295-138">Naam</span><span class="sxs-lookup"><span data-stu-id="11295-138">Name</span></span>                   | <span data-ttu-id="11295-139">Type</span><span class="sxs-lookup"><span data-stu-id="11295-139">Type</span></span> | <span data-ttu-id="11295-140">Vereist</span><span class="sxs-lookup"><span data-stu-id="11295-140">Required</span></span> | <span data-ttu-id="11295-141">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="11295-141">Description</span></span>                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="11295-142">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="11295-142">**customer-tenant-id**</span></span> | <span data-ttu-id="11295-143">GUID</span><span class="sxs-lookup"><span data-stu-id="11295-143">GUID</span></span> | <span data-ttu-id="11295-144">Yes</span><span class="sxs-lookup"><span data-stu-id="11295-144">Yes</span></span>      | <span data-ttu-id="11295-145">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="11295-145">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="11295-146">**validationCode**</span><span class="sxs-lookup"><span data-stu-id="11295-146">**validationCode**</span></span>     | <span data-ttu-id="11295-147">int</span><span class="sxs-lookup"><span data-stu-id="11295-147">int</span></span>  | <span data-ttu-id="11295-148">No</span><span class="sxs-lookup"><span data-stu-id="11295-148">No</span></span>       | <span data-ttu-id="11295-149">Alleen nodig voor Government Community Cloud.</span><span class="sxs-lookup"><span data-stu-id="11295-149">Only needed for Government Community Cloud.</span></span>                                                                                                            |

### <a name="request-headers"></a><span data-ttu-id="11295-150">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="11295-150">Request headers</span></span>

<span data-ttu-id="11295-151">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="11295-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="11295-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="11295-152">Request body</span></span>

<span data-ttu-id="11295-153">In deze tabel wordt het kwalificatieobject in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="11295-153">This table describes the qualification object in the request body.</span></span>

<span data-ttu-id="11295-154">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="11295-154">Property</span></span> | <span data-ttu-id="11295-155">Type</span><span class="sxs-lookup"><span data-stu-id="11295-155">Type</span></span> | <span data-ttu-id="11295-156">Vereist</span><span class="sxs-lookup"><span data-stu-id="11295-156">Required</span></span> | <span data-ttu-id="11295-157">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="11295-157">Description</span></span>
-------- | ---- | -------- | -----------
<span data-ttu-id="11295-158">Kwalificatie</span><span class="sxs-lookup"><span data-stu-id="11295-158">Qualification</span></span> | <span data-ttu-id="11295-159">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="11295-159">string</span></span> | <span data-ttu-id="11295-160">Yes</span><span class="sxs-lookup"><span data-stu-id="11295-160">Yes</span></span> | <span data-ttu-id="11295-161">De tekenreekswaarde uit [**de enum CustomerQualification.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification)</span><span class="sxs-lookup"><span data-stu-id="11295-161">The string value from the [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) enum.</span></span>

### <a name="request-example"></a><span data-ttu-id="11295-162">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="11295-162">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="11295-163">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="11295-163">REST response</span></span>

<span data-ttu-id="11295-164">Als dit lukt, retourneert deze methode een kwalificatieobject in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="11295-164">If successful, this method returns a qualifications object in the response body.</span></span> <span data-ttu-id="11295-165">Hieronder vindt u een voorbeeld van de **POST-aanroep** van een klant (met een eerdere kwalificatie van **Geen**) met de **kwalificatie voor** het onderwijs.</span><span class="sxs-lookup"><span data-stu-id="11295-165">Below is an example of the **POST** call on a customer (with a previous qualification of **None**) with the **Education** qualification.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="11295-166">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="11295-166">Response success and error codes</span></span>

<span data-ttu-id="11295-167">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="11295-167">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="11295-168">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="11295-168">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="11295-169">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="11295-169">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="11295-170">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="11295-170">Response example</span></span>

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

## <a name="related-articles"></a><span data-ttu-id="11295-171">Verwante artikelen:</span><span class="sxs-lookup"><span data-stu-id="11295-171">Related articles</span></span>

- [<span data-ttu-id="11295-172">De kwalificaties van een klant krijgen</span><span class="sxs-lookup"><span data-stu-id="11295-172">Get a customer's qualifications</span></span>](./get-customer-qualification-asynchronous.md)
- [<span data-ttu-id="11295-173">De validatiecodes van een partner ophalen</span><span class="sxs-lookup"><span data-stu-id="11295-173">Get a partner's validation codes</span></span>](get-a-partner-s-validation-codes.md)
