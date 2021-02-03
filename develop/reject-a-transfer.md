---
title: Een overdracht afwijzen
description: Een overdracht van abonnementen voor een klant afwijzen.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e4a182ff92a21cf72ca1c2da9de7e211b433725f
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767254"
---
# <a name="reject-a-transfer"></a><span data-ttu-id="35525-103">Een overdracht afwijzen</span><span class="sxs-lookup"><span data-stu-id="35525-103">Reject a transfer</span></span>

<span data-ttu-id="35525-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="35525-104">**Applies to:**</span></span>

- <span data-ttu-id="35525-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="35525-105">Partner Center</span></span>

## <a name="prerequisites"></a><span data-ttu-id="35525-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="35525-106">Prerequisites</span></span>

- <span data-ttu-id="35525-107">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="35525-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="35525-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="35525-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="35525-109">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="35525-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="35525-110">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="35525-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="35525-111">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="35525-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="35525-112">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="35525-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="35525-113">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="35525-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="35525-114">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="35525-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="35525-115">Een overdrachts-id voor een bestaande overdracht.</span><span class="sxs-lookup"><span data-stu-id="35525-115">A transfer identifier for an existing transfer.</span></span>

## <a name="rest-request"></a><span data-ttu-id="35525-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="35525-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="35525-117">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="35525-117">Request syntax</span></span>

