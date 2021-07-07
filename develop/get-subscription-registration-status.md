---
title: De registratiestatus van het abonnement ophalen
description: Haal de status op van een abonnement dat is geregistreerd voor gebruik met Azure Reserved VM Instances.
ms.date: 03/19/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9e39f94c0eac402a0be3afde84279aa637868f96
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445949"
---
# <a name="get-subscription-registration-status"></a><span data-ttu-id="845a1-103">De registratiestatus van het abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="845a1-103">Get subscription registration status</span></span>

<span data-ttu-id="845a1-104">De registratiestatus van het abonnement voor een klantabonnement dat is ingeschakeld voor het kopen van Azure Reserved VM Instances.</span><span class="sxs-lookup"><span data-stu-id="845a1-104">How to get the subscription registration status for a customer subscription that has been enabled for purchasing Azure Reserved VM Instances.</span></span>

<span data-ttu-id="845a1-105">Als u een gereserveerde VM-instantie van Azure wilt kopen met behulp van Partner Center API, moet u ten minste één bestaand CSP Azure-abonnement hebben.</span><span class="sxs-lookup"><span data-stu-id="845a1-105">To purchase an Azure Reserved VM Instance using the Partner Center API, you must have at least one existing CSP Azure subscription.</span></span> <span data-ttu-id="845a1-106">Met [de methode Een abonnement](register-a-subscription.md) registreren kunt u uw bestaande CSP Azure-abonnement registreren en deze inschakelen voor Azure Reserved VM Instances.</span><span class="sxs-lookup"><span data-stu-id="845a1-106">The [Register a subscription](register-a-subscription.md) method allows you to register your existing CSP Azure subscription, enabling it for purchasing Azure Reserved VM Instances.</span></span> <span data-ttu-id="845a1-107">Met deze methode kunt u de status van die registratie ophalen.</span><span class="sxs-lookup"><span data-stu-id="845a1-107">This method allows you to retrieve the status of that registration.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="845a1-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="845a1-108">Prerequisites</span></span>

- <span data-ttu-id="845a1-109">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="845a1-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="845a1-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="845a1-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="845a1-111">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="845a1-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="845a1-112">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="845a1-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="845a1-113">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="845a1-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="845a1-114">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="845a1-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="845a1-115">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="845a1-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="845a1-116">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="845a1-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="845a1-117">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="845a1-117">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="845a1-118">C\#</span><span class="sxs-lookup"><span data-stu-id="845a1-118">C\#</span></span>

<span data-ttu-id="845a1-119">Als u de registratiestatus van een abonnement wilt weten, gebruikt u eerst de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="845a1-119">To get the registration status of a subscription, begin by using the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="845a1-120">Haal vervolgens een interface op voor abonnementsbewerkingen door de methode [**Subscription.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) aan te roepen met de abonnements-id om het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="845a1-120">Then, get an interface to subscription operations by calling the [**Subscription.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method with the subscription ID to identify the subscription.</span></span> <span data-ttu-id="845a1-121">Gebruik vervolgens de eigenschap RegistrationStatus om een interface te verkrijgen voor de registratiestatusbewerkingen van het huidige abonnement en roep de methode **Get** of **GetAsync** aan om het object **SubscriptionRegistrationStatus op te** halen.</span><span class="sxs-lookup"><span data-stu-id="845a1-121">Next, use the RegistrationStatus property to obtain an interface to the current subscription's registration status operations, and call the **Get** or **GetAsync** method to retrieve the **SubscriptionRegistrationStatus** object.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId;
// var selectedSubscriptionId;

// Retrieve a subscription's registration status details.
var subscriptionRegistrationDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).RegistrationStatus.Get();
```

## <a name="rest-request"></a><span data-ttu-id="845a1-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="845a1-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="845a1-123">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="845a1-123">Request syntax</span></span>

| <span data-ttu-id="845a1-124">Methode</span><span class="sxs-lookup"><span data-stu-id="845a1-124">Method</span></span>    | <span data-ttu-id="845a1-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="845a1-125">Request URI</span></span>                                                                                                                        |
|-----------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="845a1-126">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="845a1-126">**GET**</span></span>  | <span data-ttu-id="845a1-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrationstatus HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="845a1-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrationstatus HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="845a1-128">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="845a1-128">URI parameters</span></span>

<span data-ttu-id="845a1-129">Gebruik de volgende padparameters om de klant en het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="845a1-129">Use the following path parameters to identify the customer and subscription.</span></span>

| <span data-ttu-id="845a1-130">Naam</span><span class="sxs-lookup"><span data-stu-id="845a1-130">Name</span></span>                    | <span data-ttu-id="845a1-131">Type</span><span class="sxs-lookup"><span data-stu-id="845a1-131">Type</span></span>       | <span data-ttu-id="845a1-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="845a1-132">Required</span></span> | <span data-ttu-id="845a1-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="845a1-133">Description</span></span>                                                   |
|-------------------------|------------|----------|---------------------------------------------------------------|
| <span data-ttu-id="845a1-134">customer-id</span><span class="sxs-lookup"><span data-stu-id="845a1-134">customer-id</span></span>             | <span data-ttu-id="845a1-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="845a1-135">string</span></span>     | <span data-ttu-id="845a1-136">Ja</span><span class="sxs-lookup"><span data-stu-id="845a1-136">Yes</span></span>      | <span data-ttu-id="845a1-137">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="845a1-137">A GUID formatted string that identifies the customer.</span></span>         |
| <span data-ttu-id="845a1-138">subscription-id</span><span class="sxs-lookup"><span data-stu-id="845a1-138">subscription-id</span></span>         | <span data-ttu-id="845a1-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="845a1-139">string</span></span>     | <span data-ttu-id="845a1-140">Ja</span><span class="sxs-lookup"><span data-stu-id="845a1-140">Yes</span></span>      | <span data-ttu-id="845a1-141">Een tekenreeks met GUID-indeling die het abonnement identificeert.</span><span class="sxs-lookup"><span data-stu-id="845a1-141">A GUID formatted string that identifies the subscription.</span></span>     |

### <a name="request-headers"></a><span data-ttu-id="845a1-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="845a1-142">Request headers</span></span>

<span data-ttu-id="845a1-143">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="845a1-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="845a1-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="845a1-144">Request body</span></span>

<span data-ttu-id="845a1-145">Geen.</span><span class="sxs-lookup"><span data-stu-id="845a1-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="845a1-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="845a1-146">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="845a1-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="845a1-147">REST response</span></span>

<span data-ttu-id="845a1-148">Als dit lukt, bevat de antwoord-body een [resource SubscriptionRegistrationStatus.](subscription-resources.md#subscriptionregistrationstatus)</span><span class="sxs-lookup"><span data-stu-id="845a1-148">If successful, the response body contains a [SubscriptionRegistrationStatus](subscription-resources.md#subscriptionregistrationstatus) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="845a1-149">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="845a1-149">Response success and error codes</span></span>

<span data-ttu-id="845a1-150">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="845a1-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="845a1-151">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="845a1-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="845a1-152">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="845a1-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="845a1-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="845a1-153">Response example</span></span>

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
