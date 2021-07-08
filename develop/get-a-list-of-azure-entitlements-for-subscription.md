---
title: Een lijst met Azure-rechten voor een abonnement ophalen
description: U kunt de resource AzureEntitlement gebruiken om een verzameling Azure-rechtenresources op te halen die deel uitmaken van een abonnement.
ms.date: 07/06/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 280da155122ed9efd99838d7819fb34f8f7ec52c
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874360"
---
# <a name="get-a-list-of-azure-entitlements-for-a-subscription"></a><span data-ttu-id="73d87-103">Een lijst met Azure-rechten voor een abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="73d87-103">Get a list of Azure entitlements for a subscription</span></span>

<span data-ttu-id="73d87-104">U kunt de [Azure-rechtenresource](subscription-resources.md#azureentitlement) **(AzureEntitlement)** gebruiken om een verzameling resources op te halen die deel uitmaken van een abonnement.</span><span class="sxs-lookup"><span data-stu-id="73d87-104">You can use the [Azure entitlement resource](subscription-resources.md#azureentitlement) (**AzureEntitlement**) to get a collection of resources that belong to a subscription.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="73d87-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="73d87-105">Prerequisites</span></span>

- <span data-ttu-id="73d87-106">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="73d87-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="73d87-107">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="73d87-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="73d87-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="73d87-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="73d87-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="73d87-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="73d87-110">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="73d87-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="73d87-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="73d87-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="73d87-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="73d87-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="73d87-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="73d87-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="73d87-114">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="73d87-114">A subscription identifier.</span></span>

## <a name="rest-request"></a><span data-ttu-id="73d87-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="73d87-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="73d87-116">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="73d87-116">Request syntax</span></span>

| <span data-ttu-id="73d87-117">Methode</span><span class="sxs-lookup"><span data-stu-id="73d87-117">Method</span></span>  | <span data-ttu-id="73d87-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="73d87-118">Request URI</span></span>                                                                                                                   |
|---------|---------------------------------------------------------------------------------|
| <span data-ttu-id="73d87-119">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="73d87-119">**GET**</span></span> | <span data-ttu-id="73d87-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/azureentitlements HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="73d87-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/azureentitlements HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="73d87-121">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="73d87-121">URI parameters</span></span>

<span data-ttu-id="73d87-122">De volgende tabel bevat de vereiste queryparameters om alle Azure-rechten voor een abonnement op te halen.</span><span class="sxs-lookup"><span data-stu-id="73d87-122">The following table lists the required query parameters to get all the Azure entitlements for a subscription.</span></span>

| <span data-ttu-id="73d87-123">Naam</span><span class="sxs-lookup"><span data-stu-id="73d87-123">Name</span></span>                   | <span data-ttu-id="73d87-124">Type</span><span class="sxs-lookup"><span data-stu-id="73d87-124">Type</span></span>     | <span data-ttu-id="73d87-125">Vereist</span><span class="sxs-lookup"><span data-stu-id="73d87-125">Required</span></span> | <span data-ttu-id="73d87-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="73d87-126">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="73d87-127">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="73d87-127">**customer-tenant-id**</span></span> | <span data-ttu-id="73d87-128">**guid**</span><span class="sxs-lookup"><span data-stu-id="73d87-128">**guid**</span></span> | <span data-ttu-id="73d87-129">J</span><span class="sxs-lookup"><span data-stu-id="73d87-129">Y</span></span>        | <span data-ttu-id="73d87-130">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="73d87-130">A GUID corresponding to the customer.</span></span> |
| <span data-ttu-id="73d87-131">**subscription-id**</span><span class="sxs-lookup"><span data-stu-id="73d87-131">**subscription-id**</span></span>       | <span data-ttu-id="73d87-132">**guid**</span><span class="sxs-lookup"><span data-stu-id="73d87-132">**guid**</span></span> | <span data-ttu-id="73d87-133">J</span><span class="sxs-lookup"><span data-stu-id="73d87-133">Y</span></span>        | <span data-ttu-id="73d87-134">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="73d87-134">A GUID corresponding to the subscription.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="73d87-135">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="73d87-135">Request headers</span></span>

<span data-ttu-id="73d87-136">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="73d87-136">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="73d87-137">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="73d87-137">Request body</span></span>

<span data-ttu-id="73d87-138">Geen.</span><span class="sxs-lookup"><span data-stu-id="73d87-138">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="73d87-139">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="73d87-139">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/11f9bc2a-1f38-431c-a0b0-9455c6f5bbc0/subscriptions/3f15978e-005c-b763-bb78-2a8fab289c58/azureEntitlements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 16fee928-dc2c-412f-adbb-871f68babf16
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="73d87-140">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="73d87-140">REST response</span></span>

<span data-ttu-id="73d87-141">Als dit lukt, retourneert deze methode een verzameling [**AzureEntitlement-resources**](subscription-resources.md#azureentitlement) in de antwoordhoofd body.</span><span class="sxs-lookup"><span data-stu-id="73d87-141">If successful, this method returns a collection of [**AzureEntitlement**](subscription-resources.md#azureentitlement) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="73d87-142">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="73d87-142">Response success and error codes</span></span>

<span data-ttu-id="73d87-143">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="73d87-143">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="73d87-144">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="73d87-144">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="73d87-145">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="73d87-145">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="73d87-146">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="73d87-146">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 73754
Content-Type: application/json
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
MS-RequestId: 16fee928-dc2c-412f-adbb-871f68babf16
Date: Wed, 04 Oct 2019 05:50:45 GMT

{
"totalCount":1,
"items":[
  {
    "id":"899ae6f1-8a74-4d5e-b6c6-e6b5019bbff8",
    "friendlyName":"Microsoft Azure",
    "status":"active",
    "subscriptionId":"3f15978e-005c-b763-bb78-2a8fab289c58"
   }],
    "attributes":{"objectType":"Collection"}
  }
```