| <span data-ttu-id="35525-118">Methode</span><span class="sxs-lookup"><span data-stu-id="35525-118">Method</span></span>   | <span data-ttu-id="35525-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="35525-119">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="35525-120">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="35525-120">**PATCH**</span></span> | <span data-ttu-id="35525-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/transfers/{Transfer-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="35525-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span></span>                    |

### <a name="uri-parameter"></a><span data-ttu-id="35525-122">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="35525-122">URI parameter</span></span>

<span data-ttu-id="35525-123">Gebruik de volgende para meter Path om de klant te identificeren en de overdracht op te geven die moet worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="35525-123">Use the following path parameter to identify the customer and specify the transfer to be accepted.</span></span>

| <span data-ttu-id="35525-124">Naam</span><span class="sxs-lookup"><span data-stu-id="35525-124">Name</span></span>            | <span data-ttu-id="35525-125">Type</span><span class="sxs-lookup"><span data-stu-id="35525-125">Type</span></span>     | <span data-ttu-id="35525-126">Vereist</span><span class="sxs-lookup"><span data-stu-id="35525-126">Required</span></span> | <span data-ttu-id="35525-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="35525-127">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="35525-128">**klant-id**</span><span class="sxs-lookup"><span data-stu-id="35525-128">**customer-id**</span></span> | <span data-ttu-id="35525-129">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="35525-129">string</span></span>   | <span data-ttu-id="35525-130">Yes</span><span class="sxs-lookup"><span data-stu-id="35525-130">Yes</span></span>      | <span data-ttu-id="35525-131">Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="35525-131">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="35525-132">**overdracht-id**</span><span class="sxs-lookup"><span data-stu-id="35525-132">**transfer-id**</span></span> | <span data-ttu-id="35525-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="35525-133">string</span></span>   | <span data-ttu-id="35525-134">Yes</span><span class="sxs-lookup"><span data-stu-id="35525-134">Yes</span></span>      | <span data-ttu-id="35525-135">Een door de GUID geformatteerde overdracht-id waarmee de overdracht wordt aangeduid.</span><span class="sxs-lookup"><span data-stu-id="35525-135">A GUID formatted transfer-id that identifies the transfer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="35525-136">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="35525-136">Request headers</span></span>

<span data-ttu-id="35525-137">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="35525-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="35525-138">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="35525-138">Request body</span></span>

<span data-ttu-id="35525-139">In deze tabel worden de eigenschappen van [TransferEntity](transfer-entity-resources.md) in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="35525-139">This table describes the [TransferEntity](transfer-entity-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="35525-140">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="35525-140">Property</span></span>              | <span data-ttu-id="35525-141">Type</span><span class="sxs-lookup"><span data-stu-id="35525-141">Type</span></span>          | <span data-ttu-id="35525-142">Vereist</span><span class="sxs-lookup"><span data-stu-id="35525-142">Required</span></span>  | <span data-ttu-id="35525-143">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="35525-143">Description</span></span>                                                                                |
|-----------------------|---------------|-----------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="35525-144">id</span><span class="sxs-lookup"><span data-stu-id="35525-144">id</span></span>                    | <span data-ttu-id="35525-145">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="35525-145">string</span></span>        | <span data-ttu-id="35525-146">No</span><span class="sxs-lookup"><span data-stu-id="35525-146">No</span></span>    | <span data-ttu-id="35525-147">Een transferEntity-id die wordt geleverd bij het maken van de transferEntity.</span><span class="sxs-lookup"><span data-stu-id="35525-147">A transferEntity identifier that is supplied upon successful creation of the transferEntity.</span></span>                               |
| <span data-ttu-id="35525-148">status</span><span class="sxs-lookup"><span data-stu-id="35525-148">status</span></span>                | <span data-ttu-id="35525-149">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="35525-149">string</span></span>        | <span data-ttu-id="35525-150">No</span><span class="sxs-lookup"><span data-stu-id="35525-150">No</span></span>    | <span data-ttu-id="35525-151">De status van de transferEntity.</span><span class="sxs-lookup"><span data-stu-id="35525-151">The status of the transferEntity.</span></span> <span data-ttu-id="35525-152">Als u een overdracht wilt afwijzen, moet de waarde worden ingesteld op ' afwijzen '</span><span class="sxs-lookup"><span data-stu-id="35525-152">To reject a transfer, the value is to be set as "reject"</span></span>|

### <a name="request-example"></a><span data-ttu-id="35525-153">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="35525-153">Request example</span></span>

```http
PATCH /v1/customers/b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0/transfers/ac4a9d22-ba07-444e-890f-cfe084eed498 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: efa4c6f5-153a-4f76-e458-1375e181cc14
MS-RequestId: 5b46e795-b661-428e-a2e7-f208b8d0d25c
Connection: keep-alive
Content-Length: 63

{"id":"ac4a9d22-ba07-444e-890f-cfe084eed498","status":"reject"}

```

## <a name="rest-response"></a><span data-ttu-id="35525-154">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="35525-154">REST response</span></span>

<span data-ttu-id="35525-155">Als dit lukt, retourneert deze methode de gevulde [TransferEntity](transfer-entity-resources.md) -resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="35525-155">If successful, this method returns the populated [TransferEntity](transfer-entity-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="35525-156">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="35525-156">Response success and error codes</span></span>

<span data-ttu-id="35525-157">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="35525-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="35525-158">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="35525-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="35525-159">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="35525-159">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="35525-160">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="35525-160">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1069
Content-Type: application/json; charset=utf-8
MS-CorrelationId: efa4c6f5-153a-4f76-e458-1375e181cc14
MS-RequestId: 5b46e795-b661-428e-a2e7-f208b8d0d25c
X-Locale: en-US
Date: Fri, 27 Mar 2020 17:50:33 GMT

{
  "id": "ac4a9d22-ba07-444e-890f-cfe084eed498",
  "status": "Reject",
  "createdTime": "2020-03-25T22:05:25.1057725Z",
  "lastModifiedTime": "2020-03-27T17:50:32Z",
  "customerTenantId": "b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0",
  "partnertenantid": "3a9a35ce-d5be-4814-ab58-4451c36fe157",
  "sourcePartnerName": "Test_Test_09092019GBL",
  "sourcePartnerTenantId": "7c8db11f-1e5e-4472-8386-f0b627d1f3e1",
  "targetPartnerName": "Test_Test_09032019GBL",
  "targetPartnerTenantId": "3a9a35ce-d5be-4814-ab58-4451c36fe157",
  "lastModifiedUser": "01a7548d-1136-4cf0-ba9a-300f921ffb22",
  "lineItems": [
    {
      "id": 0,
      "subscriptionId": "1151B8CE-125C-49D7-8C48-E62FC9101B77",
      "offerId": "13D32E13-A1B0-400D-96C0-4EAAA14DCED5",
      "billingCycle": "monthly",
      "friendlyName": "Dynamics 365 for Supply Chain Management Attach to Qualifying Dynamics 365 Base Offer (Qualified Offer)",
      "quantity": 20,
      "partnerIdOnRecord": "5139005",
      "addonItems": [

      ]
    }
  ],
  "links": {
    "self": {
      "uri": "/customers/b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0/transfers/ac4a9d22-ba07-444e-890f-cfe084eed498",
      "method": "GET",
      "headers": [

      ]
    }
  },
  "attributes": {
    "objectType": "TransferEntity"
  }
}
```
