---
title: Richtlijnen voor API-beperking
description: Voor partners die partner Center-Api's aanroepen, leert u welke Api's van invloed zijn op de micro soft-API-beperking en best practices om de beperking te voor komen of te verbeteren.
ms.date: 09/09/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: vijvala
ms.author: vijvala
ms.openlocfilehash: a52751a97e699050075c1aac910cc51e94514f26
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/08/2020
ms.locfileid: "97768661"
---
# <a name="api-throttling-guidance-for-partners-calling-partner-center-apis"></a><span data-ttu-id="31b62-103">Richt lijnen voor API-beperking voor partners die partner Center-Api's aanroepen</span><span class="sxs-lookup"><span data-stu-id="31b62-103">API throttling guidance for partners calling Partner Center APIs</span></span> 

<span data-ttu-id="31b62-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="31b62-104">**Applies to**</span></span>

- <span data-ttu-id="31b62-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="31b62-105">Partner Center</span></span>

<span data-ttu-id="31b62-106">Micro soft implementeert de API-beperking om consistente prestaties binnen een tijds spanne te bieden voor partners die de Api's van het partner centrum aanroepen.</span><span class="sxs-lookup"><span data-stu-id="31b62-106">Microsoft is implementing API throttling to allow more consistent performance within a time span for partners calling the Partner Center APIs.</span></span> <span data-ttu-id="31b62-107">Met beperking wordt het aantal aanvragen van een service in een bepaalde periode beperkt om te voor komen dat bronnen worden gevermijdd.</span><span class="sxs-lookup"><span data-stu-id="31b62-107">Throttling limits the number of requests to a service in a time span to prevent overuse of resources.</span></span> <span data-ttu-id="31b62-108">Hoewel het partner centrum is ontworpen voor het afhandelen van een groot aantal aanvragen, kunt u met bandbreedte beperking optimale prestaties en betrouw baarheid behouden voor alle partners.</span><span class="sxs-lookup"><span data-stu-id="31b62-108">While Partner Center is designed to handle a high volume of requests, if an overwhelming number of requests occur by few partners, throttling helps maintain optimal performance and reliability for all partners.</span></span>  

<span data-ttu-id="31b62-109">Beperkings limieten variëren op basis van het scenario.</span><span class="sxs-lookup"><span data-stu-id="31b62-109">Throttling limits vary based on the scenario.</span></span> <span data-ttu-id="31b62-110">Als u bijvoorbeeld een groot aantal schrijf bewerkingen uitvoert, is de kans op beperking hoger dan wanneer u alleen lees bewerkingen uitvoert.</span><span class="sxs-lookup"><span data-stu-id="31b62-110">For example, if you are performing a large volume of writes, the possibility for throttling is higher than if you are only performing reads.</span></span>

## <a name="what-happens-when-throttling-occurs"></a><span data-ttu-id="31b62-111">Wat gebeurt er wanneer het beperken wordt uitgevoerd?</span><span class="sxs-lookup"><span data-stu-id="31b62-111">What happens when throttling occurs?</span></span> 

<span data-ttu-id="31b62-112">Wanneer een drempel waarde voor bandbreedte beperking wordt overschreden, beperkt het partner centrum voor een bepaalde periode verdere aanvragen van die client.</span><span class="sxs-lookup"><span data-stu-id="31b62-112">When a throttling threshold is exceeded, Partner Center limits any further requests from that client for a period of time.</span></span> <span data-ttu-id="31b62-113">Beperkings gedrag is afhankelijk van het type en het aantal aanvragen.</span><span class="sxs-lookup"><span data-stu-id="31b62-113">Throttling behavior depends on the type and number of requests.</span></span>   

### <a name="common-throttling-scenarios"></a><span data-ttu-id="31b62-114">Algemene beperkings scenario's</span><span class="sxs-lookup"><span data-stu-id="31b62-114">Common throttling scenarios</span></span> 

<span data-ttu-id="31b62-115">De meest voorkomende oorzaken van het beperken van clients zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="31b62-115">The most common causes of throttling of clients include:</span></span> 

