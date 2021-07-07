---
title: Acceptatie door de klant van Microsoft-klantovereenkomst bevestigen
description: Meer informatie over hoe u de klantacceptatie van de Microsoft-klantovereenkomst met behulp Partner Center API's.
ms.date: 02/08/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 002508109191ede53cd06f25efc38286647fd67c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974009"
---
# <a name="confirm-customer-acceptance-of-the-microsoft-customer-agreement-using-partner-center-apis"></a><span data-ttu-id="09ffb-103">Bevestig dat de klant de Microsoft-klantovereenkomst met Partner Center API's</span><span class="sxs-lookup"><span data-stu-id="09ffb-103">Confirm customer acceptance of the Microsoft Customer Agreement using Partner Center APIs</span></span>

<span data-ttu-id="09ffb-104">**Van toepassing op**: Partner Center</span><span class="sxs-lookup"><span data-stu-id="09ffb-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="09ffb-105">**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="09ffb-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="09ffb-106">Partner Center ondersteunt momenteel bevestiging van de klantacceptatie van de Microsoft-klantovereenkomst alleen in de openbare Cloud van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="09ffb-106">Partner Center currently supports confirmation of customer acceptance of the Microsoft Customer Agreement only in the Microsoft public cloud.</span></span>

<span data-ttu-id="09ffb-107">In dit artikel wordt beschreven hoe u de acceptatie van de klant van de Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="09ffb-107">This article describes how to confirm or reconfirm customer acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="09ffb-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="09ffb-108">Prerequisites</span></span>

- <span data-ttu-id="09ffb-109">Als u de .NET SDK Partner Center, is versie 1.14 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="09ffb-109">If you are using the Partner Center .NET SDK, version 1.14 or newer is required.</span></span>

