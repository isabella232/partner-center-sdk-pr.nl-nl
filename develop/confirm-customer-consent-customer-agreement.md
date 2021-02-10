---
title: Acceptatie door de klant van Microsoft-klantovereenkomst bevestigen
description: Meer informatie over het bevestigen van de acceptatie van klanten van de micro soft-klant overeenkomst met behulp van partner Center-Api's.
ms.date: 02/08/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 62a6cebd5d6d093377dd5940dcff6204b7095c70
ms.sourcegitcommit: ebb36208d6e2dea705f62b7d60d471f10c55132e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/09/2021
ms.locfileid: "100006075"
---
# <a name="confirm-customer-acceptance-of-the-microsoft-customer-agreement-using-partner-center-apis"></a><span data-ttu-id="d540f-103">Acceptatie van klant bevestigen voor de micro soft-klant overeenkomst met behulp van partner Center-Api's</span><span class="sxs-lookup"><span data-stu-id="d540f-103">Confirm customer acceptance of the Microsoft Customer Agreement using Partner Center APIs</span></span>

<span data-ttu-id="d540f-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="d540f-104">**Applies to:**</span></span>

- <span data-ttu-id="d540f-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="d540f-105">Partner Center</span></span>

<span data-ttu-id="d540f-106">Het partner Centrum ondersteunt momenteel alleen bevestiging van klant acceptatie van de micro soft-klant overeenkomst in de *open bare cloud van micro soft*.</span><span class="sxs-lookup"><span data-stu-id="d540f-106">Partner Center currently supports confirmation of customer acceptance of the Microsoft Customer Agreement only in the *Microsoft public cloud*.</span></span> <span data-ttu-id="d540f-107">Deze functionaliteit is momenteel niet van toepassing op:</span><span class="sxs-lookup"><span data-stu-id="d540f-107">This functionality doesn't currently apply to:</span></span>

- <span data-ttu-id="d540f-108">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="d540f-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="d540f-109">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="d540f-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="d540f-110">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d540f-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d540f-111">In dit artikel wordt beschreven hoe u de acceptatie van klanten van micro soft-klanten overeenkomst bevestigt of opnieuw bevestigt.</span><span class="sxs-lookup"><span data-stu-id="d540f-111">This article describes how to confirm or re-confirm customer acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d540f-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d540f-112">Prerequisites</span></span>

- <span data-ttu-id="d540f-113">Als u gebruikmaakt van de .NET SDK van partner Center, is versie 1,14 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="d540f-113">If you are using the Partner Center .NET SDK, version 1.14 or newer is required.</span></span>

