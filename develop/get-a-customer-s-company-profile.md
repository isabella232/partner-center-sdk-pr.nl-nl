---
title: Een bedrijfsprofiel van een klant ophalen
description: Hiermee haalt u het bedrijfs profiel van een klant.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: c26a86ecb96e5e7942ba179f8a3cc704abab7df5
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767385"
---
# <a name="get-a-customers-company-profile"></a><span data-ttu-id="dd40d-103">Een bedrijfsprofiel van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="dd40d-103">Get a customer's company profile</span></span>

<span data-ttu-id="dd40d-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="dd40d-104">**Applies To**</span></span>

- <span data-ttu-id="dd40d-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="dd40d-105">Partner Center</span></span>
- <span data-ttu-id="dd40d-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="dd40d-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="dd40d-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="dd40d-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="dd40d-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="dd40d-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="dd40d-109">Hiermee haalt u het bedrijfs profiel van een klant.</span><span class="sxs-lookup"><span data-stu-id="dd40d-109">Gets the company profile of a customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dd40d-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="dd40d-110">Prerequisites</span></span>

- <span data-ttu-id="dd40d-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="dd40d-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="dd40d-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="dd40d-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="dd40d-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="dd40d-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="dd40d-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="dd40d-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="dd40d-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="dd40d-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="dd40d-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="dd40d-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="dd40d-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="dd40d-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="dd40d-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="dd40d-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="dd40d-119">C\#</span><span class="sxs-lookup"><span data-stu-id="dd40d-119">C\#</span></span>

<span data-ttu-id="dd40d-120">Als u het bedrijfs profiel voor een klant wilt ophalen, roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="dd40d-120">To get the company profile for a customer, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="dd40d-121">Haal vervolgens de [**ICustomerProfileCollection**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection) -interface van de klant op uit de eigenschap [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) om toegang te krijgen tot de bedrijfs eigenschap.</span><span class="sxs-lookup"><span data-stu-id="dd40d-121">Then get the customer's [**ICustomerProfileCollection**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection) interface from the [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) property, in order to access its Company property.</span></span> <span data-ttu-id="dd40d-122">Vervolgens haalt u de [**ICustomerReadonlyProfile**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1) -interface van de eigenschap [**ICustomerProfileCollection. Company**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.company) op en roept u de methoden [**Get ()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="dd40d-122">Next, get the [**ICustomerReadonlyProfile**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1) interface from the [**ICustomerProfileCollection.Company**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.company) property, and call its [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

var companyProfile = partnerOperations.Customers.ById(customerId).Profiles.Company.Get();
```

<span data-ttu-id="dd40d-123">Voor **beeld**: [de Partner Center-SDK downloaden](https://go.microsoft.com/fwlink/p/?LinkId=746681).</span><span class="sxs-lookup"><span data-stu-id="dd40d-123">**Sample**: [Download the Partner Center SDK](https://go.microsoft.com/fwlink/p/?LinkId=746681).</span></span> <span data-ttu-id="dd40d-124">**Project**: PartnerSdk. FeatureSamples- **klasse**: GetCustomerCompanyProfile.cs</span><span class="sxs-lookup"><span data-stu-id="dd40d-124">**Project**: PartnerSdk.FeatureSamples **Class**: GetCustomerCompanyProfile.cs</span></span>

## <a name="java"></a><span data-ttu-id="dd40d-125">Java</span><span class="sxs-lookup"><span data-stu-id="dd40d-125">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="dd40d-126">Als u het bedrijfs profiel voor een klant wilt ophalen, roept u de functie **IAggregatePartner. getCustomers (). byId** aan met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="dd40d-126">To get the company profile for a customer, call the **IAggregatePartner.getCustomers().byId** function with the customer identifier to identify the customer.</span></span> <span data-ttu-id="dd40d-127">Haal vervolgens de **ICustomerProfileCollection** -interface van de klant op uit de functie [**getProfiles**] om toegang te krijgen tot de bedrijfs eigenschap.</span><span class="sxs-lookup"><span data-stu-id="dd40d-127">Then get the customer's **ICustomerProfileCollection** interface from the [**getProfiles**] function, in order to access its Company property.</span></span> <span data-ttu-id="dd40d-128">Vervolgens haalt u de **ICustomerReadonlyProfile** -interface op uit de functie **ICustomerProfileCollection. getCompany** en roept u de **Get** -functie aan.</span><span class="sxs-lookup"><span data-stu-id="dd40d-128">Next, get the **ICustomerReadonlyProfile** interface from the **ICustomerProfileCollection.getCompany** function, and call the **get** function.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;

CustomerCompanyProfile companyProfile = partnerOperations.getCustomers().byId(customerId).getProfiles().getCompany().get();
```

