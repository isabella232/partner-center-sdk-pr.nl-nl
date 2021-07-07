---
title: Een nieuw configuratiebeleid voor klanten maken
description: Meer informatie over het gebruik Partner Center API's om een nieuw configuratiebeleid te maken voor een opgegeven klant. Het artikel bevat vereisten, stappen en voorbeelden.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 530ff72862204bda093385252450f4eb81b63160
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973669"
---
# <a name="create-a-new-configuration-policy-for-the-specified-customer"></a><span data-ttu-id="90347-104">Een nieuw configuratiebeleid maken voor de opgegeven klant</span><span class="sxs-lookup"><span data-stu-id="90347-104">Create a new configuration policy for the specified customer</span></span>

<span data-ttu-id="90347-105">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="90347-105">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="90347-106">Een nieuw configuratiebeleid maken voor de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="90347-106">How to create a new configuration policy for the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="90347-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="90347-107">Prerequisites</span></span>

- <span data-ttu-id="90347-108">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="90347-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="90347-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="90347-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="90347-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="90347-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="90347-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="90347-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="90347-112">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="90347-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="90347-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="90347-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="90347-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="90347-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="90347-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="90347-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="90347-116">C\#</span><span class="sxs-lookup"><span data-stu-id="90347-116">C\#</span></span>

<span data-ttu-id="90347-117">Een nieuw configuratiebeleid maken voor de opgegeven klant:</span><span class="sxs-lookup"><span data-stu-id="90347-117">To create a new configuration policy for the specified customer:</span></span>

1. <span data-ttu-id="90347-118">Instantieer een nieuw [**ConfigurationPolicy-object,**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) zoals wordt weergegeven in het volgende codefragment.</span><span class="sxs-lookup"><span data-stu-id="90347-118">Instantiate a new [**ConfigurationPolicy**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) object as shown in the following code snippet.</span></span> <span data-ttu-id="90347-119">Roep vervolgens de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="90347-119">Then call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span>

2. <span data-ttu-id="90347-120">Haal de [**eigenschap ConfigurationPolicies op**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.configurationpolicies) om een interface op te halen voor bewerkingen voor het verzamelen van configuratiebeleid.</span><span class="sxs-lookup"><span data-stu-id="90347-120">Retrieve the [**ConfigurationPolicies**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.configurationpolicies) property to get an interface to configuration policy collection operations.</span></span>

3. <span data-ttu-id="90347-121">Roep de [**methode Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) of [**CreateAsync aan**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) om het configuratiebeleid te maken.</span><span class="sxs-lookup"><span data-stu-id="90347-121">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) method to create the configuration policy.</span></span>

### <a name="c-example"></a><span data-ttu-id="90347-122">\#C-voorbeeld</span><span class="sxs-lookup"><span data-stu-id="90347-122">C\# example</span></span>

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

<span data-ttu-id="90347-123">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="90347-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="90347-124">**Project**: Partnercentrum-SDK Samples **Class**: CreateConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="90347-124">**Project**: Partner Center SDK Samples **Class**: CreateConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="90347-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="90347-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="90347-126">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="90347-126">Request syntax</span></span>

| <span data-ttu-id="90347-127">Methode</span><span class="sxs-lookup"><span data-stu-id="90347-127">Method</span></span>   | <span data-ttu-id="90347-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="90347-128">Request URI</span></span>                                                                              |
|----------|------------------------------------------------------------------------------------------|
| <span data-ttu-id="90347-129">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="90347-129">**POST**</span></span> | <span data-ttu-id="90347-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="90347-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="90347-131">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="90347-131">URI parameter</span></span>

<span data-ttu-id="90347-132">Gebruik de volgende padparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="90347-132">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="90347-133">Naam</span><span class="sxs-lookup"><span data-stu-id="90347-133">Name</span></span>        | <span data-ttu-id="90347-134">Type</span><span class="sxs-lookup"><span data-stu-id="90347-134">Type</span></span>   | <span data-ttu-id="90347-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="90347-135">Required</span></span> | <span data-ttu-id="90347-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="90347-136">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="90347-137">customer-id</span><span class="sxs-lookup"><span data-stu-id="90347-137">customer-id</span></span> | <span data-ttu-id="90347-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90347-138">string</span></span> | <span data-ttu-id="90347-139">Ja</span><span class="sxs-lookup"><span data-stu-id="90347-139">Yes</span></span>      | <span data-ttu-id="90347-140">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="90347-140">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="90347-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="90347-141">Request headers</span></span>

