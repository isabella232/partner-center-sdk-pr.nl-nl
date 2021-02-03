---
title: Metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u de meta gegevens van de overeenkomst voor micro soft-klanten overeenkomst kunt ophalen.
ms.date: 8/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khakiali
ms.author: alikhaki
ms.openlocfilehash: c3ebecc51859c9d2240d319d823f7e555eaecc27
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767405"
---
# <a name="get-agreement-metadata-for-the-microsoft-customer-agreement"></a><span data-ttu-id="12cc8-103">Metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst ophalen</span><span class="sxs-lookup"><span data-stu-id="12cc8-103">Get agreement metadata for the Microsoft Customer Agreement</span></span>

<span data-ttu-id="12cc8-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="12cc8-104">**Applies to:**</span></span>

- <span data-ttu-id="12cc8-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="12cc8-105">Partner Center</span></span>

<span data-ttu-id="12cc8-106">De meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst worden momenteel alleen ondersteund door het partner centrum in de *open bare cloud van micro soft*.</span><span class="sxs-lookup"><span data-stu-id="12cc8-106">Agreement metadata for Microsoft Customer Agreement is currently supported by Partner Center only in the *Microsoft public cloud*.</span></span> <span data-ttu-id="12cc8-107">Het is niet van toepassing op:</span><span class="sxs-lookup"><span data-stu-id="12cc8-107">It doesn't apply to:</span></span>

- <span data-ttu-id="12cc8-108">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="12cc8-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="12cc8-109">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="12cc8-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="12cc8-110">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="12cc8-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="12cc8-111">U moet de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst ophalen voordat u het volgende kunt doen:</span><span class="sxs-lookup"><span data-stu-id="12cc8-111">You must retrieve the agreement metadata for the Microsoft Customer Agreement before you can:</span></span>

