---
title: Een order annuleren vanuit een integratie sandbox
description: Meer informatie over het gebruik van partner Center-Api's voor het annuleren van verschillende soorten abonnements orders uit integratie Sandbox-accounts.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 363bf209e27d5223259c8c533710a3b35bbef1e6
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2020
ms.locfileid: "97767622"
---
# <a name="cancel-an-order-from-the-integration-sandbox-using-partner-center-apis"></a><span data-ttu-id="78104-103">Een order annuleren vanuit de integratie sandbox met partner Center-Api's</span><span class="sxs-lookup"><span data-stu-id="78104-103">Cancel an order from the integration sandbox using Partner Center APIs</span></span>

<span data-ttu-id="78104-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="78104-104">**Applies to:**</span></span>

- <span data-ttu-id="78104-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="78104-105">Partner Center</span></span>
- <span data-ttu-id="78104-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="78104-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="78104-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="78104-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="78104-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="78104-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="78104-109">In dit artikel wordt beschreven hoe u partner Center-Api's kunt gebruiken om verschillende soorten abonnements orders te annuleren op basis van integratie Sandbox-accounts.</span><span class="sxs-lookup"><span data-stu-id="78104-109">This article describes how to use Partner Center APIs to cancel different types of subscription orders from integration sandbox accounts.</span></span> <span data-ttu-id="78104-110">Deze orders kunnen gereserveerde instanties, software en software als een service (SaaS)-abonnement op de markt zijn.</span><span class="sxs-lookup"><span data-stu-id="78104-110">Such orders can include reserved instances, software, and commercial marketplace Software as a Service (SaaS) subscription orders.</span></span>

>[!NOTE]
><span data-ttu-id="78104-111">Houd er rekening mee dat de annuleringen van gereserveerde instanties of het gebruik van SaaS-abonnements orders voor commerciële Marketplace alleen mogelijk zijn via integratie Sandbox-accounts.</span><span class="sxs-lookup"><span data-stu-id="78104-111">Please be aware that the cancellations of reserved instance, or commercial marketplace SaaS subscription orders are only possible from integration sandbox accounts.</span></span>  

<span data-ttu-id="78104-112">Gebruik [annulering-software-purchases](cancel-software-purchases.md)om productie orders van software via API te annuleren.</span><span class="sxs-lookup"><span data-stu-id="78104-112">To cancel production orders of software through API, use [cancel-software-purchases](cancel-software-purchases.md).</span></span>
<span data-ttu-id="78104-113">U kunt ook productie orders van software annuleren via een dash board met behulp van [een aankoop annuleren](/partner-center/csp-software-subscriptions).</span><span class="sxs-lookup"><span data-stu-id="78104-113">You can also cancel production orders of software through dashboard using [cancel a purchase](/partner-center/csp-software-subscriptions).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="78104-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="78104-114">Prerequisites</span></span>

- <span data-ttu-id="78104-115">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="78104-115">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="78104-116">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="78104-116">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="78104-117">Een integratie sandbox-partner account met een klant die actief gereserveerde instanties/software/SaaS-abonnements orders van derden heeft.</span><span class="sxs-lookup"><span data-stu-id="78104-117">An integration sandbox partner account with a customer having active reserved instance / software / third-party SaaS subscription orders.</span></span>

## <a name="c"></a><span data-ttu-id="78104-118">C\#</span><span class="sxs-lookup"><span data-stu-id="78104-118">C\#</span></span>

<span data-ttu-id="78104-119">Als u een order wilt annuleren vanuit de integratie sandbox, geeft u uw account referenties door aan de- [**`CreatePartnerOperations`**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) methode om een [**`IPartner`**](/dotnet/api/microsoft.store.partnercenter.ipartner) interface te verkrijgen voor het ophalen van partner bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="78104-119">To cancel an order from the integration sandbox, pass your account credentials to the [**`CreatePartnerOperations`**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) method to get an [**`IPartner`**](/dotnet/api/microsoft.store.partnercenter.ipartner) interface to get partner operations.</span></span>

