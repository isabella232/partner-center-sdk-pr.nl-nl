---
title: Het configuratiebeleid van een klant ophalen
description: Het opgegeven configuratie beleid voor de opgegeven klant ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8d5d4ee83d1a66f33872d8b1f1327f47eeb4465e
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767524"
---
# <a name="retrieve-a-customers-configuration-policy"></a><span data-ttu-id="2e12f-103">Het configuratiebeleid van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="2e12f-103">Retrieve a customer's configuration policy</span></span>

<span data-ttu-id="2e12f-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="2e12f-104">**Applies To**</span></span>

- <span data-ttu-id="2e12f-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="2e12f-105">Partner Center</span></span>
- <span data-ttu-id="2e12f-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="2e12f-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="2e12f-107">Het opgegeven configuratie beleid voor de opgegeven klant ophalen.</span><span class="sxs-lookup"><span data-stu-id="2e12f-107">How to retrieve the specified configuration policy for the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2e12f-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2e12f-108">Prerequisites</span></span>

- <span data-ttu-id="2e12f-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2e12f-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2e12f-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="2e12f-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="2e12f-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2e12f-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="2e12f-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="2e12f-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="2e12f-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="2e12f-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="2e12f-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="2e12f-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="2e12f-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="2e12f-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="2e12f-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2e12f-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="2e12f-117">De beleids-id.</span><span class="sxs-lookup"><span data-stu-id="2e12f-117">The policy identifier.</span></span>

## <a name="c"></a><span data-ttu-id="2e12f-118">C\#</span><span class="sxs-lookup"><span data-stu-id="2e12f-118">C\#</span></span>

<span data-ttu-id="2e12f-119">Als u een configuratie beleid wilt ophalen voor de opgegeven klant, roept u eerst de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="2e12f-119">To retrieve a configuration policy for the specified customer, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="2e12f-120">Vervolgens roept u de methode [**ConfigurationPolicies. ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) aan met de beleids-id om een interface op te halen voor configuratie beleids bewerkingen voor het opgegeven beleid.</span><span class="sxs-lookup"><span data-stu-id="2e12f-120">Next, call the [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) method with the policy ID to retrieve an interface to configuration policy operations for the specified policy.</span></span> <span data-ttu-id="2e12f-121">Roep ten slotte de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.getasync) aan om het configuratie beleid op te halen.</span><span class="sxs-lookup"><span data-stu-id="2e12f-121">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.getasync) method to retrieve the configuration policy.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedConfigurationPolicyId;

ConfigurationPolicy retrievedConfigurationPolicy =
    partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.ById(selectedConfigurationPolicyId).Get();
```

<span data-ttu-id="2e12f-122">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="2e12f-122">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="2e12f-123">**Project**: Partner Center SDK-voor beelden **klasse**: GetConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="2e12f-123">**Project**: Partner Center SDK Samples **Class**: GetConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="2e12f-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="2e12f-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2e12f-125">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2e12f-125">Request syntax</span></span>

| <span data-ttu-id="2e12f-126">Methode</span><span class="sxs-lookup"><span data-stu-id="2e12f-126">Method</span></span>  | <span data-ttu-id="2e12f-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="2e12f-127">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2e12f-128">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="2e12f-128">**GET**</span></span> | <span data-ttu-id="2e12f-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/policies/{Policy-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="2e12f-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="2e12f-130">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="2e12f-130">URI parameter</span></span>

<span data-ttu-id="2e12f-131">Gebruik de volgende pad-en query parameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="2e12f-131">Use the following path and query parameters when creating the request.</span></span>

| <span data-ttu-id="2e12f-132">Naam</span><span class="sxs-lookup"><span data-stu-id="2e12f-132">Name</span></span>        | <span data-ttu-id="2e12f-133">Type</span><span class="sxs-lookup"><span data-stu-id="2e12f-133">Type</span></span>   | <span data-ttu-id="2e12f-134">Vereist</span><span class="sxs-lookup"><span data-stu-id="2e12f-134">Required</span></span> | <span data-ttu-id="2e12f-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2e12f-135">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="2e12f-136">klant-id</span><span class="sxs-lookup"><span data-stu-id="2e12f-136">customer-id</span></span> | <span data-ttu-id="2e12f-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2e12f-137">string</span></span> | <span data-ttu-id="2e12f-138">Yes</span><span class="sxs-lookup"><span data-stu-id="2e12f-138">Yes</span></span>      | <span data-ttu-id="2e12f-139">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="2e12f-139">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="2e12f-140">beleid-id</span><span class="sxs-lookup"><span data-stu-id="2e12f-140">policy-id</span></span>   | <span data-ttu-id="2e12f-141">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2e12f-141">string</span></span> | <span data-ttu-id="2e12f-142">Yes</span><span class="sxs-lookup"><span data-stu-id="2e12f-142">Yes</span></span>      | <span data-ttu-id="2e12f-143">Een teken reeks met een GUID-indeling waarmee het beleid wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="2e12f-143">A GUID-formatted string that identifies the policy.</span></span>   |

### <a name="request-headers"></a><span data-ttu-id="2e12f-144">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="2e12f-144">Request headers</span></span>

<span data-ttu-id="2e12f-145">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2e12f-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2e12f-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="2e12f-146">Request body</span></span>

<span data-ttu-id="2e12f-147">Geen</span><span class="sxs-lookup"><span data-stu-id="2e12f-147">None</span></span>

### <a name="request-example"></a><span data-ttu-id="2e12f-148">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2e12f-148">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/policies/56edf752-ee77-4fd8-b7f5-df1f74a3a9ac HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Content-Length: 0
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="2e12f-149">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="2e12f-149">REST response</span></span>

<span data-ttu-id="2e12f-150">Als dit is gelukt, bevat het antwoord de aangevraagde [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) -resource.</span><span class="sxs-lookup"><span data-stu-id="2e12f-150">If successful, the response contains the requested [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2e12f-151">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="2e12f-151">Response success and error codes</span></span>

<span data-ttu-id="2e12f-152">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="2e12f-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2e12f-153">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="2e12f-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2e12f-154">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="2e12f-154">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2e12f-155">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="2e12f-155">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 443
MS-CorrelationId: abe150cf-c677-435c-b5d5-b34899a6d1ec
MS-RequestId: ab3abfe7-dce7-46c0-ab20-4fd49bc3e2f7
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:08:27 GMT

{
    "id": "56edf752-ee77-4fd8-b7f5-df1f74a3a9ac",
    "name": "Test policy",
    "category": "o_o_b_e",
    "description": "Test policy creation from API 1",
    "devicesAssigned": 0,
    "policySettings": ["skip_express_settings"],
    "createdDate": "2017-07-25T11:03:03.8457116-07:00",
    "lastModifiedDate": "2017-07-25T11:04:00.8149974-07:00",
    "attributes": {
        "objectType": "ConfigurationPolicy"
    }
}
```
