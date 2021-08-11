---
title: Richtlijnen voor API-beperking
description: Voor partners die Partner Center API's aanroepen, moet u weten welke API's worden beïnvloed door microsoft API-beperking en best practices om beperking te voorkomen of beter af te handelen.
ms.date: 04/14/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: vijvala
ms.author: vijvala
ms.openlocfilehash: 4eead16c5bb2b01f0fba85e30ea35fbcdae9d5a6682872eecfeeb9e47f43d324
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115993755"
---
# <a name="api-throttling-guidance-for-partners-calling-partner-center-apis"></a>Richtlijnen voor API-beperking voor partners die api'Partner Center aanroepen 

Microsoft implementeert API-beperking om binnen een tijdspanne consistentere prestaties mogelijk te maken voor partners die de api'Partner Center aanroepen. Beperking beperkt het aantal aanvragen naar een service in een tijdsspanne om te voorkomen dat resources te veel worden gebruikt. Hoewel Partner Center is ontworpen voor het verwerken van een groot aantal aanvragen, helpt beperking bij een groot aantal aanvragen van enkele partners om optimale prestaties en betrouwbaarheid voor alle partners te behouden.  

Beperkingslimieten variëren afhankelijk van het scenario. Als u bijvoorbeeld een groot aantal schrijfvolumes gebruikt, is de kans op bandbreedtebeperking groter dan wanneer u alleen lees- en schrijf- of schrijfvolumes gebruikt.

## <a name="what-happens-when-throttling-occurs"></a>Wat gebeurt er wanneer beperking optreedt? 

Wanneer een drempelwaarde voor bandbreedtebeperking wordt overschreden, Partner Center verdere aanvragen van die client voor een bepaalde periode beperkt. Beperkingsgedrag is afhankelijk van het type en het aantal aanvragen.   

### <a name="common-throttling-scenarios"></a>Veelvoorkomende beperkingsscenario's 

De meest voorkomende oorzaken van beperking van clients zijn: 

- Een groot aantal aanvragen voor een **API per partner-tenant-id:** voor sommige Partner Center-API's wordt beperking bepaald door de tenant-id van de partner. Te veel aanroepen naar deze API's op dezelfde tenant-id van de partner leiden ertoe dat de drempelwaarde voor beperking wordt overschreden.  

- Een groot aantal aanvragen voor een **API per partner-tenant-id per** tenant-id van de klant: voor andere API's wordt de beperking bepaald door de combinatie partner-tenant-id/tenant-id van de klant; In dergelijke gevallen leidt te veel aanroepen naar dezelfde tenant-id van de klant tot beperking, terwijl aanroepen tegen andere klanten kunnen slagen.

## <a name="best-practices-to-avoid-throttling"></a>Best practices om beperking te voorkomen 
 
Programmeerprocedures zoals het continu peilen van een resource om te controleren op updates en het regelmatig scannen van resourceverzamelingen om te controleren op nieuwe of verwijderde resources, leiden waarschijnlijk tot beperking en zullen de algehele prestaties verslechteren. Gelijktijdige API-aanroepen kunnen leiden tot een groot aantal aanvragen per eenheidstijd, waardoor aanvragen ook worden beperkt. In plaats daarvan moet u de meldingen voor bijhouden en wijzigen gebruiken. Daarnaast moet u activiteitenlogboeken kunnen gebruiken voor het detecteren van wijzigingen. Zie activiteitenlogboeken voor [Partner Center meer informatie.](get-a-record-of-partner-center-activity-by-user.md)  We raden partners ten zeerste aan om de API voor activiteitenlogboek te gebruiken voor meer efficiëntie en om beperking te voorkomen. Zie ook het voorbeeld van het gebruik van activiteitenlogboeken hieronder.

## <a name="best-practices-to-handle-throttling"></a>Best practices voor het afhandelen van beperkingen

Hier volgen de best practices voor het afhandelen van bandbreedtebeperking: 

- Verminder de mate van parallellelisme. 
- Verminder de frequentie van aanroepen. 
- Vermijd onmiddellijke nieuwe aanvragen omdat alle aanvragen worden opgeteld bij uw gebruikslimieten. 

Gebruik de HTTP-foutcode 429 om beperking te detecteren wanneer u foutafhandeling implementeert. Het mislukte antwoord bevat de Retry-After-antwoordheader. Het uitschakelen van aanvragen met behulp van de vertraging na opnieuw proberen is de snelste manier om te herstellen van bandbreedtebeperking. 

Ga als volgt te werk als u de vertraging Opnieuw proberen na wilt gebruiken: 

1. Wacht het aantal seconden dat is opgegeven in de Retry-After koptekst. 

2. De aanvraag opnieuw proberen.  

3. Als de aanvraag opnieuw mislukt met een 429-foutcode, wordt u nog steeds beperkt. Opnieuw proberen met exponentieel uitstel, gebruik de aanbevolen Retry-After uit te stellen en de aanvraag opnieuw uit te proberen totdat deze is geslaagd.

4. Als u de SDK gebruikt, ontvangt u een uitzondering met statuscode 429 wanneer uw aanvraag wordt beperkt. Gebruik de eigenschap RetryAfter in de uitzondering en de aanvraag opnieuw nadat de tijd is verstreken.


