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
# <a name="api-throttling-guidance-for-partners-calling-partner-center-apis"></a>Richt lijnen voor API-beperking voor partners die partner Center-Api's aanroepen 

**Van toepassing op**

- Partnercentrum

Micro soft implementeert de API-beperking om consistente prestaties binnen een tijds spanne te bieden voor partners die de Api's van het partner centrum aanroepen. Met beperking wordt het aantal aanvragen van een service in een bepaalde periode beperkt om te voor komen dat bronnen worden gevermijdd. Hoewel het partner centrum is ontworpen voor het afhandelen van een groot aantal aanvragen, kunt u met bandbreedte beperking optimale prestaties en betrouw baarheid behouden voor alle partners.  

Beperkings limieten variëren op basis van het scenario. Als u bijvoorbeeld een groot aantal schrijf bewerkingen uitvoert, is de kans op beperking hoger dan wanneer u alleen lees bewerkingen uitvoert.

## <a name="what-happens-when-throttling-occurs"></a>Wat gebeurt er wanneer het beperken wordt uitgevoerd? 

Wanneer een drempel waarde voor bandbreedte beperking wordt overschreden, beperkt het partner centrum voor een bepaalde periode verdere aanvragen van die client. Beperkings gedrag is afhankelijk van het type en het aantal aanvragen.   

### <a name="common-throttling-scenarios"></a>Algemene beperkings scenario's 

De meest voorkomende oorzaken van het beperken van clients zijn onder andere: 

- **Een groot aantal aanvragen voor een API per partner-Tenant-id**: voor sommige Partner Center-api's wordt beperking bepaald door de Tenant-id van de partner. als er te veel aanroepen naar deze api's worden uitgevoerd op dezelfde partner-Tenant-id, wordt de drempel waarde voor bandbreedte overschrijding overschreden.  

- **Een groot aantal aanvragen voor een API per partner-Tenant-id per Tenant-id** van de klant: voor andere api's wordt beperking bepaald door de Tenant-id van de partner en de Tenant-id van de klant. in dergelijke gevallen is het mogelijk dat er te veel aanroepen worden uitgevoerd voor dezelfde Tenant-ID van de klant.

## <a name="best-practices-to-avoid-throttling"></a>Aanbevolen procedures om beperking te voor komen 
 
Programmeer procedures, zoals voortdurend pollen van een resource om te controleren op updates en regel matig scan van resource verzamelingen om te controleren of er nieuwe of verwijderde resources zijn, zullen de algehele prestaties waarschijnlijk beperken. Gelijktijdige API-aanroepen kunnen leiden tot een groot aantal aanvragen per eenheids tijd, waardoor er ook aanvragen worden vertraagd. U moet in plaats daarvan wijzigingen bijhouden en wijzigings meldingen Toep assen. Daarnaast kunt u activiteiten Logboeken gebruiken voor het detecteren van wijzigingen. Zie [activiteiten logboeken van de partner centrum](get-a-record-of-partner-center-activity-by-user.md) voor meer informatie.  Het wordt ten zeerste aangeraden partners te overwegen om de API voor activiteiten logboek te gebruiken voor meer efficiëntie en om te voor komen dat deze wordt beperkt. Zie ook het voor beeld van het gebruik van activiteiten Logboeken.

## <a name="best-practices-to-handle-throttling"></a>Best practices voor het afhandelen van beperking

Hieronder volgen enkele aanbevolen procedures voor het beperken van de verwerking: 

- Verminder de mate van parallelle uitvoering. 
- Verminder de frequentie van aanroepen. 
- Vermijd onmiddellijke pogingen omdat alle aanvragen toenemen ten opzichte van uw gebruiks limieten. 

Gebruik de HTTP-foutcode 429 om beperking te detecteren wanneer u foutafhandeling implementeert. Het mislukte antwoord bevat de Retry-After-antwoord header. Het maken van een back-up van aanvragen met de vertraging opnieuw proberen is de snelste manier om te herstellen. 

Ga als volgt te werk om de vertraging opnieuw proberen te gebruiken: 

1. Wacht het aantal seconden dat is opgegeven in de Retry-After-header. 

