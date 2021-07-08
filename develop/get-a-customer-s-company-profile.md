---
title: Een bedrijfsprofiel van een klant ophalen
description: Haalt het bedrijfsprofiel van een klant op.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: a1c0c8401207f4b0bb33755a8eabc66de0ad9ff9
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874972"
---
# <a name="get-a-customers-company-profile"></a><span data-ttu-id="ccbbc-103">Een bedrijfsprofiel van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="ccbbc-103">Get a customer's company profile</span></span>

<span data-ttu-id="ccbbc-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="ccbbc-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="ccbbc-105">Haalt het bedrijfsprofiel van een klant op.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-105">Gets the company profile of a customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ccbbc-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ccbbc-106">Prerequisites</span></span>

- <span data-ttu-id="ccbbc-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ccbbc-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ccbbc-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="ccbbc-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ccbbc-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="ccbbc-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="ccbbc-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="ccbbc-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="ccbbc-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="ccbbc-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="ccbbc-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="ccbbc-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="ccbbc-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ccbbc-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="ccbbc-115">C\#</span><span class="sxs-lookup"><span data-stu-id="ccbbc-115">C\#</span></span>

<span data-ttu-id="ccbbc-116">Als u het bedrijfsprofiel voor een klant wilt op halen, roept u de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-116">To get the company profile for a customer, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="ccbbc-117">Haal vervolgens de [**ICustomerProfileCollection-interface**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection) van de klant op uit de eigenschap [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) om toegang te krijgen tot de bedrijfseigenschap.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-117">Then get the customer's [**ICustomerProfileCollection**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection) interface from the [**Profiles**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.profiles) property, in order to access its Company property.</span></span> <span data-ttu-id="ccbbc-118">Haal vervolgens de [**interface ICustomerReadonlyProfile**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1) op uit de eigenschap [**ICustomerProfileCollection.Company**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.company) en roep de [**methoden Get()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) of [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-118">Next, get the [**ICustomerReadonlyProfile**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1) interface from the [**ICustomerProfileCollection.Company**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerprofilecollection.company) property, and call its [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.profiles.icustomerreadonlyprofile-1.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

var companyProfile = partnerOperations.Customers.ById(customerId).Profiles.Company.Get();
```

<span data-ttu-id="ccbbc-119">**Voorbeeld:** [download de Partnercentrum-SDK](https://go.microsoft.com/fwlink/p/?LinkId=746681).</span><span class="sxs-lookup"><span data-stu-id="ccbbc-119">**Sample**: [Download the Partner Center SDK](https://go.microsoft.com/fwlink/p/?LinkId=746681).</span></span> <span data-ttu-id="ccbbc-120">**Project:** Klasse PartnerSdk.FeatureSamples: GetCustomerCompanyProfile.cs </span><span class="sxs-lookup"><span data-stu-id="ccbbc-120">**Project**: PartnerSdk.FeatureSamples **Class**: GetCustomerCompanyProfile.cs</span></span>

## <a name="java"></a><span data-ttu-id="ccbbc-121">Java</span><span class="sxs-lookup"><span data-stu-id="ccbbc-121">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="ccbbc-122">Als u het bedrijfsprofiel voor een klant wilt op halen, roept u de functie **IAggregatePartner.getCustomers().byId** aan met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-122">To get the company profile for a customer, call the **IAggregatePartner.getCustomers().byId** function with the customer identifier to identify the customer.</span></span> <span data-ttu-id="ccbbc-123">Haal vervolgens de **ICustomerProfileCollection-interface** van de klant op uit de functie [**getProfiles**] om toegang te krijgen tot de bedrijfseigenschap.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-123">Then get the customer's **ICustomerProfileCollection** interface from the [**getProfiles**] function, in order to access its Company property.</span></span> <span data-ttu-id="ccbbc-124">Haal vervolgens de **interface ICustomerReadonlyProfile** op uit de functie **ICustomerProfileCollection.getCompany** en roep de **functie get** aan.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-124">Next, get the **ICustomerReadonlyProfile** interface from the **ICustomerProfileCollection.getCompany** function, and call the **get** function.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;

CustomerCompanyProfile companyProfile = partnerOperations.getCustomers().byId(customerId).getProfiles().getCompany().get();
```

## <a name="rest-request"></a><span data-ttu-id="ccbbc-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="ccbbc-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ccbbc-126">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="ccbbc-126">Request syntax</span></span>

| <span data-ttu-id="ccbbc-127">Methode</span><span class="sxs-lookup"><span data-stu-id="ccbbc-127">Method</span></span>  | <span data-ttu-id="ccbbc-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="ccbbc-128">Request URI</span></span>                                                             |
|---------|-------------------------------------------------------------------------|
| <span data-ttu-id="ccbbc-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ccbbc-129">**GET**</span></span> | <span data-ttu-id="ccbbc-130">*{baseURL}*/v1/customers/{customer-tenant-id}/profiles/company HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ccbbc-130">*{baseURL}*/v1/customers/{customer-tenant-id}/profiles/company HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="ccbbc-131">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="ccbbc-131">URI parameter</span></span>

<span data-ttu-id="ccbbc-132">Gebruik de volgende queryparameter om het bedrijfsprofiel op te halen.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-132">Use the following query parameter to get the company profile.</span></span>

| <span data-ttu-id="ccbbc-133">Naam</span><span class="sxs-lookup"><span data-stu-id="ccbbc-133">Name</span></span>                   | <span data-ttu-id="ccbbc-134">Type</span><span class="sxs-lookup"><span data-stu-id="ccbbc-134">Type</span></span>     | <span data-ttu-id="ccbbc-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="ccbbc-135">Required</span></span> | <span data-ttu-id="ccbbc-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ccbbc-136">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ccbbc-137">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="ccbbc-137">**customer-tenant-id**</span></span> | <span data-ttu-id="ccbbc-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="ccbbc-138">**guid**</span></span> | <span data-ttu-id="ccbbc-139">J</span><span class="sxs-lookup"><span data-stu-id="ccbbc-139">Y</span></span>        | <span data-ttu-id="ccbbc-140">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-140">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ccbbc-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ccbbc-141">Request headers</span></span>

<span data-ttu-id="ccbbc-142">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="ccbbc-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ccbbc-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="ccbbc-143">Request body</span></span>

<span data-ttu-id="ccbbc-144">Geen</span><span class="sxs-lookup"><span data-stu-id="ccbbc-144">None</span></span>

### <a name="request-example"></a><span data-ttu-id="ccbbc-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ccbbc-145">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="ccbbc-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="ccbbc-146">REST response</span></span>

<span data-ttu-id="ccbbc-147">Als dit lukt, retourneert deze methode informatie in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-147">If successful, this method returns information in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ccbbc-148">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="ccbbc-148">Response success and error codes</span></span>

<span data-ttu-id="ccbbc-149">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ccbbc-150">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="ccbbc-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ccbbc-151">Zie REST-foutcodes voor [Partner Center de volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="ccbbc-151">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ccbbc-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="ccbbc-152">Response example</span></span>

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