## <a name="apis-currently-impacted-by-throttling"></a>API's die momenteel worden beïnvloed door beperking

Uiteindelijk wordt elke api Partner Center die het eindpunt 'api.partnercenter.microsoft.com/' aanroept, beperkt. Op dit moment worden de beperkingslimieten alleen afgedwongen voor de HIERONDER vermelde API's. Partner Center verzamelt de telemetrie op elk van de API's en past de beperkingslimieten dynamisch aan. De volgende tabel bevat de API's waar beperking momenteel wordt afgedwongen.  


|**Bewerking**| **Documentatie voor Partnercentrum**|
|------------------------|----------------------------|
|{baseURL}/v1/customers/{customer_id}/orders|[een order maken](create-an-order.md)|
|{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/upgrades|[een abonnement overstappen](transition-a-subscription.md)|
|{baseURL}/v1/customers/{customer-tenant-id}/orders/{order-id}|[een invoegaanvoeging aanschaffen voor een abonnement](purchase-an-add-on-to-a-subscription.md)|
|{baseURL}/v1/customers/{customer-id}/carts/{cart-id}|[een winkelwagen maken](create-a-cart.md)|
|{baseURL}/v1/customers/{customer-id}/carts/{cart-id}/checkout|[een winkelwagen uitchecken](checkout-a-cart.md)|
|{baseURL}/v1/customers/{customer-id}/carts/{cart-id}|[een winkelwagen bijwerken](update-a-cart.md)|
|{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrations|[een abonnement registreren](register-a-subscription.md)|
|{baseURL}/v1/productupgrades|[entiteit productupgrade maken](create-product-upgrade-entity.md)|
|{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions |[Een proefabonnement converteren naar betaald](convert-a-trial-subscription-to-paid.md)|
|{baseURL}/v1/customers/{customer-tenant-id}|[een klant op id krijgen](get-a-customer-by-id.md)|
|{baseURL}/v1/productUpgrades/geschiktheid|[geschiktheid voor productupgrade krijgen](get-eligibility-for-product-upgrade.md)|
|{baseURL}/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} |[abonnement beheren](manage-orders.md#manage-a-subscription)|
|{baseURL}/v1/customers/{customer_id}/subscriptions |[get-all-of-a-customer-s-subscriptions](get-all-of-a-customer-s-subscriptions.md)|
|{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}|[Een abonnement ophalen op basis van id](get-a-subscription-by-id.md)|
|{baseURL}/v1/customers/{customer_id}/orders|[Alle klantorders ontvangen](get-all-of-a-customer-s-orders.md)|
|{baseURL}/v1/customers/{customer_id}/orders/{order_id}|[Een bestelling ophalen op basis van id](get-an-order-by-id.md)|
|{baseURL}/v1/customers/{customer_id}/orders/{order_id}/provisioningstatus|[De inrichtingsstatus van het abonnement ophalen](get-subscription-provisioning-status.md)|
|{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}|[Orders beheren en een abonnement beheren](manage-orders.md#manage-a-subscription)|
|{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}/addons|[Een lijst met invoegtoepassingen voor een abonnement ophalen](get-a-list-of-add-ons-for-a-subscription.md)|
|{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}/azureEntitlements|[Een lijst met Azure-rechten voor een abonnement op halen](get-a-list-of-azure-entitlements-for-subscription.md)|
|{baseURL}/v1/customers/{customer_id}/subscriptions/{subscription_id}/registrationstatus|[De registratiestatus van het abonnement ophalen](get-subscription-registration-status.md)|
|{baseURL}/v1/customers/{customer-tenant-id}/transfers|[Alle overdrachten van een klant krijgen](get-all-of-a-customer-s-transfers.md)|
|{baseURL}/v1/productUpgrades/{upgrade-id}/status|[Upgradestatus van product ophalen](get-product-upgrade-status.md)|
|{baseURL}/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions|[Een lijst met aanbiedingen voor omzetten van de proefversie ophalen](get-a-list-of-trial-conversion-offers.md)|


### <a name="error-code-response"></a>Antwoord van foutcode:
```http
HTTP/1.1 429 Too Many Requests 

Content-Length: 84 

Content-Type: application/json 

Retry-After: 57 

Date: Tue, 21 Jul 2020 04:10:58 GMT 

{ "statusCode": 429, "message": "Rate limit is exceeded. Try again in 57 seconds." } 
```

## <a name="example-of-activity-log"></a>Voorbeeld van activiteitenlogboek

Voor best practice het analyseren van dagelijkse wijzigingen, raden we u aan om een query uit te voeren op auditrecords voor een specifieke dag. 

In het antwoord krijgt u een resultaat met wijzigingen in het specifieke bewerkingstype.U kunt filteren op basis van de bewerking die u belangrijk vindt. Als u bijvoorbeeld geïnteresseerd bent in een nieuwe klant, kunt u operationType = "add_customer" bekijken.  

De lijst met operationtype/resources vindt u in de onderstaande API-documenten.  

- [Resources controleren](auditing-resources.md)  

- [Een record van een Partner Center per gebruiker](get-a-record-of-partner-center-activity-by-user.md)  



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

**Antwoord:**    
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
 

