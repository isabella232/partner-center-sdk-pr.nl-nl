---
title: Bevestiging van acceptatie door de klant van Microsoft-klantovereenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u de acceptatie van klanten kunt bevestigen van de klant overeenkomst van micro soft.
ms.date: 09/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 55f63311e7bb1857fdc6c4b3d68446674542ba98
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767407"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-customer-agreement"></a><span data-ttu-id="e5d02-103">Bevestiging van acceptatie door de klant van Microsoft-klantovereenkomst ophalen</span><span class="sxs-lookup"><span data-stu-id="e5d02-103">Get confirmation of customer acceptance of Microsoft Customer Agreement</span></span>

<span data-ttu-id="e5d02-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="e5d02-104">**Applies to:**</span></span>

- <span data-ttu-id="e5d02-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e5d02-105">Partner Center</span></span>

<span data-ttu-id="e5d02-106">De **overeenkomst** resource wordt momenteel alleen ondersteund door het partner centrum in de *open bare cloud van micro soft*.</span><span class="sxs-lookup"><span data-stu-id="e5d02-106">The **Agreement** resource is currently supported by Partner Center only in the *Microsoft public cloud*.</span></span> <span data-ttu-id="e5d02-107">Deze resource is niet van toepassing op:</span><span class="sxs-lookup"><span data-stu-id="e5d02-107">This resource doesn't apply to:</span></span>

- <span data-ttu-id="e5d02-108">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="e5d02-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="e5d02-109">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="e5d02-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="e5d02-110">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e5d02-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e5d02-111">In dit artikel wordt uitgelegd hoe u bevestiging (en) kunt ophalen van de acceptatie van de klant overeenkomst van micro soft.</span><span class="sxs-lookup"><span data-stu-id="e5d02-111">This article explains how you can retrieve confirmation(s) of a customer's acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e5d02-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e5d02-112">Prerequisites</span></span>

- <span data-ttu-id="e5d02-113">Als u gebruikmaakt van de .NET SDK van partner Center, is versie 1,14 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="e5d02-113">If you are using the Partner Center .NET SDK, version 1.14 or newer is required.</span></span>

