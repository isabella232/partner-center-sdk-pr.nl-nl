---
title: Een configuratiebeleid verwijderen voor de opgegeven klant
description: Een configuratie beleid voor een opgegeven klant en beleid-id verwijderen.
ms.date: 06/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 586878367fc0873ef0fb1415799b2b7022954053
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767391"
---
# <a name="delete-a-configuration-policy-for-the-specified-customer"></a><span data-ttu-id="c37aa-103">Een configuratiebeleid verwijderen voor de opgegeven klant</span><span class="sxs-lookup"><span data-stu-id="c37aa-103">Delete a configuration policy for the specified customer</span></span>

<span data-ttu-id="c37aa-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="c37aa-104">**Applies to:**</span></span>

- <span data-ttu-id="c37aa-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="c37aa-105">Partner Center</span></span>
- <span data-ttu-id="c37aa-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="c37aa-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="c37aa-107">Een configuratie beleid voor een opgegeven klant en beleid-id verwijderen.</span><span class="sxs-lookup"><span data-stu-id="c37aa-107">How to delete a configuration policy for a specified customer and policy identifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c37aa-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c37aa-108">Prerequisites</span></span>

- <span data-ttu-id="c37aa-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c37aa-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c37aa-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="c37aa-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="c37aa-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c37aa-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="c37aa-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="c37aa-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="c37aa-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="c37aa-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="c37aa-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="c37aa-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="c37aa-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="c37aa-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="c37aa-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c37aa-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="c37aa-117">De beleids-id.</span><span class="sxs-lookup"><span data-stu-id="c37aa-117">The policy identifier.</span></span>

## <a name="c"></a><span data-ttu-id="c37aa-118">C\#</span><span class="sxs-lookup"><span data-stu-id="c37aa-118">C\#</span></span>

<span data-ttu-id="c37aa-119">Een configuratie beleid voor een opgegeven klant verwijderen:</span><span class="sxs-lookup"><span data-stu-id="c37aa-119">To delete a configuration policy for a specified customer:</span></span>

1. <span data-ttu-id="c37aa-120">Roep de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="c37aa-120">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span>

2. <span data-ttu-id="c37aa-121">Roep de methode [**ConfigurationPolicies. ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) aan met de beleids-id om een interface op te halen voor configuratie beleids bewerkingen voor het opgegeven beleid.</span><span class="sxs-lookup"><span data-stu-id="c37aa-121">Call the [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) method with the policy ID to retrieve an interface to configuration policy operations for the specified policy.</span></span>

3. <span data-ttu-id="c37aa-122">Roep de methode [**Delete**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.delete) of [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.deleteasync) aan om het configuratie beleid te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="c37aa-122">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.delete) or [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.deleteasync) method to delete the configuration policy.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedPolicyId;

partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.ById(selectedPolicyId).Delete();
```

<span data-ttu-id="c37aa-123">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="c37aa-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="c37aa-124">**Project**: Partner Center SDK-voor beelden **klasse**: DeleteConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="c37aa-124">**Project**: Partner Center SDK Samples **Class**: DeleteConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="c37aa-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c37aa-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c37aa-126">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c37aa-126">Request syntax</span></span>

| <span data-ttu-id="c37aa-127">Methode</span><span class="sxs-lookup"><span data-stu-id="c37aa-127">Method</span></span>     | <span data-ttu-id="c37aa-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c37aa-128">Request URI</span></span>                                                                                          |
|------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c37aa-129">**VERWIJDERD**</span><span class="sxs-lookup"><span data-stu-id="c37aa-129">**DELETE**</span></span> | <span data-ttu-id="c37aa-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/policies/{Policy-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="c37aa-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="c37aa-131">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="c37aa-131">URI parameters</span></span>

<span data-ttu-id="c37aa-132">Gebruik de volgende Path-para meters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="c37aa-132">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="c37aa-133">Naam</span><span class="sxs-lookup"><span data-stu-id="c37aa-133">Name</span></span>        | <span data-ttu-id="c37aa-134">Type</span><span class="sxs-lookup"><span data-stu-id="c37aa-134">Type</span></span>   | <span data-ttu-id="c37aa-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="c37aa-135">Required</span></span> | <span data-ttu-id="c37aa-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c37aa-136">Description</span></span>                                                   |
|-------------|--------|----------|---------------------------------------------------------------|
| <span data-ttu-id="c37aa-137">klant-id</span><span class="sxs-lookup"><span data-stu-id="c37aa-137">customer-id</span></span> | <span data-ttu-id="c37aa-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="c37aa-138">string</span></span> | <span data-ttu-id="c37aa-139">Yes</span><span class="sxs-lookup"><span data-stu-id="c37aa-139">Yes</span></span>      | <span data-ttu-id="c37aa-140">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="c37aa-140">A GUID-formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="c37aa-141">beleid-id</span><span class="sxs-lookup"><span data-stu-id="c37aa-141">policy-id</span></span>   | <span data-ttu-id="c37aa-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="c37aa-142">string</span></span> | <span data-ttu-id="c37aa-143">Yes</span><span class="sxs-lookup"><span data-stu-id="c37aa-143">Yes</span></span>      | <span data-ttu-id="c37aa-144">Een teken reeks met een GUID-indeling die het beleid identificeert dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c37aa-144">A GUID-formatted string that identifies the policy to delete.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c37aa-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c37aa-145">Request headers</span></span>

<span data-ttu-id="c37aa-146">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c37aa-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c37aa-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c37aa-147">Request body</span></span>

<span data-ttu-id="c37aa-148">Geen</span><span class="sxs-lookup"><span data-stu-id="c37aa-148">None</span></span>

### <a name="request-example"></a><span data-ttu-id="c37aa-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c37aa-149">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/policies/56edf752-ee77-4fd8-b7f5-df1f74a3a9ac HTTP/1.1
Authorization: Bearer <token>
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Content-Length: 0
Content-Type: application/json
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="c37aa-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c37aa-150">REST response</span></span>

<span data-ttu-id="c37aa-151">Als de aanvraag is voltooid, wordt de status code van 204 geen inhoud geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c37aa-151">If successful, the response returns a 204 No Content status code.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c37aa-152">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="c37aa-152">Response success and error codes</span></span>

<span data-ttu-id="c37aa-153">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="c37aa-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c37aa-154">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c37aa-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c37aa-155">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="c37aa-155">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c37aa-156">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="c37aa-156">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: cee5caf4-c322-4baa-b1d7-e94afb9891a4
MS-RequestId: 76b6f317-1da1-4b61-a6fd-9952439a2c46
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:10:41 GMT
```