- <span data-ttu-id="09ffb-110">Referenties zoals beschreven in [Partner Center verificatie](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="09ffb-110">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="09ffb-111">*Dit scenario biedt alleen ondersteuning voor app- en gebruikersverificatie.*</span><span class="sxs-lookup"><span data-stu-id="09ffb-111">*This scenario only supports App+User authentication.*</span></span>

- <span data-ttu-id="09ffb-112">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="09ffb-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="09ffb-113">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="09ffb-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="09ffb-114">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="09ffb-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="09ffb-115">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="09ffb-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="09ffb-116">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="09ffb-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="09ffb-117">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="09ffb-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="09ffb-118">De datum (**dateAgreed**) wanneer de klant de Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="09ffb-118">The date (**dateAgreed**) when the customer accepted the Microsoft Customer Agreement.</span></span>

- <span data-ttu-id="09ffb-119">Informatie over de gebruiker van de klantorganisatie die de Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="09ffb-119">Information about the user from the customer organization that accepted the Microsoft Customer Agreement.</span></span> <span data-ttu-id="09ffb-120">Dit omvat:</span><span class="sxs-lookup"><span data-stu-id="09ffb-120">This includes:</span></span>
  - <span data-ttu-id="09ffb-121">Voornaam</span><span class="sxs-lookup"><span data-stu-id="09ffb-121">First name</span></span>
  - <span data-ttu-id="09ffb-122">Achternaam</span><span class="sxs-lookup"><span data-stu-id="09ffb-122">Last name</span></span>
  - <span data-ttu-id="09ffb-123">E-mailadres</span><span class="sxs-lookup"><span data-stu-id="09ffb-123">Email address</span></span>
  - <span data-ttu-id="09ffb-124">Telefoon getal (optioneel)</span><span class="sxs-lookup"><span data-stu-id="09ffb-124">Phone number (optional)</span></span>
- <span data-ttu-id="09ffb-125">Als de volgende waarden voor een klant worden gewijzigd, kan Partner Center een andere overeenkomst maken voor die klant: Voornaam achternaam e-mailadres Telefoon nummer Anders ontvangen partners de volgende foutcode omdat er een dubbele klant wordt gemaakt</span><span class="sxs-lookup"><span data-stu-id="09ffb-125">If the following values change for a customer, Partner Center  will allow for another agreement to be created for that customer:       First Name       Last Name       Email address       Phone number Otherwise partners will receive the following error code, due to a duplicate customer being created</span></span>


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

## <a name="net"></a><span data-ttu-id="09ffb-126">.NET</span><span class="sxs-lookup"><span data-stu-id="09ffb-126">.NET</span></span>

<span data-ttu-id="09ffb-127">Bevestig of bevestig de klantacceptatie van de Microsoft-klantovereenkomst:</span><span class="sxs-lookup"><span data-stu-id="09ffb-127">To confirm or reconfirm customer acceptance of the Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="09ffb-128">Haal de metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="09ffb-128">Retrieve the agreement metadata for the Microsoft Customer Agreement.</span></span> <span data-ttu-id="09ffb-129">U moet de **templateId van** de Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="09ffb-129">You must obtain the **templateId** of the Microsoft Customer Agreement.</span></span> <span data-ttu-id="09ffb-130">Zie Get [agreement metadata for Microsoft-klantovereenkomst (Metagegevens van overeenkomst verkrijgen voor Microsoft-klantovereenkomst) voor meer informatie.](get-customer-agreement-metadata.md)</span><span class="sxs-lookup"><span data-stu-id="09ffb-130">For more information, see [Get agreement metadata for Microsoft Customer Agreement](get-customer-agreement-metadata.md).</span></span>

   ```csharp
   // IAggregatePartner partnerOperations;

   string agreementType = "MicrosoftCustomerAgreement";

   var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
   ```

2. <span data-ttu-id="09ffb-131">Maak een nieuw **Agreement-object** met details van de bevestiging.</span><span class="sxs-lookup"><span data-stu-id="09ffb-131">Create a new **Agreement** object containing details of the confirmation.</span></span>

3. <span data-ttu-id="09ffb-132">Gebruik de **verzameling IAgreggatePartner.Customers** en roep de **ById-methode** aan met de opgegeven **customer-tenant-id**.</span><span class="sxs-lookup"><span data-stu-id="09ffb-132">Use the **IAgreggatePartner.Customers** collection and call the **ById** method with the specified **customer-tenant-id**.</span></span>

4. <span data-ttu-id="09ffb-133">Gebruik de **eigenschap Agreements,** gevolgd door het aanroepen **van Create** of **CreateAsync.**</span><span class="sxs-lookup"><span data-stu-id="09ffb-133">Use the **Agreements** property, followed by calling **Create** or **CreateAsync**.</span></span>

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

<span data-ttu-id="09ffb-134">Een volledig voorbeeld vindt u in de klasse [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) van het [consoletest-app-project.](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples)</span><span class="sxs-lookup"><span data-stu-id="09ffb-134">A complete sample can be found in the [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="rest-request"></a><span data-ttu-id="09ffb-135">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="09ffb-135">REST request</span></span>

<span data-ttu-id="09ffb-136">Bevestig of bevestig de klantacceptatie van de Microsoft-klantovereenkomst:</span><span class="sxs-lookup"><span data-stu-id="09ffb-136">To confirm or reconfirm customer acceptance of the Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="09ffb-137">Haal de metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="09ffb-137">Retrieve the agreement metadata for the Microsoft Customer Agreement.</span></span> <span data-ttu-id="09ffb-138">U moet de **templateId van** de Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="09ffb-138">You must obtain the **templateId** of the Microsoft Customer Agreement.</span></span> <span data-ttu-id="09ffb-139">Zie Get [agreement metadata for Microsoft-klantovereenkomst (Metagegevens van overeenkomst verkrijgen voor Microsoft-klantovereenkomst) voor meer informatie.](get-customer-agreement-metadata.md)</span><span class="sxs-lookup"><span data-stu-id="09ffb-139">For more information, see [Get agreement metadata for Microsoft Customer Agreement](get-customer-agreement-metadata.md).</span></span>

2. <span data-ttu-id="09ffb-140">Maak een nieuwe [ **overeenkomstresource**](agreement-resources.md) om te bevestigen dat een klant de Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="09ffb-140">Create a new [**Agreement** resource](agreement-resources.md) to confirm that a customer has accepted the Microsoft Customer Agreement.</span></span> <span data-ttu-id="09ffb-141">Gebruik de volgende [REST-aanvraagsyntaxis](#request-syntax).</span><span class="sxs-lookup"><span data-stu-id="09ffb-141">Use the following [REST request syntax](#request-syntax).</span></span>

### <a name="request-syntax"></a><span data-ttu-id="09ffb-142">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="09ffb-142">Request syntax</span></span>

| <span data-ttu-id="09ffb-143">Methode</span><span class="sxs-lookup"><span data-stu-id="09ffb-143">Method</span></span> | <span data-ttu-id="09ffb-144">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="09ffb-144">Request URI</span></span>                                                                                        |
|--------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="09ffb-145">POST</span><span class="sxs-lookup"><span data-stu-id="09ffb-145">POST</span></span>   | <span data-ttu-id="09ffb-146">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="09ffb-146">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="09ffb-147">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="09ffb-147">URI parameter</span></span>

<span data-ttu-id="09ffb-148">Gebruik de volgende queryparameter om de klant op te geven die u wilt bevestigen.</span><span class="sxs-lookup"><span data-stu-id="09ffb-148">Use the following query parameter to specify the customer that you're confirming.</span></span>

| <span data-ttu-id="09ffb-149">Naam</span><span class="sxs-lookup"><span data-stu-id="09ffb-149">Name</span></span>               | <span data-ttu-id="09ffb-150">Type</span><span class="sxs-lookup"><span data-stu-id="09ffb-150">Type</span></span> | <span data-ttu-id="09ffb-151">Vereist</span><span class="sxs-lookup"><span data-stu-id="09ffb-151">Required</span></span> | <span data-ttu-id="09ffb-152">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="09ffb-152">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="09ffb-153">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="09ffb-153">customer-tenant-id</span></span> | <span data-ttu-id="09ffb-154">GUID</span><span class="sxs-lookup"><span data-stu-id="09ffb-154">GUID</span></span> | <span data-ttu-id="09ffb-155">Ja</span><span class="sxs-lookup"><span data-stu-id="09ffb-155">Yes</span></span> | <span data-ttu-id="09ffb-156">De waarde is een **klant-tenant-id** in GUID-indeling. Dit is een id waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="09ffb-156">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="09ffb-157">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="09ffb-157">Request headers</span></span>

<span data-ttu-id="09ffb-158">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="09ffb-158">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="09ffb-159">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="09ffb-159">Request body</span></span>

<span data-ttu-id="09ffb-160">In deze tabel worden de vereiste eigenschappen in de rest-aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="09ffb-160">This table describes the required properties in the REST request body.</span></span>

| <span data-ttu-id="09ffb-161">Naam</span><span class="sxs-lookup"><span data-stu-id="09ffb-161">Name</span></span>      | <span data-ttu-id="09ffb-162">Type</span><span class="sxs-lookup"><span data-stu-id="09ffb-162">Type</span></span>   | <span data-ttu-id="09ffb-163">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="09ffb-163">Description</span></span>                                                                                  |
|-----------|--------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="09ffb-164">Overeenkomst</span><span class="sxs-lookup"><span data-stu-id="09ffb-164">Agreement</span></span> | <span data-ttu-id="09ffb-165">object</span><span class="sxs-lookup"><span data-stu-id="09ffb-165">object</span></span> | <span data-ttu-id="09ffb-166">Details die door de partner worden verstrekt om te bevestigen dat de klant de Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="09ffb-166">Details provided by partner to confirm customer acceptance of the Microsoft Customer Agreement.</span></span> |

#### <a name="agreement"></a><span data-ttu-id="09ffb-167">Overeenkomst</span><span class="sxs-lookup"><span data-stu-id="09ffb-167">Agreement</span></span>

<span data-ttu-id="09ffb-168">In deze tabel worden de minimaal vereiste velden beschreven voor het maken van een [ **Agreement-resource.**](agreement-resources.md)</span><span class="sxs-lookup"><span data-stu-id="09ffb-168">This table describes the minimum required fields to create an [**Agreement** resource](agreement-resources.md).</span></span>

| <span data-ttu-id="09ffb-169">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="09ffb-169">Property</span></span>       | <span data-ttu-id="09ffb-170">Type</span><span class="sxs-lookup"><span data-stu-id="09ffb-170">Type</span></span>   | <span data-ttu-id="09ffb-171">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="09ffb-171">Description</span></span>                              |
|----------------|--------|------------------------------------------|
| <span data-ttu-id="09ffb-172">primaryContact</span><span class="sxs-lookup"><span data-stu-id="09ffb-172">primaryContact</span></span> | [<span data-ttu-id="09ffb-173">Contact</span><span class="sxs-lookup"><span data-stu-id="09ffb-173">Contact</span></span>](./utility-resources.md#contact) | <span data-ttu-id="09ffb-174">Informatie over de gebruiker van de klantorganisatie die de Microsoft-klantovereenkomst heeft geaccepteerd, waaronder:  **firstName,** **lastName,** **email** en **phoneNumber** (optioneel)</span><span class="sxs-lookup"><span data-stu-id="09ffb-174">Information about the user from the customer organization who accepted the Microsoft Customer Agreement, including:  **firstName**, **lastName**, **email**, and **phoneNumber** (optional)</span></span> |
| <span data-ttu-id="09ffb-175">dateAgreed</span><span class="sxs-lookup"><span data-stu-id="09ffb-175">dateAgreed</span></span>     | <span data-ttu-id="09ffb-176">tekenreeks in UTC-datum/tijd-indeling</span><span class="sxs-lookup"><span data-stu-id="09ffb-176">string in UTC date time format</span></span> |<span data-ttu-id="09ffb-177">De datum waarop de klant de overeenkomst heeft geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="09ffb-177">The date when the customer accepted the agreement.</span></span> |
| <span data-ttu-id="09ffb-178">templateId</span><span class="sxs-lookup"><span data-stu-id="09ffb-178">templateId</span></span>     | <span data-ttu-id="09ffb-179">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="09ffb-179">string</span></span> | <span data-ttu-id="09ffb-180">De unieke id van het overeenkomsttype dat door de klant is geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="09ffb-180">Unique identifier of the agreement type accepted by the customer.</span></span> <span data-ttu-id="09ffb-181">U kunt de **templateId voor Microsoft-klantovereenkomst verkrijgen** door de metagegevens van de overeenkomst op te halen voor Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="09ffb-181">You can obtain the **templateId** for Microsoft Customer Agreement by retrieving the agreement metadata for Microsoft Customer Agreement.</span></span> <span data-ttu-id="09ffb-182">Zie [Metagegevens van overeenkomst Microsoft-klantovereenkomst](./get-customer-agreement-metadata.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="09ffb-182">See [Get agreement metadata for Microsoft Customer Agreement](./get-customer-agreement-metadata.md) for details.</span></span> |
| <span data-ttu-id="09ffb-183">type</span><span class="sxs-lookup"><span data-stu-id="09ffb-183">type</span></span>           | <span data-ttu-id="09ffb-184">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="09ffb-184">string</span></span> | <span data-ttu-id="09ffb-185">Overeenkomsttype dat door de klant is geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="09ffb-185">Agreement type accepted by the customer.</span></span> <span data-ttu-id="09ffb-186">Gebruik MicrosoftCustomerAgreement als de klant de Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="09ffb-186">Use "MicrosoftCustomerAgreement" if customer accepted the Microsoft Customer Agreement.</span></span> |

#### <a name="request-example"></a><span data-ttu-id="09ffb-187">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="09ffb-187">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="09ffb-188">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="09ffb-188">REST response</span></span>

<span data-ttu-id="09ffb-189">Als dit lukt, retourneert deze methode een [ **Agreement-resource**](./agreement-resources.md).</span><span class="sxs-lookup"><span data-stu-id="09ffb-189">If successful, this method returns an [**Agreement** resource](./agreement-resources.md).</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="09ffb-190">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="09ffb-190">Response success and error codes</span></span>

<span data-ttu-id="09ffb-191">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="09ffb-191">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="09ffb-192">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="09ffb-192">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="09ffb-193">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="09ffb-193">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

#### <a name="response-example"></a><span data-ttu-id="09ffb-194">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="09ffb-194">Response example</span></span>

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
