---
title: Activeringskoppeling ophalen op basis van bestellingsregelitem
description: Hiermee wordt een koppeling voor het activeren van een abonnement opgehaald per order regel item.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: c0e84888870571cf6bd21306f527863f2aa7ee85
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767350"
---
# <a name="get-activation-link-by-order-line-item"></a><span data-ttu-id="00d3e-103">Activeringskoppeling ophalen op basis van bestellingsregelitem</span><span class="sxs-lookup"><span data-stu-id="00d3e-103">Get activation link by order line item</span></span>

<span data-ttu-id="00d3e-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="00d3e-104">**Applies To**</span></span>

- <span data-ttu-id="00d3e-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="00d3e-105">Partner Center</span></span>
- <span data-ttu-id="00d3e-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="00d3e-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="00d3e-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="00d3e-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="00d3e-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="00d3e-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="00d3e-109">Hiermee wordt een activerings koppeling voor een commercieel Marketplace-abonnement opgehaald door het artikel nummer van de order regel.</span><span class="sxs-lookup"><span data-stu-id="00d3e-109">Gets a commercial marketplace subscription activation link by the order line item number.</span></span>

<span data-ttu-id="00d3e-110">In het dash board van de Partner Center kunt u deze bewerking uitvoeren door een **specifiek abonnement** te selecteren onder **abonnement** op de hoofd pagina of door de **site koppeling go to Publisher** naast het abonnement te selecteren om te activeren op de pagina **abonnementen** .</span><span class="sxs-lookup"><span data-stu-id="00d3e-110">In the Partner Center dashboard, you can do this operation by selecting either a **Specific Subscription** under **Subscription** on the main page, or selecting the **Go to Publisher's site** link next to the subscription to activate on the **Subscriptions** page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="00d3e-111">Vereisten</span><span class="sxs-lookup"><span data-stu-id="00d3e-111">Prerequisites</span></span>

- <span data-ttu-id="00d3e-112">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="00d3e-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="00d3e-113">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="00d3e-113">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="00d3e-114">Voltooide bestelling met een product dat moet worden geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="00d3e-114">Completed order with product that needs activation.</span></span>

## <a name="c"></a><span data-ttu-id="00d3e-115">C\#</span><span class="sxs-lookup"><span data-stu-id="00d3e-115">C\#</span></span>

<span data-ttu-id="00d3e-116">Als u de activerings koppeling van een regel item wilt ophalen, gebruikt u de verzameling [**IAggregatePartner. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) en roept u de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de geselecteerde klant-id.</span><span class="sxs-lookup"><span data-stu-id="00d3e-116">To get a line item's activation link, use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the selected customer ID.</span></span> <span data-ttu-id="00d3e-117">Roep vervolgens de eigenschap [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) en de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) aan met de opgegeven  [**OrderID**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.id).</span><span class="sxs-lookup"><span data-stu-id="00d3e-117">Then call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property and the [**ById()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) method with your specified  [**OrderId**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.id).</span></span> <span data-ttu-id="00d3e-118">Roep vervolgens de [**regel items**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) aan met de methode **ById ()** met de id van het regel item nummer.</span><span class="sxs-lookup"><span data-stu-id="00d3e-118">Then, call the [**LineItems**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) with **ById()** method with the line item number identifier.</span></span>  <span data-ttu-id="00d3e-119">Roep ten slotte de methode **ActivationLinks ()** aan.</span><span class="sxs-lookup"><span data-stu-id="00d3e-119">Finally, call the **ActivationLinks()** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string orderId;
// string lineItemNumber

// get the activation link for the specific line item
var partnerOperations.Customers.ById(customerId).Orders.ById(orderId).OrderLineItems.ById(lineItemNumber).ActivationLinks();
```

## <a name="rest-request"></a><span data-ttu-id="00d3e-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="00d3e-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="00d3e-121">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="00d3e-121">Request syntax</span></span>

| <span data-ttu-id="00d3e-122">Methode</span><span class="sxs-lookup"><span data-stu-id="00d3e-122">Method</span></span>  | <span data-ttu-id="00d3e-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="00d3e-123">Request URI</span></span>                                                                                                                               |
|---------|-------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="00d3e-124">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="00d3e-124">**GET**</span></span> | <span data-ttu-id="00d3e-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{customerId}/orders/{orderId}/lineitems/{lineItemNumber}/activationlinks http/1.1</span><span class="sxs-lookup"><span data-stu-id="00d3e-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customerId}/orders/{orderId}/lineitems/{lineItemNumber}/activationlinks HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="00d3e-126">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="00d3e-126">Request headers</span></span>

<span data-ttu-id="00d3e-127">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="00d3e-127">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="00d3e-128">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="00d3e-128">Request body</span></span>

<span data-ttu-id="00d3e-129">Geen.</span><span class="sxs-lookup"><span data-stu-id="00d3e-129">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="00d3e-130">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="00d3e-130">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/8c5b65fd-c725-4f50-8d9c-97ec9169fdd0/orders/03fb46b3-bf8c-49aa-b908-ca2e93bcc04a/lineitems/0/activationlinks HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
```

## <a name="rest-response"></a><span data-ttu-id="00d3e-131">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="00d3e-131">REST response</span></span>

<span data-ttu-id="00d3e-132">Als dit lukt, retourneert deze methode een verzameling [klant](customer-resources.md#customer) resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="00d3e-132">If successful, this method returns a collection of [Customer](customer-resources.md#customer) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="00d3e-133">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="00d3e-133">Response success and error codes</span></span>

<span data-ttu-id="00d3e-134">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="00d3e-134">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="00d3e-135">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="00d3e-135">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="00d3e-136">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="00d3e-136">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="00d3e-137">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="00d3e-137">Response example</span></span>

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
