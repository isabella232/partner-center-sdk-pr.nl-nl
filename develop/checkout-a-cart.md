---
title: Een winkelwagen afhandelen
description: Meer informatie over het controleren van een bestelling voor een klant in een mandje met behulp van partner Center-Api's. U kunt dit doen om een klant order te volt ooien.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 094817a34cd29bc96788fcfb6a16610a8192d784
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2020
ms.locfileid: "97767621"
---
# <a name="checkout-an-order-for-a-customer-in-a-cart"></a><span data-ttu-id="3ce32-104">Een bestelling voor een klant in een mandje afhandelen</span><span class="sxs-lookup"><span data-stu-id="3ce32-104">Checkout an order for a customer in a cart</span></span>

<span data-ttu-id="3ce32-105">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="3ce32-105">**Applies to:**</span></span>

- <span data-ttu-id="3ce32-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="3ce32-106">Partner Center</span></span>
- <span data-ttu-id="3ce32-107">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="3ce32-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="3ce32-108">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="3ce32-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="3ce32-109">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="3ce32-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="3ce32-110">Het afhandelen van een bestelling voor een klant in een winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="3ce32-110">How to checkout an order for a customer in a cart.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3ce32-111">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3ce32-111">Prerequisites</span></span>

- <span data-ttu-id="3ce32-112">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3ce32-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="3ce32-113">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="3ce32-113">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="3ce32-114">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3ce32-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="3ce32-115">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="3ce32-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="3ce32-116">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="3ce32-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="3ce32-117">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="3ce32-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="3ce32-118">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="3ce32-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="3ce32-119">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3ce32-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="3ce32-120">Een winkel wagen-ID voor een bestaande winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="3ce32-120">A Cart ID for an existing cart.</span></span>

## <a name="c"></a><span data-ttu-id="3ce32-121">C\#</span><span class="sxs-lookup"><span data-stu-id="3ce32-121">C\#</span></span>

<span data-ttu-id="3ce32-122">Als u een bestelling wilt afhandelen voor een klant, kunt u een verwijzing naar de winkel wagen ophalen met behulp van het wagentje en de klant-id.</span><span class="sxs-lookup"><span data-stu-id="3ce32-122">To checkout an order for a customer, get a reference to the cart using the cart and customer identifier.</span></span> <span data-ttu-id="3ce32-123">Roep tot slot de functies **Create** of **CreateAsync** aan om de volg orde te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="3ce32-123">Finally, call the **Create** or **CreateAsync** functions to complete the order.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string cartId;

var cart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Checkout();
```

## <a name="java"></a><span data-ttu-id="3ce32-124">Java</span><span class="sxs-lookup"><span data-stu-id="3ce32-124">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](<../includes/java-sdk-support.md>)]

<span data-ttu-id="3ce32-125">Als u een bestelling wilt afhandelen voor een klant, kunt u een verwijzing naar de winkel wagen ophalen met behulp van het wagentje en de klant-id.</span><span class="sxs-lookup"><span data-stu-id="3ce32-125">To checkout an order for a customer, get a reference to the cart using the cart and customer identifier.</span></span> <span data-ttu-id="3ce32-126">Roep ten slotte de functie **maken** aan om de volg orde te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="3ce32-126">Finally, call the **create** function to complete the order.</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String cartId;

Cart cart = partnerOperations.getCustomers().byId(customerId).getCart().byId(cartId).checkout();
```

## <a name="powershell"></a><span data-ttu-id="3ce32-127">PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ce32-127">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](<../includes/powershell-module-support.md>)]

<span data-ttu-id="3ce32-128">Als u een bestelling voor een klant wilt afhandelen, voert u de opdracht [**Submit-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Submit-PartnerCustomerCart.md) uit om de order te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="3ce32-128">To checkout an order for a customer, execute the [**Submit-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Submit-PartnerCustomerCart.md) to complete the order.</span></span>

```powershell
# $customerId
# $cartId

Submit-PartnerCustomerCart -CartId $cartId -CustomerId $customerId
```

## <a name="rest-request"></a><span data-ttu-id="3ce32-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="3ce32-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3ce32-130">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3ce32-130">Request syntax</span></span>

| <span data-ttu-id="3ce32-131">Methode</span><span class="sxs-lookup"><span data-stu-id="3ce32-131">Method</span></span>   | <span data-ttu-id="3ce32-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="3ce32-132">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3ce32-133">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="3ce32-133">**POST**</span></span> | <span data-ttu-id="3ce32-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Carts/{Cart-id}/checkout http/1.1</span><span class="sxs-lookup"><span data-stu-id="3ce32-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts/{cart-id}/checkout HTTP/1.1</span></span>     |

### <a name="uri-parameters"></a><span data-ttu-id="3ce32-135">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="3ce32-135">URI parameters</span></span>

<span data-ttu-id="3ce32-136">Gebruik de volgende para meters om de klant te identificeren en de winkel wagen op te geven die moet worden uitgecheckt.</span><span class="sxs-lookup"><span data-stu-id="3ce32-136">Use the following path parameters to identify the customer and specify the cart to be checked out.</span></span>