<span data-ttu-id="90347-142">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="90347-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="90347-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="90347-143">Request body</span></span>

<span data-ttu-id="90347-144">De aanvraag body moet een object bevatten met de configuratiebeleidsgegevens zoals beschreven in de volgende tabel:</span><span class="sxs-lookup"><span data-stu-id="90347-144">The request body must contain an object with the configuration policy information as described in the following table:</span></span>

| <span data-ttu-id="90347-145">Naam</span><span class="sxs-lookup"><span data-stu-id="90347-145">Name</span></span>           | <span data-ttu-id="90347-146">Type</span><span class="sxs-lookup"><span data-stu-id="90347-146">Type</span></span>             | <span data-ttu-id="90347-147">Vereist</span><span class="sxs-lookup"><span data-stu-id="90347-147">Required</span></span> | <span data-ttu-id="90347-148">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="90347-148">Description</span></span>                      |
|----------------|------------------|----------|----------------------------------|
| <span data-ttu-id="90347-149">naam</span><span class="sxs-lookup"><span data-stu-id="90347-149">name</span></span>           | <span data-ttu-id="90347-150">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90347-150">string</span></span>           | <span data-ttu-id="90347-151">Ja</span><span class="sxs-lookup"><span data-stu-id="90347-151">Yes</span></span>      | <span data-ttu-id="90347-152">De gebruiksvriendelijke naam van het beleid.</span><span class="sxs-lookup"><span data-stu-id="90347-152">The friendly name of the policy.</span></span> |
| <span data-ttu-id="90347-153">category</span><span class="sxs-lookup"><span data-stu-id="90347-153">category</span></span>       | <span data-ttu-id="90347-154">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90347-154">string</span></span>           | <span data-ttu-id="90347-155">Ja</span><span class="sxs-lookup"><span data-stu-id="90347-155">Yes</span></span>      | <span data-ttu-id="90347-156">De beleidscategorie.</span><span class="sxs-lookup"><span data-stu-id="90347-156">The policy category.</span></span>             |
| <span data-ttu-id="90347-157">beschrijving</span><span class="sxs-lookup"><span data-stu-id="90347-157">description</span></span>    | <span data-ttu-id="90347-158">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90347-158">string</span></span>           | <span data-ttu-id="90347-159">No</span><span class="sxs-lookup"><span data-stu-id="90347-159">No</span></span>       | <span data-ttu-id="90347-160">De beschrijving van het beleid.</span><span class="sxs-lookup"><span data-stu-id="90347-160">The policy description.</span></span>          |
| <span data-ttu-id="90347-161">policySettings</span><span class="sxs-lookup"><span data-stu-id="90347-161">policySettings</span></span> | <span data-ttu-id="90347-162">tekenreeksmatrix</span><span class="sxs-lookup"><span data-stu-id="90347-162">array of strings</span></span> | <span data-ttu-id="90347-163">Ja</span><span class="sxs-lookup"><span data-stu-id="90347-163">Yes</span></span>      | <span data-ttu-id="90347-164">De beleidsinstellingen.</span><span class="sxs-lookup"><span data-stu-id="90347-164">The policy settings.</span></span>             |

### <a name="request-example"></a><span data-ttu-id="90347-165">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="90347-165">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="90347-166">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="90347-166">REST response</span></span>

<span data-ttu-id="90347-167">Als dit lukt, bevat de antwoord-body de [ConfigurationPolicy-resource](device-deployment-resources.md#configurationpolicy) voor het nieuwe beleid.</span><span class="sxs-lookup"><span data-stu-id="90347-167">If successful, the response body contains the [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) resource for the new policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="90347-168">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="90347-168">Response success and error codes</span></span>

<span data-ttu-id="90347-169">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="90347-169">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="90347-170">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="90347-170">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="90347-171">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="90347-171">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="90347-172">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="90347-172">Response example</span></span>

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
