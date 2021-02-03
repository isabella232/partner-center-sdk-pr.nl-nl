---
title: Acceptatie door de klant van Microsoft-klantovereenkomst bevestigen
description: Meer informatie over het bevestigen van de acceptatie van klanten van de micro soft-klant overeenkomst met behulp van partner Center-Api's.
ms.date: 02/04/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 239ca43c70fb8aa7f0d06e564e6c0726b235ffbe
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2020
ms.locfileid: "97767619"
---
# <a name="confirm-customer-acceptance-of-the-microsoft-customer-agreement-using-partner-center-apis"></a><span data-ttu-id="3b256-103">Acceptatie van klant bevestigen voor de micro soft-klant overeenkomst met behulp van partner Center-Api's</span><span class="sxs-lookup"><span data-stu-id="3b256-103">Confirm customer acceptance of the Microsoft Customer Agreement using Partner Center APIs</span></span>

<span data-ttu-id="3b256-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="3b256-104">**Applies to:**</span></span>

- <span data-ttu-id="3b256-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="3b256-105">Partner Center</span></span>

<span data-ttu-id="3b256-106">Het partner Centrum ondersteunt momenteel alleen bevestiging van klant acceptatie van de micro soft-klant overeenkomst in de *open bare cloud van micro soft*.</span><span class="sxs-lookup"><span data-stu-id="3b256-106">Partner Center currently supports confirmation of customer acceptance of the Microsoft Customer Agreement only in the *Microsoft public cloud*.</span></span> <span data-ttu-id="3b256-107">Deze functionaliteit is momenteel niet van toepassing op:</span><span class="sxs-lookup"><span data-stu-id="3b256-107">This functionality doesn't currently apply to:</span></span>

- <span data-ttu-id="3b256-108">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="3b256-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="3b256-109">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="3b256-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="3b256-110">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="3b256-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="3b256-111">In dit artikel wordt beschreven hoe u de acceptatie van klanten van micro soft-klanten overeenkomst bevestigt of opnieuw bevestigt.</span><span class="sxs-lookup"><span data-stu-id="3b256-111">This article describes how to confirm or re-confirm customer acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3b256-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3b256-112">Prerequisites</span></span>

- <span data-ttu-id="3b256-113">Als u gebruikmaakt van de .NET SDK van partner Center, is versie 1,14 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="3b256-113">If you are using the Partner Center .NET SDK, version 1.14 or newer is required.</span></span>

