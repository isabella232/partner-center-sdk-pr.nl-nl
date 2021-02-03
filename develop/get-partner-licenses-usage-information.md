---
title: Gebruiksgegevens van partnerlicenties ophalen
description: Het verkrijgen van gebruiks gegevens van partner licenties voor het toevoegen van alle klanten.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 93d003fb269a3421b8efd8cebe8f396f97599a10
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767562"
---
# <a name="get-partner-licenses-usage-information"></a><span data-ttu-id="644a7-103">Gebruiksgegevens van partnerlicenties ophalen</span><span class="sxs-lookup"><span data-stu-id="644a7-103">Get partner licenses usage information</span></span>

<span data-ttu-id="644a7-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="644a7-104">**Applies To**</span></span>

- <span data-ttu-id="644a7-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="644a7-105">Partner Center</span></span>

<span data-ttu-id="644a7-106">Het verkrijgen van gebruiks gegevens van partner licenties voor het toevoegen van alle klanten.</span><span class="sxs-lookup"><span data-stu-id="644a7-106">How to get partner licenses usage information aggregated to include all customers.</span></span>

> [!NOTE]
> <span data-ttu-id="644a7-107">Dit scenario wordt vervangen door [gebruiks gegevens over licenties te verkrijgen](get-licenses-usage-information.md).</span><span class="sxs-lookup"><span data-stu-id="644a7-107">This scenario is superceded by [Get licenses usage information](get-licenses-usage-information.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="644a7-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="644a7-108">Prerequisites</span></span>

<span data-ttu-id="644a7-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="644a7-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="644a7-110">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="644a7-110">This scenario supports authentication with App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="644a7-111">C\#</span><span class="sxs-lookup"><span data-stu-id="644a7-111">C\#</span></span>

<span data-ttu-id="644a7-112">Als u geaggregeerde gegevens voor de implementatie van licenties wilt ophalen, moet u eerst een interface op het niveau van de verzameling van de [**IAggregatePartner. Analytics**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics) -eigenschappen ophalen.</span><span class="sxs-lookup"><span data-stu-id="644a7-112">To retrieve aggregated data on licenses deployment, first get an interface to partner level analytics collection operations from the [**IAggregatePartner.Analytics**](/dotnet/api/microsoft.store.partnercenter.ipartner.analytics) property.</span></span> <span data-ttu-id="644a7-113">Haal vervolgens een interface op bij de verzameling van de licenties voor het partner niveau-analyse van de eigenschap [**licenties**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses) .</span><span class="sxs-lookup"><span data-stu-id="644a7-113">Then retrieve an interface to the partner level licenses analytics collection from the [**Licenses**](/dotnet/api/microsoft.store.partnercenter.analytics.ipartneranalyticscollection.licenses) property.</span></span> <span data-ttu-id="644a7-114">Roep tot slot de methode [**usage. Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) aan om de geaggregeerde gegevens over het gebruik van licenties op te halen.</span><span class="sxs-lookup"><span data-stu-id="644a7-114">Finally, call the [**Usage.Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) method to get the aggregated data on licenses usage.</span></span> <span data-ttu-id="644a7-115">Als de methode slaagt, krijgt u een verzameling [**PartnerLicensesUsageInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesusageinsights) -objecten.</span><span class="sxs-lookup"><span data-stu-id="644a7-115">If the method succeeds you'll get a collection of [**PartnerLicensesUsageInsights**](/dotnet/api/microsoft.store.partnercenter.models.analytics.partnerlicensesusageinsights) objects.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var partnerLicensesUsageAnalytics = partnerOperations.Analytics.Licenses.Usage.Get();
```

## <a name="rest-request"></a><span data-ttu-id="644a7-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="644a7-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="644a7-117">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="644a7-117">Request syntax</span></span>

| <span data-ttu-id="644a7-118">Methode</span><span class="sxs-lookup"><span data-stu-id="644a7-118">Method</span></span>  | <span data-ttu-id="644a7-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="644a7-119">Request URI</span></span>                                                                      |
|---------|----------------------------------------------------------------------------------|
| <span data-ttu-id="644a7-120">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="644a7-120">**GET**</span></span> | <span data-ttu-id="644a7-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/Analytics/licenses/Usage http/1.1</span><span class="sxs-lookup"><span data-stu-id="644a7-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/licenses/usage HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="644a7-122">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="644a7-122">Request headers</span></span>

<span data-ttu-id="644a7-123">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="644a7-123">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="644a7-124">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="644a7-124">Request body</span></span>

<span data-ttu-id="644a7-125">Geen.</span><span class="sxs-lookup"><span data-stu-id="644a7-125">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="644a7-126">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="644a7-126">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/analytics/licenses/usage HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 6b588e9b-1d02-471a-bce2-79374497c24e
MS-CorrelationId: ae3b8c36-348b-46bc-9a60-398f973153ff
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="644a7-127">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="644a7-127">REST response</span></span>

<span data-ttu-id="644a7-128">Als dit lukt, bevat de antwoord tekst een verzameling [PartnerLicensesUsageInsights](analytics-resources.md#partnerlicensesusageinsights) -resources die informatie geven over de gebruikte licenties.</span><span class="sxs-lookup"><span data-stu-id="644a7-128">If successful, the response body contains a collection of [PartnerLicensesUsageInsights](analytics-resources.md#partnerlicensesusageinsights) resources that provide information about the licenses used.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="644a7-129">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="644a7-129">Response success and error codes</span></span>

<span data-ttu-id="644a7-130">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="644a7-130">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="644a7-131">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="644a7-131">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="644a7-132">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="644a7-132">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="644a7-133">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="644a7-133">Response example</span></span>

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
