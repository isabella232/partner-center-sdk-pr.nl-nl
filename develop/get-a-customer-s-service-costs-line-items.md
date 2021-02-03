---
title: De regelitems van de servicekosten van een klant ophalen
description: Hiermee worden de service kosten regel items van een klant opgehaald voor de opgegeven facturerings periode.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c2034eaf11342493797688b44b634b8e9598e2e4
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767383"
---
# <a name="get-a-customers-service-costs-line-items"></a><span data-ttu-id="eb2d4-103">De regelitems van de servicekosten van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="eb2d4-103">Get a customer's service costs line items</span></span>

<span data-ttu-id="eb2d4-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="eb2d4-104">**Applies to:**</span></span>

- <span data-ttu-id="eb2d4-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="eb2d4-105">Partner Center</span></span>

<span data-ttu-id="eb2d4-106">Hiermee worden de service kosten regel items van een klant opgehaald voor de opgegeven facturerings periode.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-106">Gets a customer's service cost line items for the specified billing period.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eb2d4-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="eb2d4-107">Prerequisites</span></span>

- <span data-ttu-id="eb2d4-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="eb2d4-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="eb2d4-109">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-109">This scenario supports authentication with App+User credentials.</span></span>

- <span data-ttu-id="eb2d4-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eb2d4-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="eb2d4-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="eb2d4-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="eb2d4-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="eb2d4-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="eb2d4-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="eb2d4-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eb2d4-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="eb2d4-116">Een facturerings periode-indicator ( **`mostrecent`** ).</span><span class="sxs-lookup"><span data-stu-id="eb2d4-116">A billing period indicator (**`mostrecent`**).</span></span>

## <a name="c"></a><span data-ttu-id="eb2d4-117">C\#</span><span class="sxs-lookup"><span data-stu-id="eb2d4-117">C\#</span></span>

<span data-ttu-id="eb2d4-118">Een samen vatting van service kosten ophalen voor de opgegeven klant:</span><span class="sxs-lookup"><span data-stu-id="eb2d4-118">To retrieve a service costs summary for the specified customer:</span></span>

1. <span data-ttu-id="eb2d4-119">Roep de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-119">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="eb2d4-120">Gebruik de eigenschap [**ServiceCosts**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicecosts) om een interface te verkrijgen voor het verzamelen van bewerkingen van de klanten service.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-120">Use the [**ServiceCosts**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicecosts) property to get an interface to customer service costs collection operations.</span></span>

3. <span data-ttu-id="eb2d4-121">Roep de methode [**ByBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.icustomerservicecostscollection.bybillingperiod) aan met een lid van de inventarisatie [**ServiceCostsBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.models.servicecosts.servicecostsbillingperiod) om een [**IServiceCostsCollection**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostscollection)te retour neren.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-121">Call the [**ByBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.icustomerservicecostscollection.bybillingperiod) method with a member of the [**ServiceCostsBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.models.servicecosts.servicecostsbillingperiod) enumeration to return an [**IServiceCostsCollection**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostscollection).</span></span>