- [<span data-ttu-id="12cc8-112">Bevestig de acceptatie van de micro soft-klant overeenkomst door de klant</span><span class="sxs-lookup"><span data-stu-id="12cc8-112">Confirm a customer's acceptance of the Microsoft Customer Agreement</span></span>](./confirm-customer-consent-customer-agreement.md)
- [<span data-ttu-id="12cc8-113">Een download koppeling voor de micro soft-sjabloon voor klant overeenkomsten ophalen</span><span class="sxs-lookup"><span data-stu-id="12cc8-113">Retrieve a download link for the Microsoft Customer Agreement template</span></span>](./download-customer-agreement-template.md)

## <a name="prerequisites"></a><span data-ttu-id="12cc8-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="12cc8-114">Prerequisites</span></span>

- <span data-ttu-id="12cc8-115">Als u gebruikmaakt van de .NET SDK van partner Center, is versie 1,14 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="12cc8-115">If you are using the Partner Center .NET SDK, version 1.14 or newer is required.</span></span>

- <span data-ttu-id="12cc8-116">Referenties zoals beschreven in [Partner Center-verificatie](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="12cc8-116">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="12cc8-117">Dit scenario ondersteunt alleen app + gebruikers authenticatie.</span><span class="sxs-lookup"><span data-stu-id="12cc8-117">This scenario supports App+User authentication only.</span></span>

## <a name="net-version-114-or-newer"></a><span data-ttu-id="12cc8-118">.NET (versie 1,14 of nieuwer)</span><span class="sxs-lookup"><span data-stu-id="12cc8-118">.NET (version 1.14 or newer)</span></span>

<span data-ttu-id="12cc8-119">De meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst ophalen:</span><span class="sxs-lookup"><span data-stu-id="12cc8-119">To retrieve the agreement metadata for Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="12cc8-120">Haal eerst de verzameling **IAggregatePartner. AgreementDetails** op.</span><span class="sxs-lookup"><span data-stu-id="12cc8-120">First, retrieve the **IAggregatePartner.AgreementDetails** collection.</span></span>

2. <span data-ttu-id="12cc8-121">Roep **ByAgreementType** -methode aan om de verzameling te filteren op de micro soft-klant overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="12cc8-121">Call **ByAgreementType** method to filter the collection to Microsoft Customer Agreement.</span></span>

3. <span data-ttu-id="12cc8-122">Tot slot roept u de methode Get of **GetAsync** **aan** .</span><span class="sxs-lookup"><span data-stu-id="12cc8-122">Finally, call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCustomerAgreement";

var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

<span data-ttu-id="12cc8-123">Een volledig voor beeld vindt u in de [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) -klasse in het [console test-app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) -project.</span><span class="sxs-lookup"><span data-stu-id="12cc8-123">A complete sample can be found in the [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="rest-request"></a><span data-ttu-id="12cc8-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="12cc8-124">REST request</span></span>

<span data-ttu-id="12cc8-125">De meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst ophalen:</span><span class="sxs-lookup"><span data-stu-id="12cc8-125">To retrieve the agreement metadata for Microsoft Customer Agreement:</span></span>

1. <span data-ttu-id="12cc8-126">Maak een REST-aanvraag om de [AgreementMetaData](./agreement-metadata-resources.md) -verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="12cc8-126">Create a REST request to retrieve the [AgreementMetaData](./agreement-metadata-resources.md) collection.</span></span>

2. <span data-ttu-id="12cc8-127">Gebruik de **Agreement type** -query parameter om het resultaat te beperken tot alleen de micro soft-klant overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="12cc8-127">Use the **agreementType** query parameter to scope the result to only the Microsoft Customer Agreement.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="12cc8-128">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="12cc8-128">Request syntax</span></span>

| <span data-ttu-id="12cc8-129">Methode</span><span class="sxs-lookup"><span data-stu-id="12cc8-129">Method</span></span> | <span data-ttu-id="12cc8-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="12cc8-130">Request URI</span></span>                                                         |
|--------|---------------------------------------------------------------------|
| <span data-ttu-id="12cc8-131">GET</span><span class="sxs-lookup"><span data-stu-id="12cc8-131">GET</span></span>    | <span data-ttu-id="12cc8-132">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/agreements? Agreement type = {Agreement-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="12cc8-132">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/agreements?agreementType={agreement-type} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="12cc8-133">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="12cc8-133">URI parameters</span></span>

| <span data-ttu-id="12cc8-134">Naam</span><span class="sxs-lookup"><span data-stu-id="12cc8-134">Name</span></span>                   | <span data-ttu-id="12cc8-135">Type</span><span class="sxs-lookup"><span data-stu-id="12cc8-135">Type</span></span>     | <span data-ttu-id="12cc8-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="12cc8-136">Required</span></span> | <span data-ttu-id="12cc8-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="12cc8-137">Description</span></span>                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| <span data-ttu-id="12cc8-138">overeenkomst-type</span><span class="sxs-lookup"><span data-stu-id="12cc8-138">agreement-type</span></span> | <span data-ttu-id="12cc8-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="12cc8-139">string</span></span> | <span data-ttu-id="12cc8-140">No</span><span class="sxs-lookup"><span data-stu-id="12cc8-140">No</span></span> | <span data-ttu-id="12cc8-141">Gebruik deze para meter om het query-antwoord op een specifiek overeenkomst type te bereiken.</span><span class="sxs-lookup"><span data-stu-id="12cc8-141">Use this parameter to scope the query response to specific agreement type.</span></span> <span data-ttu-id="12cc8-142">De ondersteunde waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="12cc8-142">The supported values are:</span></span> <br/><br/><span data-ttu-id="12cc8-143">**MicrosoftCloudAgreement** die alleen overeenkomst meta gegevens van het type *MicrosoftCloudAgreement* bevat</span><span class="sxs-lookup"><span data-stu-id="12cc8-143">**MicrosoftCloudAgreement** that includes agreement metadata only of the type *MicrosoftCloudAgreement*</span></span><br/><br/><span data-ttu-id="12cc8-144">**MicrosoftCustomerAgreement** die alleen overeenkomst met de meta gegevens van het type *MicrosoftCustomerAgreement* bevat.</span><span class="sxs-lookup"><span data-stu-id="12cc8-144">**MicrosoftCustomerAgreement** that includes agreement metadata only of the type *MicrosoftCustomerAgreement*.</span></span><br/><br/><span data-ttu-id="12cc8-145">**\*** Hiermee worden alle meta gegevens van de overeenkomst geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="12cc8-145">**\*** that returns all agreement metadata.</span></span> <span data-ttu-id="12cc8-146">(Alleen gebruiken **\*** als uw code de nood zakelijke runtime logica heeft voor het verwerken van onbekende overeenkomst typen, omdat micro soft op elk moment overeenkomst meta gegevens kan introduceren met nieuwe overeenkomst typen.)</span><span class="sxs-lookup"><span data-stu-id="12cc8-146">(Don't use **\*** unless your code has the necessary runtime logic to handle unfamiliar agreement types because Microsoft may introduce agreement metadata with new agreement types at any time.)</span></span><br/><br/> <span data-ttu-id="12cc8-147">**Opmerking:** Als de URI-para meter niet is opgegeven, wordt de query standaard ingesteld op **MicrosoftCloudAgreement** voor achterwaartse compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="12cc8-147">**Note:** If the URI parameter isn't specified, the query defaults to **MicrosoftCloudAgreement** for backward compatibility.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="12cc8-148">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="12cc8-148">Request headers</span></span>

<span data-ttu-id="12cc8-149">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="12cc8-149">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="12cc8-150">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="12cc8-150">Request body</span></span>

<span data-ttu-id="12cc8-151">Geen.</span><span class="sxs-lookup"><span data-stu-id="12cc8-151">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="12cc8-152">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="12cc8-152">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/agreements?agreementType=MicrosoftCustomerAgreement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="12cc8-153">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="12cc8-153">REST response</span></span>

<span data-ttu-id="12cc8-154">Als dit lukt, retourneert deze methode een verzameling [ **AgreementMetaData** -resources](./agreement-metadata-resources.md) in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="12cc8-154">If successful, this method returns a collection of [**AgreementMetaData** resources](./agreement-metadata-resources.md) in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="12cc8-155">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="12cc8-155">Response success and error codes</span></span>

<span data-ttu-id="12cc8-156">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="12cc8-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="12cc8-157">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="12cc8-157">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="12cc8-158">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="12cc8-158">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="12cc8-159">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="12cc8-159">Response example</span></span>

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
