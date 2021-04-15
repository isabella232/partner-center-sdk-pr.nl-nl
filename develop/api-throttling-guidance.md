---
title: Richtlijnen voor API-beperking
description: Voor partners die Partner Center API's aanroepen, moet u weten welke API's worden beïnvloed door microsoft API-beperking en best practices om beperking te voorkomen of beter af te handelen.
ms.date: 04/14/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: vijvala
ms.author: vijvala
ms.openlocfilehash: ab1138e19e06111299ab43ea13a6f033274aaa5d
ms.sourcegitcommit: 3c3a21e73aaadf3023cf4c13b09809ceae5f027a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/14/2021
ms.locfileid: "107496141"
---
# <a name="api-throttling-guidance-for-partners-calling-partner-center-apis"></a><span data-ttu-id="d7351-103">Richtlijnen voor API-beperking voor partners die api'Partner Center aanroepen</span><span class="sxs-lookup"><span data-stu-id="d7351-103">API throttling guidance for partners calling Partner Center APIs</span></span> 

<span data-ttu-id="d7351-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="d7351-104">**Applies to**</span></span>

- <span data-ttu-id="d7351-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="d7351-105">Partner Center</span></span>

<span data-ttu-id="d7351-106">Microsoft implementeert API-beperking om binnen een tijdspanne consistentere prestaties mogelijk te maken voor partners die de api'Partner Center aanroepen.</span><span class="sxs-lookup"><span data-stu-id="d7351-106">Microsoft is implementing API throttling to allow more consistent performance within a time span for partners calling the Partner Center APIs.</span></span> <span data-ttu-id="d7351-107">Beperking beperkt het aantal aanvragen voor een service in een tijdsspanne om te voorkomen dat resources te veel worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d7351-107">Throttling limits the number of requests to a service in a time span to prevent overuse of resources.</span></span> <span data-ttu-id="d7351-108">Hoewel Partner Center is ontworpen voor het verwerken van een groot aantal aanvragen, helpt beperking bij een groot aantal aanvragen van enkele partners om optimale prestaties en betrouwbaarheid voor alle partners te behouden.</span><span class="sxs-lookup"><span data-stu-id="d7351-108">While Partner Center is designed to handle a high volume of requests, if an overwhelming number of requests occur by few partners, throttling helps maintain optimal performance and reliability for all partners.</span></span>  

<span data-ttu-id="d7351-109">Beperkingslimieten variëren afhankelijk van het scenario.</span><span class="sxs-lookup"><span data-stu-id="d7351-109">Throttling limits vary based on the scenario.</span></span> <span data-ttu-id="d7351-110">Als u bijvoorbeeld een groot aantal schrijfvolumes gebruikt, is de kans op bandbreedtebeperking groter dan wanneer u alleen lees- en schrijf- of schrijfvolumes gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d7351-110">For example, if you are performing a large volume of writes, the possibility for throttling is higher than if you are only performing reads.</span></span>

## <a name="what-happens-when-throttling-occurs"></a><span data-ttu-id="d7351-111">Wat gebeurt er wanneer beperking optreedt?</span><span class="sxs-lookup"><span data-stu-id="d7351-111">What happens when throttling occurs?</span></span> 

<span data-ttu-id="d7351-112">Wanneer een drempelwaarde voor bandbreedtebeperking wordt overschreden, Partner Center verdere aanvragen van die client voor een bepaalde periode beperkt.</span><span class="sxs-lookup"><span data-stu-id="d7351-112">When a throttling threshold is exceeded, Partner Center limits any further requests from that client for a period of time.</span></span> <span data-ttu-id="d7351-113">Beperkingsgedrag is afhankelijk van het type en het aantal aanvragen.</span><span class="sxs-lookup"><span data-stu-id="d7351-113">Throttling behavior depends on the type and number of requests.</span></span>   

### <a name="common-throttling-scenarios"></a><span data-ttu-id="d7351-114">Veelvoorkomende beperkingsscenario's</span><span class="sxs-lookup"><span data-stu-id="d7351-114">Common throttling scenarios</span></span> 

<span data-ttu-id="d7351-115">De meest voorkomende oorzaken van beperking van clients zijn:</span><span class="sxs-lookup"><span data-stu-id="d7351-115">The most common causes of throttling of clients include:</span></span> 

- <span data-ttu-id="d7351-116">Een groot aantal aanvragen voor een **API per partner-tenant-id:** voor sommige Partner Center-API's wordt beperking bepaald door de tenant-id van de partner. Te veel aanroepen naar deze API's op dezelfde tenant-id van de partner leiden ertoe dat de drempelwaarde voor beperking wordt overschreden.</span><span class="sxs-lookup"><span data-stu-id="d7351-116">**A large number of requests for an API per Partner Tenant ID**: for some Partner Center APIs, throttling is determined by Partner Tenant ID, too many calls to those APIs on the same Partner Tenant ID will result in exceeding the throttling threshold.</span></span>  

