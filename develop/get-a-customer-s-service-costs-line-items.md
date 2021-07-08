---
title: De regelitems van de servicekosten van een klant ophalen
description: Hiermee haalt u de servicekostenregelitems van een klant op voor de opgegeven factureringsperiode.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1bc2914d7c8d41c6d806131444fdc241aa1feb90
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874938"
---
# <a name="get-a-customers-service-costs-line-items"></a><span data-ttu-id="c3366-103">De regelitems van de servicekosten van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="c3366-103">Get a customer's service costs line items</span></span>

<span data-ttu-id="c3366-104">Hiermee haalt u de servicekostenregelitems van een klant op voor de opgegeven factureringsperiode.</span><span class="sxs-lookup"><span data-stu-id="c3366-104">Gets a customer's service cost line items for the specified billing period.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3366-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c3366-105">Prerequisites</span></span>

- <span data-ttu-id="c3366-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c3366-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c3366-107">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="c3366-107">This scenario supports authentication with App+User credentials.</span></span>

- <span data-ttu-id="c3366-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c3366-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="c3366-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="c3366-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="c3366-110">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="c3366-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="c3366-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="c3366-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="c3366-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="c3366-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="c3366-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c3366-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="c3366-114">Een factureringsperiode-indicator ( **`mostrecent`** ).</span><span class="sxs-lookup"><span data-stu-id="c3366-114">A billing period indicator (**`mostrecent`**).</span></span>

## <a name="c"></a><span data-ttu-id="c3366-115">C\#</span><span class="sxs-lookup"><span data-stu-id="c3366-115">C\#</span></span>

<span data-ttu-id="c3366-116">Een samenvatting van de servicekosten voor de opgegeven klant ophalen:</span><span class="sxs-lookup"><span data-stu-id="c3366-116">To retrieve a service costs summary for the specified customer:</span></span>

