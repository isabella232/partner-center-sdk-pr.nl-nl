---
title: Een lijst met producten ophalen (per klant)
description: U kunt een klant-id gebruiken om een verzameling producten per klant op te halen.
ms.assetid: ''
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: a7cb2430aa93beb89e4d1f9b8c89a016d66624ca
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874190"
---
# <a name="get-a-list-of-products-by-customer"></a><span data-ttu-id="0377d-103">Een lijst met producten ophalen (per klant)</span><span class="sxs-lookup"><span data-stu-id="0377d-103">Get a list of products (by customer)</span></span>

<span data-ttu-id="0377d-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="0377d-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="0377d-105">U kunt de volgende methoden gebruiken om een verzameling producten voor een bestaande klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="0377d-105">You can use the following methods to get a collection of products for an existing customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0377d-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0377d-106">Prerequisites</span></span>

- <span data-ttu-id="0377d-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0377d-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="0377d-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="0377d-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="0377d-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0377d-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="0377d-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="0377d-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="0377d-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="0377d-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="0377d-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="0377d-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="0377d-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="0377d-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="0377d-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0377d-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="0377d-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="0377d-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0377d-116">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="0377d-116">Request syntax</span></span>

| <span data-ttu-id="0377d-117">Methode</span><span class="sxs-lookup"><span data-stu-id="0377d-117">Method</span></span> | <span data-ttu-id="0377d-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="0377d-118">Request URI</span></span>                                                                                                              |
|--------|--------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0377d-119">POST</span><span class="sxs-lookup"><span data-stu-id="0377d-119">POST</span></span>   | <span data-ttu-id="0377d-120">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products?targetView={targetView} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="0377d-120">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products?targetView={targetView} HTTP/1.1</span></span> |

#### <a name="request-uri-parameters"></a><span data-ttu-id="0377d-121">Aanvraag-URI-parameters</span><span class="sxs-lookup"><span data-stu-id="0377d-121">Request URI parameters</span></span>

