---
title: De status van de directe ondertekening van de klant ophalen voor de micro soft-klant overeenkomst.
description: U kunt de DirectSignedCustomerAgreementStatus-Resource gebruiken om de status van de directe ondertekening (directe acceptatie) van een klant van de micro soft-klant overeenkomst te verkrijgen.
ms.date: 02/11/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 267e3aa63a94c5045977ad566eb5061df3b59882
ms.sourcegitcommit: bbdb5f7c9ddd42c2fc4eaadbb67d61aeeae805ca
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/24/2021
ms.locfileid: "105030552"
---
# <a name="get-the-status-of-a-customers-direct-signing-direct-acceptance-of-microsoft-customer-agreement"></a><span data-ttu-id="e4e67-103">De status van de directe ondertekening van een klant (direct accepteren) van de micro soft-klant overeenkomst ophalen</span><span class="sxs-lookup"><span data-stu-id="e4e67-103">Get the status of a customer's direct signing (direct acceptance) of Microsoft Customer Agreement</span></span>

<span data-ttu-id="e4e67-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="e4e67-104">**Applies to:**</span></span>

- <span data-ttu-id="e4e67-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e4e67-105">Partner Center</span></span>

<span data-ttu-id="e4e67-106">De **DirectSignedCustomerAgreementStatus** -resource wordt momenteel alleen ondersteund door het partner centrum in de open bare cloud van micro soft.</span><span class="sxs-lookup"><span data-stu-id="e4e67-106">The **DirectSignedCustomerAgreementStatus** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="e4e67-107">Deze resource is *niet van toepassing* op:</span><span class="sxs-lookup"><span data-stu-id="e4e67-107">This resource is *not applicable* to:</span></span>

- <span data-ttu-id="e4e67-108">Partnercentrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="e4e67-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="e4e67-109">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="e4e67-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="e4e67-110">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e4e67-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e4e67-111">In dit artikel wordt uitgelegd hoe u de status van de directe acceptatie van een klant kunt ophalen van de klant overeenkomst van micro soft.</span><span class="sxs-lookup"><span data-stu-id="e4e67-111">This article explains how you can retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e4e67-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e4e67-112">Prerequisites</span></span>

- <span data-ttu-id="e4e67-113">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e4e67-113">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e4e67-114">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="e4e67-114">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="e4e67-115">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e4e67-115">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e4e67-116">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="e4e67-116">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e4e67-117">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="e4e67-117">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e4e67-118">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="e4e67-118">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e4e67-119">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="e4e67-119">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e4e67-120">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e4e67-120">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="e4e67-121">C\#</span><span class="sxs-lookup"><span data-stu-id="e4e67-121">C\#</span></span>

