---
title: Een sandbox-abonnement voor commerciële Marketplace-producten activeren
description: Meer informatie over het gebruik van C/# en de REST Api's van het Partner Center om een sandbox-abonnement voor commerciële Marketplace-producten te activeren.
ms.date: 09/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a78b2c84368b29f1378f46971c4814929094e299
ms.sourcegitcommit: 8a5c37376a29e29fe0002a980082d4acc6b91131
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/11/2020
ms.locfileid: "97767578"
---
# <a name="activate-a-sandbox-subscription-for-commercial-marketplace-saas-products-to-enable-billing"></a><span data-ttu-id="c97bd-103">Een sandbox-abonnement voor SaaS-producten voor commerciële Marketplace activeren om facturering mogelijk te maken</span><span class="sxs-lookup"><span data-stu-id="c97bd-103">Activate a sandbox subscription for commercial marketplace SaaS products to enable billing</span></span>

<span data-ttu-id="c97bd-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="c97bd-104">**Applies to:**</span></span>

- <span data-ttu-id="c97bd-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="c97bd-105">Partner Center</span></span>

<span data-ttu-id="c97bd-106">Het activeren van een abonnement voor software als een service (SaaS) voor commerciële Marketplace vanuit integratie Sandbox-accounts om facturering mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="c97bd-106">How to activate a subscription for commercial marketplace Software as a Service (SaaS) products from integration sandbox accounts to enable billing.</span></span>

> [!NOTE]
> <span data-ttu-id="c97bd-107">Het is alleen mogelijk om een abonnement te activeren voor commerciële Marketplace SaaS-producten vanuit integratie Sandbox-accounts.</span><span class="sxs-lookup"><span data-stu-id="c97bd-107">It's only possible to activate a subscription for commercial marketplace SaaS products from integration sandbox accounts.</span></span> <span data-ttu-id="c97bd-108">Als u een productie abonnement hebt, moet u de site van de uitgever bezoeken om het installatie proces te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="c97bd-108">If you have a production subscription, you must visit the publisher's site to complete the setup process.</span></span> <span data-ttu-id="c97bd-109">De facturering van het abonnement wordt pas gestart nadat de installatie is voltooid.</span><span class="sxs-lookup"><span data-stu-id="c97bd-109">Subscription billing will begin only after setup is complete.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c97bd-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c97bd-110">Prerequisites</span></span>

- <span data-ttu-id="c97bd-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c97bd-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c97bd-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="c97bd-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="c97bd-113">Een integratie sandbox-partner account met een klant die beschikt over een actief abonnement voor producten van de commerciële Marketplace SaaS.</span><span class="sxs-lookup"><span data-stu-id="c97bd-113">An integration sandbox partner account with a customer having an active subscription for commercial marketplace SaaS products.</span></span>

- <span data-ttu-id="c97bd-114">Voor partners die gebruikmaken van partner Center .NET SDK, moet u SDK-versie 1.14.0 of hoger gebruiken om toegang te krijgen tot deze mogelijkheid.</span><span class="sxs-lookup"><span data-stu-id="c97bd-114">For partners using Partner Center .NET SDK, you must use SDK version 1.14.0 or higher to access this capability.</span></span>

## <a name="c"></a><span data-ttu-id="c97bd-115">C\#</span><span class="sxs-lookup"><span data-stu-id="c97bd-115">C\#</span></span>

<span data-ttu-id="c97bd-116">Gebruik de volgende stappen om een abonnement te activeren voor producten voor commerciële Marketplace SaaS:</span><span class="sxs-lookup"><span data-stu-id="c97bd-116">Use the following steps to activate a subscription for commercial marketplace SaaS products:</span></span>

1. <span data-ttu-id="c97bd-117">Maak een interface voor de beschik bare abonnements bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="c97bd-117">Make an interface to the subscription operations available.</span></span> <span data-ttu-id="c97bd-118">U moet de klant identificeren en de abonnements-id van het proef abonnement opgeven.</span><span class="sxs-lookup"><span data-stu-id="c97bd-118">You must identify the customer and specify the subscription identifier of the trial subscription.</span></span>

   ```csharp
   var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
   ```

