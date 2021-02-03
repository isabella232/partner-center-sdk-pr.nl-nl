---
title: Een klant op basis van id ophalen
description: Hiermee wordt een klant resource opgehaald die overeenkomt met een klant-ID.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: dd4301dbb6f749b675fe624daf7f63751806f856
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767387"
---
# <a name="get-a-customer-by-id"></a><span data-ttu-id="b8c78-103">Een klant op basis van id ophalen</span><span class="sxs-lookup"><span data-stu-id="b8c78-103">Get a customer by ID</span></span>

<span data-ttu-id="b8c78-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="b8c78-104">**Applies To**</span></span>

- <span data-ttu-id="b8c78-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="b8c78-105">Partner Center</span></span>
- <span data-ttu-id="b8c78-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="b8c78-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="b8c78-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="b8c78-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="b8c78-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b8c78-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b8c78-109">Hiermee wordt een **klant** resource opgehaald die overeenkomt met een klant-id.</span><span class="sxs-lookup"><span data-stu-id="b8c78-109">Gets a **Customer** resource that corresponds to a customer ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b8c78-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b8c78-110">Prerequisites</span></span>

- <span data-ttu-id="b8c78-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b8c78-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b8c78-112">Dit scenario ondersteunt app + gebruikers referenties of alleen app-verificatie.</span><span class="sxs-lookup"><span data-stu-id="b8c78-112">This scenario supports app+user credentials or app-only authentication.</span></span>

- <span data-ttu-id="b8c78-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b8c78-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="b8c78-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="b8c78-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="b8c78-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="b8c78-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="b8c78-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="b8c78-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="b8c78-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="b8c78-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="b8c78-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b8c78-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="b8c78-119">C\#</span><span class="sxs-lookup"><span data-stu-id="b8c78-119">C\#</span></span>

<span data-ttu-id="b8c78-120">Als u een klant wilt ophalen op basis van de ID, gebruikt u de verzameling [**IAggregatePartner. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) , roept u de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan en roept u de methoden [**Get ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.get) of [**GetAsync (**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.getasync) ) aan.</span><span class="sxs-lookup"><span data-stu-id="b8c78-120">To get a customer by ID, use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection, call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method, then call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerIdToRetrieve;

Customer customerInfo = partnerOperations.Customers.ById(customerIdToRetrieve).Get();
```

<span data-ttu-id="b8c78-121">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="b8c78-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="b8c78-122">**Project**: PartnerSDK. FeatureSamples- **klasse**: CustomerInformation.cs</span><span class="sxs-lookup"><span data-stu-id="b8c78-122">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerInformation.cs</span></span>

## <a name="java"></a><span data-ttu-id="b8c78-123">Java</span><span class="sxs-lookup"><span data-stu-id="b8c78-123">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="b8c78-124">Als u een klant wilt ophalen op basis van de ID, gebruikt u de functie **IAggregatePartner. getCustomers** , roept u de functie **byId ()** aan en roept u vervolgens de functie **Get ()** aan.</span><span class="sxs-lookup"><span data-stu-id="b8c78-124">To get a customer by ID, use your **IAggregatePartner.getCustomers** function, call the **byId()** function, then call the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerIdToRetrieve;

Customer customerInfo = partnerOperations.getCustomers().byId(customerIdToRetrieve).get();
```

## <a name="powershell"></a><span data-ttu-id="b8c78-125">PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8c78-125">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="b8c78-126">Als u een klant wilt ophalen op basis van ID, voert u de opdracht [**Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) uit en geeft u de para meter **KlantId** op.</span><span class="sxs-lookup"><span data-stu-id="b8c78-126">To get a customer by ID, execute the [**Get-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomer.md) command and specify the **CustomerId** parameter.</span></span>

```powershell
Get-PartnerCustomer -CustomerId '2ca7de6c-c05c-46b5-b689-32e53573a97a'
```

## <a name="rest-request"></a><span data-ttu-id="b8c78-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="b8c78-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b8c78-128">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b8c78-128">Request syntax</span></span>

| <span data-ttu-id="b8c78-129">Methode</span><span class="sxs-lookup"><span data-stu-id="b8c78-129">Method</span></span>  | <span data-ttu-id="b8c78-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="b8c78-130">Request URI</span></span>                                                                            |
|---------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="b8c78-131">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="b8c78-131">**GET**</span></span> | <span data-ttu-id="b8c78-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="b8c78-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="b8c78-133">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="b8c78-133">URI parameter</span></span>

<span data-ttu-id="b8c78-134">Gebruik de volgende query parameter voor een specifieke klant.</span><span class="sxs-lookup"><span data-stu-id="b8c78-134">Use the following query parameter to a specific customer.</span></span>

| <span data-ttu-id="b8c78-135">Naam</span><span class="sxs-lookup"><span data-stu-id="b8c78-135">Name</span></span>                   | <span data-ttu-id="b8c78-136">Type</span><span class="sxs-lookup"><span data-stu-id="b8c78-136">Type</span></span>     | <span data-ttu-id="b8c78-137">Vereist</span><span class="sxs-lookup"><span data-stu-id="b8c78-137">Required</span></span> | <span data-ttu-id="b8c78-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b8c78-138">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b8c78-139">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="b8c78-139">**customer-tenant-id**</span></span> | <span data-ttu-id="b8c78-140">**guid**</span><span class="sxs-lookup"><span data-stu-id="b8c78-140">**guid**</span></span> | <span data-ttu-id="b8c78-141">J</span><span class="sxs-lookup"><span data-stu-id="b8c78-141">Y</span></span>        | <span data-ttu-id="b8c78-142">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="b8c78-142">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="b8c78-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="b8c78-143">Request headers</span></span>

<span data-ttu-id="b8c78-144">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b8c78-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b8c78-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="b8c78-145">Request body</span></span>

<span data-ttu-id="b8c78-146">Geen.</span><span class="sxs-lookup"><span data-stu-id="b8c78-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b8c78-147">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b8c78-147">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: a176c585-b5de-4d65-824c-67a6deb45cd9
MS-RequestId: 74ca1db9-df92-41c6-a362-a16433b0542b
```

## <a name="rest-response"></a><span data-ttu-id="b8c78-148">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="b8c78-148">REST response</span></span>

<span data-ttu-id="b8c78-149">Als dit lukt, retourneert deze methode een [klant](customer-resources.md#customer) resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="b8c78-149">If successful, this method returns a [Customer](customer-resources.md#customer) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b8c78-150">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="b8c78-150">Response success and error codes</span></span>

<span data-ttu-id="b8c78-151">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="b8c78-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b8c78-152">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="b8c78-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b8c78-153">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="b8c78-153">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b8c78-154">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="b8c78-154">Response example</span></span>

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
