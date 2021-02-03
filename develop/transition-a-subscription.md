---
title: Een abonnement overdragen
description: Hiermee wordt het abonnement van een klant bijgewerkt naar een opgegeven doel abonnement.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9b757eee8bc65c16b5c65221a4c14b6c0fd6369e
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767240"
---
# <a name="transition-a-subscription"></a><span data-ttu-id="28fb7-103">Een abonnement overdragen</span><span class="sxs-lookup"><span data-stu-id="28fb7-103">Transition a subscription</span></span>

<span data-ttu-id="28fb7-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="28fb7-104">**Applies To**</span></span>

- <span data-ttu-id="28fb7-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="28fb7-105">Partner Center</span></span>
- <span data-ttu-id="28fb7-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="28fb7-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="28fb7-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="28fb7-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="28fb7-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="28fb7-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="28fb7-109">Hiermee wordt het abonnement van een klant bijgewerkt naar een opgegeven doel abonnement.</span><span class="sxs-lookup"><span data-stu-id="28fb7-109">Upgrades a customer's subscription to a specified target subscription.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28fb7-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="28fb7-110">Prerequisites</span></span>

- <span data-ttu-id="28fb7-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="28fb7-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="28fb7-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="28fb7-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="28fb7-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="28fb7-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="28fb7-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="28fb7-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="28fb7-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="28fb7-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="28fb7-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="28fb7-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="28fb7-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="28fb7-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="28fb7-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="28fb7-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="28fb7-119">Twee abonnement-Id's, één voor het eerste abonnement en één voor het doel abonnement.</span><span class="sxs-lookup"><span data-stu-id="28fb7-119">Two subscription IDs, one for the initial subscription and one for the target subscription.</span></span>

## <a name="c"></a><span data-ttu-id="28fb7-120">C\#</span><span class="sxs-lookup"><span data-stu-id="28fb7-120">C\#</span></span>

