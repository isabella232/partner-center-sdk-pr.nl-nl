---
title: Implementatiegegevens van partnerlicenties ophalen
description: Informatie over het verkrijgen van implementatie gegevens van partner licenties voor het toevoegen van alle klanten.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 229f63d4df4f59cd0fde2bd0fc5e3f10cf6b25c0
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767540"
---
# <a name="get-partner-licenses-deployment-information"></a><span data-ttu-id="d3be8-103">Implementatiegegevens van partnerlicenties ophalen</span><span class="sxs-lookup"><span data-stu-id="d3be8-103">Get partner licenses deployment information</span></span>

<span data-ttu-id="d3be8-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="d3be8-104">**Applies To**</span></span>

- <span data-ttu-id="d3be8-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="d3be8-105">Partner Center</span></span>

<span data-ttu-id="d3be8-106">Informatie over het verkrijgen van implementatie gegevens van partner licenties voor het toevoegen van alle klanten.</span><span class="sxs-lookup"><span data-stu-id="d3be8-106">How to get partner licenses deployment information aggregated to include all customers.</span></span>

> [!NOTE]
> <span data-ttu-id="d3be8-107">Dit scenario wordt vervangen door [informatie over de implementatie van licenties](get-licenses-deployment-information.md).</span><span class="sxs-lookup"><span data-stu-id="d3be8-107">This scenario is superceded by [Get licenses deployment information](get-licenses-deployment-information.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d3be8-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d3be8-108">Prerequisites</span></span>

<span data-ttu-id="d3be8-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d3be8-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d3be8-110">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="d3be8-110">This scenario supports authentication with App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="d3be8-111">C\#</span><span class="sxs-lookup"><span data-stu-id="d3be8-111">C\#</span></span>

<span data-ttu-id="d3be8-112">Als u geaggregeerde gegevens voor de implementatie van licenties wilt ophalen, moet u eerst een interface op het niveau van de verzameling van de [**IAggregatePartner. Analytics**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics) -eigenschappen ophalen.</span><span class="sxs-lookup"><span data-stu-id="d3be8-112">To retrieve aggregated data on licenses deployment, first get an interface to partner level analytics collection operations from the [**IAggregatePartner.Analytics**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics) property.</span></span> <span data-ttu-id="d3be8-113">Haal vervolgens een interface op bij de verzameling van de licenties voor het partner niveau-analyse van de eigenschap [**licenties**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses) .</span><span class="sxs-lookup"><span data-stu-id="d3be8-113">Then retrieve an interface to the partner level licenses analytics collection from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses) property.</span></span> <span data-ttu-id="d3be8-114">Roep ten slotte de [**implementatie. Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) -methode aan om de geaggregeerde gegevens over de implementatie van licenties op te halen.</span><span class="sxs-lookup"><span data-stu-id="d3be8-114">Finally, call the [**Deployment.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) method to get the aggregated data on licenses deployment.</span></span> <span data-ttu-id="d3be8-115">Als de methode slaagt, krijgt u een verzameling [**PartnerLicensesDeploymentInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesdeploymentinsights) -objecten.</span><span class="sxs-lookup"><span data-stu-id="d3be8-115">If the method succeeds you'll get a collection of [**PartnerLicensesDeploymentInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesdeploymentinsights) objects.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var partnerLicensesDeploymentAnalytics = partnerOperations.Analytics.Licenses.Deployment.Get();
```

## <a name="rest-request"></a><span data-ttu-id="d3be8-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="d3be8-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d3be8-117">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d3be8-117">Request syntax</span></span>

| <span data-ttu-id="d3be8-118">Methode</span><span class="sxs-lookup"><span data-stu-id="d3be8-118">Method</span></span>  | <span data-ttu-id="d3be8-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="d3be8-119">Request URI</span></span>                                                                           |
|---------|---------------------------------------------------------------------------------------|
| <span data-ttu-id="d3be8-120">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="d3be8-120">**GET**</span></span> | <span data-ttu-id="d3be8-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/Analytics/licenses/Deployment http/1.1</span><span class="sxs-lookup"><span data-stu-id="d3be8-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/licenses/deployment HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d3be8-122">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="d3be8-122">Request headers</span></span>

<span data-ttu-id="d3be8-123">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d3be8-123">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d3be8-124">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="d3be8-124">Request body</span></span>

<span data-ttu-id="d3be8-125">Geen.</span><span class="sxs-lookup"><span data-stu-id="d3be8-125">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d3be8-126">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d3be8-126">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/analytics/licenses/deployment HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 25b6edd5-1f53-456b-b48c-c64f60ec2dda
MS-CorrelationId: 6492b9d6-5629-429b-934c-040b1946e760
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="d3be8-127">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="d3be8-127">REST response</span></span>

<span data-ttu-id="d3be8-128">Als dit lukt, bevat de antwoord tekst een verzameling [PartnerLicensesDeploymentInsights](analytics-resources.md#partnerlicensesdeploymentinsights) -resources die informatie geven over de geïmplementeerde licenties.</span><span class="sxs-lookup"><span data-stu-id="d3be8-128">If successful, the response body contains a collection of [PartnerLicensesDeploymentInsights](analytics-resources.md#partnerlicensesdeploymentinsights) resources that provide information about the licenses deployed.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d3be8-129">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="d3be8-129">Response success and error codes</span></span>

<span data-ttu-id="d3be8-130">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="d3be8-130">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d3be8-131">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="d3be8-131">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d3be8-132">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="d3be8-132">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d3be8-133">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="d3be8-133">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 487
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 6492b9d6-5629-429b-934c-040b1946e760
MS-RequestId: 25b6edd5-1f53-456b-b48c-c64f60ec2dda
MS-CV: f0trvmq8mEScHcFS.0
MS-ServerId: 102030524
Date: Tue, 14 Mar 2017 17:55:01 GMT

{
    "totalCount": 2,
    "items": [{
            "proratedDeploymentPercent": 0.0,
            "licensesSold": 343,
            "processedDateTime": "2017-03-10T00:00:00+00:00",
            "serviceName": "crm",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesDeploymentInsights"
            }
        }, {
            "proratedDeploymentPercent": 1.0,
            "licensesSold": 4464,
            "processedDateTime": "2017-03-14T03:25:16.36+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesDeploymentInsights"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
