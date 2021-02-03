---
title: Gebruiksgegevens van klantlicenties ophalen
description: Het gebruik van inzichten over licenties voor een specifieke klant ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 1ee19e458ec65faa21034dd230b5388f7de981b2
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767497"
---
# <a name="get-customer-licenses-usage-information"></a><span data-ttu-id="61618-103">Gebruiksgegevens van klantlicenties ophalen</span><span class="sxs-lookup"><span data-stu-id="61618-103">Get customer licenses usage information</span></span>

<span data-ttu-id="61618-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="61618-104">**Applies To**</span></span>

- <span data-ttu-id="61618-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="61618-105">Partner Center</span></span>

<span data-ttu-id="61618-106">Het verkrijgen van inzichten over de implementatie van licenties voor een specifieke klant.</span><span class="sxs-lookup"><span data-stu-id="61618-106">How to get licenses deployment insights for a specific customer.</span></span>

> [!NOTE]
> <span data-ttu-id="61618-107">Dit scenario wordt vervangen door [gebruiks gegevens over licenties te verkrijgen](get-licenses-usage-information.md).</span><span class="sxs-lookup"><span data-stu-id="61618-107">This scenario is superceded by [Get licenses usage information](get-licenses-usage-information.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="61618-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="61618-108">Prerequisites</span></span>

<span data-ttu-id="61618-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="61618-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="61618-110">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="61618-110">This scenario supports authentication with App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="61618-111">C\#</span><span class="sxs-lookup"><span data-stu-id="61618-111">C\#</span></span>

<span data-ttu-id="61618-112">Als u geaggregeerde gegevens wilt ophalen voor de implementatie van een opgegeven klant, roept u eerst de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="61618-112">To retrieve aggregated data on deployment for a specified customer, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="61618-113">Krijg vervolgens een interface voor verzamelings bewerkingen op klant niveau van de eigenschap [**Analytics**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.analytics) .</span><span class="sxs-lookup"><span data-stu-id="61618-113">Then get an interface to customer level analytics collection operations from the [**Analytics**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.analytics) property.</span></span> <span data-ttu-id="61618-114">Vervolgens haalt u een interface op bij de analyse verzameling licenties op klant niveau vanuit de eigenschap [**licenties**](/dotnet/api/microsoft.store.partnercenter.analytics.icustomeranalyticscollection.licenses) .</span><span class="sxs-lookup"><span data-stu-id="61618-114">Next, retrieve an interface to the customer level licenses analytics collection from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.analytics.icustomeranalyticscollection.licenses) property.</span></span> <span data-ttu-id="61618-115">Roep tot slot de methode [**usage. Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) aan om de geaggregeerde gegevens over het gebruik van licenties op te halen.</span><span class="sxs-lookup"><span data-stu-id="61618-115">Finally, call the [**Usage.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) method to get the aggregated data on licenses usage.</span></span> <span data-ttu-id="61618-116">Als de methode slaagt, krijgt u een verzameling [**CustomerLicensesUsageInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.customerlicensesusageinsights) -objecten.</span><span class="sxs-lookup"><span data-stu-id="61618-116">If the method succeeds you'll get a collection of [**CustomerLicensesUsageInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.customerlicensesusageinsights) objects.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerIdToRetrieve;

