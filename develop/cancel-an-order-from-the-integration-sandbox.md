---
title: Een bestelling van de integratie-sandbox annuleren
description: Meer informatie over het gebruik Partner Center API's om verschillende typen abonnementsorders van sandbox-accounts voor integratie te annuleren.
ms.date: 04/28/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c3bf862c62804a56e6f73dd3ec36d2e9eb65f997
ms.sourcegitcommit: f59a9311c8a37d45695caf74794ec1697426acc9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/29/2021
ms.locfileid: "108210016"
---
# <a name="cancel-an-order-from-the-integration-sandbox-using-partner-center-apis"></a><span data-ttu-id="1aca8-103">Een bestelling van de integratie-sandbox annuleren met behulp van Partner Center API's</span><span class="sxs-lookup"><span data-stu-id="1aca8-103">Cancel an order from the integration sandbox using Partner Center APIs</span></span>

<span data-ttu-id="1aca8-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="1aca8-104">**Applies to:**</span></span>

- <span data-ttu-id="1aca8-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="1aca8-105">Partner Center</span></span>
- <span data-ttu-id="1aca8-106">Partnercentrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="1aca8-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="1aca8-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="1aca8-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="1aca8-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="1aca8-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="1aca8-109">In dit artikel wordt beschreven hoe u Partner Center api's kunt gebruiken om verschillende typen abonnementsorders van sandbox-accounts voor integratie te annuleren.</span><span class="sxs-lookup"><span data-stu-id="1aca8-109">This article describes how to use Partner Center APIs to cancel different types of subscription orders from integration sandbox accounts.</span></span> <span data-ttu-id="1aca8-110">Dergelijke orders kunnen gereserveerde instanties, software en commerciële marketplace-SaaS-abonnementsorders (Software as a Service) bevatten.</span><span class="sxs-lookup"><span data-stu-id="1aca8-110">Such orders can include reserved instances, software, and commercial marketplace Software as a Service (SaaS) subscription orders.</span></span>

>[!NOTE] 
><span data-ttu-id="1aca8-111">Houd er rekening mee dat het annuleren van gereserveerde instanties of saaS-abonnementsorders op de commerciële marketplace alleen mogelijk is via sandbox-accounts voor integratie.</span><span class="sxs-lookup"><span data-stu-id="1aca8-111">Please be aware that the cancellations of reserved instance, or commercial marketplace SaaS subscription orders are only possible from integration sandbox accounts.</span></span> <span data-ttu-id="1aca8-112">Sandbox-orders die ouder zijn dan 60 dagen, kunnen niet worden geannuleerd voor Partner Center.</span><span class="sxs-lookup"><span data-stu-id="1aca8-112">Any sandbox orders which are older than 60 days cannot be cancelled from Partner Center.</span></span> <span data-ttu-id="1aca8-113">Als u hulp nodig hebt, kunt u contact op Partner Center ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="1aca8-113">If you need assistance, reach out to Partner Center Support.</span></span> 

<span data-ttu-id="1aca8-114">Als u productieorders van software via de API wilt annuleren, gebruikt [u cancel-software-purchases.](cancel-software-purchases.md)</span><span class="sxs-lookup"><span data-stu-id="1aca8-114">To cancel production orders of software through API, use [cancel-software-purchases](cancel-software-purchases.md).</span></span>
<span data-ttu-id="1aca8-115">U kunt productieorders van software ook annuleren via een dashboard met [behulp van een aankoop annuleren.](/partner-center/csp-software-subscriptions)</span><span class="sxs-lookup"><span data-stu-id="1aca8-115">You can also cancel production orders of software through dashboard using [cancel a purchase](/partner-center/csp-software-subscriptions).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1aca8-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1aca8-116">Prerequisites</span></span>

- <span data-ttu-id="1aca8-117">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="1aca8-117">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1aca8-118">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="1aca8-118">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="1aca8-119">Een sandbox-partneraccount voor integratie met een klant met actieve gereserveerde instanties/software/SaaS-abonnementsorders van derden.</span><span class="sxs-lookup"><span data-stu-id="1aca8-119">An integration sandbox partner account with a customer having active reserved instance / software / third-party SaaS subscription orders.</span></span>

## <a name="c"></a><span data-ttu-id="1aca8-120">C\#</span><span class="sxs-lookup"><span data-stu-id="1aca8-120">C\#</span></span>

<span data-ttu-id="1aca8-121">Als u een bestelling uit de integratie-sandbox wilt annuleren, moet u uw accountreferenties doorgeven aan de methode om een interface op te halen voor [**`CreatePartnerOperations`**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) [**`IPartner`**](/dotnet/api/microsoft.store.partnercenter.ipartner) het uitvoeren van partnerbewerkingen.</span><span class="sxs-lookup"><span data-stu-id="1aca8-121">To cancel an order from the integration sandbox, pass your account credentials to the [**`CreatePartnerOperations`**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) method to get an [**`IPartner`**](/dotnet/api/microsoft.store.partnercenter.ipartner) interface to get partner operations.</span></span>

