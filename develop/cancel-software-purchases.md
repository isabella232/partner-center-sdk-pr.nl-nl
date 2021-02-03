---
title: Softwareaankopen annuleren
description: U kunt kiezen voor het annuleren van software-abonnementen en aankopen met een permanente software met behulp van partner Center-Api's.
ms.date: 12/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 25fd10a171fa6ca01f3442d49145443f2382cc18
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767370"
---
# <a name="cancel-software-purchases"></a><span data-ttu-id="1a83d-103">Softwareaankopen annuleren</span><span class="sxs-lookup"><span data-stu-id="1a83d-103">Cancel software purchases</span></span>

<span data-ttu-id="1a83d-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="1a83d-104">**Applies to:**</span></span>

- <span data-ttu-id="1a83d-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="1a83d-105">Partner Center</span></span>

<span data-ttu-id="1a83d-106">U kunt de Api's van het partner centrum gebruiken om software-abonnementen en aankopen met een permanente software te annuleren (zolang de aankopen zijn gedaan in het annulerings venster vanaf de aankoop datum).</span><span class="sxs-lookup"><span data-stu-id="1a83d-106">You can use the Partner Center APIs to cancel software subscriptions and perpetual software purchases (as long as those purchases were made within the cancellation window from the purchase date).</span></span> <span data-ttu-id="1a83d-107">U hoeft geen ondersteunings ticket te maken om dergelijke annuleringen te maken en u kunt in plaats daarvan de volgende self-service methoden gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1a83d-107">You don't need to create a support ticket to make such cancellations, and can use the following self-service methods instead.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1a83d-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1a83d-108">Prerequisites</span></span>

- <span data-ttu-id="1a83d-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1a83d-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1a83d-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="1a83d-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="1a83d-111">C\#</span><span class="sxs-lookup"><span data-stu-id="1a83d-111">C\#</span></span>

<span data-ttu-id="1a83d-112">Als u een software order wilt annuleren,</span><span class="sxs-lookup"><span data-stu-id="1a83d-112">To cancel a software order,</span></span>

1. <span data-ttu-id="1a83d-113">Geef uw account referenties door aan de [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) -methode om een [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) -interface te verkrijgen om partner bewerkingen te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="1a83d-113">Pass your account credentials to the [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) method to get an [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) interface to get partner operations.</span></span>

