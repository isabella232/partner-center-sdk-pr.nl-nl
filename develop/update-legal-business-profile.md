---
title: Het wettelijke bedrijfsprofiel van een partner bijwerken
description: Het juridische bedrijfsprofiel van de partner bijwerken.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: parthpandyaMSFT
ms.author: parthp
ms.openlocfilehash: cb9f5815e0019c5e9b648dfd865e9752f0afdf05
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530324"
---
# <a name="update-the-partner-legal-business-profile"></a><span data-ttu-id="c1978-103">Het wettelijke bedrijfsprofiel van een partner bijwerken</span><span class="sxs-lookup"><span data-stu-id="c1978-103">Update the partner legal business profile</span></span>

<span data-ttu-id="c1978-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c1978-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c1978-105">Het juridische bedrijfsprofiel van de partner bijwerken.</span><span class="sxs-lookup"><span data-stu-id="c1978-105">How to update the partner legal business profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c1978-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c1978-106">Prerequisites</span></span>

- <span data-ttu-id="c1978-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c1978-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c1978-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="c1978-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="c1978-109">C\#</span><span class="sxs-lookup"><span data-stu-id="c1978-109">C\#</span></span>

<span data-ttu-id="c1978-110">Als u het juridische bedrijfsprofiel van de partner wilt bijwerken, instantieert u eerst een **LegalBusinessProfile-object** en vult u dit met het bestaande profiel.</span><span class="sxs-lookup"><span data-stu-id="c1978-110">To update the partner legal business profile, first instantiate a **LegalBusinessProfile** object and populate it with the existing profile.</span></span> <span data-ttu-id="c1978-111">Zie Het juridische bedrijfsprofiel van [de partner verkrijgen voor meer informatie.](get-legal-business-profile.md)</span><span class="sxs-lookup"><span data-stu-id="c1978-111">For more information, see [Get the partner legal business profile](get-legal-business-profile.md).</span></span> <span data-ttu-id="c1978-112">Werk vervolgens de eigenschappen bij die u moet wijzigen.</span><span class="sxs-lookup"><span data-stu-id="c1978-112">Then, update the properties that you need to change.</span></span> <span data-ttu-id="c1978-113">Het volgende codevoorbeeld illustreert het wijzigen van het adres en de telefoonnummers van de primaire contactpersoon.</span><span class="sxs-lookup"><span data-stu-id="c1978-113">The following code example illustrates changing the address and primary contact phone numbers.</span></span>

<span data-ttu-id="c1978-114">Haal vervolgens een interface op voor de verzameling bewerkingen van het partnerprofiel van **de eigenschap IAggregatePartner.Profiles.**</span><span class="sxs-lookup"><span data-stu-id="c1978-114">Next, get an interface to the partner profile operations collection from the **IAggregatePartner.Profiles** property.</span></span> <span data-ttu-id="c1978-115">Haal vervolgens de waarde van de eigenschap **LegalBusinessProfile** op om een interface te krijgen voor juridische bedrijfsprofielbewerkingen.</span><span class="sxs-lookup"><span data-stu-id="c1978-115">Then, retrieve the value of the **LegalBusinessProfile** property to get an interface to legal business profile operations.</span></span> <span data-ttu-id="c1978-116">Roep ten slotte de [**methode Update**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.update) of [**UpdateAsync aan**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.updateasync) met het gewijzigde object om het profiel bij te werken.</span><span class="sxs-lookup"><span data-stu-id="c1978-116">Finally, call the [**Update**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.update) or [**UpdateAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.updateasync) method with the changed object to update the profile.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var legalBusinessProfile = partnerOperations.Profiles.LegalBusinessProfile.Get();

// Change the address and primary contact phone number.
legalBusinessProfile.Address.PhoneNumber = "4255550110";
legalBusinessProfile.PrimaryContact.PhoneNumber = "4255550110";

