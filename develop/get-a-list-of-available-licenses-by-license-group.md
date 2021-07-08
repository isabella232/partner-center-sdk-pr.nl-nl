---
title: Een lijst met beschikbare licenties per licentiegroep ophalen
description: Een lijst met licenties op te halen voor de opgegeven licentiegroepen die beschikbaar zijn voor gebruikers van de opgegeven klant.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: de59dfccf723c8f2411d9dadc51beb88688d5b02
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874513"
---
# <a name="get-a-list-of-available-licenses-by-license-group"></a><span data-ttu-id="fefc6-103">Een lijst met beschikbare licenties per licentiegroep ophalen</span><span class="sxs-lookup"><span data-stu-id="fefc6-103">Get a list of available licenses by license group</span></span>

<span data-ttu-id="fefc6-104">Een lijst met licenties op te halen voor de opgegeven licentiegroepen die beschikbaar zijn voor gebruikers van de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="fefc6-104">How to get a list of licenses for the specified license groups available to users of the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fefc6-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fefc6-105">Prerequisites</span></span>

- <span data-ttu-id="fefc6-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fefc6-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fefc6-107">Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="fefc6-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="fefc6-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fefc6-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="fefc6-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="fefc6-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="fefc6-110">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="fefc6-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="fefc6-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="fefc6-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="fefc6-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="fefc6-112">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="fefc6-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fefc6-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="fefc6-114">Een lijst met een of meer licentiegroep-id's.</span><span class="sxs-lookup"><span data-stu-id="fefc6-114">A list of one or more license group identifiers.</span></span>

## <a name="c"></a><span data-ttu-id="fefc6-115">C\#</span><span class="sxs-lookup"><span data-stu-id="fefc6-115">C\#</span></span>

<span data-ttu-id="fefc6-116">Als u een lijst met beschikbare licenties voor de opgegeven licentiegroepen wilt krijgen, begint u met het instantiëren van een lijst van het type [**LicenseGroupId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid)en voegt u vervolgens de licentiegroepen toe aan de lijst. [](/dotnet/api/system.collections.generic.list-1)</span><span class="sxs-lookup"><span data-stu-id="fefc6-116">To get a list of available licenses for the specified license groups, start by instantiating a [List](/dotnet/api/system.collections.generic.list-1) of type [**LicenseGroupId**](/dotnet/api/microsoft.store.partnercenter.models.licenses.licensegroupid), and then add the license groups to the list.</span></span> <span data-ttu-id="fefc6-117">Gebruik vervolgens de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="fefc6-117">Next, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="fefc6-118">Haal vervolgens de waarde van de eigenschap [**SubscribedSkus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) op om een interface op te halen voor bewerkingen van de SKU-verzameling die door de klant zijn geabonneerd.</span><span class="sxs-lookup"><span data-stu-id="fefc6-118">Then, get the value of the [**SubscribedSkus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) property to retrieve an interface to customer subscribed SKU collection operations.</span></span> <span data-ttu-id="fefc6-119">Geef ten slotte de lijst met licentiegroepen door aan de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) om de lijst met geabonneerde SKU's op te halen met details over beschikbare licentie-eenheden.</span><span class="sxs-lookup"><span data-stu-id="fefc6-119">Finally, pass the list of license groups to the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) method to retrieve the list of subscribed SKUs with details on available license units.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

// To get subscribed SKUs available for group1, the license group for Azure Active Directory (AAD).
List<LicenseGroupId> licenseGroupIds = new List<LicenseGroupId>() { LicenseGroupId.Group1};
var customerUserAadSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get(licenseGroupIds);

// To get subscribed SKUs available for group2, the license group for Minecraft product licenses.
List<LicenseGroupId> licenseGroupIds = new List<LicenseGroupId>() { LicenseGroupId.Group2};
var customerUserSfbSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get(licenseGroupIds);

