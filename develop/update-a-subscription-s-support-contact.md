---
title: De ondersteuningscontactpersoon van een abonnement bijwerken
description: Het bijwerken van de ondersteunings contact persoon van een abonnement op een van de toegevoegde waarden van de partner.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c8c6b658cfe6e14c75b0c06b177920ce3eb1b4ed
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767457"
---
# <a name="update-a-subscriptions-support-contact"></a><span data-ttu-id="9f399-103">De ondersteuningscontactpersoon van een abonnement bijwerken</span><span class="sxs-lookup"><span data-stu-id="9f399-103">Update a subscription's support contact</span></span>

<span data-ttu-id="9f399-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="9f399-104">**Applies To**</span></span>

- <span data-ttu-id="9f399-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="9f399-105">Partner Center</span></span>
- <span data-ttu-id="9f399-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="9f399-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="9f399-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="9f399-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="9f399-108">Het bijwerken van de ondersteunings contact persoon van een abonnement op een van de toegevoegde waarden van de partner.</span><span class="sxs-lookup"><span data-stu-id="9f399-108">How to update a subscription's support contact to one of the partner's value added resellers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9f399-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9f399-109">Prerequisites</span></span>

- <span data-ttu-id="9f399-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9f399-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9f399-111">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="9f399-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="9f399-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9f399-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="9f399-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="9f399-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="9f399-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="9f399-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="9f399-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="9f399-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="9f399-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="9f399-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="9f399-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9f399-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="9f399-118">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="9f399-118">A subscription identifier.</span></span>

- <span data-ttu-id="9f399-119">Informatie over de nieuwe ondersteunings contactpersoon: Tenant-id, Microsoft Partner Network-ID en naam.</span><span class="sxs-lookup"><span data-stu-id="9f399-119">Information about the new support contact: tenant identifier, Microsoft Partner Network identifier, and name.</span></span> <span data-ttu-id="9f399-120">De contact persoon voor ondersteuning moet een van de toegevoegde waarde van de partner zijn.</span><span class="sxs-lookup"><span data-stu-id="9f399-120">The support contact must be one of the partner's value added resellers.</span></span>

## <a name="c"></a><span data-ttu-id="9f399-121">C\#</span><span class="sxs-lookup"><span data-stu-id="9f399-121">C\#</span></span>

<span data-ttu-id="9f399-122">Als u de ondersteunings contactpersoon van een abonnement wilt bijwerken, moet u eerst een [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact) -object instantiëren en vullen met de nieuwe waarden.</span><span class="sxs-lookup"><span data-stu-id="9f399-122">To update a subscription's support contact, first instantiate and populate a [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.supportcontact) object with the new values.</span></span> <span data-ttu-id="9f399-123">Gebruik vervolgens de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="9f399-123">Then use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="9f399-124">Vervolgens krijgt u een interface voor het uitvoeren van een abonnement door de methode [**abonnementen. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) aan te roepen met de abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="9f399-124">Next, get an interface to subscription operations by calling the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method with the subscription ID.</span></span> <span data-ttu-id="9f399-125">Gebruik vervolgens de eigenschap [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) om een interface te verkrijgen voor de ondersteuning van contact bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="9f399-125">Then, use the [**SupportContact**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.supportcontact) property to obtain an interface to support contact operations.</span></span> <span data-ttu-id="9f399-126">Roep tot slot de [**Update**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.update) -of [**UpdateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.updateasync) -methode aan met het gevulde SupportContact-object om de ondersteunings contactpersoon bij te werken.</span><span class="sxs-lookup"><span data-stu-id="9f399-126">Finally, call the [**Update**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.update) or [**UpdateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionsupportcontact.updateasync) method with the populated SupportContact object to update the support contact.</span></span>

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

<span data-ttu-id="9f399-127">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="9f399-127">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="9f399-128">**Project**: Partner Center SDK-voor beelden **klasse**: UpdateSubscriptionSupportContact.cs</span><span class="sxs-lookup"><span data-stu-id="9f399-128">**Project**: Partner Center SDK Samples **Class**: UpdateSubscriptionSupportContact.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="9f399-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="9f399-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9f399-130">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9f399-130">Request syntax</span></span>

