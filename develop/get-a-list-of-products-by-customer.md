---
title: Een lijst met producten ophalen (per klant)
description: U kunt een klant-id gebruiken om een verzameling van producten per klant op te halen.
ms.assetid: ''
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 98a099c458535123f675c6452db950b087b9f387
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767411"
---
# <a name="get-a-list-of-products-by-customer"></a><span data-ttu-id="6501a-103">Een lijst met producten ophalen (per klant)</span><span class="sxs-lookup"><span data-stu-id="6501a-103">Get a list of products (by customer)</span></span>

<span data-ttu-id="6501a-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="6501a-104">**Applies to:**</span></span>

- <span data-ttu-id="6501a-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="6501a-105">Partner Center</span></span>
- <span data-ttu-id="6501a-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="6501a-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="6501a-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="6501a-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="6501a-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6501a-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6501a-109">U kunt de volgende methoden gebruiken om een verzameling producten voor een bestaande klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="6501a-109">You can use the following methods to get a collection of products for an existing customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6501a-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6501a-110">Prerequisites</span></span>

- <span data-ttu-id="6501a-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6501a-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6501a-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="6501a-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="6501a-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6501a-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="6501a-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="6501a-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="6501a-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="6501a-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="6501a-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="6501a-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="6501a-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="6501a-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="6501a-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6501a-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="6501a-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="6501a-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6501a-120">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6501a-120">Request syntax</span></span>

| <span data-ttu-id="6501a-121">Methode</span><span class="sxs-lookup"><span data-stu-id="6501a-121">Method</span></span> | <span data-ttu-id="6501a-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="6501a-122">Request URI</span></span>                                                                                                              |
|--------|--------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6501a-123">POST</span><span class="sxs-lookup"><span data-stu-id="6501a-123">POST</span></span>   | <span data-ttu-id="6501a-124">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Products? targetView = {targetView} http/1.1</span><span class="sxs-lookup"><span data-stu-id="6501a-124">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products?targetView={targetView} HTTP/1.1</span></span> |

#### <a name="request-uri-parameters"></a><span data-ttu-id="6501a-125">URI-para meters aanvragen</span><span class="sxs-lookup"><span data-stu-id="6501a-125">Request URI parameters</span></span>

| <span data-ttu-id="6501a-126">Naam</span><span class="sxs-lookup"><span data-stu-id="6501a-126">Name</span></span>               | <span data-ttu-id="6501a-127">Type</span><span class="sxs-lookup"><span data-stu-id="6501a-127">Type</span></span> | <span data-ttu-id="6501a-128">Vereist</span><span class="sxs-lookup"><span data-stu-id="6501a-128">Required</span></span> | <span data-ttu-id="6501a-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6501a-129">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="6501a-130">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="6501a-130">**customer-tenant-id**</span></span> | <span data-ttu-id="6501a-131">GUID</span><span class="sxs-lookup"><span data-stu-id="6501a-131">GUID</span></span> | <span data-ttu-id="6501a-132">Yes</span><span class="sxs-lookup"><span data-stu-id="6501a-132">Yes</span></span> | <span data-ttu-id="6501a-133">De waarde is een **klant-Tenant-id** van de GUID-indeling, een id waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="6501a-133">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |
| <span data-ttu-id="6501a-134">**targetView**</span><span class="sxs-lookup"><span data-stu-id="6501a-134">**targetView**</span></span> | <span data-ttu-id="6501a-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6501a-135">string</span></span> | <span data-ttu-id="6501a-136">Yes</span><span class="sxs-lookup"><span data-stu-id="6501a-136">Yes</span></span> | <span data-ttu-id="6501a-137">Hiermee wordt de doel weergave van de catalogus geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="6501a-137">Identifies the target view of the catalog.</span></span> <span data-ttu-id="6501a-138">De ondersteunde waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="6501a-138">The supported values are:</span></span> <br/><br/><span data-ttu-id="6501a-139">**Azure**, inclusief alle Azure-items</span><span class="sxs-lookup"><span data-stu-id="6501a-139">**Azure**, which includes all Azure items</span></span><br/><br/><span data-ttu-id="6501a-140">**AzureReservations**, inclusief alle Azure-reserverings items</span><span class="sxs-lookup"><span data-stu-id="6501a-140">**AzureReservations**, which includes all Azure reservation items</span></span><br/><br/><span data-ttu-id="6501a-141">**AzureReservationsVM**, dat alle reserve ringen items van virtuele machines (VM) omvat</span><span class="sxs-lookup"><span data-stu-id="6501a-141">**AzureReservationsVM**, which includes all virtual machine (VM) reservation items</span></span><br/><br/><span data-ttu-id="6501a-142">**AzureReservationsSQL**, inclusief alle SQL-reserverings items</span><span class="sxs-lookup"><span data-stu-id="6501a-142">**AzureReservationsSQL**, which includes all SQL reservation items</span></span><br/><br/><span data-ttu-id="6501a-143">**AzureReservationsCosmosDb**, met alle reserverings items voor de Cosmos-data base</span><span class="sxs-lookup"><span data-stu-id="6501a-143">**AzureReservationsCosmosDb**, which includes all Cosmos database reservation items</span></span><br/><br/><span data-ttu-id="6501a-144">**MicrosoftAzure**, die items bevat voor Microsoft Azure-abonnementen (**MS-AZR-0145P**) en Azure-plannen</span><span class="sxs-lookup"><span data-stu-id="6501a-144">**MicrosoftAzure**, which includes items for Microsoft Azure subscriptions (**MS-AZR-0145P**) and Azure plans</span></span><br/><br/><span data-ttu-id="6501a-145">**OnlineServices**, dat alle online service-items omvat, inclusief commerciële Marketplace-Producten</span><span class="sxs-lookup"><span data-stu-id="6501a-145">**OnlineServices**, which  includes all online service items, including commercial marketplace products</span></span><br/><br/><span data-ttu-id="6501a-146">**Software**, inclusief alle software-items</span><span class="sxs-lookup"><span data-stu-id="6501a-146">**Software**, which  includes all software items</span></span><br/><br/><span data-ttu-id="6501a-147">**SoftwareSUSELinux**, dat alle software SuSE Linux-items omvat</span><span class="sxs-lookup"><span data-stu-id="6501a-147">**SoftwareSUSELinux**, which includes all software SUSE Linux items</span></span><br/><br/><span data-ttu-id="6501a-148">**SoftwarePerpetual**, inclusief alle permanente software-items</span><span class="sxs-lookup"><span data-stu-id="6501a-148">**SoftwarePerpetual**, which includes all perpetual software items</span></span><br/><br/><span data-ttu-id="6501a-149">**SoftwareSubscriptions**, inclusief alle software-abonnements items</span><span class="sxs-lookup"><span data-stu-id="6501a-149">**SoftwareSubscriptions**, which includes all software subscription items</span></span>  |

