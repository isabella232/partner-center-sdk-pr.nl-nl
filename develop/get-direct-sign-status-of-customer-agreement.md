---
title: Haal de status van directe ondertekening van de klant op voor Microsoft-klantovereenkomst.
description: U kunt de resource DirectSignedCustomerAgreementStatus gebruiken om de status van de directe ondertekening (directe acceptatie) van de klant van de Microsoft-klantovereenkomst.
ms.date: 02/11/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: a17775614b4eb328514b2b32b4cac1e513019cff
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549175"
---
# <a name="get-the-status-of-a-customers-direct-signing-direct-acceptance-of-microsoft-customer-agreement"></a><span data-ttu-id="c0b55-103">De status van de directe ondertekening (directe acceptatie) van de Microsoft-klantovereenkomst</span><span class="sxs-lookup"><span data-stu-id="c0b55-103">Get the status of a customer's direct signing (direct acceptance) of Microsoft Customer Agreement</span></span>

<span data-ttu-id="c0b55-104">**Van toepassing op**: Partner Center</span><span class="sxs-lookup"><span data-stu-id="c0b55-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="c0b55-105">**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c0b55-105">**Does not apply to**: Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c0b55-106">De **resource DirectSignedCustomerAgreementStatus** wordt momenteel alleen Partner Center in de openbare Cloud van Microsoft ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c0b55-106">The **DirectSignedCustomerAgreementStatus** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="c0b55-107">In dit artikel wordt uitgelegd hoe u de status kunt ophalen van de rechtstreekse acceptatie van de Microsoft-klantovereenkomst.</span><span class="sxs-lookup"><span data-stu-id="c0b55-107">This article explains how you can retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c0b55-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c0b55-108">Prerequisites</span></span>

- <span data-ttu-id="c0b55-109">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c0b55-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c0b55-110">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="c0b55-110">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="c0b55-111">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c0b55-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="c0b55-112">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="c0b55-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="c0b55-113">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="c0b55-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="c0b55-114">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="c0b55-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="c0b55-115">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="c0b55-115">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="c0b55-116">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c0b55-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="c0b55-117">C\#</span><span class="sxs-lookup"><span data-stu-id="c0b55-117">C\#</span></span>

