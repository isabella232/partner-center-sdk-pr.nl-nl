---
title: De ondersteuningscontactpersoon van een abonnement ophalen
description: De contactpersoon voor ondersteuning van een abonnement krijgen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b6c98e5ed96f2ca4787e93504c9e094bd46ae783
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760756"
---
# <a name="get-a-subscriptions-support-contact"></a><span data-ttu-id="fede8-103">De ondersteuningscontactpersoon van een abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="fede8-103">Get a subscription's support contact</span></span>

<span data-ttu-id="fede8-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="fede8-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="fede8-105">De contactpersoon voor ondersteuning van een abonnement krijgen.</span><span class="sxs-lookup"><span data-stu-id="fede8-105">How to get a subscription's support contact.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fede8-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fede8-106">Prerequisites</span></span>

- <span data-ttu-id="fede8-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fede8-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fede8-108">Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="fede8-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="fede8-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fede8-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="fede8-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="fede8-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="fede8-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="fede8-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="fede8-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="fede8-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="fede8-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="fede8-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="fede8-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fede8-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="fede8-115">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="fede8-115">A subscription identifier.</span></span>

## <a name="c"></a><span data-ttu-id="fede8-116">C\#</span><span class="sxs-lookup"><span data-stu-id="fede8-116">C\#</span></span>

<span data-ttu-id="fede8-117">Als u de contactpersoon voor ondersteuning van een abonnement wilt krijgen, gebruikt u eerst de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="fede8-117">To get a subscription's support contact, start by using the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="fede8-118">Haal vervolgens een interface op voor abonnementsbewerkingen door de methode [**Subscriptions.ById aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) te roepen met de abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="fede8-118">Then, get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the subscription ID.</span></span> <span data-ttu-id="fede8-119">Gebruik vervolgens de eigenschap [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) om een interface te verkrijgen voor de ondersteuning van contactbewerkingen en roep vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) aan om het [**object SupportContact op te**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact) halen.</span><span class="sxs-lookup"><span data-stu-id="fede8-119">Next, use the [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) property to obtain an interface to support contact operations, and then call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) method to retrieve the [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact) object.</span></span>

``` csharp
// IAggregatePartner partnerOperations.
// string customerId;
// string subscriptionId;

// Retrieve subscription's support contact.
var supportContact = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId).SupportContact.Get();
```

<span data-ttu-id="fede8-120">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="fede8-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="fede8-121">**Project:** Partnercentrum-SDK **Klasse**: GetSubscriptionSupportContact.cs</span><span class="sxs-lookup"><span data-stu-id="fede8-121">**Project**: Partner Center SDK Samples **Class**: GetSubscriptionSupportContact.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="fede8-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fede8-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fede8-123">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="fede8-123">Request syntax</span></span>

| <span data-ttu-id="fede8-124">Methode</span><span class="sxs-lookup"><span data-stu-id="fede8-124">Method</span></span>  | <span data-ttu-id="fede8-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fede8-125">Request URI</span></span>                                                                                                                    |
|---------|--------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fede8-126">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fede8-126">**GET**</span></span> | <span data-ttu-id="fede8-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/supportcontact HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fede8-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/supportcontact HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="fede8-128">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="fede8-128">URI parameter</span></span>

<span data-ttu-id="fede8-129">Gebruik de volgende padparameters om de klant en het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="fede8-129">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="fede8-130">Naam</span><span class="sxs-lookup"><span data-stu-id="fede8-130">Name</span></span>            | <span data-ttu-id="fede8-131">Type</span><span class="sxs-lookup"><span data-stu-id="fede8-131">Type</span></span>   | <span data-ttu-id="fede8-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="fede8-132">Required</span></span> | <span data-ttu-id="fede8-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fede8-133">Description</span></span>                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="fede8-134">customer-id</span><span class="sxs-lookup"><span data-stu-id="fede8-134">customer-id</span></span>     | <span data-ttu-id="fede8-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fede8-135">string</span></span> | <span data-ttu-id="fede8-136">Ja</span><span class="sxs-lookup"><span data-stu-id="fede8-136">Yes</span></span>      | <span data-ttu-id="fede8-137">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="fede8-137">A GUID formatted string that identifies the customer.</span></span>           |
| <span data-ttu-id="fede8-138">subscription-id</span><span class="sxs-lookup"><span data-stu-id="fede8-138">subscription-id</span></span> | <span data-ttu-id="fede8-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fede8-139">string</span></span> | <span data-ttu-id="fede8-140">Ja</span><span class="sxs-lookup"><span data-stu-id="fede8-140">Yes</span></span>      | <span data-ttu-id="fede8-141">Een tekenreeks met GUID-indeling die het proefabonnement identificeert.</span><span class="sxs-lookup"><span data-stu-id="fede8-141">A GUID formatted string that identifies the trial subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="fede8-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="fede8-142">Request headers</span></span>

<span data-ttu-id="fede8-143">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="fede8-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fede8-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="fede8-144">Request body</span></span>

<span data-ttu-id="fede8-145">Geen.</span><span class="sxs-lookup"><span data-stu-id="fede8-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="fede8-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fede8-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/C8D8FBAB-6A62-44DC-BE50-B7C74E43A296/supportcontact HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: d052776c-e8fd-4803-b6a3-1659055ac3c4
MS-CorrelationId: a6c552a8-1922-4d0c-bb94-335a33334d14
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="fede8-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fede8-147">REST response</span></span>

<span data-ttu-id="fede8-148">Als dit lukt, bevat de antwoord-body de resource [SupportContact.](subscription-resources.md#supportcontact)</span><span class="sxs-lookup"><span data-stu-id="fede8-148">If successful, the response body contains the [SupportContact](subscription-resources.md#supportcontact) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fede8-149">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="fede8-149">Response success and error codes</span></span>

<span data-ttu-id="fede8-150">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="fede8-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fede8-151">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fede8-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fede8-152">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="fede8-152">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fede8-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fede8-153">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 328
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a6c552a8-1922-4d0c-bb94-335a33334d14
MS-RequestId: d052776c-e8fd-4803-b6a3-1659055ac3c4
MS-CV: bLbUhqy0+ESOX1v4.0
MS-ServerId: 201022015
Date: Tue, 20 Jun 2017 19:30:19 GMT

{
    "supportTenantId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "supportMpnId": "4391507",
    "name": "Trey Research",
    "links": {
        "self": {
            "uri": "/customers/0C39D6D5-C70D-4C55-BC02-F620844F3FD1/subscriptions/C8D8FBAB-6A62-44DC-BE50-B7C74E43A296/supportcontact",
            "method": "Get",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "SupportContact"
    }
}
```
