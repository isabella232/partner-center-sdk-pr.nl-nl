---
title: Een configuratiebeleid bijwerken voor de opgegeven klant
description: Het opgegeven configuratie beleid voor de opgegeven klant bijwerken.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 42c57a92020723415b4621e9f9d7c5c3278bfb77
ms.sourcegitcommit: 970031473b2e8cd3d08c6c097949c057a51df3ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505336"
---
# <a name="update-a-configuration-policy-for-the-specified-customer"></a><span data-ttu-id="45384-103">Een configuratiebeleid bijwerken voor de opgegeven klant</span><span class="sxs-lookup"><span data-stu-id="45384-103">Update a configuration policy for the specified customer</span></span>

<span data-ttu-id="45384-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="45384-104">**Applies To**</span></span>

- <span data-ttu-id="45384-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="45384-105">Partner Center</span></span>
- <span data-ttu-id="45384-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="45384-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="45384-107">Het opgegeven configuratie beleid voor de opgegeven klant bijwerken.</span><span class="sxs-lookup"><span data-stu-id="45384-107">How to update the specified configuration policy for the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="45384-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="45384-108">Prerequisites</span></span>

- <span data-ttu-id="45384-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="45384-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="45384-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="45384-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="45384-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="45384-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="45384-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="45384-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="45384-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="45384-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="45384-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="45384-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="45384-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="45384-115">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="45384-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="45384-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="45384-117">De beleids-id.</span><span class="sxs-lookup"><span data-stu-id="45384-117">The policy identifier.</span></span>

## <a name="c"></a><span data-ttu-id="45384-118">C\#</span><span class="sxs-lookup"><span data-stu-id="45384-118">C\#</span></span>

<span data-ttu-id="45384-119">Als u een bestaand configuratie beleid voor de opgegeven klant wilt bijwerken, moet u een nieuw [**ConfigurationPolicy**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) -object instantiëren, zoals wordt weer gegeven in het volgende code fragment.</span><span class="sxs-lookup"><span data-stu-id="45384-119">To update an existing configuration policy for the specified customer, instantiate a new [**ConfigurationPolicy**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) object as shown in the following code snippet.</span></span> <span data-ttu-id="45384-120">De waarden in dit nieuwe object vervangen de overeenkomende waarden in het bestaande object.</span><span class="sxs-lookup"><span data-stu-id="45384-120">The values in this new object replace the corresponding values in the existing object.</span></span> <span data-ttu-id="45384-121">Vervolgens roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="45384-121">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="45384-122">Vervolgens roept u de methode [**ConfigurationPolicies. ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) aan met de beleids-id om een interface op te halen voor configuratie beleids bewerkingen voor het opgegeven beleid.</span><span class="sxs-lookup"><span data-stu-id="45384-122">Next, call the [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) method with the policy ID to retrieve an interface to configuration policy operations for the specified policy.</span></span> <span data-ttu-id="45384-123">Roep ten slotte de [**patch**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patch) -of [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patchasync) -methode aan om het configuratie beleid bij te werken.</span><span class="sxs-lookup"><span data-stu-id="45384-123">Finally, call the [**Patch**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patch) or [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patchasync) method to update the configuration policy.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedConfigurationPolicyId;

ConfigurationPolicy configPolicyToBeUpdated = new ConfigurationPolicy()
{
    Name= "Test Config Policy",
    Id = selectedConfigurationPolicyId,
    PolicySettings = new List<PolicySettingsType>() {
        PolicySettingsType.OobeUserNotLocalAdmin,
        PolicySettingsType.RemoveOemPreinstalls }
};

ConfigurationPolicy updatedConfigurationPolicy =
    partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.ById(selectedConfigurationPolicyId).Patch(configPolicyToBeUpdated);
