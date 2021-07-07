---
title: Metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u metagegevens van een overeenkomst voor Microsoft-klantovereenkomst.
ms.date: 8/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khakiali
ms.author: alikhaki
ms.openlocfilehash: 5c20b317edf16b159050884070683880cf7e45bb
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025714"
---
# <a name="get-agreement-metadata-for-the-microsoft-customer-agreement"></a><span data-ttu-id="466f7-103">Metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst ophalen</span><span class="sxs-lookup"><span data-stu-id="466f7-103">Get agreement metadata for the Microsoft Customer Agreement</span></span>

<span data-ttu-id="466f7-104">**Van toepassing op**: Partner Center</span><span class="sxs-lookup"><span data-stu-id="466f7-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="466f7-105">**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="466f7-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="466f7-106">Metagegevens van overeenkomst voor Microsoft-klantovereenkomst worden momenteel ondersteund door Partner Center alleen in de openbare Cloud van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="466f7-106">Agreement metadata for Microsoft Customer Agreement is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="466f7-107">U moet de metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst voordat u het volgende kunt doen:</span><span class="sxs-lookup"><span data-stu-id="466f7-107">You must retrieve the agreement metadata for the Microsoft Customer Agreement before you can:</span></span>

- [<span data-ttu-id="466f7-108">Bevestig dat een klant de Microsoft-klantovereenkomst</span><span class="sxs-lookup"><span data-stu-id="466f7-108">Confirm a customer's acceptance of the Microsoft Customer Agreement</span></span>](./confirm-customer-consent-customer-agreement.md)
- [<span data-ttu-id="466f7-109">Een downloadkoppeling ophalen voor de Microsoft-klantovereenkomst sjabloon</span><span class="sxs-lookup"><span data-stu-id="466f7-109">Retrieve a download link for the Microsoft Customer Agreement template</span></span>](./download-customer-agreement-template.md)

## <a name="prerequisites"></a><span data-ttu-id="466f7-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="466f7-110">Prerequisites</span></span>

- <span data-ttu-id="466f7-111">Als u de .NET SDK Partner Center, is versie 1.14 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="466f7-111">If you are using the Partner Center .NET SDK, version 1.14 or newer is required.</span></span>

- <span data-ttu-id="466f7-112">Referenties zoals beschreven in [Partner Center verificatie](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="466f7-112">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="466f7-113">Dit scenario biedt alleen ondersteuning voor app- en gebruikersverificatie.</span><span class="sxs-lookup"><span data-stu-id="466f7-113">This scenario supports App+User authentication only.</span></span>

## <a name="net-version-114-or-newer"></a><span data-ttu-id="466f7-114">.NET (versie 1.14 of nieuwer)</span><span class="sxs-lookup"><span data-stu-id="466f7-114">.NET (version 1.14 or newer)</span></span>

<span data-ttu-id="466f7-115">De metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst:</span><span class="sxs-lookup"><span data-stu-id="466f7-115">To retrieve the agreement metadata for Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="466f7-116">Haal eerst de **verzameling IAggregatePartner.AgreementDetails** op.</span><span class="sxs-lookup"><span data-stu-id="466f7-116">First, retrieve the **IAggregatePartner.AgreementDetails** collection.</span></span>

2. <span data-ttu-id="466f7-117">Roep **de methode ByAgreementType aan** om de verzameling te filteren op Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="466f7-117">Call **ByAgreementType** method to filter the collection to Microsoft Customer Agreement.</span></span>

3. <span data-ttu-id="466f7-118">Roep ten slotte **de methode Get** of **GetAsync aan.**</span><span class="sxs-lookup"><span data-stu-id="466f7-118">Finally, call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCustomerAgreement";

var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

<span data-ttu-id="466f7-119">Een volledig voorbeeld vindt u in de [klasse GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) van het [consoletest-app-project.](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples)</span><span class="sxs-lookup"><span data-stu-id="466f7-119">A complete sample can be found in the [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="rest-request"></a><span data-ttu-id="466f7-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="466f7-120">REST request</span></span>

<span data-ttu-id="466f7-121">De metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst:</span><span class="sxs-lookup"><span data-stu-id="466f7-121">To retrieve the agreement metadata for Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="466f7-122">Maak een REST-aanvraag om de [verzameling AgreementMetaData op te](./agreement-metadata-resources.md) halen.</span><span class="sxs-lookup"><span data-stu-id="466f7-122">Create a REST request to retrieve the [AgreementMetaData](./agreement-metadata-resources.md) collection.</span></span>

2. <span data-ttu-id="466f7-123">Gebruik de **queryparameter agreementType** om het bereik van het resultaat alleen te Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="466f7-123">Use the **agreementType** query parameter to scope the result to only the Microsoft Customer Agreement.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="466f7-124">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="466f7-124">Request syntax</span></span>

| <span data-ttu-id="466f7-125">Methode</span><span class="sxs-lookup"><span data-stu-id="466f7-125">Method</span></span> | <span data-ttu-id="466f7-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="466f7-126">Request URI</span></span>                                                         |
|--------|---------------------------------------------------------------------|
| <span data-ttu-id="466f7-127">GET</span><span class="sxs-lookup"><span data-stu-id="466f7-127">GET</span></span>    | <span data-ttu-id="466f7-128">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/agreements?agreementType={agreement-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="466f7-128">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/agreements?agreementType={agreement-type} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="466f7-129">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="466f7-129">URI parameters</span></span>

| <span data-ttu-id="466f7-130">Naam</span><span class="sxs-lookup"><span data-stu-id="466f7-130">Name</span></span>                   | <span data-ttu-id="466f7-131">Type</span><span class="sxs-lookup"><span data-stu-id="466f7-131">Type</span></span>     | <span data-ttu-id="466f7-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="466f7-132">Required</span></span> | <span data-ttu-id="466f7-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="466f7-133">Description</span></span>                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| <span data-ttu-id="466f7-134">agreement-type</span><span class="sxs-lookup"><span data-stu-id="466f7-134">agreement-type</span></span> | <span data-ttu-id="466f7-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="466f7-135">string</span></span> | <span data-ttu-id="466f7-136">No</span><span class="sxs-lookup"><span data-stu-id="466f7-136">No</span></span> | <span data-ttu-id="466f7-137">Gebruik deze parameter om het bereik van de queryreactie te wijzigen in een specifiek overeenkomsttype.</span><span class="sxs-lookup"><span data-stu-id="466f7-137">Use this parameter to scope the query response to specific agreement type.</span></span> <span data-ttu-id="466f7-138">De ondersteunde waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="466f7-138">The supported values are:</span></span> <br/><br/><span data-ttu-id="466f7-139">**MicrosoftCloudAgreement dat** alleen metagegevens van overeenkomst bevat van het type *MicrosoftCloudAgreement*</span><span class="sxs-lookup"><span data-stu-id="466f7-139">**MicrosoftCloudAgreement** that includes agreement metadata only of the type *MicrosoftCloudAgreement*</span></span><br/><br/><span data-ttu-id="466f7-140">**MicrosoftCustomerAgreement** dat alleen metagegevens van overeenkomst bevat van het type *MicrosoftCustomerAgreement*.</span><span class="sxs-lookup"><span data-stu-id="466f7-140">**MicrosoftCustomerAgreement** that includes agreement metadata only of the type *MicrosoftCustomerAgreement*.</span></span><br/><br/><span data-ttu-id="466f7-141">**\**_ die alle metagegevens van de overeenkomst retourneert. (Gebruik niet _\* \* \*_ tenzij uw code de benodigde runtimelogica heeft om onbekende typen overeenkomst af te handelen, omdat Microsoft op elk moment metagegevens van overeenkomst met nieuwe typen overeenkomst kan introduceren.) <br/> <br/> _\* Opmerking:*\* als de URI-parameter niet is opgegeven, wordt de query standaard ingesteld op **MicrosoftCloudAgreement** voor compatibiliteit met eerdere compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="466f7-141">**\**_ that returns all agreement metadata. (Don't use _*\**_ unless your code has the necessary runtime logic to handle unfamiliar agreement types because Microsoft may introduce agreement metadata with new agreement types at any time.)<br/><br/> _\* Note:*\* If the URI parameter isn't specified, the query defaults to **MicrosoftCloudAgreement** for backward compatibility.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="466f7-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="466f7-142">Request headers</span></span>

<span data-ttu-id="466f7-143">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="466f7-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="466f7-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="466f7-144">Request body</span></span>

<span data-ttu-id="466f7-145">Geen.</span><span class="sxs-lookup"><span data-stu-id="466f7-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="466f7-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="466f7-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/agreements?agreementType=MicrosoftCustomerAgreement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="466f7-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="466f7-147">REST response</span></span>

<span data-ttu-id="466f7-148">Als dit lukt, retourneert deze methode een verzameling [ **AgreementMetaData-resources**](./agreement-metadata-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="466f7-148">If successful, this method returns a collection of [**AgreementMetaData** resources](./agreement-metadata-resources.md) in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="466f7-149">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="466f7-149">Response success and error codes</span></span>

<span data-ttu-id="466f7-150">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="466f7-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="466f7-151">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="466f7-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="466f7-152">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="466f7-152">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="466f7-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="466f7-153">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 620
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "totalCount": 1,
    "items": [
        {
            "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
            "agreementType": "MicrosoftCustomerAgreement",
            "agreementLink": "https://aka.ms/customeragreement",
            "versionRank": 0
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
