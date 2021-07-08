---
title: Metagegevens van de overeenkomst voor Microsoft Cloud-overeenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u metagegevens van een overeenkomst voor Microsoft Cloud-overeenkomst.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 2588327e72a13de75eb9e02675edbd535491adc4
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760790"
---
# <a name="get-agreement-metadata-for-microsoft-cloud-agreement"></a><span data-ttu-id="da2e9-103">Metagegevens van de overeenkomst voor Microsoft Cloud-overeenkomst ophalen</span><span class="sxs-lookup"><span data-stu-id="da2e9-103">Get agreement metadata for Microsoft Cloud Agreement</span></span>

<span data-ttu-id="da2e9-104">**Van toepassing op**: Partner Center</span><span class="sxs-lookup"><span data-stu-id="da2e9-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="da2e9-105">**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="da2e9-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="da2e9-106">De **AgreementMetaData-resource** wordt momenteel alleen ondersteund door Partner Center in de openbare cloud van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="da2e9-106">The **AgreementMetaData** resource is currently supported by Partner Center in the Microsoft public cloud only.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="da2e9-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="da2e9-107">Prerequisites</span></span>

- <span data-ttu-id="da2e9-108">Als u de .NET SDK Partner Center, is versie 1.9 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="da2e9-108">If you are using the Partner Center .NET SDK, version 1.9 or newer is required.</span></span>

- <span data-ttu-id="da2e9-109">Als u de Java SDK Partner Center, is versie 1.8 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="da2e9-109">If you are using the Partner Center Java SDK, version 1.8 or newer is required.</span></span>