- <span data-ttu-id="31b62-116">**Een groot aantal aanvragen voor een API per partner-Tenant-id**: voor sommige Partner Center-api's wordt beperking bepaald door de Tenant-id van de partner. als er te veel aanroepen naar deze api's worden uitgevoerd op dezelfde partner-Tenant-id, wordt de drempel waarde voor bandbreedte overschrijding overschreden.</span><span class="sxs-lookup"><span data-stu-id="31b62-116">**A large number of requests for an API per Partner Tenant ID**: for some Partner Center APIs, throttling is determined by Partner Tenant ID, too many calls to those APIs on the same Partner Tenant ID will result in exceeding the throttling threshold.</span></span>  

- <span data-ttu-id="31b62-117">**Een groot aantal aanvragen voor een API per partner-Tenant-id per Tenant-id** van de klant: voor andere api's wordt beperking bepaald door de Tenant-id van de partner en de Tenant-id van de klant. in dergelijke gevallen is het mogelijk dat er te veel aanroepen worden uitgevoerd voor dezelfde Tenant-ID van de klant.</span><span class="sxs-lookup"><span data-stu-id="31b62-117">**A large number of requests for an API per Partner Tenant ID per Customer Tenant ID**: for other APIs, throttling is determined by Partner Tenant ID/Customer Tenant ID combination; in those cases, making too many calls against the same customer tenant ID will result in throttling - while calls against other customers may succeed.</span></span>

## <a name="best-practices-to-avoid-throttling"></a><span data-ttu-id="31b62-118">Aanbevolen procedures om beperking te voor komen</span><span class="sxs-lookup"><span data-stu-id="31b62-118">Best practices to avoid throttling</span></span> 
 
