---
title: Gebruiksgegevens van partnerlicenties ophalen
description: Gebruiksgegevens van partnerlicenties samenvoegen om alle klanten op te nemen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f3d05d61ac4f2c90b0d8a4bfd93fe24e94bd5c1b
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445592"
---
# <a name="get-partner-licenses-usage-information"></a><span data-ttu-id="96644-103">Gebruiksgegevens van partnerlicenties ophalen</span><span class="sxs-lookup"><span data-stu-id="96644-103">Get partner licenses usage information</span></span>

<span data-ttu-id="96644-104">Gebruiksgegevens van partnerlicenties samenvoegen om alle klanten op te nemen.</span><span class="sxs-lookup"><span data-stu-id="96644-104">How to get partner licenses usage information aggregated to include all customers.</span></span>

> [!NOTE]
> <span data-ttu-id="96644-105">Dit scenario wordt vervangen door [Gebruiksgegevens voor licenties verkrijgen.](get-licenses-usage-information.md)</span><span class="sxs-lookup"><span data-stu-id="96644-105">This scenario is superceded by [Get licenses usage information](get-licenses-usage-information.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="96644-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="96644-106">Prerequisites</span></span>

<span data-ttu-id="96644-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="96644-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="96644-108">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="96644-108">This scenario supports authentication with App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="96644-109">C\#</span><span class="sxs-lookup"><span data-stu-id="96644-109">C\#</span></span>

<span data-ttu-id="96644-110">Als u geaggregeerde gegevens over de implementatie van licenties wilt ophalen, moet u eerst een interface ophalen voor bewerkingen voor het verzamelen van analyses op partnerniveau van de [**eigenschap IAggregatePartner.Analytics.**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics)</span><span class="sxs-lookup"><span data-stu-id="96644-110">To retrieve aggregated data on licenses deployment, first get an interface to partner level analytics collection operations from the [**IAggregatePartner.Analytics**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics) property.</span></span> <span data-ttu-id="96644-111">Haal vervolgens een interface op voor de analyseverzameling licenties op partnerniveau uit [**de eigenschap Licenties.**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses)</span><span class="sxs-lookup"><span data-stu-id="96644-111">Then retrieve an interface to the partner level licenses analytics collection from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses) property.</span></span> <span data-ttu-id="96644-112">Roep ten slotte de [**methode Usage.Get aan**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) om de geaggregeerde gegevens over het gebruik van licenties op te halen.</span><span class="sxs-lookup"><span data-stu-id="96644-112">Finally, call the [**Usage.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) method to get the aggregated data on licenses usage.</span></span> <span data-ttu-id="96644-113">Als de methode slaagt, krijgt u een verzameling [**PartnerLicensesUsageInsights-objecten.**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesusageinsights)</span><span class="sxs-lookup"><span data-stu-id="96644-113">If the method succeeds, you'll get a collection of [**PartnerLicensesUsageInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesusageinsights) objects.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var partnerLicensesUsageAnalytics = partnerOperations.Analytics.Licenses.Usage.Get();
```

## <a name="rest-request"></a><span data-ttu-id="96644-114">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="96644-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="96644-115">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="96644-115">Request syntax</span></span>

| <span data-ttu-id="96644-116">Methode</span><span class="sxs-lookup"><span data-stu-id="96644-116">Method</span></span>  | <span data-ttu-id="96644-117">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="96644-117">Request URI</span></span>                                                                      |
|---------|----------------------------------------------------------------------------------|
| <span data-ttu-id="96644-118">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="96644-118">**GET**</span></span> | <span data-ttu-id="96644-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/licenses/usage HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="96644-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/licenses/usage HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="96644-120">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="96644-120">Request headers</span></span>

<span data-ttu-id="96644-121">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="96644-121">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="96644-122">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="96644-122">Request body</span></span>

<span data-ttu-id="96644-123">Geen.</span><span class="sxs-lookup"><span data-stu-id="96644-123">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="96644-124">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="96644-124">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/analytics/licenses/usage HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 6b588e9b-1d02-471a-bce2-79374497c24e
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="96644-125">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="96644-125">REST response</span></span>

<span data-ttu-id="96644-126">Als dit lukt, bevat de antwoord-body een verzameling [PartnerLicensesUsageInsights-resources](analytics-resources.md#partnerlicensesusageinsights) die informatie bieden over de gebruikte licenties.</span><span class="sxs-lookup"><span data-stu-id="96644-126">If successful, the response body contains a collection of [PartnerLicensesUsageInsights](analytics-resources.md#partnerlicensesusageinsights) resources that provide information about the licenses used.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="96644-127">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="96644-127">Response success and error codes</span></span>

<span data-ttu-id="96644-128">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="96644-128">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="96644-129">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="96644-129">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="96644-130">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="96644-130">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="96644-131">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="96644-131">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1156
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
MS-RequestId: 6b588e9b-1d02-471a-bce2-79374497c24e
MS-CV: wk0/vjugzEe0Z9cv.0
MS-ServerId: 101112012
Date: Wed, 15 Mar 2017 01:18:26 GMT

{
    "totalCount": 5,
    "items": [{
            "proratedLicensesUsagePercent": 0.0,
            "workloadName": "Microsoft Dynamics CRM",
            "processedDateTime": "2017-03-10T00:00:00+00:00",
            "serviceName": "crm",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesUsageInsights"
            }
        }, {
            "proratedLicensesUsagePercent": 0.0,
            "workloadName": "SharePoint",
            "processedDateTime": "2017-03-10T00:00:00+00:00",
            "serviceName": "crm",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesUsageInsights"
            }
        }, {
            "proratedLicensesUsagePercent": 0.0,
            "workloadName": "Exchange",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesUsageInsights"
            }
        }, {
            "proratedLicensesUsagePercent": 0.0,
            "workloadName": "SharePoint",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesUsageInsights"
            }
        }, {
            "proratedLicensesUsagePercent": 0.0,
            "workloadName": "Skype For Business",
            "processedDateTime": "2017-03-09T00:00:00+00:00",
            "serviceName": "o365",
            "channel": "reseller",
            "attributes": {
                "objectType": "PartnerLicensesUsageInsights"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