<span data-ttu-id="c0b55-118">Als u de status van de directe acceptatie van de Microsoft-klantovereenkomst van een klant wilt ophalen, roept u de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id.</span><span class="sxs-lookup"><span data-stu-id="c0b55-118">To retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="c0b55-119">Gebruik vervolgens de [**eigenschap Agreements**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.agreements) om een [**ICustomerAgreementCollection-interface op te**](/dotnet/api/microsoft.store.partnercenter.agreements.icustomeragreementcollection) halen.</span><span class="sxs-lookup"><span data-stu-id="c0b55-119">Then use the [**Agreements**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.agreements) property to retrieve a [**ICustomerAgreementCollection**](/dotnet/api/microsoft.store.partnercenter.agreements.icustomeragreementcollection) interface.</span></span> <span data-ttu-id="c0b55-120">Roep ten slotte `GetDirectSignedCustomerAgreementStatus()` of aan om de status op te `GetDirectSignedCustomerAgreementStatusAsync()` halen.</span><span class="sxs-lookup"><span data-stu-id="c0b55-120">Finally, call `GetDirectSignedCustomerAgreementStatus()` or `GetDirectSignedCustomerAgreementStatusAsync()` to retrieve the status.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
var customerDirectSigningStatus = partnerOperations.Customers.ById(selectedCustomerId).Agreements.GetDirectSignedCustomerAgreementStatus();
```

<span data-ttu-id="c0b55-121">**Voorbeeld:** [consolevoorbeeld-app.](https://github.com/microsoft/Partner-Center-DotNet-Samples)</span><span class="sxs-lookup"><span data-stu-id="c0b55-121">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="c0b55-122">**Project:** Klasse SdkSamples: GetDirectSignedCustomerAgreementStatus.cs </span><span class="sxs-lookup"><span data-stu-id="c0b55-122">**Project**: SdkSamples **Class**: GetDirectSignedCustomerAgreementStatus.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="c0b55-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c0b55-123">REST request</span></span>

<span data-ttu-id="c0b55-124">Als u de status van de directe acceptatie van de Microsoft-klantovereenkomst van een klant wilt ophalen, maakt u een REST-aanvraag om [de DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) voor de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="c0b55-124">To retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement, create a REST request to retrieve the [DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) for the customer.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c0b55-125">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="c0b55-125">Request syntax</span></span>

<span data-ttu-id="c0b55-126">Gebruik de volgende aanvraagsyntaxis:</span><span class="sxs-lookup"><span data-stu-id="c0b55-126">Use the following request syntax:</span></span>

| <span data-ttu-id="c0b55-127">Methode</span><span class="sxs-lookup"><span data-stu-id="c0b55-127">Method</span></span> | <span data-ttu-id="c0b55-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c0b55-128">Request URI</span></span>                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c0b55-129">GET</span><span class="sxs-lookup"><span data-stu-id="c0b55-129">GET</span></span>    | <span data-ttu-id="c0b55-130">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c0b55-130">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="c0b55-131">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="c0b55-131">URI parameters</span></span>

<span data-ttu-id="c0b55-132">U kunt de volgende URI-parameters gebruiken bij uw aanvraag:</span><span class="sxs-lookup"><span data-stu-id="c0b55-132">You can use the following URI parameters with your request:</span></span>

| <span data-ttu-id="c0b55-133">Naam</span><span class="sxs-lookup"><span data-stu-id="c0b55-133">Name</span></span>             | <span data-ttu-id="c0b55-134">Type</span><span class="sxs-lookup"><span data-stu-id="c0b55-134">Type</span></span> | <span data-ttu-id="c0b55-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="c0b55-135">Required</span></span> | <span data-ttu-id="c0b55-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c0b55-136">Description</span></span>                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| <span data-ttu-id="c0b55-137">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="c0b55-137">customer-tenant-id</span></span> | <span data-ttu-id="c0b55-138">GUID</span><span class="sxs-lookup"><span data-stu-id="c0b55-138">GUID</span></span> | <span data-ttu-id="c0b55-139">Ja</span><span class="sxs-lookup"><span data-stu-id="c0b55-139">Yes</span></span> | <span data-ttu-id="c0b55-140">De waarde is een **CustomerTenantId** in GUID-indeling waarmee u de tenant-id van een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="c0b55-140">The value is a GUID-formatted **CustomerTenantId** that allows you to specify the tenant ID of a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c0b55-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c0b55-141">Request headers</span></span>

<span data-ttu-id="c0b55-142">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="c0b55-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c0b55-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c0b55-143">Request body</span></span>

<span data-ttu-id="c0b55-144">Geen.</span><span class="sxs-lookup"><span data-stu-id="c0b55-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c0b55-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c0b55-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="c0b55-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c0b55-146">REST response</span></span>

<span data-ttu-id="c0b55-147">Als dit lukt, retourneert deze methode een [ **DirectSignedCustomerAgreementStatus-resource**](./customer-agreement-direct-sign-status-resource.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="c0b55-147">If successful, this method returns a [**DirectSignedCustomerAgreementStatus** resource](./customer-agreement-direct-sign-status-resource.md) in the response body.</span></span>

<span data-ttu-id="c0b55-148">De resource heeft een **eigenschap isSigned** die de status van directe ondertekening (directe acceptatie) van de klant aangeeft.</span><span class="sxs-lookup"><span data-stu-id="c0b55-148">The resource has an **isSigned** property that indicates the customer's direct signing (direct acceptance) status.</span></span>

- <span data-ttu-id="c0b55-149">De waarde **true geeft** aan dat de overeenkomst rechtstreeks door de klant is ondertekend (geaccepteerd).</span><span class="sxs-lookup"><span data-stu-id="c0b55-149">A value of **true** indicates that the agreement has been signed (accepted) directly by the customer.</span></span>

- <span data-ttu-id="c0b55-150">De waarde **false geeft** aan dat de overeenkomst niet rechtstreeks door de klant is ondertekend (geaccepteerd). </span><span class="sxs-lookup"><span data-stu-id="c0b55-150">A value of **false** indicates that the agreement has *not* been signed (accepted) directly by the customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c0b55-151">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="c0b55-151">Response success and error codes</span></span>

<span data-ttu-id="c0b55-152">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="c0b55-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="c0b55-153">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c0b55-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c0b55-154">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="c0b55-154">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c0b55-155">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="c0b55-155">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 20
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b

{"isSigned":true}
```