4. <span data-ttu-id="eb2d4-122">Gebruik de methode [**IServiceCostsCollection. regel items. Get**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostlineitemscollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostlineitemscollection.getasync) om de service kosten regel items van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-122">Use the [**IServiceCostsCollection.LineItems.Get**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostlineitemscollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostlineitemscollection.getasync) method to get the customer's service costs line items.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var serviceCostsSummary = partnerOperations.Customers.ById(selectedCustomerId).ServiceCosts.ByBillingPeriod(ServiceCostsBillingPeriod.MostRecent).LineItems.Get();
```

## <a name="rest-request"></a><span data-ttu-id="eb2d4-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="eb2d4-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="eb2d4-124">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="eb2d4-124">Request syntax</span></span>

| <span data-ttu-id="eb2d4-125">Methode</span><span class="sxs-lookup"><span data-stu-id="eb2d4-125">Method</span></span>  | <span data-ttu-id="eb2d4-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="eb2d4-126">Request URI</span></span>                                                                                                             |
|---------|-------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="eb2d4-127">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="eb2d4-127">**GET**</span></span> | <span data-ttu-id="eb2d4-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/servicecosts/{billing-period}/lineitems http/1.1</span><span class="sxs-lookup"><span data-stu-id="eb2d4-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/servicecosts/{billing-period}/lineitems HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="eb2d4-129">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="eb2d4-129">URI parameters</span></span>

<span data-ttu-id="eb2d4-130">Gebruik de volgende para meters voor het identificeren van de klant en de facturerings periode.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-130">Use the following path parameters to identify the customer and the billing period.</span></span>

| <span data-ttu-id="eb2d4-131">Naam</span><span class="sxs-lookup"><span data-stu-id="eb2d4-131">Name</span></span>           | <span data-ttu-id="eb2d4-132">Type</span><span class="sxs-lookup"><span data-stu-id="eb2d4-132">Type</span></span>   | <span data-ttu-id="eb2d4-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="eb2d4-133">Required</span></span> | <span data-ttu-id="eb2d4-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="eb2d4-134">Description</span></span>                                                                                                                      |
|----------------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="eb2d4-135">klant-id</span><span class="sxs-lookup"><span data-stu-id="eb2d4-135">customer-id</span></span>    | <span data-ttu-id="eb2d4-136">guid</span><span class="sxs-lookup"><span data-stu-id="eb2d4-136">guid</span></span>   | <span data-ttu-id="eb2d4-137">Yes</span><span class="sxs-lookup"><span data-stu-id="eb2d4-137">Yes</span></span>      | <span data-ttu-id="eb2d4-138">Een klant-ID met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-138">A GUID formatted customer ID that identifies the customer.</span></span>                                                                       |
| <span data-ttu-id="eb2d4-139">facturering-periode</span><span class="sxs-lookup"><span data-stu-id="eb2d4-139">billing-period</span></span> | <span data-ttu-id="eb2d4-140">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="eb2d4-140">string</span></span> | <span data-ttu-id="eb2d4-141">Yes</span><span class="sxs-lookup"><span data-stu-id="eb2d4-141">Yes</span></span>      | <span data-ttu-id="eb2d4-142">Een indicator die de facturerings periode vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-142">An indicator that represents the billing period.</span></span> <span data-ttu-id="eb2d4-143">De enige ondersteunde waarde is MostRecent.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-143">The only supported value is MostRecent.</span></span> <span data-ttu-id="eb2d4-144">Het geval van de teken reeks is niet van belang.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-144">The case of the string does not matter.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="eb2d4-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="eb2d4-145">Request headers</span></span>

<span data-ttu-id="eb2d4-146">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="eb2d4-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="eb2d4-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="eb2d4-147">Request body</span></span>

<span data-ttu-id="eb2d4-148">Geen.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="eb2d4-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="eb2d4-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65726577-c208-40fd-9735-8c85ac9cac68/servicecosts/mostrecent/lineitems HTTP/1.1
Authorization: Bearer <authorization token>
Accept: application/json
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="eb2d4-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="eb2d4-150">REST response</span></span>

<span data-ttu-id="eb2d4-151">Als dit lukt, bevat de antwoord tekst een [ServiceCostLineItem](service-costs-resources.md) -resource die informatie over de service kosten biedt.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-151">If successful, the response body contains a [ServiceCostLineItem](service-costs-resources.md) resource that provides information about the service costs.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb2d4-152">De volgende eigenschappen *gelden alleen voor* service kosten regel items waarbij het product een *eenmalige aankoop* is: **ProductID**, **productName**, **skuId**, **skuName**, **availabilityId**, **publisherId**, naam **Uitgever**, **termAndBillingCycle**, **discountDetails**.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-152">The following properties *only apply to* service cost line items where the product is a *one-time purchase*: **productId**, **productName**, **skuId**, **skuName**, **availabilityId**, **publisherId**, **publisherName**, **termAndBillingCycle**, **discountDetails**.</span></span> <span data-ttu-id="eb2d4-153">Deze eigenschappen *zijn niet van toepassing op* service regel items waarbij het product een *terugkerende aankoop* is.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-153">These properties *don't apply to* service line items where the product is a *recurring purchase*.</span></span> <span data-ttu-id="eb2d4-154">Deze eigenschappen *zijn bijvoorbeeld niet van toepassing* op op abonnementen gebaseerde Office 365 en Azure.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-154">For example, these properties *don't apply* to subscription-based Office 365 and Azure.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="eb2d4-155">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="eb2d4-155">Response success and error codes</span></span>

<span data-ttu-id="eb2d4-156">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="eb2d4-157">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-157">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="eb2d4-158">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="eb2d4-158">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="eb2d4-159">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="eb2d4-159">Response example</span></span>

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