| <span data-ttu-id="0377d-122">Naam</span><span class="sxs-lookup"><span data-stu-id="0377d-122">Name</span></span>               | <span data-ttu-id="0377d-123">Type</span><span class="sxs-lookup"><span data-stu-id="0377d-123">Type</span></span> | <span data-ttu-id="0377d-124">Vereist</span><span class="sxs-lookup"><span data-stu-id="0377d-124">Required</span></span> | <span data-ttu-id="0377d-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0377d-125">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="0377d-126">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="0377d-126">**customer-tenant-id**</span></span> | <span data-ttu-id="0377d-127">GUID</span><span class="sxs-lookup"><span data-stu-id="0377d-127">GUID</span></span> | <span data-ttu-id="0377d-128">Ja</span><span class="sxs-lookup"><span data-stu-id="0377d-128">Yes</span></span> | <span data-ttu-id="0377d-129">De waarde is een **klant-tenant-id** in GUID-indeling. Dit is een id waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="0377d-129">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |
| <span data-ttu-id="0377d-130">**targetView**</span><span class="sxs-lookup"><span data-stu-id="0377d-130">**targetView**</span></span> | <span data-ttu-id="0377d-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="0377d-131">string</span></span> | <span data-ttu-id="0377d-132">Ja</span><span class="sxs-lookup"><span data-stu-id="0377d-132">Yes</span></span> | <span data-ttu-id="0377d-133">Identificeert de doelweergave van de catalogus.</span><span class="sxs-lookup"><span data-stu-id="0377d-133">Identifies the target view of the catalog.</span></span> <span data-ttu-id="0377d-134">De ondersteunde waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="0377d-134">The supported values are:</span></span> <br/><br/><span data-ttu-id="0377d-135">**Azure,** dat alle Azure-items bevat</span><span class="sxs-lookup"><span data-stu-id="0377d-135">**Azure**, which includes all Azure items</span></span><br/><br/><span data-ttu-id="0377d-136">**AzureReservations,** dat alle Azure-reserveringsitems bevat</span><span class="sxs-lookup"><span data-stu-id="0377d-136">**AzureReservations**, which includes all Azure reservation items</span></span><br/><br/><span data-ttu-id="0377d-137">**AzureReservationsVM,** dat alle reserveringsitems voor virtuele machines (VM's) bevat</span><span class="sxs-lookup"><span data-stu-id="0377d-137">**AzureReservationsVM**, which includes all virtual machine (VM) reservation items</span></span><br/><br/><span data-ttu-id="0377d-138">**AzureReservationsSQL,** dat alle SQL reserveringsitems bevat</span><span class="sxs-lookup"><span data-stu-id="0377d-138">**AzureReservationsSQL**, which includes all SQL reservation items</span></span><br/><br/><span data-ttu-id="0377d-139">**AzureReservationsCosmosDb,** dat alle reserveringsitems voor de Cosmos-database bevat</span><span class="sxs-lookup"><span data-stu-id="0377d-139">**AzureReservationsCosmosDb**, which includes all Cosmos database reservation items</span></span><br/><br/><span data-ttu-id="0377d-140">**MicrosoftAzure,** dat items bevat voor Microsoft Azure -abonnementen (**MS-AZR-0145P**) en Azure-abonnementen</span><span class="sxs-lookup"><span data-stu-id="0377d-140">**MicrosoftAzure**, which includes items for Microsoft Azure subscriptions (**MS-AZR-0145P**) and Azure plans</span></span><br/><br/><span data-ttu-id="0377d-141">**OnlineServices,** die alle onlineservice-items bevat, met inbegrip van commerciële marketplace-producten</span><span class="sxs-lookup"><span data-stu-id="0377d-141">**OnlineServices**, which includes all online service items, including commercial marketplace products</span></span><br/><br/><span data-ttu-id="0377d-142">**Software**, die alle software-items bevat</span><span class="sxs-lookup"><span data-stu-id="0377d-142">**Software**, which  includes all software items</span></span><br/><br/><span data-ttu-id="0377d-143">**SoftwareSUSELinux,** dat alle software-SUSE Linux-items bevat</span><span class="sxs-lookup"><span data-stu-id="0377d-143">**SoftwareSUSELinux**, which includes all software SUSE Linux items</span></span><br/><br/><span data-ttu-id="0377d-144">**SoftwarePerpetual,** dat alle permanente software-items bevat</span><span class="sxs-lookup"><span data-stu-id="0377d-144">**SoftwarePerpetual**, which includes all perpetual software items</span></span><br/><br/><span data-ttu-id="0377d-145">**SoftwareAbonnementen,** die alle softwareabonnementitems bevat</span><span class="sxs-lookup"><span data-stu-id="0377d-145">**SoftwareSubscriptions**, which includes all software subscription items</span></span>  |

### <a name="request-header"></a><span data-ttu-id="0377d-146">Aanvraagheader</span><span class="sxs-lookup"><span data-stu-id="0377d-146">Request header</span></span>

<span data-ttu-id="0377d-147">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="0377d-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="0377d-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="0377d-148">Request body</span></span>

<span data-ttu-id="0377d-149">Geen.</span><span class="sxs-lookup"><span data-stu-id="0377d-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="0377d-150">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="0377d-150">Request example</span></span>