<span data-ttu-id="78104-120">Als u een bepaalde [volg orde](order-resources.md#order)wilt selecteren, gebruikt u de partner bewerkingen en roept [**`Customers.ById()`**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) u de methode van de klant-id op om de klant op te geven, gevolgd door de **`Orders.ById()`** order-id om de volg orde en ten slotte **`Get`** of de methode op te geven die u wilt **`GetAsync`** ophalen.</span><span class="sxs-lookup"><span data-stu-id="78104-120">To select a particular [Order](order-resources.md#order), use the partner operations and call [**`Customers.ById()`**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to specify the customer, followed by **`Orders.ById()`** with order identifier to specify the order and finally **`Get`** or **`GetAsync`** method to retrieve it.</span></span>

<span data-ttu-id="78104-121">Stel de [**`Order.Status`**](order-resources.md#order) eigenschap in op `cancelled` en gebruik de **`Patch()`** methode om de volg orde bij te werken.</span><span class="sxs-lookup"><span data-stu-id="78104-121">Set the [**`Order.Status`**](order-resources.md#order) property to `cancelled` and use the **`Patch()`** method to update the order.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="78104-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="78104-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="78104-123">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="78104-123">Request syntax</span></span>

| <span data-ttu-id="78104-124">Methode</span><span class="sxs-lookup"><span data-stu-id="78104-124">Method</span></span>     | <span data-ttu-id="78104-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="78104-125">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="78104-126">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="78104-126">**PATCH**</span></span> | <span data-ttu-id="78104-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/orders/{order-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="78104-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="78104-128">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="78104-128">URI parameter</span></span>

<span data-ttu-id="78104-129">Gebruik de volgende query parameter om een klant te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="78104-129">Use the following query parameter to delete a customer.</span></span>

| <span data-ttu-id="78104-130">Naam</span><span class="sxs-lookup"><span data-stu-id="78104-130">Name</span></span>                   | <span data-ttu-id="78104-131">Type</span><span class="sxs-lookup"><span data-stu-id="78104-131">Type</span></span>     | <span data-ttu-id="78104-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="78104-132">Required</span></span> | <span data-ttu-id="78104-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="78104-133">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="78104-134">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="78104-134">**customer-tenant-id**</span></span> | <span data-ttu-id="78104-135">**guid**</span><span class="sxs-lookup"><span data-stu-id="78104-135">**guid**</span></span> | <span data-ttu-id="78104-136">J</span><span class="sxs-lookup"><span data-stu-id="78104-136">Y</span></span>        | <span data-ttu-id="78104-137">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="78104-137">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="78104-138">**order-id**</span><span class="sxs-lookup"><span data-stu-id="78104-138">**order-id**</span></span> | <span data-ttu-id="78104-139">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="78104-139">**string**</span></span> | <span data-ttu-id="78104-140">J</span><span class="sxs-lookup"><span data-stu-id="78104-140">Y</span></span>        | <span data-ttu-id="78104-141">De waarde is een teken reeks voor het identificeren van de order-Id's die moeten worden geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="78104-141">The value is a string denoting the order IDs that need to be canceled.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="78104-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="78104-142">Request headers</span></span>

<span data-ttu-id="78104-143">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="78104-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="78104-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="78104-144">Request body</span></span>

```http
{
    "id": "UKXASSO1dezh3HdxClHxSp5UEFXGbAnt1",
    "status": "cancelled",
}
```

### <a name="request-example"></a><span data-ttu-id="78104-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="78104-145">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="78104-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="78104-146">REST response</span></span>

<span data-ttu-id="78104-147">Als deze methode is geslaagd, wordt de geannuleerde volg orde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="78104-147">If successful, this method returns the canceled order.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="78104-148">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="78104-148">Response success and error codes</span></span>

<span data-ttu-id="78104-149">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="78104-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="78104-150">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="78104-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="78104-151">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="78104-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="78104-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="78104-152">Response example</span></span>

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
