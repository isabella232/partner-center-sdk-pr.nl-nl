---
title: Een factureringsprofiel van een klant ophalen
description: Hiermee wordt het facturerings Profiel van een klant opgehaald. In het dash board van de partner centrum kan deze bewerking worden uitgevoerd door eerst een klant te selecteren.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 6c837c1c220e334df82e75eb680b6012862c9686
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767505"
---
# <a name="get-a-customers-billing-profile"></a><span data-ttu-id="28b42-103">Een factureringsprofiel van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="28b42-103">Get a customer's billing profile</span></span>

<span data-ttu-id="28b42-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="28b42-104">**Applies To**</span></span>

- <span data-ttu-id="28b42-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="28b42-105">Partner Center</span></span>
- <span data-ttu-id="28b42-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="28b42-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="28b42-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="28b42-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="28b42-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="28b42-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="28b42-109">Hiermee wordt het facturerings Profiel van een klant opgehaald.</span><span class="sxs-lookup"><span data-stu-id="28b42-109">Gets the billing profile of a customer.</span></span>

<span data-ttu-id="28b42-110">In het dash board van de partner centrum kan deze bewerking worden uitgevoerd door eerst [een klant te selecteren](get-a-customer-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="28b42-110">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="28b42-111">Selecteer vervolgens onder de naam van de klant in de zijbalk links **account**.</span><span class="sxs-lookup"><span data-stu-id="28b42-111">Then, under the customer's name in the left sidebar, select **Account**.</span></span> <span data-ttu-id="28b42-112">Het facturerings profiel bevindt zich onder de kop **factuur info** .</span><span class="sxs-lookup"><span data-stu-id="28b42-112">The billing profile can be found under the **Bill-to info** heading.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28b42-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="28b42-113">Prerequisites</span></span>

- <span data-ttu-id="28b42-114">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="28b42-114">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="28b42-115">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="28b42-115">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="28b42-116">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="28b42-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="28b42-117">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="28b42-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="28b42-118">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="28b42-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="28b42-119">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="28b42-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="28b42-120">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="28b42-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="28b42-121">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="28b42-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="28b42-122">C\#</span><span class="sxs-lookup"><span data-stu-id="28b42-122">C\#</span></span>

<span data-ttu-id="28b42-123">Als u het facturerings Profiel van een klant wilt ophalen, gebruikt u uw verzameling [**IPartner. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) en roept u de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="28b42-123">To get a customer's billing profile, use your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="28b42-124">Roep vervolgens de eigenschap [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) aan, gevolgd door de eigenschap [**facturering**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing) .</span><span class="sxs-lookup"><span data-stu-id="28b42-124">Then call the [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) property, followed by the [**Billing**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing) property.</span></span> <span data-ttu-id="28b42-125">Roep ten slotte de methoden [**Get ()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="28b42-125">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;

var billingProfile = partnerOperations.Customers.ById(selectedCustomerId).Profiles.Billing.Get();
```

<span data-ttu-id="28b42-126">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="28b42-126">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="28b42-127">**Project**: PartnerSDK. FeatureSamples- **klasse**: GetCustomerBillingProfile.cs</span><span class="sxs-lookup"><span data-stu-id="28b42-127">**Project**: PartnerSDK.FeatureSamples **Class**: GetCustomerBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="28b42-128">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="28b42-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="28b42-129">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="28b42-129">Request syntax</span></span>

| <span data-ttu-id="28b42-130">Methode</span><span class="sxs-lookup"><span data-stu-id="28b42-130">Method</span></span>  | <span data-ttu-id="28b42-131">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="28b42-131">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="28b42-132">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="28b42-132">**GET**</span></span> | <span data-ttu-id="28b42-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Profiles/billing http/1.1</span><span class="sxs-lookup"><span data-stu-id="28b42-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/profiles/billing HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="28b42-134">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="28b42-134">URI parameter</span></span>

<span data-ttu-id="28b42-135">Gebruik de volgende query parameter om het facturerings profiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="28b42-135">Use the following query parameter to get the billing profile.</span></span>

| <span data-ttu-id="28b42-136">Naam</span><span class="sxs-lookup"><span data-stu-id="28b42-136">Name</span></span>                   | <span data-ttu-id="28b42-137">Type</span><span class="sxs-lookup"><span data-stu-id="28b42-137">Type</span></span>     | <span data-ttu-id="28b42-138">Vereist</span><span class="sxs-lookup"><span data-stu-id="28b42-138">Required</span></span> | <span data-ttu-id="28b42-139">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="28b42-139">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="28b42-140">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="28b42-140">**customer-tenant-id**</span></span> | <span data-ttu-id="28b42-141">**guid**</span><span class="sxs-lookup"><span data-stu-id="28b42-141">**guid**</span></span> | <span data-ttu-id="28b42-142">J</span><span class="sxs-lookup"><span data-stu-id="28b42-142">Y</span></span>        | <span data-ttu-id="28b42-143">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="28b42-143">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="28b42-144">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="28b42-144">Request headers</span></span>

<span data-ttu-id="28b42-145">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="28b42-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="28b42-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="28b42-146">Request body</span></span>

<span data-ttu-id="28b42-147">Geen</span><span class="sxs-lookup"><span data-stu-id="28b42-147">None</span></span>

### <a name="request-example"></a><span data-ttu-id="28b42-148">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="28b42-148">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/profiles/billing HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a5581a74-2778-4e34-9172-18baa4877081
MS-CorrelationId: 51d521b3-62db-4682-b75d-fb8ab09113b2
```

## <a name="rest-response"></a><span data-ttu-id="28b42-149">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="28b42-149">REST response</span></span>

<span data-ttu-id="28b42-150">Als dit lukt, retourneert deze methode een verzameling [profiel](profile-resources.md) bronnen in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="28b42-150">If successful, this method returns a collection of [Profile](profile-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="28b42-151">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="28b42-151">Response success and error codes</span></span>

<span data-ttu-id="28b42-152">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="28b42-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="28b42-153">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="28b42-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="28b42-154">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="28b42-154">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="28b42-155">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="28b42-155">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1206
Content-Type: application/json
MS-CorrelationId: 51d521b3-62db-4682-b75d-fb8ab09113b2
MS-RequestId: a5581a74-2778-4e34-9172-18baa4877081
Date: Mon, 23 Nov 2015 18:13:43 GMT

{
    "id": "<billing-profile-id>",
    "firstName": "FirstName",
    "lastName": "LastName",
    "email": "email@sample.com",
    "culture": "en-US",
    "language": "en",
    "companyName": "CompanyName",
    "defaultAddress": {
        "country": "US",
        "city": "Redmond",
        "state": "WA",
        "addressLine1": "1 Microsoft Way",
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
