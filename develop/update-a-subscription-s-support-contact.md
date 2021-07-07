---
title: De ondersteuningscontactpersoon van een abonnement bijwerken
description: Het bijwerken van de ondersteuningscontact van een abonnement naar een van de toegevoegde waarde resellers van de partner.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8c89f91fc9e89384a7be1237c08d7a9a1cfe3164
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530358"
---
# <a name="update-a-subscriptions-support-contact"></a><span data-ttu-id="cf1cf-103">De ondersteuningscontactpersoon van een abonnement bijwerken</span><span class="sxs-lookup"><span data-stu-id="cf1cf-103">Update a subscription's support contact</span></span>

<span data-ttu-id="cf1cf-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="cf1cf-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="cf1cf-105">Het bijwerken van de ondersteuningscontact van een abonnement naar een van de toegevoegde waarde resellers van de partner.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-105">How to update a subscription's support contact to one of the partner's value added resellers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cf1cf-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cf1cf-106">Prerequisites</span></span>

- <span data-ttu-id="cf1cf-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cf1cf-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cf1cf-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="cf1cf-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cf1cf-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="cf1cf-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="cf1cf-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="cf1cf-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="cf1cf-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="cf1cf-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="cf1cf-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="cf1cf-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cf1cf-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="cf1cf-115">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-115">A subscription identifier.</span></span>

- <span data-ttu-id="cf1cf-116">Informatie over de nieuwe contactpersoon voor ondersteuning: tenant-id, Microsoft Partner Network id en naam.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-116">Information about the new support contact: tenant identifier, Microsoft Partner Network identifier, and name.</span></span> <span data-ttu-id="cf1cf-117">De contactpersoon voor ondersteuning moet een van de toegevoegde waarde resellers van de partner zijn.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-117">The support contact must be one of the partner's value added resellers.</span></span>

## <a name="c"></a><span data-ttu-id="cf1cf-118">C\#</span><span class="sxs-lookup"><span data-stu-id="cf1cf-118">C\#</span></span>

<span data-ttu-id="cf1cf-119">Als u de contactpersoon voor ondersteuning van een abonnement wilt bijwerken, instantieert en vult u eerst een [**SupportContact-object**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact) met de nieuwe waarden.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-119">To update a subscription's support contact, first instantiate and populate a [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact) object with the new values.</span></span> <span data-ttu-id="cf1cf-120">Gebruik vervolgens de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-120">Then use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="cf1cf-121">Haal vervolgens een interface op voor abonnementsbewerkingen door de methode [**Subscriptions.ById aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) te roepen met de abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-121">Next, get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the subscription ID.</span></span> <span data-ttu-id="cf1cf-122">Gebruik vervolgens de eigenschap [**SupportContact om een**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) interface te verkrijgen voor de ondersteuning van contactbewerkingen.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-122">Then, use the [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) property to obtain an interface to support contact operations.</span></span> <span data-ttu-id="cf1cf-123">Roep ten slotte de [**methode Update**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.update) of [**UpdateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.updateasync) aan met het ingevulde SupportContact-object om de contactpersoon voor ondersteuning bij te werken.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-123">Finally, call the [**Update**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.update) or [**UpdateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.updateasync) method with the populated SupportContact object to update the support contact.</span></span>

``` csharp
// IAggregatePartner partnerOperations.
// string customerId;
// string subscriptionId;

// Instantiate a SupportContact object and populate it with the new support contact information.
var supportContact = new SupportContact()
{
    Name = "Support contact's name",
    SupportTenantId = "Support contact's tenant ID",
    SupportMpnId = "Support contact's MPN ID"
};

// Update the support contact with a new object that has valid VAR values.
var updatedSupportContact = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionID).SupportContact.Update(supportContact);
```

<span data-ttu-id="cf1cf-124">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="cf1cf-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="cf1cf-125">**Project:** Partnercentrum-SDK Samples **Class**: UpdateSubscriptionSupportContact.cs</span><span class="sxs-lookup"><span data-stu-id="cf1cf-125">**Project**: Partner Center SDK Samples **Class**: UpdateSubscriptionSupportContact.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="cf1cf-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="cf1cf-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cf1cf-127">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="cf1cf-127">Request syntax</span></span>

| <span data-ttu-id="cf1cf-128">Methode</span><span class="sxs-lookup"><span data-stu-id="cf1cf-128">Method</span></span>  | <span data-ttu-id="cf1cf-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="cf1cf-129">Request URI</span></span>                                                                                                                    |
|---------|--------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="cf1cf-130">**PUT**</span><span class="sxs-lookup"><span data-stu-id="cf1cf-130">**PUT**</span></span> | <span data-ttu-id="cf1cf-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/supportcontact HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="cf1cf-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/supportcontact HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="cf1cf-132">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="cf1cf-132">URI parameter</span></span>

