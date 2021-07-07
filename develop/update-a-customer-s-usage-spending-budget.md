---
title: Het gebruiksbudget van een klant bijwerken
description: Werk het bestedingsbudget bij dat is toegewezen voor het gebruik van een klant.
ms.date: 02/05/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 043bd442266d081105e5e8767b6d597e89fc9e8b
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529712"
---
# <a name="update-a-customers-usage-spending-budget"></a><span data-ttu-id="000fa-103">Het gebruiksbudget van een klant bijwerken</span><span class="sxs-lookup"><span data-stu-id="000fa-103">Update a customer's usage spending budget</span></span>

<span data-ttu-id="000fa-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="000fa-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="000fa-105">Werk het [bestedingsbudget](customer-usage-resources.md#customerusagesummary) bij dat is toegewezen voor het gebruik van een klant.</span><span class="sxs-lookup"><span data-stu-id="000fa-105">Update the [spending budget](customer-usage-resources.md#customerusagesummary) allocated for a customer's usage.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="000fa-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="000fa-106">Prerequisites</span></span>

- <span data-ttu-id="000fa-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="000fa-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="000fa-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="000fa-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="000fa-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="000fa-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="000fa-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="000fa-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="000fa-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="000fa-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="000fa-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="000fa-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="000fa-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="000fa-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="000fa-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="000fa-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="000fa-115">C\#</span><span class="sxs-lookup"><span data-stu-id="000fa-115">C\#</span></span>

<span data-ttu-id="000fa-116">Als u het gebruiksuitgavenbudget van een klant wilt bijwerken, maakt u eerst een nieuw [**uitgavenbudgetobject**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) met het bijgewerkte bedrag.</span><span class="sxs-lookup"><span data-stu-id="000fa-116">To update a customer's usage spending budget, first create a new [**SpendingBudget**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) object with the updated amount.</span></span> <span data-ttu-id="000fa-117">Gebruik vervolgens de [**verzameling IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) en roep de [**methode ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de opgegeven klant-id.</span><span class="sxs-lookup"><span data-stu-id="000fa-117">Then use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer's ID.</span></span> <span data-ttu-id="000fa-118">Ga vervolgens naar [**de eigenschap UsageBudget**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.usagebudget) en geef het bijgewerkte gebruiksbudget door aan de [**methode Patch()**](/dotnet/api/microsoft.store.partnercenter.usage.icustomerusagespendingbudget.patch) of [**PatchAsync().**](/dotnet/api/microsoft.store.partnercenter.usage.icustomerusagespendingbudget.patchasync)</span><span class="sxs-lookup"><span data-stu-id="000fa-118">Then access the [**UsageBudget**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.usagebudget) property and pass the updated usage budget to the [**Patch()**](/dotnet/api/microsoft.store.partnercenter.usage.icustomerusagespendingbudget.patch) or [**PatchAsync()**](/dotnet/api/microsoft.store.partnercenter.usage.icustomerusagespendingbudget.patchasync) method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

// Create a new spending budget with the udpated amount.
var newUsageBudget = new SpendingBudget()
{
    Amount = 100
};

// Update the customer's usage budget.
var usageBudget = partnerOperations.Customers.ById(selectedCustomerId).UsageBudget.Patch(newUsageBudget);
```

## <a name="rest-request"></a><span data-ttu-id="000fa-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="000fa-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="000fa-120">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="000fa-120">Request syntax</span></span>

| <span data-ttu-id="000fa-121">Methode</span><span class="sxs-lookup"><span data-stu-id="000fa-121">Method</span></span>    | <span data-ttu-id="000fa-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="000fa-122">Request URI</span></span>                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="000fa-123">**Patch**</span><span class="sxs-lookup"><span data-stu-id="000fa-123">**PATCH**</span></span> | <span data-ttu-id="000fa-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/usagebudget HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="000fa-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/usagebudget  HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="000fa-125">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="000fa-125">URI parameter</span></span>

<span data-ttu-id="000fa-126">Gebruik de volgende queryparameter om het factureringsprofiel bij te werken.</span><span class="sxs-lookup"><span data-stu-id="000fa-126">Use the following query parameter to update the billing profile.</span></span>

| <span data-ttu-id="000fa-127">Naam</span><span class="sxs-lookup"><span data-stu-id="000fa-127">Name</span></span>                   | <span data-ttu-id="000fa-128">Type</span><span class="sxs-lookup"><span data-stu-id="000fa-128">Type</span></span>     | <span data-ttu-id="000fa-129">Vereist</span><span class="sxs-lookup"><span data-stu-id="000fa-129">Required</span></span> | <span data-ttu-id="000fa-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="000fa-130">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="000fa-131">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="000fa-131">**customer-tenant-id**</span></span> | <span data-ttu-id="000fa-132">**guid**</span><span class="sxs-lookup"><span data-stu-id="000fa-132">**guid**</span></span> | <span data-ttu-id="000fa-133">J</span><span class="sxs-lookup"><span data-stu-id="000fa-133">Y</span></span>        | <span data-ttu-id="000fa-134">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="000fa-134">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="000fa-135">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="000fa-135">Request headers</span></span>

<span data-ttu-id="000fa-136">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="000fa-136">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="000fa-137">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="000fa-137">Request body</span></span>

<span data-ttu-id="000fa-138">De volledige resource.</span><span class="sxs-lookup"><span data-stu-id="000fa-138">The full resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="000fa-139">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="000fa-139">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/usagebudget HTTP/1.1
Authorization: Bearer <token>
Accept: application/json, text/plain, */*
MS-RequestId: 312b044d-dc41-4b37-c2d5-7d27322d9654
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
Content-Type: application/json;charset=utf-8
X-Locale: "en-US"

{
     "Amount": 100,
     "Attributes": {
          "ObjectType": "SpendingBudget"
     }
}
```

## <a name="rest-response"></a><span data-ttu-id="000fa-140">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="000fa-140">REST response</span></span>

<span data-ttu-id="000fa-141">Als dit lukt, retourneert deze methode het bestedingsbudget van een gebruiker met het bijgewerkte bedrag.</span><span class="sxs-lookup"><span data-stu-id="000fa-141">If successful, this method returns a user's spending budget with the updated amount.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="000fa-142">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="000fa-142">Response success and error codes</span></span>

<span data-ttu-id="000fa-143">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="000fa-143">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="000fa-144">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="000fa-144">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="000fa-145">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="000fa-145">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="000fa-146">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="000fa-146">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 12014
Content-Type: application/json
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
MS-RequestId: be82a8ba-4a53-49f7-8313-b033c058687e
Date: Tue, 10 Nov 2015 19:09:59 GMT

{
    {
        "amount": 100,
        "usageSpendingBudget": 100,
        "attributes":{
            "objectType":"SpendingBudget"
        }
    },
    "links":{
        "self":{
            "uri":"/v1/customers/<customer-tenant-id>/usagebudget",
            "method":"PATCH",
            "headers":[]
        }
    }
}
```