// Apply changes to the profile.
var updatedLegalBusinessProfile = partnerOperations.Profiles.LegalBusinessProfile.Update(legalBusinessProfile);
```

## <a name="rest-request"></a><span data-ttu-id="c1978-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c1978-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c1978-118">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="c1978-118">Request syntax</span></span>

| <span data-ttu-id="c1978-119">Methode</span><span class="sxs-lookup"><span data-stu-id="c1978-119">Method</span></span>  | <span data-ttu-id="c1978-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c1978-120">Request URI</span></span>                                                                    |
|---------|--------------------------------------------------------------------------------|
| <span data-ttu-id="c1978-121">**PUT**</span><span class="sxs-lookup"><span data-stu-id="c1978-121">**PUT**</span></span> | <span data-ttu-id="c1978-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/legalbusiness HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c1978-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/legalbusiness HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c1978-123">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c1978-123">Request headers</span></span>

<span data-ttu-id="c1978-124">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="c1978-124">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c1978-125">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c1978-125">Request body</span></span>

<span data-ttu-id="c1978-126">De juridische bedrijfsprofielresource.</span><span class="sxs-lookup"><span data-stu-id="c1978-126">The legal business profile resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="c1978-127">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c1978-127">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/profiles/legalbusiness HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4549ac0c-0f1d-4d8f-b02f-6d36fadcccee
MS-CorrelationId: aa2a0d8c-7a41-470f-97ae-b82e6c338ee4
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 806
Expect: 100-continue

{
    "CompanyName": "Lucerne Publishing",
    "Address": {
        "Country": "US",
        "Region": null,
        "City": "Redmond",
        "State": "WA",
        "AddressLine1": "123 Main Street",
        "AddressLine2": "",
        "PostalCode": "98052",
        "FirstName": "Gena",
        "LastName": "Soto",
        "PhoneNumber": "4255550110"
    },
    "PrimaryContact": {
        "FirstName": "Gena",
        "LastName": "Soto",
        "Email": "gena@lucernepublishing.com",
        "PhoneNumber": "4255550110"
    },
    "CompanyApproverAddress": {
        "Country": "US",
        "Region": null,
        "City": "Redmond",
        "State": "WA",
        "AddressLine1": "123 Main Street",
        "AddressLine2": "",
        "PostalCode": "98052",
        "FirstName": null,
        "LastName": null,
        "PhoneNumber": null
    },
    "CompanyApproverEmail": "gena@lucernepublishing.com",
    "VettingStatus": "authorized",
    "VettingSubStatus": "none",
    "Links": {
        "Self": {
            "Uri": "/profiles/legalbusiness",
            "Method": "GET",
            "Headers": []
        }
    },
    "Attributes": {
        "ObjectType": "LegalBusinessProfile"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="c1978-128">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c1978-128">REST response</span></span>

<span data-ttu-id="c1978-129">Als dit lukt, bevat de antwoord-body het **bijgewerkte LegalBusinessProfile**</span><span class="sxs-lookup"><span data-stu-id="c1978-129">If successful, the response body contains the updated **LegalBusinessProfile**</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c1978-130">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="c1978-130">Response success and error codes</span></span>

<span data-ttu-id="c1978-131">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="c1978-131">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c1978-132">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c1978-132">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c1978-133">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="c1978-133">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c1978-134">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="c1978-134">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1157
Content-Type: application/json; charset=utf-8
MS-CorrelationId: aa2a0d8c-7a41-470f-97ae-b82e6c338ee4
MS-RequestId: 4549ac0c-0f1d-4d8f-b02f-6d36fadcccee
MS-CV: KZLU42qJ4EObO75q.0
MS-ServerId: 030020643
Date: Tue, 21 Mar 2017 22:03:15 GMT

{
    "companyName": "Lucerne Publishing",
    "address": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "123 Main Street",
        "addressLine2": "",
        "postalCode": "98052",
        "firstName": "Gena",
        "lastName": "Soto",
        "phoneNumber": "4255550110"
    },
    "primaryContact": {
        "firstName": "Gena",
        "lastName": "Soto",
        "email": "gena@lucernepublishing.com",
        "phoneNumber": "4255550110"
    },
    "companyApproverAddress": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "123 Main Street",
        "addressLine2": "",
        "postalCode": "98052"
    },
    "companyApproverEmail": "gena@lucernepublishing.com",
    "vettingStatus": "authorized",
    "vettingSubStatus": "none",
    "profileType": "LegalBusinessProfile",
    "links": {
        "self": {
            "uri": "/profiles/legalbusiness",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "LegalBusinessProfile"
    }
}
```
