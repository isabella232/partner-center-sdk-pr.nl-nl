---
title: Een factureringsprofiel van een klant bijwerken
description: Hiermee wordt het facturerings Profiel van een klant bijgewerkt, met inbegrip van het adres dat aan het profiel is gekoppeld.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: adf4e3de9941fded632e0561624d91d854c5aa24
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767520"
---
# <a name="update-a-customers-billing-profile"></a><span data-ttu-id="a4548-103">Een factureringsprofiel van een klant bijwerken</span><span class="sxs-lookup"><span data-stu-id="a4548-103">Update a customer's billing profile</span></span>

<span data-ttu-id="a4548-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="a4548-104">**Applies To**</span></span>

- <span data-ttu-id="a4548-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="a4548-105">Partner Center</span></span>
- <span data-ttu-id="a4548-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="a4548-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="a4548-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="a4548-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="a4548-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="a4548-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="a4548-109">Hiermee wordt het facturerings Profiel van een klant bijgewerkt, met inbegrip van het adres dat aan het profiel is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="a4548-109">Updates a customer's billing profile, including the address associated with the profile.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a4548-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a4548-110">Prerequisites</span></span>

- <span data-ttu-id="a4548-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a4548-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a4548-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="a4548-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="a4548-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a4548-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="a4548-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="a4548-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="a4548-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="a4548-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="a4548-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="a4548-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="a4548-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="a4548-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="a4548-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="a4548-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="a4548-119">C\#</span><span class="sxs-lookup"><span data-stu-id="a4548-119">C\#</span></span>

<span data-ttu-id="a4548-120">Als u het facturerings Profiel van een klant wilt bijwerken, haalt u het facturerings profiel op en werkt u de eigenschappen zo nodig bij.</span><span class="sxs-lookup"><span data-stu-id="a4548-120">To update a customer's billing profile, retrieve the billing profile and update the properties as necessary.</span></span> <span data-ttu-id="a4548-121">Vervolgens haalt u de verzameling [**IPartner. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) op en roept u de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="a4548-121">Then, retrieve your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection, and then call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="a4548-122">Roep vervolgens de eigenschap [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) aan, gevolgd door de eigenschap [**facturering**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing) .</span><span class="sxs-lookup"><span data-stu-id="a4548-122">Then call the [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) property, followed by the [**Billing**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing) property.</span></span> <span data-ttu-id="a4548-123">Voltooi vervolgens de methoden [**Update ()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.update) of [**UpdateAsync ()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.updateasync) .</span><span class="sxs-lookup"><span data-stu-id="a4548-123">Then, finish by calling the [**Update()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.update) or [**UpdateAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofile-1.updateasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;

var billingProfile = partnerOperations.Customers.ById(selectedCustomerId).Profiles.Billing.Get();

// Apply changes to profile;

billingProfile = partnerOperations.Customers.ById(selectedCustomerId).Profiles.Billing.Update(billingProfile);
```

<span data-ttu-id="a4548-124">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="a4548-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="a4548-125">**Project**: PartnerSDK. FeatureSamples- **klasse**: UpdateCustomerBillingProfile.cs</span><span class="sxs-lookup"><span data-stu-id="a4548-125">**Project**: PartnerSDK.FeatureSamples **Class**: UpdateCustomerBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="a4548-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="a4548-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a4548-127">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="a4548-127">Request syntax</span></span>

| <span data-ttu-id="a4548-128">Methode</span><span class="sxs-lookup"><span data-stu-id="a4548-128">Method</span></span>  | <span data-ttu-id="a4548-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="a4548-129">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a4548-130">**PUT**</span><span class="sxs-lookup"><span data-stu-id="a4548-130">**PUT**</span></span> | <span data-ttu-id="a4548-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Profiles/billing http/1.1</span><span class="sxs-lookup"><span data-stu-id="a4548-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/profiles/billing HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="a4548-132">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="a4548-132">URI parameter</span></span>

<span data-ttu-id="a4548-133">Gebruik de volgende query parameter om het facturerings profiel bij te werken.</span><span class="sxs-lookup"><span data-stu-id="a4548-133">Use the following query parameter to update the billing profile.</span></span>

| <span data-ttu-id="a4548-134">Naam</span><span class="sxs-lookup"><span data-stu-id="a4548-134">Name</span></span>                   | <span data-ttu-id="a4548-135">Type</span><span class="sxs-lookup"><span data-stu-id="a4548-135">Type</span></span>     | <span data-ttu-id="a4548-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="a4548-136">Required</span></span> | <span data-ttu-id="a4548-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a4548-137">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a4548-138">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="a4548-138">**customer-tenant-id**</span></span> | <span data-ttu-id="a4548-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="a4548-139">**guid**</span></span> | <span data-ttu-id="a4548-140">J</span><span class="sxs-lookup"><span data-stu-id="a4548-140">Y</span></span>        | <span data-ttu-id="a4548-141">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="a4548-141">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="a4548-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="a4548-142">Request headers</span></span>

- <span data-ttu-id="a4548-143">**If-match**: " &lt; ETAG &gt; " is vereist voor de gelijktijdigheids detectie.</span><span class="sxs-lookup"><span data-stu-id="a4548-143">**If-Match**: "&lt;ETag&gt;" is required for concurrency detection.</span></span>
<span data-ttu-id="a4548-144">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="a4548-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a4548-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="a4548-145">Request body</span></span>

<span data-ttu-id="a4548-146">De volledige resource.</span><span class="sxs-lookup"><span data-stu-id="a4548-146">The full resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="a4548-147">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="a4548-147">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="a4548-148">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="a4548-148">REST response</span></span>

<span data-ttu-id="a4548-149">Als dit lukt, retourneert deze methode bijgewerkte [profiel](profile-resources.md) bron eigenschappen in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="a4548-149">If successful, this method returns updated [Profile](profile-resources.md) resource properties in the response body.</span></span> <span data-ttu-id="a4548-150">Voor deze aanroep is een ETag vereist voor de gelijktijdigheids detectie.</span><span class="sxs-lookup"><span data-stu-id="a4548-150">This call requires an ETag for concurrency detection.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a4548-151">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="a4548-151">Response success and error codes</span></span>

<span data-ttu-id="a4548-152">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="a4548-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a4548-153">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="a4548-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a4548-154">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="a4548-154">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="a4548-155">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="a4548-155">Response example</span></span>

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
