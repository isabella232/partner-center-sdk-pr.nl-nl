---
title: Een lijst met Azure-rechten voor een abonnement ophalen
description: U kunt de AzureEntitlement-Resource gebruiken om een verzameling van Azure-rechten resources te verkrijgen die tot een abonnement behoren.
ms.date: 07/06/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: d7d0a10c571dc073bd49e82084f3b7ece7234daf
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767300"
---
# <a name="get-a-list-of-azure-entitlements-for-a-subscription"></a><span data-ttu-id="596d1-103">Een lijst met Azure-rechten voor een abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="596d1-103">Get a list of Azure entitlements for a subscription</span></span>

<span data-ttu-id="596d1-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="596d1-104">**Applies to:**</span></span>

- <span data-ttu-id="596d1-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="596d1-105">Partner Center</span></span>

<span data-ttu-id="596d1-106">U kunt de [Azure-resource](subscription-resources.md#azureentitlement) (**AzureEntitlement**) gebruiken voor het ophalen van een verzameling resources die deel uitmaken van een abonnement.</span><span class="sxs-lookup"><span data-stu-id="596d1-106">You can use the [Azure entitlement resource](subscription-resources.md#azureentitlement) (**AzureEntitlement**) to get a collection of resources that belong to a subscription.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="596d1-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="596d1-107">Prerequisites</span></span>

- <span data-ttu-id="596d1-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="596d1-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="596d1-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="596d1-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="596d1-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="596d1-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="596d1-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="596d1-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="596d1-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="596d1-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="596d1-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="596d1-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="596d1-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="596d1-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="596d1-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="596d1-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="596d1-116">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="596d1-116">A subscription identifier.</span></span>

## <a name="rest-request"></a><span data-ttu-id="596d1-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="596d1-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="596d1-118">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="596d1-118">Request syntax</span></span>

| <span data-ttu-id="596d1-119">Methode</span><span class="sxs-lookup"><span data-stu-id="596d1-119">Method</span></span>  | <span data-ttu-id="596d1-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="596d1-120">Request URI</span></span>                                                                                                                   |
|---------|---------------------------------------------------------------------------------|
| <span data-ttu-id="596d1-121">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="596d1-121">**GET**</span></span> | <span data-ttu-id="596d1-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{Subscription-id}/azureentitlements http/1.1</span><span class="sxs-lookup"><span data-stu-id="596d1-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/azureentitlements HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="596d1-123">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="596d1-123">URI parameters</span></span>

<span data-ttu-id="596d1-124">De volgende tabel bevat de vereiste query parameters om alle Azure-rechten voor een abonnement te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="596d1-124">The following table lists the required query parameters to get all the Azure entitlements for a subscription.</span></span>

| <span data-ttu-id="596d1-125">Naam</span><span class="sxs-lookup"><span data-stu-id="596d1-125">Name</span></span>                   | <span data-ttu-id="596d1-126">Type</span><span class="sxs-lookup"><span data-stu-id="596d1-126">Type</span></span>     | <span data-ttu-id="596d1-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="596d1-127">Required</span></span> | <span data-ttu-id="596d1-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="596d1-128">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="596d1-129">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="596d1-129">**customer-tenant-id**</span></span> | <span data-ttu-id="596d1-130">**guid**</span><span class="sxs-lookup"><span data-stu-id="596d1-130">**guid**</span></span> | <span data-ttu-id="596d1-131">J</span><span class="sxs-lookup"><span data-stu-id="596d1-131">Y</span></span>        | <span data-ttu-id="596d1-132">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="596d1-132">A GUID corresponding to the customer.</span></span> |
| <span data-ttu-id="596d1-133">**abonnement-id**</span><span class="sxs-lookup"><span data-stu-id="596d1-133">**subscription-id**</span></span>       | <span data-ttu-id="596d1-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="596d1-134">**guid**</span></span> | <span data-ttu-id="596d1-135">J</span><span class="sxs-lookup"><span data-stu-id="596d1-135">Y</span></span>        | <span data-ttu-id="596d1-136">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="596d1-136">A GUID corresponding to the subscription.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="596d1-137">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="596d1-137">Request headers</span></span>

<span data-ttu-id="596d1-138">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="596d1-138">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="596d1-139">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="596d1-139">Request body</span></span>

<span data-ttu-id="596d1-140">Geen.</span><span class="sxs-lookup"><span data-stu-id="596d1-140">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="596d1-141">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="596d1-141">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/11f9bc2a-1f38-431c-a0b0-9455c6f5bbc0/subscriptions/3f15978e-005c-b763-bb78-2a8fab289c58/azureEntitlements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 16fee928-dc2c-412f-adbb-871f68babf16
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="596d1-142">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="596d1-142">REST response</span></span>

<span data-ttu-id="596d1-143">Als dit lukt, retourneert deze methode een verzameling [**AzureEntitlement**](subscription-resources.md#azureentitlement) -resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="596d1-143">If successful, this method returns a collection of [**AzureEntitlement**](subscription-resources.md#azureentitlement) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="596d1-144">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="596d1-144">Response success and error codes</span></span>

<span data-ttu-id="596d1-145">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="596d1-145">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="596d1-146">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="596d1-146">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="596d1-147">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="596d1-147">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="596d1-148">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="596d1-148">Response example</span></span>

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
