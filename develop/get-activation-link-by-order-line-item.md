---
title: Activeringskoppeling ophalen op basis van bestellingsregelitem
description: Haalt een abonnementsactiveringskoppeling op op orderregelitem.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: aa02a5a5b4a281b96e32ee6d239cc440cf8af4ec
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760773"
---
# <a name="get-activation-link-by-order-line-item"></a><span data-ttu-id="7f157-103">Activeringskoppeling ophalen op basis van bestellingsregelitem</span><span class="sxs-lookup"><span data-stu-id="7f157-103">Get activation link by order line item</span></span>

<span data-ttu-id="7f157-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="7f157-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="7f157-105">Haalt een commerciële marketplace-abonnementsactiveringskoppeling op op basis van het orderregelitemnummer.</span><span class="sxs-lookup"><span data-stu-id="7f157-105">Gets a commercial marketplace subscription activation link by the order line item number.</span></span>

<span data-ttu-id="7f157-106">In het Partner Center-dashboard kunt u deze bewerking uitvoeren  door een Specifiek abonnement te selecteren onder Abonnement op de hoofdpagina of door de  koppeling Naar de site van **Publisher** te gaan naast het abonnement dat u wilt activeren op de pagina Abonnementen. </span><span class="sxs-lookup"><span data-stu-id="7f157-106">In the Partner Center dashboard, you can do this operation by selecting either a **Specific Subscription** under **Subscription** on the main page, or selecting the **Go to Publisher's site** link next to the subscription to activate on the **Subscriptions** page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7f157-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7f157-107">Prerequisites</span></span>

- <span data-ttu-id="7f157-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7f157-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7f157-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="7f157-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="7f157-110">Voltooide bestelling met product dat moet worden geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="7f157-110">Completed order with product that needs activation.</span></span>

## <a name="c"></a><span data-ttu-id="7f157-111">C\#</span><span class="sxs-lookup"><span data-stu-id="7f157-111">C\#</span></span>

<span data-ttu-id="7f157-112">Als u de activeringskoppeling van een regelitem wilt ophalen, gebruikt u de verzameling [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) en roept u de [**methode ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de geselecteerde klant-id.</span><span class="sxs-lookup"><span data-stu-id="7f157-112">To get a line item's activation link, use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the selected customer ID.</span></span> <span data-ttu-id="7f157-113">Roep vervolgens de [**eigenschap Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) en de [**methode ById()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) aan met de opgegeven  [**OrderId**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.id).</span><span class="sxs-lookup"><span data-stu-id="7f157-113">Then call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property and the [**ById()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) method with your specified  [**OrderId**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.id).</span></span> <span data-ttu-id="7f157-114">Roep vervolgens de methode [**LineItems met**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) **ById()** aan met de id van het regelitemnummer.</span><span class="sxs-lookup"><span data-stu-id="7f157-114">Then, call the [**LineItems**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) with **ById()** method with the line item number identifier.</span></span>  <span data-ttu-id="7f157-115">Roep ten slotte de **methode ActivationLinks()** aan.</span><span class="sxs-lookup"><span data-stu-id="7f157-115">Finally, call the **ActivationLinks()** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string orderId;
// string lineItemNumber

// get the activation link for the specific line item
var partnerOperations.Customers.ById(customerId).Orders.ById(orderId).OrderLineItems.ById(lineItemNumber).ActivationLinks();
```

## <a name="rest-request"></a><span data-ttu-id="7f157-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="7f157-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7f157-117">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="7f157-117">Request syntax</span></span>

| <span data-ttu-id="7f157-118">Methode</span><span class="sxs-lookup"><span data-stu-id="7f157-118">Method</span></span>  | <span data-ttu-id="7f157-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="7f157-119">Request URI</span></span>                                                                                                                               |
|---------|-------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7f157-120">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7f157-120">**GET**</span></span> | <span data-ttu-id="7f157-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customerId}/orders/{orderId}/lineitems/{lineItemNumber}/activationlinks HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7f157-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customerId}/orders/{orderId}/lineitems/{lineItemNumber}/activationlinks HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="7f157-122">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="7f157-122">Request headers</span></span>

<span data-ttu-id="7f157-123">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="7f157-123">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7f157-124">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="7f157-124">Request body</span></span>

<span data-ttu-id="7f157-125">Geen.</span><span class="sxs-lookup"><span data-stu-id="7f157-125">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="7f157-126">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7f157-126">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/8c5b65fd-c725-4f50-8d9c-97ec9169fdd0/orders/03fb46b3-bf8c-49aa-b908-ca2e93bcc04a/lineitems/0/activationlinks HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
```

## <a name="rest-response"></a><span data-ttu-id="7f157-127">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="7f157-127">REST response</span></span>

<span data-ttu-id="7f157-128">Als dit lukt, retourneert deze methode een verzameling [Klantresources](customer-resources.md#customer) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="7f157-128">If successful, this method returns a collection of [Customer](customer-resources.md#customer) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7f157-129">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="7f157-129">Response success and error codes</span></span>

<span data-ttu-id="7f157-130">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="7f157-130">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7f157-131">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="7f157-131">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7f157-132">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="7f157-132">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="7f157-133">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="7f157-133">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 809
Content-Type: application/json
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
Date: Fri, 20 Nov 2015 01:08:23 GMT
{
  "totalCount": 1,
  "items": [
    {
      "lineItemNumber": 0,
      "link": {
        "uri": "<link populated here>",
        "method": "GET",
        "headers": [

        ]
      }
    }
  ],
  "links": {
    "self": {
      "uri": "/customers/8c5b65fd-c725-4f50-8d9c-97ec9169fdd0/orders/03fb46b3-bf8c-49aa-b908-ca2e93bcc04a/lineitems/0/activationlinks",
      "method": "GET",
      "headers": [

      ]
    }
  },
  "attributes": {
    "objectType": "Collection"
  }
}
```
