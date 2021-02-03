---
title: De registratiestatus van het abonnement ophalen
description: De status ophalen van een abonnement dat is geregistreerd voor gebruik met Azure Reserved VM Instances.
ms.date: 03/19/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e06cf8a450d6c281f7f83a68c899d1e5b29e9855
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767544"
---
# <a name="get-subscription-registration-status"></a><span data-ttu-id="76a04-103">De registratiestatus van het abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="76a04-103">Get subscription registration status</span></span>

<span data-ttu-id="76a04-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="76a04-104">**Applies To**</span></span>

- <span data-ttu-id="76a04-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="76a04-105">Partner Center</span></span>

<span data-ttu-id="76a04-106">De registratie status van abonnementen ophalen voor een klant abonnement dat is ingeschakeld voor aankoop van Azure Reserved VM Instances.</span><span class="sxs-lookup"><span data-stu-id="76a04-106">How to get the subscription registration status for a customer subscription that has been enabled for purchasing Azure Reserved VM Instances.</span></span>

<span data-ttu-id="76a04-107">Als u een voor Azure gereserveerde VM-instantie wilt kopen met de Partner Center API, moet u ten minste één bestaand CSP Azure-abonnement hebben.</span><span class="sxs-lookup"><span data-stu-id="76a04-107">To purchase an Azure Reserved VM Instance using the Partner Center API, you must have at least one existing CSP Azure subscription.</span></span> <span data-ttu-id="76a04-108">Met de methode [een abonnement registreren](register-a-subscription.md) kunt u uw bestaande CSP Azure-abonnement registreren, zodat deze kan worden gekocht Azure reserved VM instances.</span><span class="sxs-lookup"><span data-stu-id="76a04-108">The [Register a subscription](register-a-subscription.md) method allows you to register your existing CSP Azure subscription, enabling it for purchasing Azure Reserved VM Instances.</span></span> <span data-ttu-id="76a04-109">Met deze methode kunt u de status van die registratie ophalen.</span><span class="sxs-lookup"><span data-stu-id="76a04-109">This method allows you to retrieve the status of that registration.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="76a04-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="76a04-110">Prerequisites</span></span>

- <span data-ttu-id="76a04-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="76a04-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="76a04-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="76a04-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="76a04-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="76a04-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="76a04-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="76a04-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="76a04-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="76a04-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="76a04-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="76a04-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="76a04-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="76a04-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="76a04-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="76a04-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="76a04-119">Een abonnements-ID.</span><span class="sxs-lookup"><span data-stu-id="76a04-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="76a04-120">C\#</span><span class="sxs-lookup"><span data-stu-id="76a04-120">C\#</span></span>

<span data-ttu-id="76a04-121">Als u de registratie status van een abonnement wilt ophalen, begint u met de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="76a04-121">To get the registration status of a subscription, begin by using the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="76a04-122">Vervolgens krijgt u een interface voor abonnements bewerkingen door de methode [**Subscription. ById ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) aan te roepen met de abonnements-id om het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="76a04-122">Then, get an interface to subscription operations by calling the [**Subscription.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method with the subscription ID to identify the subscription.</span></span> <span data-ttu-id="76a04-123">Vervolgens gebruikt u de eigenschap RegistrationStatus om een interface te verkrijgen voor de registratie status bewerkingen van het huidige abonnement en roept u de methode **Get** of **GetAsync** aan om het **SubscriptionRegistrationStatus** -object op te halen.</span><span class="sxs-lookup"><span data-stu-id="76a04-123">Next, use the RegistrationStatus property to obtain an interface to the current subscription's registration status operations, and call the **Get** or **GetAsync** method to retrieve the **SubscriptionRegistrationStatus** object.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId;
// var selectedSubscriptionId;

// Retrieve a subscription's registration status details.
var subscriptionRegistrationDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).RegistrationStatus.Get();
```

## <a name="rest-request"></a><span data-ttu-id="76a04-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="76a04-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="76a04-125">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="76a04-125">Request syntax</span></span>

| <span data-ttu-id="76a04-126">Methode</span><span class="sxs-lookup"><span data-stu-id="76a04-126">Method</span></span>    | <span data-ttu-id="76a04-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="76a04-127">Request URI</span></span>                                                                                                                        |
|-----------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="76a04-128">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="76a04-128">**GET**</span></span>  | <span data-ttu-id="76a04-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Subscriptions/{Subscription-id}/registrationstatus http/1.1</span><span class="sxs-lookup"><span data-stu-id="76a04-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrationstatus HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="76a04-130">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="76a04-130">URI parameters</span></span>

<span data-ttu-id="76a04-131">Gebruik de volgende Path-para meters om de klant en het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="76a04-131">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="76a04-132">Naam</span><span class="sxs-lookup"><span data-stu-id="76a04-132">Name</span></span>                    | <span data-ttu-id="76a04-133">Type</span><span class="sxs-lookup"><span data-stu-id="76a04-133">Type</span></span>       | <span data-ttu-id="76a04-134">Vereist</span><span class="sxs-lookup"><span data-stu-id="76a04-134">Required</span></span> | <span data-ttu-id="76a04-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="76a04-135">Description</span></span>                                                   |
|-------------------------|------------|----------|---------------------------------------------------------------|
| <span data-ttu-id="76a04-136">klant-id</span><span class="sxs-lookup"><span data-stu-id="76a04-136">customer-id</span></span>             | <span data-ttu-id="76a04-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="76a04-137">string</span></span>     | <span data-ttu-id="76a04-138">Yes</span><span class="sxs-lookup"><span data-stu-id="76a04-138">Yes</span></span>      | <span data-ttu-id="76a04-139">Een teken reeks met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="76a04-139">A GUID formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="76a04-140">abonnement-id</span><span class="sxs-lookup"><span data-stu-id="76a04-140">subscription-id</span></span>         | <span data-ttu-id="76a04-141">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="76a04-141">string</span></span>     | <span data-ttu-id="76a04-142">Yes</span><span class="sxs-lookup"><span data-stu-id="76a04-142">Yes</span></span>      | <span data-ttu-id="76a04-143">Een teken reeks met een GUID-indeling waarmee het abonnement wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="76a04-143">A GUID formatted string that identifies the subscription.</span></span>     |

### <a name="request-headers"></a><span data-ttu-id="76a04-144">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="76a04-144">Request headers</span></span>

<span data-ttu-id="76a04-145">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="76a04-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="76a04-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="76a04-146">Request body</span></span>

<span data-ttu-id="76a04-147">Geen.</span><span class="sxs-lookup"><span data-stu-id="76a04-147">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="76a04-148">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="76a04-148">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-id>/subscriptions/<subscription-id>/registrationstatus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="76a04-149">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="76a04-149">REST response</span></span>

<span data-ttu-id="76a04-150">Als dit lukt, bevat de antwoord tekst een [SubscriptionRegistrationStatus](subscription-resources.md#subscriptionregistrationstatus) -resource.</span><span class="sxs-lookup"><span data-stu-id="76a04-150">If successful, the response body contains a [SubscriptionRegistrationStatus](subscription-resources.md#subscriptionregistrationstatus) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="76a04-151">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="76a04-151">Response success and error codes</span></span>

<span data-ttu-id="76a04-152">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="76a04-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="76a04-153">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="76a04-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="76a04-154">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="76a04-154">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="76a04-155">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="76a04-155">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123
MS-CV: InswEQre402koceL.0
MS-ServerId: 030020344

{
    "subscriptionId":"<subscription-id>",
    "status":"NotRegistered",
    "attributes":{
        "objectType":"SubscriptionRegistrationStatus"
    }
}
```
