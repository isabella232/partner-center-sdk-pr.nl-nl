---
title: Microsoft Partner Network-profiel ophalen
description: Haalt een -object op dat het MPN-profiel van de partner vertegenwoordigt.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 38c12a9a9755b9838b7742d9f38c5cbd52b81210
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548852"
---
# <a name="get-microsoft-partner-network-profile"></a><span data-ttu-id="4d635-103">Microsoft Partner Network-profiel ophalen</span><span class="sxs-lookup"><span data-stu-id="4d635-103">Get Microsoft Partner Network profile</span></span>

<span data-ttu-id="4d635-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="4d635-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="4d635-105">Haalt een -object op dat het MPN-profiel van de partner vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="4d635-105">Gets an object representing the partner's MPN profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4d635-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4d635-106">Prerequisites</span></span>

- <span data-ttu-id="4d635-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4d635-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4d635-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="4d635-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="4d635-109">C\#</span><span class="sxs-lookup"><span data-stu-id="4d635-109">C\#</span></span>

<span data-ttu-id="4d635-110">Als u een partnernetwerkprofiel wilt ophalen, gebruikt u de verzameling **IAggregatePartner.Profiles** en roept u de **eigenschap MpnProfile aan.**</span><span class="sxs-lookup"><span data-stu-id="4d635-110">To get a partner network profile, use your **IAggregatePartner.Profiles** collection and call the **MpnProfile** property.</span></span> <span data-ttu-id="4d635-111">Roep ten slotte de [**methoden Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) of [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="4d635-111">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var mpnProfile = partnerOperations.Profiles.MpnProfile.Get();
```

<span data-ttu-id="4d635-112">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="4d635-112">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="4d635-113">**Project**:P artnerCenterSDK.FeaturesSamples-klasse: GetMPNProfile.cs</span><span class="sxs-lookup"><span data-stu-id="4d635-113">**Project**:PartnerCenterSDK.FeaturesSamples **Class**: GetMPNProfile.cs</span></span>

## <a name="java"></a><span data-ttu-id="4d635-114">Java</span><span class="sxs-lookup"><span data-stu-id="4d635-114">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="4d635-115">Als u een partnernetwerkprofiel wilt op halen, gebruikt u de functie **IAggregatePartner.getProfiles** en roept u de **functie getMpnProfile** aan.</span><span class="sxs-lookup"><span data-stu-id="4d635-115">To get a partner network profile, use your **IAggregatePartner.getProfiles** function and call the **getMpnProfile** function.</span></span> <span data-ttu-id="4d635-116">Roep ten slotte de **functie get()** aan.</span><span class="sxs-lookup"><span data-stu-id="4d635-116">Finally, call the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;

MpnProfile mpnProfile = partnerOperations.getProfiles().getMpnProfile().get();
```

## <a name="powershell"></a><span data-ttu-id="4d635-117">PowerShell</span><span class="sxs-lookup"><span data-stu-id="4d635-117">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="4d635-118">Voer de opdracht [**Get-PartnerMpnProfile**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerMpnProfile.md) uit om een partnernetwerkprofiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="4d635-118">To get a partner network profile, execute the [**Get-PartnerMpnProfile**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerMpnProfile.md) command.</span></span>

```powershell
Get-PartnerMpnProfile
```

## <a name="rest-request"></a><span data-ttu-id="4d635-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="4d635-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4d635-120">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="4d635-120">Request syntax</span></span>

| <span data-ttu-id="4d635-121">Methode</span><span class="sxs-lookup"><span data-stu-id="4d635-121">Method</span></span>  | <span data-ttu-id="4d635-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="4d635-122">Request URI</span></span>                                                          |
|---------|----------------------------------------------------------------------|
| <span data-ttu-id="4d635-123">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="4d635-123">**GET**</span></span> | <span data-ttu-id="4d635-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/mpn HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4d635-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/mpn HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4d635-125">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="4d635-125">Request headers</span></span>

<span data-ttu-id="4d635-126">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="4d635-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4d635-127">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="4d635-127">Request body</span></span>

<span data-ttu-id="4d635-128">Geen.</span><span class="sxs-lookup"><span data-stu-id="4d635-128">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="4d635-129">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4d635-129">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/mpn HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 76879323-92d1-437e-90dd-c84dbb9f7dec
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="4d635-130">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="4d635-130">REST response</span></span>

<span data-ttu-id="4d635-131">Als dit lukt, retourneert deze methode een **MPNProfile-object** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="4d635-131">If successful, this method returns a **MPNProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4d635-132">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="4d635-132">Response success and error codes</span></span>

<span data-ttu-id="4d635-133">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="4d635-133">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4d635-134">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="4d635-134">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4d635-135">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="4d635-135">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4d635-136">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="4d635-136">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
MS-RequestId: 76879323-92d1-437e-90dd-c84dbb9f7dec
Date: Mon, 21 Mar 2016 05:51:29 GMT

{
    "mpnId":"<mpnID>",
    "profileType":"MpnProfile",
    "links":{
        "self":{
            "uri":"/profiles/mpn",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "objectType":"MpnProfile"
    }
}
```