<span data-ttu-id="cf1cf-133">Gebruik de volgende padparameters om de klant en het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-133">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="cf1cf-134">Naam</span><span class="sxs-lookup"><span data-stu-id="cf1cf-134">Name</span></span>            | <span data-ttu-id="cf1cf-135">Type</span><span class="sxs-lookup"><span data-stu-id="cf1cf-135">Type</span></span>   | <span data-ttu-id="cf1cf-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="cf1cf-136">Required</span></span> | <span data-ttu-id="cf1cf-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cf1cf-137">Description</span></span>                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="cf1cf-138">customer-id</span><span class="sxs-lookup"><span data-stu-id="cf1cf-138">customer-id</span></span>     | <span data-ttu-id="cf1cf-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="cf1cf-139">string</span></span> | <span data-ttu-id="cf1cf-140">Ja</span><span class="sxs-lookup"><span data-stu-id="cf1cf-140">Yes</span></span>      | <span data-ttu-id="cf1cf-141">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-141">A GUID formatted string that identifies the customer.</span></span>           |
| <span data-ttu-id="cf1cf-142">subscription-id</span><span class="sxs-lookup"><span data-stu-id="cf1cf-142">subscription-id</span></span> | <span data-ttu-id="cf1cf-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="cf1cf-143">string</span></span> | <span data-ttu-id="cf1cf-144">Ja</span><span class="sxs-lookup"><span data-stu-id="cf1cf-144">Yes</span></span>      | <span data-ttu-id="cf1cf-145">Een tekenreeks met GUID-indeling die het proefabonnement identificeert.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-145">A GUID formatted string that identifies the trial subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="cf1cf-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="cf1cf-146">Request headers</span></span>

<span data-ttu-id="cf1cf-147">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="cf1cf-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cf1cf-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="cf1cf-148">Request body</span></span>

<span data-ttu-id="cf1cf-149">U moet een ingevulde [resource SupportContact](subscription-resources.md#supportcontact) opnemen in de aanvraag body.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-149">You must include a populated [SupportContact](subscription-resources.md#supportcontact) resource in the request body.</span></span> <span data-ttu-id="cf1cf-150">De contactpersoon voor ondersteuning moet een bestaande reseller zijn met een relatie met de partner.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-150">The support contact must be an existing reseller with a relationship to the partner.</span></span>

### <a name="request-example"></a><span data-ttu-id="cf1cf-151">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cf1cf-151">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/C8D8FBAB-6A62-44DC-BE50-B7C74E43A296/supportcontact HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b72d732a-eed7-4a60-82d1-1b2e6cba0ed2
MS-CorrelationId: 84eff9e1-6a8c-42aa-8678-c00b0d3fb26f
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 320
Expect: 100-continue

{
    "SupportTenantId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "SupportMpnId": "4391507",
    "Name": "Trey Research",
    "Links": {
        "Self": {
            "Uri": "/customers/0C39D6D5-C70D-4C55-BC02-F620844F3FD1/subscriptions/C8D8FBAB-6A62-44DC-BE50-B7C74E43A296/supportcontact",
            "Method": "Get",
            "Headers": []
        }
    },
    "Attributes": {
        "ObjectType": "SupportContact"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="cf1cf-152">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="cf1cf-152">REST response</span></span>

<span data-ttu-id="cf1cf-153">Als dit lukt, bevat de antwoord-body de resource [SupportContact.](subscription-resources.md#supportcontact)</span><span class="sxs-lookup"><span data-stu-id="cf1cf-153">If successful, the response body contains the [SupportContact](subscription-resources.md#supportcontact) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cf1cf-154">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="cf1cf-154">Response success and error codes</span></span>

<span data-ttu-id="cf1cf-155">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-155">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cf1cf-156">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="cf1cf-156">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="cf1cf-157">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="cf1cf-157">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="cf1cf-158">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="cf1cf-158">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 328
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b0cd9bcc-742e-4c76-9e34-a96d3bdc7673
MS-RequestId: 7591ca22-d4e3-409d-bfa6-09806eaff4f3
MS-CV: W8Tzj6NGckKHcq+E.0
MS-ServerId: 030020344
Date: Wed, 21 Jun 2017 01:01:17 GMT

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