| <span data-ttu-id="9f399-131">Methode</span><span class="sxs-lookup"><span data-stu-id="9f399-131">Method</span></span>  | <span data-ttu-id="9f399-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="9f399-132">Request URI</span></span>                                                                                                                    |
|---------|--------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9f399-133">**PUT**</span><span class="sxs-lookup"><span data-stu-id="9f399-133">**PUT**</span></span> | <span data-ttu-id="9f399-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Subscriptions/{Subscription-id}/supportcontact http/1.1</span><span class="sxs-lookup"><span data-stu-id="9f399-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/supportcontact HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="9f399-135">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="9f399-135">URI parameter</span></span>

<span data-ttu-id="9f399-136">Gebruik de volgende Path-para meters om de klant en het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="9f399-136">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="9f399-137">Naam</span><span class="sxs-lookup"><span data-stu-id="9f399-137">Name</span></span>            | <span data-ttu-id="9f399-138">Type</span><span class="sxs-lookup"><span data-stu-id="9f399-138">Type</span></span>   | <span data-ttu-id="9f399-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="9f399-139">Required</span></span> | <span data-ttu-id="9f399-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9f399-140">Description</span></span>                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="9f399-141">klant-id</span><span class="sxs-lookup"><span data-stu-id="9f399-141">customer-id</span></span>     | <span data-ttu-id="9f399-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9f399-142">string</span></span> | <span data-ttu-id="9f399-143">Yes</span><span class="sxs-lookup"><span data-stu-id="9f399-143">Yes</span></span>      | <span data-ttu-id="9f399-144">Een teken reeks met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="9f399-144">A GUID formatted string that identifies the customer.</span></span>           |
| <span data-ttu-id="9f399-145">abonnement-id</span><span class="sxs-lookup"><span data-stu-id="9f399-145">subscription-id</span></span> | <span data-ttu-id="9f399-146">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9f399-146">string</span></span> | <span data-ttu-id="9f399-147">Yes</span><span class="sxs-lookup"><span data-stu-id="9f399-147">Yes</span></span>      | <span data-ttu-id="9f399-148">Een teken reeks met een GUID-indeling waarmee het proef abonnement wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="9f399-148">A GUID formatted string that identifies the trial subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9f399-149">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="9f399-149">Request headers</span></span>

<span data-ttu-id="9f399-150">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="9f399-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9f399-151">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="9f399-151">Request body</span></span>

<span data-ttu-id="9f399-152">U moet een gevulde [SupportContact](subscription-resources.md#supportcontact) -resource in de hoofd tekst van de aanvraag toevoegen.</span><span class="sxs-lookup"><span data-stu-id="9f399-152">You must include a populated [SupportContact](subscription-resources.md#supportcontact) resource in the request body.</span></span> <span data-ttu-id="9f399-153">De contact persoon voor ondersteuning moet een bestaande wederverkoper zijn met een relatie met de partner.</span><span class="sxs-lookup"><span data-stu-id="9f399-153">The support contact must be an existing reseller with a relationship to the partner.</span></span>

### <a name="request-example"></a><span data-ttu-id="9f399-154">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9f399-154">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="9f399-155">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="9f399-155">REST response</span></span>

<span data-ttu-id="9f399-156">Als dit lukt, bevat de antwoord tekst de [SupportContact](subscription-resources.md#supportcontact) -resource.</span><span class="sxs-lookup"><span data-stu-id="9f399-156">If successful, the response body contains the [SupportContact](subscription-resources.md#supportcontact) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9f399-157">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="9f399-157">Response success and error codes</span></span>

<span data-ttu-id="9f399-158">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="9f399-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9f399-159">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="9f399-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9f399-160">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="9f399-160">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9f399-161">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="9f399-161">Response example</span></span>

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
