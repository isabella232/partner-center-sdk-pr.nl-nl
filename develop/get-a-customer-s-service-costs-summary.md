---
title: Een samenvatting van de servicekosten van een klant ophalen
description: Hiermee worden de servicekosten van een klant voor de opgegeven factureringsperiode opgeslagen.
ms.date: 06/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1cab23238b5f62a02a5f7368f626648d5b1b5b7e
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874904"
---
# <a name="get-a-customers-service-costs-summary"></a><span data-ttu-id="f833a-103">Een samenvatting van de servicekosten van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="f833a-103">Get a customer's service costs summary</span></span>

<span data-ttu-id="f833a-104">Hiermee worden de servicekosten van een klant voor de opgegeven factureringsperiode opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="f833a-104">Gets a customer's service costs for the specified billing period.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f833a-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f833a-105">Prerequisites</span></span>

- <span data-ttu-id="f833a-106">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="f833a-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f833a-107">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="f833a-107">This scenario supports authentication with App+User credentials.</span></span>

- <span data-ttu-id="f833a-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f833a-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f833a-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="f833a-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f833a-110">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="f833a-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f833a-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="f833a-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f833a-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="f833a-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f833a-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f833a-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="f833a-114">Een factureringsperiode-indicator ( **`mostrecent`** ).</span><span class="sxs-lookup"><span data-stu-id="f833a-114">A billing period indicator (**`mostrecent`**).</span></span>

## <a name="c"></a><span data-ttu-id="f833a-115">C\#</span><span class="sxs-lookup"><span data-stu-id="f833a-115">C\#</span></span>

<span data-ttu-id="f833a-116">Een samenvatting van de servicekosten voor de opgegeven klant ophalen:</span><span class="sxs-lookup"><span data-stu-id="f833a-116">To retrieve a service costs summary for the specified customer:</span></span>

