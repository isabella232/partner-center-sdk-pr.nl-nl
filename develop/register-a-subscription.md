---
title: Een abonnement registreren
description: Registreer een bestaand abonnement zodat het geschikt is voor het best Ellen van Azure-reserve ringen.
ms.date: 07/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9a96bb350f22430c9fd7a1759e336cc9f3ca1939
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767478"
---
# <a name="register-a-subscription"></a><span data-ttu-id="19453-103">Een abonnement registreren</span><span class="sxs-lookup"><span data-stu-id="19453-103">Register a subscription</span></span>

<span data-ttu-id="19453-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="19453-104">**Applies To**</span></span>

- <span data-ttu-id="19453-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="19453-105">Partner Center</span></span>

<span data-ttu-id="19453-106">Registreer een bestaand [abonnement](subscription-resources.md) zodat het geschikt is voor het best Ellen van Azure-reserve ringen.</span><span class="sxs-lookup"><span data-stu-id="19453-106">Register an existing [Subscription](subscription-resources.md) so that it is enabled for ordering Azure reservations.</span></span>

<span data-ttu-id="19453-107">Als u een Azure-reserve ring wilt kopen, moet u ten minste één bestaand CSP Azure-abonnement hebben.</span><span class="sxs-lookup"><span data-stu-id="19453-107">To purchase an Azure reservation you must have at least one existing CSP Azure subscription.</span></span> <span data-ttu-id="19453-108">Met deze methode kunt u uw bestaande CSP Azure-abonnement registreren, zodat het Azure-reserve ringen kan aanschaffen.</span><span class="sxs-lookup"><span data-stu-id="19453-108">This method allows you to register your existing CSP Azure subscription, enabling it for purchasing Azure reservations.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="19453-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="19453-109">Prerequisites</span></span>

- <span data-ttu-id="19453-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="19453-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="19453-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="19453-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="19453-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="19453-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="19453-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="19453-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="19453-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="19453-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="19453-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="19453-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="19453-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="19453-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="19453-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="19453-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="19453-118">Een abonnements-ID.</span><span class="sxs-lookup"><span data-stu-id="19453-118">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="19453-119">C\#</span><span class="sxs-lookup"><span data-stu-id="19453-119">C\#</span></span>

<span data-ttu-id="19453-120">Als u het abonnement van een klant wilt registreren, haalt u een interface op voor abonnements bewerkingen door de [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan te roepen met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="19453-120">To register a customer's subscription, retrieve an interface to subscription operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="19453-121">Vervolgens roept u de methode [**Subscription. ById ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) aan met de abonnements-id om het abonnement te identificeren dat u registreert.</span><span class="sxs-lookup"><span data-stu-id="19453-121">Then, call the [**Subscription.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method with the subscription ID to identify the subscription that you are registering.</span></span>

<span data-ttu-id="19453-122">Roep ten slotte de methode **Registration. REGI ster ()** aan om het abonnement te registreren en haal een URI op die kan worden gebruikt om de registratie status van het abonnement op te halen.</span><span class="sxs-lookup"><span data-stu-id="19453-122">Finally, call the **Registration.Register()** method to register the subscription and retrieve a URI that can be used to get the subscription registration status.</span></span> <span data-ttu-id="19453-123">Zie [inschrijvings status van abonnementen ophalen](get-subscription-registration-status.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="19453-123">For more information, see [Get subscription registration status](get-subscription-registration-status.md).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId;
// var selectedSubscriptionId;

// Retrieve the subscription registration details.
var subscriptionRegistrationDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).Registration.Register();
```

## <a name="rest-request"></a><span data-ttu-id="19453-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="19453-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="19453-125">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="19453-125">Request syntax</span></span>

| <span data-ttu-id="19453-126">Methode</span><span class="sxs-lookup"><span data-stu-id="19453-126">Method</span></span>    | <span data-ttu-id="19453-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="19453-127">Request URI</span></span>                                                                                                                        |
|-----------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="19453-128">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="19453-128">**POST**</span></span>  | <span data-ttu-id="19453-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Subscriptions/{Subscription-id}/Registrations http/1.1</span><span class="sxs-lookup"><span data-stu-id="19453-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrations HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="19453-130">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="19453-130">URI parameters</span></span>

<span data-ttu-id="19453-131">Gebruik de volgende Path-para meters om de klant en het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="19453-131">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="19453-132">Naam</span><span class="sxs-lookup"><span data-stu-id="19453-132">Name</span></span>                    | <span data-ttu-id="19453-133">Type</span><span class="sxs-lookup"><span data-stu-id="19453-133">Type</span></span>       | <span data-ttu-id="19453-134">Vereist</span><span class="sxs-lookup"><span data-stu-id="19453-134">Required</span></span> | <span data-ttu-id="19453-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="19453-135">Description</span></span>                                                   |
|-------------------------|------------|----------|---------------------------------------------------------------|
| <span data-ttu-id="19453-136">klant-id</span><span class="sxs-lookup"><span data-stu-id="19453-136">customer-id</span></span>             | <span data-ttu-id="19453-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="19453-137">string</span></span>     | <span data-ttu-id="19453-138">Yes</span><span class="sxs-lookup"><span data-stu-id="19453-138">Yes</span></span>      | <span data-ttu-id="19453-139">Een teken reeks met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="19453-139">A GUID formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="19453-140">abonnement-id</span><span class="sxs-lookup"><span data-stu-id="19453-140">subscription-id</span></span>         | <span data-ttu-id="19453-141">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="19453-141">string</span></span>     | <span data-ttu-id="19453-142">Yes</span><span class="sxs-lookup"><span data-stu-id="19453-142">Yes</span></span>      | <span data-ttu-id="19453-143">Een teken reeks met een GUID-indeling waarmee het abonnement wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="19453-143">A GUID formatted string that identifies the subscription.</span></span>     |

### <a name="request-headers"></a><span data-ttu-id="19453-144">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="19453-144">Request headers</span></span>

<span data-ttu-id="19453-145">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="19453-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="19453-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="19453-146">Request body</span></span>

<span data-ttu-id="19453-147">Geen.</span><span class="sxs-lookup"><span data-stu-id="19453-147">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="19453-148">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="19453-148">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="19453-149">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="19453-149">REST response</span></span>

<span data-ttu-id="19453-150">Als dit is gelukt, bevat het antwoord een **locatie** header met een URI die kan worden gebruikt om de registratie status van het abonnement op te halen.</span><span class="sxs-lookup"><span data-stu-id="19453-150">If successful, the response contains a **Location** header with a URI that can be used to retrieve the subscription registration status.</span></span> <span data-ttu-id="19453-151">Sla deze URI op voor gebruik met andere verwante REST Api's.</span><span class="sxs-lookup"><span data-stu-id="19453-151">Save this URI for use with other related REST APIs.</span></span> <span data-ttu-id="19453-152">Zie [inschrijvings status van abonnementen ophalen](get-subscription-registration-status.md)voor een voor beeld van het ophalen van de status.</span><span class="sxs-lookup"><span data-stu-id="19453-152">For an example of how to retrieve the status, see [Get subscription registration status](get-subscription-registration-status.md).</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="19453-153">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="19453-153">Response success and error codes</span></span>

<span data-ttu-id="19453-154">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="19453-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="19453-155">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="19453-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="19453-156">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="19453-156">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="19453-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="19453-157">Response example</span></span>

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/<customer-id>/subscriptions/<subscription-id>/registrationstatus
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
```
