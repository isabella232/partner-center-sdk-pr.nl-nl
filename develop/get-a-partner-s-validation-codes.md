---
title: De Cloud validatie codes van een partner community ophalen
description: Informatie over het verkrijgen van validatie codes voor Cloud Community's van een partner.
ms.date: 11/08/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khakiali
ms.author: alikhaki
ms.openlocfilehash: d84a3d3c69d835e42565c4e6f1edb06ab338340a
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767356"
---
# <a name="get-a-partners-validation-codes"></a><span data-ttu-id="28157-103">De validatiecodes van een partner ophalen</span><span class="sxs-lookup"><span data-stu-id="28157-103">Get a partner's validation codes</span></span>

<span data-ttu-id="28157-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="28157-104">**Applies To**</span></span>

- <span data-ttu-id="28157-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="28157-105">Partner Center</span></span>

<span data-ttu-id="28157-106">Een verzameling van de Cloud validatie codes van een partner community ophalen.</span><span class="sxs-lookup"><span data-stu-id="28157-106">How to get a collection of a partner's Government Community Cloud validation codes.</span></span> <span data-ttu-id="28157-107">Een validatie code is vereist voor het maken van een klant in de cloud van de Government-community.</span><span class="sxs-lookup"><span data-stu-id="28157-107">A validation code is required to create a customer in the government community cloud.</span></span>

<span data-ttu-id="28157-108">Als u geïnteresseerd bent in het goed keuren van uw organisatie of uw organisatie voor Office 365 Government GCC voor CSP, raadpleegt u [Office 365 Government GCC voor CSP-partner en klant geschiktheids criteria/Partner-Center/CSP-gcc-validate).</span><span class="sxs-lookup"><span data-stu-id="28157-108">If you are interested in having your organization or your customers organization approved for Office 365 Government GCC for CSP, please see [Office 365 Government GCC for CSP Partner and Customer Eligibility Criteria/partner-center/csp-gcc-validate).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28157-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="28157-109">Prerequisites</span></span>

- <span data-ttu-id="28157-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="28157-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="28157-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="28157-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="28157-112">Bevestigde validatie na invullen van [het formulier.](https://products.office.com/government/eligibility-validation?ReqType=CSPPartner)</span><span class="sxs-lookup"><span data-stu-id="28157-112">Confirmed validation after filling out form [here](https://products.office.com/government/eligibility-validation?ReqType=CSPPartner).</span></span>

- <span data-ttu-id="28157-113">Een klant zonder een kwalificatie.</span><span class="sxs-lookup"><span data-stu-id="28157-113">A customer without a qualification.</span></span>

## <a name="c"></a><span data-ttu-id="28157-114">C\#</span><span class="sxs-lookup"><span data-stu-id="28157-114">C\#</span></span>

<span data-ttu-id="28157-115">Roep **GetValidationCodes** aan om een lijst met alle validatie codes van een partner op te halen.</span><span class="sxs-lookup"><span data-stu-id="28157-115">To get a list of all of a partner's validation codes, call **GetValidationCodes**.</span></span>

``` csharp
// create the partner operations
IAggregatePartner partnerOperations = PartnerService.Instance.CreatePartnerOperations(credentials);

var gccValidations = partnerOperations.Validations.GetValidationCodes();
```

## <a name="rest-request"></a><span data-ttu-id="28157-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="28157-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="28157-117">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="28157-117">Request syntax</span></span>

| <span data-ttu-id="28157-118">Methode</span><span class="sxs-lookup"><span data-stu-id="28157-118">Method</span></span>  | <span data-ttu-id="28157-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="28157-119">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="28157-120">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="28157-120">**GET**</span></span> | <span data-ttu-id="28157-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/all/validations http/1.1</span><span class="sxs-lookup"><span data-stu-id="28157-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/all/validations HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="28157-122">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="28157-122">Request headers</span></span>

<span data-ttu-id="28157-123">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="28157-123">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="28157-124">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="28157-124">Request body</span></span>

<span data-ttu-id="28157-125">Geen.</span><span class="sxs-lookup"><span data-stu-id="28157-125">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="28157-126">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="28157-126">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/all/validations HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 283b9b70-963a-4159-9920-f2bdf7ab7fce
MS-RequestId: 7266f5f6-30ca-4672-9eb6-6c9d6dd0e9d3
```

## <a name="rest-response"></a><span data-ttu-id="28157-127">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="28157-127">REST response</span></span>

<span data-ttu-id="28157-128">Als deze methode is geslaagd, wordt een lijst met [**ValidationCode**](utility-resources.md#validationcode) -resources in de antwoord tekst geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="28157-128">If successful, this method returns a list of [**ValidationCode**](utility-resources.md#validationcode) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="28157-129">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="28157-129">Response success and error codes</span></span>

<span data-ttu-id="28157-130">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="28157-130">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="28157-131">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="28157-131">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="28157-132">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="28157-132">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="28157-133">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="28157-133">Response example</span></span>

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