2. <span data-ttu-id="c97bd-119">Activeer het abonnement met de bewerking **Activate** .</span><span class="sxs-lookup"><span data-stu-id="c97bd-119">Activate the subscription using the **Activate** operation.</span></span>

   ```csharp
   var subscriptionActivationResult = subscriptionOperations.Activate();
   ```

## <a name="rest-request"></a><span data-ttu-id="c97bd-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c97bd-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c97bd-121">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c97bd-121">Request syntax</span></span>

| <span data-ttu-id="c97bd-122">Methode</span><span class="sxs-lookup"><span data-stu-id="c97bd-122">Method</span></span>     | <span data-ttu-id="c97bd-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c97bd-123">Request URI</span></span>                                                                            |
|------------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="c97bd-124">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="c97bd-124">**POST**</span></span> | <span data-ttu-id="c97bd-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{Subscription-id}/Activate http/1.1</span><span class="sxs-lookup"><span data-stu-id="c97bd-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/activate HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="c97bd-126">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="c97bd-126">URI parameter</span></span>

| <span data-ttu-id="c97bd-127">Naam</span><span class="sxs-lookup"><span data-stu-id="c97bd-127">Name</span></span>                   | <span data-ttu-id="c97bd-128">Type</span><span class="sxs-lookup"><span data-stu-id="c97bd-128">Type</span></span>     | <span data-ttu-id="c97bd-129">Vereist</span><span class="sxs-lookup"><span data-stu-id="c97bd-129">Required</span></span> | <span data-ttu-id="c97bd-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c97bd-130">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c97bd-131">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="c97bd-131">**customer-tenant-id**</span></span> | <span data-ttu-id="c97bd-132">**guid**</span><span class="sxs-lookup"><span data-stu-id="c97bd-132">**guid**</span></span> | <span data-ttu-id="c97bd-133">J</span><span class="sxs-lookup"><span data-stu-id="c97bd-133">Y</span></span> | <span data-ttu-id="c97bd-134">De waarde is een Tenant-id voor de GUID-indeling (**klant-Tenant-id**), waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="c97bd-134">The value is a GUID-formatted customer tenant identifier (**customer-tenant-id**), which allows you to specify a customer.</span></span> |
| <span data-ttu-id="c97bd-135">**abonnement-id**</span><span class="sxs-lookup"><span data-stu-id="c97bd-135">**subscription-id**</span></span> | <span data-ttu-id="c97bd-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="c97bd-136">**guid**</span></span> | <span data-ttu-id="c97bd-137">J</span><span class="sxs-lookup"><span data-stu-id="c97bd-137">Y</span></span> | <span data-ttu-id="c97bd-138">De waarde is een abonnements-id met een GUID-indeling (**abonnements-id**) waarmee u een abonnement kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="c97bd-138">The value is a GUID-formatted subscription identifier (**subscription-id**), which allows you to specify a subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c97bd-139">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c97bd-139">Request headers</span></span>

<span data-ttu-id="c97bd-140">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c97bd-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c97bd-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c97bd-141">Request body</span></span>

<span data-ttu-id="c97bd-142">Geen.</span><span class="sxs-lookup"><span data-stu-id="c97bd-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c97bd-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c97bd-143">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/42b5f772-5c5c-4bce-b9d7-bdadeecca411/subscriptions/87363db7-39ab-dd25-d371-94340aaa2f97/activate HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

```

## <a name="rest-response"></a><span data-ttu-id="c97bd-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c97bd-144">REST response</span></span>

<span data-ttu-id="c97bd-145">Met deze methode worden de eigenschappen van de **abonnements-id** en de **status** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c97bd-145">This method returns the **subscription-id** and **status** properties.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c97bd-146">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="c97bd-146">Response success and error codes</span></span>

<span data-ttu-id="c97bd-147">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="c97bd-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c97bd-148">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c97bd-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c97bd-149">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="c97bd-149">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c97bd-150">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="c97bd-150">Response example</span></span>

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
