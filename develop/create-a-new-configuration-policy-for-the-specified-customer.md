---
title: Een nieuw configuratie beleid voor klanten maken
description: Meer informatie over het gebruik van partner Center-Api's voor het maken van een nieuw configuratie beleid voor een opgegeven klant. Artikel bevat vereisten, stappen en voor beelden.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 21a0bfde7f931371ff09d6c27de0281a4ed3b3cb
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767647"
---
# <a name="create-a-new-configuration-policy-for-the-specified-customer"></a><span data-ttu-id="42536-104">Een nieuw configuratiebeleid maken voor de opgegeven klant</span><span class="sxs-lookup"><span data-stu-id="42536-104">Create a new configuration policy for the specified customer</span></span>

<span data-ttu-id="42536-105">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="42536-105">**Applies to:**</span></span>

- <span data-ttu-id="42536-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="42536-106">Partner Center</span></span>
- <span data-ttu-id="42536-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="42536-107">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="42536-108">Een nieuw configuratie beleid maken voor de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="42536-108">How to create a new configuration policy for the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="42536-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="42536-109">Prerequisites</span></span>

- <span data-ttu-id="42536-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="42536-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="42536-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="42536-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="42536-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="42536-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="42536-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="42536-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="42536-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="42536-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="42536-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="42536-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="42536-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="42536-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="42536-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="42536-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="42536-118">C\#</span><span class="sxs-lookup"><span data-stu-id="42536-118">C\#</span></span>

<span data-ttu-id="42536-119">Een nieuw configuratie beleid maken voor de opgegeven klant:</span><span class="sxs-lookup"><span data-stu-id="42536-119">To create a new configuration policy for the specified customer:</span></span>

1. <span data-ttu-id="42536-120">Exemplaar een nieuw [**ConfigurationPolicy**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) -object zoals wordt weer gegeven in het volgende code fragment.</span><span class="sxs-lookup"><span data-stu-id="42536-120">Instantiate a new [**ConfigurationPolicy**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) object as shown in the following code snippet.</span></span> <span data-ttu-id="42536-121">Roep vervolgens de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="42536-121">Then call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span>

2. <span data-ttu-id="42536-122">Haal de eigenschap [**ConfigurationPolicies**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.configurationpolicies) op om een interface voor het verzamelen van configuratie beleidsregels op te halen.</span><span class="sxs-lookup"><span data-stu-id="42536-122">Retrieve the [**ConfigurationPolicies**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.configurationpolicies) property to get an interface to configuration policy collection operations.</span></span>

3. <span data-ttu-id="42536-123">Roep de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) aan om het configuratie beleid te maken.</span><span class="sxs-lookup"><span data-stu-id="42536-123">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) method to create the configuration policy.</span></span>

### <a name="c-example"></a><span data-ttu-id="42536-124">C- \# voor beeld</span><span class="sxs-lookup"><span data-stu-id="42536-124">C\# example</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var configurationPolicyToCreate = new ConfigurationPolicy
{
    Name = "Test Config Policy",
    Description = "This configuration policy is created by the SDK samples",
    PolicySettings = new List<PolicySettingsType>() {
        PolicySettingsType.OobeUserNotLocalAdmin,
        PolicySettingsType.SkipEula }
};

var createdConfigurationPolicy =
    partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.Create(configurationPolicyToCreate);