```

<span data-ttu-id="45384-124">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="45384-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="45384-125">**Project**: Partner Center SDK-voor beelden **klasse**: UpdateConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="45384-125">**Project**: Partner Center SDK Samples **Class**: UpdateConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="45384-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="45384-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="45384-127">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="45384-127">Request syntax</span></span>

| <span data-ttu-id="45384-128">Methode</span><span class="sxs-lookup"><span data-stu-id="45384-128">Method</span></span>  | <span data-ttu-id="45384-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="45384-129">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="45384-130">**PUT**</span><span class="sxs-lookup"><span data-stu-id="45384-130">**PUT**</span></span> | <span data-ttu-id="45384-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/policies/{Policy-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="45384-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="45384-132">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="45384-132">URI parameter</span></span>

<span data-ttu-id="45384-133">Gebruik de volgende Path-para meters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="45384-133">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="45384-134">Naam</span><span class="sxs-lookup"><span data-stu-id="45384-134">Name</span></span>        | <span data-ttu-id="45384-135">Type</span><span class="sxs-lookup"><span data-stu-id="45384-135">Type</span></span>   | <span data-ttu-id="45384-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="45384-136">Required</span></span> | <span data-ttu-id="45384-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="45384-137">Description</span></span>                                                   |
|-------------|--------|----------|---------------------------------------------------------------|
| <span data-ttu-id="45384-138">klant-id</span><span class="sxs-lookup"><span data-stu-id="45384-138">customer-id</span></span> | <span data-ttu-id="45384-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="45384-139">string</span></span> | <span data-ttu-id="45384-140">Ja</span><span class="sxs-lookup"><span data-stu-id="45384-140">Yes</span></span>      | <span data-ttu-id="45384-141">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="45384-141">A GUID-formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="45384-142">beleid-id</span><span class="sxs-lookup"><span data-stu-id="45384-142">policy-id</span></span>   | <span data-ttu-id="45384-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="45384-143">string</span></span> | <span data-ttu-id="45384-144">Ja</span><span class="sxs-lookup"><span data-stu-id="45384-144">Yes</span></span>      | <span data-ttu-id="45384-145">Een teken reeks met een GUID-indeling die het beleid identificeert dat moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="45384-145">A GUID-formatted string that identifies the policy to update.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="45384-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="45384-146">Request headers</span></span>

<span data-ttu-id="45384-147">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="45384-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="45384-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="45384-148">Request body</span></span>

<span data-ttu-id="45384-149">De aanvraag tekst moet een object bevatten dat de beleids gegevens levert.</span><span class="sxs-lookup"><span data-stu-id="45384-149">The request body must contain an object that provides the policy information.</span></span>

| <span data-ttu-id="45384-150">Naam</span><span class="sxs-lookup"><span data-stu-id="45384-150">Name</span></span>            | <span data-ttu-id="45384-151">Type</span><span class="sxs-lookup"><span data-stu-id="45384-151">Type</span></span>             | <span data-ttu-id="45384-152">Vereist</span><span class="sxs-lookup"><span data-stu-id="45384-152">Required</span></span> | <span data-ttu-id="45384-153">Worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="45384-153">Updatable</span></span> | <span data-ttu-id="45384-154">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="45384-154">Description</span></span>                                                                                                                                              |
|-----------------|------------------|----------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="45384-155">id</span><span class="sxs-lookup"><span data-stu-id="45384-155">id</span></span>              | <span data-ttu-id="45384-156">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="45384-156">string</span></span>           | <span data-ttu-id="45384-157">Ja</span><span class="sxs-lookup"><span data-stu-id="45384-157">Yes</span></span>      | <span data-ttu-id="45384-158">Nee</span><span class="sxs-lookup"><span data-stu-id="45384-158">No</span></span>        | <span data-ttu-id="45384-159">De teken reeks met de GUID-indeling waarmee het beleid wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="45384-159">The GUID-formatted string that identifies the policy.</span></span>                                                                                                    |
| <span data-ttu-id="45384-160">naam</span><span class="sxs-lookup"><span data-stu-id="45384-160">name</span></span>            | <span data-ttu-id="45384-161">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="45384-161">string</span></span>           | <span data-ttu-id="45384-162">Ja</span><span class="sxs-lookup"><span data-stu-id="45384-162">Yes</span></span>      | <span data-ttu-id="45384-163">Ja</span><span class="sxs-lookup"><span data-stu-id="45384-163">Yes</span></span>       | <span data-ttu-id="45384-164">De beschrijvende naam van het beleid.</span><span class="sxs-lookup"><span data-stu-id="45384-164">The friendly name of the policy.</span></span>                                                                                                                         |
| <span data-ttu-id="45384-165">category</span><span class="sxs-lookup"><span data-stu-id="45384-165">category</span></span>        | <span data-ttu-id="45384-166">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="45384-166">string</span></span>           | <span data-ttu-id="45384-167">Ja</span><span class="sxs-lookup"><span data-stu-id="45384-167">Yes</span></span>      | <span data-ttu-id="45384-168">Nee</span><span class="sxs-lookup"><span data-stu-id="45384-168">No</span></span>        | <span data-ttu-id="45384-169">De beleids categorie.</span><span class="sxs-lookup"><span data-stu-id="45384-169">The policy category.</span></span>                                                                                                                                     |
| <span data-ttu-id="45384-170">beschrijving</span><span class="sxs-lookup"><span data-stu-id="45384-170">description</span></span>     | <span data-ttu-id="45384-171">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="45384-171">string</span></span>           | <span data-ttu-id="45384-172">Nee</span><span class="sxs-lookup"><span data-stu-id="45384-172">No</span></span>       | <span data-ttu-id="45384-173">Ja</span><span class="sxs-lookup"><span data-stu-id="45384-173">Yes</span></span>       | <span data-ttu-id="45384-174">De beschrijving van het beleid.</span><span class="sxs-lookup"><span data-stu-id="45384-174">The policy description.</span></span>                                                                                                                                  |
| <span data-ttu-id="45384-175">devicesAssigned</span><span class="sxs-lookup"><span data-stu-id="45384-175">devicesAssigned</span></span> | <span data-ttu-id="45384-176">getal</span><span class="sxs-lookup"><span data-stu-id="45384-176">number</span></span>           | <span data-ttu-id="45384-177">Nee</span><span class="sxs-lookup"><span data-stu-id="45384-177">No</span></span>       | <span data-ttu-id="45384-178">Nee</span><span class="sxs-lookup"><span data-stu-id="45384-178">No</span></span>        | <span data-ttu-id="45384-179">Het aantal apparaten.</span><span class="sxs-lookup"><span data-stu-id="45384-179">The number of devices.</span></span>                                                                                                                                   |
| <span data-ttu-id="45384-180">policySettings</span><span class="sxs-lookup"><span data-stu-id="45384-180">policySettings</span></span>  | <span data-ttu-id="45384-181">tekenreeksmatrix</span><span class="sxs-lookup"><span data-stu-id="45384-181">array of strings</span></span> | <span data-ttu-id="45384-182">Ja</span><span class="sxs-lookup"><span data-stu-id="45384-182">Yes</span></span>      | <span data-ttu-id="45384-183">Ja</span><span class="sxs-lookup"><span data-stu-id="45384-183">Yes</span></span>       | <span data-ttu-id="45384-184">De beleids instellingen: ' geen ', ' \_ OEM- \_ voor installatie verwijderen ', ' OOBE- \_ gebruiker \_ niet \_ lokale \_ beheerder ', ' Skip \_ Express Settings ', ' overs laan van \_ \_ OEM \_ -registratie, ' EULA overs Laan \_ '.</span><span class="sxs-lookup"><span data-stu-id="45384-184">The policy settings: "none","remove\_oem\_preinstalls","oobe\_user\_not\_local\_admin","skip\_express\_settings","skip \_oem\_registration,"skip\_eula".</span></span> |

### <a name="request-example"></a><span data-ttu-id="45384-185">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="45384-185">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/policies/56edf752-ee77-4fd8-b7f5-df1f74a3a9ac HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Content-Length: 256
Content-Type: application/json
Host: api.partnercenter.microsoft.com

{
    "id": "56edf752-ee77-4fd8-b7f5-df1f74a3a9ac",
    "name": "Windows test policy",
    "category": "o_o_b_e",
    "description": "Test policy creation from API",
    "devicesAssigned": 0,
    "policySettings": ["skip_express_settings"]
}
```

