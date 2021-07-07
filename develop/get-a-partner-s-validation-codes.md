---
title: Validatiecodes van een partner Government Community Cloud krijgen
description: De validatiecodes van een partner Government Community Cloud krijgen.
ms.date: 11/08/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khakiali
ms.author: alikhaki
ms.openlocfilehash: 04bccf587628337004a5825b534048945f791839
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873867"
---
# <a name="get-a-partners-validation-codes"></a><span data-ttu-id="e1b3d-103">De validatiecodes van een partner ophalen</span><span class="sxs-lookup"><span data-stu-id="e1b3d-103">Get a partner's validation codes</span></span>

<span data-ttu-id="e1b3d-104">In dit artikel wordt beschreven hoe u een verzameling van de validatiecodes van een partner Government Community Cloud ophalen.</span><span class="sxs-lookup"><span data-stu-id="e1b3d-104">This article describes how to get a collection of a partner's Government Community Cloud validation codes.</span></span> <span data-ttu-id="e1b3d-105">Er is een validatiecode vereist om een klant te maken in de communitycloud van de overheid.</span><span class="sxs-lookup"><span data-stu-id="e1b3d-105">A validation code is required to create a customer in the government community cloud.</span></span>

<span data-ttu-id="e1b3d-106">Zie Office 365 Government GCC for CSP Partner and Customer eligibility criteria (Office 365 Government GCC voor [CSP-partner](/partner-center/csp-gcc-validate)en klantcriteria) als u geïnteresseerd bent in het goedkeuren van Office 365 Government GCC voor CSP door uw organisatie of de organisatie van uw klant.</span><span class="sxs-lookup"><span data-stu-id="e1b3d-106">If you are interested in having your organization or your customer's organization approved for Office 365 Government GCC for CSP, see [Office 365 Government GCC for CSP Partner and Customer eligibility criteria](/partner-center/csp-gcc-validate).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e1b3d-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e1b3d-107">Prerequisites</span></span>

- <span data-ttu-id="e1b3d-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e1b3d-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e1b3d-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="e1b3d-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="e1b3d-110">Validatie bevestigd na het invullen van het [formulier hier](https://products.office.com/government/eligibility-validation?ReqType=CSPPartner).</span><span class="sxs-lookup"><span data-stu-id="e1b3d-110">Confirmed validation after filling out form [here](https://products.office.com/government/eligibility-validation?ReqType=CSPPartner).</span></span>

- <span data-ttu-id="e1b3d-111">Een klant zonder kwalificatie.</span><span class="sxs-lookup"><span data-stu-id="e1b3d-111">A customer without a qualification.</span></span>

## <a name="c"></a><span data-ttu-id="e1b3d-112">C\#</span><span class="sxs-lookup"><span data-stu-id="e1b3d-112">C\#</span></span>

<span data-ttu-id="e1b3d-113">Voor een lijst met alle validatiecodes van een partner roept u **GetValidationCodes aan.**</span><span class="sxs-lookup"><span data-stu-id="e1b3d-113">To get a list of all of a partner's validation codes, call **GetValidationCodes**.</span></span>

``` csharp
// create the partner operations
IAggregatePartner partnerOperations = PartnerService.Instance.CreatePartnerOperations(credentials);

var gccValidations = partnerOperations.Validations.GetValidationCodes();
```

## <a name="rest-request"></a><span data-ttu-id="e1b3d-114">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e1b3d-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e1b3d-115">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e1b3d-115">Request syntax</span></span>

| <span data-ttu-id="e1b3d-116">Methode</span><span class="sxs-lookup"><span data-stu-id="e1b3d-116">Method</span></span>  | <span data-ttu-id="e1b3d-117">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e1b3d-117">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e1b3d-118">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e1b3d-118">**GET**</span></span> | <span data-ttu-id="e1b3d-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/all/validations HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e1b3d-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/all/validations HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e1b3d-120">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e1b3d-120">Request headers</span></span>

<span data-ttu-id="e1b3d-121">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e1b3d-121">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e1b3d-122">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e1b3d-122">Request body</span></span>

<span data-ttu-id="e1b3d-123">Geen.</span><span class="sxs-lookup"><span data-stu-id="e1b3d-123">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e1b3d-124">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e1b3d-124">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/all/validations HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 283b9b70-963a-4159-9920-f2bdf7ab7fce
MS-RequestId: 7266f5f6-30ca-4672-9eb6-6c9d6dd0e9d3
```

## <a name="rest-response"></a><span data-ttu-id="e1b3d-125">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e1b3d-125">REST response</span></span>

<span data-ttu-id="e1b3d-126">Als dit lukt, retourneert deze methode een lijst met [**ValidationCode-resources**](utility-resources.md#validationcode) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="e1b3d-126">If successful, this method returns a list of [**ValidationCode**](utility-resources.md#validationcode) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e1b3d-127">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e1b3d-127">Response success and error codes</span></span>

<span data-ttu-id="e1b3d-128">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e1b3d-128">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e1b3d-129">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e1b3d-129">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e1b3d-130">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="e1b3d-130">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e1b3d-131">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e1b3d-131">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 434
Content-Type: application/json
MS-CorrelationId: 283b9b70-963a-4159-9920-f2bdf7ab7fce
MS-RequestId: 7266f5f6-30ca-4672-9eb6-6c9d6dd0e9d3

[
  {
    "partnerId": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d",
    "organizationName": "Contoso, Inc.",
    "validationId": "12345",
    "maxCreates": 5,
    "remainingCreates": 4,
    "eTag": "W/\"datetime'2018-10-10T18%3A49%3A58.727348Z'\""
  },
  {
    "partnerId": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d",
    "organizationName": "Contoso, Inc. Finance Department",
    "validationId": "987654",
    "maxCreates": 5,
    "remainingCreates": 5,
    "eTag": "W/\"datetime'2018-10-19T17%3A51%3A45.6584512Z'\""
  }
]
```