1. <span data-ttu-id="c3366-117">Roep de [**methode IAggregatePartner.Customers.ById aan**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="c3366-117">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="c3366-118">Gebruik de [**eigenschap ServiceCosts om**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicecosts) een interface te krijgen voor het verzamelen van kosten van de klantenservice.</span><span class="sxs-lookup"><span data-stu-id="c3366-118">Use the [**ServiceCosts**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicecosts) property to get an interface to customer service costs collection operations.</span></span>

3. <span data-ttu-id="c3366-119">Roep de [**methode ByBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.icustomerservicecostscollection.bybillingperiod) aan met een lid van de enumeratie [**ServiceCostsBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.models.servicecosts.servicecostsbillingperiod) om een [**IServiceCostsCollection te retourneren.**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostscollection)</span><span class="sxs-lookup"><span data-stu-id="c3366-119">Call the [**ByBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.icustomerservicecostscollection.bybillingperiod) method with a member of the [**ServiceCostsBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.models.servicecosts.servicecostsbillingperiod) enumeration to return an [**IServiceCostsCollection**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostscollection).</span></span>

4. <span data-ttu-id="c3366-120">Gebruik de [**methode IServiceCostsCollection.LineItems.Get**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostlineitemscollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostlineitemscollection.getasync) om de regelitems voor servicekosten van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="c3366-120">Use the [**IServiceCostsCollection.LineItems.Get**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostlineitemscollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostlineitemscollection.getasync) method to get the customer's service costs line items.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var serviceCostsSummary = partnerOperations.Customers.ById(selectedCustomerId).ServiceCosts.ByBillingPeriod(ServiceCostsBillingPeriod.MostRecent).LineItems.Get();
```

## <a name="rest-request"></a><span data-ttu-id="c3366-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c3366-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c3366-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="c3366-122">Request syntax</span></span>

| <span data-ttu-id="c3366-123">Methode</span><span class="sxs-lookup"><span data-stu-id="c3366-123">Method</span></span>  | <span data-ttu-id="c3366-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c3366-124">Request URI</span></span>                                                                                                             |
|---------|-------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c3366-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="c3366-125">**GET**</span></span> | <span data-ttu-id="c3366-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/servicecosts/{billing-period}/lineitems HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c3366-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/servicecosts/{billing-period}/lineitems HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="c3366-127">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="c3366-127">URI parameters</span></span>

<span data-ttu-id="c3366-128">Gebruik de volgende padparameters om de klant en de factureringsperiode te identificeren.</span><span class="sxs-lookup"><span data-stu-id="c3366-128">Use the following path parameters to identify the customer and the billing period.</span></span>

| <span data-ttu-id="c3366-129">Naam</span><span class="sxs-lookup"><span data-stu-id="c3366-129">Name</span></span>           | <span data-ttu-id="c3366-130">Type</span><span class="sxs-lookup"><span data-stu-id="c3366-130">Type</span></span>   | <span data-ttu-id="c3366-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="c3366-131">Required</span></span> | <span data-ttu-id="c3366-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c3366-132">Description</span></span>                                                                                                                      |
|----------------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c3366-133">customer-id</span><span class="sxs-lookup"><span data-stu-id="c3366-133">customer-id</span></span>    | <span data-ttu-id="c3366-134">guid</span><span class="sxs-lookup"><span data-stu-id="c3366-134">guid</span></span>   | <span data-ttu-id="c3366-135">Ja</span><span class="sxs-lookup"><span data-stu-id="c3366-135">Yes</span></span>      | <span data-ttu-id="c3366-136">Een klant-id met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="c3366-136">A GUID formatted customer ID that identifies the customer.</span></span>                                                                       |
| <span data-ttu-id="c3366-137">factureringsperiode</span><span class="sxs-lookup"><span data-stu-id="c3366-137">billing-period</span></span> | <span data-ttu-id="c3366-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="c3366-138">string</span></span> | <span data-ttu-id="c3366-139">Ja</span><span class="sxs-lookup"><span data-stu-id="c3366-139">Yes</span></span>      | <span data-ttu-id="c3366-140">Een indicator die de factureringsperiode vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c3366-140">An indicator that represents the billing period.</span></span> <span data-ttu-id="c3366-141">De enige ondersteunde waarde is MostRecent.</span><span class="sxs-lookup"><span data-stu-id="c3366-141">The only supported value is MostRecent.</span></span> <span data-ttu-id="c3366-142">Het geval van de tekenreeks is niet van belang.</span><span class="sxs-lookup"><span data-stu-id="c3366-142">The case of the string does not matter.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c3366-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c3366-143">Request headers</span></span>

<span data-ttu-id="c3366-144">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="c3366-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c3366-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c3366-145">Request body</span></span>

<span data-ttu-id="c3366-146">Geen.</span><span class="sxs-lookup"><span data-stu-id="c3366-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c3366-147">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c3366-147">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65726577-c208-40fd-9735-8c85ac9cac68/servicecosts/mostrecent/lineitems HTTP/1.1
Authorization: Bearer <authorization token>
Accept: application/json
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="c3366-148">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c3366-148">REST response</span></span>

<span data-ttu-id="c3366-149">Als dit lukt, bevat de antwoord-body een [ServiceCostLineItem-resource](service-costs-resources.md) die informatie biedt over de servicekosten.</span><span class="sxs-lookup"><span data-stu-id="c3366-149">If successful, the response body contains a [ServiceCostLineItem](service-costs-resources.md) resource that provides information about the service costs.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c3366-150">De volgende  eigenschappen zijn alleen van toepassing op servicekostenregelitems waarbij het product een een *time-aankoop* is: **productId**, **productName**, **skuId**, **skuName,** **availabilityId**, **publisherId,** **publisherName**, **termAndBillingCycle,** **discountDetails**.</span><span class="sxs-lookup"><span data-stu-id="c3366-150">The following properties *only apply to* service cost line items where the product is a *one-time purchase*: **productId**, **productName**, **skuId**, **skuName**, **availabilityId**, **publisherId**, **publisherName**, **termAndBillingCycle**, **discountDetails**.</span></span> <span data-ttu-id="c3366-151">Deze eigenschappen *zijn niet van toepassing op* serviceregelitems waarbij het product een terugkerende aankoop *is.*</span><span class="sxs-lookup"><span data-stu-id="c3366-151">These properties *don't apply to* service line items where the product is a *recurring purchase*.</span></span> <span data-ttu-id="c3366-152">Deze eigenschappen zijn bijvoorbeeld niet *van toepassing op* abonnementsgebaseerde Office 365 en Azure.</span><span class="sxs-lookup"><span data-stu-id="c3366-152">For example, these properties *don't apply* to subscription-based Office 365 and Azure.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c3366-153">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="c3366-153">Response success and error codes</span></span>

<span data-ttu-id="c3366-154">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="c3366-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c3366-155">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c3366-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c3366-156">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="c3366-156">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c3366-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="c3366-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 2148
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CV: gPPoyNX1X0asAAcw.0
MS-ServerId: 101112202
Date: Fri, 02 Dec 2016 18: 54: 38 GMT

{
    "attributes": {
        "objectType": "Collection"
    },
    "items":
    [{
            "afterTaxTotal": 0.0,
            "chargeType": "PURCHASE FEE",
            "currencyCode": "USD",
            "currencySymbol": "$",
            "customerId": "ae1d5b32-f9ff-4252-b2bf-40e21937a51a",
            "customerName": "AABB CCDD",
            "endDate": "2016-01-11T00:00:00",
            "offerId": "11E3C9A9-24A2-4CFD-9F60-A9797D68E296",
            "offerName": "Project for Office 365 (Government Pricing)",
            "orderId": "4FEB262A-FAF3-4710-B216-D563421B006F",
            "pretaxTotal": 0.0,
            "quantity": 1.0,
            "resellerMPNId": "-1",
            "startDate": "2015-12-15T00:00:00",
            "subscriptionFriendlyName": "Project Pro for Office 365 (Government Pricing)",
            "subscriptionId": "71B5BCDD-51C8-4BF2-B704-D3432EE33064",
            "tax": 0.0,
            "unitPrice": 0.0,
            "invoiceNumber": "T000003163",
            "invoiceType": "OneTime",
            "productId": "DZH318Z0BJR6",
            "skuId": "0001",
            "availabilityId": "DZH318Z0BMFK",
            "productName": "Azure Managed Experience",
            "skuName": "Azure Managed Experience - Optimize",
            "publisherName": "Microsoft",
            "publisherId": "01323244",
            "termAndBillingCycle": "",
            "discountDetails": "N/A"
        }, {
            "afterTaxTotal": 17.219999999999999,
            "chargeType": "CYCLE FEE",
            "currencyCode": "USD",
            "currencySymbol": "$",
            "customerId": "ae1d5b32-f9ff-4252-b2bf-40e21937a51a",
            "customerName": "AABB CCDD",
            "endDate": "2016-02-11T00:00:00",
            "offerId": "11E3C9A9-24A2-4CFD-9F60-A9797D68E296",
            "offerName": "Project for Office 365 (Government Pricing)",
            "orderId": "4FEB262A-FAF3-4710-B216-D563421B006F",
            "pretaxTotal": 17.219999999999999,
            "quantity": 1.0,
            "resellerMPNId": "-1",
            "startDate": "2016-01-12T00:00:00",
            "subscriptionFriendlyName": "Project Pro for Office 365 (Government Pricing)",
            "subscriptionId": "71B5BCDD-51C8-4BF2-B704-D3432EE33064",
            "tax": 0.0,
            "unitPrice": 17.219999999999999,
            "invoiceNumber": "D000003163",
            "invoiceType": "Recurring",
            "productId": "DZH318Z0BJR7",
            "skuId": "0001",
            "availabilityId": "DZH318Z0BTTTT",
            "productName": "NGINX Plus",
            "skuName": "NGINX Plus (Ubuntu 14.04)",
            "publisherName": "Nginx, Inc.",
            "publisherId": "212336222",
            "termAndBillingCycle": "30 Days Trial",
            "discountDetails": "20%"
        }
    ],
    "links": {
        "self": {
            "headers": [],
            "method": "GET",
            "uri": "/customers/ae1d5b32-f9ff-4252-b2bf-40e21937a51a/servicecosts/MostRecent/lineitems"
        }
    },
    "totalCount": 2
}
```
