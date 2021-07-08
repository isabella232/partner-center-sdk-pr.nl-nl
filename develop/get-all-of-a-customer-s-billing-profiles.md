---
title: Een factureringsprofiel van een klant ophalen
description: Haalt het factureringsprofiel van een klant op. In het Partner Center dashboard kunt u deze bewerking uitvoeren door eerst een klant te selecteren.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: d22be53a5be4efcda76a568578468615495febb6
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760586"
---
# <a name="get-a-customers-billing-profile"></a><span data-ttu-id="24e40-104">Een factureringsprofiel van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="24e40-104">Get a customer's billing profile</span></span>

<span data-ttu-id="24e40-105">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="24e40-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="24e40-106">Haalt het factureringsprofiel van een klant op.</span><span class="sxs-lookup"><span data-stu-id="24e40-106">Gets the billing profile of a customer.</span></span>

<span data-ttu-id="24e40-107">In het Partner Center dashboard kunt u deze bewerking uitvoeren door eerst [een klant te selecteren.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="24e40-107">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="24e40-108">Selecteer vervolgens account onder de naam van de klant in de **linkerzijbalk.**</span><span class="sxs-lookup"><span data-stu-id="24e40-108">Then, under the customer's name in the left sidebar, select **Account**.</span></span> <span data-ttu-id="24e40-109">Het factureringsprofiel vindt u onder de kop **Factuurgegevens.**</span><span class="sxs-lookup"><span data-stu-id="24e40-109">The billing profile can be found under the **Bill-to info** heading.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="24e40-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="24e40-110">Prerequisites</span></span>

- <span data-ttu-id="24e40-111">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="24e40-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="24e40-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="24e40-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="24e40-113">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="24e40-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="24e40-114">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="24e40-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="24e40-115">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="24e40-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="24e40-116">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="24e40-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="24e40-117">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="24e40-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="24e40-118">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="24e40-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="24e40-119">C\#</span><span class="sxs-lookup"><span data-stu-id="24e40-119">C\#</span></span>

<span data-ttu-id="24e40-120">Als u het factureringsprofiel van een klant wilt ophalen, gebruikt u de [**verzameling IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) en roept u de [**methode ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="24e40-120">To get a customer's billing profile, use your [**IPartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="24e40-121">Roep vervolgens de [**eigenschap Profielen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) aan, gevolgd door de [**eigenschap**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing) Facturering.</span><span class="sxs-lookup"><span data-stu-id="24e40-121">Then call the [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) property, followed by the [**Billing**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.billing) property.</span></span> <span data-ttu-id="24e40-122">Roep ten slotte de [**methoden Get()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) of [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="24e40-122">Finally, call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;

var billingProfile = partnerOperations.Customers.ById(selectedCustomerId).Profiles.Billing.Get();
```

<span data-ttu-id="24e40-123">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="24e40-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="24e40-124">**Project:** Klasse PartnerSDK.FeatureSamples: GetCustomerBillingProfile.cs </span><span class="sxs-lookup"><span data-stu-id="24e40-124">**Project**: PartnerSDK.FeatureSamples **Class**: GetCustomerBillingProfile.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="24e40-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="24e40-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="24e40-126">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="24e40-126">Request syntax</span></span>

| <span data-ttu-id="24e40-127">Methode</span><span class="sxs-lookup"><span data-stu-id="24e40-127">Method</span></span>  | <span data-ttu-id="24e40-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="24e40-128">Request URI</span></span>                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="24e40-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="24e40-129">**GET**</span></span> | <span data-ttu-id="24e40-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/profiles/billing HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="24e40-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/profiles/billing HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="24e40-131">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="24e40-131">URI parameter</span></span>

<span data-ttu-id="24e40-132">Gebruik de volgende queryparameter om het factureringsprofiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="24e40-132">Use the following query parameter to get the billing profile.</span></span>

| <span data-ttu-id="24e40-133">Naam</span><span class="sxs-lookup"><span data-stu-id="24e40-133">Name</span></span>                   | <span data-ttu-id="24e40-134">Type</span><span class="sxs-lookup"><span data-stu-id="24e40-134">Type</span></span>     | <span data-ttu-id="24e40-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="24e40-135">Required</span></span> | <span data-ttu-id="24e40-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="24e40-136">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="24e40-137">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="24e40-137">**customer-tenant-id**</span></span> | <span data-ttu-id="24e40-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="24e40-138">**guid**</span></span> | <span data-ttu-id="24e40-139">J</span><span class="sxs-lookup"><span data-stu-id="24e40-139">Y</span></span>        | <span data-ttu-id="24e40-140">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="24e40-140">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="24e40-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="24e40-141">Request headers</span></span>

<span data-ttu-id="24e40-142">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="24e40-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="24e40-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="24e40-143">Request body</span></span>

<span data-ttu-id="24e40-144">Geen</span><span class="sxs-lookup"><span data-stu-id="24e40-144">None</span></span>

### <a name="request-example"></a><span data-ttu-id="24e40-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="24e40-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/profiles/billing HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a5581a74-2778-4e34-9172-18baa4877081
MS-CorrelationId: 51d521b3-62db-4682-b75d-fb8ab09113b2
```

## <a name="rest-response"></a><span data-ttu-id="24e40-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="24e40-146">REST response</span></span>

<span data-ttu-id="24e40-147">Als dit lukt, retourneert deze methode een verzameling [profielresources](profile-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="24e40-147">If successful, this method returns a collection of [Profile](profile-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="24e40-148">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="24e40-148">Response success and error codes</span></span>

<span data-ttu-id="24e40-149">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="24e40-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="24e40-150">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="24e40-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="24e40-151">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="24e40-151">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="24e40-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="24e40-152">Response example</span></span>

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
