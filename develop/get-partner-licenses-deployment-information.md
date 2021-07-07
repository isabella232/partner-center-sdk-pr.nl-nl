---
title: Implementatiegegevens van partnerlicenties ophalen
description: Informatie over de implementatie van partnerlicenties verzamelen om alle klanten op te nemen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 2464242fc6dc4e7464511eac5d4197630e22fac0
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445970"
---
# <a name="get-partner-licenses-deployment-information"></a><span data-ttu-id="3f84c-103">Implementatiegegevens van partnerlicenties ophalen</span><span class="sxs-lookup"><span data-stu-id="3f84c-103">Get partner licenses deployment information</span></span>

<span data-ttu-id="3f84c-104">Informatie over de implementatie van partnerlicenties verzamelen om alle klanten op te nemen.</span><span class="sxs-lookup"><span data-stu-id="3f84c-104">How to get partner licenses deployment information aggregated to include all customers.</span></span>

> [!NOTE]
> <span data-ttu-id="3f84c-105">Dit scenario wordt vervangen door Implementatiegegevens voor [licenties verkrijgen.](get-licenses-deployment-information.md)</span><span class="sxs-lookup"><span data-stu-id="3f84c-105">This scenario is superceded by [Get licenses deployment information](get-licenses-deployment-information.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f84c-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3f84c-106">Prerequisites</span></span>

<span data-ttu-id="3f84c-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3f84c-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="3f84c-108">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="3f84c-108">This scenario supports authentication with App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="3f84c-109">C\#</span><span class="sxs-lookup"><span data-stu-id="3f84c-109">C\#</span></span>

<span data-ttu-id="3f84c-110">Als u geaggregeerde gegevens over de implementatie van licenties wilt ophalen, moet u eerst een interface ophalen voor bewerkingen voor het verzamelen van analyses op partnerniveau van de [**eigenschap IAggregatePartner.Analytics.**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics)</span><span class="sxs-lookup"><span data-stu-id="3f84c-110">To retrieve aggregated data on licenses deployment, first get an interface to partner level analytics collection operations from the [**IAggregatePartner.Analytics**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics) property.</span></span> <span data-ttu-id="3f84c-111">Haal vervolgens een interface op voor de analyseverzameling licenties op partnerniveau uit [**de eigenschap Licenties.**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses)</span><span class="sxs-lookup"><span data-stu-id="3f84c-111">Then retrieve an interface to the partner level licenses analytics collection from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses) property.</span></span> <span data-ttu-id="3f84c-112">Roep ten slotte de [**methode Deployment.Get aan**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) om de geaggregeerde gegevens over de implementatie van licenties op te halen.</span><span class="sxs-lookup"><span data-stu-id="3f84c-112">Finally, call the [**Deployment.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) method to get the aggregated data on licenses deployment.</span></span> <span data-ttu-id="3f84c-113">Als de methode slaagt, krijgt u een verzameling [**PartnerLicensesDeploymentInsights-objecten.**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesdeploymentinsights)</span><span class="sxs-lookup"><span data-stu-id="3f84c-113">If the method succeeds, you'll get a collection of [**PartnerLicensesDeploymentInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesdeploymentinsights) objects.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var partnerLicensesDeploymentAnalytics = partnerOperations.Analytics.Licenses.Deployment.Get();
```

## <a name="rest-request"></a><span data-ttu-id="3f84c-114">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="3f84c-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3f84c-115">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="3f84c-115">Request syntax</span></span>

| <span data-ttu-id="3f84c-116">Methode</span><span class="sxs-lookup"><span data-stu-id="3f84c-116">Method</span></span>  | <span data-ttu-id="3f84c-117">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="3f84c-117">Request URI</span></span>                                                                           |
|---------|---------------------------------------------------------------------------------------|
| <span data-ttu-id="3f84c-118">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="3f84c-118">**GET**</span></span> | <span data-ttu-id="3f84c-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/licenses/deployment HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="3f84c-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/licenses/deployment HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="3f84c-120">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="3f84c-120">Request headers</span></span>

<span data-ttu-id="3f84c-121">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="3f84c-121">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3f84c-122">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="3f84c-122">Request body</span></span>

<span data-ttu-id="3f84c-123">Geen.</span><span class="sxs-lookup"><span data-stu-id="3f84c-123">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="3f84c-124">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3f84c-124">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/analytics/licenses/deployment HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 25b6edd5-1f53-456b-b48c-c64f60ec2dda
MS-CorrelationId: 6492b9d6-5629-429b-934c-040b1946e760
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="3f84c-125">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="3f84c-125">REST response</span></span>

<span data-ttu-id="3f84c-126">Als dit lukt, bevat de antwoord-body een verzameling [PartnerLicensesDeploymentInsights-resources](analytics-resources.md#partnerlicensesdeploymentinsights) die informatie bieden over de geïmplementeerde licenties.</span><span class="sxs-lookup"><span data-stu-id="3f84c-126">If successful, the response body contains a collection of [PartnerLicensesDeploymentInsights](analytics-resources.md#partnerlicensesdeploymentinsights) resources that provide information about the licenses deployed.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3f84c-127">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="3f84c-127">Response success and error codes</span></span>

<span data-ttu-id="3f84c-128">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="3f84c-128">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="3f84c-129">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="3f84c-129">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3f84c-130">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="3f84c-130">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="3f84c-131">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="3f84c-131">Response example</span></span>

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