- <span data-ttu-id="d540f-114">Referenties zoals beschreven in [Partner Center-verificatie](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d540f-114">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="d540f-115">*Dit scenario ondersteunt alleen app + gebruikers verificatie.*</span><span class="sxs-lookup"><span data-stu-id="d540f-115">*This scenario only supports App+User authentication.*</span></span>

- <span data-ttu-id="d540f-116">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d540f-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d540f-117">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="d540f-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d540f-118">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="d540f-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d540f-119">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="d540f-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d540f-120">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="d540f-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d540f-121">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d540f-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="d540f-122">De datum (**dateAgreed**) waarop de klant de micro soft-klant overeenkomst heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="d540f-122">The date (**dateAgreed**) when the customer accepted the Microsoft Customer Agreement.</span></span>

- <span data-ttu-id="d540f-123">Informatie over de gebruiker van de organisatie van de klant die de micro soft-klant overeenkomst heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="d540f-123">Information about the user from the customer organization that accepted the Microsoft Customer Agreement.</span></span> <span data-ttu-id="d540f-124">Dit omvat:</span><span class="sxs-lookup"><span data-stu-id="d540f-124">This includes:</span></span>
  - <span data-ttu-id="d540f-125">Voornaam</span><span class="sxs-lookup"><span data-stu-id="d540f-125">First name</span></span>
  - <span data-ttu-id="d540f-126">Achternaam</span><span class="sxs-lookup"><span data-stu-id="d540f-126">Last name</span></span>
  - <span data-ttu-id="d540f-127">E-mailadres</span><span class="sxs-lookup"><span data-stu-id="d540f-127">Email address</span></span>
  - <span data-ttu-id="d540f-128">Telefoon nummer (optioneel)</span><span class="sxs-lookup"><span data-stu-id="d540f-128">Phone number (optional)</span></span>
- <span data-ttu-id="d540f-129">Als de volgende waarden voor een klant worden gewijzigd, kan het partner centrum een andere overeenkomst voor die klant maken: voor naam achternaam e-mail adres telefoon nummer, anders ontvangen partners de volgende fout code, vanwege een dubbele klant die wordt gemaakt</span><span class="sxs-lookup"><span data-stu-id="d540f-129">If the following values change for a customer, Partner Center  will allow for another agreement to be created for that customer:       First Name       Last Name       Email address       Phone number Otherwise partners will receive the following error code, due to a duplicate customer being created</span></span>


```
{
"code": 600061,
"message": "A partner confirmed agreement already exists for the customer.",
"description": "A partner confirmed agreement already exists for the customer.",
"errorName": "PartnerConfirmedAgreementAlreadyExists",
"isRetryable": false,
"parameters": {},
"errorMessageExtended": "InternalErrorCode=600061"
}
 ```

## <a name="net"></a><span data-ttu-id="d540f-130">.NET</span><span class="sxs-lookup"><span data-stu-id="d540f-130">.NET</span></span>

<span data-ttu-id="d540f-131">Bevestigen of herbevestigen van de acceptatie van de klant door de klant overeenkomst van micro soft:</span><span class="sxs-lookup"><span data-stu-id="d540f-131">To confirm or re-confirm customer acceptance of the Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="d540f-132">Haal de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst op.</span><span class="sxs-lookup"><span data-stu-id="d540f-132">Retrieve the agreement metadata for the Microsoft Customer Agreement.</span></span> <span data-ttu-id="d540f-133">U moet de **ontbrekende templateid** van de micro soft-klant overeenkomst verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="d540f-133">You must obtain the **templateId** of the Microsoft Customer Agreement.</span></span> <span data-ttu-id="d540f-134">Zie voor meer informatie de [meta gegevens van de overeenkomst ophalen voor de micro soft-klant overeenkomst](get-customer-agreement-metadata.md).</span><span class="sxs-lookup"><span data-stu-id="d540f-134">For more details, see [Get agreement metadata for Microsoft Customer Agreement](get-customer-agreement-metadata.md).</span></span>

   ```csharp
   // IAggregatePartner partnerOperations;

   string agreementType = "MicrosoftCustomerAgreement";

   var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
   ```

2. <span data-ttu-id="d540f-135">Maak een nieuw object **overeenkomst** met details van de bevestiging.</span><span class="sxs-lookup"><span data-stu-id="d540f-135">Create a new **Agreement** object containing details of the confirmation.</span></span>

3. <span data-ttu-id="d540f-136">Gebruik de verzameling **IAgreggatePartner. Customers** en roep de methode **ById** aan met de opgegeven **klant-Tenant-id**.</span><span class="sxs-lookup"><span data-stu-id="d540f-136">Use the **IAgreggatePartner.Customers** collection and call the **ById** method with the specified **customer-tenant-id**.</span></span>

4. <span data-ttu-id="d540f-137">Gebruik de eigenschap **overeenkomsten** , gevolgd door het aanroepen van **Create** of **CreateAsync**.</span><span class="sxs-lookup"><span data-stu-id="d540f-137">Use the **Agreements** property, followed by calling **Create** or **CreateAsync**.</span></span>

   ```csharp
   // string selectedCustomerId;

   var agreementToCreate = new Agreement
   {
       DateAgreed = DateTime.UtcNow,
       TemplateId = microsoftCustomerAgreementDetails.TemplateId,
       PrimaryContact = new Contact
       {
           FirstName = "Tania",
           LastName = "Carr",
           Email = "someone@example.com",
           PhoneNumber = "1234567890"
       }
   };

   Agreement agreement = partnerOperations.Customers.ById(selectedCustomerId).Agreements.Create(agreementToCreate);
   ```

<span data-ttu-id="d540f-138">Een volledig voor beeld vindt u in de [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) -klasse in het [console test-app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) -project.</span><span class="sxs-lookup"><span data-stu-id="d540f-138">A complete sample can be found in the [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="rest-request"></a><span data-ttu-id="d540f-139">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="d540f-139">REST request</span></span>

<span data-ttu-id="d540f-140">Bevestigen of herbevestigen van de acceptatie van de klant door de klant overeenkomst van micro soft:</span><span class="sxs-lookup"><span data-stu-id="d540f-140">To confirm or re-confirm customer acceptance of the Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="d540f-141">Haal de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst op.</span><span class="sxs-lookup"><span data-stu-id="d540f-141">Retrieve the agreement metadata for the Microsoft Customer Agreement.</span></span> <span data-ttu-id="d540f-142">U moet de **ontbrekende templateid** van de micro soft-klant overeenkomst verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="d540f-142">You must obtain the **templateId** of the Microsoft Customer Agreement.</span></span> <span data-ttu-id="d540f-143">Zie voor meer informatie de [meta gegevens van de overeenkomst ophalen voor de micro soft-klant overeenkomst](get-customer-agreement-metadata.md).</span><span class="sxs-lookup"><span data-stu-id="d540f-143">For more details, see [Get agreement metadata for Microsoft Customer Agreement](get-customer-agreement-metadata.md).</span></span>

2. <span data-ttu-id="d540f-144">Maak een nieuwe [ **overeenkomst** resource](agreement-resources.md) om te bevestigen dat een klant de micro soft-klant overeenkomst heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="d540f-144">Create a new [**Agreement** resource](agreement-resources.md) to confirm that a customer has accepted the Microsoft Customer Agreement.</span></span> <span data-ttu-id="d540f-145">Gebruik de volgende [syntaxis voor rest-aanvragen](#request-syntax).</span><span class="sxs-lookup"><span data-stu-id="d540f-145">Use the following [REST request syntax](#request-syntax).</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d540f-146">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d540f-146">Request syntax</span></span>

| <span data-ttu-id="d540f-147">Methode</span><span class="sxs-lookup"><span data-stu-id="d540f-147">Method</span></span> | <span data-ttu-id="d540f-148">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="d540f-148">Request URI</span></span>                                                                                        |
|--------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d540f-149">POST</span><span class="sxs-lookup"><span data-stu-id="d540f-149">POST</span></span>   | <span data-ttu-id="d540f-150">[*\{ BASEURL \}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/agreements http/1.1</span><span class="sxs-lookup"><span data-stu-id="d540f-150">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="d540f-151">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="d540f-151">URI parameter</span></span>

<span data-ttu-id="d540f-152">Gebruik de volgende query parameter om de klant op te geven die u wilt bevestigen.</span><span class="sxs-lookup"><span data-stu-id="d540f-152">Use the following query parameter to specify the customer that you're confirming.</span></span>

| <span data-ttu-id="d540f-153">Naam</span><span class="sxs-lookup"><span data-stu-id="d540f-153">Name</span></span>               | <span data-ttu-id="d540f-154">Type</span><span class="sxs-lookup"><span data-stu-id="d540f-154">Type</span></span> | <span data-ttu-id="d540f-155">Vereist</span><span class="sxs-lookup"><span data-stu-id="d540f-155">Required</span></span> | <span data-ttu-id="d540f-156">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d540f-156">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="d540f-157">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="d540f-157">customer-tenant-id</span></span> | <span data-ttu-id="d540f-158">GUID</span><span class="sxs-lookup"><span data-stu-id="d540f-158">GUID</span></span> | <span data-ttu-id="d540f-159">Ja</span><span class="sxs-lookup"><span data-stu-id="d540f-159">Yes</span></span> | <span data-ttu-id="d540f-160">De waarde is een **klant-Tenant-id** van de GUID-indeling, een id waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="d540f-160">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d540f-161">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="d540f-161">Request headers</span></span>

<span data-ttu-id="d540f-162">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d540f-162">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d540f-163">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="d540f-163">Request body</span></span>

<span data-ttu-id="d540f-164">In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de REST-aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="d540f-164">This table describes the required properties in the REST request body.</span></span>

| <span data-ttu-id="d540f-165">Naam</span><span class="sxs-lookup"><span data-stu-id="d540f-165">Name</span></span>      | <span data-ttu-id="d540f-166">Type</span><span class="sxs-lookup"><span data-stu-id="d540f-166">Type</span></span>   | <span data-ttu-id="d540f-167">Description</span><span class="sxs-lookup"><span data-stu-id="d540f-167">Description</span></span>                                                                                  |
|-----------|--------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="d540f-168">Overeenkomst</span><span class="sxs-lookup"><span data-stu-id="d540f-168">Agreement</span></span> | <span data-ttu-id="d540f-169">object</span><span class="sxs-lookup"><span data-stu-id="d540f-169">object</span></span> | <span data-ttu-id="d540f-170">Details van de partner voor het bevestigen van de acceptatie van de klant door de klant overeenkomst van micro soft.</span><span class="sxs-lookup"><span data-stu-id="d540f-170">Details provided by partner to confirm customer acceptance of the Microsoft Customer Agreement.</span></span> |

#### <a name="agreement"></a><span data-ttu-id="d540f-171">Overeenkomst</span><span class="sxs-lookup"><span data-stu-id="d540f-171">Agreement</span></span>

<span data-ttu-id="d540f-172">In deze tabel worden de minimale vereiste velden voor het maken van een [ **overeenkomst** resource](agreement-resources.md)beschreven.</span><span class="sxs-lookup"><span data-stu-id="d540f-172">This table describes the minimum required fields to create an [**Agreement** resource](agreement-resources.md).</span></span>

| <span data-ttu-id="d540f-173">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="d540f-173">Property</span></span>       | <span data-ttu-id="d540f-174">Type</span><span class="sxs-lookup"><span data-stu-id="d540f-174">Type</span></span>   | <span data-ttu-id="d540f-175">Description</span><span class="sxs-lookup"><span data-stu-id="d540f-175">Description</span></span>                              |
|----------------|--------|------------------------------------------|
| <span data-ttu-id="d540f-176">primaryContact</span><span class="sxs-lookup"><span data-stu-id="d540f-176">primaryContact</span></span> | [<span data-ttu-id="d540f-177">Contact</span><span class="sxs-lookup"><span data-stu-id="d540f-177">Contact</span></span>](./utility-resources.md#contact) | <span data-ttu-id="d540f-178">Informatie over de gebruiker van de organisatie van de klant die de klant overeenkomst van micro soft heeft geaccepteerd, waaronder:  **FirstName**, **LastName**, **email** en **phonenumber** (optioneel)</span><span class="sxs-lookup"><span data-stu-id="d540f-178">Information about the user from the customer organization who accepted the Microsoft Customer Agreement, including:  **firstName**, **lastName**, **email** and **phoneNumber** (optional)</span></span> |
| <span data-ttu-id="d540f-179">dateAgreed</span><span class="sxs-lookup"><span data-stu-id="d540f-179">dateAgreed</span></span>     | <span data-ttu-id="d540f-180">teken reeks in UTC-datum tijd notatie</span><span class="sxs-lookup"><span data-stu-id="d540f-180">string in UTC date time format</span></span> |<span data-ttu-id="d540f-181">De datum waarop de klant de overeenkomst heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="d540f-181">The date when the customer accepted the agreement.</span></span> |
| <span data-ttu-id="d540f-182">Ontbrekende templateid</span><span class="sxs-lookup"><span data-stu-id="d540f-182">templateId</span></span>     | <span data-ttu-id="d540f-183">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d540f-183">string</span></span> | <span data-ttu-id="d540f-184">De unieke id van het overeenkomst type dat door de klant is geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="d540f-184">Unique identifier of the agreement type accepted by the customer.</span></span> <span data-ttu-id="d540f-185">U kunt de **ontbrekende templateid** voor de micro soft-klant overeenkomst verkrijgen door de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst op te halen.</span><span class="sxs-lookup"><span data-stu-id="d540f-185">You can obtain the **templateId** for Microsoft Customer Agreement by retrieving the agreement metadata for Microsoft Customer Agreement.</span></span> <span data-ttu-id="d540f-186">Zie de [meta gegevens van de overeenkomst voor micro soft Customer Agreement ophalen](./get-customer-agreement-metadata.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d540f-186">See [Get agreement metadata for Microsoft Customer Agreement](./get-customer-agreement-metadata.md) for details.</span></span> |
| <span data-ttu-id="d540f-187">type</span><span class="sxs-lookup"><span data-stu-id="d540f-187">type</span></span>           | <span data-ttu-id="d540f-188">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d540f-188">string</span></span> | <span data-ttu-id="d540f-189">Type overeenkomst geaccepteerd door de klant.</span><span class="sxs-lookup"><span data-stu-id="d540f-189">Agreement type accepted by the customer.</span></span> <span data-ttu-id="d540f-190">Gebruik ' MicrosoftCustomerAgreement ' als de klant de micro soft-klant overeenkomst heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="d540f-190">Use "MicrosoftCustomerAgreement" if customer accepted the Microsoft Customer Agreement.</span></span> |

#### <a name="request-example"></a><span data-ttu-id="d540f-191">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d540f-191">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements HTTP/1.1
Authorization: Bearer <token>
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "primaryContact": {
        "firstName": "Tania",
        "lastName": "Carr",
        "email": "someone@example.com",
        "phoneNumber": "1234567890"
    },
    "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
    "dateAgreed": "2018-06-14T00:00:00.000Z",
    "type": "MicrosoftCustomerAgreement"
}
```

## <a name="rest-response"></a><span data-ttu-id="d540f-192">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="d540f-192">REST response</span></span>

<span data-ttu-id="d540f-193">Als deze methode is geslaagd, wordt een [ **overeenkomst** resource](./agreement-resources.md)geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d540f-193">If successful, this method returns an [**Agreement** resource](./agreement-resources.md).</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d540f-194">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="d540f-194">Response success and error codes</span></span>

<span data-ttu-id="d540f-195">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="d540f-195">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="d540f-196">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="d540f-196">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d540f-197">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="d540f-197">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

#### <a name="response-example"></a><span data-ttu-id="d540f-198">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="d540f-198">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 261
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "userId": "3d6f2c09-eb40-48ca-a4b3-d24c9c007531",
    "primaryContact": {
        "firstName": "Tania",
        "lastName": "Carr",
        "email": "someone@example.com",
        "phoneNumber": "1234567890"
    },
    "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
    "dateAgreed": "2018-06-14T00:00:00.000Z",
    "type": "MicrosoftCustomerAgreement"
}
```
