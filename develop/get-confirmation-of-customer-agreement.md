---
title: Bevestiging van acceptatie door de klant van Microsoft-klantovereenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u de klantacceptatie van de Microsoft-klantovereenkomst.
ms.date: 09/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 3668a5e510effb533cade311f52513b9a81d40af
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760535"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-customer-agreement"></a><span data-ttu-id="e244d-103">Bevestiging van acceptatie door de klant van Microsoft-klantovereenkomst ophalen</span><span class="sxs-lookup"><span data-stu-id="e244d-103">Get confirmation of customer acceptance of Microsoft Customer Agreement</span></span>

<span data-ttu-id="e244d-104">**Van toepassing op**: Partner Center</span><span class="sxs-lookup"><span data-stu-id="e244d-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="e244d-105">**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e244d-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e244d-106">De **overeenkomstresource** wordt momenteel alleen ondersteund door Partner Center in de openbare cloud van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e244d-106">The **Agreement** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="e244d-107">In dit artikel wordt uitgelegd hoe u bevestiging(en) kunt ophalen van de acceptatie van de Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="e244d-107">This article explains how you can retrieve confirmation(s) of a customer's acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e244d-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e244d-108">Prerequisites</span></span>

- <span data-ttu-id="e244d-109">Als u de .NET SDK Partner Center, is versie 1.14 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="e244d-109">If you are using the Partner Center .NET SDK, version 1.14 or newer is required.</span></span>