```

<span data-ttu-id="42536-125">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="42536-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="42536-126">**Project**: Partner Center SDK-voor beelden **klasse**: CreateConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="42536-126">**Project**: Partner Center SDK Samples **Class**: CreateConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="42536-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="42536-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="42536-128">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="42536-128">Request syntax</span></span>

| <span data-ttu-id="42536-129">Methode</span><span class="sxs-lookup"><span data-stu-id="42536-129">Method</span></span>   | <span data-ttu-id="42536-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="42536-130">Request URI</span></span>                                                                              |
|----------|------------------------------------------------------------------------------------------|
| <span data-ttu-id="42536-131">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="42536-131">**POST**</span></span> | <span data-ttu-id="42536-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/policies http/1.1</span><span class="sxs-lookup"><span data-stu-id="42536-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="42536-133">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="42536-133">URI parameter</span></span>

<span data-ttu-id="42536-134">Gebruik de volgende Path-para meters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="42536-134">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="42536-135">Naam</span><span class="sxs-lookup"><span data-stu-id="42536-135">Name</span></span>        | <span data-ttu-id="42536-136">Type</span><span class="sxs-lookup"><span data-stu-id="42536-136">Type</span></span>   | <span data-ttu-id="42536-137">Vereist</span><span class="sxs-lookup"><span data-stu-id="42536-137">Required</span></span> | <span data-ttu-id="42536-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="42536-138">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="42536-139">klant-id</span><span class="sxs-lookup"><span data-stu-id="42536-139">customer-id</span></span> | <span data-ttu-id="42536-140">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="42536-140">string</span></span> | <span data-ttu-id="42536-141">Yes</span><span class="sxs-lookup"><span data-stu-id="42536-141">Yes</span></span>      | <span data-ttu-id="42536-142">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="42536-142">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="42536-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="42536-143">Request headers</span></span>

<span data-ttu-id="42536-144">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="42536-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="42536-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="42536-145">Request body</span></span>

<span data-ttu-id="42536-146">De aanvraag tekst moet een object met de informatie over het configuratie beleid bevatten, zoals wordt beschreven in de volgende tabel:</span><span class="sxs-lookup"><span data-stu-id="42536-146">The request body must contain an object with the configuration policy information as described in the following table:</span></span>

| <span data-ttu-id="42536-147">Naam</span><span class="sxs-lookup"><span data-stu-id="42536-147">Name</span></span>           | <span data-ttu-id="42536-148">Type</span><span class="sxs-lookup"><span data-stu-id="42536-148">Type</span></span>             | <span data-ttu-id="42536-149">Vereist</span><span class="sxs-lookup"><span data-stu-id="42536-149">Required</span></span> | <span data-ttu-id="42536-150">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="42536-150">Description</span></span>                      |
|----------------|------------------|----------|----------------------------------|
| <span data-ttu-id="42536-151">naam</span><span class="sxs-lookup"><span data-stu-id="42536-151">name</span></span>           | <span data-ttu-id="42536-152">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="42536-152">string</span></span>           | <span data-ttu-id="42536-153">Yes</span><span class="sxs-lookup"><span data-stu-id="42536-153">Yes</span></span>      | <span data-ttu-id="42536-154">De beschrijvende naam van het beleid.</span><span class="sxs-lookup"><span data-stu-id="42536-154">The friendly name of the policy.</span></span> |
| <span data-ttu-id="42536-155">category</span><span class="sxs-lookup"><span data-stu-id="42536-155">category</span></span>       | <span data-ttu-id="42536-156">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="42536-156">string</span></span>           | <span data-ttu-id="42536-157">Yes</span><span class="sxs-lookup"><span data-stu-id="42536-157">Yes</span></span>      | <span data-ttu-id="42536-158">De beleids categorie.</span><span class="sxs-lookup"><span data-stu-id="42536-158">The policy category.</span></span>             |
| <span data-ttu-id="42536-159">beschrijving</span><span class="sxs-lookup"><span data-stu-id="42536-159">description</span></span>    | <span data-ttu-id="42536-160">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="42536-160">string</span></span>           | <span data-ttu-id="42536-161">No</span><span class="sxs-lookup"><span data-stu-id="42536-161">No</span></span>       | <span data-ttu-id="42536-162">De beschrijving van het beleid.</span><span class="sxs-lookup"><span data-stu-id="42536-162">The policy description.</span></span>          |
| <span data-ttu-id="42536-163">policySettings</span><span class="sxs-lookup"><span data-stu-id="42536-163">policySettings</span></span> | <span data-ttu-id="42536-164">tekenreeksmatrix</span><span class="sxs-lookup"><span data-stu-id="42536-164">array of strings</span></span> | <span data-ttu-id="42536-165">Yes</span><span class="sxs-lookup"><span data-stu-id="42536-165">Yes</span></span>      | <span data-ttu-id="42536-166">De beleids instellingen.</span><span class="sxs-lookup"><span data-stu-id="42536-166">The policy settings.</span></span>             |

### <a name="request-example"></a><span data-ttu-id="42536-167">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="42536-167">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com//v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/policies HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Content-Length: 212
Content-Type: application/json
Host: api.partnercenter.microsoft.com

{
    "name": "Windows 10 Enterprise E5",
    "category": "o_o_b_e",
    "description": "test policy creation from API",
    "policySettings": ["oobe_user_not_local_admin", "skip_express_settings"]
}
```

## <a name="rest-response"></a><span data-ttu-id="42536-168">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="42536-168">REST response</span></span>

<span data-ttu-id="42536-169">Als dit lukt, bevat de antwoord tekst de [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) -resource voor het nieuwe beleid.</span><span class="sxs-lookup"><span data-stu-id="42536-169">If successful, the response body contains the [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) resource for the new policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="42536-170">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="42536-170">Response success and error codes</span></span>

<span data-ttu-id="42536-171">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="42536-171">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="42536-172">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="42536-172">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="42536-173">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="42536-173">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="42536-174">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="42536-174">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 404
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 4beda413-74fc-4839-b74f-f580c353ab45
MS-RequestId: 0dfadf74-aa66-49ed-9a67-b3b78d9297cc
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:07:36 GMT

{
    "id": "40cdb858-edcc-44d7-9083-d6a36d43bd3f",
    "name": "Windows 10 Enterprise E5",
    "category": "o_o_b_e",
    "description": "test policy creation from API",
    "devicesAssigned": 0,
    "policySettings": ["oobe_user_not_local_admin", "skip_express_settings"],
    "createdDate": "2017-07-25T18:07:36",
    "lastModifiedDate": "2017-07-25T18:07:36",
    "attributes": {
        "objectType": "ConfigurationPolicy"
    }
}
```