- <span data-ttu-id="3b256-114">Referenties zoals beschreven in [Partner Center-verificatie](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3b256-114">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="3b256-115">*Dit scenario ondersteunt alleen app + gebruikers verificatie.*</span><span class="sxs-lookup"><span data-stu-id="3b256-115">*This scenario only supports App+User authentication.*</span></span>

- <span data-ttu-id="3b256-116">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3b256-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="3b256-117">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="3b256-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="3b256-118">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="3b256-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="3b256-119">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="3b256-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="3b256-120">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="3b256-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="3b256-121">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3b256-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="3b256-122">De datum (**dateAgreed**) waarop de klant de micro soft-klant overeenkomst heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="3b256-122">The date (**dateAgreed**) when the customer accepted the Microsoft Customer Agreement.</span></span>

- <span data-ttu-id="3b256-123">Informatie over de gebruiker van de organisatie van de klant die de micro soft-klant overeenkomst heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="3b256-123">Information about the user from the customer organization that accepted the Microsoft Customer Agreement.</span></span> <span data-ttu-id="3b256-124">Dit omvat:</span><span class="sxs-lookup"><span data-stu-id="3b256-124">This includes:</span></span>
  - <span data-ttu-id="3b256-125">Voornaam</span><span class="sxs-lookup"><span data-stu-id="3b256-125">First name</span></span>
  - <span data-ttu-id="3b256-126">Achternaam</span><span class="sxs-lookup"><span data-stu-id="3b256-126">Last name</span></span>
  - <span data-ttu-id="3b256-127">E-mailadres</span><span class="sxs-lookup"><span data-stu-id="3b256-127">Email address</span></span>
  - <span data-ttu-id="3b256-128">Telefoon nummer (optioneel)</span><span class="sxs-lookup"><span data-stu-id="3b256-128">Phone number (optional)</span></span>

## <a name="net"></a><span data-ttu-id="3b256-129">.NET</span><span class="sxs-lookup"><span data-stu-id="3b256-129">.NET</span></span>

<span data-ttu-id="3b256-130">Bevestigen of herbevestigen van de acceptatie van de klant door de klant overeenkomst van micro soft:</span><span class="sxs-lookup"><span data-stu-id="3b256-130">To confirm or re-confirm customer acceptance of the Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="3b256-131">Haal de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst op.</span><span class="sxs-lookup"><span data-stu-id="3b256-131">Retrieve the agreement metadata for the Microsoft Customer Agreement.</span></span> <span data-ttu-id="3b256-132">U moet de **ontbrekende templateid** van de micro soft-klant overeenkomst verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="3b256-132">You must obtain the **templateId** of the Microsoft Customer Agreement.</span></span> <span data-ttu-id="3b256-133">Zie voor meer informatie de [meta gegevens van de overeenkomst ophalen voor de micro soft-klant overeenkomst](get-customer-agreement-metadata.md).</span><span class="sxs-lookup"><span data-stu-id="3b256-133">For more details, see [Get agreement metadata for Microsoft Customer Agreement](get-customer-agreement-metadata.md).</span></span>

   ```csharp
   // IAggregatePartner partnerOperations;

   string agreementType = "MicrosoftCustomerAgreement";

   var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
   ```

2. <span data-ttu-id="3b256-134">Maak een nieuw object **overeenkomst** met details van de bevestiging.</span><span class="sxs-lookup"><span data-stu-id="3b256-134">Create a new **Agreement** object containing details of the confirmation.</span></span>

3. <span data-ttu-id="3b256-135">Gebruik de verzameling **IAgreggatePartner. Customers** en roep de methode **ById** aan met de opgegeven **klant-Tenant-id**.</span><span class="sxs-lookup"><span data-stu-id="3b256-135">Use the **IAgreggatePartner.Customers** collection and call the **ById** method with the specified **customer-tenant-id**.</span></span>

4. <span data-ttu-id="3b256-136">Gebruik de eigenschap **overeenkomsten** , gevolgd door het aanroepen van **Create** of **CreateAsync**.</span><span class="sxs-lookup"><span data-stu-id="3b256-136">Use the **Agreements** property, followed by calling **Create** or **CreateAsync**.</span></span>

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

<span data-ttu-id="3b256-137">Een volledig voor beeld vindt u in de [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) -klasse in het [console test-app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) -project.</span><span class="sxs-lookup"><span data-stu-id="3b256-137">A complete sample can be found in the [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="rest-request"></a><span data-ttu-id="3b256-138">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="3b256-138">REST request</span></span>

<span data-ttu-id="3b256-139">Bevestigen of herbevestigen van de acceptatie van de klant door de klant overeenkomst van micro soft:</span><span class="sxs-lookup"><span data-stu-id="3b256-139">To confirm or re-confirm customer acceptance of the Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="3b256-140">Haal de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst op.</span><span class="sxs-lookup"><span data-stu-id="3b256-140">Retrieve the agreement metadata for the Microsoft Customer Agreement.</span></span> <span data-ttu-id="3b256-141">U moet de **ontbrekende templateid** van de micro soft-klant overeenkomst verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="3b256-141">You must obtain the **templateId** of the Microsoft Customer Agreement.</span></span> <span data-ttu-id="3b256-142">Zie voor meer informatie de [meta gegevens van de overeenkomst ophalen voor de micro soft-klant overeenkomst](get-customer-agreement-metadata.md).</span><span class="sxs-lookup"><span data-stu-id="3b256-142">For more details, see [Get agreement metadata for Microsoft Customer Agreement](get-customer-agreement-metadata.md).</span></span>

2. <span data-ttu-id="3b256-143">Maak een nieuwe [ **overeenkomst** resource](agreement-resources.md) om te bevestigen dat een klant de micro soft-klant overeenkomst heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="3b256-143">Create a new [**Agreement** resource](agreement-resources.md) to confirm that a customer has accepted the Microsoft Customer Agreement.</span></span> <span data-ttu-id="3b256-144">Gebruik de volgende [syntaxis voor rest-aanvragen](#request-syntax).</span><span class="sxs-lookup"><span data-stu-id="3b256-144">Use the following [REST request syntax](#request-syntax).</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3b256-145">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3b256-145">Request syntax</span></span>

| <span data-ttu-id="3b256-146">Methode</span><span class="sxs-lookup"><span data-stu-id="3b256-146">Method</span></span> | <span data-ttu-id="3b256-147">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="3b256-147">Request URI</span></span>                                                                                        |
|--------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3b256-148">POST</span><span class="sxs-lookup"><span data-stu-id="3b256-148">POST</span></span>   | <span data-ttu-id="3b256-149">[*\{ BASEURL \}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/agreements http/1.1</span><span class="sxs-lookup"><span data-stu-id="3b256-149">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="3b256-150">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="3b256-150">URI parameter</span></span>

<span data-ttu-id="3b256-151">Gebruik de volgende query parameter om de klant op te geven die u wilt bevestigen.</span><span class="sxs-lookup"><span data-stu-id="3b256-151">Use the following query parameter to specify the customer that you're confirming.</span></span>

| <span data-ttu-id="3b256-152">Naam</span><span class="sxs-lookup"><span data-stu-id="3b256-152">Name</span></span>               | <span data-ttu-id="3b256-153">Type</span><span class="sxs-lookup"><span data-stu-id="3b256-153">Type</span></span> | <span data-ttu-id="3b256-154">Vereist</span><span class="sxs-lookup"><span data-stu-id="3b256-154">Required</span></span> | <span data-ttu-id="3b256-155">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3b256-155">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="3b256-156">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="3b256-156">customer-tenant-id</span></span> | <span data-ttu-id="3b256-157">GUID</span><span class="sxs-lookup"><span data-stu-id="3b256-157">GUID</span></span> | <span data-ttu-id="3b256-158">Yes</span><span class="sxs-lookup"><span data-stu-id="3b256-158">Yes</span></span> | <span data-ttu-id="3b256-159">De waarde is een **klant-Tenant-id** van de GUID-indeling, een id waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="3b256-159">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="3b256-160">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="3b256-160">Request headers</span></span>

<span data-ttu-id="3b256-161">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="3b256-161">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3b256-162">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="3b256-162">Request body</span></span>

<span data-ttu-id="3b256-163">In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de REST-aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="3b256-163">This table describes the required properties in the REST request body.</span></span>

| <span data-ttu-id="3b256-164">Naam</span><span class="sxs-lookup"><span data-stu-id="3b256-164">Name</span></span>      | <span data-ttu-id="3b256-165">Type</span><span class="sxs-lookup"><span data-stu-id="3b256-165">Type</span></span>   | <span data-ttu-id="3b256-166">Description</span><span class="sxs-lookup"><span data-stu-id="3b256-166">Description</span></span>                                                                                  |
|-----------|--------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="3b256-167">Overeenkomst</span><span class="sxs-lookup"><span data-stu-id="3b256-167">Agreement</span></span> | <span data-ttu-id="3b256-168">object</span><span class="sxs-lookup"><span data-stu-id="3b256-168">object</span></span> | <span data-ttu-id="3b256-169">Details van de partner voor het bevestigen van de acceptatie van de klant door de klant overeenkomst van micro soft.</span><span class="sxs-lookup"><span data-stu-id="3b256-169">Details provided by partner to confirm customer acceptance of the Microsoft Customer Agreement.</span></span> |

#### <a name="agreement"></a><span data-ttu-id="3b256-170">Overeenkomst</span><span class="sxs-lookup"><span data-stu-id="3b256-170">Agreement</span></span>

<span data-ttu-id="3b256-171">In deze tabel worden de minimale vereiste velden voor het maken van een [ **overeenkomst** resource](agreement-resources.md)beschreven.</span><span class="sxs-lookup"><span data-stu-id="3b256-171">This table describes the minimum required fields to create an [**Agreement** resource](agreement-resources.md).</span></span>

| <span data-ttu-id="3b256-172">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="3b256-172">Property</span></span>       | <span data-ttu-id="3b256-173">Type</span><span class="sxs-lookup"><span data-stu-id="3b256-173">Type</span></span>   | <span data-ttu-id="3b256-174">Description</span><span class="sxs-lookup"><span data-stu-id="3b256-174">Description</span></span>                              |
|----------------|--------|------------------------------------------|
| <span data-ttu-id="3b256-175">primaryContact</span><span class="sxs-lookup"><span data-stu-id="3b256-175">primaryContact</span></span> | [<span data-ttu-id="3b256-176">Contact</span><span class="sxs-lookup"><span data-stu-id="3b256-176">Contact</span></span>](./utility-resources.md#contact) | <span data-ttu-id="3b256-177">Informatie over de gebruiker van de organisatie van de klant die de klant overeenkomst van micro soft heeft geaccepteerd, waaronder:  **FirstName**, **LastName**, **email** en **phonenumber** (optioneel)</span><span class="sxs-lookup"><span data-stu-id="3b256-177">Information about the user from the customer organization who accepted the Microsoft Customer Agreement, including:  **firstName**, **lastName**, **email** and **phoneNumber** (optional)</span></span> |
| <span data-ttu-id="3b256-178">dateAgreed</span><span class="sxs-lookup"><span data-stu-id="3b256-178">dateAgreed</span></span>     | <span data-ttu-id="3b256-179">teken reeks in UTC-datum tijd notatie</span><span class="sxs-lookup"><span data-stu-id="3b256-179">string in UTC date time format</span></span> |<span data-ttu-id="3b256-180">De datum waarop de klant de overeenkomst heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="3b256-180">The date when the customer accepted the agreement.</span></span> |
| <span data-ttu-id="3b256-181">Ontbrekende templateid</span><span class="sxs-lookup"><span data-stu-id="3b256-181">templateId</span></span>     | <span data-ttu-id="3b256-182">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3b256-182">string</span></span> | <span data-ttu-id="3b256-183">De unieke id van het overeenkomst type dat door de klant is geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="3b256-183">Unique identifier of the agreement type accepted by the customer.</span></span> <span data-ttu-id="3b256-184">U kunt de **ontbrekende templateid** voor de micro soft-klant overeenkomst verkrijgen door de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst op te halen.</span><span class="sxs-lookup"><span data-stu-id="3b256-184">You can obtain the **templateId** for Microsoft Customer Agreement by retrieving the agreement metadata for Microsoft Customer Agreement.</span></span> <span data-ttu-id="3b256-185">Zie de [meta gegevens van de overeenkomst voor micro soft Customer Agreement ophalen](./get-customer-agreement-metadata.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3b256-185">See [Get agreement metadata for Microsoft Customer Agreement](./get-customer-agreement-metadata.md) for details.</span></span> |
| <span data-ttu-id="3b256-186">type</span><span class="sxs-lookup"><span data-stu-id="3b256-186">type</span></span>           | <span data-ttu-id="3b256-187">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3b256-187">string</span></span> | <span data-ttu-id="3b256-188">Type overeenkomst geaccepteerd door de klant.</span><span class="sxs-lookup"><span data-stu-id="3b256-188">Agreement type accepted by the customer.</span></span> <span data-ttu-id="3b256-189">Gebruik ' MicrosoftCustomerAgreement ' als de klant de micro soft-klant overeenkomst heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="3b256-189">Use "MicrosoftCustomerAgreement" if customer accepted the Microsoft Customer Agreement.</span></span> |

#### <a name="request-example"></a><span data-ttu-id="3b256-190">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3b256-190">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="3b256-191">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="3b256-191">REST response</span></span>

<span data-ttu-id="3b256-192">Als deze methode is geslaagd, wordt een [ **overeenkomst** resource](./agreement-resources.md)geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3b256-192">If successful, this method returns an [**Agreement** resource](./agreement-resources.md).</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3b256-193">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="3b256-193">Response success and error codes</span></span>

<span data-ttu-id="3b256-194">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="3b256-194">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="3b256-195">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="3b256-195">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3b256-196">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="3b256-196">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

#### <a name="response-example"></a><span data-ttu-id="3b256-197">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="3b256-197">Response example</span></span>

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
