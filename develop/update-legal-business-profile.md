---
title: Het wettelijke bedrijfsprofiel van een partner bijwerken
description: Het partner juridisch Business-profiel bijwerken.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: parthpandyaMSFT
ms.author: parthp
ms.openlocfilehash: 6c61b51ab0680e36daa99c11dc8e8c3506259d29
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767461"
---
# <a name="update-the-partner-legal-business-profile"></a><span data-ttu-id="a5b79-103">Het wettelijke bedrijfsprofiel van een partner bijwerken</span><span class="sxs-lookup"><span data-stu-id="a5b79-103">Update the partner legal business profile</span></span>

<span data-ttu-id="a5b79-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="a5b79-104">**Applies To**</span></span>

- <span data-ttu-id="a5b79-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="a5b79-105">Partner Center</span></span>
- <span data-ttu-id="a5b79-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="a5b79-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="a5b79-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="a5b79-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="a5b79-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="a5b79-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="a5b79-109">Het partner juridisch Business-profiel bijwerken.</span><span class="sxs-lookup"><span data-stu-id="a5b79-109">How to update the partner legal business profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a5b79-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a5b79-110">Prerequisites</span></span>

- <span data-ttu-id="a5b79-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a5b79-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a5b79-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="a5b79-112">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="a5b79-113">C\#</span><span class="sxs-lookup"><span data-stu-id="a5b79-113">C\#</span></span>

<span data-ttu-id="a5b79-114">Als u het partner juridisch Business-profiel wilt bijwerken, moet u eerst een **LegalBusinessProfile** -object instantiëren en dit vullen met het bestaande profiel.</span><span class="sxs-lookup"><span data-stu-id="a5b79-114">To update the partner legal business profile, first instantiate a **LegalBusinessProfile** object and populate it with the existing profile.</span></span> <span data-ttu-id="a5b79-115">Zie [het partner juridisch Business-profiel ophalen](get-legal-business-profile.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a5b79-115">For more information, see [Get the partner legal business profile](get-legal-business-profile.md).</span></span> <span data-ttu-id="a5b79-116">Werk vervolgens de eigenschappen bij die u wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a5b79-116">Then, update the properties that you need to change.</span></span> <span data-ttu-id="a5b79-117">In het volgende code voorbeeld ziet u hoe u het adres en de telefoon nummer van de primaire contact persoon wijzigt.</span><span class="sxs-lookup"><span data-stu-id="a5b79-117">The following code example illustrates changing the address and primary contact phone numbers.</span></span>

<span data-ttu-id="a5b79-118">Vervolgens krijgt u een interface voor de verzameling van de partner profiel bewerkingen van de eigenschap **IAggregatePartner. Profiles** .</span><span class="sxs-lookup"><span data-stu-id="a5b79-118">Next, get an interface to the partner profile operations collection from the **IAggregatePartner.Profiles** property.</span></span> <span data-ttu-id="a5b79-119">Vervolgens haalt u de waarde van de eigenschap **LegalBusinessProfile** op om een interface te verkrijgen voor juridische bedrijfs profiel bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="a5b79-119">Then, retrieve the value of the **LegalBusinessProfile** property to get an interface to legal business profile operations.</span></span> <span data-ttu-id="a5b79-120">Roep tot slot de [**Update**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.update) -of [**UpdateAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.updateasync) -methode aan met het gewijzigde object om het profiel bij te werken.</span><span class="sxs-lookup"><span data-stu-id="a5b79-120">Finally, call the [**Update**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.update) or [**UpdateAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.ilegalbusinessprofile.updateasync) method with the changed object to update the profile.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var legalBusinessProfile = partnerOperations.Profiles.LegalBusinessProfile.Get();

// Change the address and primary contact phone number.
legalBusinessProfile.Address.PhoneNumber = "4255550110";
legalBusinessProfile.PrimaryContact.PhoneNumber = "4255550110";

// Apply changes to the profile.
var updatedLegalBusinessProfile = partnerOperations.Profiles.LegalBusinessProfile.Update(legalBusinessProfile);
```

## <a name="rest-request"></a><span data-ttu-id="a5b79-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="a5b79-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a5b79-122">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="a5b79-122">Request syntax</span></span>

| <span data-ttu-id="a5b79-123">Methode</span><span class="sxs-lookup"><span data-stu-id="a5b79-123">Method</span></span>  | <span data-ttu-id="a5b79-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="a5b79-124">Request URI</span></span>                                                                    |
|---------|--------------------------------------------------------------------------------|
| <span data-ttu-id="a5b79-125">**PUT**</span><span class="sxs-lookup"><span data-stu-id="a5b79-125">**PUT**</span></span> | <span data-ttu-id="a5b79-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/Profiles/legalbusiness http/1.1</span><span class="sxs-lookup"><span data-stu-id="a5b79-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/legalbusiness HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="a5b79-127">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="a5b79-127">Request headers</span></span>

<span data-ttu-id="a5b79-128">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="a5b79-128">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a5b79-129">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="a5b79-129">Request body</span></span>

<span data-ttu-id="a5b79-130">De bron van het juridische zakelijke profiel.</span><span class="sxs-lookup"><span data-stu-id="a5b79-130">The legal business profile resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="a5b79-131">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="a5b79-131">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="a5b79-132">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="a5b79-132">REST response</span></span>

<span data-ttu-id="a5b79-133">Als dit lukt, bevat de antwoord tekst de bijgewerkte **LegalBusinessProfile**</span><span class="sxs-lookup"><span data-stu-id="a5b79-133">If successful, the response body contains the updated **LegalBusinessProfile**</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a5b79-134">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="a5b79-134">Response success and error codes</span></span>

<span data-ttu-id="a5b79-135">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="a5b79-135">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a5b79-136">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="a5b79-136">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a5b79-137">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="a5b79-137">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="a5b79-138">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="a5b79-138">Response example</span></span>

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
