---
title: Een lijst met beschikbare licenties ophalen
description: Een lijst met licenties verkrijgen die beschikbaar zijn voor gebruikers van de opgegeven klant.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 02a6fccc2cf7f3f4dc929b96ec0f17e0f4a31b06
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874496"
---
# <a name="get-a-list-of-available-licenses"></a><span data-ttu-id="75090-103">Een lijst met beschikbare licenties ophalen</span><span class="sxs-lookup"><span data-stu-id="75090-103">Get a list of available licenses</span></span>

<span data-ttu-id="75090-104">In dit artikel wordt beschreven hoe u een lijst op kunt halen met licenties die beschikbaar zijn voor gebruikers van de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="75090-104">This article describes how to get a list of licenses available to users of the specified customer.</span></span>

<span data-ttu-id="75090-105">De volgende voorbeelden retourneren licenties die beschikbaar zijn via **group1**, de standaardlicentiegroep die licenties vertegenwoordigt die worden beheerd door Azure Active Directory (Azure AD).</span><span class="sxs-lookup"><span data-stu-id="75090-105">The following examples return licenses available from **group1**, the default license group that represents licenses managed by Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="75090-106">Zie Get [a list of available licenses by license group (Een](get-a-list-of-available-licenses-by-license-group.md)lijst met beschikbare licenties per licentiegroep verkrijgen) voor meer informatie over het verkrijgen van beschikbare licenties voor een opgegeven licentiegroep.</span><span class="sxs-lookup"><span data-stu-id="75090-106">To get available licenses for a specified license group, see [Get a list of available licenses by license group](get-a-list-of-available-licenses-by-license-group.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="75090-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="75090-107">Prerequisites</span></span>

- <span data-ttu-id="75090-108">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="75090-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="75090-109">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="75090-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="75090-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="75090-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="75090-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="75090-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="75090-112">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="75090-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="75090-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="75090-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="75090-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="75090-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="75090-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="75090-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="75090-116">C\#</span><span class="sxs-lookup"><span data-stu-id="75090-116">C\#</span></span>

<span data-ttu-id="75090-117">De lijst met licenties ophalen die beschikbaar zijn in de standaardlicentiegroep voor gebruikers van een klant:</span><span class="sxs-lookup"><span data-stu-id="75090-117">To retrieve the list of licenses available from the default license group to users of a customer:</span></span>

1. <span data-ttu-id="75090-118">Gebruik de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="75090-118">Use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="75090-119">Haal de waarde van de eigenschap [**SubscribedSkus op om**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) een interface op te halen voor bewerkingen voor de door de klant geabonneerde SKU-verzameling.</span><span class="sxs-lookup"><span data-stu-id="75090-119">Get the value of the [**SubscribedSkus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) property to retrieve an interface to customer subscribed SKU collection operations.</span></span>

3. <span data-ttu-id="75090-120">Roep de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) om de lijst met licenties op te halen.</span><span class="sxs-lookup"><span data-stu-id="75090-120">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) method to retrieve the list of licenses.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var customerUserSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get();
```

<span data-ttu-id="75090-121">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="75090-121">For an example, see the following:</span></span>

- <span data-ttu-id="75090-122">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="75090-122">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="75090-123">Project: **Partnercentrum-SDK Voorbeelden**</span><span class="sxs-lookup"><span data-stu-id="75090-123">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="75090-124">Klasse: **GetCustomerSubscribedSkus.cs**</span><span class="sxs-lookup"><span data-stu-id="75090-124">Class: **GetCustomerSubscribedSkus.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="75090-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="75090-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="75090-126">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="75090-126">Request syntax</span></span>

| <span data-ttu-id="75090-127">Methode</span><span class="sxs-lookup"><span data-stu-id="75090-127">Method</span></span>  | <span data-ttu-id="75090-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="75090-128">Request URI</span></span>                                                                                    |
|---------|------------------------------------------------------------------------------------------------|
| <span data-ttu-id="75090-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="75090-129">**GET**</span></span> | <span data-ttu-id="75090-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="75090-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="75090-131">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="75090-131">URI parameter</span></span>

<span data-ttu-id="75090-132">Gebruik de volgende padparameter om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="75090-132">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="75090-133">Naam</span><span class="sxs-lookup"><span data-stu-id="75090-133">Name</span></span>        | <span data-ttu-id="75090-134">Type</span><span class="sxs-lookup"><span data-stu-id="75090-134">Type</span></span>   | <span data-ttu-id="75090-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="75090-135">Required</span></span> | <span data-ttu-id="75090-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="75090-136">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="75090-137">customer-id</span><span class="sxs-lookup"><span data-stu-id="75090-137">customer-id</span></span> | <span data-ttu-id="75090-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="75090-138">string</span></span> | <span data-ttu-id="75090-139">Ja</span><span class="sxs-lookup"><span data-stu-id="75090-139">Yes</span></span>      | <span data-ttu-id="75090-140">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="75090-140">A GUID formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="75090-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="75090-141">Request headers</span></span>

<span data-ttu-id="75090-142">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="75090-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="75090-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="75090-143">Request body</span></span>

<span data-ttu-id="75090-144">Geen.</span><span class="sxs-lookup"><span data-stu-id="75090-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="75090-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="75090-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscribedskus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 53308f82-1bf7-44e2-8dda-4517e4688bd4
MS-CorrelationId: 95660db2-7425-4021-babe-a26ddbcb0187
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="75090-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="75090-146">REST response</span></span>

<span data-ttu-id="75090-147">Als dit lukt, bevat de antwoord-body een verzameling [SubscribedSku-resources.](license-resources.md#subscribedsku)</span><span class="sxs-lookup"><span data-stu-id="75090-147">If successful, the response body contains a collection of [SubscribedSku](license-resources.md#subscribedsku) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="75090-148">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="75090-148">Response success and error codes</span></span>

<span data-ttu-id="75090-149">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="75090-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="75090-150">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="75090-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="75090-151">Zie REST-foutcodes voor [Partner Center een volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="75090-151">For a full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="75090-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="75090-152">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 4859
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 95660db2-7425-4021-babe-a26ddbcb0187
MS-RequestId: 53308f82-1bf7-44e2-8dda-4517e4688bd4
MS-CV: 7BQ0jitzXUCLwRM6.0
MS-ServerId: 020021921
Date: Fri, 09 Jun 2017 17:50:46 GMT

 {
    "totalCount": 2,
    "items": [{
            "availableUnits": 4,
            "activeUnits": 5,
            "consumedUnits": 1,
            "suspendedUnits": 0,
            "totalUnits": 5,
            "warningUnits": 0,
            "productSku": {
                "id": "efccb6f7-5641-4e0e-bd10-b4976e1bf68e",
                "name": "Enterprise Mobility + Security E3",
                "skuPartNumber": "EMS",
                "targetType": "User",
                "licenseGroupId": "group1"
            },
            "servicePlans": [{
                    "displayName": "Azure Information Protection Premium P1",
                    "serviceName": "RMS_S_PREMIUM",
                    "id": "6c57d4b6-3b23-47a5-9bc9-69f17b4947b3",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }, {
                    "displayName": "Microsoft Intune A Direct",
                    "serviceName": "INTUNE_A",
                    "id": "c1ec4a95-1f05-45b3-a911-aa3fa01094f5",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }, {
                    "displayName": "Microsoft Azure Active Directory Rights",
                    "serviceName": "RMS_S_ENTERPRISE",
                    "id": "bea4c11e-220a-4e6d-8eb8-8ea15d019f90",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }, {
                    "displayName": "Azure Active Directory Premium P1",
                    "serviceName": "AAD_PREMIUM",
                    "id": "41781fb2-bc02-4b7c-bd55-b576c07bb09d",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }, {
                    "displayName": "Microsoft Azure Multi-Factor Authentication",
                    "serviceName": "MFA_PREMIUM",
                    "id": "8a256a2b-b617-496d-b51b-e76466e88db0",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }
            ],
            "capabilityStatus": "Enabled",
            "attributes": {
                "objectType": "SubscribedSku"
            }
        },  {
            "availableUnits": 0,
            "activeUnits": 1,
            "consumedUnits": 1,
            "suspendedUnits": 0,
            "totalUnits": 1,
            "warningUnits": 0,
            "productSku": {
                "id": "f8a1db68-be16-40ed-86d5-cb42ce701560",
                "name": "Power BI Pro",
                "skuPartNumber": "POWER_BI_PRO",
                "targetType": "User",
                "licenseGroupId": "group1"
            },
            "servicePlans": [{
                    "displayName": "Exchange Foundation",
                    "serviceName": "EXCHANGE_S_FOUNDATION",
                    "id": "113feb6c-3fe4-4440-bddc-54d774bf0318",
                    "capabilityStatus": "Enabled",
                    "targetType": "Tenant"
                }, {
                    "displayName": "Power BI Pro",
                    "serviceName": "BI_AZURE_P2",
                    "id": "70d33638-9c74-4d01-bfd3-562de28bd4ba",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }
            ],
            "capabilityStatus": "Enabled",
            "attributes": {
                "objectType": "SubscribedSku"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
