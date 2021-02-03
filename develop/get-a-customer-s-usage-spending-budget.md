---
title: Het bestedings budget van een klant ophalen
description: U kunt een bestedings budget (het SpendingBudget-object) gebruiken om een samen vatting van klant gebruik (de CustomerUsageSummary-resource) bij te werken.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8be9ceaab6b7546de8eacba1e52e8766719e5125
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767376"
---
# <a name="get-a-customers-usage-spending-budget"></a><span data-ttu-id="03b27-103">Het bestedings budget van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="03b27-103">Get a customer's usage spending budget</span></span>

<span data-ttu-id="03b27-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="03b27-104">**Applies to:**</span></span>

- <span data-ttu-id="03b27-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="03b27-105">Partner Center</span></span>
- <span data-ttu-id="03b27-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="03b27-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="03b27-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="03b27-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="03b27-108">U kunt het bestedings budget (het object **SpendingBudget** ) bijwerken in de [samen vatting van klant gebruik (de **CustomerUsageSummary** -resource)](customer-usage-resources.md#customerusagesummary).</span><span class="sxs-lookup"><span data-stu-id="03b27-108">You can update the spending budget (the **SpendingBudget** object) in the [customer usage summary (the **CustomerUsageSummary** resource)](customer-usage-resources.md#customerusagesummary).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="03b27-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="03b27-109">Prerequisites</span></span>

- <span data-ttu-id="03b27-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="03b27-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="03b27-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="03b27-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="03b27-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="03b27-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="03b27-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="03b27-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="03b27-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="03b27-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="03b27-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="03b27-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="03b27-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="03b27-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="03b27-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="03b27-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="03b27-118">C\#</span><span class="sxs-lookup"><span data-stu-id="03b27-118">C\#</span></span>

<span data-ttu-id="03b27-119">Het budget voor gebruik van een klant bijwerken:</span><span class="sxs-lookup"><span data-stu-id="03b27-119">To update a customer's usage spending budget:</span></span>

1. <span data-ttu-id="03b27-120">Maak een nieuw [**SpendingBudget**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) -object met de bijgewerkte hoeveelheid.</span><span class="sxs-lookup"><span data-stu-id="03b27-120">Create a new [**SpendingBudget**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) object with the updated amount.</span></span>

2. <span data-ttu-id="03b27-121">Gebruik de verzameling [**IAggregatePartner. Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) om de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met de opgegeven klant-id.</span><span class="sxs-lookup"><span data-stu-id="03b27-121">Use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) collection to call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer's identifier.</span></span>

3. <span data-ttu-id="03b27-122">Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) aan om het gebruiks budget van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="03b27-122">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) method to get the customer's usage budget.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

// Create a new spending budget with the udpated amount.
var newUsageBudget = new SpendingBudget()
{
    Amount = 100
};

// Update the customer's usage budget.
var usageBudget = partnerOperations.Customers.ById(selectedCustomerId).UsageBudget.Get();
```

## <a name="rest-request"></a><span data-ttu-id="03b27-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="03b27-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="03b27-124">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="03b27-124">Request syntax</span></span>

| <span data-ttu-id="03b27-125">Methode</span><span class="sxs-lookup"><span data-stu-id="03b27-125">Method</span></span>    | <span data-ttu-id="03b27-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="03b27-126">Request URI</span></span>                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="03b27-127">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="03b27-127">**GET**</span></span> | <span data-ttu-id="03b27-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/usagebudget http/1.1</span><span class="sxs-lookup"><span data-stu-id="03b27-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/usagebudget  HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="03b27-129">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="03b27-129">URI parameter</span></span>

<span data-ttu-id="03b27-130">Gebruik de volgende query parameter om het facturerings profiel bij te werken.</span><span class="sxs-lookup"><span data-stu-id="03b27-130">Use the following query parameter to update the billing profile.</span></span>

| <span data-ttu-id="03b27-131">Naam</span><span class="sxs-lookup"><span data-stu-id="03b27-131">Name</span></span>                   | <span data-ttu-id="03b27-132">Type</span><span class="sxs-lookup"><span data-stu-id="03b27-132">Type</span></span>     | <span data-ttu-id="03b27-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="03b27-133">Required</span></span> | <span data-ttu-id="03b27-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="03b27-134">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="03b27-135">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="03b27-135">**customer-tenant-id**</span></span> | <span data-ttu-id="03b27-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="03b27-136">**guid**</span></span> | <span data-ttu-id="03b27-137">J</span><span class="sxs-lookup"><span data-stu-id="03b27-137">Y</span></span>        | <span data-ttu-id="03b27-138">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="03b27-138">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="03b27-139">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="03b27-139">Request headers</span></span>

<span data-ttu-id="03b27-140">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="03b27-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="03b27-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="03b27-141">Request body</span></span>

<span data-ttu-id="03b27-142">De volledige resource.</span><span class="sxs-lookup"><span data-stu-id="03b27-142">The full resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="03b27-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="03b27-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/usagebudget HTTP/1.1
Authorization: Bearer <token>
Accept: application/json, text/plain, */*
MS-RequestId: 312b044d-dc41-4b37-c2d5-7d27322d9654
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
Content-Type: application/json;charset=utf-8
X-Locale: "en-US"
```

## <a name="rest-response"></a><span data-ttu-id="03b27-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="03b27-144">REST response</span></span>

<span data-ttu-id="03b27-145">Als dit lukt, retourneert deze methode het uitgaven budget van een gebruiker met de bijgewerkte hoeveelheid.</span><span class="sxs-lookup"><span data-stu-id="03b27-145">If successful, this method returns a user's spending budget with the updated amount.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="03b27-146">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="03b27-146">Response success and error codes</span></span>

<span data-ttu-id="03b27-147">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="03b27-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="03b27-148">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="03b27-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="03b27-149">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="03b27-149">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="03b27-150">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="03b27-150">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 12014
Content-Type: application/json
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
MS-RequestId: be82a8ba-4a53-49f7-8313-b033c058687e
Date: Tue, 17 Sep 2019 20:31:45 GMT

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
            "method":"GET",
            "headers":[]
        }
    }
}
```