### <a name="request-header"></a><span data-ttu-id="6501a-150">Aanvraagheader</span><span class="sxs-lookup"><span data-stu-id="6501a-150">Request header</span></span>

<span data-ttu-id="6501a-151">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="6501a-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6501a-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="6501a-152">Request body</span></span>

<span data-ttu-id="6501a-153">Geen.</span><span class="sxs-lookup"><span data-stu-id="6501a-153">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6501a-154">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6501a-154">Request example</span></span>

<span data-ttu-id="6501a-155">Aanvraag voor een lijst met op Azure-gebruik gebaseerde producten die beschikbaar zijn voor een bepaalde klant.</span><span class="sxs-lookup"><span data-stu-id="6501a-155">Request for a list of Azure usage-based products available to a given customer.</span></span> <span data-ttu-id="6501a-156">Producten voor zowel Microsoft Azure (MS-AZR-0145P) als Azure-abonnementen worden geretourneerd voor klanten in een open bare Cloud:</span><span class="sxs-lookup"><span data-stu-id="6501a-156">Products for both Microsoft Azure (MS-AZR-0145P) and Azure plans will be returned for customers in public cloud:</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products?targetView=MicrosoftAzure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 83643f5e-5dfd-4375-88ed-054412460dc8
MS-CorrelationId: b1939cb2-e83d-4fb0-989f-514fb741b734
```

## <a name="rest-response"></a><span data-ttu-id="6501a-157">Rest-antwoord</span><span class="sxs-lookup"><span data-stu-id="6501a-157">Rest response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6501a-158">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="6501a-158">Response success and error codes</span></span>

<span data-ttu-id="6501a-159">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="6501a-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6501a-160">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="6501a-160">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6501a-161">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="6501a-161">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="6501a-162">Deze methode retourneert de volgende fout codes:</span><span class="sxs-lookup"><span data-stu-id="6501a-162">This method returns the following error codes:</span></span>

| <span data-ttu-id="6501a-163">HTTP-status code</span><span class="sxs-lookup"><span data-stu-id="6501a-163">HTTP Status Code</span></span> | <span data-ttu-id="6501a-164">Foutcode</span><span class="sxs-lookup"><span data-stu-id="6501a-164">Error code</span></span>   | <span data-ttu-id="6501a-165">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6501a-165">Description</span></span>                     |
|------------------|--------------|---------------------------------|
| <span data-ttu-id="6501a-166">403</span><span class="sxs-lookup"><span data-stu-id="6501a-166">403</span></span> | <span data-ttu-id="6501a-167">400036</span><span class="sxs-lookup"><span data-stu-id="6501a-167">400036</span></span> | <span data-ttu-id="6501a-168">Toegang tot de aangevraagde targetView is niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6501a-168">Access to the requested targetView is not allowed.</span></span> |

### <a name="response-example"></a><span data-ttu-id="6501a-169">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="6501a-169">Response example</span></span>

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
