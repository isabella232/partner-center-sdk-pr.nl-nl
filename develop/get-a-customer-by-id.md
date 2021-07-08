---
title: Een klant op basis van id ophalen
description: Haalt een klantresource op die overeenkomt met een klant-id.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 196d653c789c4b4e1327f0c6e5d2531a18681a71
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874989"
---
# <a name="get-a-customer-by-id"></a><span data-ttu-id="e263e-103">Een klant op basis van id ophalen</span><span class="sxs-lookup"><span data-stu-id="e263e-103">Get a customer by ID</span></span>

<span data-ttu-id="e263e-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e263e-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e263e-105">Haalt een **klantresource** op die overeenkomt met een klant-id.</span><span class="sxs-lookup"><span data-stu-id="e263e-105">Gets a **Customer** resource that corresponds to a customer ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e263e-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e263e-106">Prerequisites</span></span>

- <span data-ttu-id="e263e-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e263e-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e263e-108">Dit scenario ondersteunt app+gebruikersreferenties of verificatie alleen voor apps.</span><span class="sxs-lookup"><span data-stu-id="e263e-108">This scenario supports app+user credentials or app-only authentication.</span></span>

- <span data-ttu-id="e263e-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e263e-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e263e-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="e263e-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e263e-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="e263e-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e263e-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="e263e-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e263e-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="e263e-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e263e-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e263e-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="e263e-115">C\#</span><span class="sxs-lookup"><span data-stu-id="e263e-115">C\#</span></span>

