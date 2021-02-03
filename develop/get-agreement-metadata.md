---
title: Metagegevens van de overeenkomst voor Microsoft Cloud-overeenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u de meta gegevens van de overeenkomst kunt ophalen voor Microsoft Cloud overeenkomst.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: c6a404eb38c4c31d3e69bb598872b932d8985529
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767348"
---
# <a name="get-agreement-metadata-for-microsoft-cloud-agreement"></a><span data-ttu-id="53770-103">Metagegevens van de overeenkomst voor Microsoft Cloud-overeenkomst ophalen</span><span class="sxs-lookup"><span data-stu-id="53770-103">Get agreement metadata for Microsoft Cloud Agreement</span></span>

<span data-ttu-id="53770-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="53770-104">**Applies To**</span></span>

- <span data-ttu-id="53770-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="53770-105">Partner Center</span></span>

> [!NOTE]
> <span data-ttu-id="53770-106">De **AgreementMetaData** -resource wordt momenteel alleen ondersteund door het partner centrum in de open bare cloud van micro soft.</span><span class="sxs-lookup"><span data-stu-id="53770-106">The **AgreementMetaData** resource is currently supported by Partner Center in the Microsoft public cloud only.</span></span> <span data-ttu-id="53770-107">Het is niet van toepassing op:</span><span class="sxs-lookup"><span data-stu-id="53770-107">It isn't applicable to:</span></span>
> - <span data-ttu-id="53770-108">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="53770-108">Partner Center operated by 21Vianet</span></span>
> - <span data-ttu-id="53770-109">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="53770-109">Partner Center for Microsoft Cloud Germany</span></span>
> - <span data-ttu-id="53770-110">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="53770-110">Partner Center for Microsoft Cloud for US Government</span></span>

## <a name="prerequisites"></a><span data-ttu-id="53770-111">Vereisten</span><span class="sxs-lookup"><span data-stu-id="53770-111">Prerequisites</span></span>

- <span data-ttu-id="53770-112">Als u gebruikmaakt van de .NET SDK van partner Center, is versie 1,9 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="53770-112">If you are using the Partner Center .NET SDK, version 1.9 or newer is required.</span></span>

- <span data-ttu-id="53770-113">Als u de Java SDK van het partner centrum gebruikt, is versie 1,8 of nieuwer vereist.</span><span class="sxs-lookup"><span data-stu-id="53770-113">If you are using the Partner Center Java SDK, version 1.8 or newer is required.</span></span>