<span data-ttu-id="e4e67-122">Als u de status van de directe acceptatie van een klant wilt ophalen van de micro soft-klant overeenkomst, roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id.</span><span class="sxs-lookup"><span data-stu-id="e4e67-122">To retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier.</span></span> <span data-ttu-id="e4e67-123">Gebruik vervolgens de eigenschap [**overeenkomsten**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.agreements) om een [**ICustomerAgreementCollection**](/dotnet/api/microsoft.store.partnercenter.agreements.icustomeragreementcollection) -interface op te halen.</span><span class="sxs-lookup"><span data-stu-id="e4e67-123">Then use the [**Agreements**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.agreements) property to retrieve a [**ICustomerAgreementCollection**](/dotnet/api/microsoft.store.partnercenter.agreements.icustomeragreementcollection) interface.</span></span> <span data-ttu-id="e4e67-124">Roep tot slot `GetDirectSignedCustomerAgreementStatus()` `GetDirectSignedCustomerAgreementStatusAsync()` de status aan of op te halen.</span><span class="sxs-lookup"><span data-stu-id="e4e67-124">Finally, call `GetDirectSignedCustomerAgreementStatus()` or `GetDirectSignedCustomerAgreementStatusAsync()` to retrieve the status.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
var customerDirectSigningStatus = partnerOperations.Customers.ById(selectedCustomerId).Agreements.GetDirectSignedCustomerAgreementStatus();
```

<span data-ttu-id="e4e67-125">Voor **beeld**: console-voor [beeld-app](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span><span class="sxs-lookup"><span data-stu-id="e4e67-125">**Sample**: [Console Sample App](https://github.com/microsoft/Partner-Center-DotNet-Samples).</span></span> <span data-ttu-id="e4e67-126">**Project**: SdkSamples- **klasse**: GetDirectSignedCustomerAgreementStatus. cs</span><span class="sxs-lookup"><span data-stu-id="e4e67-126">**Project**: SdkSamples **Class**: GetDirectSignedCustomerAgreementStatus.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="e4e67-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e4e67-127">REST request</span></span>

<span data-ttu-id="e4e67-128">Als u de status van de directe acceptatie van een klant wilt ophalen van de micro soft-klant overeenkomst, maakt u een REST-aanvraag om de [DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) voor de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="e4e67-128">To retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement, create a REST request to retrieve the [DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) for the customer.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e4e67-129">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e4e67-129">Request syntax</span></span>

<span data-ttu-id="e4e67-130">Gebruik de volgende aanvraag syntaxis:</span><span class="sxs-lookup"><span data-stu-id="e4e67-130">Use the following request syntax:</span></span>

| <span data-ttu-id="e4e67-131">Methode</span><span class="sxs-lookup"><span data-stu-id="e4e67-131">Method</span></span> | <span data-ttu-id="e4e67-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e4e67-132">Request URI</span></span>                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e4e67-133">GET</span><span class="sxs-lookup"><span data-stu-id="e4e67-133">GET</span></span>    | <span data-ttu-id="e4e67-134">[*\{ BASEURL \}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/directSignedMicrosoftCustomerAgreementStatus http/1.1</span><span class="sxs-lookup"><span data-stu-id="e4e67-134">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="e4e67-135">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="e4e67-135">URI parameters</span></span>

<span data-ttu-id="e4e67-136">U kunt de volgende URI-para meters met uw aanvraag gebruiken:</span><span class="sxs-lookup"><span data-stu-id="e4e67-136">You can use the following URI parameters with your request:</span></span>

| <span data-ttu-id="e4e67-137">Naam</span><span class="sxs-lookup"><span data-stu-id="e4e67-137">Name</span></span>             | <span data-ttu-id="e4e67-138">Type</span><span class="sxs-lookup"><span data-stu-id="e4e67-138">Type</span></span> | <span data-ttu-id="e4e67-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="e4e67-139">Required</span></span> | <span data-ttu-id="e4e67-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e4e67-140">Description</span></span>                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| <span data-ttu-id="e4e67-141">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="e4e67-141">customer-tenant-id</span></span> | <span data-ttu-id="e4e67-142">GUID</span><span class="sxs-lookup"><span data-stu-id="e4e67-142">GUID</span></span> | <span data-ttu-id="e4e67-143">Ja</span><span class="sxs-lookup"><span data-stu-id="e4e67-143">Yes</span></span> | <span data-ttu-id="e4e67-144">De waarde is een **CustomerTenantId** met de GUID-indeling waarmee u de Tenant-id van een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="e4e67-144">The value is a GUID-formatted **CustomerTenantId** that allows you to specify the tenant ID of a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e4e67-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e4e67-145">Request headers</span></span>

<span data-ttu-id="e4e67-146">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e4e67-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e4e67-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e4e67-147">Request body</span></span>

<span data-ttu-id="e4e67-148">Geen.</span><span class="sxs-lookup"><span data-stu-id="e4e67-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e4e67-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e4e67-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="e4e67-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e4e67-150">REST response</span></span>

<span data-ttu-id="e4e67-151">Als dit lukt, retourneert deze methode een [ **DirectSignedCustomerAgreementStatus** -resource](./customer-agreement-direct-sign-status-resource.md) in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="e4e67-151">If successful, this method returns a [**DirectSignedCustomerAgreementStatus** resource](./customer-agreement-direct-sign-status-resource.md) in the response body.</span></span>

<span data-ttu-id="e4e67-152">De resource heeft een **isSigned** -eigenschap die de directe goedkeurings status van de klant aanduidt.</span><span class="sxs-lookup"><span data-stu-id="e4e67-152">The resource has an **isSigned** property that indicates the customer's direct signing (direct acceptance) status.</span></span>

- <span data-ttu-id="e4e67-153">De waarde **True** geeft aan dat de overeenkomst rechtstreeks door de klant is ondertekend (geaccepteerd).</span><span class="sxs-lookup"><span data-stu-id="e4e67-153">A value of **true** indicates that the agreement has been signed (accepted) directly by the customer.</span></span>

- <span data-ttu-id="e4e67-154">De waarde **False** geeft aan dat de overeenkomst rechtstreeks door de *klant is ondertekend* (geaccepteerd).</span><span class="sxs-lookup"><span data-stu-id="e4e67-154">A value of **false** indicates that the agreement has *not* been signed (accepted) directly by the customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e4e67-155">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="e4e67-155">Response success and error codes</span></span>

<span data-ttu-id="e4e67-156">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="e4e67-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="e4e67-157">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e4e67-157">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e4e67-158">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="e4e67-158">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e4e67-159">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e4e67-159">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 20
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b

{"isSigned":true}
```
