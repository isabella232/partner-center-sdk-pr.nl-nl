---
title: Het configuratiebeleid van een klant ophalen
description: Het opgegeven configuratiebeleid voor de opgegeven klant ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f9a8cb435c63d8d02c3b4633abc8723353116f37
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547492"
---
# <a name="retrieve-a-customers-configuration-policy"></a><span data-ttu-id="e2403-103">Het configuratiebeleid van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="e2403-103">Retrieve a customer's configuration policy</span></span>

<span data-ttu-id="e2403-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="e2403-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="e2403-105">Het opgegeven configuratiebeleid voor de opgegeven klant ophalen.</span><span class="sxs-lookup"><span data-stu-id="e2403-105">How to retrieve the specified configuration policy for the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e2403-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e2403-106">Prerequisites</span></span>

- <span data-ttu-id="e2403-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e2403-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e2403-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="e2403-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="e2403-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e2403-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e2403-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="e2403-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e2403-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="e2403-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e2403-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="e2403-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e2403-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="e2403-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e2403-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e2403-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="e2403-115">De beleids-id.</span><span class="sxs-lookup"><span data-stu-id="e2403-115">The policy identifier.</span></span>

## <a name="c"></a><span data-ttu-id="e2403-116">C\#</span><span class="sxs-lookup"><span data-stu-id="e2403-116">C\#</span></span>

<span data-ttu-id="e2403-117">Als u een configuratiebeleid voor de opgegeven klant wilt ophalen, roept u eerst de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="e2403-117">To retrieve a configuration policy for the specified customer, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="e2403-118">Roep vervolgens de [**methode ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) aan met de beleids-id om een interface op te halen voor configuratiebeleidsbewerkingen voor het opgegeven beleid.</span><span class="sxs-lookup"><span data-stu-id="e2403-118">Next, call the [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) method with the policy ID to retrieve an interface to configuration policy operations for the specified policy.</span></span> <span data-ttu-id="e2403-119">Roep ten slotte de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.getasync) om het configuratiebeleid op te halen.</span><span class="sxs-lookup"><span data-stu-id="e2403-119">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.getasync) method to retrieve the configuration policy.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedConfigurationPolicyId;

ConfigurationPolicy retrievedConfigurationPolicy =
    partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.ById(selectedConfigurationPolicyId).Get();
```

<span data-ttu-id="e2403-120">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="e2403-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="e2403-121">**Project**: Partnercentrum-SDK Samples **Class:** GetConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="e2403-121">**Project**: Partner Center SDK Samples **Class**: GetConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="e2403-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e2403-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e2403-123">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e2403-123">Request syntax</span></span>

| <span data-ttu-id="e2403-124">Methode</span><span class="sxs-lookup"><span data-stu-id="e2403-124">Method</span></span>  | <span data-ttu-id="e2403-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e2403-125">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e2403-126">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e2403-126">**GET**</span></span> | <span data-ttu-id="e2403-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e2403-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="e2403-128">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="e2403-128">URI parameter</span></span>

<span data-ttu-id="e2403-129">Gebruik het volgende pad en de queryparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="e2403-129">Use the following path and query parameters when creating the request.</span></span>

| <span data-ttu-id="e2403-130">Naam</span><span class="sxs-lookup"><span data-stu-id="e2403-130">Name</span></span>        | <span data-ttu-id="e2403-131">Type</span><span class="sxs-lookup"><span data-stu-id="e2403-131">Type</span></span>   | <span data-ttu-id="e2403-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="e2403-132">Required</span></span> | <span data-ttu-id="e2403-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e2403-133">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="e2403-134">customer-id</span><span class="sxs-lookup"><span data-stu-id="e2403-134">customer-id</span></span> | <span data-ttu-id="e2403-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e2403-135">string</span></span> | <span data-ttu-id="e2403-136">Ja</span><span class="sxs-lookup"><span data-stu-id="e2403-136">Yes</span></span>      | <span data-ttu-id="e2403-137">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="e2403-137">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="e2403-138">policy-id</span><span class="sxs-lookup"><span data-stu-id="e2403-138">policy-id</span></span>   | <span data-ttu-id="e2403-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e2403-139">string</span></span> | <span data-ttu-id="e2403-140">Ja</span><span class="sxs-lookup"><span data-stu-id="e2403-140">Yes</span></span>      | <span data-ttu-id="e2403-141">Een tekenreeks met GUID-indeling die het beleid identificeert.</span><span class="sxs-lookup"><span data-stu-id="e2403-141">A GUID-formatted string that identifies the policy.</span></span>   |

### <a name="request-headers"></a><span data-ttu-id="e2403-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e2403-142">Request headers</span></span>

<span data-ttu-id="e2403-143">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e2403-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e2403-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e2403-144">Request body</span></span>

<span data-ttu-id="e2403-145">Geen</span><span class="sxs-lookup"><span data-stu-id="e2403-145">None</span></span>

### <a name="request-example"></a><span data-ttu-id="e2403-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e2403-146">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="e2403-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e2403-147">REST response</span></span>

<span data-ttu-id="e2403-148">Als dit lukt, bevat het antwoord de [aangevraagde ConfigurationPolicy-resource.](device-deployment-resources.md#configurationpolicy)</span><span class="sxs-lookup"><span data-stu-id="e2403-148">If successful, the response contains the requested [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e2403-149">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e2403-149">Response success and error codes</span></span>

<span data-ttu-id="e2403-150">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e2403-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e2403-151">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e2403-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e2403-152">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="e2403-152">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e2403-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e2403-153">Response example</span></span>

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