<span data-ttu-id="0377d-151">Vraag een lijst aan met producten op basis van Azure-gebruik die beschikbaar zijn voor een bepaalde klant.</span><span class="sxs-lookup"><span data-stu-id="0377d-151">Request for a list of Azure usage-based products available to a given customer.</span></span> <span data-ttu-id="0377d-152">Producten voor zowel Microsoft Azure (MS-AZR-0145P) als Azure-abonnementen worden geretourneerd voor klanten in de openbare cloud:</span><span class="sxs-lookup"><span data-stu-id="0377d-152">Products for both Microsoft Azure (MS-AZR-0145P) and Azure plans will be returned for customers in public cloud:</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products?targetView=MicrosoftAzure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 83643f5e-5dfd-4375-88ed-054412460dc8
MS-CorrelationId: b1939cb2-e83d-4fb0-989f-514fb741b734
```

## <a name="rest-response"></a><span data-ttu-id="0377d-153">Rest-antwoord</span><span class="sxs-lookup"><span data-stu-id="0377d-153">Rest response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0377d-154">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="0377d-154">Response success and error codes</span></span>

<span data-ttu-id="0377d-155">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="0377d-155">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0377d-156">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="0377d-156">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0377d-157">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="0377d-157">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="0377d-158">Deze methode retourneert de volgende foutcodes:</span><span class="sxs-lookup"><span data-stu-id="0377d-158">This method returns the following error codes:</span></span>

| <span data-ttu-id="0377d-159">HTTP-statuscode</span><span class="sxs-lookup"><span data-stu-id="0377d-159">HTTP Status Code</span></span> | <span data-ttu-id="0377d-160">Foutcode</span><span class="sxs-lookup"><span data-stu-id="0377d-160">Error code</span></span>   | <span data-ttu-id="0377d-161">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0377d-161">Description</span></span>                     |
|------------------|--------------|---------------------------------|
| <span data-ttu-id="0377d-162">403</span><span class="sxs-lookup"><span data-stu-id="0377d-162">403</span></span> | <span data-ttu-id="0377d-163">400036</span><span class="sxs-lookup"><span data-stu-id="0377d-163">400036</span></span> | <span data-ttu-id="0377d-164">Toegang tot de aangevraagde targetView is niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="0377d-164">Access to the requested targetView is not allowed.</span></span> |

### <a name="response-example"></a><span data-ttu-id="0377d-165">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="0377d-165">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1909
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cad955c2-8efc-47fe-b112-548ff002ba18
MS-RequestId: ae7288e2-2673-4ad4-8c12-7aad818d5949

{
    "totalCount": 2,
    "items": [
        {
            "id": "MS-AZR-0145P",
            "productId": "9DEA7946-EC2C-441E-9FFD-E3B275F7E838",
            "title": "Microsoft Azure",
            "description": "Azure Cloud Solution Provider offer for Partner and Resellers",
            "minimumQuantity": 1,
            "maximumQuantity": 1,
            "isTrial": false,
            "supportedBillingCycles": [
                "monthly"
            ],
            "purchasePrerequisites": [
                "MicrosoftCloudAgreement"
            ],
            "actions": [
                "Refund"
            ],
            "dynamicAttributes": {
                "isMicrosoftProduct": true,
                "billingType": "usage",
                "category": "Enterprise",
                "isAddon": false,
                "prerequisiteSkus": [],
                "rank": 1413,
                "hasAddOns": false,
                "isAutoRenewable": false,
                "upgradeTargetOffers": null,
                "conversionTargetOffers": [],
                "unitType": "Usage-based",
                "limitUnitOfMeasure": "None",
                "limit": 0,
                "reselleeQualifications": [],
                "resellerQualifications": []
            },
            "links": {
                "availabilities": {
                    "uri": "/products/9DEA7946-EC2C-441E-9FFD-E3B275F7E838/skus/MS-AZR-0145P/availabilities?country=US&targetSegment=Commercial",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/products/9DEA7946-EC2C-441E-9FFD-E3B275F7E838/skus/MS-AZR-0145P?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        },
        {
            "id": "0001",
            "productId": "DZH318Z0BPS6",
            "title": "Microsoft Azure plan",
            "description": "Microsoft Azure plan (MS-AZR-0017G)",
            "minimumQuantity": 1,
            "maximumQuantity": 1,
            "isTrial": false,
            "supportedBillingCycles": [
                "one_time"
            ],
            "purchasePrerequisites": [
                "MicrosoftCustomerAgreement"
            ],
            "inventoryVariables": [],
            "provisioningVariables": [],
            "actions": [
                "Refund"
            ],
            "dynamicAttributes": {
                "isMicrosoftProduct": true,
                "pilotProgram": "modernazurepilot"
            },
            "links": {
                "availabilities": {
                    "uri": "/products/DZH318Z0BPS6/skus/0001/availabilities?country=US&targetSegment=Commercial",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/products/DZH318Z0BPS6/skus/0001?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/e2a0c0f3-0f74-4d1c-808c-dfa511481913/products/all/skus?targetView=MicrosoftAzure&targetSegment=Commercial",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