<span data-ttu-id="28fb7-121">Als u het abonnement van een klant wilt bijwerken, moet u eerst [dat customer's-abonnement ophalen](get-a-subscription-by-id.md).</span><span class="sxs-lookup"><span data-stu-id="28fb7-121">To upgrade a customer's subscription, first [get that's customer's subscription](get-a-subscription-by-id.md).</span></span> <span data-ttu-id="28fb7-122">Vervolgens moet u een lijst met upgrades voor dat abonnement verkrijgen door de eigenschap **upgrades** aan te roepen, gevolgd door de methoden **Get ()** of **GetAsync ()** .</span><span class="sxs-lookup"><span data-stu-id="28fb7-122">Then, obtain a list of upgrades for that subscription by calling the **Upgrades** property followed by the **Get()** or **GetAsync()** methods.</span></span> <span data-ttu-id="28fb7-123">Kies een doel upgrade van die lijst met upgrades en roep vervolgens de eigenschap **upgrades** aan van het eerste abonnement, gevolgd door de methode **Create ()** .</span><span class="sxs-lookup"><span data-stu-id="28fb7-123">Choose a target upgrade from that list of upgrades, and then call the **Upgrades** property of the initial subscription, followed by the **Create()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string subscriptionIdForUpgrade;
// Upgrade targetOffer;

UpgradeResult upgradeResult = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(subscriptionIdForUpgrade).Upgrades.Create(targetOffer);
```

<span data-ttu-id="28fb7-124">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="28fb7-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="28fb7-125">**Project**: PartnerSDK. FeatureSamples- **klasse**: UpgradeSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="28fb7-125">**Project**: PartnerSDK.FeatureSamples **Class**: UpgradeSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="28fb7-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="28fb7-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="28fb7-127">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="28fb7-127">Request syntax</span></span>

| <span data-ttu-id="28fb7-128">Methode</span><span class="sxs-lookup"><span data-stu-id="28fb7-128">Method</span></span>   | <span data-ttu-id="28fb7-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="28fb7-129">Request URI</span></span>                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="28fb7-130">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="28fb7-130">**GET**</span></span>  | <span data-ttu-id="28fb7-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{id-for-Subscription}/upgrades http/1.1</span><span class="sxs-lookup"><span data-stu-id="28fb7-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/upgrades HTTP/1.1</span></span> |
| <span data-ttu-id="28fb7-132">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="28fb7-132">**POST**</span></span> | <span data-ttu-id="28fb7-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{id-for-target}/upgrades http/1.1</span><span class="sxs-lookup"><span data-stu-id="28fb7-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-target}/upgrades HTTP/1.1</span></span>       |

### <a name="uri-parameter"></a><span data-ttu-id="28fb7-134">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="28fb7-134">URI parameter</span></span>

<span data-ttu-id="28fb7-135">Gebruik de volgende query parameter om het abonnement te overzetten.</span><span class="sxs-lookup"><span data-stu-id="28fb7-135">Use the following query parameter to transition the subscription.</span></span>

| <span data-ttu-id="28fb7-136">Naam</span><span class="sxs-lookup"><span data-stu-id="28fb7-136">Name</span></span>                    | <span data-ttu-id="28fb7-137">Type</span><span class="sxs-lookup"><span data-stu-id="28fb7-137">Type</span></span>     | <span data-ttu-id="28fb7-138">Vereist</span><span class="sxs-lookup"><span data-stu-id="28fb7-138">Required</span></span> | <span data-ttu-id="28fb7-139">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="28fb7-139">Description</span></span>                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| <span data-ttu-id="28fb7-140">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="28fb7-140">**customer-tenant-id**</span></span>  | <span data-ttu-id="28fb7-141">**guid**</span><span class="sxs-lookup"><span data-stu-id="28fb7-141">**guid**</span></span> | <span data-ttu-id="28fb7-142">J</span><span class="sxs-lookup"><span data-stu-id="28fb7-142">Y</span></span>        | <span data-ttu-id="28fb7-143">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="28fb7-143">A GUID corresponding to the customer.</span></span>             |
| <span data-ttu-id="28fb7-144">**id voor abonnement**</span><span class="sxs-lookup"><span data-stu-id="28fb7-144">**id-for-subscription**</span></span> | <span data-ttu-id="28fb7-145">**guid**</span><span class="sxs-lookup"><span data-stu-id="28fb7-145">**guid**</span></span> | <span data-ttu-id="28fb7-146">J</span><span class="sxs-lookup"><span data-stu-id="28fb7-146">Y</span></span>        | <span data-ttu-id="28fb7-147">Een GUID die overeenkomt met het eerste abonnement.</span><span class="sxs-lookup"><span data-stu-id="28fb7-147">A GUID corresponding to the initial subscription.</span></span> |
| <span data-ttu-id="28fb7-148">**id voor doel**</span><span class="sxs-lookup"><span data-stu-id="28fb7-148">**id-for-target**</span></span>       | <span data-ttu-id="28fb7-149">**guid**</span><span class="sxs-lookup"><span data-stu-id="28fb7-149">**guid**</span></span> | <span data-ttu-id="28fb7-150">J</span><span class="sxs-lookup"><span data-stu-id="28fb7-150">Y</span></span>        | <span data-ttu-id="28fb7-151">Een GUID die overeenkomt met het doel abonnement.</span><span class="sxs-lookup"><span data-stu-id="28fb7-151">A GUID corresponding to the target subscription.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="28fb7-152">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="28fb7-152">Request headers</span></span>

<span data-ttu-id="28fb7-153">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="28fb7-153">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="28fb7-154">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="28fb7-154">Request body</span></span>

<span data-ttu-id="28fb7-155">Geen</span><span class="sxs-lookup"><span data-stu-id="28fb7-155">None</span></span>

### <a name="request-example"></a><span data-ttu-id="28fb7-156">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="28fb7-156">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/upgrades HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US

POST https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{id-for-target}/upgrades HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 750fd5ea-904b-4c3e-b476-60d0feacab0d
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
Content-Type: application/json
Content-Length: 1098
Expect: 100-continue

{
    "TargetOffer":{
        "Id":"796B6B5F-613C-4E24-A17C-EBA730D49C02",
        "Name":"Office 365 Enterprise E3",
        "Description":"The best plan for businesses that need full productivity, communication and collaboration tools with the familiar Office suite, including Office Online.",
        "MinimumQuantity":1,
        "MaximumQuantity":10000000,
        "Rank":61,
        "Uri":"/3c95518e-8c37-41e3-9627-0ca339200f53/Offers/796B6B5F-613C-4E24-A17C-EBA730D49C02",
        "Locale":"en-us",
        "Country":"US",
        "Category":{
            "Id":"Enterprise_Key",
            "Name":"Enterprise",
            "Rank":20,
            "Locale":"en-us",
            "Country":"US",
            "Attributes":{
                "ObjectType":"OfferCategory"
            }
        },
        "PrerequisiteOffers":[],
        "IsAddOn":false,
        "IsAvailableForPurchase":true,
        "Billing":"license",
        "IsAutoRenewable":true,
        "Product":{
            "Id":"6fd2c87f-b296-42f0-b197-1e91e994b900",
            "Name":"Office 365 Enterprise E3",
            "Unit":"Licenses"
        },
        "UnitType":"Licenses",
        "Links":{
            "LearnMore":{
                "Uri":"http://g.microsoftonline.com/0BXPS00en/1015",
                "Method":"GET",
                "Headers":[]
            }
        }
        "Attributes":{
            "ObjectType":"Offer"
        }
    },
    "UpgradeType":1,
    "IsEligible":true,
    "Quantity":1,
    "UpgradeErrors":[],
    "Attributes":{
        "ObjectType":"Upgrade"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="28fb7-157">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="28fb7-157">REST response</span></span>

<span data-ttu-id="28fb7-158">Als dit lukt, retourneert deze methode een bron van een **upgrade** resultaat in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="28fb7-158">If successful, this method returns an **Upgrade** result resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="28fb7-159">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="28fb7-159">Response success and error codes</span></span>

<span data-ttu-id="28fb7-160">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="28fb7-160">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="28fb7-161">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="28fb7-161">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="28fb7-162">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="28fb7-162">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="28fb7-163">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="28fb7-163">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 29 Jan 2016 20:42:26 GMT

{
    "totalCount": 1,
    "items": [{
        "targetOffer": {
            "id": "91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "name": "Office 365 Enterprise E1",
            "description": "For businesses that need communication and collaboration tools and the ability to read and do lightweight editing of documents with Office Online.",
            "minimumQuantity": 1,
            "maximumQuantity": 10000000,
            "rank": 48,
            "uri": "/3c95518e-8c37-41e3-9627-0ca339200f53/Offers/91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "locale": "en-us",
            "country": "US",
            "category": {
                "id": "Enterprise_Key",
                "name": "Enterprise",
                "rank": 20,
                "locale": "en-us",
                "country": "US",
                "attributes": {
                    "objectType": "OfferCategory"
                }
            },
            "prerequisiteOffers": [],
            "isAddOn": false,
            "isAvailableForPurchase": true,
            "billing": "license",
            "isAutoRenewable": true,
            "isInternal": false,
            "conversionTargetOffers": [],
            "partnerQualifications": ["none"],
            "product": {
                "id": "18181a46-0d4e-45cd-891e-60aabd171b4e",
                "name": "Office 365 Enterprise E1",
                "unit": "Licenses"
            },
            "unitType": "Licenses",
            "links": {
                "learnMore": {
                    "uri": "http://g.microsoftonline.com/0BXPS00en/1013",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/offers/91FD106F-4B2C-4938-95AC-F54F74E9A239?country=US",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Offer"
            }
        },
        "upgradeType": "upgrade_only",
        "isEligible": false,
        "quantity": 1,
        "upgradeErrors": [{
            "code": 2,
            "description": "Subscription cannot be upgraded because the source subscription state is not active.  Additional Details contains the current source subscription state.",
            "attributes": {
                "objectType": "UpgradeError"
            }
        }],
        "attributes": {
            "objectType": "Upgrade"
        }
    }],
    "attributes": {
        "objectType": "Collection"
    }
}

HTTP/1.1 200 OK
Content-Length: 448
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 750fd5ea-904b-4c3e-b476-60d0feacab0d
MS-CV: RnK86LBbDkWP/w2R.0
MS-ServerId: 102031201
Date: Fri, 29 Jan 2016 20:44:21 GMT

{
    "sourceSubscriptionId":"896a2862-67e2-4f3d-bb3f-c50c42b5fad8",
    "targetSubscriptionId":"2add8a55-454a-4ae5-a4c9-5107dc6e9768",
    "upgradeType":1,
    "upgradeErrors":[],
    "licenseErrors":[],
    "attributes":{
        "objectType":"UpgradeResult"
    }
}
```