- <span data-ttu-id="da2e9-110">Referenties zoals beschreven in [Partner Center verificatie](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="da2e9-110">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="da2e9-111">Dit scenario biedt ondersteuning voor app- en gebruikersverificatie.</span><span class="sxs-lookup"><span data-stu-id="da2e9-111">This scenario supports app + user authentication.</span></span>

## <a name="net-version-114-or-newer"></a><span data-ttu-id="da2e9-112">.NET (versie 1.14 of nieuwer)</span><span class="sxs-lookup"><span data-stu-id="da2e9-112">.NET (version 1.14 or newer)</span></span>

<span data-ttu-id="da2e9-113">De metagegevens van de overeenkomst voor de Microsoft Cloud-overeenkomst:</span><span class="sxs-lookup"><span data-stu-id="da2e9-113">To retrieve the agreement metadata for Microsoft Cloud Agreement:</span></span>

1. <span data-ttu-id="da2e9-114">Haal eerst de **verzameling IAggregatePartner.AgreementDetails** op.</span><span class="sxs-lookup"><span data-stu-id="da2e9-114">First, retrieve the **IAggregatePartner.AgreementDetails** collection.</span></span>

2. <span data-ttu-id="da2e9-115">Roep **de methode ByAgreementType aan** om de verzameling te filteren op Microsoft Cloud-overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="da2e9-115">Call **ByAgreementType** method to filter the collection to Microsoft Cloud Agreement.</span></span>

3. <span data-ttu-id="da2e9-116">Roep ten slotte **de methode Get** of **GetAsync aan.**</span><span class="sxs-lookup"><span data-stu-id="da2e9-116">Finally, call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCloudAgreement";

var microsoftCloudAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

<span data-ttu-id="da2e9-117">Een volledig voorbeeld vindt u in de [klasse GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) van het [consoletest-app-project.](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples)</span><span class="sxs-lookup"><span data-stu-id="da2e9-117">A complete sample can be found in the [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="net-version-19---113"></a><span data-ttu-id="da2e9-118">.NET (versie 1.9 - 1.13)</span><span class="sxs-lookup"><span data-stu-id="da2e9-118">.NET (version 1.9 - 1.13)</span></span>

<span data-ttu-id="da2e9-119">De metagegevens van de overeenkomst voor de Microsoft Cloud-overeenkomst:</span><span class="sxs-lookup"><span data-stu-id="da2e9-119">To retrieve agreement metadata for the Microsoft Cloud Agreement:</span></span>

<span data-ttu-id="da2e9-120">Haal eerst de **verzameling IAggregatePartner.AgreementDetails** op en roep vervolgens de **methoden Get** of **GetAsync aan.**</span><span class="sxs-lookup"><span data-stu-id="da2e9-120">First retrieve the **IAggregatePartner.AgreementDetails** collection and then call the **Get** or **GetAsync** methods.</span></span> <span data-ttu-id="da2e9-121">Zoek vervolgens naar het item in de verzameling, dat overeenkomt met de Microsoft Cloud-overeenkomst:</span><span class="sxs-lookup"><span data-stu-id="da2e9-121">Then search for the item within the collection, which corresponds to the Microsoft Cloud Agreement:</span></span>

```csharp
// IAggregatePartner partnerOperations;

var agreements = partnerOperations.AgreementDetails.Get();

AgreementMetaData microsoftCloudAgreement = agreements.Items.FirstOrDefault (agr => agr.AgreementType == AgreementType.MicrosoftCloudAgreement);
```

## <a name="java"></a><span data-ttu-id="da2e9-122">Java</span><span class="sxs-lookup"><span data-stu-id="da2e9-122">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="da2e9-123">De metagegevens van de overeenkomst voor de Microsoft Cloud-overeenkomst:</span><span class="sxs-lookup"><span data-stu-id="da2e9-123">To retrieve agreement metadata for the Microsoft Cloud Agreement:</span></span>

<span data-ttu-id="da2e9-124">Roep eerst de **functie IAggregatePartner.getAgreementDetails** aan en roep vervolgens de **functie get** aan.</span><span class="sxs-lookup"><span data-stu-id="da2e9-124">First call the **IAggregatePartner.getAgreementDetails** function and then call the **get** function.</span></span> <span data-ttu-id="da2e9-125">Zoek vervolgens naar het item in de verzameling, dat overeenkomt met de Microsoft Cloud-overeenkomst:</span><span class="sxs-lookup"><span data-stu-id="da2e9-125">Then search for the item within the collection, which corresponds to the Microsoft Cloud Agreement:</span></span>

```java
// IAggregatePartner partnerOperations;

ResourceCollection<AgreementMetaData> agreements = partnerOperations.getAgreements().get();

AgreementMetaData microsoftCloudAgreement;

for (AgreementMetaData metadata : agreements)
{
    if(metadata.getAgreementType() == AgreementType.MicrosoftCloudAgreement)
    {
        microsoftCloudAgreement = metadata;
    }
}
```

<span data-ttu-id="da2e9-126">Een volledig voorbeeld vindt u in de [klasse GetAgreementDetails](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetAgreementDetails.java) van het [consoletest-app-project.](https://github.com/Microsoft/Partner-Center-Java-Samples)</span><span class="sxs-lookup"><span data-stu-id="da2e9-126">A complete sample can be found in the [GetAgreementDetails](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetAgreementDetails.java) class from the [console test app](https://github.com/Microsoft/Partner-Center-Java-Samples) project.</span></span>

## <a name="powershell"></a><span data-ttu-id="da2e9-127">PowerShell</span><span class="sxs-lookup"><span data-stu-id="da2e9-127">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="da2e9-128">De metagegevens van de overeenkomst voor de Microsoft Cloud-overeenkomst:</span><span class="sxs-lookup"><span data-stu-id="da2e9-128">To retrieve agreement metadata for the Microsoft Cloud Agreement:</span></span>

<span data-ttu-id="da2e9-129">Gebruik de [**opdracht Get-PartnerAgreementDetail.**](/powershell/module/partnercenter/get-partneragreementdetail)</span><span class="sxs-lookup"><span data-stu-id="da2e9-129">Use the [**Get-PartnerAgreementDetail**](/powershell/module/partnercenter/get-partneragreementdetail) command.</span></span> <span data-ttu-id="da2e9-130">Zoek vervolgens naar het item in de verzameling, dat overeenkomt met de Microsoft Cloud-overeenkomst:</span><span class="sxs-lookup"><span data-stu-id="da2e9-130">Then search for the item within the collection, which corresponds to the Microsoft Cloud Agreement:</span></span>

```powershell
Get-PartnerAgreementDetail | Where-Object {$_.AgreementType -eq 'MicrosoftCloudAgreement'} | Select-Object -First 1
```

## <a name="rest-request"></a><span data-ttu-id="da2e9-131">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="da2e9-131">REST request</span></span>

<span data-ttu-id="da2e9-132">Als u metagegevens van overeenkomst voor Microsoft Cloud-overeenkomst, maakt u eerst een REST-aanvraag om de **verzameling AgreementMetaData op te** halen.</span><span class="sxs-lookup"><span data-stu-id="da2e9-132">To retrieve agreement metadata for Microsoft Cloud Agreement, first create a REST Request to retrieve the **AgreementMetaData** collection.</span></span> <span data-ttu-id="da2e9-133">Zoek vervolgens naar het item in de verzameling dat overeenkomt met de Microsoft Cloud-overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="da2e9-133">Then search for the item in the collection that corresponds to the Microsoft Cloud Agreement.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="da2e9-134">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="da2e9-134">Request syntax</span></span>

| <span data-ttu-id="da2e9-135">Methode</span><span class="sxs-lookup"><span data-stu-id="da2e9-135">Method</span></span> | <span data-ttu-id="da2e9-136">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="da2e9-136">Request URI</span></span>                                                         |
|--------|---------------------------------------------------------------------|
| <span data-ttu-id="da2e9-137">GET</span><span class="sxs-lookup"><span data-stu-id="da2e9-137">GET</span></span>    | <span data-ttu-id="da2e9-138">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/agreements HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="da2e9-138">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/agreements HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="da2e9-139">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="da2e9-139">Request headers</span></span>

<span data-ttu-id="da2e9-140">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="da2e9-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="da2e9-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="da2e9-141">Request body</span></span>

<span data-ttu-id="da2e9-142">Geen.</span><span class="sxs-lookup"><span data-stu-id="da2e9-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="da2e9-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="da2e9-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/agreements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="da2e9-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="da2e9-144">REST response</span></span>

<span data-ttu-id="da2e9-145">Als dit lukt, retourneert deze methode een verzameling **AgreementMetaData-resources** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="da2e9-145">If successful, this method returns a collection of **AgreementMetaData** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="da2e9-146">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="da2e9-146">Response success and error codes</span></span>

<span data-ttu-id="da2e9-147">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="da2e9-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="da2e9-148">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="da2e9-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="da2e9-149">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="da2e9-149">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="da2e9-150">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="da2e9-150">Response example</span></span>

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
            "templateId": "998b88de-aa99-4388-a42c-1b3517d49490",
            "agreementType": "MicrosoftCloudAgreement",
            "agreementLink": "https://docs.microsoft.com/partner-center/agreements",
            "versionRank": 0
        }
    ],
    "links": {
        "self": {
            "uri": "/agreements",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

<span data-ttu-id="da2e9-151">Als u de resource wilt identificeren in het antwoord dat overeenkomt met de Microsoft Cloud-overeenkomst, zoek dan naar de resource waarvan de eigenschap **agreementType** de waarde MicrosoftCloudAgreement heeft.</span><span class="sxs-lookup"><span data-stu-id="da2e9-151">To identify the resource in the response that corresponds to the Microsoft Cloud Agreement, look for the resource whose **agreementType** property has value "MicrosoftCloudAgreement".</span></span>
