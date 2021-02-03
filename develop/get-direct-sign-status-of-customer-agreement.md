---
title: De status van de directe ondertekening van de klant ophalen voor de micro soft-klant overeenkomst.
description: U kunt de DirectSignedCustomerAgreementStatus-Resource gebruiken om de status van de directe ondertekening (directe acceptatie) van een klant van de micro soft-klant overeenkomst te verkrijgen.
ms.date: 02/11/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 3f1deb20a18bc6e7133cac91db528f2d1ad694e2
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767174"
---
# <a name="get-the-status-of-a-customers-direct-signing-direct-acceptance-of-microsoft-customer-agreement"></a><span data-ttu-id="589c4-103">De status van de directe ondertekening van een klant (direct accepteren) van de micro soft-klant overeenkomst ophalen</span><span class="sxs-lookup"><span data-stu-id="589c4-103">Get the status of a customer's direct signing (direct acceptance) of Microsoft Customer Agreement</span></span>

<span data-ttu-id="589c4-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="589c4-104">**Applies to:**</span></span>

- <span data-ttu-id="589c4-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="589c4-105">Partner Center</span></span>

<span data-ttu-id="589c4-106">De **DirectSignedCustomerAgreementStatus** -resource wordt momenteel alleen ondersteund door het partner centrum in de open bare cloud van micro soft.</span><span class="sxs-lookup"><span data-stu-id="589c4-106">The **DirectSignedCustomerAgreementStatus** resource is currently supported by Partner Center only in the Microsoft public cloud.</span></span>

<span data-ttu-id="589c4-107">Deze resource is *niet van toepassing* op:</span><span class="sxs-lookup"><span data-stu-id="589c4-107">This resource is *not applicable* to:</span></span>

- <span data-ttu-id="589c4-108">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="589c4-108">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="589c4-109">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="589c4-109">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="589c4-110">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="589c4-110">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="589c4-111">In dit artikel wordt uitgelegd hoe u de status van de directe acceptatie van een klant kunt ophalen van de klant overeenkomst van micro soft.</span><span class="sxs-lookup"><span data-stu-id="589c4-111">This article explains how you can retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement.</span></span>

## <a name="rest-request"></a><span data-ttu-id="589c4-112">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="589c4-112">REST request</span></span>

<span data-ttu-id="589c4-113">Als u de status van de directe acceptatie van een klant wilt ophalen van de micro soft-klant overeenkomst, maakt u een REST-aanvraag om de [DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) voor de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="589c4-113">To retrieve the status of a customer's direct acceptance of the Microsoft Customer Agreement, create a REST request to retrieve the [DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) for the customer.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="589c4-114">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="589c4-114">Request syntax</span></span>

<span data-ttu-id="589c4-115">Gebruik de volgende aanvraag syntaxis:</span><span class="sxs-lookup"><span data-stu-id="589c4-115">Use the following request syntax:</span></span>

| <span data-ttu-id="589c4-116">Methode</span><span class="sxs-lookup"><span data-stu-id="589c4-116">Method</span></span> | <span data-ttu-id="589c4-117">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="589c4-117">Request URI</span></span>                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| <span data-ttu-id="589c4-118">GET</span><span class="sxs-lookup"><span data-stu-id="589c4-118">GET</span></span>    | <span data-ttu-id="589c4-119">[*\{ BASEURL \}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/directSignedMicrosoftCustomerAgreementStatus http/1.1</span><span class="sxs-lookup"><span data-stu-id="589c4-119">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="589c4-120">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="589c4-120">URI parameters</span></span>

<span data-ttu-id="589c4-121">U kunt de volgende URI-para meters met uw aanvraag gebruiken:</span><span class="sxs-lookup"><span data-stu-id="589c4-121">You can use the following URI parameters with your request:</span></span>

| <span data-ttu-id="589c4-122">Naam</span><span class="sxs-lookup"><span data-stu-id="589c4-122">Name</span></span>             | <span data-ttu-id="589c4-123">Type</span><span class="sxs-lookup"><span data-stu-id="589c4-123">Type</span></span> | <span data-ttu-id="589c4-124">Vereist</span><span class="sxs-lookup"><span data-stu-id="589c4-124">Required</span></span> | <span data-ttu-id="589c4-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="589c4-125">Description</span></span>                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| <span data-ttu-id="589c4-126">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="589c4-126">customer-tenant-id</span></span> | <span data-ttu-id="589c4-127">GUID</span><span class="sxs-lookup"><span data-stu-id="589c4-127">GUID</span></span> | <span data-ttu-id="589c4-128">Yes</span><span class="sxs-lookup"><span data-stu-id="589c4-128">Yes</span></span> | <span data-ttu-id="589c4-129">De waarde is een **CustomerTenantId** met de GUID-indeling waarmee u de Tenant-id van een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="589c4-129">The value is a GUID-formatted **CustomerTenantId** that allows you to specify the tenant ID of a customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="589c4-130">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="589c4-130">Request headers</span></span>

<span data-ttu-id="589c4-131">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="589c4-131">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="589c4-132">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="589c4-132">Request body</span></span>

<span data-ttu-id="589c4-133">Geen.</span><span class="sxs-lookup"><span data-stu-id="589c4-133">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="589c4-134">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="589c4-134">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a><span data-ttu-id="589c4-135">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="589c4-135">REST response</span></span>

<span data-ttu-id="589c4-136">Als dit lukt, retourneert deze methode een [ **DirectSignedCustomerAgreementStatus** -resource](./customer-agreement-direct-sign-status-resource.md) in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="589c4-136">If successful, this method returns a [**DirectSignedCustomerAgreementStatus** resource](./customer-agreement-direct-sign-status-resource.md) in the response body.</span></span>

<span data-ttu-id="589c4-137">De resource heeft een **isSigned** -eigenschap die de directe goedkeurings status van de klant aanduidt.</span><span class="sxs-lookup"><span data-stu-id="589c4-137">The resource has an **isSigned** property that indicates the customer's direct signing (direct acceptance) status.</span></span>

- <span data-ttu-id="589c4-138">De waarde **True** geeft aan dat de overeenkomst rechtstreeks door de klant is ondertekend (geaccepteerd).</span><span class="sxs-lookup"><span data-stu-id="589c4-138">A value of **true** indicates that the agreement has been signed (accepted) directly by the customer.</span></span>

- <span data-ttu-id="589c4-139">De waarde **False** geeft aan dat de overeenkomst rechtstreeks door de *klant is ondertekend* (geaccepteerd).</span><span class="sxs-lookup"><span data-stu-id="589c4-139">A value of **false** indicates that the agreement has *not* been signed (accepted) directly by the customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="589c4-140">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="589c4-140">Response success and error codes</span></span>

<span data-ttu-id="589c4-141">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="589c4-141">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span>

<span data-ttu-id="589c4-142">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="589c4-142">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="589c4-143">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="589c4-143">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="589c4-144">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="589c4-144">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 20
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b

{"isSigned":true}
```
