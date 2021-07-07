---
title: Een factureringsprofiel van een klant bijwerken
description: Hiermee wordt het factureringsprofiel van een klant bijgewerkt, inclusief het adres dat is gekoppeld aan het profiel.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: 1605c3e8cb050717209cb482d2299e2a42b9b186
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530035"
---
# <a name="update-a-customers-billing-profile"></a><span data-ttu-id="88040-103">Een factureringsprofiel van een klant bijwerken</span><span class="sxs-lookup"><span data-stu-id="88040-103">Update a customer's billing profile</span></span>

<span data-ttu-id="88040-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="88040-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="88040-105">Hiermee wordt het factureringsprofiel van een klant bijgewerkt, inclusief het adres dat is gekoppeld aan het profiel.</span><span class="sxs-lookup"><span data-stu-id="88040-105">Updates a customer's billing profile, including the address associated with the profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="88040-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="88040-106">Prerequisites</span></span>

- <span data-ttu-id="88040-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="88040-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="88040-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="88040-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="88040-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="88040-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="88040-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="88040-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="88040-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="88040-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="88040-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="88040-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="88040-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="88040-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="88040-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="88040-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="88040-115">C\#</span><span class="sxs-lookup"><span data-stu-id="88040-115">C\#</span></span>

<span data-ttu-id="88040-116">Als u het factureringsprofiel van een klant wilt bijwerken, haalt u het factureringsprofiel op en werkt u de eigenschappen indien nodig bij.</span><span class="sxs-lookup"><span data-stu-id="88040-116">To update a customer's billing profile, retrieve the billing profile and update the properties as necessary.</span></span> <span data-ttu-id="88040-117">Haal vervolgens de verzameling [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) op en roep vervolgens de [**methode ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="88040-117">Then, retrieve your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection, and then call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="88040-118">Roep vervolgens de [**eigenschap Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) aan, gevolgd door de [**eigenschap Billing.**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing)</span><span class="sxs-lookup"><span data-stu-id="88040-118">Then call the [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) property, followed by the [**Billing**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing) property.</span></span> <span data-ttu-id="88040-119">Vervolgens roept u de [**methoden Update()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.update) of [**UpdateAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.updateasync) aan.</span><span class="sxs-lookup"><span data-stu-id="88040-119">Then, finish by calling the [**Update()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.update) or [**UpdateAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.updateasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;

var billingProfile = partnerOperations.Customers.ById(selectedCustomerId).Profiles.Billing.Get();

// Apply changes to profile;