## <a name="rest-response"></a><span data-ttu-id="45384-186">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="45384-186">REST response</span></span>

<span data-ttu-id="45384-187">Als dit lukt, bevat de antwoord tekst de [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) -resource voor het nieuwe beleid.</span><span class="sxs-lookup"><span data-stu-id="45384-187">If successful, the response body contains the [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) resource for the new policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="45384-188">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="45384-188">Response success and error codes</span></span>

<span data-ttu-id="45384-189">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="45384-189">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="45384-190">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="45384-190">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="45384-191">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="45384-191">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="45384-192">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="45384-192">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 421
Content-Type: application/json; charset=utf-8
MS-CorrelationId: f9fd5973-6ad8-4585-aadc-f2b0443fe27b
MS-RequestId: cb1fa1f3-1381-45d9-99c5-511e5d3efa7c
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:10:29 GMT

{
    "id": "56edf752-ee77-4fd8-b7f5-df1f74a3a9ac",
    "name": "Windows test policy",
    "category": "o_o_b_e",
    "description": "Test policy creation from API",
    "devicesAssigned": 0,
    "policySettings": ["skip_express_settings"],
    "createdDate": "2017-01-01T00:00:00",
    "lastModifiedDate": "2017-07-25T18:10:15",
    "attributes": {
        "objectType": "ConfigurationPolicy"
    }
}
```