<span data-ttu-id="e263e-116">Als u een klant wilt ophalen op id, gebruikt u de verzameling [**IAggregatePartner.Customers,**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) roept u de [**methode ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan en roept u vervolgens de methoden [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.get) of [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="e263e-116">To get a customer by ID, use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection, call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method, then call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerIdToRetrieve;

Customer customerInfo = partnerOperations.Customers.ById(customerIdToRetrieve).Get();
```

<span data-ttu-id="e263e-117">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="e263e-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="e263e-118">**Project:** Klasse PartnerSDK.FeatureSamples: CustomerInformation.cs </span><span class="sxs-lookup"><span data-stu-id="e263e-118">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerInformation.cs</span></span>

## <a name="java"></a><span data-ttu-id="e263e-119">Java</span><span class="sxs-lookup"><span data-stu-id="e263e-119">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="e263e-120">Als u een klant wilt op basis van de id, gebruikt u de functie **IAggregatePartner.getCustomers,** roept u de **functie byId()** aan en roept u vervolgens de **functie get()** aan.</span><span class="sxs-lookup"><span data-stu-id="e263e-120">To get a customer by ID, use your **IAggregatePartner.getCustomers** function, call the **byId()** function, then call the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerIdToRetrieve;

Customer customerInfo = partnerOperations.getCustomers().byId(customerIdToRetrieve).get();
```

## <a name="powershell"></a><span data-ttu-id="e263e-121">PowerShell</span><span class="sxs-lookup"><span data-stu-id="e263e-121">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="e263e-122">Als u een klant op id wilt krijgen, voert u [**de opdracht Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) uit en geeft u de parameter **CustomerId** op.</span><span class="sxs-lookup"><span data-stu-id="e263e-122">To get a customer by ID, execute the [**Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) command and specify the **CustomerId** parameter.</span></span>

```powershell
Get-PartnerCustomer -CustomerId '2ca7de6c-c05c-46b5-b689-32e53573a97a'
```

## <a name="rest-request"></a><span data-ttu-id="e263e-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e263e-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e263e-124">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e263e-124">Request syntax</span></span>

| <span data-ttu-id="e263e-125">Methode</span><span class="sxs-lookup"><span data-stu-id="e263e-125">Method</span></span>  | <span data-ttu-id="e263e-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e263e-126">Request URI</span></span>                                                                            |
|---------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="e263e-127">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e263e-127">**GET**</span></span> | <span data-ttu-id="e263e-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e263e-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="e263e-129">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="e263e-129">URI parameter</span></span>

<span data-ttu-id="e263e-130">Gebruik de volgende queryparameter voor een specifieke klant.</span><span class="sxs-lookup"><span data-stu-id="e263e-130">Use the following query parameter to a specific customer.</span></span>

| <span data-ttu-id="e263e-131">Naam</span><span class="sxs-lookup"><span data-stu-id="e263e-131">Name</span></span>                   | <span data-ttu-id="e263e-132">Type</span><span class="sxs-lookup"><span data-stu-id="e263e-132">Type</span></span>     | <span data-ttu-id="e263e-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="e263e-133">Required</span></span> | <span data-ttu-id="e263e-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e263e-134">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e263e-135">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="e263e-135">**customer-tenant-id**</span></span> | <span data-ttu-id="e263e-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="e263e-136">**guid**</span></span> | <span data-ttu-id="e263e-137">J</span><span class="sxs-lookup"><span data-stu-id="e263e-137">Y</span></span>        | <span data-ttu-id="e263e-138">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="e263e-138">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e263e-139">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e263e-139">Request headers</span></span>

<span data-ttu-id="e263e-140">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e263e-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e263e-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e263e-141">Request body</span></span>

<span data-ttu-id="e263e-142">Geen.</span><span class="sxs-lookup"><span data-stu-id="e263e-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e263e-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e263e-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: a176c585-b5de-4d65-824c-67a6deb45cd9
MS-RequestId: 74ca1db9-df92-41c6-a362-a16433b0542b
```

## <a name="rest-response"></a><span data-ttu-id="e263e-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e263e-144">REST response</span></span>

<span data-ttu-id="e263e-145">Als dit lukt, retourneert deze methode een [klantresource](customer-resources.md#customer) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="e263e-145">If successful, this method returns a [Customer](customer-resources.md#customer) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e263e-146">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e263e-146">Response success and error codes</span></span>

<span data-ttu-id="e263e-147">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e263e-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e263e-148">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e263e-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e263e-149">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="e263e-149">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e263e-150">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e263e-150">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1530
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a176c585-b5de-4d65-824c-67a6deb45cd9
MS-RequestId: 74ca1db9-df92-41c6-a362-a16433b0542b

{
  "id": "eebd1b55-5360-4438-a11d-5c06918c3014",
  "commerceId": "99e6a635-48e7-424d-9059-c9db944e3c54",
  "companyProfile": {
    "tenantId": "eebd1b55-5360-4438-a11d-5c06918c3014",
    "domain": "abcdefgh1234.ccsctp.net",
    "companyName": "1kl as kjk",
    "address": {
      "country": "US",
      "region": "wa",
      "city": "redmond",
      "addressLine1": "1 ms way",
      "postalCode": "98052",
      "phoneNumber": "1234567890"
    },
    "email": "a@a.com",
    "links": {
      "self": {
        "uri": "/customers/eebd1b55-5360-4438-a11d-5c06918c3014/profiles/company",
        "method": "GET",
        "headers": []
      }
    },
    "attributes": {
      "objectType": "CustomerCompanyProfile"
    }
  },
  "billingProfile": {
    "id": "eeada110-69d6-4cc9-b093-75feb7ca9d3f",
    "firstName": "d0d89d776d03471c819bf772191ed728",
    "lastName": "kjkAJJAAAAAAAAAAAAAAAAAAAA",
    "email": "a@a.com",
    "culture": "en-US",
    "language": "en",
    "companyName": "1kl as kjkAAAAAAAAAAAAAAAJJJJJJJJJJJAAAAAJJJJJJJJJJJAAJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJAJJJJJAJJAAAAJAJJAAAAAAAAAAAAAAAAAAAA",
    "defaultAddress": {
      "country": "US",
      "city": "redmond",
      "state": "WA",
      "addressLine1": "1 ms way",
      "postalCode": "98052",
      "firstName": "1kl as",
      "lastName": "kjk",
      "phoneNumber": "1234567890"
    },
    "links": {
      "self": {
        "uri": "/customers/eebd1b55-5360-4438-a11d-5c06918c3014/profiles/billing",
        "method": "GET",
        "headers": [

        ]
      }
    },
    "attributes": {
      "etag": "-4242348048554929329",
      "objectType": "CustomerBillingProfile"
    }
  },
  "relationshipToPartner": "reseller",
  "allowDelegatedAccess": true,
  "customDomains": [
    "abcdefgh1234.ccsctp.net"
  ],
  "links": {
    "self": {
      "uri": "/customers/eebd1b55-5360-4438-a11d-5c06918c3014",
      "method": "GET",
      "headers": []
    }
  },
  "attributes": {
    "objectType": "Customer"
  }
}
```
