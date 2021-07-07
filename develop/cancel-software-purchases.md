---
title: Softwareaankopen annuleren
description: Self-serve optie voor het annuleren van softwareabonnementen en permanente software-aankopen met behulp Partner Center API's.
ms.date: 12/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 877702ac930919ff72c6cc45a3c0e8ecc7e1b5f4
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974230"
---
# <a name="cancel-software-purchases"></a><span data-ttu-id="bb701-103">Softwareaankopen annuleren</span><span class="sxs-lookup"><span data-stu-id="bb701-103">Cancel software purchases</span></span>

<span data-ttu-id="bb701-104">U kunt de Partner Center-API's gebruiken om softwareabonnementen en permanente software-aankopen te annuleren (zolang deze aankopen zijn gedaan binnen het annuleringsvenster vanaf de aankoopdatum).</span><span class="sxs-lookup"><span data-stu-id="bb701-104">You can use the Partner Center APIs to cancel software subscriptions and perpetual software purchases (as long as those purchases were made within the cancellation window from the purchase date).</span></span> <span data-ttu-id="bb701-105">U hoeft geen ondersteuningsticket te maken om dergelijke annuleringen te maken en u kunt in plaats daarvan de volgende selfservicemethoden gebruiken.</span><span class="sxs-lookup"><span data-stu-id="bb701-105">You don't need to create a support ticket to make such cancellations, and can use the following self-service methods instead.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bb701-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="bb701-106">Prerequisites</span></span>

- <span data-ttu-id="bb701-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bb701-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="bb701-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="bb701-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="bb701-109">C\#</span><span class="sxs-lookup"><span data-stu-id="bb701-109">C\#</span></span>

<span data-ttu-id="bb701-110">Een softwareorder annuleren:</span><span class="sxs-lookup"><span data-stu-id="bb701-110">To cancel a software order,</span></span>

1. <span data-ttu-id="bb701-111">Geef uw accountreferenties door aan de [**methode CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) om een [**IPartner-interface**](/dotnet/api/microsoft.store.partnercenter.ipartner) op te halen om partnerbewerkingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="bb701-111">Pass your account credentials to the [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) method to get an [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) interface to get partner operations.</span></span>

