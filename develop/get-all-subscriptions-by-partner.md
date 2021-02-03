---
title: De abonnementen van een klant ophalen op basis van de MPN-id van de partner
description: Een lijst met abonnementen die door een bepaalde partner worden verstrekt aan een opgegeven klant weer geven.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: c95488b62449e1ab6bd2eeefea58d6686c291f4c
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767498"
---
# <a name="get-a-customers-subscriptions-by-partner-mpn-id"></a><span data-ttu-id="cbb33-103">De abonnementen van een klant ophalen op basis van de MPN-id van de partner</span><span class="sxs-lookup"><span data-stu-id="cbb33-103">Get a customer's subscriptions by partner MPN ID</span></span>

<span data-ttu-id="cbb33-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="cbb33-104">**Applies To**</span></span>

- <span data-ttu-id="cbb33-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="cbb33-105">Partner Center</span></span>
- <span data-ttu-id="cbb33-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="cbb33-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="cbb33-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="cbb33-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="cbb33-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="cbb33-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="cbb33-109">Een lijst met abonnementen die door een bepaalde partner worden verstrekt aan een opgegeven klant weer geven.</span><span class="sxs-lookup"><span data-stu-id="cbb33-109">How to get a list of subscriptions provided by a given partner to a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cbb33-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cbb33-110">Prerequisites</span></span>

- <span data-ttu-id="cbb33-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cbb33-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cbb33-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="cbb33-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="cbb33-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cbb33-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="cbb33-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="cbb33-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="cbb33-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="cbb33-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="cbb33-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="cbb33-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="cbb33-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="cbb33-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="cbb33-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cbb33-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="cbb33-119">Een partner Microsoft Partner Network-ID (MPN).</span><span class="sxs-lookup"><span data-stu-id="cbb33-119">A partner Microsoft Partner Network (MPN) identifier.</span></span>

## <a name="c"></a><span data-ttu-id="cbb33-120">C\#</span><span class="sxs-lookup"><span data-stu-id="cbb33-120">C\#</span></span>

<span data-ttu-id="cbb33-121">Als u een lijst met abonnementen van een bepaalde partner aan een opgegeven klant wilt krijgen, gebruikt u eerst de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="cbb33-121">To get a list of subscriptions provided by a given partner to a specified customer, first use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="cbb33-122">Vervolgens krijgt u een interface voor het verzamelen van klant abonnements bewerkingen via de eigenschap [**abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) en roept u de [**ByPartner**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.bypartner) -methode aan met de MPN-id om de partner te identificeren en een interface op te halen voor het abonnement op de partner.</span><span class="sxs-lookup"><span data-stu-id="cbb33-122">Then get an interface to customer subscription collection operations from the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, and call the [**ByPartner**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.bypartner) method with the MPN ID to identify the partner and retrieve an interface to partner subscription operations.</span></span> <span data-ttu-id="cbb33-123">Roep ten slotte de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync) aan om de verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="cbb33-123">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync) method to get the collection.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string partnerMpnId;

var customerSubscriptionsByMpnId = partnerOperations.Customers.ById(customerId).Subscriptions.ByPartner(partnerMpnId).Get();
```

<span data-ttu-id="cbb33-124">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="cbb33-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="cbb33-125">**Project**: Partner Center SDK-voor beelden **klasse**: GetSubscriptionsByMpnid.cs</span><span class="sxs-lookup"><span data-stu-id="cbb33-125">**Project**: Partner Center SDK Samples **Class**: GetSubscriptionsByMpnid.cs</span></span>

## <a name="java"></a><span data-ttu-id="cbb33-126">Java</span><span class="sxs-lookup"><span data-stu-id="cbb33-126">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="cbb33-127">Als u een lijst met abonnementen van een bepaalde partner aan een opgegeven klant wilt krijgen, gebruikt u eerst de functie **IAggregatePartner. getCustomers. byId** met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="cbb33-127">To get a list of subscriptions provided by a given partner to a specified customer, first use the **IAggregatePartner.getCustomers.byId** function with the customer ID to identify the customer.</span></span> <span data-ttu-id="cbb33-128">Vervolgens krijgt u een interface voor het verzamelen van klant abonnementen via de functie **getSubscriptions** en roept u de functie **byPartner** aan met de MPN-id om de partner te identificeren en een interface op te halen voor abonnements bewerkingen op partner.</span><span class="sxs-lookup"><span data-stu-id="cbb33-128">Then get an interface to customer subscription collection operations from the **getSubscriptions** function, and call the **byPartner** function with the MPN ID to identify the partner and retrieve an interface to partner subscription operations.</span></span> <span data-ttu-id="cbb33-129">Roep ten slotte de **Get** -functie aan om de verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="cbb33-129">Finally, call the **get** function to get the collection.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String partnerMpnId;

ResourceCollection<Subscription> customerSubscriptionsByMpnId = partnerOperations.getCustomers().byId(customerId).getSubscriptions().byPartner(partnerMpnId).get();
```