var customerLicensesDeploymentAnalytics = partnerOperations.Customers.ById(customerIdToRetrieve).Analytics.Licenses.Usage.Get();
```

## <a name="rest-request"></a><span data-ttu-id="61618-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="61618-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="61618-118">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="61618-118">Request syntax</span></span>

| <span data-ttu-id="61618-119">Methode</span><span class="sxs-lookup"><span data-stu-id="61618-119">Method</span></span>  | <span data-ttu-id="61618-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="61618-120">Request URI</span></span>                                                                                              |
|---------|----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="61618-121">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="61618-121">**GET**</span></span> | <span data-ttu-id="61618-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Analytics/licenses/Usage http/1.1</span><span class="sxs-lookup"><span data-stu-id="61618-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/analytics/licenses/usage HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="61618-123">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="61618-123">URI parameter</span></span>

<span data-ttu-id="61618-124">Gebruik de volgende para meter voor het identificeren van de klant.</span><span class="sxs-lookup"><span data-stu-id="61618-124">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="61618-125">Naam</span><span class="sxs-lookup"><span data-stu-id="61618-125">Name</span></span>        | <span data-ttu-id="61618-126">Type</span><span class="sxs-lookup"><span data-stu-id="61618-126">Type</span></span> | <span data-ttu-id="61618-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="61618-127">Required</span></span> | <span data-ttu-id="61618-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="61618-128">Description</span></span>                                                |
|-------------|------|----------|------------------------------------------------------------|
| <span data-ttu-id="61618-129">klant-id</span><span class="sxs-lookup"><span data-stu-id="61618-129">customer-id</span></span> | <span data-ttu-id="61618-130">guid</span><span class="sxs-lookup"><span data-stu-id="61618-130">guid</span></span> | <span data-ttu-id="61618-131">Yes</span><span class="sxs-lookup"><span data-stu-id="61618-131">Yes</span></span>      | <span data-ttu-id="61618-132">Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="61618-132">A GUID formatted customer-id that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="61618-133">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="61618-133">Request headers</span></span>

<span data-ttu-id="61618-134">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="61618-134">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="61618-135">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="61618-135">Request body</span></span>

<span data-ttu-id="61618-136">Geen.</span><span class="sxs-lookup"><span data-stu-id="61618-136">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="61618-137">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="61618-137">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/analytics/licenses/usage HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f657d2a8-9ed6-41b4-abfc-3cf4abebd62f
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="61618-138">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="61618-138">REST response</span></span>

<span data-ttu-id="61618-139">Als dit lukt, bevat de antwoord tekst een verzameling [CustomerLicensesUsageInsights](analytics-resources.md#customerlicensesusageinsights) -resources die informatie geven over het gebruik van licenties.</span><span class="sxs-lookup"><span data-stu-id="61618-139">If successful, the response body contains a collection of [CustomerLicensesUsageInsights](analytics-resources.md#customerlicensesusageinsights) resources that provide information about licenses usage.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="61618-140">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="61618-140">Response success and error codes</span></span>

<span data-ttu-id="61618-141">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="61618-141">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="61618-142">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="61618-142">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="61618-143">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="61618-143">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="61618-144">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="61618-144">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1726
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
MS-RequestId: f657d2a8-9ed6-41b4-abfc-3cf4abebd62f
MS-CV: 0mufM0K1kEOoR7oI.0
MS-ServerId: 030020525
Date: Wed, 15 Mar 2017 01:19:58 GMT

{
    "totalCount": 5,
    "items": [{
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "OFFICE 365 BUSINESS ESSENTIALS",
            "licensesActive": 0,
            "licensesQualified": 1,
            "usagePercent": 0.0,
            "workloadName": "Exchange",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesUsageInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "OFFICE 365 BUSINESS ESSENTIALS",
            "licensesActive": 0,
            "licensesQualified": 1,
            "usagePercent": 0.0,
            "workloadName": "SharePoint",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesUsageInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "OFFICE 365 BUSINESS ESSENTIALS",
            "licensesActive": 0,
            "licensesQualified": 1,
            "usagePercent": 0.0,
            "workloadName": "Skype For Business",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesUsageInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "EXCHANGE ONLINE (PLAN 1)",
            "licensesActive": 0,
            "licensesQualified": 5,
            "usagePercent": 0.0,
            "workloadName": "Exchange",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesUsageInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "EXCHANGE ONLINE ARCHIVING FOR EXCHANGE ONLINE",
            "licensesActive": 0,
            "licensesQualified": 2,
            "usagePercent": 0.0,
            "workloadName": "Exchange",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesUsageInsights"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
