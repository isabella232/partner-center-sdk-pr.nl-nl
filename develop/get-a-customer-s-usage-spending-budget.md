---
title: Het uitgavenbudget voor gebruik van een klant op halen
description: U kunt een uitgavenbudget (het object SpendingBudget) gebruiken om een samenvatting van het gebruik van klanten bij te werken (de resource CustomerUsageSummary).
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b55f59fff7e5d7865811ecab3e901848126d31f7
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874870"
---
# <a name="get-a-customers-usage-spending-budget"></a><span data-ttu-id="58bc3-103">Het uitgavenbudget voor gebruik van een klant op halen</span><span class="sxs-lookup"><span data-stu-id="58bc3-103">Get a customer's usage spending budget</span></span>

<span data-ttu-id="58bc3-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="58bc3-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="58bc3-105">U kunt het bestedingsbudget (het object **SpendingBudget)** bijwerken in het gebruiksoverzicht van de klant [(de resource **CustomerUsageSummary).**](customer-usage-resources.md#customerusagesummary)</span><span class="sxs-lookup"><span data-stu-id="58bc3-105">You can update the spending budget (the **SpendingBudget** object) in the [customer usage summary (the **CustomerUsageSummary** resource)](customer-usage-resources.md#customerusagesummary).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="58bc3-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="58bc3-106">Prerequisites</span></span>

- <span data-ttu-id="58bc3-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="58bc3-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="58bc3-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="58bc3-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="58bc3-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="58bc3-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="58bc3-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="58bc3-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="58bc3-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="58bc3-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="58bc3-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="58bc3-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="58bc3-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="58bc3-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="58bc3-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="58bc3-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="58bc3-115">C\#</span><span class="sxs-lookup"><span data-stu-id="58bc3-115">C\#</span></span>

<span data-ttu-id="58bc3-116">Ga als volgende te werk om het gebruiksbudget van een klant bij te werken:</span><span class="sxs-lookup"><span data-stu-id="58bc3-116">To update a customer's usage spending budget:</span></span>

1. <span data-ttu-id="58bc3-117">Maak een nieuw [**SpendingBudget-object**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) met het bijgewerkte bedrag.</span><span class="sxs-lookup"><span data-stu-id="58bc3-117">Create a new [**SpendingBudget**](/dotnet/api/microsoft.store.partnercenter.models.usage.spendingbudget) object with the updated amount.</span></span>

2. <span data-ttu-id="58bc3-118">Gebruik de [**verzameling IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) om de [**methode ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met de id van de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="58bc3-118">Use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection) collection to call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer's identifier.</span></span>

3. <span data-ttu-id="58bc3-119">Roep de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) om het gebruiksbudget van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="58bc3-119">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) method to get the customer's usage budget.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="58bc3-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="58bc3-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="58bc3-121">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="58bc3-121">Request syntax</span></span>

| <span data-ttu-id="58bc3-122">Methode</span><span class="sxs-lookup"><span data-stu-id="58bc3-122">Method</span></span>    | <span data-ttu-id="58bc3-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="58bc3-123">Request URI</span></span>                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="58bc3-124">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="58bc3-124">**GET**</span></span> | <span data-ttu-id="58bc3-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/usagebudget HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="58bc3-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/usagebudget  HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="58bc3-126">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="58bc3-126">URI parameter</span></span>

<span data-ttu-id="58bc3-127">Gebruik de volgende queryparameter om het factureringsprofiel bij te werken.</span><span class="sxs-lookup"><span data-stu-id="58bc3-127">Use the following query parameter to update the billing profile.</span></span>

| <span data-ttu-id="58bc3-128">Naam</span><span class="sxs-lookup"><span data-stu-id="58bc3-128">Name</span></span>                   | <span data-ttu-id="58bc3-129">Type</span><span class="sxs-lookup"><span data-stu-id="58bc3-129">Type</span></span>     | <span data-ttu-id="58bc3-130">Vereist</span><span class="sxs-lookup"><span data-stu-id="58bc3-130">Required</span></span> | <span data-ttu-id="58bc3-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="58bc3-131">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="58bc3-132">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="58bc3-132">**customer-tenant-id**</span></span> | <span data-ttu-id="58bc3-133">**guid**</span><span class="sxs-lookup"><span data-stu-id="58bc3-133">**guid**</span></span> | <span data-ttu-id="58bc3-134">J</span><span class="sxs-lookup"><span data-stu-id="58bc3-134">Y</span></span>        | <span data-ttu-id="58bc3-135">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="58bc3-135">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="58bc3-136">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="58bc3-136">Request headers</span></span>

<span data-ttu-id="58bc3-137">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="58bc3-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="58bc3-138">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="58bc3-138">Request body</span></span>

<span data-ttu-id="58bc3-139">De volledige resource.</span><span class="sxs-lookup"><span data-stu-id="58bc3-139">The full resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="58bc3-140">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="58bc3-140">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/usagebudget HTTP/1.1
Authorization: Bearer <token>
Accept: application/json, text/plain, */*
MS-RequestId: 312b044d-dc41-4b37-c2d5-7d27322d9654
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
Content-Type: application/json;charset=utf-8
X-Locale: "en-US"
```

## <a name="rest-response"></a><span data-ttu-id="58bc3-141">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="58bc3-141">REST response</span></span>

<span data-ttu-id="58bc3-142">Als dit lukt, retourneert deze methode het bestedingsbudget van een gebruiker met het bijgewerkte bedrag.</span><span class="sxs-lookup"><span data-stu-id="58bc3-142">If successful, this method returns a user's spending budget with the updated amount.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="58bc3-143">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="58bc3-143">Response success and error codes</span></span>

<span data-ttu-id="58bc3-144">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="58bc3-144">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="58bc3-145">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="58bc3-145">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="58bc3-146">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="58bc3-146">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="58bc3-147">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="58bc3-147">Response example</span></span>

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