## <a name="rest-request"></a><span data-ttu-id="dd40d-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="dd40d-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="dd40d-130">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="dd40d-130">Request syntax</span></span>

| <span data-ttu-id="dd40d-131">Methode</span><span class="sxs-lookup"><span data-stu-id="dd40d-131">Method</span></span>  | <span data-ttu-id="dd40d-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="dd40d-132">Request URI</span></span>                                                             |
|---------|-------------------------------------------------------------------------|
| <span data-ttu-id="dd40d-133">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="dd40d-133">**GET**</span></span> | <span data-ttu-id="dd40d-134">*{baseURL}*/v1/Customers/{Customer-Tenant-id}/Profiles/Company http/1.1</span><span class="sxs-lookup"><span data-stu-id="dd40d-134">*{baseURL}*/v1/customers/{customer-tenant-id}/profiles/company HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="dd40d-135">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="dd40d-135">URI parameter</span></span>

<span data-ttu-id="dd40d-136">Gebruik de volgende query parameter om het bedrijfs profiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="dd40d-136">Use the following query parameter to get the company profile.</span></span>

| <span data-ttu-id="dd40d-137">Naam</span><span class="sxs-lookup"><span data-stu-id="dd40d-137">Name</span></span>                   | <span data-ttu-id="dd40d-138">Type</span><span class="sxs-lookup"><span data-stu-id="dd40d-138">Type</span></span>     | <span data-ttu-id="dd40d-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="dd40d-139">Required</span></span> | <span data-ttu-id="dd40d-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dd40d-140">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="dd40d-141">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="dd40d-141">**customer-tenant-id**</span></span> | <span data-ttu-id="dd40d-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="dd40d-142">**guid**</span></span> | <span data-ttu-id="dd40d-143">J</span><span class="sxs-lookup"><span data-stu-id="dd40d-143">Y</span></span>        | <span data-ttu-id="dd40d-144">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="dd40d-144">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="dd40d-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="dd40d-145">Request headers</span></span>

<span data-ttu-id="dd40d-146">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="dd40d-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="dd40d-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="dd40d-147">Request body</span></span>

<span data-ttu-id="dd40d-148">Geen</span><span class="sxs-lookup"><span data-stu-id="dd40d-148">None</span></span>

### <a name="request-example"></a><span data-ttu-id="dd40d-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="dd40d-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/profiles/company HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0b6f039c-e4b5-4b9e-bdac-b39077bb60da
MS-CorrelationId: ffa9174c-dbcb-47de-b70d-10e640a7f1b4
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="dd40d-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="dd40d-150">REST response</span></span>

<span data-ttu-id="dd40d-151">Als dit lukt, retourneert deze methode informatie in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="dd40d-151">If successful, this method returns information in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="dd40d-152">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="dd40d-152">Response success and error codes</span></span>

<span data-ttu-id="dd40d-153">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="dd40d-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="dd40d-154">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="dd40d-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="dd40d-155">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="dd40d-155">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="dd40d-156">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="dd40d-156">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 488
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ffa9174c-dbcb-47de-b70d-10e640a7f1b4
MS-RequestId: 0b6f039c-e4b5-4b9e-bdac-b39077bb60da
MS-CV: /e74N8OrkE29ycwZ.0
MS-ServerId: 101112202
Date: Wed, 04 Jan 2017 19:48:51 GMT

{
    "tenantId": "4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04",
    "domain": "dtdemocspcustomer005.onmicrosoft.com",
    "companyName": "DT Demo CSP Customer 005",
    "address": {
        "country": "US",
        "region": "WA",
        "city": "Redmond ",
        "addressLine1": "1 Microsoft Way",
        "postalCode": "98052",
        "phoneNumber": "4155551212"
    },
    "email": "daniel@hotmail.com.tw",
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/profiles/company",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "CustomerCompanyProfile"
    }
}
```
