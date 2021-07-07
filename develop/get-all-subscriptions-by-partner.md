---
title: De abonnementen van een klant ophalen op basis van de MPN-id van de partner
description: Een lijst met abonnementen die door een bepaalde partner aan een opgegeven klant worden geleverd, op te halen.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 857caa667245503f111b27379a5c8f93aa1fb0b0
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760654"
---
# <a name="get-a-customers-subscriptions-by-partner-mpn-id"></a><span data-ttu-id="8fded-103">De abonnementen van een klant ophalen op basis van de MPN-id van de partner</span><span class="sxs-lookup"><span data-stu-id="8fded-103">Get a customer's subscriptions by partner MPN ID</span></span>

<span data-ttu-id="8fded-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="8fded-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="8fded-105">Een lijst met abonnementen die door een bepaalde mpn-partner (MICROSOFT PARTNER NETWORK) aan een opgegeven klant worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="8fded-105">How to get a list of subscriptions provided by a given Microsoft Partner Network (MPN) partner to a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8fded-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="8fded-106">Prerequisites</span></span>

- <span data-ttu-id="8fded-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8fded-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8fded-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="8fded-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="8fded-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8fded-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="8fded-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="8fded-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="8fded-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="8fded-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="8fded-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="8fded-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="8fded-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="8fded-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="8fded-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8fded-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="8fded-115">Een MPN-partner-id.</span><span class="sxs-lookup"><span data-stu-id="8fded-115">A partner MPN identifier.</span></span>

## <a name="c"></a><span data-ttu-id="8fded-116">C\#</span><span class="sxs-lookup"><span data-stu-id="8fded-116">C\#</span></span>

<span data-ttu-id="8fded-117">Gebruik eerst de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om een lijst op te halen met abonnementen die door een bepaalde partner aan een opgegeven klant worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="8fded-117">To get a list of subscriptions provided by a given partner to a specified customer, first use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="8fded-118">Haal vervolgens een interface op voor [](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) verzamelingen van klantabonnementen van de eigenschap Abonnementen en roep de methode [**ByPartner**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.bypartner) aan met de MPN-id om de partner te identificeren en een interface voor partnerabonnementbewerkingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="8fded-118">Then get an interface to customer subscription collection operations from the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, and call the [**ByPartner**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.bypartner) method with the MPN ID to identify the partner and retrieve an interface to partner subscription operations.</span></span> <span data-ttu-id="8fded-119">Roep ten slotte de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync) om de verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="8fded-119">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync) method to get the collection.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string partnerMpnId;

var customerSubscriptionsByMpnId = partnerOperations.Customers.ById(customerId).Subscriptions.ByPartner(partnerMpnId).Get();
```

<span data-ttu-id="8fded-120">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="8fded-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="8fded-121">**Project**: Partnercentrum-SDK Samples **Class**: GetSubscriptionsByMpnid.cs</span><span class="sxs-lookup"><span data-stu-id="8fded-121">**Project**: Partner Center SDK Samples **Class**: GetSubscriptionsByMpnid.cs</span></span>

## <a name="java"></a><span data-ttu-id="8fded-122">Java</span><span class="sxs-lookup"><span data-stu-id="8fded-122">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="8fded-123">Gebruik eerst de functie **IAggregatePartner.getCustomers.byId** met de klant-id om een lijst met abonnementen op te halen die door een bepaalde partner aan een opgegeven klant worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="8fded-123">To get a list of subscriptions provided by a given partner to a specified customer, first use the **IAggregatePartner.getCustomers.byId** function with the customer ID to identify the customer.</span></span> <span data-ttu-id="8fded-124">Haal vervolgens een interface op voor verzamelingen van klantabonnementen via de functie **getSubscriptions** en roep de functie **byPartner** aan met de MPN-id om de partner te identificeren en een interface voor partnerabonnementbewerkingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="8fded-124">Then get an interface to customer subscription collection operations from the **getSubscriptions** function, and call the **byPartner** function with the MPN ID to identify the partner and retrieve an interface to partner subscription operations.</span></span> <span data-ttu-id="8fded-125">Roep ten slotte de **functie get aan** om de verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="8fded-125">Finally, call the **get** function to get the collection.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String partnerMpnId;

ResourceCollection<Subscription> customerSubscriptionsByMpnId = partnerOperations.getCustomers().byId(customerId).getSubscriptions().byPartner(partnerMpnId).get();
```

## <a name="powershell"></a><span data-ttu-id="8fded-126">PowerShell</span><span class="sxs-lookup"><span data-stu-id="8fded-126">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="8fded-127">Voer de opdracht [**Get-PartnerCustomerSubscription**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscription.md) uit om een lijst met abonnementen op te halen die door een bepaalde partner aan een opgegeven klant worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="8fded-127">To get a list of subscriptions provided by a given partner to a specified customer, execute the [**Get-PartnerCustomerSubscription**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscription.md) command.</span></span> <span data-ttu-id="8fded-128">Geef de klant-id op om de klant te identificeren met behulp van de parameter **CustomerId** en vul de parameter **MpnId** met de MPN-id om de partner te identificeren.</span><span class="sxs-lookup"><span data-stu-id="8fded-128">Specify the customer ID to identify the customer using the **CustomerId** parameter, and populate the **MpnId** parameter with the MPN ID to identify the partner.</span></span>

```powershell
# $customerId
# $partnerMpnId

Get-PartnerCustomerSubscription -CustomerId $customerId -MpnId $partnerMpnId
```