1. <span data-ttu-id="f833a-117">Roep de [**methode IAggregatePartner.Customers.ById aan**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="f833a-117">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="f833a-118">Gebruik de [**eigenschap ServiceCosts om**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicecosts) een interface te krijgen voor het verzamelen van kosten van de klantenservice.</span><span class="sxs-lookup"><span data-stu-id="f833a-118">Use the [**ServiceCosts**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicecosts) property to get an interface to customer service costs collection operations.</span></span>

3. <span data-ttu-id="f833a-119">Roep de [**methode ByBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.icustomerservicecostscollection.bybillingperiod) aan met een lid van de enumeratie [**ServiceCostsBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.models.servicecosts.servicecostsbillingperiod) om een [**IServiceCostsCollection te retourneren.**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostscollection)</span><span class="sxs-lookup"><span data-stu-id="f833a-119">Call the [**ByBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.icustomerservicecostscollection.bybillingperiod) method with a member of the [**ServiceCostsBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.models.servicecosts.servicecostsbillingperiod) enumeration to return an [**IServiceCostsCollection**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostscollection).</span></span>

4. <span data-ttu-id="f833a-120">Gebruik de [**methode IServiceCostsCollection.Summary.Get**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostsummary.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostsummary.getasync) om het overzicht van de servicekosten van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="f833a-120">Use the [**IServiceCostsCollection.Summary.Get**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostsummary.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostsummary.getasync) method to get the customer's service costs summary.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var serviceCostsSummary = partnerOperations.Customers.ById(selectedCustomerId).ServiceCosts.ByBillingPeriod(ServiceCostsBillingPeriod.MostRecent).Summary.Get();
```

## <a name="rest-request"></a><span data-ttu-id="f833a-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="f833a-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f833a-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="f833a-122">Request syntax</span></span>

| <span data-ttu-id="f833a-123">Methode</span><span class="sxs-lookup"><span data-stu-id="f833a-123">Method</span></span>  | <span data-ttu-id="f833a-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="f833a-124">Request URI</span></span>                                                                                                   |
|---------|---------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f833a-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="f833a-125">**GET**</span></span> | <span data-ttu-id="f833a-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/servicecosts/{billing-period} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="f833a-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/servicecosts/{billing-period} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="f833a-127">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="f833a-127">URI parameters</span></span>

<span data-ttu-id="f833a-128">Gebruik de volgende padparameters om de klant en de factureringsperiode te identificeren.</span><span class="sxs-lookup"><span data-stu-id="f833a-128">Use the following path parameters to identify the customer and the billing period.</span></span>

| <span data-ttu-id="f833a-129">Naam</span><span class="sxs-lookup"><span data-stu-id="f833a-129">Name</span></span>           | <span data-ttu-id="f833a-130">Type</span><span class="sxs-lookup"><span data-stu-id="f833a-130">Type</span></span>   | <span data-ttu-id="f833a-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="f833a-131">Required</span></span> | <span data-ttu-id="f833a-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f833a-132">Description</span></span>                                                                                                                      |
|----------------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f833a-133">customer-id</span><span class="sxs-lookup"><span data-stu-id="f833a-133">customer-id</span></span>    | <span data-ttu-id="f833a-134">guid</span><span class="sxs-lookup"><span data-stu-id="f833a-134">guid</span></span>   | <span data-ttu-id="f833a-135">Ja</span><span class="sxs-lookup"><span data-stu-id="f833a-135">Yes</span></span>      | <span data-ttu-id="f833a-136">Een klant-id met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="f833a-136">A GUID formatted customer ID that identifies the customer.</span></span>                                                                       |
| <span data-ttu-id="f833a-137">factureringsperiode</span><span class="sxs-lookup"><span data-stu-id="f833a-137">billing-period</span></span> | <span data-ttu-id="f833a-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="f833a-138">string</span></span> | <span data-ttu-id="f833a-139">Ja</span><span class="sxs-lookup"><span data-stu-id="f833a-139">Yes</span></span>      | <span data-ttu-id="f833a-140">Een indicator die de factureringsperiode vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f833a-140">An indicator that represents the billing period.</span></span> <span data-ttu-id="f833a-141">De enige ondersteunde waarde is MostRecent.</span><span class="sxs-lookup"><span data-stu-id="f833a-141">The only supported value is MostRecent.</span></span> <span data-ttu-id="f833a-142">Het geval van de tekenreeks maakt niet uit.</span><span class="sxs-lookup"><span data-stu-id="f833a-142">The case of the string does not matter.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="f833a-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="f833a-143">Request headers</span></span>

<span data-ttu-id="f833a-144">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="f833a-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="f833a-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="f833a-145">Request body</span></span>

<span data-ttu-id="f833a-146">Geen.</span><span class="sxs-lookup"><span data-stu-id="f833a-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="f833a-147">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="f833a-147">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65726577-c208-40fd-9735-8c85ac9cac68/servicecosts/mostrecent HTTP/1.1
Authorization: Bearer <authorization token>
Accept: application/json
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="f833a-148">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="f833a-148">REST response</span></span>

<span data-ttu-id="f833a-149">Als dit lukt, bevat de antwoord-body een [ServiceCostsSummary-resource](service-costs-resources.md) met informatie over de servicekosten.</span><span class="sxs-lookup"><span data-stu-id="f833a-149">If successful, the response body contains a [ServiceCostsSummary](service-costs-resources.md) resource that provides information about the service costs.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f833a-150">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="f833a-150">Response success and error codes</span></span>

<span data-ttu-id="f833a-151">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="f833a-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f833a-152">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="f833a-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f833a-153">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="f833a-153">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="f833a-154">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="f833a-154">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 766
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CV: gPPoyNX1X0asAAcw.0
MS-ServerId: 101112202
Date: Fri, 02 Dec 2016 18: 54: 38 GMT

{
    "billingStartDate": "2015-12-12T00:00:00Z",
    "billingEndDate": "2016-01-11T00:00:00Z",
    "pretaxTotal": 17.22,
    "tax": 0.0,
    "afterTaxTotal": 17.22,
    "currencySymbol": "$",
    "customerId": "ae1d5b32-f9ff-4252-b2bf-40e21937a51a",
    "details":
     [
        {
            "invoiceType": "Recurring",
            "summary": {
                "billingStartDate": "2015-12-12T00:00:00Z",
                "billingEndDate": "2016-01-11T00:00:00Z",
                "pretaxTotal": 17.22,
                "tax": 0.0,
                "afterTaxTotal": 17.22,
                "currencyCode": "USD",
                "currencySymbol": "$",
                "customerId": "ae1d5b32-f9ff-4252-b2bf-40e21937a51a",
                "links": {},
                "attributes": {
                    "objectType": "ServiceCostsSummary"
                }
            }
        },
        {
            "invoiceType": "OneTime",
            "summary": {
                "billingStartDate": "2019-04-01T00:00:00Z",
                "billingEndDate": "2019-04-30T23:59:59.9999999Z",
                "pretaxTotal": 2,
                "tax": 0.2,
                "afterTaxTotal": 2.2,
                "currencyCode": "USD",
                "currencySymbol": "$",
                "customerId": "ae1d5b32-f9ff-4252-b2bf-40e21937a51a",
                "links": {},
                "attributes": {
                    "objectType": "ServiceCostsSummary"
                }
            }
        }
    ],
    "links": {
        "serviceCostLineItems": {
            "uri": "/customers/ae1d5b32-f9ff-4252-b2bf-40e21937a51a/servicecosts/MostRecent/lineitems",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/ae1d5b32-f9ff-4252-b2bf-40e21937a51a/servicecosts/MostRecent",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "ServiceCostsSummary"
    }
}
```
