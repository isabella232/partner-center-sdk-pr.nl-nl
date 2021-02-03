---
title: Een configuratiebeleid bijwerken voor de opgegeven klant
description: Het opgegeven configuratie beleid voor de opgegeven klant bijwerken.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6bf3b6f4db7516779c157b647725368ff0e4a570
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767525"
---
# <a name="update-a-configuration-policy-for-the-specified-customer"></a><span data-ttu-id="29823-103">Een configuratiebeleid bijwerken voor de opgegeven klant</span><span class="sxs-lookup"><span data-stu-id="29823-103">Update a configuration policy for the specified customer</span></span>

<span data-ttu-id="29823-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="29823-104">**Applies To**</span></span>

- <span data-ttu-id="29823-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="29823-105">Partner Center</span></span>
- <span data-ttu-id="29823-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="29823-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="29823-107">Het opgegeven configuratie beleid voor de opgegeven klant bijwerken.</span><span class="sxs-lookup"><span data-stu-id="29823-107">How to update the specified configuration policy for the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="29823-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="29823-108">Prerequisites</span></span>

- <span data-ttu-id="29823-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="29823-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="29823-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="29823-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="29823-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="29823-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="29823-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="29823-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="29823-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="29823-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="29823-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="29823-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="29823-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="29823-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="29823-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="29823-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="29823-117">De beleids-id.</span><span class="sxs-lookup"><span data-stu-id="29823-117">The policy identifier.</span></span>

## <a name="c"></a><span data-ttu-id="29823-118">C\#</span><span class="sxs-lookup"><span data-stu-id="29823-118">C\#</span></span>

<span data-ttu-id="29823-119">Als u een bestaand configuratie beleid voor de opgegeven klant wilt bijwerken, moet u een nieuw [**ConfigurationPolicy**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) -object instantiëren, zoals wordt weer gegeven in het volgende code fragment.</span><span class="sxs-lookup"><span data-stu-id="29823-119">To update an existing configuration policy for the specified customer, instantiate a new [**ConfigurationPolicy**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.configurationpolicy) object as shown in the following code snippet.</span></span> <span data-ttu-id="29823-120">De waarden in dit nieuwe object vervangen de overeenkomende waarden in het bestaande object.</span><span class="sxs-lookup"><span data-stu-id="29823-120">The values in this new object replace the corresponding values in the existing object.</span></span> <span data-ttu-id="29823-121">Vervolgens roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="29823-121">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="29823-122">Vervolgens roept u de methode [**ConfigurationPolicies. ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) aan met de beleids-id om een interface op te halen voor configuratie beleids bewerkingen voor het opgegeven beleid.</span><span class="sxs-lookup"><span data-stu-id="29823-122">Next, call the [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) method with the policy ID to retrieve an interface to configuration policy operations for the specified policy.</span></span> <span data-ttu-id="29823-123">Roep ten slotte de [**patch**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patch) -of [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patchasync) -methode aan om het configuratie beleid bij te werken.</span><span class="sxs-lookup"><span data-stu-id="29823-123">Finally, call the [**Patch**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patch) or [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.patchasync) method to update the configuration policy.</span></span>

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

<span data-ttu-id="29823-124">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="29823-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="29823-125">**Project**: Partner Center SDK-voor beelden **klasse**: UpdateConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="29823-125">**Project**: Partner Center SDK Samples **Class**: UpdateConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="29823-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="29823-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="29823-127">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="29823-127">Request syntax</span></span>

