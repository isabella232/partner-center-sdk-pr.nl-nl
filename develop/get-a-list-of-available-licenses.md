---
title: Een lijst met beschikbare licenties ophalen
description: Een lijst met beschik bare licenties voor gebruikers van de opgegeven klant weer geven.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: f675e5b96b2f2040d662c0dc7f1e06625f267689
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767443"
---
# <a name="get-a-list-of-available-licenses"></a><span data-ttu-id="bf68f-103">Een lijst met beschikbare licenties ophalen</span><span class="sxs-lookup"><span data-stu-id="bf68f-103">Get a list of available licenses</span></span>

<span data-ttu-id="bf68f-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="bf68f-104">**Applies to:**</span></span>

- <span data-ttu-id="bf68f-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="bf68f-105">Partner Center</span></span>

<span data-ttu-id="bf68f-106">In dit artikel wordt beschreven hoe u een lijst met licenties kunt verkrijgen die beschikbaar zijn voor gebruikers van de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="bf68f-106">This article describes how to get a list of licenses available to users of the specified customer.</span></span>

<span data-ttu-id="bf68f-107">De volgende voor beelden geven licenties weer die beschikbaar zijn via **Group1**, de standaard licentie groep die de licenties vertegenwoordigt die worden beheerd door Azure Active Directory (Azure AD).</span><span class="sxs-lookup"><span data-stu-id="bf68f-107">The following examples return licenses available from **group1**, the default license group that represents licenses managed by Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="bf68f-108">Zie [een lijst met beschik bare licenties per licentie groep ophalen](get-a-list-of-available-licenses-by-license-group.md)om beschik bare licenties voor een opgegeven licentie groep te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="bf68f-108">To get available licenses for a specified license group, see [Get a list of available licenses by license group](get-a-list-of-available-licenses-by-license-group.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bf68f-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="bf68f-109">Prerequisites</span></span>

- <span data-ttu-id="bf68f-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bf68f-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="bf68f-111">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf68f-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="bf68f-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="bf68f-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="bf68f-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="bf68f-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="bf68f-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="bf68f-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="bf68f-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="bf68f-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="bf68f-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="bf68f-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="bf68f-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="bf68f-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="bf68f-118">C\#</span><span class="sxs-lookup"><span data-stu-id="bf68f-118">C\#</span></span>

<span data-ttu-id="bf68f-119">De lijst met beschik bare licenties van de standaard licentie groep ophalen voor gebruikers van een klant:</span><span class="sxs-lookup"><span data-stu-id="bf68f-119">To retrieve the list of licenses available from the default license group to users of a customer:</span></span>

1. <span data-ttu-id="bf68f-120">Gebruik de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="bf68f-120">Use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="bf68f-121">Haal de waarde van de eigenschap [**SubscribedSkus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) op om een interface op te halen voor de door de klant geabonneerde SKU verzamelings bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="bf68f-121">Get the value of the [**SubscribedSkus**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscribedskus) property to retrieve an interface to customer subscribed SKU collection operations.</span></span>

3. <span data-ttu-id="bf68f-122">Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) aan om de lijst met licenties op te halen.</span><span class="sxs-lookup"><span data-stu-id="bf68f-122">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscribedskus.icustomersubscribedskucollection.getasync) method to retrieve the list of licenses.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var customerUserSubscribedSkus = partnerOperations.Customers.ById(selectedCustomerId).SubscribedSkus.Get();
```

<span data-ttu-id="bf68f-123">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="bf68f-123">For an example, see the following:</span></span>

- <span data-ttu-id="bf68f-124">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="bf68f-124">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="bf68f-125">Project: **Partner Center SDK** -voor beelden</span><span class="sxs-lookup"><span data-stu-id="bf68f-125">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="bf68f-126">Klasse: **GetCustomerSubscribedSkus.cs**</span><span class="sxs-lookup"><span data-stu-id="bf68f-126">Class: **GetCustomerSubscribedSkus.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="bf68f-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="bf68f-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="bf68f-128">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="bf68f-128">Request syntax</span></span>

| <span data-ttu-id="bf68f-129">Methode</span><span class="sxs-lookup"><span data-stu-id="bf68f-129">Method</span></span>  | <span data-ttu-id="bf68f-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="bf68f-130">Request URI</span></span>                                                                                    |
|---------|------------------------------------------------------------------------------------------------|
| <span data-ttu-id="bf68f-131">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="bf68f-131">**GET**</span></span> | <span data-ttu-id="bf68f-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/subscribedskus http/1.1</span><span class="sxs-lookup"><span data-stu-id="bf68f-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscribedskus HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="bf68f-133">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="bf68f-133">URI parameter</span></span>

<span data-ttu-id="bf68f-134">Gebruik de volgende para meter voor het identificeren van de klant.</span><span class="sxs-lookup"><span data-stu-id="bf68f-134">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="bf68f-135">Naam</span><span class="sxs-lookup"><span data-stu-id="bf68f-135">Name</span></span>        | <span data-ttu-id="bf68f-136">Type</span><span class="sxs-lookup"><span data-stu-id="bf68f-136">Type</span></span>   | <span data-ttu-id="bf68f-137">Vereist</span><span class="sxs-lookup"><span data-stu-id="bf68f-137">Required</span></span> | <span data-ttu-id="bf68f-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bf68f-138">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="bf68f-139">klant-id</span><span class="sxs-lookup"><span data-stu-id="bf68f-139">customer-id</span></span> | <span data-ttu-id="bf68f-140">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="bf68f-140">string</span></span> | <span data-ttu-id="bf68f-141">Yes</span><span class="sxs-lookup"><span data-stu-id="bf68f-141">Yes</span></span>      | <span data-ttu-id="bf68f-142">Een teken reeks met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="bf68f-142">A GUID formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="bf68f-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="bf68f-143">Request headers</span></span>

<span data-ttu-id="bf68f-144">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="bf68f-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="bf68f-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="bf68f-145">Request body</span></span>

<span data-ttu-id="bf68f-146">Geen.</span><span class="sxs-lookup"><span data-stu-id="bf68f-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="bf68f-147">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="bf68f-147">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscribedskus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 53308f82-1bf7-44e2-8dda-4517e4688bd4
MS-CorrelationId: 95660db2-7425-4021-babe-a26ddbcb0187
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="bf68f-148">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="bf68f-148">REST response</span></span>

<span data-ttu-id="bf68f-149">Als dit lukt, bevat de antwoord tekst een verzameling [SubscribedSku](license-resources.md#subscribedsku) -resources.</span><span class="sxs-lookup"><span data-stu-id="bf68f-149">If successful, the response body contains a collection of [SubscribedSku](license-resources.md#subscribedsku) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="bf68f-150">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="bf68f-150">Response success and error codes</span></span>

<span data-ttu-id="bf68f-151">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="bf68f-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="bf68f-152">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="bf68f-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="bf68f-153">Zie voor een volledige lijst de [rest-fout codes van het partner centrum](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="bf68f-153">For a full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="bf68f-154">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="bf68f-154">Response example</span></span>

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
