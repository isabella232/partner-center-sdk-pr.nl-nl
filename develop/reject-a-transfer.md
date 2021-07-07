---
title: Een overdracht afwijzen
description: Het afwijzen van een overdracht van abonnementen voor een klant.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d09905979a89c9b2092462512c485524cd681d5f
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445371"
---
# <a name="reject-a-transfer"></a><span data-ttu-id="659c7-103">Een overdracht afwijzen</span><span class="sxs-lookup"><span data-stu-id="659c7-103">Reject a transfer</span></span>

## <a name="prerequisites"></a><span data-ttu-id="659c7-104">Vereisten</span><span class="sxs-lookup"><span data-stu-id="659c7-104">Prerequisites</span></span>

- <span data-ttu-id="659c7-105">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="659c7-105">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="659c7-106">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="659c7-106">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="659c7-107">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="659c7-107">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="659c7-108">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="659c7-108">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="659c7-109">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="659c7-109">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="659c7-110">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="659c7-110">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="659c7-111">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="659c7-111">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="659c7-112">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="659c7-112">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="659c7-113">Een overdrachts-id voor een bestaande overdracht.</span><span class="sxs-lookup"><span data-stu-id="659c7-113">A transfer identifier for an existing transfer.</span></span>

## <a name="rest-request"></a><span data-ttu-id="659c7-114">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="659c7-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="659c7-115">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="659c7-115">Request syntax</span></span>

| <span data-ttu-id="659c7-116">Methode</span><span class="sxs-lookup"><span data-stu-id="659c7-116">Method</span></span>   | <span data-ttu-id="659c7-117">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="659c7-117">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="659c7-118">**Patch**</span><span class="sxs-lookup"><span data-stu-id="659c7-118">**PATCH**</span></span> | <span data-ttu-id="659c7-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="659c7-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers/{transfer-id} HTTP/1.1</span></span>                    |

### <a name="uri-parameter"></a><span data-ttu-id="659c7-120">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="659c7-120">URI parameter</span></span>

<span data-ttu-id="659c7-121">Gebruik de volgende padparameter om de klant te identificeren en geef de overdracht op die moet worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="659c7-121">Use the following path parameter to identify the customer and specify the transfer to be accepted.</span></span>

| <span data-ttu-id="659c7-122">Naam</span><span class="sxs-lookup"><span data-stu-id="659c7-122">Name</span></span>            | <span data-ttu-id="659c7-123">Type</span><span class="sxs-lookup"><span data-stu-id="659c7-123">Type</span></span>     | <span data-ttu-id="659c7-124">Vereist</span><span class="sxs-lookup"><span data-stu-id="659c7-124">Required</span></span> | <span data-ttu-id="659c7-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="659c7-125">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="659c7-126">**customer-id**</span><span class="sxs-lookup"><span data-stu-id="659c7-126">**customer-id**</span></span> | <span data-ttu-id="659c7-127">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="659c7-127">string</span></span>   | <span data-ttu-id="659c7-128">Ja</span><span class="sxs-lookup"><span data-stu-id="659c7-128">Yes</span></span>      | <span data-ttu-id="659c7-129">Een in GUID opgemaakte klant-id die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="659c7-129">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="659c7-130">**transfer-id**</span><span class="sxs-lookup"><span data-stu-id="659c7-130">**transfer-id**</span></span> | <span data-ttu-id="659c7-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="659c7-131">string</span></span>   | <span data-ttu-id="659c7-132">Ja</span><span class="sxs-lookup"><span data-stu-id="659c7-132">Yes</span></span>      | <span data-ttu-id="659c7-133">Een met GUID opgemaakte overdrachts-id die de overdracht identificeert.</span><span class="sxs-lookup"><span data-stu-id="659c7-133">A GUID formatted transfer-id that identifies the transfer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="659c7-134">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="659c7-134">Request headers</span></span>

<span data-ttu-id="659c7-135">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="659c7-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="659c7-136">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="659c7-136">Request body</span></span>

<span data-ttu-id="659c7-137">In deze tabel worden de [eigenschappen van TransferEntity](transfer-entity-resources.md) in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="659c7-137">This table describes the [TransferEntity](transfer-entity-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="659c7-138">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="659c7-138">Property</span></span>              | <span data-ttu-id="659c7-139">Type</span><span class="sxs-lookup"><span data-stu-id="659c7-139">Type</span></span>          | <span data-ttu-id="659c7-140">Vereist</span><span class="sxs-lookup"><span data-stu-id="659c7-140">Required</span></span>  | <span data-ttu-id="659c7-141">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="659c7-141">Description</span></span>                                                                                |
|-----------------------|---------------|-----------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="659c7-142">id</span><span class="sxs-lookup"><span data-stu-id="659c7-142">id</span></span>                    | <span data-ttu-id="659c7-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="659c7-143">string</span></span>        | <span data-ttu-id="659c7-144">No</span><span class="sxs-lookup"><span data-stu-id="659c7-144">No</span></span>    | <span data-ttu-id="659c7-145">Een id voor transferEntity die wordt opgegeven bij het maken van de transferEntity.</span><span class="sxs-lookup"><span data-stu-id="659c7-145">A transferEntity identifier that is supplied upon successful creation of the transferEntity.</span></span>                               |
| <span data-ttu-id="659c7-146">status</span><span class="sxs-lookup"><span data-stu-id="659c7-146">status</span></span>                | <span data-ttu-id="659c7-147">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="659c7-147">string</span></span>        | <span data-ttu-id="659c7-148">No</span><span class="sxs-lookup"><span data-stu-id="659c7-148">No</span></span>    | <span data-ttu-id="659c7-149">De status van de transferEntity.</span><span class="sxs-lookup"><span data-stu-id="659c7-149">The status of the transferEntity.</span></span> <span data-ttu-id="659c7-150">Als u een overdracht wilt weigeren, moet de waarde worden ingesteld op 'weigeren'</span><span class="sxs-lookup"><span data-stu-id="659c7-150">To reject a transfer, the value is to be set as "reject"</span></span>|

### <a name="request-example"></a><span data-ttu-id="659c7-151">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="659c7-151">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="659c7-152">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="659c7-152">REST response</span></span>

<span data-ttu-id="659c7-153">Als dit lukt, retourneert deze methode de ingevulde [TransferEntity-resource](transfer-entity-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="659c7-153">If successful, this method returns the populated [TransferEntity](transfer-entity-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="659c7-154">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="659c7-154">Response success and error codes</span></span>

<span data-ttu-id="659c7-155">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="659c7-155">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="659c7-156">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="659c7-156">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="659c7-157">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="659c7-157">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="659c7-158">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="659c7-158">Response example</span></span>

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
