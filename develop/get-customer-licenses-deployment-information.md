---
title: Implementatiegegevens van klantlicenties ophalen
description: Het verkrijgen van inzichten over de implementatie van licenties voor een specifieke klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 3a39c6c908048305ff2dabf85a29d7ddc3628500
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767546"
---
# <a name="get-customer-licenses-deployment-information"></a><span data-ttu-id="ecbaa-103">Implementatiegegevens van klantlicenties ophalen</span><span class="sxs-lookup"><span data-stu-id="ecbaa-103">Get customer licenses deployment information</span></span>

<span data-ttu-id="ecbaa-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="ecbaa-104">**Applies To**</span></span>

- <span data-ttu-id="ecbaa-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="ecbaa-105">Partner Center</span></span>

<span data-ttu-id="ecbaa-106">Het verkrijgen van inzichten over de implementatie van licenties voor een specifieke klant.</span><span class="sxs-lookup"><span data-stu-id="ecbaa-106">How to get licenses deployment insights for a specific customer.</span></span>

> [!NOTE]
> <span data-ttu-id="ecbaa-107">Dit scenario wordt vervangen door [informatie over de implementatie van licenties](get-licenses-deployment-information.md).</span><span class="sxs-lookup"><span data-stu-id="ecbaa-107">This scenario is superceded by [Get licenses deployment information](get-licenses-deployment-information.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ecbaa-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ecbaa-108">Prerequisites</span></span>

<span data-ttu-id="ecbaa-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ecbaa-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ecbaa-110">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="ecbaa-110">This scenario supports authentication with App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="ecbaa-111">C\#</span><span class="sxs-lookup"><span data-stu-id="ecbaa-111">C\#</span></span>

<span data-ttu-id="ecbaa-112">Als u geaggregeerde gegevens wilt ophalen voor de implementatie van een opgegeven klant, roept u eerst de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="ecbaa-112">To retrieve aggregated data on deployment for a specified customer, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="ecbaa-113">Krijg vervolgens een interface voor verzamelings bewerkingen op klant niveau van de eigenschap [**Analytics**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.analytics) .</span><span class="sxs-lookup"><span data-stu-id="ecbaa-113">Then get an interface to customer level analytics collection operations from the [**Analytics**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.analytics) property.</span></span> <span data-ttu-id="ecbaa-114">Vervolgens haalt u een interface op bij de analyse verzameling licenties op klant niveau vanuit de eigenschap [**licenties**](/dotnet/api/microsoft.store.partnercenter.analytics.icustomeranalyticscollection.licenses) .</span><span class="sxs-lookup"><span data-stu-id="ecbaa-114">Next, retrieve an interface to the customer level licenses analytics collection from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.analytics.icustomeranalyticscollection.licenses) property.</span></span> <span data-ttu-id="ecbaa-115">Roep ten slotte de [**implementatie. Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) -methode aan om de geaggregeerde gegevens over de implementatie van licenties op te halen.</span><span class="sxs-lookup"><span data-stu-id="ecbaa-115">Finally, call the [**Deployment.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) method to get the aggregated data on licenses deployment.</span></span> <span data-ttu-id="ecbaa-116">Als de methode slaagt, krijgt u een verzameling [**CustomerLicensesDeploymentInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.customerlicensesdeploymentinsights) -objecten.</span><span class="sxs-lookup"><span data-stu-id="ecbaa-116">If the method succeeds you'll get a collection of [**CustomerLicensesDeploymentInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.customerlicensesdeploymentinsights) objects.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerIdToRetrieve;

