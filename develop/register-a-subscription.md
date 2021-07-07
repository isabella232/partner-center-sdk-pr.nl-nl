---
title: Een abonnement registreren
description: Registreer een bestaand abonnement zodat het is ingeschakeld voor het bestellen van Azure-reserveringen.
ms.date: 07/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d26a7c77f60e6ef817cde80b9e97c88bd8bdc786
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446612"
---
# <a name="register-a-subscription"></a><span data-ttu-id="7f313-103">Een abonnement registreren</span><span class="sxs-lookup"><span data-stu-id="7f313-103">Register a subscription</span></span>

<span data-ttu-id="7f313-104">Registreer een bestaand [abonnement](subscription-resources.md) zodat dit is ingeschakeld voor het bestellen van Azure-reserveringen.</span><span class="sxs-lookup"><span data-stu-id="7f313-104">Register an existing [Subscription](subscription-resources.md) so that it is enabled for ordering Azure reservations.</span></span>

<span data-ttu-id="7f313-105">Als u een Azure-reservering wilt aanschaffen, moet u ten minste één bestaand CSP Azure-abonnement hebben.</span><span class="sxs-lookup"><span data-stu-id="7f313-105">To purchase an Azure reservation, you must have at least one existing CSP Azure subscription.</span></span> <span data-ttu-id="7f313-106">Met deze methode kunt u uw bestaande CSP Azure-abonnement registreren, zodat u deze kunt inschakelen voor het kopen van Azure-reserveringen.</span><span class="sxs-lookup"><span data-stu-id="7f313-106">This method allows you to register your existing CSP Azure subscription, enabling it for purchasing Azure reservations.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7f313-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7f313-107">Prerequisites</span></span>

- <span data-ttu-id="7f313-108">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="7f313-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7f313-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="7f313-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="7f313-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7f313-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="7f313-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="7f313-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="7f313-112">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="7f313-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="7f313-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="7f313-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="7f313-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="7f313-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="7f313-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7f313-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="7f313-116">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="7f313-116">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="7f313-117">C\#</span><span class="sxs-lookup"><span data-stu-id="7f313-117">C\#</span></span>

<span data-ttu-id="7f313-118">Als u het abonnement van een klant wilt registreren, haalt u een interface op voor abonnementsbewerkingen door de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="7f313-118">To register a customer's subscription, retrieve an interface to subscription operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="7f313-119">Roep vervolgens de methode [**Subscription.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) aan met de abonnements-id om het abonnement te identificeren dat u registreert.</span><span class="sxs-lookup"><span data-stu-id="7f313-119">Then, call the [**Subscription.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method with the subscription ID to identify the subscription that you are registering.</span></span>

<span data-ttu-id="7f313-120">Roep ten slotte de **methode Registration.Register()** aan om het abonnement te registreren en een URI op te halen die kan worden gebruikt om de registratiestatus van het abonnement op te halen.</span><span class="sxs-lookup"><span data-stu-id="7f313-120">Finally, call the **Registration.Register()** method to register the subscription and retrieve a URI that can be used to get the subscription registration status.</span></span> <span data-ttu-id="7f313-121">Zie Registratiestatus van abonnement verkrijgen [voor meer informatie.](get-subscription-registration-status.md)</span><span class="sxs-lookup"><span data-stu-id="7f313-121">For more information, see [Get subscription registration status](get-subscription-registration-status.md).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId;
// var selectedSubscriptionId;

// Retrieve the subscription registration details.
var subscriptionRegistrationDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).Registration.Register();
```

## <a name="rest-request"></a><span data-ttu-id="7f313-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="7f313-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7f313-123">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="7f313-123">Request syntax</span></span>

| <span data-ttu-id="7f313-124">Methode</span><span class="sxs-lookup"><span data-stu-id="7f313-124">Method</span></span>    | <span data-ttu-id="7f313-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="7f313-125">Request URI</span></span>                                                                                                                        |
|-----------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7f313-126">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="7f313-126">**POST**</span></span>  | <span data-ttu-id="7f313-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrations HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7f313-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrations HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="7f313-128">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="7f313-128">URI parameters</span></span>

<span data-ttu-id="7f313-129">Gebruik de volgende padparameters om de klant en het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="7f313-129">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="7f313-130">Naam</span><span class="sxs-lookup"><span data-stu-id="7f313-130">Name</span></span>                    | <span data-ttu-id="7f313-131">Type</span><span class="sxs-lookup"><span data-stu-id="7f313-131">Type</span></span>       | <span data-ttu-id="7f313-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="7f313-132">Required</span></span> | <span data-ttu-id="7f313-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7f313-133">Description</span></span>                                                   |
|-------------------------|------------|----------|---------------------------------------------------------------|
| <span data-ttu-id="7f313-134">customer-id</span><span class="sxs-lookup"><span data-stu-id="7f313-134">customer-id</span></span>             | <span data-ttu-id="7f313-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7f313-135">string</span></span>     | <span data-ttu-id="7f313-136">Ja</span><span class="sxs-lookup"><span data-stu-id="7f313-136">Yes</span></span>      | <span data-ttu-id="7f313-137">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="7f313-137">A GUID formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="7f313-138">subscription-id</span><span class="sxs-lookup"><span data-stu-id="7f313-138">subscription-id</span></span>         | <span data-ttu-id="7f313-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7f313-139">string</span></span>     | <span data-ttu-id="7f313-140">Ja</span><span class="sxs-lookup"><span data-stu-id="7f313-140">Yes</span></span>      | <span data-ttu-id="7f313-141">Een tekenreeks met GUID-indeling die het abonnement identificeert.</span><span class="sxs-lookup"><span data-stu-id="7f313-141">A GUID formatted string that identifies the subscription.</span></span>     |

### <a name="request-headers"></a><span data-ttu-id="7f313-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="7f313-142">Request headers</span></span>

<span data-ttu-id="7f313-143">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="7f313-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7f313-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="7f313-144">Request body</span></span>

<span data-ttu-id="7f313-145">Geen.</span><span class="sxs-lookup"><span data-stu-id="7f313-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="7f313-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7f313-146">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-id>/subscriptions/<subscription-id>/registrations HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="7f313-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="7f313-147">REST response</span></span>

<span data-ttu-id="7f313-148">Als dit lukt, bevat het antwoord een **Location-header** met een URI die kan worden gebruikt om de registratiestatus van het abonnement op te halen.</span><span class="sxs-lookup"><span data-stu-id="7f313-148">If successful, the response contains a **Location** header with a URI that can be used to retrieve the subscription registration status.</span></span> <span data-ttu-id="7f313-149">Sla deze URI op voor gebruik met andere gerelateerde REST API's.</span><span class="sxs-lookup"><span data-stu-id="7f313-149">Save this URI for use with other related REST APIs.</span></span> <span data-ttu-id="7f313-150">Zie Registratiestatus van abonnement ophalen voor een voorbeeld van het ophalen [van de status.](get-subscription-registration-status.md)</span><span class="sxs-lookup"><span data-stu-id="7f313-150">For an example of how to retrieve the status, see [Get subscription registration status](get-subscription-registration-status.md).</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7f313-151">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="7f313-151">Response success and error codes</span></span>

<span data-ttu-id="7f313-152">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="7f313-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7f313-153">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="7f313-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7f313-154">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="7f313-154">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="7f313-155">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="7f313-155">Response example</span></span>

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/<customer-id>/subscriptions/<subscription-id>/registrationstatus
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
```