| <span data-ttu-id="3ce32-137">Naam</span><span class="sxs-lookup"><span data-stu-id="3ce32-137">Name</span></span>            | <span data-ttu-id="3ce32-138">Type</span><span class="sxs-lookup"><span data-stu-id="3ce32-138">Type</span></span>     | <span data-ttu-id="3ce32-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="3ce32-139">Required</span></span> | <span data-ttu-id="3ce32-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3ce32-140">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="3ce32-141">**klant-id**</span><span class="sxs-lookup"><span data-stu-id="3ce32-141">**customer-id**</span></span> | <span data-ttu-id="3ce32-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3ce32-142">string</span></span>   | <span data-ttu-id="3ce32-143">Yes</span><span class="sxs-lookup"><span data-stu-id="3ce32-143">Yes</span></span>      | <span data-ttu-id="3ce32-144">Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="3ce32-144">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="3ce32-145">**Winkel wagen-id**</span><span class="sxs-lookup"><span data-stu-id="3ce32-145">**cart-id**</span></span>     | <span data-ttu-id="3ce32-146">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3ce32-146">string</span></span>   | <span data-ttu-id="3ce32-147">Yes</span><span class="sxs-lookup"><span data-stu-id="3ce32-147">Yes</span></span>      | <span data-ttu-id="3ce32-148">Een door de GUID ingedeelde winkel wagen-id waarmee de winkel wagen wordt aangeduid.</span><span class="sxs-lookup"><span data-stu-id="3ce32-148">A GUID formatted cart-id that identifies the cart.</span></span>                     |

### <a name="request-headers"></a><span data-ttu-id="3ce32-149">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="3ce32-149">Request headers</span></span>

<span data-ttu-id="3ce32-150">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="3ce32-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3ce32-151">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="3ce32-151">Request body</span></span>

<span data-ttu-id="3ce32-152">Geen.</span><span class="sxs-lookup"><span data-stu-id="3ce32-152">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="3ce32-153">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3ce32-153">Request example</span></span>

```http
POST /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts/b4c8fdea-cbe4-4d17-9576-13fcacbf9605/checkout HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 0
Expect: 100-continue

No-Content-Body
```

## <a name="rest-response"></a><span data-ttu-id="3ce32-154">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="3ce32-154">REST response</span></span>

<span data-ttu-id="3ce32-155">Als dit lukt, bevat de antwoord tekst de gevulde [CartCheckoutResult](cart-resources.md#cartcheckoutresult) -resource.</span><span class="sxs-lookup"><span data-stu-id="3ce32-155">If successful, the response body contains the populated [CartCheckoutResult](cart-resources.md#cartcheckoutresult) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3ce32-156">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="3ce32-156">Response success and error codes</span></span>

<span data-ttu-id="3ce32-157">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="3ce32-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="3ce32-158">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="3ce32-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3ce32-159">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="3ce32-159">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="3ce32-160">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="3ce32-160">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 764
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
X-Locale: en-US,en-US
MS-CV: sF/wRa2ih0CzbABc.0
MS-ServerId: 000001
Date: Thu, 15 Mar 2018 17:15:01 GMT
?{
  "orders": [
    {
      "id": "3c6f2530-1e31-4088-8230-dd1c31a18bce",
      "alternateId": "3c6f2530-1e31-4088-8230-dd1c31a18bce",
      "referenceCustomerId": "28045616-f6b9-462f-9701-0d89b5e65c44",
      "billingCycle": "monthly",
      "currencyCode": "USD",
      "lineItems": [
        {
          "lineItemNumber": 0,
          "offerId": "MS-AZR-0145P",
          "subscriptionId": "EF2E1307-86E6-40E3-A794-872403FBD31C",
          "termDuration": "P1Y",
          "transactionType": "New",
          "friendlyName": "Microsoft Azure",
          "quantity": 1,
          "links": {...}
        }
      ],
      "creationDate": "2019-01-16T00:48:44.76+00:00",
      "status": "completed",
      "transactionType": "UserPurchase",
      "links": {...},
      ...
    },
    {
      "id": "311qiN8iFwkv-XARWMvXRYAwYKMACVqv1",
      "alternateId": "0a3624c6e47d",
      "referenceCustomerId": "28045616-f6b9-462f-9701-0d89b5e65c44",
      "billingCycle": "one_time",
      "currencyCode": "USD",
      "currencySymbol": "$",
      "lineItems": [
        {
          "lineItemNumber": 0,
          "offerId": "DZH318Z0BQ36:004G:DZH318Z08C0S",
          "termDuration": "P1Y",
          "transactionType": "New",
          "friendlyName": "Reserved VM Instance, Standard_NV12, US East 2, 1 Year",
          "quantity": 1,
          "links": {...}
        },
        {
          "lineItemNumber": 1,
          "offerId": "DZH318Z0BQ36:004J:DZH318Z08B8X",
          "termDuration": "P3Y",
          "transactionType": "New",
          "friendlyName": "Reserved VM Instance, Standard_NV12, US East 2, 3 Years",
          "quantity": 1,
          "links": {...}
        },
        {
          "lineItemNumber": 2,
          "offerId": "DG7GMGF0DWM3:0002:DG7GMGF0DT1M",
          "transactionType": "New",
          "friendlyName": "BizTalk Server 2016 Branch",
          "quantity": 1,
          "links": {...}
        }
      ],
      "creationDate": "2019-01-16T00:48:51.6578126Z",
      "status": "pending",
      "transactionType": "UserPurchase",
      "links": {...},
      ...
    },
    {
      "id": "HVu_cO8Ea7fNRQP4ia1QTpZap-kg_7P71",
      "alternateId": "55a4e6854d54",
      "referenceCustomerId": "28045616-f6b9-462f-9701-0d89b5e65c44",
      "billingCycle": "monthly",
      "currencyCode": "USD",
      "currencySymbol": "$",
      "lineItems": [
        {
          "lineItemNumber": 0,
          "offerId": "DZH318Z0BXWC:0002:DZH318Z0BMRV",
          "termDuration": "P1M",
          "transactionType": "New",
          "friendlyName": "Barracuda WaaS - Medium Plan",
          "quantity": 1,
          "links": {...}
        }
      ],
      "creationDate": "2019-01-16T00:48:44.4514129Z",
      "status": "pending",
      "transactionType": "UserPurchase",
      "links": {...},
      ...
    }
  ],
  ...
}
```