2. <span data-ttu-id="1a83d-114">Selecteer een bepaalde [order](order-resources.md#order) die u wilt annuleren.</span><span class="sxs-lookup"><span data-stu-id="1a83d-114">Select a particular [Order](order-resources.md#order) you wish to cancel.</span></span> <span data-ttu-id="1a83d-115">Roep de methode [**klanten. ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id, gevolgd door **Orders. ById ()** met Order-id.</span><span class="sxs-lookup"><span data-stu-id="1a83d-115">Call the [**Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier, followed by **Orders.ById()** with order identifier.</span></span>

3. <span data-ttu-id="1a83d-116">Roep de methode **Get** of **GetAsync** aan om de volg orde op te halen.</span><span class="sxs-lookup"><span data-stu-id="1a83d-116">Call the **Get** or **GetAsync** method to retrieve the order.</span></span>

4. <span data-ttu-id="1a83d-117">Stel de eigenschap [**order. status**](order-resources.md#order) in op `cancelled` .</span><span class="sxs-lookup"><span data-stu-id="1a83d-117">Set the [**Order.Status**](order-resources.md#order) property to `cancelled`.</span></span>

5. <span data-ttu-id="1a83d-118">Beschrijving Als u bepaalde regel items voor annulering wilt opgeven, stelt u de [**order. regel items**](order-resources.md#order) in op een lijst met regel items die u wilt annuleren.</span><span class="sxs-lookup"><span data-stu-id="1a83d-118">(Optional) If you want to specify certain line items for cancellation, set the [**Order.LineItems**](order-resources.md#order) to list of line items that you want to cancel.</span></span>

6. <span data-ttu-id="1a83d-119">Gebruik de methode **patch ()** om de volg orde bij te werken.</span><span class="sxs-lookup"><span data-stu-id="1a83d-119">Use the **Patch()** method to update the order.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="1a83d-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="1a83d-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1a83d-121">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1a83d-121">Request syntax</span></span>

| <span data-ttu-id="1a83d-122">Methode</span><span class="sxs-lookup"><span data-stu-id="1a83d-122">Method</span></span>     | <span data-ttu-id="1a83d-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="1a83d-123">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="1a83d-124">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="1a83d-124">**PATCH**</span></span> | <span data-ttu-id="1a83d-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/orders/{order-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="1a83d-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="1a83d-126">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="1a83d-126">URI parameters</span></span>

<span data-ttu-id="1a83d-127">Gebruik de volgende query parameters om een klant te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="1a83d-127">Use the following query parameters to delete a customer.</span></span>

| <span data-ttu-id="1a83d-128">Naam</span><span class="sxs-lookup"><span data-stu-id="1a83d-128">Name</span></span>                   | <span data-ttu-id="1a83d-129">Type</span><span class="sxs-lookup"><span data-stu-id="1a83d-129">Type</span></span>     | <span data-ttu-id="1a83d-130">Vereist</span><span class="sxs-lookup"><span data-stu-id="1a83d-130">Required</span></span> | <span data-ttu-id="1a83d-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1a83d-131">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1a83d-132">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="1a83d-132">**customer-tenant-id**</span></span> | <span data-ttu-id="1a83d-133">**guid**</span><span class="sxs-lookup"><span data-stu-id="1a83d-133">**guid**</span></span> | <span data-ttu-id="1a83d-134">J</span><span class="sxs-lookup"><span data-stu-id="1a83d-134">Y</span></span>        | <span data-ttu-id="1a83d-135">De waarde is een id voor de identiteit van een klant die de wederverkoper toestaat de resultaten te filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="1a83d-135">The value is a GUID formatted customer tenant identifier that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="1a83d-136">**order-id**</span><span class="sxs-lookup"><span data-stu-id="1a83d-136">**order-id**</span></span> | <span data-ttu-id="1a83d-137">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="1a83d-137">**string**</span></span> | <span data-ttu-id="1a83d-138">J</span><span class="sxs-lookup"><span data-stu-id="1a83d-138">Y</span></span>        | <span data-ttu-id="1a83d-139">De waarde is een teken reeks waarmee de id wordt aangegeven van de order die u wilt annuleren.</span><span class="sxs-lookup"><span data-stu-id="1a83d-139">The value is a string that denotes the identifier of the order that you want to cancel.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="1a83d-140">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="1a83d-140">Request headers</span></span>

<span data-ttu-id="1a83d-141">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="1a83d-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1a83d-142">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="1a83d-142">Request body</span></span>

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

### <a name="request-example"></a><span data-ttu-id="1a83d-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1a83d-143">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="1a83d-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="1a83d-144">REST response</span></span>

<span data-ttu-id="1a83d-145">Als deze methode is geslaagd, wordt de volg orde met Geannuleerde regel items geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1a83d-145">If successful, this method returns the order with canceled line items.</span></span>

<span data-ttu-id="1a83d-146">De status van de bestelling wordt gemarkeerd als **geannuleerd** als alle regel items in de order worden geannuleerd of worden **voltooid** als niet alle regel items in de order worden geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="1a83d-146">The order status will be marked as either **cancelled** if all the line items in the order are cancelled, or **completed** if not all line items in the order are canceled.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1a83d-147">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="1a83d-147">Response success and error codes</span></span>

<span data-ttu-id="1a83d-148">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="1a83d-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1a83d-149">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="1a83d-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1a83d-150">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="1a83d-150">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="1a83d-151">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="1a83d-151">Response example</span></span>

<span data-ttu-id="1a83d-152">In het volgende voor beeld kunt u zien dat de hoeveelheid van het regel item met de aanbiedings-id **`DG7GMGF0FKZV:0003:DG7GMGF0DWMS`** nul (0) is geworden.</span><span class="sxs-lookup"><span data-stu-id="1a83d-152">In the following example response, you can see that the quantity of line item with the offer identifier **`DG7GMGF0FKZV:0003:DG7GMGF0DWMS`** has become zero (0).</span></span> <span data-ttu-id="1a83d-153">Deze wijziging betekent dat het regel item dat is gemarkeerd voor annulering, is geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="1a83d-153">This change means that the line item that was marked for cancellation has been canceled successfully.</span></span> <span data-ttu-id="1a83d-154">De voorbeeld volgorde bevat andere regel items die niet zijn geannuleerd. Dit betekent dat de status van de algemene order wordt gemarkeerd als **voltooid**, en niet wordt **geannuleerd**.</span><span class="sxs-lookup"><span data-stu-id="1a83d-154">The example order contains other line items that weren't canceled, which means that the status of the overall order will be marked as **completed**, not **cancelled**.</span></span>

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