## <a name="powershell"></a><span data-ttu-id="cbb33-130">PowerShell</span><span class="sxs-lookup"><span data-stu-id="cbb33-130">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="cbb33-131">Voer de opdracht [**Get-PartnerCustomerSubscription**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscription.md) uit om een lijst met abonnementen van een bepaalde partner aan een opgegeven klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="cbb33-131">To get a list of subscriptions provided by a given partner to a specified customer, execute the [**Get-PartnerCustomerSubscription**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerSubscription.md) command.</span></span> <span data-ttu-id="cbb33-132">Geef de klant-ID op om de klant aan te duiden met de para meter **KlantId** en vul de **MpnId** -para meter in met de MPN-id om de partner te identificeren.</span><span class="sxs-lookup"><span data-stu-id="cbb33-132">Specify the customer ID to identify the customer using the **CustomerId** parameter, and populate the **MpnId** parameter with the MPN ID to identify the partner.</span></span>

```powershell
# $customerId
# $partnerMpnId

Get-PartnerCustomerSubscription -CustomerId $customerId -MpnId $partnerMpnId
```

## <a name="rest-request"></a><span data-ttu-id="cbb33-133">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="cbb33-133">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cbb33-134">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cbb33-134">Request syntax</span></span>

| <span data-ttu-id="cbb33-135">Methode</span><span class="sxs-lookup"><span data-stu-id="cbb33-135">Method</span></span>  | <span data-ttu-id="cbb33-136">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="cbb33-136">Request URI</span></span> |
|---------|----------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="cbb33-137">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="cbb33-137">**GET**</span></span> | <span data-ttu-id="cbb33-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Subscriptions? MPN \_ -id = {MPN-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="cbb33-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions?mpn\_id={mpn-id} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="cbb33-139">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="cbb33-139">URI parameters</span></span>

<span data-ttu-id="cbb33-140">Gebruik de volgende pad-en query parameters om de klant en de partner te identificeren.</span><span class="sxs-lookup"><span data-stu-id="cbb33-140">Use the following path and query parameters to identify the customer and partner.</span></span>

| <span data-ttu-id="cbb33-141">Naam</span><span class="sxs-lookup"><span data-stu-id="cbb33-141">Name</span></span>        | <span data-ttu-id="cbb33-142">Type</span><span class="sxs-lookup"><span data-stu-id="cbb33-142">Type</span></span>   | <span data-ttu-id="cbb33-143">Vereist</span><span class="sxs-lookup"><span data-stu-id="cbb33-143">Required</span></span> | <span data-ttu-id="cbb33-144">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cbb33-144">Description</span></span>                                                 |
|-------------|--------|----------|-------------------------------------------------------------|
| <span data-ttu-id="cbb33-145">klant-id</span><span class="sxs-lookup"><span data-stu-id="cbb33-145">customer-id</span></span> | <span data-ttu-id="cbb33-146">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="cbb33-146">string</span></span> | <span data-ttu-id="cbb33-147">Yes</span><span class="sxs-lookup"><span data-stu-id="cbb33-147">Yes</span></span>      | <span data-ttu-id="cbb33-148">Een teken reeks met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="cbb33-148">A GUID formatted string that identifies the customer.</span></span>       |
| <span data-ttu-id="cbb33-149">MPN-id</span><span class="sxs-lookup"><span data-stu-id="cbb33-149">mpn-id</span></span>      | <span data-ttu-id="cbb33-150">int</span><span class="sxs-lookup"><span data-stu-id="cbb33-150">int</span></span>    | <span data-ttu-id="cbb33-151">Ja</span><span class="sxs-lookup"><span data-stu-id="cbb33-151">Yes</span></span>      | <span data-ttu-id="cbb33-152">Een Microsoft Partner Network-ID waarmee de partner wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="cbb33-152">A Microsoft Partner Network ID that identifies the partner.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="cbb33-153">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="cbb33-153">Request headers</span></span>

<span data-ttu-id="cbb33-154">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="cbb33-154">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cbb33-155">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="cbb33-155">Request body</span></span>

<span data-ttu-id="cbb33-156">Geen.</span><span class="sxs-lookup"><span data-stu-id="cbb33-156">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="cbb33-157">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cbb33-157">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="cbb33-158">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="cbb33-158">REST response</span></span>

<span data-ttu-id="cbb33-159">Als dit lukt, bevat de antwoord tekst de verzameling [abonnements](subscription-resources.md) resources.</span><span class="sxs-lookup"><span data-stu-id="cbb33-159">If successful, the response body contains the collection of [Subscription](subscription-resources.md) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cbb33-160">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="cbb33-160">Response success and error codes</span></span>

<span data-ttu-id="cbb33-161">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="cbb33-161">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cbb33-162">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="cbb33-162">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="cbb33-163">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="cbb33-163">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="cbb33-164">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="cbb33-164">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cbb33-165">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cbb33-165">See also</span></span>

- [<span data-ttu-id="cbb33-166">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="cbb33-166">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