- <span data-ttu-id="d7351-117">Een groot aantal aanvragen voor een **API per partner-tenant-id per** tenant-id van de klant: voor andere API's wordt de beperking bepaald door de combinatie partner-tenant-id/tenant-id van de klant; In dergelijke gevallen leidt het maken van te veel aanroepen op dezelfde tenant-id van de klant tot beperking, terwijl aanroepen tegen andere klanten kunnen slagen.</span><span class="sxs-lookup"><span data-stu-id="d7351-117">**A large number of requests for an API per Partner Tenant ID per Customer Tenant ID**: for other APIs, throttling is determined by Partner Tenant ID/Customer Tenant ID combination; in those cases, making too many calls against the same customer tenant ID will result in throttling - while calls against other customers may succeed.</span></span>

## <a name="best-practices-to-avoid-throttling"></a><span data-ttu-id="d7351-118">Best practices om beperking te voorkomen</span><span class="sxs-lookup"><span data-stu-id="d7351-118">Best practices to avoid throttling</span></span> 
 
<span data-ttu-id="d7351-119">Programmeerprocedures zoals het continu peilen van een resource om te controleren op updates en het regelmatig scannen van resourceverzamelingen om te controleren of er nieuwe of verwijderde resources zijn, leiden waarschijnlijk tot beperking en zullen de algehele prestaties verslechteren.</span><span class="sxs-lookup"><span data-stu-id="d7351-119">Programming practices such as continuously polling a resource to check for updates and regularly scanning resource collections to check for new or deleted resources are more likely to lead to throttling and will degrade overall performance.</span></span> <span data-ttu-id="d7351-120">Gelijktijdige API-aanroepen kunnen leiden tot een groot aantal aanvragen per eenheidstijd, waardoor aanvragen ook worden beperkt.</span><span class="sxs-lookup"><span data-stu-id="d7351-120">Concurrent API calls may lead to high number of requests per unit time, which will also cause requests to be throttled.</span></span> <span data-ttu-id="d7351-121">U moet in plaats daarvan gebruikmaken van meldingen over het bijhouden en wijzigen van wijzigen.</span><span class="sxs-lookup"><span data-stu-id="d7351-121">You should instead leverage change tracking and change notifications.</span></span> <span data-ttu-id="d7351-122">Daarnaast moet u activiteitenlogboeken kunnen gebruiken voor het detecteren van wijzigingen. Zie Partner Center [activiteitenlogboeken](get-a-record-of-partner-center-activity-by-user.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d7351-122">Additionally, you should be able to leverage activity logs for detecting changes, see [Partner Center activity logs](get-a-record-of-partner-center-activity-by-user.md) for more information.</span></span>  <span data-ttu-id="d7351-123">We raden partners ten zeerste aan de API voor activiteitenlogboek te gebruiken voor meer efficiëntie en om bandbreedtebeperking te voorkomen.</span><span class="sxs-lookup"><span data-stu-id="d7351-123">We highly recommend partners to consider using the activity log API for more efficiency and to avoid throttling.</span></span> <span data-ttu-id="d7351-124">Zie ook het voorbeeld van het gebruik van activiteitenlogboeken hieronder.</span><span class="sxs-lookup"><span data-stu-id="d7351-124">See also the example of using activity logs, below.</span></span>

## <a name="best-practices-to-handle-throttling"></a><span data-ttu-id="d7351-125">Best practices voor het afhandelen van beperking</span><span class="sxs-lookup"><span data-stu-id="d7351-125">Best practices to handle throttling</span></span>

<span data-ttu-id="d7351-126">Hier volgen de best practices voor het afhandelen van bandbreedtebeperking:</span><span class="sxs-lookup"><span data-stu-id="d7351-126">The following are best practices for handling throttling:</span></span> 

- <span data-ttu-id="d7351-127">Verminder de mate van parallellelisme.</span><span class="sxs-lookup"><span data-stu-id="d7351-127">Reduce the degree of parallelism.</span></span> 
- <span data-ttu-id="d7351-128">Verminder de frequentie van aanroepen.</span><span class="sxs-lookup"><span data-stu-id="d7351-128">Reduce the frequency of calls.</span></span> 
- <span data-ttu-id="d7351-129">Vermijd onmiddellijke nieuwe nieuwe aanvragen omdat alle aanvragen worden opgeteld bij uw gebruikslimieten.</span><span class="sxs-lookup"><span data-stu-id="d7351-129">Avoid immediate retries because all requests accrue against your usage limits.</span></span> 

<span data-ttu-id="d7351-130">Gebruik de HTTP-foutcode 429 om beperking te detecteren wanneer u foutafhandeling implementeert.</span><span class="sxs-lookup"><span data-stu-id="d7351-130">When you implement error handling, use the HTTP error code 429 to detect throttling.</span></span> <span data-ttu-id="d7351-131">Het mislukte antwoord bevat de Retry-After antwoordheader.</span><span class="sxs-lookup"><span data-stu-id="d7351-131">The failed response includes the Retry-After response header.</span></span> <span data-ttu-id="d7351-132">Het uitschakelen van aanvragen met behulp van de vertraging na opnieuw proberen is de snelste manier om te herstellen van beperking.</span><span class="sxs-lookup"><span data-stu-id="d7351-132">Backing off requests using the Retry-after delay is the fastest way to recover from throttling.</span></span> 

<span data-ttu-id="d7351-133">Ga als volgt te werk als u de vertraging Opnieuw proberen na wilt gebruiken:</span><span class="sxs-lookup"><span data-stu-id="d7351-133">To use the Retry-after delay, do the following:</span></span> 

1. <span data-ttu-id="d7351-134">Wacht het aantal seconden dat is opgegeven in de Retry-After koptekst.</span><span class="sxs-lookup"><span data-stu-id="d7351-134">Wait the number of seconds specified in the Retry-After header.</span></span> 

2. <span data-ttu-id="d7351-135">De aanvraag opnieuw proberen.</span><span class="sxs-lookup"><span data-stu-id="d7351-135">Retry the request.</span></span>  

3. <span data-ttu-id="d7351-136">Als de aanvraag opnieuw mislukt met een 429-foutcode, wordt u nog steeds beperkt.</span><span class="sxs-lookup"><span data-stu-id="d7351-136">If the request fails again with a 429 error code, you are still being throttled.</span></span> <span data-ttu-id="d7351-137">Opnieuw proberen met exponentieel uitstel, gebruik de aanbevolen Retry-After vertraging en de aanvraag opnieuw totdat deze is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="d7351-137">Retry with Exponential backoff, use the recommended Retry-After delay and retry the request until it succeeds.</span></span>

4. <span data-ttu-id="d7351-138">Als u de SDK gebruikt, ontvangt u een uitzondering met statuscode 429 wanneer uw aanvraag wordt beperkt.</span><span class="sxs-lookup"><span data-stu-id="d7351-138">If you are using SDK you'll receive an exception with status code 429 when your request is being throttled.</span></span> <span data-ttu-id="d7351-139">Gebruik de eigenschap RetryAfter in de uitzondering en de aanvraag opnieuw nadat de tijd is verstreken.</span><span class="sxs-lookup"><span data-stu-id="d7351-139">Use the RetryAfter property in the exception and retry the request after the time is elapsed.</span></span>


## <a name="apis-currently-impacted-by-throttling"></a><span data-ttu-id="d7351-140">API's die momenteel worden beïnvloed door beperking</span><span class="sxs-lookup"><span data-stu-id="d7351-140">APIs currently impacted by throttling</span></span>

<span data-ttu-id="d7351-141">Op de lange termijn wordt elke Partner Center API die het eindpunt 'api.partnercenter.microsoft.com/' aanroept, beperkt.</span><span class="sxs-lookup"><span data-stu-id="d7351-141">In the long run, every single Partner Center API that calls the endpoint “api.partnercenter.microsoft.com/” will be throttled.</span></span> <span data-ttu-id="d7351-142">Op dit moment worden de beperkingslimieten alleen afgedwongen voor de HIERONDER vermelde API's.</span><span class="sxs-lookup"><span data-stu-id="d7351-142">Currently, the throttling limits are only enforced on the APIs listed below.</span></span> <span data-ttu-id="d7351-143">Partner Center verzamelt de telemetrie op elk van de API's en past de beperkingslimieten dynamisch aan.</span><span class="sxs-lookup"><span data-stu-id="d7351-143">Partner Center will be collecting the telemetry on each of the APIs and will dynamically adjust the throttling limits.</span></span> <span data-ttu-id="d7351-144">De volgende tabel bevat de API's waar beperking momenteel wordt afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="d7351-144">The following table lists the APIs where throttling is currently enforced.</span></span>  


|<span data-ttu-id="d7351-145">**Bewerking**</span><span class="sxs-lookup"><span data-stu-id="d7351-145">**Operation**</span></span>| <span data-ttu-id="d7351-146">**Documentatie voor Partnercentrum**</span><span class="sxs-lookup"><span data-stu-id="d7351-146">**Partner Center documentation**</span></span>|
|------------------------|----------------------------|
|<span data-ttu-id="d7351-147">{baseURL}/v1/customers/{customer_id}/orders</span><span class="sxs-lookup"><span data-stu-id="d7351-147">{baseURL}/v1/customers/{customer_id}/orders</span></span>|[<span data-ttu-id="d7351-148">een order maken</span><span class="sxs-lookup"><span data-stu-id="d7351-148">create an order</span></span>](create-an-order.md)|
|<span data-ttu-id="d7351-149">{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/upgrades</span><span class="sxs-lookup"><span data-stu-id="d7351-149">{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/upgrades</span></span>|[<span data-ttu-id="d7351-150">een abonnement overstappen</span><span class="sxs-lookup"><span data-stu-id="d7351-150">transition a subscription</span></span>](transition-a-subscription.md)|
|<span data-ttu-id="d7351-151">{baseURL}/v1/customers/{customer-tenant-id}/orders/{order-id}</span><span class="sxs-lookup"><span data-stu-id="d7351-151">{baseURL}/v1/customers/{customer-tenant-id}/orders/{order-id}</span></span>|[<span data-ttu-id="d7351-152">een invoegaanvoeging aanschaffen voor een abonnement</span><span class="sxs-lookup"><span data-stu-id="d7351-152">purchase an addon to a subscription</span></span>](purchase-an-add-on-to-a-subscription.md)|
|<span data-ttu-id="d7351-153">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}</span><span class="sxs-lookup"><span data-stu-id="d7351-153">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}</span></span>|[<span data-ttu-id="d7351-154">een winkelwagen maken</span><span class="sxs-lookup"><span data-stu-id="d7351-154">create a cart</span></span>](create-a-cart.md)|
|<span data-ttu-id="d7351-155">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}/checkout</span><span class="sxs-lookup"><span data-stu-id="d7351-155">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}/checkout</span></span>|[<span data-ttu-id="d7351-156">een winkelwagen uitchecken</span><span class="sxs-lookup"><span data-stu-id="d7351-156">checkout a cart</span></span>](checkout-a-cart.md)|
|<span data-ttu-id="d7351-157">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}</span><span class="sxs-lookup"><span data-stu-id="d7351-157">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}</span></span>|[<span data-ttu-id="d7351-158">een winkelwagen bijwerken</span><span class="sxs-lookup"><span data-stu-id="d7351-158">update a cart</span></span>](update-a-cart.md)|
|<span data-ttu-id="d7351-159">{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrations</span><span class="sxs-lookup"><span data-stu-id="d7351-159">{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrations</span></span>|[<span data-ttu-id="d7351-160">een abonnement registreren</span><span class="sxs-lookup"><span data-stu-id="d7351-160">register a subscription</span></span>](register-a-subscription.md)|
|<span data-ttu-id="d7351-161">{baseURL}/v1/productupgrades</span><span class="sxs-lookup"><span data-stu-id="d7351-161">{baseURL}/v1/productupgrades</span></span>|[<span data-ttu-id="d7351-162">entiteit productupgrade maken</span><span class="sxs-lookup"><span data-stu-id="d7351-162">create product upgrade entity</span></span>](create-product-upgrade-entity.md)|
|<span data-ttu-id="d7351-163">{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions</span><span class="sxs-lookup"><span data-stu-id="d7351-163">{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions</span></span> |[<span data-ttu-id="d7351-164">Een proefabonnement converteren naar betaald</span><span class="sxs-lookup"><span data-stu-id="d7351-164">convert a trial subscription to paid</span></span>](convert-a-trial-subscription-to-paid.md)|
|<span data-ttu-id="d7351-165">{baseURL}/v1/customers/{customer-tenant-id}</span><span class="sxs-lookup"><span data-stu-id="d7351-165">{baseURL}/v1/customers/{customer-tenant-id}</span></span>|[<span data-ttu-id="d7351-166">een klant op id krijgen</span><span class="sxs-lookup"><span data-stu-id="d7351-166">get a customer by id</span></span>](get-a-customer-by-id.md)|
|<span data-ttu-id="d7351-167">{baseURL}/v1/productUpgrades/geschiktheid</span><span class="sxs-lookup"><span data-stu-id="d7351-167">{baseURL}/v1/productUpgrades/eligibility</span></span>|[<span data-ttu-id="d7351-168">geschiktheid voor productupgrade krijgen</span><span class="sxs-lookup"><span data-stu-id="d7351-168">get eligibility for product upgrade</span></span>](get-eligibility-for-product-upgrade.md)|
|<span data-ttu-id="d7351-169">{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}</span><span class="sxs-lookup"><span data-stu-id="d7351-169">{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}</span></span> |[<span data-ttu-id="d7351-170">abonnement beheren</span><span class="sxs-lookup"><span data-stu-id="d7351-170">manage subscription</span></span>](manage-orders.md#manage-a-subscription)|
|<span data-ttu-id="d7351-171">{baseURL}/v1/customers/{customer_id}/subscriptions</span><span class="sxs-lookup"><span data-stu-id="d7351-171">{baseURL}/v1/customers/{customer_id}/subscriptions</span></span> |[<span data-ttu-id="d7351-172">get-all-of-a-customer-s-subscriptions</span><span class="sxs-lookup"><span data-stu-id="d7351-172">get-all-of-a-customer-s-subscriptions</span></span>](get-all-of-a-customer-s-subscriptions.md)|
|<span data-ttu-id="d7351-173">{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}</span><span class="sxs-lookup"><span data-stu-id="d7351-173">{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}</span></span>|[<span data-ttu-id="d7351-174">Een abonnement ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="d7351-174">Get a subscription by ID</span></span>](get-a-subscription-by-id.md)|
|<span data-ttu-id="d7351-175">{baseURL}/v1/customers/{customer_id}/orders</span><span class="sxs-lookup"><span data-stu-id="d7351-175">{baseURL}/v1/customers/{customer_id}/orders</span></span>|[<span data-ttu-id="d7351-176">Alle klantorders ontvangen</span><span class="sxs-lookup"><span data-stu-id="d7351-176">Get all customer orders</span></span>](get-all-of-a-customer-s-orders.md)|
|<span data-ttu-id="d7351-177">{baseURL}/v1/customers/{customer_id}/orders/{order_id}</span><span class="sxs-lookup"><span data-stu-id="d7351-177">{baseURL}/v1/customers/{customer_id}/orders/{order_id}</span></span>|[<span data-ttu-id="d7351-178">Een bestelling ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="d7351-178">Get an order by ID</span></span>](get-an-order-by-id.md)|
|<span data-ttu-id="d7351-179">{baseURL}/v1/customers/{customer_id}/orders/{order_id}/provisioningstatus</span><span class="sxs-lookup"><span data-stu-id="d7351-179">{baseURL}/v1/customers/{customer_id}/orders/{order_id}/provisioningstatus</span></span>|[<span data-ttu-id="d7351-180">De inrichtingsstatus van het abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="d7351-180">Get subscription provisioning status</span></span>](get-subscription-provisioning-status.md)|
|<span data-ttu-id="d7351-181">{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}</span><span class="sxs-lookup"><span data-stu-id="d7351-181">{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}</span></span>|[<span data-ttu-id="d7351-182">Orders beheren en een abonnement beheren</span><span class="sxs-lookup"><span data-stu-id="d7351-182">Manage orders and manage a subscription</span></span>](manage-orders.md#manage-a-subscription)|
|<span data-ttu-id="d7351-183">{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}/addons</span><span class="sxs-lookup"><span data-stu-id="d7351-183">{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}/addons</span></span>|[<span data-ttu-id="d7351-184">Een lijst met invoegtoepassingen voor een abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="d7351-184">Get a list of add-ons for a subscription</span></span>](get-a-list-of-add-ons-for-a-subscription.md)|
|<span data-ttu-id="d7351-185">{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}/azureEntitlements</span><span class="sxs-lookup"><span data-stu-id="d7351-185">{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}/azureEntitlements</span></span>|[<span data-ttu-id="d7351-186">Een lijst met Azure-rechten voor een abonnement op halen</span><span class="sxs-lookup"><span data-stu-id="d7351-186">Get a list of Azure entitlements for a subscription</span></span>](get-a-list-of-azure-entitlements-for-subscription.md)|
|<span data-ttu-id="d7351-187">{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}/registrationstatus</span><span class="sxs-lookup"><span data-stu-id="d7351-187">{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}/registrationstatus</span></span>|[<span data-ttu-id="d7351-188">De registratiestatus van het abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="d7351-188">Get subscription registration status</span></span>](get-subscription-registration-status.md)|
|<span data-ttu-id="d7351-189">{baseURL}/v1/customers/{customer-tenant-id}/transfers</span><span class="sxs-lookup"><span data-stu-id="d7351-189">{baseURL}/v1/customers/{customer-tenant-id}/transfers</span></span>|[<span data-ttu-id="d7351-190">Alle overdrachten van een klant krijgen</span><span class="sxs-lookup"><span data-stu-id="d7351-190">Get all of a customer's transfers</span></span>](get-all-of-a-customer-s-transfers.md)|
|<span data-ttu-id="d7351-191">{baseURL}/v1/productUpgrades/{upgrade-id}/status</span><span class="sxs-lookup"><span data-stu-id="d7351-191">{baseURL}/v1/productUpgrades/{upgrade-id}/status</span></span>|[<span data-ttu-id="d7351-192">Upgradestatus van product ophalen</span><span class="sxs-lookup"><span data-stu-id="d7351-192">Get product upgrade status</span></span>](get-product-upgrade-status.md)|
|<span data-ttu-id="d7351-193">{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions</span><span class="sxs-lookup"><span data-stu-id="d7351-193">{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions</span></span>|[<span data-ttu-id="d7351-194">Een lijst met aanbiedingen voor omzetten van de proefversie ophalen</span><span class="sxs-lookup"><span data-stu-id="d7351-194">Get a list of trial conversion offers</span></span>](get-a-list-of-trial-conversion-offers.md)|


### <a name="error-code-response"></a><span data-ttu-id="d7351-195">Antwoord van foutcode:</span><span class="sxs-lookup"><span data-stu-id="d7351-195">Error code response:</span></span>
```http
HTTP/1.1 429 Too Many Requests 

Content-Length: 84 

Content-Type: application/json 

Retry-After: 57 

Date: Tue, 21 Jul 2020 04:10:58 GMT 

{ "statusCode": 429, "message": "Rate limit is exceeded. Try again in 57 seconds." } 
```

## <a name="example-of-activity-log"></a><span data-ttu-id="d7351-196">Voorbeeld van activiteitenlogboek</span><span class="sxs-lookup"><span data-stu-id="d7351-196">Example of activity log</span></span>

<span data-ttu-id="d7351-197">Voor best practice het analyseren van dagelijkse wijzigingen, raden we u aan om een query uit te voeren op auditrecords voor een specifieke dag.</span><span class="sxs-lookup"><span data-stu-id="d7351-197">For best practice in analyzing daily changes, we recommend that you query audit record for a specific day.</span></span> 

<span data-ttu-id="d7351-198">In het antwoord krijgt u een resultaat met wijzigingen in het specifieke bewerkingstype.</span><span class="sxs-lookup"><span data-stu-id="d7351-198">In the response, you will get a result with changes to specific operation type.</span></span><span data-ttu-id="d7351-199">U kunt filteren op basis van de bewerking die u belangrijk vindt.</span><span class="sxs-lookup"><span data-stu-id="d7351-199">  You can filter based on the operation you care about.</span></span> <span data-ttu-id="d7351-200">Als u bijvoorbeeld geïnteresseerd bent in een nieuwe klant, kunt u operationType = "add_customer" bekijken.</span><span class="sxs-lookup"><span data-stu-id="d7351-200"> For example, if you are interested in a newly created customer, you can look at operationType = “add_customer”.</span></span>  

<span data-ttu-id="d7351-201">De lijst met operationtype/resources vindt u in de onderstaande API-documenten.</span><span class="sxs-lookup"><span data-stu-id="d7351-201">List of operationtype/resources can be found in below API docs.</span></span>  

- [<span data-ttu-id="d7351-202">Resources controleren</span><span class="sxs-lookup"><span data-stu-id="d7351-202">Auditing resources</span></span>](auditing-resources.md)  

- [<span data-ttu-id="d7351-203">Een record van een Partner Center per gebruiker</span><span class="sxs-lookup"><span data-stu-id="d7351-203">Get a record of a Partner Center activity by user</span></span>](get-a-record-of-partner-center-activity-by-user.md)  



### <a name="response-example"></a><span data-ttu-id="d7351-204">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="d7351-204">Response example</span></span>

<span data-ttu-id="d7351-205">**Aanvraag**:</span><span class="sxs-lookup"><span data-stu-id="d7351-205">**Request**:</span></span>  
```http
Http Get call:  https://api.partnercenter.microsoft.com/v1/auditrecords?startDate=2020-09-02&endDate=2020-09-02&size=50 

Authorization: Bearer <token> 

Accept: application/json 

MS-RequestId: 127facaa-e389-41f8-8bb7-1d1af99db893 

MS-CorrelationId: de9c2ccc-40dd-4186-9660-65b9b64c3d14 

X-Locale: en-US 

Host: api.partnercenter.microsoft.com 

Connection: Keep-Alive 
```

<span data-ttu-id="d7351-206">**Antwoord:**</span><span class="sxs-lookup"><span data-stu-id="d7351-206">**Response**:</span></span>    
```http
{ 

    "totalCount": 17, 

    "items": [ 

        { 

            "id": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d_e905b566-4779-4e57-944c-7b1b5312705b_updatecustomeruserlicenses_637346859797753934", 

            "partnerId": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d", 

            "participants": [ 

                "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d" 

            ], 

            "customerId": "e905b566-4779-4e57-944c-7b1b5312705b", 

            "userPrincipalName": "admin@testsw09.onmicrosoft.com", 

            "applicationId": "FulfillmentService", 

            "resourceType": "license", 

            "operationType": "update_customer_user_licenses", 

            "operationDate": "2020-09-02T23:26:19.7753934Z", 

            "operationStatus": "succeeded", 

            "customizedData": [ 

                { 

                    "key": "CustomerUserId", 

                    "value": "933808c7-b165-496c-a24e-1a4b7846fab4" 

                } 

            ], 

            "attributes": { 

                "objectType": "AuditRecord" 

            } 

        }, 

        { 

            "id": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d_86bddccf-9a53-40c6-907c-08067a3f8da7_ia80zlkxp6ewoqpp35pbqjlhqv9iigvz1_createorder_637346662909268372", 

            "partnerId": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d", 

            "participants": [ 

                "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d" 

            ], 

            "customerId": "86bddccf-9a53-40c6-907c-08067a3f8da7", 

            "customerName": "CustomMetersStagingTest", 

            "userPrincipalName": "admin@testsw09.onmicrosoft.com", 

            "applicationId": "4990cffe-04e8-4e8b-808a-1175604b879f", 

            "resourceType": "order", 

            "resourceNewValue": "{\"Id\":\"Ia80ZLkXp6eWOqpp35pBQJLhqv9IiGVZ1\",\"AlternateId\":\"64144d300bde\",\"ReferenceCustomerId\":\"86bddccf-9a53-40c6-907c-08067a3f8da7\",\"BillingCycle\":\"monthly\",\"CurrencyCode\":\"USD\",\"CurrencySymbol\":\"$\",\"LineItems\":[{\"LineItemNumber\":0,\"ProvisioningContext\":null,\"OfferId\":\"DZH318Z0C964:0001:DZH318Z0BZDG\",\"SubscriptionId\":\"f428d44a-d08b-348b-579e-ce92a6362c7b\",\"ParentSubscriptionId\":null,\"TermDuration\":\"P1M\",\"TransactionType\":\"New\",\"FriendlyName\":\"SaaS custom meter offer - Bronze\",\"Quantity\":1,\"Pricing\":null,\"PartnerIdOnRecord\":null,\"RenewsTo\":null,\"Links\":{\"Product\":{\"Uri\":\"/products/DZH318Z0C964?country=US\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]},\"Sku\":{\"Uri\":\"/products/DZH318Z0C964/skus/0001?country=US\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]},\"Availability\":{\"Uri\":\"/products/DZH318Z0C964/skus/0001/availabilities/DZH318Z0BZDG?country=US\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]},\"ActivationLinks\":{\"Uri\":\"/customers/86bddccf-9a53-40c6-907c-08067a3f8da7/orders/Ia80ZLkXp6eWOqpp35pBQJLhqv9IiGVZ1/lineitems/0/activationlinks\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]}}}],\"CreationDate\":\"2020-09-02T17:58:01.7755853Z\",\"Status\":\"pending\",\"TransactionType\":\"UserPurchase\",\"Links\":{\"Self\":{\"Uri\":\"/customers/86bddccf-9a53-40c6-907c-08067a3f8da7/orders/Ia80ZLkXp6eWOqpp35pBQJLhqv9IiGVZ1\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]},\"ProvisioningStatus\":{\"Uri\":\"/customers/86bddccf-9a53-40c6-907c-08067a3f8da7/orders/Ia80ZLkXp6eWOqpp35pBQJLhqv9IiGVZ1/provisioningstatus\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]},\"PatchOperation\":{\"Uri\":\"/customers/86bddccf-9a53-40c6-907c-08067a3f8da7/orders/Ia80ZLkXp6eWOqpp35pBQJLhqv9IiGVZ1\",\"Method\":\"PATCH\",\"Body\":null,\"Headers\":[]}},\"Client\":{\"marketplaceCountry\":\"US\",\"deviceFamily\":\"UniversalStore-PartnerCenter\",\"name\":\"Partner Center Web\"},\"Attributes\":{\"ObjectType\":\"Order\"}}", 

            "operationType": "create_order", 

            "originalCorrelationId": "96514ebe-c1b2-4865-cb46-2c2d20a2e911", 

            "operationDate": "2020-09-02T17:58:10.9268372Z", 

            "operationStatus": "succeeded", 

            "customizedData": [ 

                { 

                    "key": "OrderId", 

                    "value": "Ia80ZLkXp6eWOqpp35pBQJLhqv9IiGVZ1" 

                }, 

                { 

                    "key": "AlternateId", 

                    "value": "64144d300bde" 

                }, 

                { 

                    "key": "BillingCycle", 

                    "value": "Monthly" 

                }, 

                { 

                    "key": "OfferId-0", 

                    "value": "DZH318Z0C964:0001:DZH318Z0BZDG" 

                }, 

                { 

                    "key": "SubscriptionId-0", 

                    "value": "f428d44a-d08b-348b-579e-ce92a6362c7b" 

                }, 

                { 

                    "key": "SubscriptionName-0", 

                    "value": "SaaS custom meter offer - Bronze" 

                }, 

                { 

                   "key": "Quantity-0", 

                    "value": "1" 

                }, 

                { 

                    "key": "PartnerOnRecord-0", 

                    "value": null 

                } 

            ], 

            "attributes": { 

                "objectType": "AuditRecord" 

            } 

        }, 

                           { 

            "id": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d_86bddccf-9a53-40c6-907c-08067a3f8da7_86bddccf-9a53-40c6-907c-08067a3f8da7_addcustomer_637346648528069005", 

            "partnerId": "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d", 

            "participants": [ 

                "9daaeb1c-4195-4db5-9f1d-509eb70c8c2d" 

            ], 

            "customerId": "86bddccf-9a53-40c6-907c-08067a3f8da7", 

            "customerName": "CustomMetersStagingTest", 

            "userPrincipalName": "admin@testsw09.onmicrosoft.com", 

            "applicationId": "4990cffe-04e8-4e8b-808a-1175604b879f", 

            "resourceType": "customer", 

            "resourceNewValue": "{\"Id\":\"86bddccf-9a53-40c6-907c-08067a3f8da7\",\"CommerceId\":\"9dd78b4f-f98a-44b4-a2fa-2b82ac58d24c\",\"CompanyProfile\":{\"TenantId\":\"86bddccf-9a53-40c6-907c-08067a3f8da7\",\"Domain\":\"CustomMetersStagingTest.onmicrosoft.com\",\"CompanyName\":\"CustomMetersStagingTest\",\"Address\":null,\"Email\":null,\"OrganizationRegistrationNumber\":null,\"Links\":{\"Self\":{\"Uri\":\"/customers/86bddccf-9a53-40c6-907c-08067a3f8da7/profiles/company\",\"Method\":\"GET\",\"Body\":null,\"Headers\":[]}},\"Attributes\":{\"ObjectType\":\"CustomerCompanyProfile\"}},\"BillingProfile\":{\"Id\":\"4beafd7b-cdab-5bdc-52ed-02e16edf2e7a\",\"FirstName\":\"CustomMetersStagingTest\",\"LastName\":\"CustomMetersStagingTest\",\"Email\":\"CustomMetersStagingTest@CustomMetersStagingTest.com\",\"Culture\":\"en-US\",\"Language\":\"en\",\"CompanyName\":\"CustomMetersStagingTest\",\"DefaultAddress\":{\"Id\":null,\"Country\":\"US\",\"Region\":null,\"City\":\"Seattle\",\"State\":\"WA\",\"District\":null,\"AddressLine1\":\"CustomMetersStagingTest\",\"AddressLine2\":null,\"AddressLine3\":null,\"PostalCode\":\"98122\",\"FirstName\":\"CustomMetersStagingTest\",\"LastName\":\"CustomMetersStagingTest\",\"EmailAddress\":null,\"PhoneNumber\":null,\"MiddleName\":null},\"Attributes\":{\"Etag\":\"-2279334701316321663\",\"ObjectType\":\"CustomerBillingProfile\"}},\"RelationshipToPartner\":\"reseller\",\"AllowDelegatedAccess\":true,\"UserCredentials\":{\"userName\":\"admin\",\"password\":\"\"},\"AssociatedPartnerId\":null,\"CustomDomains\":null,\"Attributes\":{\"ObjectType\":\"Customer\"}}", 

            "operationType": "add_customer", 

            "originalCorrelationId": "7550d9ea-e64a-416f-e49b-3670c516cf69", 

            "operationDate": "2020-09-02T17:34:12.8069005Z", 

            "operationStatus": "succeeded", 

            "customizedData": [ 

                { 

                    "key": "PrimaryDomainName", 

                    "value": "CustomMetersStagingTest.onmicrosoft.com" 

                }, 

                { 

                    "key": "Relationship", 

                    "value": "Reseller" 

                } 

            ], 

            "attributes": { 

                "objectType": "AuditRecord" 

            } 

        }, 

                            

        ... 

    ], 

    "links": { 

        "self": { 

            "uri": "/auditrecords?startDate=2020-09-02&endDate=2020-09-02&size=50", 

            "method": "GET", 

            "headers": [] 

        } 

    }, 

    "attributes": { 

        "objectType": "Collection" 

    } 

} 
```
 

