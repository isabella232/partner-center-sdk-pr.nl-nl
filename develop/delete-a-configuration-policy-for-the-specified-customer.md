---
title: Een configuratiebeleid verwijderen voor de opgegeven klant
description: Een configuratiebeleid verwijderen voor een opgegeven klant en beleids-id.
ms.date: 06/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 2d6a7d392bd6af6850eb7716528e6745943bb7bb
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973023"
---
# <a name="delete-a-configuration-policy-for-the-specified-customer"></a><span data-ttu-id="4d943-103">Een configuratiebeleid verwijderen voor de opgegeven klant</span><span class="sxs-lookup"><span data-stu-id="4d943-103">Delete a configuration policy for the specified customer</span></span>

<span data-ttu-id="4d943-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="4d943-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="4d943-105">Een configuratiebeleid verwijderen voor een opgegeven klant en beleids-id.</span><span class="sxs-lookup"><span data-stu-id="4d943-105">How to delete a configuration policy for a specified customer and policy identifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4d943-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4d943-106">Prerequisites</span></span>

- <span data-ttu-id="4d943-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4d943-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4d943-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="4d943-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="4d943-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4d943-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="4d943-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="4d943-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="4d943-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="4d943-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="4d943-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="4d943-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="4d943-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="4d943-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="4d943-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4d943-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="4d943-115">De beleids-id.</span><span class="sxs-lookup"><span data-stu-id="4d943-115">The policy identifier.</span></span>

## <a name="c"></a><span data-ttu-id="4d943-116">C\#</span><span class="sxs-lookup"><span data-stu-id="4d943-116">C\#</span></span>

<span data-ttu-id="4d943-117">Een configuratiebeleid voor een opgegeven klant verwijderen:</span><span class="sxs-lookup"><span data-stu-id="4d943-117">To delete a configuration policy for a specified customer:</span></span>

1. <span data-ttu-id="4d943-118">Roep de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="4d943-118">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span>

2. <span data-ttu-id="4d943-119">Roep de [**methode ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) aan met de beleids-id om een interface op te halen voor configuratiebeleidsbewerkingen voor het opgegeven beleid.</span><span class="sxs-lookup"><span data-stu-id="4d943-119">Call the [**ConfigurationPolicies.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.byid) method with the policy ID to retrieve an interface to configuration policy operations for the specified policy.</span></span>

3. <span data-ttu-id="4d943-120">Roep de [**methode Delete**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.delete) of [**DeleteAsync aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.deleteasync) om het configuratiebeleid te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="4d943-120">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.delete) or [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicy.deleteasync) method to delete the configuration policy.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedPolicyId;

partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.ById(selectedPolicyId).Delete();
```

<span data-ttu-id="4d943-121">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="4d943-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="4d943-122">**Project**: Partnercentrum-SDK Samples **Class:** DeleteConfigurationPolicy.cs</span><span class="sxs-lookup"><span data-stu-id="4d943-122">**Project**: Partner Center SDK Samples **Class**: DeleteConfigurationPolicy.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="4d943-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="4d943-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4d943-124">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="4d943-124">Request syntax</span></span>

| <span data-ttu-id="4d943-125">Methode</span><span class="sxs-lookup"><span data-stu-id="4d943-125">Method</span></span>     | <span data-ttu-id="4d943-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="4d943-126">Request URI</span></span>                                                                                          |
|------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4d943-127">**Verwijderen**</span><span class="sxs-lookup"><span data-stu-id="4d943-127">**DELETE**</span></span> | <span data-ttu-id="4d943-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4d943-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies/{policy-id} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="4d943-129">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="4d943-129">URI parameters</span></span>

<span data-ttu-id="4d943-130">Gebruik de volgende padparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="4d943-130">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="4d943-131">Naam</span><span class="sxs-lookup"><span data-stu-id="4d943-131">Name</span></span>        | <span data-ttu-id="4d943-132">Type</span><span class="sxs-lookup"><span data-stu-id="4d943-132">Type</span></span>   | <span data-ttu-id="4d943-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="4d943-133">Required</span></span> | <span data-ttu-id="4d943-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4d943-134">Description</span></span>                                                   |
|-------------|--------|----------|---------------------------------------------------------------|
| <span data-ttu-id="4d943-135">customer-id</span><span class="sxs-lookup"><span data-stu-id="4d943-135">customer-id</span></span> | <span data-ttu-id="4d943-136">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4d943-136">string</span></span> | <span data-ttu-id="4d943-137">Ja</span><span class="sxs-lookup"><span data-stu-id="4d943-137">Yes</span></span>      | <span data-ttu-id="4d943-138">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="4d943-138">A GUID-formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="4d943-139">policy-id</span><span class="sxs-lookup"><span data-stu-id="4d943-139">policy-id</span></span>   | <span data-ttu-id="4d943-140">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4d943-140">string</span></span> | <span data-ttu-id="4d943-141">Ja</span><span class="sxs-lookup"><span data-stu-id="4d943-141">Yes</span></span>      | <span data-ttu-id="4d943-142">Een tekenreeks met GUID-indeling die het beleid identificeert dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="4d943-142">A GUID-formatted string that identifies the policy to delete.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4d943-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="4d943-143">Request headers</span></span>

<span data-ttu-id="4d943-144">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="4d943-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4d943-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="4d943-145">Request body</span></span>

<span data-ttu-id="4d943-146">Geen</span><span class="sxs-lookup"><span data-stu-id="4d943-146">None</span></span>

### <a name="request-example"></a><span data-ttu-id="4d943-147">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4d943-147">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="4d943-148">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="4d943-148">REST response</span></span>

<span data-ttu-id="4d943-149">Als dit lukt, retourneert het antwoord de statuscode 204 Geen inhoud.</span><span class="sxs-lookup"><span data-stu-id="4d943-149">If successful, the response returns a 204 No Content status code.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4d943-150">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="4d943-150">Response success and error codes</span></span>

<span data-ttu-id="4d943-151">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="4d943-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4d943-152">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="4d943-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4d943-153">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="4d943-153">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4d943-154">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="4d943-154">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: cee5caf4-c322-4baa-b1d7-e94afb9891a4
MS-RequestId: 76b6f317-1da1-4b61-a6fd-9952439a2c46
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:10:41 GMT
```