billingProfile = partnerOperations.Customers.ById(selectedCustomerId).Profiles.Billing.Update(billingProfile);
```

<span data-ttu-id="88040-120">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="88040-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="88040-121">**Project:** Klasse PartnerSDK.FeatureSamples: UpdateCustomerBillingProfile.cs </span><span class="sxs-lookup"><span data-stu-id="88040-121">**Project**: PartnerSDK.FeatureSamples **Class**: UpdateCustomerBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="88040-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="88040-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="88040-123">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="88040-123">Request syntax</span></span>

| <span data-ttu-id="88040-124">Methode</span><span class="sxs-lookup"><span data-stu-id="88040-124">Method</span></span>  | <span data-ttu-id="88040-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="88040-125">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="88040-126">**PUT**</span><span class="sxs-lookup"><span data-stu-id="88040-126">**PUT**</span></span> | <span data-ttu-id="88040-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/profiles/billing HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="88040-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/profiles/billing HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="88040-128">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="88040-128">URI parameter</span></span>

<span data-ttu-id="88040-129">Gebruik de volgende queryparameter om het factureringsprofiel bij te werken.</span><span class="sxs-lookup"><span data-stu-id="88040-129">Use the following query parameter to update the billing profile.</span></span>

| <span data-ttu-id="88040-130">Naam</span><span class="sxs-lookup"><span data-stu-id="88040-130">Name</span></span>                   | <span data-ttu-id="88040-131">Type</span><span class="sxs-lookup"><span data-stu-id="88040-131">Type</span></span>     | <span data-ttu-id="88040-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="88040-132">Required</span></span> | <span data-ttu-id="88040-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="88040-133">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="88040-134">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="88040-134">**customer-tenant-id**</span></span> | <span data-ttu-id="88040-135">**guid**</span><span class="sxs-lookup"><span data-stu-id="88040-135">**guid**</span></span> | <span data-ttu-id="88040-136">J</span><span class="sxs-lookup"><span data-stu-id="88040-136">Y</span></span>        | <span data-ttu-id="88040-137">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="88040-137">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="88040-138">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="88040-138">Request headers</span></span>

- <span data-ttu-id="88040-139">**If-Match:**" &lt; ETag &gt; " is vereist voor gelijktijdigheidsdetectie.</span><span class="sxs-lookup"><span data-stu-id="88040-139">**If-Match**: "&lt;ETag&gt;" is required for concurrency detection.</span></span>
<span data-ttu-id="88040-140">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="88040-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="88040-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="88040-141">Request body</span></span>

<span data-ttu-id="88040-142">De volledige resource.</span><span class="sxs-lookup"><span data-stu-id="88040-142">The full resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="88040-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="88040-143">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/profiles/billing HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ff85f13a-eb65-4b8e-9b67-05beb0565410
MS-CorrelationId: ff1b757d-cfaf-463a-b48b-0f96d05e95d7
Content-Type: application/json
Content-Length: 639
Expect: 100-continue

{
    "Id": "a58ceba5-60ac-48e4-a0bc-2a855811807a",
    "FirstName": "FirstName",
    "LastName": "LastName",
    "Email": "email@sample.com",
    "Culture": "en-US",
    "Language": "en",
    "CompanyName": "CompanyName",
    "DefaultAddress": {
        "Country": "US",
        "Region": null,
        "City": "Redmond",
        "State": "WA",
        "AddressLine1": "One Microsoft Way",
        "AddressLine2": null,
        "PostalCode": "98052",
        "FirstName": "FirstName",
        "LastName": "LastName",
        "PhoneNumber": "4255555555"
    },
    "Links": {
        "Self": {
            "Uri": "/v1/customers/<customer-tenant-id>/profiles/billing",
            "Method": "GET",
            "Headers": []
        }
    },
    "Attributes": {
        "Etag": "<etag>",
        "ObjectType": "CustomerBillingProfile"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="88040-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="88040-144">REST response</span></span>

<span data-ttu-id="88040-145">Als dit lukt, retourneert deze methode [bijgewerkte eigenschappen van](profile-resources.md) profielresources in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="88040-145">If successful, this method returns updated [Profile](profile-resources.md) resource properties in the response body.</span></span> <span data-ttu-id="88040-146">Voor deze aanroep is een ETag vereist voor gelijktijdigheidsdetectie.</span><span class="sxs-lookup"><span data-stu-id="88040-146">This call requires an ETag for concurrency detection.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="88040-147">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="88040-147">Response success and error codes</span></span>

<span data-ttu-id="88040-148">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="88040-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="88040-149">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="88040-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="88040-150">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="88040-150">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="88040-151">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="88040-151">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1210
Content-Type: application/json
MS-CorrelationId: ff1b757d-cfaf-463a-b48b-0f96d05e95d7
MS-RequestId: ff85f13a-eb65-4b8e-9b67-05beb0565410
Date: Mon, 23 Nov 2015 18:20:43 GMT

{
    "id": "a58ceba5-60ac-48e4-a0bc-2a855811807a",
    "firstName": "FirstName",
    "lastName": "LastName",
    "email": "email@sample.com",
    "culture": "en-US",
    "language": "en",
    "companyName": "companyName",
    "defaultAddress": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "One Microsoft Way",
        "postalCode": "98052",
        "firstName": "FirstName",
        "lastName": "LastName",
        "phoneNumber": "4255555555"
    },
    "links": {
        "self": {
            "uri": "/v1/customers/<customer-tenant-id>/profiles/billing",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "etag": "<etag>",
        "objectType": "CustomerBillingProfile"
    }
}
```