var customerLicensesDeploymentAnalytics = partnerOperations.Customers.ById(customerIdToRetrieve).Analytics.Licenses.Deployment.Get();
```

## <a name="rest-request"></a><span data-ttu-id="ecbaa-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="ecbaa-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ecbaa-118">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ecbaa-118">Request syntax</span></span>

| <span data-ttu-id="ecbaa-119">Methode</span><span class="sxs-lookup"><span data-stu-id="ecbaa-119">Method</span></span>  | <span data-ttu-id="ecbaa-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="ecbaa-120">Request URI</span></span>                                                                                                   |
|---------|---------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ecbaa-121">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ecbaa-121">**GET**</span></span> | <span data-ttu-id="ecbaa-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Analytics/licenses/Deployment http/1.1</span><span class="sxs-lookup"><span data-stu-id="ecbaa-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/analytics/licenses/deployment HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="ecbaa-123">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="ecbaa-123">URI parameter</span></span>

<span data-ttu-id="ecbaa-124">Gebruik de volgende para meter voor het identificeren van de klant.</span><span class="sxs-lookup"><span data-stu-id="ecbaa-124">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="ecbaa-125">Naam</span><span class="sxs-lookup"><span data-stu-id="ecbaa-125">Name</span></span>        | <span data-ttu-id="ecbaa-126">Type</span><span class="sxs-lookup"><span data-stu-id="ecbaa-126">Type</span></span> | <span data-ttu-id="ecbaa-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="ecbaa-127">Required</span></span> | <span data-ttu-id="ecbaa-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ecbaa-128">Description</span></span>                                                |
|-------------|------|----------|------------------------------------------------------------|
| <span data-ttu-id="ecbaa-129">klant-id</span><span class="sxs-lookup"><span data-stu-id="ecbaa-129">customer-id</span></span> | <span data-ttu-id="ecbaa-130">guid</span><span class="sxs-lookup"><span data-stu-id="ecbaa-130">guid</span></span> | <span data-ttu-id="ecbaa-131">Yes</span><span class="sxs-lookup"><span data-stu-id="ecbaa-131">Yes</span></span>      | <span data-ttu-id="ecbaa-132">Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="ecbaa-132">A GUID formatted customer-id that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ecbaa-133">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ecbaa-133">Request headers</span></span>

<span data-ttu-id="ecbaa-134">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="ecbaa-134">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ecbaa-135">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="ecbaa-135">Request body</span></span>

<span data-ttu-id="ecbaa-136">Geen.</span><span class="sxs-lookup"><span data-stu-id="ecbaa-136">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="ecbaa-137">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ecbaa-137">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/analytics/licenses/deployment HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b01b8759-4dbe-4605-adb7-e5839a796c33
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="ecbaa-138">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="ecbaa-138">REST response</span></span>

<span data-ttu-id="ecbaa-139">Als dit lukt, bevat de antwoord tekst een verzameling [CustomerLicensesDeploymentInsights](analytics-resources.md#customerlicensesdeploymentinsights) -resources die informatie geven over de geïmplementeerde licenties.</span><span class="sxs-lookup"><span data-stu-id="ecbaa-139">If successful, the response body contains a collection of [CustomerLicensesDeploymentInsights](analytics-resources.md#customerlicensesdeploymentinsights) resources that provide information about the licenses deployed.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ecbaa-140">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="ecbaa-140">Response success and error codes</span></span>

<span data-ttu-id="ecbaa-141">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="ecbaa-141">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ecbaa-142">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="ecbaa-142">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ecbaa-143">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="ecbaa-143">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ecbaa-144">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="ecbaa-144">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1012
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
MS-RequestId: b01b8759-4dbe-4605-adb7-e5839a796c33
MS-CV: deEp2Wy6DUitMCYA.0
MS-ServerId: 102030524
Date: Wed, 15 Mar 2017 01:19:18 GMT

{
    "totalCount": 3,
    "items": [{
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "OFFICE 365 BUSINESS ESSENTIALS",
            "licensesDeployed": 0,
            "deploymentPercent": 0.0,
            "licensesSold": 1,
            "processedDateTime": "2017-03-14T03:25:16.36+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesDeploymentInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "EXCHANGE ONLINE (PLAN 1)",
            "licensesDeployed": 0,
            "deploymentPercent": 0.0,
            "licensesSold": 5,
            "processedDateTime": "2017-03-14T03:25:16.36+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesDeploymentInsights"
            }
        }, {
            "customerName": "DT DEMO CSP CUSTOMER 005",
            "productName": "EXCHANGE ONLINE ARCHIVING FOR EXCHANGE ONLINE",
            "licensesDeployed": 0,
            "deploymentPercent": 0.0,
            "licensesSold": 2,
            "processedDateTime": "2017-03-14T03:25:16.36+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "CustomerLicensesDeploymentInsights"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
