---
title: Overdrachtsdetails per id op halen
description: Meer informatie over een overdracht van abonnementen voor een klant.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1347f95debec458b8c70c5e803cef6203ad34818
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445932"
---
# <a name="get-transfer-details-by-id"></a><span data-ttu-id="fee90-103">Overdrachtsdetails per id op halen</span><span class="sxs-lookup"><span data-stu-id="fee90-103">Get transfer details by ID</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fee90-104">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fee90-104">Prerequisites</span></span>

- <span data-ttu-id="fee90-105">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fee90-105">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fee90-106">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="fee90-106">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="fee90-107">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fee90-107">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="fee90-108">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="fee90-108">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="fee90-109">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="fee90-109">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="fee90-110">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="fee90-110">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="fee90-111">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="fee90-111">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="fee90-112">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fee90-112">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="fee90-113">Een overdrachts-id voor een bestaande overdracht.</span><span class="sxs-lookup"><span data-stu-id="fee90-113">A transfer identifier for an existing transfer.</span></span>

## <a name="rest-request"></a><span data-ttu-id="fee90-114">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fee90-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fee90-115">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="fee90-115">Request syntax</span></span>

| <span data-ttu-id="fee90-116">Methode</span><span class="sxs-lookup"><span data-stu-id="fee90-116">Method</span></span>   | <span data-ttu-id="fee90-117">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fee90-117">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fee90-118">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fee90-118">**GET**</span></span> | <span data-ttu-id="fee90-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fee90-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span></span>                    |

### <a name="uri-parameter"></a><span data-ttu-id="fee90-120">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="fee90-120">URI parameter</span></span>

<span data-ttu-id="fee90-121">Gebruik de volgende padparameter om de klant te identificeren en geef de overdracht op die moet worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="fee90-121">Use the following path parameter to identify the customer and specify the transfer to be accepted.</span></span>

| <span data-ttu-id="fee90-122">Naam</span><span class="sxs-lookup"><span data-stu-id="fee90-122">Name</span></span>            | <span data-ttu-id="fee90-123">Type</span><span class="sxs-lookup"><span data-stu-id="fee90-123">Type</span></span>     | <span data-ttu-id="fee90-124">Vereist</span><span class="sxs-lookup"><span data-stu-id="fee90-124">Required</span></span> | <span data-ttu-id="fee90-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fee90-125">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="fee90-126">**customer-id**</span><span class="sxs-lookup"><span data-stu-id="fee90-126">**customer-id**</span></span> | <span data-ttu-id="fee90-127">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fee90-127">string</span></span>   | <span data-ttu-id="fee90-128">Ja</span><span class="sxs-lookup"><span data-stu-id="fee90-128">Yes</span></span>      | <span data-ttu-id="fee90-129">Een met GUID opgemaakte klant-id die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="fee90-129">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="fee90-130">**transfer-id**</span><span class="sxs-lookup"><span data-stu-id="fee90-130">**transfer-id**</span></span> | <span data-ttu-id="fee90-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fee90-131">string</span></span>   | <span data-ttu-id="fee90-132">Ja</span><span class="sxs-lookup"><span data-stu-id="fee90-132">Yes</span></span>      | <span data-ttu-id="fee90-133">Een met GUID opgemaakte overdrachts-id die de overdracht identificeert.</span><span class="sxs-lookup"><span data-stu-id="fee90-133">A GUID formatted transfer-id that identifies the transfer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="fee90-134">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="fee90-134">Request headers</span></span>

<span data-ttu-id="fee90-135">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="fee90-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-example"></a><span data-ttu-id="fee90-136">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fee90-136">Request example</span></span>

```http
GET /v1/customers/b67f0b00-f9e8-4c57-bcb5-0b8b95c6ccf0/transfers/46e8ed67-8adf-4f65-b3d8-d31318080556 HTTP/1.1
Authorization: Bearer <token>
Connection: keep-alive
MS-RequestId: 0d61b5ce-b396-4f5e-a50b-e8779d0d23cc
MS-CorrelationId: 68eacc61-971c-43b0-c06f-2622bf79b090
Accept: application/json
```

## <a name="rest-response"></a><span data-ttu-id="fee90-137">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fee90-137">REST response</span></span>

<span data-ttu-id="fee90-138">Als dit lukt, retourneert deze methode de ingevulde [TransferEntity-resource](transfer-entity-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="fee90-138">If successful, this method returns the populated [TransferEntity](transfer-entity-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fee90-139">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="fee90-139">Response success and error codes</span></span>

<span data-ttu-id="fee90-140">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="fee90-140">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fee90-141">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fee90-141">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fee90-142">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="fee90-142">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fee90-143">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fee90-143">Response example</span></span>

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