<span data-ttu-id="1aca8-122">Als u een bepaalde Order wilt [selecteren,](order-resources.md#order)gebruikt u de partnerbewerkingen en roept u de methode aan met de klant-id om de klant op te geven, gevolgd door met order-id om de order op te geven en ten slotte of de methode om deze op te [**`Customers.ById()`**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) **`Orders.ById()`** **`Get`** **`GetAsync`** halen.</span><span class="sxs-lookup"><span data-stu-id="1aca8-122">To select a particular [Order](order-resources.md#order), use the partner operations and call [**`Customers.ById()`**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to specify the customer, followed by **`Orders.ById()`** with order identifier to specify the order and finally **`Get`** or **`GetAsync`** method to retrieve it.</span></span>

<span data-ttu-id="1aca8-123">Stel de [**`Order.Status`**](order-resources.md#order) eigenschap in op en gebruik de methode om de volgorde bij te `cancelled` **`Patch()`** werken.</span><span class="sxs-lookup"><span data-stu-id="1aca8-123">Set the [**`Order.Status`**](order-resources.md#order) property to `cancelled` and use the **`Patch()`** method to update the order.</span></span>

``` csharp
// IPartnerCredentials tipAccountCredentials;
// Customer tenant Id to be deleted.
// string customerTenantId;

IPartner tipAccountPartnerOperations = PartnerService.Instance.CreatePartnerOperations(tipAccountCredentials);

// Cancel order
var order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(orderId).Get();
order.Status = "cancelled";
order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(orderId).Patch(order);

```

## <a name="rest-request"></a><span data-ttu-id="1aca8-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="1aca8-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1aca8-125">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="1aca8-125">Request syntax</span></span>

| <span data-ttu-id="1aca8-126">Methode</span><span class="sxs-lookup"><span data-stu-id="1aca8-126">Method</span></span>     | <span data-ttu-id="1aca8-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="1aca8-127">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="1aca8-128">**Patch**</span><span class="sxs-lookup"><span data-stu-id="1aca8-128">**PATCH**</span></span> | <span data-ttu-id="1aca8-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="1aca8-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="1aca8-130">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="1aca8-130">URI parameter</span></span>

<span data-ttu-id="1aca8-131">Gebruik de volgende queryparameter om een klant te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="1aca8-131">Use the following query parameter to delete a customer.</span></span>

| <span data-ttu-id="1aca8-132">Naam</span><span class="sxs-lookup"><span data-stu-id="1aca8-132">Name</span></span>                   | <span data-ttu-id="1aca8-133">Type</span><span class="sxs-lookup"><span data-stu-id="1aca8-133">Type</span></span>     | <span data-ttu-id="1aca8-134">Vereist</span><span class="sxs-lookup"><span data-stu-id="1aca8-134">Required</span></span> | <span data-ttu-id="1aca8-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1aca8-135">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1aca8-136">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="1aca8-136">**customer-tenant-id**</span></span> | <span data-ttu-id="1aca8-137">**guid**</span><span class="sxs-lookup"><span data-stu-id="1aca8-137">**guid**</span></span> | <span data-ttu-id="1aca8-138">J</span><span class="sxs-lookup"><span data-stu-id="1aca8-138">Y</span></span>        | <span data-ttu-id="1aca8-139">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="1aca8-139">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="1aca8-140">**order-id**</span><span class="sxs-lookup"><span data-stu-id="1aca8-140">**order-id**</span></span> | <span data-ttu-id="1aca8-141">**tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="1aca8-141">**string**</span></span> | <span data-ttu-id="1aca8-142">J</span><span class="sxs-lookup"><span data-stu-id="1aca8-142">Y</span></span>        | <span data-ttu-id="1aca8-143">De waarde is een tekenreeks die de order-ID's aantekent die moeten worden geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="1aca8-143">The value is a string denoting the order IDs that need to be canceled.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="1aca8-144">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="1aca8-144">Request headers</span></span>

<span data-ttu-id="1aca8-145">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="1aca8-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1aca8-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="1aca8-146">Request body</span></span>

```http
{
    "id": "UKXASSO1dezh3HdxClHxSp5UEFXGbAnt1",
    "status": "cancelled",
}
```

### <a name="request-example"></a><span data-ttu-id="1aca8-147">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1aca8-147">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/orders/<order-id> HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd

{
    "id": "UKXASSO1dezh3HdxClHxSp5UEFXGbAnt1",
    "status": "cancelled",
}
```

## <a name="rest-response"></a><span data-ttu-id="1aca8-148">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="1aca8-148">REST response</span></span>

<span data-ttu-id="1aca8-149">Als dit lukt, retourneert deze methode de geannuleerde bestelling.</span><span class="sxs-lookup"><span data-stu-id="1aca8-149">If successful, this method returns the canceled order.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1aca8-150">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="1aca8-150">Response success and error codes</span></span>

<span data-ttu-id="1aca8-151">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="1aca8-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1aca8-152">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="1aca8-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1aca8-153">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="1aca8-153">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="1aca8-154">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="1aca8-154">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 866
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

{
    "id": "UKXASSO1dezh3HdxClHxSp5UEFXGbAnt1",
    "alternateId": "11fc4bdfd47a",
    "referenceCustomerId": "bd59b416-37f9-4d8f-8df3-5750111fc615",
    "billingCycle": "one_time",
    "currencyCode": "USD",
    "currencySymbol": "$",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "offerId": "DG7GMGF0DWT0:0001:DG7GMGF0DSQR",
            "termDuration": "",
            "transactionType": "New",
            "friendlyName": "Microsoft Identity Manager 2016 - 1 User CAL",
            "quantity": 1,
            "links": {
                "product": {
                    "uri": "/products/DG7GMGF0DWT0?country=US",
                    "method": "GET",
                    "headers": []
                },
                "sku": {
                    "uri": "/products/DG7GMGF0DWT0/skus/0001?country=US",
                    "method": "GET",
                    "headers": []
                },
                "availability": {
                    "uri": "/products/DG7GMGF0DWT0/skus/0001/availabilities/DG7GMGF0DSQR?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2019-02-21T17:56:21.1335741Z",
    "status": "cancelled",
    "transactionType": "UserPurchase",
    "attributes": {
        "objectType": "Order"
    }
}
```