<span data-ttu-id="31b62-119">Programmeer procedures, zoals voortdurend pollen van een resource om te controleren op updates en regel matig scan van resource verzamelingen om te controleren of er nieuwe of verwijderde resources zijn, zullen de algehele prestaties waarschijnlijk beperken.</span><span class="sxs-lookup"><span data-stu-id="31b62-119">Programming practices such as continuously polling a resource to check for updates and regularly scanning resource collections to check for new or deleted resources are more likely to lead to throttling and will degrade overall performance.</span></span> <span data-ttu-id="31b62-120">Gelijktijdige API-aanroepen kunnen leiden tot een groot aantal aanvragen per eenheids tijd, waardoor er ook aanvragen worden vertraagd.</span><span class="sxs-lookup"><span data-stu-id="31b62-120">Concurrent API calls may lead to high number of requests per unit time, which will also cause requests to be throttled.</span></span> <span data-ttu-id="31b62-121">U moet in plaats daarvan wijzigingen bijhouden en wijzigings meldingen Toep assen.</span><span class="sxs-lookup"><span data-stu-id="31b62-121">You should instead leverage change tracking and change notifications.</span></span> <span data-ttu-id="31b62-122">Daarnaast kunt u activiteiten Logboeken gebruiken voor het detecteren van wijzigingen. Zie [activiteiten logboeken van de partner centrum](get-a-record-of-partner-center-activity-by-user.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="31b62-122">Additionally, you should be able to leverage activity logs for detecting changes, see [Partner Center activity logs](get-a-record-of-partner-center-activity-by-user.md) for more information.</span></span>  <span data-ttu-id="31b62-123">Het wordt ten zeerste aangeraden partners te overwegen om de API voor activiteiten logboek te gebruiken voor meer efficiëntie en om te voor komen dat deze wordt beperkt.</span><span class="sxs-lookup"><span data-stu-id="31b62-123">We highly recommend partners to consider using the activity log API for more efficiency and to avoid throttling.</span></span> <span data-ttu-id="31b62-124">Zie ook het voor beeld van het gebruik van activiteiten Logboeken.</span><span class="sxs-lookup"><span data-stu-id="31b62-124">See also the example of using activity logs, below.</span></span>

## <a name="best-practices-to-handle-throttling"></a><span data-ttu-id="31b62-125">Best practices voor het afhandelen van beperking</span><span class="sxs-lookup"><span data-stu-id="31b62-125">Best practices to handle throttling</span></span>

<span data-ttu-id="31b62-126">Hieronder volgen enkele aanbevolen procedures voor het beperken van de verwerking:</span><span class="sxs-lookup"><span data-stu-id="31b62-126">The following are best practices for handling throttling:</span></span> 

- <span data-ttu-id="31b62-127">Verminder de mate van parallelle uitvoering.</span><span class="sxs-lookup"><span data-stu-id="31b62-127">Reduce the degree of parallelism.</span></span> 
- <span data-ttu-id="31b62-128">Verminder de frequentie van aanroepen.</span><span class="sxs-lookup"><span data-stu-id="31b62-128">Reduce the frequency of calls.</span></span> 
- <span data-ttu-id="31b62-129">Vermijd onmiddellijke pogingen omdat alle aanvragen toenemen ten opzichte van uw gebruiks limieten.</span><span class="sxs-lookup"><span data-stu-id="31b62-129">Avoid immediate retries because all requests accrue against your usage limits.</span></span> 

<span data-ttu-id="31b62-130">Gebruik de HTTP-foutcode 429 om beperking te detecteren wanneer u foutafhandeling implementeert.</span><span class="sxs-lookup"><span data-stu-id="31b62-130">When you implement error handling, use the HTTP error code 429 to detect throttling.</span></span> <span data-ttu-id="31b62-131">Het mislukte antwoord bevat de Retry-After-antwoord header.</span><span class="sxs-lookup"><span data-stu-id="31b62-131">The failed response includes the Retry-After response header.</span></span> <span data-ttu-id="31b62-132">Het maken van een back-up van aanvragen met de vertraging opnieuw proberen is de snelste manier om te herstellen.</span><span class="sxs-lookup"><span data-stu-id="31b62-132">Backing off requests using the Retry-after delay is the fastest way to recover from throttling.</span></span> 

<span data-ttu-id="31b62-133">Ga als volgt te werk om de vertraging opnieuw proberen te gebruiken:</span><span class="sxs-lookup"><span data-stu-id="31b62-133">To use the Retry-after delay, do the following:</span></span> 

1. <span data-ttu-id="31b62-134">Wacht het aantal seconden dat is opgegeven in de Retry-After-header.</span><span class="sxs-lookup"><span data-stu-id="31b62-134">Wait the number of seconds specified in the Retry-After header.</span></span> 

2. <span data-ttu-id="31b62-135">Voer de aanvraag opnieuw uit.</span><span class="sxs-lookup"><span data-stu-id="31b62-135">Retry the request.</span></span>  

3. <span data-ttu-id="31b62-136">Als de aanvraag opnieuw mislukt met een 429-fout code, wordt u nog steeds beperkt.</span><span class="sxs-lookup"><span data-stu-id="31b62-136">If the request fails again with a 429 error code, you are still being throttled.</span></span> <span data-ttu-id="31b62-137">Probeer het opnieuw met exponentiële uitstel, gebruik de aanbevolen Retry-After vertraging en voer de aanvraag opnieuw uit totdat deze slaagt.</span><span class="sxs-lookup"><span data-stu-id="31b62-137">Retry with Exponential backoff, use the recommended Retry-After delay and retry the request until it succeeds.</span></span>

4. <span data-ttu-id="31b62-138">Als u SDK gebruikt, ontvangt u een uitzonde ring met de status code 429 wanneer uw aanvraag wordt beperkt.</span><span class="sxs-lookup"><span data-stu-id="31b62-138">If you are using SDK you'll receive an exception with status code 429 when your request is being throttled.</span></span> <span data-ttu-id="31b62-139">Gebruik de eigenschap RetryAfter in de uitzonde ring en voer de aanvraag opnieuw uit nadat de tijd is verstreken.</span><span class="sxs-lookup"><span data-stu-id="31b62-139">Use the RetryAfter property in the exception and retry the request after the time is elapsed.</span></span>


## <a name="apis-currently-impacted-by-throttling"></a><span data-ttu-id="31b62-140">Api's die momenteel worden beïnvloed door beperking</span><span class="sxs-lookup"><span data-stu-id="31b62-140">APIs currently impacted by throttling</span></span>

<span data-ttu-id="31b62-141">In de lange uitvoering wordt elke single Partner Center-API die het eind punt ' api.partnercenter.microsoft.com/' aanroept, beperkt.</span><span class="sxs-lookup"><span data-stu-id="31b62-141">In the long run, every single Partner Center API that calls the endpoint “api.partnercenter.microsoft.com/” will be throttled.</span></span> <span data-ttu-id="31b62-142">De beperkings limieten worden op dit moment alleen afgedwongen voor de enkele Api's die hieronder worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="31b62-142">Currently, the throttling limits are only enforced on the few APIs listed below.</span></span> <span data-ttu-id="31b62-143">In het partner centrum wordt de telemetrie op elk van de Api's verzameld en worden de beperkings limieten dynamisch aangepast.</span><span class="sxs-lookup"><span data-stu-id="31b62-143">Partner Center will be collecting the telemetry on each of the APIs and will dynamically adjust the throttling limits.</span></span> <span data-ttu-id="31b62-144">De volgende tabel geeft een lijst van de Api's waar bandbreedte beperking op dit moment wordt afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="31b62-144">The following table lists the APIs where throttling is currently enforced.</span></span>  


|<span data-ttu-id="31b62-145">**Bewerking**</span><span class="sxs-lookup"><span data-stu-id="31b62-145">**Operation**</span></span>| <span data-ttu-id="31b62-146">**Documentatie voor Partnercentrum**</span><span class="sxs-lookup"><span data-stu-id="31b62-146">**Partner Center documentation**</span></span>|       
|------------------------|----------------------------|
|<span data-ttu-id="31b62-147">{baseURL}/v1/Customers/{customer_id}/orders</span><span class="sxs-lookup"><span data-stu-id="31b62-147">{baseURL}/v1/customers/{customer_id}/orders</span></span>|[<span data-ttu-id="31b62-148">een order maken</span><span class="sxs-lookup"><span data-stu-id="31b62-148">create an order</span></span>](create-an-order.md)|
|<span data-ttu-id="31b62-149">{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/upgrades</span><span class="sxs-lookup"><span data-stu-id="31b62-149">{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/upgrades</span></span>|[<span data-ttu-id="31b62-150">een abonnement overdragen</span><span class="sxs-lookup"><span data-stu-id="31b62-150">transition a subscription</span></span>](transition-a-subscription.md)|
|<span data-ttu-id="31b62-151">{baseURL}/v1/customers/{customer-tenant-id}/orders/{order-id}</span><span class="sxs-lookup"><span data-stu-id="31b62-151">{baseURL}/v1/customers/{customer-tenant-id}/orders/{order-id}</span></span>|[<span data-ttu-id="31b62-152">een invoeg toepassing aanschaffen bij een abonnement</span><span class="sxs-lookup"><span data-stu-id="31b62-152">purchase an addon to a subscription</span></span>](purchase-an-add-on-to-a-subscription.md)|
|<span data-ttu-id="31b62-153">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}</span><span class="sxs-lookup"><span data-stu-id="31b62-153">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}</span></span>|[<span data-ttu-id="31b62-154">een winkel wagen maken</span><span class="sxs-lookup"><span data-stu-id="31b62-154">create a cart</span></span>](create-a-cart.md)|
|<span data-ttu-id="31b62-155">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}/checkout</span><span class="sxs-lookup"><span data-stu-id="31b62-155">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}/checkout</span></span>|[<span data-ttu-id="31b62-156">een winkel wagen afhandelen</span><span class="sxs-lookup"><span data-stu-id="31b62-156">checkout a cart</span></span>](checkout-a-cart.md)|
|<span data-ttu-id="31b62-157">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}</span><span class="sxs-lookup"><span data-stu-id="31b62-157">{baseURL}/v1/customers/{customer-id}/carts/{cart-id}</span></span>|[<span data-ttu-id="31b62-158">een winkel wagen bijwerken</span><span class="sxs-lookup"><span data-stu-id="31b62-158">update a cart</span></span>](update-a-cart.md)|
|<span data-ttu-id="31b62-159">{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrations</span><span class="sxs-lookup"><span data-stu-id="31b62-159">{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrations</span></span>|[<span data-ttu-id="31b62-160">een abonnement registreren</span><span class="sxs-lookup"><span data-stu-id="31b62-160">register a subscription</span></span>](register-a-subscription.md)|
|<span data-ttu-id="31b62-161">{baseURL}/v1/productupgrades</span><span class="sxs-lookup"><span data-stu-id="31b62-161">{baseURL}/v1/productupgrades</span></span>|[<span data-ttu-id="31b62-162">product upgrade-entiteit maken</span><span class="sxs-lookup"><span data-stu-id="31b62-162">create product upgrade entity</span></span>](create-product-upgrade-entity.md)|
|<span data-ttu-id="31b62-163">{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions</span><span class="sxs-lookup"><span data-stu-id="31b62-163">{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions</span></span> |[<span data-ttu-id="31b62-164">een proef abonnement converteren naar betaald</span><span class="sxs-lookup"><span data-stu-id="31b62-164">convert a trial subscription to paid</span></span>](convert-a-trial-subscription-to-paid.md)|
|<span data-ttu-id="31b62-165">{baseURL}/v1/customers/{customer-tenant-id}</span><span class="sxs-lookup"><span data-stu-id="31b62-165">{baseURL}/v1/customers/{customer-tenant-id}</span></span>|[<span data-ttu-id="31b62-166">een klant op basis van de id ophalen</span><span class="sxs-lookup"><span data-stu-id="31b62-166">get a customer by id</span></span>](get-a-customer-by-id.md)|
|<span data-ttu-id="31b62-167">{baseURL}/v1/productUpgrades/eligibility</span><span class="sxs-lookup"><span data-stu-id="31b62-167">{baseURL}/v1/productUpgrades/eligibility</span></span>|[<span data-ttu-id="31b62-168">geschiktheid voor product upgrade verkrijgen</span><span class="sxs-lookup"><span data-stu-id="31b62-168">get eligibility for product upgrade</span></span>](get-eligibility-for-product-upgrade.md)|
|<span data-ttu-id="31b62-169">{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}</span><span class="sxs-lookup"><span data-stu-id="31b62-169">{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}</span></span> |[<span data-ttu-id="31b62-170">abonnement beheren</span><span class="sxs-lookup"><span data-stu-id="31b62-170">manage subscription</span></span>](manage-orders.md#manage-a-subscription)|


### <a name="error-code-response"></a><span data-ttu-id="31b62-171">Reactie op fout code:</span><span class="sxs-lookup"><span data-stu-id="31b62-171">Error code response:</span></span>
```http
HTTP/1.1 429 Too Many Requests 

Content-Length: 84 

Content-Type: application/json 

Retry-After: 57 

Date: Tue, 21 Jul 2020 04:10:58 GMT 

{ "statusCode": 429, "message": "Rate limit is exceeded. Try again in 57 seconds." } 
```

## <a name="example-of-activity-log"></a><span data-ttu-id="31b62-172">Voor beeld van activiteiten logboek</span><span class="sxs-lookup"><span data-stu-id="31b62-172">Example of activity log</span></span>

<span data-ttu-id="31b62-173">Voor best practice bij het analyseren van dagelijkse wijzigingen, raden we u aan om een controle record te zoeken voor een specifieke dag.</span><span class="sxs-lookup"><span data-stu-id="31b62-173">For best practice in analyzing daily changes, we recommend that you query audit record for a specific day.</span></span> 

<span data-ttu-id="31b62-174">In het antwoord verschijnt een resultaat met wijzigingen in een specifiek bewerkings type.</span><span class="sxs-lookup"><span data-stu-id="31b62-174">In the response, you will get a result with changes to specific operation type.</span></span><span data-ttu-id="31b62-175">U kunt filteren op basis van de bewaarde bewerking.</span><span class="sxs-lookup"><span data-stu-id="31b62-175">  You can filter based on the operation you care about.</span></span> <span data-ttu-id="31b62-176">Bijvoorbeeld, als u geïnteresseerd bent in een nieuw gemaakte klant, kunt u operationType = "add_customer" bekijken.</span><span class="sxs-lookup"><span data-stu-id="31b62-176"> For example, if you are interested in a newly created customer, you can look at operationType = “add_customer”.</span></span>  

<span data-ttu-id="31b62-177">De lijst met operationtype/resources vindt u in onderstaande API-documenten.</span><span class="sxs-lookup"><span data-stu-id="31b62-177">List of operationtype/resources can be found in below API docs.</span></span>  

- [<span data-ttu-id="31b62-178">Controle bronnen</span><span class="sxs-lookup"><span data-stu-id="31b62-178">Auditing resources</span></span>](auditing-resources.md)  

- [<span data-ttu-id="31b62-179">Een record van een partner Center-activiteit door de gebruiker ophalen</span><span class="sxs-lookup"><span data-stu-id="31b62-179">Get a record of a Partner Center activity by user</span></span>](get-a-record-of-partner-center-activity-by-user.md)  



### <a name="response-example"></a><span data-ttu-id="31b62-180">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="31b62-180">Response example</span></span>

<span data-ttu-id="31b62-181">**Aanvraag**:</span><span class="sxs-lookup"><span data-stu-id="31b62-181">**Request**:</span></span>  
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

<span data-ttu-id="31b62-182">**Antwoord**:</span><span class="sxs-lookup"><span data-stu-id="31b62-182">**Response**:</span></span>    
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
 