2. Voer de aanvraag opnieuw uit.  

3. Als de aanvraag opnieuw mislukt met een 429-fout code, wordt u nog steeds beperkt. Probeer het opnieuw met exponentiële uitstel, gebruik de aanbevolen Retry-After vertraging en voer de aanvraag opnieuw uit totdat deze slaagt.

4. Als u SDK gebruikt, ontvangt u een uitzonde ring met de status code 429 wanneer uw aanvraag wordt beperkt. Gebruik de eigenschap RetryAfter in de uitzonde ring en voer de aanvraag opnieuw uit nadat de tijd is verstreken.


## <a name="apis-currently-impacted-by-throttling"></a>Api's die momenteel worden beïnvloed door beperking

In de lange uitvoering wordt elke single Partner Center-API die het eind punt ' api.partnercenter.microsoft.com/' aanroept, beperkt. De beperkings limieten worden op dit moment alleen afgedwongen voor de enkele Api's die hieronder worden weer gegeven. In het partner centrum wordt de telemetrie op elk van de Api's verzameld en worden de beperkings limieten dynamisch aangepast. De volgende tabel geeft een lijst van de Api's waar bandbreedte beperking op dit moment wordt afgedwongen.  


|**Bewerking**| **Documentatie voor Partnercentrum**|       
|------------------------|----------------------------|
|{baseURL}/v1/Customers/{customer_id}/orders|[een order maken](create-an-order.md)|
|{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/upgrades|[een abonnement overdragen](transition-a-subscription.md)|
|{baseURL}/v1/customers/{customer-tenant-id}/orders/{order-id}|[een invoeg toepassing aanschaffen bij een abonnement](purchase-an-add-on-to-a-subscription.md)|
|{baseURL}/v1/customers/{customer-id}/carts/{cart-id}|[een winkel wagen maken](create-a-cart.md)|
|{baseURL}/v1/customers/{customer-id}/carts/{cart-id}/checkout|[een winkel wagen afhandelen](checkout-a-cart.md)|
|{baseURL}/v1/customers/{customer-id}/carts/{cart-id}|[een winkel wagen bijwerken](update-a-cart.md)|
|{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrations|[een abonnement registreren](register-a-subscription.md)|
|{baseURL}/v1/productupgrades|[product upgrade-entiteit maken](create-product-upgrade-entity.md)|
|{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions |[een proef abonnement converteren naar betaald](convert-a-trial-subscription-to-paid.md)|
|{baseURL}/v1/customers/{customer-tenant-id}|[een klant op basis van de id ophalen](get-a-customer-by-id.md)|
|{baseURL}/v1/productUpgrades/eligibility|[geschiktheid voor product upgrade verkrijgen](get-eligibility-for-product-upgrade.md)|
|{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} |[abonnement beheren](manage-orders.md#manage-a-subscription)|


### <a name="error-code-response"></a>Reactie op fout code:
```http
HTTP/1.1 429 Too Many Requests 

Content-Length: 84 

Content-Type: application/json 

Retry-After: 57 

Date: Tue, 21 Jul 2020 04:10:58 GMT 

{ "statusCode": 429, "message": "Rate limit is exceeded. Try again in 57 seconds." } 
```

## <a name="example-of-activity-log"></a>Voor beeld van activiteiten logboek

Voor best practice bij het analyseren van dagelijkse wijzigingen, raden we u aan om een controle record te zoeken voor een specifieke dag. 

In het antwoord verschijnt een resultaat met wijzigingen in een specifiek bewerkings type.U kunt filteren op basis van de bewaarde bewerking. Bijvoorbeeld, als u geïnteresseerd bent in een nieuw gemaakte klant, kunt u operationType = "add_customer" bekijken.  

De lijst met operationtype/resources vindt u in onderstaande API-documenten.  

- [Controle bronnen](auditing-resources.md)  

- [Een record van een partner Center-activiteit door de gebruiker ophalen](get-a-record-of-partner-center-activity-by-user.md)  



### <a name="response-example"></a>Voorbeeld van antwoord

**Aanvraag**:  
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

**Antwoord**:    
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
 