- <span data-ttu-id="e5d02-114">Referenties zoals beschreven in [Partner Center-verificatie](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e5d02-114">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="e5d02-115">Dit scenario ondersteunt alleen app + gebruikers verificatie.</span><span class="sxs-lookup"><span data-stu-id="e5d02-115">This scenario only supports App+User authentication.</span></span>

- <span data-ttu-id="e5d02-116">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e5d02-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e5d02-117">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="e5d02-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e5d02-118">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="e5d02-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e5d02-119">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="e5d02-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e5d02-120">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="e5d02-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e5d02-121">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e5d02-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="net"></a><span data-ttu-id="e5d02-122">.NET</span><span class="sxs-lookup"><span data-stu-id="e5d02-122">.NET</span></span>

<span data-ttu-id="e5d02-123">Bevestiging (en) van door de klant geaccepteerde acceptatie ophalen:</span><span class="sxs-lookup"><span data-stu-id="e5d02-123">To retrieve confirmation(s) of customer acceptance that was previously provided:</span></span>

- <span data-ttu-id="e5d02-124">Gebruik de verzameling **IAggregatePartner. Customers** en roep **ById** methode aan met de opgegeven klant-id.</span><span class="sxs-lookup"><span data-stu-id="e5d02-124">Use the **IAggregatePartner.Customers** collection and call **ById** method with the specified customer identifier.</span></span>

- <span data-ttu-id="e5d02-125">Haal de eigenschap **overeenkomsten** op en filter de resultaten met de klant overeenkomst van micro soft door de methode **ByAgreementType** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="e5d02-125">Fetch the **Agreements** property and filter the results to Microsoft Customer Agreement by calling **ByAgreementType** method.</span></span>

- <span data-ttu-id="e5d02-126">Roep **Get** -of **GetAsync** -methode aan.</span><span class="sxs-lookup"><span data-stu-id="e5d02-126">Call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCustomerAgreement";

var customerAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

<span data-ttu-id="e5d02-127">Een volledig voor beeld vindt u in de [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) -klasse in het [console test-app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) -project.</span><span class="sxs-lookup"><span data-stu-id="e5d02-127">A complete sample can be found in the [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="rest-request"></a><span data-ttu-id="e5d02-128">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e5d02-128">REST request</span></span>

<span data-ttu-id="e5d02-129">Bevestiging van acceptatie van klant ophalen die eerder is gegeven:</span><span class="sxs-lookup"><span data-stu-id="e5d02-129">To retrieve confirmation of customer acceptance that was previously provided:</span></span>

1. <span data-ttu-id="e5d02-130">Maak een REST-aanvraag om de verzameling [overeenkomsten](./agreement-resources.md) voor de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="e5d02-130">Create a REST request to retrieve the [Agreements](./agreement-resources.md) collection for the customer.</span></span>

2. <span data-ttu-id="e5d02-131">Gebruik de query parameter **Agreement type** om de resultaten te beperken tot alleen de micro soft-klant overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="e5d02-131">Use the **agreementType** query parameter to scope the results to only the Microsoft Customer Agreement.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e5d02-132">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e5d02-132">Request syntax</span></span>

<span data-ttu-id="e5d02-133">Gebruik de volgende aanvraag syntaxis:</span><span class="sxs-lookup"><span data-stu-id="e5d02-133">Use the following request syntax:</span></span>

| <span data-ttu-id="e5d02-134">Methode</span><span class="sxs-lookup"><span data-stu-id="e5d02-134">Method</span></span> | <span data-ttu-id="e5d02-135">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e5d02-135">Request URI</span></span>                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e5d02-136">GET</span><span class="sxs-lookup"><span data-stu-id="e5d02-136">GET</span></span>    | <span data-ttu-id="e5d02-137">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/agreements? Agreement type = {Agreement-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e5d02-137">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements?agreementType={agreement-type} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="e5d02-138">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="e5d02-138">URI parameters</span></span>

<span data-ttu-id="e5d02-139">U kunt de volgende URI-para meters met uw aanvraag gebruiken:</span><span class="sxs-lookup"><span data-stu-id="e5d02-139">You can use the following URI parameters with your request:</span></span>

| <span data-ttu-id="e5d02-140">Naam</span><span class="sxs-lookup"><span data-stu-id="e5d02-140">Name</span></span>             | <span data-ttu-id="e5d02-141">Type</span><span class="sxs-lookup"><span data-stu-id="e5d02-141">Type</span></span> | <span data-ttu-id="e5d02-142">Vereist</span><span class="sxs-lookup"><span data-stu-id="e5d02-142">Required</span></span> | <span data-ttu-id="e5d02-143">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e5d02-143">Description</span></span>                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| <span data-ttu-id="e5d02-144">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="e5d02-144">customer-tenant-id</span></span> | <span data-ttu-id="e5d02-145">GUID</span><span class="sxs-lookup"><span data-stu-id="e5d02-145">GUID</span></span> | <span data-ttu-id="e5d02-146">Yes</span><span class="sxs-lookup"><span data-stu-id="e5d02-146">Yes</span></span> | <span data-ttu-id="e5d02-147">De waarde is een GUID-indeling **CustomerTenantId** waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="e5d02-147">The value is a GUID formatted **CustomerTenantId** that allows you to specify a customer.</span></span> |
| <span data-ttu-id="e5d02-148">overeenkomst-type</span><span class="sxs-lookup"><span data-stu-id="e5d02-148">agreement-type</span></span> | <span data-ttu-id="e5d02-149">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e5d02-149">string</span></span> | <span data-ttu-id="e5d02-150">No</span><span class="sxs-lookup"><span data-stu-id="e5d02-150">No</span></span> | <span data-ttu-id="e5d02-151">Deze para meter retourneert alle meta gegevens van de overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="e5d02-151">This parameter returns all agreement metadata.</span></span> <span data-ttu-id="e5d02-152">Gebruik deze para meter om het query-antwoord op een specifiek overeenkomst type te bereiken.</span><span class="sxs-lookup"><span data-stu-id="e5d02-152">Use this parameter to scope the query response to specific agreement type.</span></span> <span data-ttu-id="e5d02-153">De ondersteunde waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="e5d02-153">The supported values are:</span></span> <br/><br/> <span data-ttu-id="e5d02-154">**MicrosoftCloudAgreement** die alleen de overeenkomst met de meta gegevens van het type *MicrosoftCloudAgreement* bevat.</span><span class="sxs-lookup"><span data-stu-id="e5d02-154">**MicrosoftCloudAgreement** that only includes agreement metadata of the type *MicrosoftCloudAgreement*.</span></span><br/><br/> <span data-ttu-id="e5d02-155">**MicrosoftCustomerAgreement** die alleen de overeenkomst met de meta gegevens van het type *MicrosoftCustomerAgreement* bevat.</span><span class="sxs-lookup"><span data-stu-id="e5d02-155">**MicrosoftCustomerAgreement** that only includes agreement metadata of the type *MicrosoftCustomerAgreement*.</span></span><br/><br/> <span data-ttu-id="e5d02-156">**\*** Hiermee worden alle meta gegevens van de overeenkomst geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e5d02-156">**\*** that returns all agreement metadata.</span></span> <span data-ttu-id="e5d02-157">(Gebruik **\*** alleen als uw code de benodigde logica heeft voor het afhandelen van onverwachte overeenkomst typen.)</span><span class="sxs-lookup"><span data-stu-id="e5d02-157">(Don't use **\*** unless your code has the necessary logic to handle unexpected agreement types.)</span></span><br/><br/> <span data-ttu-id="e5d02-158">**Opmerking:** Als de URI-para meter niet is opgegeven, wordt de query standaard ingesteld op **MicrosoftCloudAgreement** voor achterwaartse compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="e5d02-158">**Note:** If the URI parameter isn't specified, the query defaults to **MicrosoftCloudAgreement** for backward compatibility.</span></span> <span data-ttu-id="e5d02-159">Micro soft kan op elk moment overeenkomst meta gegevens introduceren met nieuwe overeenkomst typen.</span><span class="sxs-lookup"><span data-stu-id="e5d02-159">Microsoft may introduce agreement metadata with new agreement types at any time.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="e5d02-160">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e5d02-160">Request headers</span></span>

<span data-ttu-id="e5d02-161">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e5d02-161">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e5d02-162">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e5d02-162">Request body</span></span>

<span data-ttu-id="e5d02-163">Geen.</span><span class="sxs-lookup"><span data-stu-id="e5d02-163">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e5d02-164">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e5d02-164">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements?agreementType=MicrosoftCustomerAgreement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="e5d02-165">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e5d02-165">REST response</span></span>

<span data-ttu-id="e5d02-166">Als dit lukt, retourneert deze methode een verzameling **overeenkomst** resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="e5d02-166">If successful, this method returns a collection of **Agreement** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e5d02-167">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="e5d02-167">Response success and error codes</span></span>

<span data-ttu-id="e5d02-168">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="e5d02-168">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="e5d02-169">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e5d02-169">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e5d02-170">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="e5d02-170">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e5d02-171">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e5d02-171">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 620
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "totalCount": 2,
    "items":
    [
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@example.com"
                "phoneNumber":"1234567890"
            },
            "templateId":"117a77b0-9360-443b-8795-c6dedc750cf9",
            "dateAgreed":"2019-08-26T00:00:00",
            "type":"MicrosoftCustomerAgreement",
            "agreementLink":"https://aka.ms/customeragreement"
        },
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@example.com"
                "phoneNumber:"1234567890"
            },
            "templateId":"117a77b0-9360-443b-8795-c6dedc750cf9",
            "dateAgreed":"2019-08-27T00:00:00",
            "type":"MicrosoftCustomerAgreement",
            "agreementLink":"https://aka.ms/customeragreement"
        }
    ]
}
```
