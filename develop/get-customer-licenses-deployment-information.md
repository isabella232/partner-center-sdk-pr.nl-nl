---
title: Implementatiegegevens van klantlicenties ophalen
description: Inzicht krijgen in de implementatie van licenties voor een specifieke klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 91fe9da185aa59025d4dc8263257b207edb4a5be
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446459"
---
# <a name="get-customer-licenses-deployment-information"></a><span data-ttu-id="af627-103">Implementatiegegevens van klantlicenties ophalen</span><span class="sxs-lookup"><span data-stu-id="af627-103">Get customer licenses deployment information</span></span>

<span data-ttu-id="af627-104">Inzicht krijgen in de implementatie van licenties voor een specifieke klant.</span><span class="sxs-lookup"><span data-stu-id="af627-104">How to get licenses deployment insights for a specific customer.</span></span>

> [!NOTE]
> <span data-ttu-id="af627-105">Dit scenario wordt vervangen door Implementatiegegevens voor [licenties verkrijgen.](get-licenses-deployment-information.md)</span><span class="sxs-lookup"><span data-stu-id="af627-105">This scenario is superceded by [Get licenses deployment information](get-licenses-deployment-information.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="af627-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="af627-106">Prerequisites</span></span>

<span data-ttu-id="af627-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="af627-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="af627-108">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="af627-108">This scenario supports authentication with App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="af627-109">C\#</span><span class="sxs-lookup"><span data-stu-id="af627-109">C\#</span></span>

<span data-ttu-id="af627-110">Als u geaggregeerde gegevens over de implementatie voor een opgegeven klant wilt ophalen, roept u eerst de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="af627-110">To retrieve aggregated data on deployment for a specified customer, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="af627-111">Haal vervolgens een interface op naar bewerkingen voor het verzamelen van analyses op klantniveau van de [**eigenschap Analytics.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.analytics)</span><span class="sxs-lookup"><span data-stu-id="af627-111">Then get an interface to customer level analytics collection operations from the [**Analytics**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.analytics) property.</span></span> <span data-ttu-id="af627-112">Haal vervolgens een interface op voor de analyseverzameling licenties op klantniveau uit de [**eigenschap Licenties.**](/dotnet/api/microsoft.store.partnercenter.analytics.icustomeranalyticscollection.licenses)</span><span class="sxs-lookup"><span data-stu-id="af627-112">Next, retrieve an interface to the customer level licenses analytics collection from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.analytics.icustomeranalyticscollection.licenses) property.</span></span> <span data-ttu-id="af627-113">Roep ten slotte de [**methode Deployment.Get aan**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) om de geaggregeerde gegevens over de implementatie van licenties op te halen.</span><span class="sxs-lookup"><span data-stu-id="af627-113">Finally, call the [**Deployment.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) method to get the aggregated data on licenses deployment.</span></span> <span data-ttu-id="af627-114">Als de methode slaagt, krijgt u een verzameling [**CustomerLicensesDeploymentInsights-objecten.**](/dotnet/api/microsoft.store.partnercenter.models.analytics.customerlicensesdeploymentinsights)</span><span class="sxs-lookup"><span data-stu-id="af627-114">If the method succeeds, you'll get a collection of [**CustomerLicensesDeploymentInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.customerlicensesdeploymentinsights) objects.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerIdToRetrieve;

var customerLicensesDeploymentAnalytics = partnerOperations.Customers.ById(customerIdToRetrieve).Analytics.Licenses.Deployment.Get();
```

## <a name="rest-request"></a><span data-ttu-id="af627-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="af627-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="af627-116">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="af627-116">Request syntax</span></span>

| <span data-ttu-id="af627-117">Methode</span><span class="sxs-lookup"><span data-stu-id="af627-117">Method</span></span>  | <span data-ttu-id="af627-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="af627-118">Request URI</span></span>                                                                                                   |
|---------|---------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="af627-119">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="af627-119">**GET**</span></span> | <span data-ttu-id="af627-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/analytics/licenses/deployment HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="af627-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/analytics/licenses/deployment HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="af627-121">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="af627-121">URI parameter</span></span>

<span data-ttu-id="af627-122">Gebruik de volgende padparameter om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="af627-122">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="af627-123">Naam</span><span class="sxs-lookup"><span data-stu-id="af627-123">Name</span></span>        | <span data-ttu-id="af627-124">Type</span><span class="sxs-lookup"><span data-stu-id="af627-124">Type</span></span> | <span data-ttu-id="af627-125">Vereist</span><span class="sxs-lookup"><span data-stu-id="af627-125">Required</span></span> | <span data-ttu-id="af627-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="af627-126">Description</span></span>                                                |
|-------------|------|----------|------------------------------------------------------------|
| <span data-ttu-id="af627-127">customer-id</span><span class="sxs-lookup"><span data-stu-id="af627-127">customer-id</span></span> | <span data-ttu-id="af627-128">guid</span><span class="sxs-lookup"><span data-stu-id="af627-128">guid</span></span> | <span data-ttu-id="af627-129">Ja</span><span class="sxs-lookup"><span data-stu-id="af627-129">Yes</span></span>      | <span data-ttu-id="af627-130">Een met GUID opgemaakte klant-id die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="af627-130">A GUID formatted customer-id that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="af627-131">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="af627-131">Request headers</span></span>

<span data-ttu-id="af627-132">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="af627-132">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="af627-133">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="af627-133">Request body</span></span>

<span data-ttu-id="af627-134">Geen.</span><span class="sxs-lookup"><span data-stu-id="af627-134">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="af627-135">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="af627-135">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/analytics/licenses/deployment HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b01b8759-4dbe-4605-adb7-e5839a796c33
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="af627-136">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="af627-136">REST response</span></span>

<span data-ttu-id="af627-137">Als dit lukt, bevat de antwoord-body een verzameling [CustomerLicensesDeploymentInsights-resources](analytics-resources.md#customerlicensesdeploymentinsights) die informatie bieden over de geïmplementeerde licenties.</span><span class="sxs-lookup"><span data-stu-id="af627-137">If successful, the response body contains a collection of [CustomerLicensesDeploymentInsights](analytics-resources.md#customerlicensesdeploymentinsights) resources that provide information about the licenses deployed.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="af627-138">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="af627-138">Response success and error codes</span></span>

<span data-ttu-id="af627-139">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="af627-139">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="af627-140">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="af627-140">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="af627-141">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="af627-141">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="af627-142">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="af627-142">Response example</span></span>

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