| <span data-ttu-id="29823-128">Methode</span><span class="sxs-lookup"><span data-stu-id="29823-128">Method</span></span>  | <span data-ttu-id="29823-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="29823-129">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="29823-130">**PUT**</span><span class="sxs-lookup"><span data-stu-id="29823-130">**PUT**</span></span> | <span data-ttu-id="29823-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/policies/{Policy-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="29823-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="29823-132">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="29823-132">URI parameter</span></span>

<span data-ttu-id="29823-133">Gebruik de volgende Path-para meters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="29823-133">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="29823-134">Naam</span><span class="sxs-lookup"><span data-stu-id="29823-134">Name</span></span>        | <span data-ttu-id="29823-135">Type</span><span class="sxs-lookup"><span data-stu-id="29823-135">Type</span></span>   | <span data-ttu-id="29823-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="29823-136">Required</span></span> | <span data-ttu-id="29823-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="29823-137">Description</span></span>                                                   |
|-------------|--------|----------|---------------------------------------------------------------|
| <span data-ttu-id="29823-138">klant-id</span><span class="sxs-lookup"><span data-stu-id="29823-138">customer-id</span></span> | <span data-ttu-id="29823-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="29823-139">string</span></span> | <span data-ttu-id="29823-140">Yes</span><span class="sxs-lookup"><span data-stu-id="29823-140">Yes</span></span>      | <span data-ttu-id="29823-141">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="29823-141">A GUID-formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="29823-142">beleid-id</span><span class="sxs-lookup"><span data-stu-id="29823-142">policy-id</span></span>   | <span data-ttu-id="29823-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="29823-143">string</span></span> | <span data-ttu-id="29823-144">Yes</span><span class="sxs-lookup"><span data-stu-id="29823-144">Yes</span></span>      | <span data-ttu-id="29823-145">Een teken reeks met een GUID-indeling die het beleid identificeert dat moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="29823-145">A GUID-formatted string that identifies the policy to update.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="29823-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="29823-146">Request headers</span></span>

<span data-ttu-id="29823-147">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="29823-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="29823-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="29823-148">Request body</span></span>

<span data-ttu-id="29823-149">De aanvraag tekst moet een object bevatten dat de beleids gegevens levert.</span><span class="sxs-lookup"><span data-stu-id="29823-149">The request body must contain an object that provides the policy information.</span></span>

| <span data-ttu-id="29823-150">Naam</span><span class="sxs-lookup"><span data-stu-id="29823-150">Name</span></span>            | <span data-ttu-id="29823-151">Type</span><span class="sxs-lookup"><span data-stu-id="29823-151">Type</span></span>             | <span data-ttu-id="29823-152">Vereist</span><span class="sxs-lookup"><span data-stu-id="29823-152">Required</span></span> | <span data-ttu-id="29823-153">Worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="29823-153">Updatable</span></span> | <span data-ttu-id="29823-154">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="29823-154">Description</span></span>                                                                                                                                              |
|-----------------|------------------|----------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="29823-155">id</span><span class="sxs-lookup"><span data-stu-id="29823-155">id</span></span>              | <span data-ttu-id="29823-156">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="29823-156">string</span></span>           | <span data-ttu-id="29823-157">Ja</span><span class="sxs-lookup"><span data-stu-id="29823-157">Yes</span></span>      | <span data-ttu-id="29823-158">Nee</span><span class="sxs-lookup"><span data-stu-id="29823-158">No</span></span>        | <span data-ttu-id="29823-159">De teken reeks met de GUID-indeling waarmee het beleid wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="29823-159">The GUID-formatted string that identifies the policy.</span></span>                                                                                                    |
| <span data-ttu-id="29823-160">naam</span><span class="sxs-lookup"><span data-stu-id="29823-160">name</span></span>            | <span data-ttu-id="29823-161">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="29823-161">string</span></span>           | <span data-ttu-id="29823-162">Ja</span><span class="sxs-lookup"><span data-stu-id="29823-162">Yes</span></span>      | <span data-ttu-id="29823-163">Ja</span><span class="sxs-lookup"><span data-stu-id="29823-163">Yes</span></span>       | <span data-ttu-id="29823-164">De beschrijvende naam van het beleid.</span><span class="sxs-lookup"><span data-stu-id="29823-164">The friendly name of the policy.</span></span>                                                                                                                         |
| <span data-ttu-id="29823-165">category</span><span class="sxs-lookup"><span data-stu-id="29823-165">category</span></span>        | <span data-ttu-id="29823-166">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="29823-166">string</span></span>           | <span data-ttu-id="29823-167">Ja</span><span class="sxs-lookup"><span data-stu-id="29823-167">Yes</span></span>      | <span data-ttu-id="29823-168">Nee</span><span class="sxs-lookup"><span data-stu-id="29823-168">No</span></span>        | <span data-ttu-id="29823-169">De beleids categorie.</span><span class="sxs-lookup"><span data-stu-id="29823-169">The policy category.</span></span>                                                                                                                                     |
| <span data-ttu-id="29823-170">beschrijving</span><span class="sxs-lookup"><span data-stu-id="29823-170">description</span></span>     | <span data-ttu-id="29823-171">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="29823-171">string</span></span>           | <span data-ttu-id="29823-172">No</span><span class="sxs-lookup"><span data-stu-id="29823-172">No</span></span>       | <span data-ttu-id="29823-173">Ja</span><span class="sxs-lookup"><span data-stu-id="29823-173">Yes</span></span>       | <span data-ttu-id="29823-174">De beschrijving van het beleid.</span><span class="sxs-lookup"><span data-stu-id="29823-174">The policy description.</span></span>                                                                                                                                  |
| <span data-ttu-id="29823-175">devicesAssigned</span><span class="sxs-lookup"><span data-stu-id="29823-175">devicesAssigned</span></span> | <span data-ttu-id="29823-176">getal</span><span class="sxs-lookup"><span data-stu-id="29823-176">number</span></span>           | <span data-ttu-id="29823-177">Nee</span><span class="sxs-lookup"><span data-stu-id="29823-177">No</span></span>       | <span data-ttu-id="29823-178">Nee</span><span class="sxs-lookup"><span data-stu-id="29823-178">No</span></span>        | <span data-ttu-id="29823-179">Het aantal apparaten.</span><span class="sxs-lookup"><span data-stu-id="29823-179">The number of devices.</span></span>                                                                                                                                   |
| <span data-ttu-id="29823-180">policySettings</span><span class="sxs-lookup"><span data-stu-id="29823-180">policySettings</span></span>  | <span data-ttu-id="29823-181">tekenreeksmatrix</span><span class="sxs-lookup"><span data-stu-id="29823-181">array of strings</span></span> | <span data-ttu-id="29823-182">Ja</span><span class="sxs-lookup"><span data-stu-id="29823-182">Yes</span></span>      | <span data-ttu-id="29823-183">Ja</span><span class="sxs-lookup"><span data-stu-id="29823-183">Yes</span></span>       | <span data-ttu-id="29823-184">De beleids instellingen: ' geen ', ' \_ OEM- \_ voor installatie verwijderen ', ' OOBE- \_ gebruiker \_ niet \_ lokale \_ beheerder ', ' Skip \_ Express Settings ', ' overs laan van \_ \_ OEM \_ -registratie, ' EULA overs Laan \_ '.</span><span class="sxs-lookup"><span data-stu-id="29823-184">The policy settings: "none","remove\_oem\_preinstalls","oobe\_user\_not\_local\_admin","skip\_express\_settings","skip \_oem\_registration,"skip\_eula".</span></span> |

### <a name="request-example"></a><span data-ttu-id="29823-185">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="29823-185">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="29823-186">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="29823-186">REST response</span></span>

<span data-ttu-id="29823-187">Als dit lukt, bevat de antwoord tekst de [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) -resource voor het nieuwe beleid.</span><span class="sxs-lookup"><span data-stu-id="29823-187">If successful, the response body contains the [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) resource for the new policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="29823-188">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="29823-188">Response success and error codes</span></span>

<span data-ttu-id="29823-189">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="29823-189">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="29823-190">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="29823-190">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="29823-191">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="29823-191">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="29823-192">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="29823-192">Response example</span></span>

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