// To get both AAD and Minecraft subscribed SKUs.
List<LicenseGroupId> licenseGroupIds = new List<LicenseGroupId>() { LicenseGroupId.Group1, LicenseGroupId.Group2};
var customerUserBothAadAndSfbSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get(licenseGroupIds);
```

## <a name="rest-request"></a><span data-ttu-id="fefc6-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fefc6-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fefc6-121">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="fefc6-121">Request syntax</span></span>

| <span data-ttu-id="fefc6-122">Methode</span><span class="sxs-lookup"><span data-stu-id="fefc6-122">Method</span></span>  | <span data-ttu-id="fefc6-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fefc6-123">Request URI</span></span>                                                                                                                                  |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fefc6-124">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fefc6-124">**GET**</span></span> | <span data-ttu-id="fefc6-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group1 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fefc6-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group1 HTTP/1.1</span></span>                        |
| <span data-ttu-id="fefc6-126">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fefc6-126">**GET**</span></span> | <span data-ttu-id="fefc6-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group2 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fefc6-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group2 HTTP/1.1</span></span>                        |
| <span data-ttu-id="fefc6-128">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fefc6-128">**GET**</span></span> | <span data-ttu-id="fefc6-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fefc6-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="fefc6-130">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="fefc6-130">URI parameter</span></span>

<span data-ttu-id="fefc6-131">Gebruik het volgende pad en de queryparameters om de klant en de licentiegroepen te identificeren.</span><span class="sxs-lookup"><span data-stu-id="fefc6-131">Use the following path and query parameters to identify the customer and the license groups.</span></span>

| <span data-ttu-id="fefc6-132">Naam</span><span class="sxs-lookup"><span data-stu-id="fefc6-132">Name</span></span>            | <span data-ttu-id="fefc6-133">Type</span><span class="sxs-lookup"><span data-stu-id="fefc6-133">Type</span></span>   | <span data-ttu-id="fefc6-134">Vereist</span><span class="sxs-lookup"><span data-stu-id="fefc6-134">Required</span></span> | <span data-ttu-id="fefc6-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fefc6-135">Description</span></span>                                                                                                                                                                                                                                                           |
|-----------------|--------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fefc6-136">customer-id</span><span class="sxs-lookup"><span data-stu-id="fefc6-136">customer-id</span></span>     | <span data-ttu-id="fefc6-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fefc6-137">string</span></span> | <span data-ttu-id="fefc6-138">Ja</span><span class="sxs-lookup"><span data-stu-id="fefc6-138">Yes</span></span>      | <span data-ttu-id="fefc6-139">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="fefc6-139">A GUID formatted string that identifies the customer.</span></span>                                                                                                                                                                                                                 |
| <span data-ttu-id="fefc6-140">licenseGroupIds</span><span class="sxs-lookup"><span data-stu-id="fefc6-140">licenseGroupIds</span></span> | <span data-ttu-id="fefc6-141">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fefc6-141">string</span></span> | <span data-ttu-id="fefc6-142">No</span><span class="sxs-lookup"><span data-stu-id="fefc6-142">No</span></span>       | <span data-ttu-id="fefc6-143">Een enum-waarde die de licentiegroep van de toegewezen licenties aangeeft.</span><span class="sxs-lookup"><span data-stu-id="fefc6-143">An enum value that indicates the license group of the assigned licenses.</span></span> <span data-ttu-id="fefc6-144">Geldige waarden: Group1, Group2 Group1: deze groep heeft alle producten waarvan de licentie kan worden beheerd in de Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="fefc6-144">Valid values: Group1, Group2 Group1 - This group has all products whose license can be managed in the Azure Active Directory (AAD).</span></span> <span data-ttu-id="fefc6-145">Group2: deze groep heeft alleen Minecraft productlicenties.</span><span class="sxs-lookup"><span data-stu-id="fefc6-145">Group2 - This group has only Minecraft product licenses.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="fefc6-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="fefc6-146">Request headers</span></span>

<span data-ttu-id="fefc6-147">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="fefc6-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fefc6-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="fefc6-148">Request body</span></span>

<span data-ttu-id="fefc6-149">Geen.</span><span class="sxs-lookup"><span data-stu-id="fefc6-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="fefc6-150">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fefc6-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscribedskus?licenseGroupIds=Group1&licenseGroupIds=Group2 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a1d077e4-28b1-4578-b873-6d1a82fa1644
MS-CorrelationId: c8cb5a60-ae08-4afc-92f0-efc42adfa186
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="fefc6-151">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fefc6-151">REST response</span></span>

<span data-ttu-id="fefc6-152">Als dit lukt, bevat de antwoord-body een verzameling [SubscribedSku-resources.](license-resources.md#subscribedsku)</span><span class="sxs-lookup"><span data-stu-id="fefc6-152">If successful, the response body contains a collection of [SubscribedSku](license-resources.md#subscribedsku) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fefc6-153">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="fefc6-153">Response success and error codes</span></span>

<span data-ttu-id="fefc6-154">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="fefc6-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fefc6-155">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fefc6-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fefc6-156">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="fefc6-156">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fefc6-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fefc6-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 4328
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c8cb5a60-ae08-4afc-92f0-efc42adfa186
MS-RequestId: a1d077e4-28b1-4578-b873-6d1a82fa1644
MS-CV: S6Pd5XQAx0Ss/zQi.0
MS-ServerId: 030011719
Date: Sat, 10 Jun 2017 00:19:44 GMT

{
    "totalCount": 04,
    "items": [{
            "availableUnits": 15,
            "activeUnits": 15,
            "consumedUnits": 0,
            "suspendedUnits": 0,
            "totalUnits": 15,
            "warningUnits": 0,
            "productSku": {
                "id": "078d2b04-f1bd-4111-bbd4-b4b1b354cef4",
                "name": "Azure Active Directory Premium P1",
                "skuPartNumber": "AAD_PREMIUM",
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
        }, {
            "availableUnits": 1,
            "activeUnits": 1,
            "consumedUnits": 0,
            "suspendedUnits": 0,
            "totalUnits": 1,
            "warningUnits": 0,
            "productSku": {
                "id": "54b84594-9c77-4499-8d65-5e0d5f410e78",
                "name": "Dynamics AX Task",
                "skuPartNumber": "AX_TASK_USER",
                "targetType": "User",
                "licenseGroupId": "group1"
            },
            "servicePlans": [

            ],
            "capabilityStatus": "Enabled",
            "attributes": {
                "objectType": "SubscribedSku"
            }
        }, {
            "availableUnits": 23,
            "activeUnits": 72,
            "consumedUnits": 49,
            "suspendedUnits": 0,
            "totalUnits": 72,
            "warningUnits": 0,
            "productSku": {
                "id": "984df360-9a74-4647-8cf8-696749f6247a",
                "name": "Minecraft Education Edition Faculty",
                "skuPartNumber": "CFQ7TTC0K5DR/0002",
                "targetType": "User",
                "licenseGroupId": "group2"
            },
            "servicePlans": [

            ],
            "capabilityStatus": "Enabled",
            "attributes": {
                "objectType": "SubscribedSku"
            }
        }, {
            "availableUnits": 71,
            "activeUnits": 112,
            "consumedUnits": 41,
            "suspendedUnits": 0,
            "totalUnits": 112,
            "warningUnits": 0,
            "productSku": {
                "id": "1e7e1070-8ccb-4aca-b470-d7cb538cb07e",
                "name": "Windows 10 Enterprise E5",
                "skuPartNumber": "WIN_ENT_E5",
                "targetType": "User",
                "licenseGroupId": "group1"
            },
            "servicePlans": [{
                    "displayName": "Windows Defender Advanced Threat Protection",
                    "serviceName": "WINDEFATP",
                    "id": "871d91ec-ec1a-452b-a83f-bd76c7d770ef",
                    "capabilityStatus": "Enabled",
                    "targetType": "User"
                }, {
                    "displayName": "Windows 10 Enterprise E3",
                    "serviceName": "WIN10_PRO_ENT_SUB",
                    "id": "21b439ba-a0ca-424f-a6cc-52f954a5b111",
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

### <a name="response-example-no-matching-skus-found"></a><span data-ttu-id="fefc6-158">Voorbeeld van antwoord (geen overeenkomende SKU's gevonden)</span><span class="sxs-lookup"><span data-stu-id="fefc6-158">Response example (no matching SKUs found)</span></span>

<span data-ttu-id="fefc6-159">Als er geen overeenkomende geabonneerde SKU's kunnen worden gevonden voor de opgegeven licentiegroepen, bevat het antwoord een lege verzameling met een totalCount-element waarvan de waarde 0 is.</span><span class="sxs-lookup"><span data-stu-id="fefc6-159">If no matching subscribed SKUs can be found for the specified license groups, the response contains an empty collection with a totalCount element whose value is 0.</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 71
Content-Type: application/json; charset=utf-8
MS-CorrelationId: c8cb5a60-ae08-4afc-92f0-efc42adfa186
MS-RequestId: a1d077e4-28b1-4578-b873-6d1a82fa1644
MS-CV: q05xrhUeDUKvhrFt.0
MS-ServerId: 030020525
Date: Fri, 09 Jun 2017 22:50:11 GMT

{
    "totalCount": 0,
    "items": [],
    "attributes": {
        "objectType": "Collection"
    }
}
```