- <span data-ttu-id="53770-114">Referenties zoals beschreven in [Partner Center-verificatie](./partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="53770-114">Credentials as described in [Partner Center authentication](./partner-center-authentication.md).</span></span> <span data-ttu-id="53770-115">Dit scenario ondersteunt app en verificatie van de gebruiker...</span><span class="sxs-lookup"><span data-stu-id="53770-115">This scenario supports app + user authentication..</span></span>

## <a name="net-version-114-or-newer"></a><span data-ttu-id="53770-116">.NET (versie 1,14 of nieuwer)</span><span class="sxs-lookup"><span data-stu-id="53770-116">.NET (version 1.14 or newer)</span></span>

<span data-ttu-id="53770-117">De meta gegevens van de overeenkomst voor Microsoft Cloud overeenkomst ophalen:</span><span class="sxs-lookup"><span data-stu-id="53770-117">To retrieve the agreement metadata for Microsoft Cloud Agreement:</span></span>

1. <span data-ttu-id="53770-118">Haal eerst de verzameling **IAggregatePartner. AgreementDetails** op.</span><span class="sxs-lookup"><span data-stu-id="53770-118">First, retrieve the **IAggregatePartner.AgreementDetails** collection.</span></span>

2. <span data-ttu-id="53770-119">Roep **ByAgreementType** -methode aan om de verzameling te filteren op Microsoft Cloud overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="53770-119">Call **ByAgreementType** method to filter the collection to Microsoft Cloud Agreement.</span></span>

3. <span data-ttu-id="53770-120">Tot slot roept u de methode Get of **GetAsync** **aan** .</span><span class="sxs-lookup"><span data-stu-id="53770-120">Finally, call **Get** or **GetAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCloudAgreement";

var microsoftCloudAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

<span data-ttu-id="53770-121">Een volledig voor beeld vindt u in de [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) -klasse in het [console test-app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) -project.</span><span class="sxs-lookup"><span data-stu-id="53770-121">A complete sample can be found in the [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) class from the [console test app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) project.</span></span>

## <a name="net-version-19---113"></a><span data-ttu-id="53770-122">.NET (versie 1,9-1,13)</span><span class="sxs-lookup"><span data-stu-id="53770-122">.NET (version 1.9 - 1.13)</span></span>

<span data-ttu-id="53770-123">U kunt als volgt meta gegevens van de overeenkomst ophalen voor de Microsoft Cloud overeenkomst:</span><span class="sxs-lookup"><span data-stu-id="53770-123">To retrieve agreement metadata for the Microsoft Cloud Agreement:</span></span>

<span data-ttu-id="53770-124">Haal eerst de verzameling **IAggregatePartner. AgreementDetails** op en roep vervolgens de methoden Get of **GetAsync** **aan** .</span><span class="sxs-lookup"><span data-stu-id="53770-124">First retrieve the **IAggregatePartner.AgreementDetails** collection and then call the **Get** or **GetAsync** methods.</span></span> <span data-ttu-id="53770-125">Zoek vervolgens naar het item in de verzameling, dat overeenkomt met de Microsoft Cloud overeenkomst:</span><span class="sxs-lookup"><span data-stu-id="53770-125">Then search for the item within the collection, which corresponds to the Microsoft Cloud Agreement:</span></span>

```csharp
// IAggregatePartner partnerOperations;

var agreements = partnerOperations.AgreementDetails.Get();

AgreementMetaData microsoftCloudAgreement = agreements.Items.FirstOrDefault (agr => agr.AgreementType == AgreementType.MicrosoftCloudAgreement);
```

## <a name="java"></a><span data-ttu-id="53770-126">Java</span><span class="sxs-lookup"><span data-stu-id="53770-126">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="53770-127">U kunt als volgt meta gegevens van de overeenkomst ophalen voor de Microsoft Cloud overeenkomst:</span><span class="sxs-lookup"><span data-stu-id="53770-127">To retrieve agreement metadata for the Microsoft Cloud Agreement:</span></span>

<span data-ttu-id="53770-128">Roep eerst de functie **IAggregatePartner. getAgreementDetails** aan en roep vervolgens de Get-functie **aan** .</span><span class="sxs-lookup"><span data-stu-id="53770-128">First call the **IAggregatePartner.getAgreementDetails** function and then call the **get** function.</span></span> <span data-ttu-id="53770-129">Zoek vervolgens naar het item in de verzameling, dat overeenkomt met de Microsoft Cloud overeenkomst:</span><span class="sxs-lookup"><span data-stu-id="53770-129">Then search for the item within the collection, which corresponds to the Microsoft Cloud Agreement:</span></span>

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

<span data-ttu-id="53770-130">Een volledig voor beeld vindt u in de [GetAgreementDetails](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetAgreementDetails.java) -klasse in het [console test-app](https://github.com/Microsoft/Partner-Center-Java-Samples) -project.</span><span class="sxs-lookup"><span data-stu-id="53770-130">A complete sample can be found in the [GetAgreementDetails](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetAgreementDetails.java) class from the [console test app](https://github.com/Microsoft/Partner-Center-Java-Samples) project.</span></span>

## <a name="powershell"></a><span data-ttu-id="53770-131">PowerShell</span><span class="sxs-lookup"><span data-stu-id="53770-131">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="53770-132">U kunt als volgt meta gegevens van de overeenkomst ophalen voor de Microsoft Cloud overeenkomst:</span><span class="sxs-lookup"><span data-stu-id="53770-132">To retrieve agreement metadata for the Microsoft Cloud Agreement:</span></span>

<span data-ttu-id="53770-133">Gebruik de opdracht [**Get-PartnerAgreementDetail**](/powershell/module/partnercenter/get-partneragreementdetail) .</span><span class="sxs-lookup"><span data-stu-id="53770-133">Use the [**Get-PartnerAgreementDetail**](/powershell/module/partnercenter/get-partneragreementdetail) command.</span></span> <span data-ttu-id="53770-134">Zoek vervolgens naar het item in de verzameling, dat overeenkomt met de Microsoft Cloud overeenkomst:</span><span class="sxs-lookup"><span data-stu-id="53770-134">Then search for the item within the collection, which corresponds to the Microsoft Cloud Agreement:</span></span>

```powershell
Get-PartnerAgreementDetail | Where-Object {$_.AgreementType -eq 'MicrosoftCloudAgreement'} | Select-Object -First 1
```

## <a name="rest-request"></a><span data-ttu-id="53770-135">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="53770-135">REST request</span></span>

<span data-ttu-id="53770-136">Als u de meta gegevens van de overeenkomst voor Microsoft Cloud overeenkomst wilt ophalen, maakt u eerst een REST-aanvraag om de **AgreementMetaData** -verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="53770-136">To retrieve agreement metadata for Microsoft Cloud Agreement, first create a REST Request to retrieve the **AgreementMetaData** collection.</span></span> <span data-ttu-id="53770-137">Zoek vervolgens naar het item in de verzameling dat overeenkomt met de Microsoft Cloud overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="53770-137">Then search for the item in the collection which corresponds to the Microsoft Cloud Agreement.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="53770-138">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="53770-138">Request syntax</span></span>

| <span data-ttu-id="53770-139">Methode</span><span class="sxs-lookup"><span data-stu-id="53770-139">Method</span></span> | <span data-ttu-id="53770-140">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="53770-140">Request URI</span></span>                                                         |
|--------|---------------------------------------------------------------------|
| <span data-ttu-id="53770-141">GET</span><span class="sxs-lookup"><span data-stu-id="53770-141">GET</span></span>    | <span data-ttu-id="53770-142">[*\{ BASEURL \}*](partner-center-rest-urls.md)/v1/agreements http/1.1</span><span class="sxs-lookup"><span data-stu-id="53770-142">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/agreements HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="53770-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="53770-143">Request headers</span></span>

<span data-ttu-id="53770-144">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="53770-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="53770-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="53770-145">Request body</span></span>

<span data-ttu-id="53770-146">Geen.</span><span class="sxs-lookup"><span data-stu-id="53770-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="53770-147">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="53770-147">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/agreements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="53770-148">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="53770-148">REST response</span></span>

<span data-ttu-id="53770-149">Als dit lukt, retourneert deze methode een verzameling **AgreementMetaData** -resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="53770-149">If successful, this method returns a collection of **AgreementMetaData** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="53770-150">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="53770-150">Response success and error codes</span></span>

<span data-ttu-id="53770-151">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="53770-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="53770-152">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="53770-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="53770-153">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="53770-153">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="53770-154">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="53770-154">Response example</span></span>

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

<span data-ttu-id="53770-155">Als u de resource wilt identificeren in het antwoord dat overeenkomt met de Microsoft Cloud overeenkomst, zoekt u naar de resource waarvan de eigenschap **Agreement type** de waarde ' MicrosoftCloudAgreement ' heeft.</span><span class="sxs-lookup"><span data-stu-id="53770-155">To identify the resource in the response which corresponds to the Microsoft Cloud Agreement, look for the resource whose **agreementType** property has value "MicrosoftCloudAgreement".</span></span>
