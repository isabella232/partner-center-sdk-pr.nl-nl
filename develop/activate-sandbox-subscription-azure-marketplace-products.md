---
title: Een sandbox-abonnement activeren voor commerciële marketplace-producten
description: Meer informatie over het gebruik van C/# en Partner Center REST API's om een sandbox-abonnement te activeren voor commerciële marketplace-producten.
ms.date: 09/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b32c3e87462f58218771fc5da7da56ed177489cb
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025697"
---
# <a name="activate-a-sandbox-subscription-for-commercial-marketplace-saas-products-to-enable-billing"></a><span data-ttu-id="5c651-103">Een sandbox-abonnement activeren voor SaaS-producten op de commerciële marketplace om facturering mogelijk te maken</span><span class="sxs-lookup"><span data-stu-id="5c651-103">Activate a sandbox subscription for commercial marketplace SaaS products to enable billing</span></span>

<span data-ttu-id="5c651-104">Een abonnement activeren voor SaaS-producten (Software as a Service) op de commerciële marketplace vanuit sandbox-accounts voor integratie om facturering mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="5c651-104">How to activate a subscription for commercial marketplace Software as a Service (SaaS) products from integration sandbox accounts to enable billing.</span></span>

> [!NOTE]
> <span data-ttu-id="5c651-105">Het is alleen mogelijk om een abonnement voor SaaS-producten op de commerciële marketplace te activeren vanuit sandbox-accounts voor integratie.</span><span class="sxs-lookup"><span data-stu-id="5c651-105">It's only possible to activate a subscription for commercial marketplace SaaS products from integration sandbox accounts.</span></span> <span data-ttu-id="5c651-106">Als u een productieabonnement hebt, moet u naar de site van de uitgever gaan om het installatieproces te voltooien.</span><span class="sxs-lookup"><span data-stu-id="5c651-106">If you have a production subscription, you must visit the publisher's site to complete the setup process.</span></span> <span data-ttu-id="5c651-107">Abonnementsfacturering begint pas nadat de installatie is voltooid.</span><span class="sxs-lookup"><span data-stu-id="5c651-107">Subscription billing will begin only after setup is complete.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5c651-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="5c651-108">Prerequisites</span></span>

- <span data-ttu-id="5c651-109">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5c651-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5c651-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="5c651-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="5c651-111">Een sandbox-partneraccount voor integratie met een klant met een actief abonnement voor SaaS-producten op de commerciële marketplace.</span><span class="sxs-lookup"><span data-stu-id="5c651-111">An integration sandbox partner account with a customer having an active subscription for commercial marketplace SaaS products.</span></span>

- <span data-ttu-id="5c651-112">Voor partners die Partner Center .NET SDK gebruiken, moet u SDK versie 1.14.0 of hoger gebruiken om toegang te krijgen tot deze mogelijkheid.</span><span class="sxs-lookup"><span data-stu-id="5c651-112">For partners using Partner Center .NET SDK, you must use SDK version 1.14.0 or higher to access this capability.</span></span>

## <a name="c"></a><span data-ttu-id="5c651-113">C\#</span><span class="sxs-lookup"><span data-stu-id="5c651-113">C\#</span></span>

<span data-ttu-id="5c651-114">Gebruik de volgende stappen om een abonnement te activeren voor SaaS-producten op de commerciële marketplace:</span><span class="sxs-lookup"><span data-stu-id="5c651-114">Use the following steps to activate a subscription for commercial marketplace SaaS products:</span></span>

1. <span data-ttu-id="5c651-115">Maak een interface voor de abonnementsbewerkingen beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="5c651-115">Make an interface to the subscription operations available.</span></span> <span data-ttu-id="5c651-116">U moet de klant identificeren en de abonnements-id van het proefabonnement opgeven.</span><span class="sxs-lookup"><span data-stu-id="5c651-116">You must identify the customer and specify the subscription identifier of the trial subscription.</span></span>

   ```csharp
   var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
   ```

