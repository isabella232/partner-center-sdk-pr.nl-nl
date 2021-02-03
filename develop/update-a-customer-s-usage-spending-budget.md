---
title: Het budget voor het gebruik van een klant bijwerken
description: Werk het bestedings budget bij dat is toegewezen aan het gebruik van een klant.
ms.date: 02/05/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 839305fb8fad3ce2442ab93e1d8a4a170b4d41c2
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767514"
---
# <a name="update-a-customers-usage-spending-budget"></a><span data-ttu-id="1c24f-103">Het budget voor het gebruik van een klant bijwerken</span><span class="sxs-lookup"><span data-stu-id="1c24f-103">Update a customer's usage spending budget</span></span>

<span data-ttu-id="1c24f-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="1c24f-104">**Applies To**</span></span>

- <span data-ttu-id="1c24f-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="1c24f-105">Partner Center</span></span>
- <span data-ttu-id="1c24f-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="1c24f-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="1c24f-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="1c24f-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="1c24f-108">Werk het [bestedings budget](customer-usage-resources.md#customerusagesummary) bij dat is toegewezen aan het gebruik van een klant.</span><span class="sxs-lookup"><span data-stu-id="1c24f-108">Update the [spending budget](customer-usage-resources.md#customerusagesummary) allocated for a customer's usage.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1c24f-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1c24f-109">Prerequisites</span></span>

- <span data-ttu-id="1c24f-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1c24f-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1c24f-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="1c24f-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="1c24f-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1c24f-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="1c24f-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="1c24f-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="1c24f-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="1c24f-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="1c24f-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="1c24f-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="1c24f-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="1c24f-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="1c24f-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1c24f-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="1c24f-118">C\#</span><span class="sxs-lookup"><span data-stu-id="1c24f-118">C\#</span></span>

<span data-ttu-id="1c24f-119">Als u het budget voor het gebruik van een klant wilt bijwerken, maakt u eerst een nieuw [**SpendingBudget**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) -object met de bijgewerkte hoeveelheid.</span><span class="sxs-lookup"><span data-stu-id="1c24f-119">To update a customer's usage spending budget, first create a new [**SpendingBudget**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) object with the updated amount.</span></span> <span data-ttu-id="1c24f-120">Vervolgens gebruikt u de verzameling [**IAggregatePartner. Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) en roept u de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de opgegeven klant-id.</span><span class="sxs-lookup"><span data-stu-id="1c24f-120">Then use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer's ID.</span></span> <span data-ttu-id="1c24f-121">Vervolgens opent u de eigenschap [**UsageBudget**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.usagebudget) en geeft u het bijgewerkte gebruiks budget door aan de methode [**patch ()**](/dotnet/api/microsoft.store.partnercenter.usage.icustomerusagespendingbudget.patch) of [**PatchAsync ()**](/dotnet/api/microsoft.store.partnercenter.usage.icustomerusagespendingbudget.patchasync) .</span><span class="sxs-lookup"><span data-stu-id="1c24f-121">Then access the [**UsageBudget**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.usagebudget) property and pass the updated usage budget to the [**Patch()**](/dotnet/api/microsoft.store.partnercenter.usage.icustomerusagespendingbudget.patch) or [**PatchAsync()**](/dotnet/api/microsoft.store.partnercenter.usage.icustomerusagespendingbudget.patchasync) method.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="1c24f-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="1c24f-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1c24f-123">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1c24f-123">Request syntax</span></span>

| <span data-ttu-id="1c24f-124">Methode</span><span class="sxs-lookup"><span data-stu-id="1c24f-124">Method</span></span>    | <span data-ttu-id="1c24f-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="1c24f-125">Request URI</span></span>                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1c24f-126">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="1c24f-126">**PATCH**</span></span> | <span data-ttu-id="1c24f-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/usagebudget http/1.1</span><span class="sxs-lookup"><span data-stu-id="1c24f-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/usagebudget  HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="1c24f-128">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="1c24f-128">URI parameter</span></span>

<span data-ttu-id="1c24f-129">Gebruik de volgende query parameter om het facturerings profiel bij te werken.</span><span class="sxs-lookup"><span data-stu-id="1c24f-129">Use the following query parameter to update the billing profile.</span></span>

| <span data-ttu-id="1c24f-130">Naam</span><span class="sxs-lookup"><span data-stu-id="1c24f-130">Name</span></span>                   | <span data-ttu-id="1c24f-131">Type</span><span class="sxs-lookup"><span data-stu-id="1c24f-131">Type</span></span>     | <span data-ttu-id="1c24f-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="1c24f-132">Required</span></span> | <span data-ttu-id="1c24f-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1c24f-133">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1c24f-134">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="1c24f-134">**customer-tenant-id**</span></span> | <span data-ttu-id="1c24f-135">**guid**</span><span class="sxs-lookup"><span data-stu-id="1c24f-135">**guid**</span></span> | <span data-ttu-id="1c24f-136">J</span><span class="sxs-lookup"><span data-stu-id="1c24f-136">Y</span></span>        | <span data-ttu-id="1c24f-137">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="1c24f-137">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="1c24f-138">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="1c24f-138">Request headers</span></span>

<span data-ttu-id="1c24f-139">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="1c24f-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1c24f-140">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="1c24f-140">Request body</span></span>

<span data-ttu-id="1c24f-141">De volledige resource.</span><span class="sxs-lookup"><span data-stu-id="1c24f-141">The full resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="1c24f-142">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1c24f-142">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="1c24f-143">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="1c24f-143">REST response</span></span>

<span data-ttu-id="1c24f-144">Als dit lukt, retourneert deze methode het uitgaven budget van een gebruiker met de bijgewerkte hoeveelheid.</span><span class="sxs-lookup"><span data-stu-id="1c24f-144">If successful, this method returns a user's spending budget with the updated amount.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1c24f-145">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="1c24f-145">Response success and error codes</span></span>

<span data-ttu-id="1c24f-146">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="1c24f-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1c24f-147">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="1c24f-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1c24f-148">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="1c24f-148">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="1c24f-149">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="1c24f-149">Response example</span></span>

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