## <a name="rest-request"></a><span data-ttu-id="8fded-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="8fded-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8fded-130">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="8fded-130">Request syntax</span></span>

| <span data-ttu-id="8fded-131">Methode</span><span class="sxs-lookup"><span data-stu-id="8fded-131">Method</span></span>  | <span data-ttu-id="8fded-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="8fded-132">Request URI</span></span> |
|---------|----------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8fded-133">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="8fded-133">**GET**</span></span> | <span data-ttu-id="8fded-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions?mpn \_ id={mpn-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8fded-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions?mpn\_id={mpn-id} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="8fded-135">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="8fded-135">URI parameters</span></span>

<span data-ttu-id="8fded-136">Gebruik het volgende pad en de queryparameters om de klant en partner te identificeren.</span><span class="sxs-lookup"><span data-stu-id="8fded-136">Use the following path and query parameters to identify the customer and partner.</span></span>

| <span data-ttu-id="8fded-137">Naam</span><span class="sxs-lookup"><span data-stu-id="8fded-137">Name</span></span>        | <span data-ttu-id="8fded-138">Type</span><span class="sxs-lookup"><span data-stu-id="8fded-138">Type</span></span>   | <span data-ttu-id="8fded-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="8fded-139">Required</span></span> | <span data-ttu-id="8fded-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8fded-140">Description</span></span>                                                 |
|-------------|--------|----------|-------------------------------------------------------------|
| <span data-ttu-id="8fded-141">customer-id</span><span class="sxs-lookup"><span data-stu-id="8fded-141">customer-id</span></span> | <span data-ttu-id="8fded-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="8fded-142">string</span></span> | <span data-ttu-id="8fded-143">Ja</span><span class="sxs-lookup"><span data-stu-id="8fded-143">Yes</span></span>      | <span data-ttu-id="8fded-144">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="8fded-144">A GUID formatted string that identifies the customer.</span></span>       |
| <span data-ttu-id="8fded-145">mpn-id</span><span class="sxs-lookup"><span data-stu-id="8fded-145">mpn-id</span></span>      | <span data-ttu-id="8fded-146">int</span><span class="sxs-lookup"><span data-stu-id="8fded-146">int</span></span>    | <span data-ttu-id="8fded-147">Ja</span><span class="sxs-lookup"><span data-stu-id="8fded-147">Yes</span></span>      | <span data-ttu-id="8fded-148">Een Microsoft Partner Network-id die de partner identificeert.</span><span class="sxs-lookup"><span data-stu-id="8fded-148">A Microsoft Partner Network ID that identifies the partner.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8fded-149">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="8fded-149">Request headers</span></span>

<span data-ttu-id="8fded-150">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="8fded-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8fded-151">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="8fded-151">Request body</span></span>

<span data-ttu-id="8fded-152">Geen.</span><span class="sxs-lookup"><span data-stu-id="8fded-152">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="8fded-153">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="8fded-153">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/subscriptions?mpn_id=4847383 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: d0e38dfd-a2c5-4a14-ac06-12d30f0ec54e
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="8fded-154">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="8fded-154">REST response</span></span>

<span data-ttu-id="8fded-155">Als dit lukt, bevat de antwoord-body de verzameling [abonnementsresources.](subscription-resources.md)</span><span class="sxs-lookup"><span data-stu-id="8fded-155">If successful, the response body contains the collection of [Subscription](subscription-resources.md) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8fded-156">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="8fded-156">Response success and error codes</span></span>

<span data-ttu-id="8fded-157">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="8fded-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8fded-158">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="8fded-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8fded-159">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="8fded-159">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8fded-160">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="8fded-160">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 985
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
MS-RequestId: d0e38dfd-a2c5-4a14-ac06-12d30f0ec54e
MS-CV: LdFhumtx6Ea0Kl5Z.0
MS-ServerId: 101112202
Date: Thu, 13 Apr 2017 20:58:08 GMT

{
    "totalCount": 1,
    "items": [{
            "id": "42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
            "offerId": "DB2E705F-B82A-4024-A3D5-D88E12F2DB35",
            "offerName": "Intune Device",
            "friendlyName": "new offer purchase",
            "quantity": 5,
            "unitType": "Licenses",
            "creationDate": "2017-04-10T23:02:26.02Z",
            "effectiveStartDate": "2017-04-10T00:00:00Z",
            "commitmentEndDate": "2018-05-07T00:00:00Z",
            "status": "active",
            "autoRenewEnabled": true,
            "isTrial": false,
            "billingType": "license",
            "billingCycle": "monthly",
            "partnerId": "4847383",
            "contractType": "subscription",
            "links": {
                "offer": {
                    "uri": "/offers/DB2E705F-B82A-4024-A3D5-D88E12F2DB35?country=US",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/subscriptions/42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
                    "method": "GET",
                    "headers": []
                }
            },
            "orderId": "3EDDCAC6-63B2-4C40-B0B6-F47E18301492",
            "attributes": {
                "etag": "eyJpZCI6IjQyMjI2ZWQ2LTA3MGEtNGUwZi1iODBjLTRjZGZiM2U5N2FhNyIsInZlcnNpb24iOjF9",
                "objectType": "Subscription"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```

## <a name="see-also"></a><span data-ttu-id="8fded-161">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8fded-161">See also</span></span>

- [<span data-ttu-id="8fded-162">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="8fded-162">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