2. <span data-ttu-id="5c651-117">Activeer het abonnement met behulp van **de bewerking Activate.**</span><span class="sxs-lookup"><span data-stu-id="5c651-117">Activate the subscription using the **Activate** operation.</span></span>

   ```csharp
   var subscriptionActivationResult = subscriptionOperations.Activate();
   ```

## <a name="rest-request"></a><span data-ttu-id="5c651-118">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="5c651-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5c651-119">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="5c651-119">Request syntax</span></span>

| <span data-ttu-id="5c651-120">Methode</span><span class="sxs-lookup"><span data-stu-id="5c651-120">Method</span></span>     | <span data-ttu-id="5c651-121">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="5c651-121">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="5c651-122">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="5c651-122">**POST**</span></span> | <span data-ttu-id="5c651-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/activate HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="5c651-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/activate HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="5c651-124">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="5c651-124">URI parameter</span></span>

| <span data-ttu-id="5c651-125">Naam</span><span class="sxs-lookup"><span data-stu-id="5c651-125">Name</span></span>                   | <span data-ttu-id="5c651-126">Type</span><span class="sxs-lookup"><span data-stu-id="5c651-126">Type</span></span>     | <span data-ttu-id="5c651-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="5c651-127">Required</span></span> | <span data-ttu-id="5c651-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5c651-128">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5c651-129">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="5c651-129">**customer-tenant-id**</span></span> | <span data-ttu-id="5c651-130">**guid**</span><span class="sxs-lookup"><span data-stu-id="5c651-130">**guid**</span></span> | <span data-ttu-id="5c651-131">J</span><span class="sxs-lookup"><span data-stu-id="5c651-131">Y</span></span> | <span data-ttu-id="5c651-132">De waarde is een tenant-id in GUID-indeling **(customer-tenant-id),** waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="5c651-132">The value is a GUID-formatted customer tenant identifier (**customer-tenant-id**), which allows you to specify a customer.</span></span> |
| <span data-ttu-id="5c651-133">**subscription-id**</span><span class="sxs-lookup"><span data-stu-id="5c651-133">**subscription-id**</span></span> | <span data-ttu-id="5c651-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="5c651-134">**guid**</span></span> | <span data-ttu-id="5c651-135">J</span><span class="sxs-lookup"><span data-stu-id="5c651-135">Y</span></span> | <span data-ttu-id="5c651-136">De waarde is een abonnements-id met **GUID-indeling (abonnements-id),** waarmee u een abonnement kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="5c651-136">The value is a GUID-formatted subscription identifier (**subscription-id**), which allows you to specify a subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="5c651-137">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="5c651-137">Request headers</span></span>

<span data-ttu-id="5c651-138">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="5c651-138">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5c651-139">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="5c651-139">Request body</span></span>

<span data-ttu-id="5c651-140">Geen.</span><span class="sxs-lookup"><span data-stu-id="5c651-140">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="5c651-141">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="5c651-141">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/42b5f772-5c5c-4bce-b9d7-bdadeecca411/subscriptions/87363db7-39ab-dd25-d371-94340aaa2f97/activate HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

```

## <a name="rest-response"></a><span data-ttu-id="5c651-142">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="5c651-142">REST response</span></span>

<span data-ttu-id="5c651-143">Deze methode retourneert de **eigenschappen subscription-id** **en status.**</span><span class="sxs-lookup"><span data-stu-id="5c651-143">This method returns the **subscription-id** and **status** properties.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5c651-144">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="5c651-144">Response success and error codes</span></span>

<span data-ttu-id="5c651-145">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="5c651-145">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5c651-146">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="5c651-146">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5c651-147">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="5c651-147">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="5c651-148">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="5c651-148">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 79
Content-Type: application/json
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

{
    "subscriptionId":"87363db7-39ab-dd25-d371-94340aaa2f97",
    "status":"Success"
}
```
