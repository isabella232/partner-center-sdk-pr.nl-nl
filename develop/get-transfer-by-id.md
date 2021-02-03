---
title: Details van overdracht op id ophalen
description: Meer informatie over het overdragen van abonnementen voor een klant.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c39e9483f1e51469981b0d6fa2541a6372ff2dac
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767231"
---
# <a name="get-transfer-details-by-id"></a><span data-ttu-id="f7467-103">Details van overdracht op id ophalen</span><span class="sxs-lookup"><span data-stu-id="f7467-103">Get transfer details by id</span></span>

<span data-ttu-id="f7467-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="f7467-104">**Applies to:**</span></span>

- <span data-ttu-id="f7467-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="f7467-105">Partner Center</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f7467-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f7467-106">Prerequisites</span></span>

- <span data-ttu-id="f7467-107">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f7467-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f7467-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="f7467-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="f7467-109">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f7467-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="f7467-110">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="f7467-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="f7467-111">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="f7467-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="f7467-112">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="f7467-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="f7467-113">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="f7467-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="f7467-114">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="f7467-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="f7467-115">Een overdrachts-id voor een bestaande overdracht.</span><span class="sxs-lookup"><span data-stu-id="f7467-115">A transfer identifier for an existing transfer.</span></span>

## <a name="rest-request"></a><span data-ttu-id="f7467-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="f7467-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f7467-117">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="f7467-117">Request syntax</span></span>

| <span data-ttu-id="f7467-118">Methode</span><span class="sxs-lookup"><span data-stu-id="f7467-118">Method</span></span>   | <span data-ttu-id="f7467-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="f7467-119">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="f7467-120">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="f7467-120">**GET**</span></span> | <span data-ttu-id="f7467-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/transfers/{Transfer-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="f7467-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span></span>                    |

### <a name="uri-parameter"></a><span data-ttu-id="f7467-122">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="f7467-122">URI parameter</span></span>

<span data-ttu-id="f7467-123">Gebruik de volgende para meter Path om de klant te identificeren en de overdracht op te geven die moet worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="f7467-123">Use the following path parameter to identify the customer and specify the transfer to be accepted.</span></span>

| <span data-ttu-id="f7467-124">Naam</span><span class="sxs-lookup"><span data-stu-id="f7467-124">Name</span></span>            | <span data-ttu-id="f7467-125">Type</span><span class="sxs-lookup"><span data-stu-id="f7467-125">Type</span></span>     | <span data-ttu-id="f7467-126">Vereist</span><span class="sxs-lookup"><span data-stu-id="f7467-126">Required</span></span> | <span data-ttu-id="f7467-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f7467-127">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="f7467-128">**klant-id**</span><span class="sxs-lookup"><span data-stu-id="f7467-128">**customer-id**</span></span> | <span data-ttu-id="f7467-129">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="f7467-129">string</span></span>   | <span data-ttu-id="f7467-130">Yes</span><span class="sxs-lookup"><span data-stu-id="f7467-130">Yes</span></span>      | <span data-ttu-id="f7467-131">Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="f7467-131">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="f7467-132">**overdracht-id**</span><span class="sxs-lookup"><span data-stu-id="f7467-132">**transfer-id**</span></span> | <span data-ttu-id="f7467-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="f7467-133">string</span></span>   | <span data-ttu-id="f7467-134">Yes</span><span class="sxs-lookup"><span data-stu-id="f7467-134">Yes</span></span>      | <span data-ttu-id="f7467-135">Een door de GUID geformatteerde overdracht-id waarmee de overdracht wordt aangeduid.</span><span class="sxs-lookup"><span data-stu-id="f7467-135">A GUID formatted transfer-id that identifies the transfer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="f7467-136">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="f7467-136">Request headers</span></span>

<span data-ttu-id="f7467-137">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="f7467-137">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-example"></a><span data-ttu-id="f7467-138">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="f7467-138">Request example</span></span>

```http
GET /v1/customers/b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0/transfers/46e8ed67-8adf-4f65-b3d8-d31318080556 HTTP/1.1
Authorization: Bearer <token>
Connection: keep-alive
MS-RequestId: 0d61b5ce-b396-4f5e-a50b-e8779d0d23cc
MS-CorrelationId: 68eacc61-971c-43b0-c06f-2622bf79b090
Accept: application/json
```

## <a name="rest-response"></a><span data-ttu-id="f7467-139">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="f7467-139">REST response</span></span>

<span data-ttu-id="f7467-140">Als dit lukt, retourneert deze methode de gevulde [TransferEntity](transfer-entity-resources.md) -resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="f7467-140">If successful, this method returns the populated [TransferEntity](transfer-entity-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f7467-141">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="f7467-141">Response success and error codes</span></span>

<span data-ttu-id="f7467-142">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="f7467-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f7467-143">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="f7467-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f7467-144">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="f7467-144">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="f7467-145">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="f7467-145">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1501
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 68eacc61-971c-43b0-c06f-2622bf79b090
MS-RequestId: 0d61b5ce-b396-4f5e-a50b-e8779d0d23cc
X-Locale: en-US
Date: Fri, 27 Mar 2020 18:25:25 GMT

{
  "id": "46e8ed67-8adf-4f65-b3d8-d31318080556",
  "status": "Active",
  "createdTime": "2020-03-27T18:22:33.2875302Z",
  "lastModifiedTime": "2020-03-27T18:22:33Z",
  "customerTenantId": "b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0",
  "partnertenantid": "3a9a35ce-d5be-4814-ab58-4451c36fe157",
  "sourcePartnerName": "Test_Test_09092019GBL",
  "sourcePartnerTenantId": "7c8db11f-1e5e-4472-8386-f0b627d1f3e1",
  "targetPartnerName": "Test_Test_09032019GBL",
  "targetPartnerTenantId": "3a9a35ce-d5be-4814-ab58-4451c36fe157",
  "lastModifiedUser": "edc0524d-2e42-4619-af7e-349c015cfdfd",
  "lineItems": [
    {
      "id": 0,
      "subscriptionId": "75B71186-73C3-45B4-A403-281C0D7EB032",
      "offerId": "F72752C8-3E37-4C9B-A1A0-69E8442068DC",
      "billingCycle": "annual",
      "friendlyName": "Dynamics 365 Business Central Team Member",
      "quantity": 1,
      "partnerIdOnRecord": "5139005",
      "addonItems": [

      ]
    },
    {
      "id": 1,
      "subscriptionId": "1FB4CB0A-EB79-4300-9E87-7D486054888A",
      "offerId": "88F9EB8A-0636-45E8-A601-553E0A48AA9E",
      "billingCycle": "annual",
      "friendlyName": "Dynamics 365 Business Central External Accountant",
      "quantity": 1,
      "partnerIdOnRecord": "5139005",
      "addonItems": [

      ]
    },
    {
      "id": 2,
      "subscriptionId": "08AB3010-B647-402E-8955-B6C0FB364D8F",
      "offerId": "4D8F3B90-29B3-4E7B-B37C-4A435DDEF1D9",
      "billingCycle": "annual",
      "friendlyName": "Common Area Phone",
      "quantity": 1,
      "partnerIdOnRecord": "5139005",
      "addonItems": [

      ]
    }
  ],
  "links": {
    "self": {
      "uri": "/customers/b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0/transfers/46e8ed67-8adf-4f65-b3d8-d31318080556",
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