2. <span data-ttu-id="bb701-112">Selecteer een bepaalde [order](order-resources.md#order) die u wilt annuleren.</span><span class="sxs-lookup"><span data-stu-id="bb701-112">Select a particular [Order](order-resources.md#order) you wish to cancel.</span></span> <span data-ttu-id="bb701-113">Roep de [**methode Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id, gevolgd door **Orders.ById() met** order-id.</span><span class="sxs-lookup"><span data-stu-id="bb701-113">Call the [**Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier, followed by **Orders.ById()** with order identifier.</span></span>

3. <span data-ttu-id="bb701-114">Roep de **methode Get** of **GetAsync aan** om de bestelling op te halen.</span><span class="sxs-lookup"><span data-stu-id="bb701-114">Call the **Get** or **GetAsync** method to retrieve the order.</span></span>

4. <span data-ttu-id="bb701-115">Stel de [**eigenschap Order.Status**](order-resources.md#order) in op `cancelled` .</span><span class="sxs-lookup"><span data-stu-id="bb701-115">Set the [**Order.Status**](order-resources.md#order) property to `cancelled`.</span></span>

5. <span data-ttu-id="bb701-116">(Optioneel) Als u bepaalde regelitems voor annulering wilt opgeven, stelt u [**Order.LineItems**](order-resources.md#order) in op een lijst met regelitems die u wilt annuleren.</span><span class="sxs-lookup"><span data-stu-id="bb701-116">(Optional) If you want to specify certain line items for cancellation, set the [**Order.LineItems**](order-resources.md#order) to list of line items that you want to cancel.</span></span>

6. <span data-ttu-id="bb701-117">Gebruik de **methode Patch()** om de volgorde bij te werken.</span><span class="sxs-lookup"><span data-stu-id="bb701-117">Use the **Patch()** method to update the order.</span></span>

``` csharp
// IPartnerCredentials accountCredentials;
// Customer tenant Id to be deleted.
// string customerTenantId;

IPartner accountPartnerOperations = PartnerService.Instance.CreatePartnerOperations(accountCredentials);

// Cancel order
var order = accountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(orderId).Get();
order.Status = "cancelled";
order.LineItems = new List<OrderLineItem> {
    order.LineItems.First()
};
order = accountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(orderId).Patch(order);

```

## <a name="rest-request"></a><span data-ttu-id="bb701-118">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="bb701-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="bb701-119">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="bb701-119">Request syntax</span></span>

| <span data-ttu-id="bb701-120">Methode</span><span class="sxs-lookup"><span data-stu-id="bb701-120">Method</span></span>     | <span data-ttu-id="bb701-121">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="bb701-121">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="bb701-122">**Patch**</span><span class="sxs-lookup"><span data-stu-id="bb701-122">**PATCH**</span></span> | <span data-ttu-id="bb701-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="bb701-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="bb701-124">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="bb701-124">URI parameters</span></span>

<span data-ttu-id="bb701-125">Gebruik de volgende queryparameters om een klant te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="bb701-125">Use the following query parameters to delete a customer.</span></span>

| <span data-ttu-id="bb701-126">Naam</span><span class="sxs-lookup"><span data-stu-id="bb701-126">Name</span></span>                   | <span data-ttu-id="bb701-127">Type</span><span class="sxs-lookup"><span data-stu-id="bb701-127">Type</span></span>     | <span data-ttu-id="bb701-128">Vereist</span><span class="sxs-lookup"><span data-stu-id="bb701-128">Required</span></span> | <span data-ttu-id="bb701-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bb701-129">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="bb701-130">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="bb701-130">**customer-tenant-id**</span></span> | <span data-ttu-id="bb701-131">**guid**</span><span class="sxs-lookup"><span data-stu-id="bb701-131">**guid**</span></span> | <span data-ttu-id="bb701-132">J</span><span class="sxs-lookup"><span data-stu-id="bb701-132">Y</span></span>        | <span data-ttu-id="bb701-133">De waarde is een tenant-id met GUID-indeling waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="bb701-133">The value is a GUID formatted customer tenant identifier that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="bb701-134">**order-id**</span><span class="sxs-lookup"><span data-stu-id="bb701-134">**order-id**</span></span> | <span data-ttu-id="bb701-135">**tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="bb701-135">**string**</span></span> | <span data-ttu-id="bb701-136">J</span><span class="sxs-lookup"><span data-stu-id="bb701-136">Y</span></span>        | <span data-ttu-id="bb701-137">De waarde is een tekenreeks die de id aanneert van de volgorde die u wilt annuleren.</span><span class="sxs-lookup"><span data-stu-id="bb701-137">The value is a string that denotes the identifier of the order that you want to cancel.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="bb701-138">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="bb701-138">Request headers</span></span>

<span data-ttu-id="bb701-139">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="bb701-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="bb701-140">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="bb701-140">Request body</span></span>

```http
{
    “id”: “2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
    status": "cancelled",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "offerId": "DG7GMGF0FKZV:0003:DG7GMGF0DWMS"
        }
    ]
}
```

### <a name="request-example"></a><span data-ttu-id="bb701-141">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="bb701-141">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/orders/<order-id> HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd

{
    "id": "2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
    "status": "cancelled",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "offerId": "DG7GMGF0FKZV:0003:DG7GMGF0DWMS"
        }
    ]
}
```

## <a name="rest-response"></a><span data-ttu-id="bb701-142">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="bb701-142">REST response</span></span>

<span data-ttu-id="bb701-143">Als dit lukt, retourneert deze methode de bestelling met geannuleerde regelitems.</span><span class="sxs-lookup"><span data-stu-id="bb701-143">If successful, this method returns the order with canceled line items.</span></span>

<span data-ttu-id="bb701-144">De orderstatus wordt gemarkeerd  als geannuleerd als alle regelitems in  de order zijn geannuleerd of worden voltooid als niet alle regelitems in de order zijn geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="bb701-144">The order status will be marked as either **cancelled** if all the line items in the order are canceled, or **completed** if not all line items in the order are canceled.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="bb701-145">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="bb701-145">Response success and error codes</span></span>

<span data-ttu-id="bb701-146">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="bb701-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="bb701-147">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="bb701-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="bb701-148">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="bb701-148">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="bb701-149">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="bb701-149">Response example</span></span>

<span data-ttu-id="bb701-150">In het volgende voorbeeld van een antwoord ziet u dat het aantal regelitem met de aanbiedings-id **`DG7GMGF0FKZV:0003:DG7GMGF0DWMS`** nul (0) is geworden.</span><span class="sxs-lookup"><span data-stu-id="bb701-150">In the following example response, you can see that the quantity of line item with the offer identifier **`DG7GMGF0FKZV:0003:DG7GMGF0DWMS`** has become zero (0).</span></span> <span data-ttu-id="bb701-151">Deze wijziging betekent dat het regelitem dat is gemarkeerd voor annulering, is geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="bb701-151">This change means that the line item that was marked for cancellation has been canceled successfully.</span></span> <span data-ttu-id="bb701-152">De voorbeeldorder bevat andere regelitems die niet zijn geannuleerd, wat betekent dat de status van de algehele bestelling wordt gemarkeerd als **voltooid,** niet **geannuleerd.**</span><span class="sxs-lookup"><span data-stu-id="bb701-152">The example order contains other line items that weren't canceled, which means that the status of the overall order will be marked as **completed**, not **cancelled**.</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 866
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

{
    "id": "2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
    "alternateId": "c403d91b21d2",
    "referenceCustomerId": "45411344-b09d-47e7-9653-542006bf9766",
    "billingCycle": "one_time",
    "currencyCode": "USD",
    "currencySymbol": "$",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "offerId": "DG7GMGF0FKZV:0003:DG7GMGF0DWMS",
            "termDuration": "P3Y",
            "transactionType": "New",
            "friendlyName": "SQL Server Enterprise - 2 Core License Pack - 3 year",
            "quantity": 0,
            "links": {
                "product": {
                    "uri": "/products/DG7GMGF0FKZV?country=US",
                    "method": "GET",
                    "headers": []
                },
                "sku": {
                    "uri": "/products/DG7GMGF0FKZV/skus/0003?country=US",
                    "method": "GET",
                    "headers": []
                },
                "availability": {
                    "uri": "/products/DG7GMGF0FKZV/skus/0003/availabilities/DG7GMGF0DWMS?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        },
        {
            "lineItemNumber": 1,
            "offerId": "DG7GMGF0DVT7:000C:DG7GMGF0FVZM",
            "termDuration": "P3Y",
            "transactionType": "New",
            "friendlyName": "Windows Server CAL - 1 Device CAL - 3 year",
            "quantity": 1,
            "links": {
                "product": {
                    "uri": "/products/DG7GMGF0DVT7?country=US",
                    "method": "GET",
                    "headers": []
                },
                "sku": {
                    "uri": "/products/DG7GMGF0DVT7/skus/000C?country=US",
                    "method": "GET",
                    "headers": []
                },
                "availability": {
                    "uri": "/products/DG7GMGF0DVT7/skus/000C/availabilities/DG7GMGF0FVZM?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2019-12-12T17:33:56.1306495Z",
    "status": "completed",
    "transactionType": "UserPurchase",
    "links": {
        "self": {
            "uri": "/customers/45411344-b09d-47e7-9653-542006bf9766/orders/2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
            "method": "GET",
            "headers": []
        },
        "provisioningStatus": {
            "uri": "/customers/45411344-b09d-47e7-9653-542006bf9766/orders/2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1/provisioningstatus",
            "method": "GET",
            "headers": []
        },
        "patchOperation": {
            "uri": "/customers/45411344-b09d-47e7-9653-542006bf9766/orders/2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
            "method": "PATCH",
            "headers": []
        }
    },
    "client": {
        "marketplaceCountry": "US",
        "deviceFamily": "UniversalStore-PartnerCenter",
        "name": "Partner Center API"
    },
    "attributes": {
        "objectType": "Order"
    }
}
```