- <span data-ttu-id="e244d-110">Referenties zoals beschreven in [Partner Center verificatie](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e244d-110">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="e244d-111">Dit scenario ondersteunt alleen App+Gebruikersverificatie.</span><span class="sxs-lookup"><span data-stu-id="e244d-111">This scenario only supports App+User authentication.</span></span>

- <span data-ttu-id="e244d-112">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e244d-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e244d-113">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="e244d-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e244d-114">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="e244d-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e244d-115">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="e244d-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e244d-116">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="e244d-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e244d-117">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e244d-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="net"></a><span data-ttu-id="e244d-118">.NET</span><span class="sxs-lookup"><span data-stu-id="e244d-118">.NET</span></span>

<span data-ttu-id="e244d-119">Bevestiging(en) van eerder opgegeven klantacceptatie ophalen:</span><span class="sxs-lookup"><span data-stu-id="e244d-119">To retrieve confirmation(s) of customer acceptance that was previously provided:</span></span>

- <span data-ttu-id="e244d-120">Gebruik de **verzameling IAggregatePartner.Customers** en roep de **ById-methode** aan met de opgegeven klant-id.</span><span class="sxs-lookup"><span data-stu-id="e244d-120">Use the **IAggregatePartner.Customers** collection and call **ById** method with the specified customer identifier.</span></span>

- <span data-ttu-id="e244d-121">Haal de **eigenschap Agreements** op en filter de resultaten naar Microsoft-klantovereenkomst **byAgreementType-methode aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="e244d-121">Fetch the **Agreements** property and filter the results to Microsoft Customer Agreement by calling **ByAgreementType** method.</span></span>

- <span data-ttu-id="e244d-122">Roep **de methode Get** of **GetAsync aan.**</span><span class="sxs-lookup"><span data-stu-id="e244d-122">Call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCustomerAgreement";

var customerAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

<span data-ttu-id="e244d-123">Een volledig voorbeeld vindt u in de [klasse GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) van het [consoletest-app-project.](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples)</span><span class="sxs-lookup"><span data-stu-id="e244d-123">A complete sample can be found in the [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="rest-request"></a><span data-ttu-id="e244d-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e244d-124">REST request</span></span>

<span data-ttu-id="e244d-125">Om bevestiging op te halen van de klantacceptatie die eerder is opgegeven:</span><span class="sxs-lookup"><span data-stu-id="e244d-125">To retrieve confirmation of customer acceptance that was previously provided:</span></span>

1. <span data-ttu-id="e244d-126">Maak een REST-aanvraag om de verzameling [Overeenkomsten voor](./agreement-resources.md) de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="e244d-126">Create a REST request to retrieve the [Agreements](./agreement-resources.md) collection for the customer.</span></span>

2. <span data-ttu-id="e244d-127">Gebruik de **queryparameter agreementType** om de resultaten alleen te Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="e244d-127">Use the **agreementType** query parameter to scope the results to only the Microsoft Customer Agreement.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e244d-128">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e244d-128">Request syntax</span></span>

<span data-ttu-id="e244d-129">Gebruik de volgende aanvraagsyntaxis:</span><span class="sxs-lookup"><span data-stu-id="e244d-129">Use the following request syntax:</span></span>

| <span data-ttu-id="e244d-130">Methode</span><span class="sxs-lookup"><span data-stu-id="e244d-130">Method</span></span> | <span data-ttu-id="e244d-131">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e244d-131">Request URI</span></span>                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e244d-132">GET</span><span class="sxs-lookup"><span data-stu-id="e244d-132">GET</span></span>    | <span data-ttu-id="e244d-133">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements?agreementType={agreement-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e244d-133">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements?agreementType={agreement-type} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="e244d-134">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="e244d-134">URI parameters</span></span>

<span data-ttu-id="e244d-135">U kunt de volgende URI-parameters gebruiken bij uw aanvraag:</span><span class="sxs-lookup"><span data-stu-id="e244d-135">You can use the following URI parameters with your request:</span></span>

| <span data-ttu-id="e244d-136">Naam</span><span class="sxs-lookup"><span data-stu-id="e244d-136">Name</span></span>             | <span data-ttu-id="e244d-137">Type</span><span class="sxs-lookup"><span data-stu-id="e244d-137">Type</span></span> | <span data-ttu-id="e244d-138">Vereist</span><span class="sxs-lookup"><span data-stu-id="e244d-138">Required</span></span> | <span data-ttu-id="e244d-139">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e244d-139">Description</span></span>                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| <span data-ttu-id="e244d-140">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="e244d-140">customer-tenant-id</span></span> | <span data-ttu-id="e244d-141">GUID</span><span class="sxs-lookup"><span data-stu-id="e244d-141">GUID</span></span> | <span data-ttu-id="e244d-142">Ja</span><span class="sxs-lookup"><span data-stu-id="e244d-142">Yes</span></span> | <span data-ttu-id="e244d-143">De waarde is een **CustomerTenantId** met GUID-indeling waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="e244d-143">The value is a GUID formatted **CustomerTenantId** that allows you to specify a customer.</span></span> |
| <span data-ttu-id="e244d-144">agreement-type</span><span class="sxs-lookup"><span data-stu-id="e244d-144">agreement-type</span></span> | <span data-ttu-id="e244d-145">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e244d-145">string</span></span> | <span data-ttu-id="e244d-146">No</span><span class="sxs-lookup"><span data-stu-id="e244d-146">No</span></span> | <span data-ttu-id="e244d-147">Deze parameter retourneert alle metagegevens van de overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="e244d-147">This parameter returns all agreement metadata.</span></span> <span data-ttu-id="e244d-148">Gebruik deze parameter om het bereik van de queryreactie te wijzigen in een specifiek overeenkomsttype.</span><span class="sxs-lookup"><span data-stu-id="e244d-148">Use this parameter to scope the query response to specific agreement type.</span></span> <span data-ttu-id="e244d-149">De ondersteunde waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="e244d-149">The supported values are:</span></span> <br/><br/> <span data-ttu-id="e244d-150">**MicrosoftCloudAgreement dat** alleen metagegevens van overeenkomst bevat van het type *MicrosoftCloudAgreement*.</span><span class="sxs-lookup"><span data-stu-id="e244d-150">**MicrosoftCloudAgreement** that only includes agreement metadata of the type *MicrosoftCloudAgreement*.</span></span><br/><br/> <span data-ttu-id="e244d-151">**MicrosoftCustomerAgreement dat** alleen metagegevens van overeenkomst bevat van het type *MicrosoftCustomerAgreement*.</span><span class="sxs-lookup"><span data-stu-id="e244d-151">**MicrosoftCustomerAgreement** that only includes agreement metadata of the type *MicrosoftCustomerAgreement*.</span></span><br/><br/> <span data-ttu-id="e244d-152">**\**_ die alle metagegevens van de overeenkomst retourneert. (Gebruik niet _\* \* \*_ tenzij uw code de benodigde logica heeft om onverwachte typen overeenkomst af te handelen.) <br/> <br/> _\* Opmerking:*\* als de URI-parameter niet is opgegeven, wordt de query standaard ingesteld op **MicrosoftCloudAgreement** voor achterwaartse compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="e244d-152">**\**_ that returns all agreement metadata. (Don't use _*\**_ unless your code has the necessary logic to handle unexpected agreement types.)<br/><br/> _\* Note:*\* If the URI parameter isn't specified, the query defaults to **MicrosoftCloudAgreement** for backward compatibility.</span></span> <span data-ttu-id="e244d-153">Microsoft kan op elk moment metagegevens van overeenkomst met nieuwe typen overeenkomst introduceren.</span><span class="sxs-lookup"><span data-stu-id="e244d-153">Microsoft may introduce agreement metadata with new agreement types at any time.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="e244d-154">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e244d-154">Request headers</span></span>

<span data-ttu-id="e244d-155">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e244d-155">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e244d-156">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e244d-156">Request body</span></span>

<span data-ttu-id="e244d-157">Geen.</span><span class="sxs-lookup"><span data-stu-id="e244d-157">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e244d-158">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e244d-158">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements?agreementType=MicrosoftCustomerAgreement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="e244d-159">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e244d-159">REST response</span></span>

<span data-ttu-id="e244d-160">Als dit lukt, retourneert deze methode een verzameling **overeenkomstresources** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="e244d-160">If successful, this method returns a collection of **Agreement** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e244d-161">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e244d-161">Response success and error codes</span></span>

<span data-ttu-id="e244d-162">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e244d-162">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="e244d-163">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e244d-163">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e244d-164">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="e244d-164">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e244d-165">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e244d-165">Response example</span></span>

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
