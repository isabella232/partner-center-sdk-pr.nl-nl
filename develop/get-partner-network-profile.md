---
title: Microsoft Partner Network-profiel ophalen
description: Hiermee wordt een object opgehaald dat het MPN-Profiel van de partner vertegenwoordigt.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f8f3e74462da05de0be47964beb34228650b1f53
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767565"
---
# <a name="get-microsoft-partner-network-profile"></a><span data-ttu-id="9bca8-103">Microsoft Partner Network-profiel ophalen</span><span class="sxs-lookup"><span data-stu-id="9bca8-103">Get Microsoft Partner Network profile</span></span>

<span data-ttu-id="9bca8-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="9bca8-104">**Applies To**</span></span>

- <span data-ttu-id="9bca8-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="9bca8-105">Partner Center</span></span>
- <span data-ttu-id="9bca8-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="9bca8-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="9bca8-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="9bca8-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="9bca8-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="9bca8-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="9bca8-109">Hiermee wordt een object opgehaald dat het MPN-Profiel van de partner vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="9bca8-109">Gets an object representing the partner's MPN profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9bca8-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9bca8-110">Prerequisites</span></span>

- <span data-ttu-id="9bca8-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9bca8-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9bca8-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="9bca8-112">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="9bca8-113">C\#</span><span class="sxs-lookup"><span data-stu-id="9bca8-113">C\#</span></span>

<span data-ttu-id="9bca8-114">Als u een profiel voor een partner netwerk wilt ophalen, gebruikt u de verzameling **IAggregatePartner. Profiles** en roept u de eigenschap **MpnProfile** aan.</span><span class="sxs-lookup"><span data-stu-id="9bca8-114">To get a partner network profile, use your **IAggregatePartner.Profiles** collection and call the **MpnProfile** property.</span></span> <span data-ttu-id="9bca8-115">Roep ten slotte de methoden [**Get ()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="9bca8-115">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var mpnProfile = partnerOperations.Profiles.MpnProfile.Get();
```

<span data-ttu-id="9bca8-116">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="9bca8-116">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="9bca8-117">**Project**:P **klasse** artnercentersdk. FeaturesSamples: GetMPNProfile.cs</span><span class="sxs-lookup"><span data-stu-id="9bca8-117">**Project**:PartnerCenterSDK.FeaturesSamples **Class**: GetMPNProfile.cs</span></span>

## <a name="java"></a><span data-ttu-id="9bca8-118">Java</span><span class="sxs-lookup"><span data-stu-id="9bca8-118">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="9bca8-119">Als u een profiel voor een partner netwerk wilt ophalen, gebruikt u de functie **IAggregatePartner. getProfiles** en roept u de functie **getMpnProfile** aan.</span><span class="sxs-lookup"><span data-stu-id="9bca8-119">To get a partner network profile, use your **IAggregatePartner.getProfiles** function and call the **getMpnProfile** function.</span></span> <span data-ttu-id="9bca8-120">Roep ten slotte de functie **Get ()** aan.</span><span class="sxs-lookup"><span data-stu-id="9bca8-120">Finally, call the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;

MpnProfile mpnProfile = partnerOperations.getProfiles().getMpnProfile().get();
```

## <a name="powershell"></a><span data-ttu-id="9bca8-121">PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bca8-121">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="9bca8-122">Voer de opdracht [**Get-PartnerMpnProfile**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerMpnProfile.md) uit om een partner netwerk profiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="9bca8-122">To get a partner network profile, execute the [**Get-PartnerMpnProfile**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerMpnProfile.md) command.</span></span>

```powershell
Get-PartnerMpnProfile
```

## <a name="rest-request"></a><span data-ttu-id="9bca8-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="9bca8-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9bca8-124">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9bca8-124">Request syntax</span></span>

| <span data-ttu-id="9bca8-125">Methode</span><span class="sxs-lookup"><span data-stu-id="9bca8-125">Method</span></span>  | <span data-ttu-id="9bca8-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="9bca8-126">Request URI</span></span>                                                          |
|---------|----------------------------------------------------------------------|
| <span data-ttu-id="9bca8-127">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="9bca8-127">**GET**</span></span> | <span data-ttu-id="9bca8-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/Profiles/MPN http/1.1</span><span class="sxs-lookup"><span data-stu-id="9bca8-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/mpn HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9bca8-129">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="9bca8-129">Request headers</span></span>

<span data-ttu-id="9bca8-130">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="9bca8-130">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9bca8-131">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="9bca8-131">Request body</span></span>

<span data-ttu-id="9bca8-132">Geen.</span><span class="sxs-lookup"><span data-stu-id="9bca8-132">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="9bca8-133">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9bca8-133">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/mpn HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 76879323-92d1-437e-90dd-c84dbb9f7dec
MS-CorrelationId: cb9f3209-d020-4bf9-871c-e1f1c75348f8
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="9bca8-134">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="9bca8-134">REST response</span></span>

<span data-ttu-id="9bca8-135">Als dit lukt, retourneert deze methode een **MPNProfile** -object in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="9bca8-135">If successful, this method returns a **MPNProfile** object in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9bca8-136">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="9bca8-136">Response success and error codes</span></span>

<span data-ttu-id="9bca8-137">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="9bca8-137">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9bca8-138">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="9bca8-138">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9bca8-139">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="9bca8-139">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9bca8-140">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="9bca8-140">Response example</span></span>

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
