---
title: Een relatie als reseller met een klant verwijderen
description: Een reseller-relatie verwijderen met een klant waarbij u geen trans acties meer hebt.
ms.date: 01/12/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 084797997e57c63b5c447379bb08ecb88ebd0cc4
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767462"
---
# <a name="remove-a-reseller-relationship-with-a-customer"></a>Een relatie als reseller met een klant verwijderen

**Van toepassing op**

- Partnercentrum

Een wederverkoper-relatie verwijderen met een klant waarbij u geen trans acties meer hebt.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Alle door Azure gereserveerde VM-exemplaar orders moeten worden geannuleerd voordat een reseller-relatie wordt verwijderd. Neem contact op met Azure-ondersteuning voor het annuleren van openstaande Azure gereserveerde VM-instantie orders.

## <a name="c"></a>C\#

Als u de reseller-relatie voor een klant wilt verwijderen, moet u er eerst voor zorgen dat alle actieve Azure Reserved VM Instances voor die klant worden geannuleerd. Zorg er vervolgens voor dat alle actieve abonnementen voor die klant worden opgeschort. Om dit te doen, bepaalt u de ID van de klant voor wie u de reseller-relatie wilt verwijderen. In het volgende code voorbeeld wordt de gebruiker gevraagd de klant-id op te geven.

Om te bepalen of een Azure Reserved VM Instances voor de klant moet worden geannuleerd, haalt u de verzameling rechten op door de [**IAggregatePartner. Customers. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan te roepen met behulp van de klant-id om de klant op te geven, en de eigenschap [**rechten**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) om een interface op te halen voor de verzamelings bewerkingen van rechten. Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) aan om de rechtings verzameling op te halen. De verzameling filteren op rechten met een [**EntitlementType**](entitlement-resources.md#entitlementtype) -waarde van [**EntitlementType. VirtualMachineReservedInstance**](entitlement-resources.md#entitlementtype) en, indien aanwezig, annuleren door ondersteuning aan te roepen voordat u doorgaat.

Vervolgens haalt u een verzameling van de abonnementen van de klant op door de [**IAggregatePartner. Customers. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan te roepen met behulp van de klant-id om de klant op te geven, en de eigenschap [**abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) om een interface op te halen voor het verzamelen van abonnementen. Roep ten slotte de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) aan om de abonnementen verzameling van de klant op te halen. Blader door de abonnements verzameling en zorg ervoor dat geen van de abonnementen een abonnement heeft. eigenschaps waarde voor [**status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) van [**SubscriptionStatus. Active**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus). Als een abonnement nog steeds actief is, raadpleegt u [een abonnement opschorten](https://review.docs.microsoft.com/partner-center/develop/suspend-a-subscription) voor informatie over hoe u dit kunt onderbreken.

Nadat u hebt gecontroleerd of alle actieve Azure Reserved VM Instances voor die klant zijn geannuleerd en alle actieve abonnementen zijn onderbroken, kunt u de reseller-relatie voor de klant verwijderen. Maak eerst een nieuw object [klant/DotNet/API/Microsoft. Store. partnercenter. Models. klanten. Customer) met de eigenschap [Customer. RelationshipToPartner/DotNet/API/micro soft. Store. partnercenter. Models. custom. Customer. RelationshipToPartner) ingesteld op [**CustomerPartnerRelationship. none**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerpartnerrelationship). Vervolgens roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant op te geven en de **patch** -methode aan te roepen, in het nieuwe klant object door te geven.

Als u de relatie opnieuw tot stand wilt brengen, herhaalt u het proces van [een reseller Relationship/Partner Center/partnership/Request-reseller-Relationship).

``` csharp
// IAggregatePartner partnerOperations;

// Prompt the user the enter the customer ID.
var customerIdToDeleteRelationshipOf = this.Context.ConsoleHelper.ReadNonEmptyString("Please enter the ID of the customer you want to delete the relationship with", "The customer ID can't be empty");

// Determine if there are any active Azure Reserved VM Instances for this customer.
ResourceCollection<Entitlement> entitlements = partnerOperations.Customers.ById(customerIdToDeleteRelationshipOf).Entitlements.Get();

If (entitlements.Items.Where(x => x.EntitlementType == EntitlementType.VirtualMachineReservedInstance).Any())
{
    this.Context.ConsoleHelper.Warning("Please cancel Azure Reserved Virtual Machine Instance orders through support and try again. Aborting the delete customer relationship operation");
               return;
}

// Verify that there are no active subscriptions.
ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(customerIdToDeleteRelationshipOf).Subscriptions.Get();
IList<Subscription> subscriptions = new List<Subscription>(customerSubscriptions.Items);

foreach (Subscription customerSubscription in subscriptions)
{
    if (customerSubscription.Status == SubscriptionStatus.Active)
    {
        this.Context.ConsoleHelper.Warning(String.Format("Subscription with ID :{0}  OfferName: {1} cannot be in active state, ", customerSubscription.Id, customerSubscription.OfferName));
        this.Context.ConsoleHelper.Warning("Please Suspend all the Subscriptions and try again. Aborting the delete customer relationship operation");
               return;
    }
}

// Delete the customer's relationship to the partner.
Customer customer = new Customer();
customer.RelationshipToPartner = CustomerPartnerRelationship.None;
customer = partnerOperations.Customers.ById(customerIdToDeleteRelationshipOf).Patch(customer);

if (customer.RelationshipToPartner == CustomerPartnerRelationship.None)
{
    this.Context.ConsoleHelper.Success("Customer Partner Relationship successfully deleted");
}
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: PartnerSDK. FeatureSample- **klasse**: DeletePartnerCustomerRelationship.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode     | Aanvraag-URI                                                                                                                           |
|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| **VERZENDEN**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Deze tabel bevat de vereiste query parameters voor het verwijderen van een reseller-relatie.

| Naam                   | Type     | Vereist | Beschrijving                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| **klant-Tenant-id** | **guid** | J        | De waarde is een **klant-Tenant-id** die de klant aanduidt. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Een **klant** resource is vereist in de aanvraag tekst. Zorg ervoor dat de eigenschap **RelationshipToPartner** is ingesteld op geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id> HTTP/1.1
Authorization: Bearer <token>
Content-Length: 74
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9b4bf2ca-f374-4d51-9113-781ca87b8380
MS-RequestId: 9fef8b23-6e3e-45d2-8678-e9fe89c35af5
Date: Fri, 12 Jan 2018 00:31:55 GMT

{
    "relationshipToPartner":"none",
    "attributes":{
        "objectType":"Customer"
    }
}
```

## <a name="rest-response"></a>REST-antwoord

Als deze methode is geslaagd, wordt een reseller-relatie voor de opgegeven klant verwijderd.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
MS-RequestId: 7988dde4-b516-472c-b226-6d53fb18f04e
MS-CorrelationId: 9b4bf2ca-f374-4d51-9113-781ca87b8380
X-Locale: en-US
Content-Type: application/json
Content-Length: 242
Expect: 100-continue

{
    "Id":null,
    "CommerceId":null,
    "CompanyProfile":null,
    "BillingProfile":null,
    "RelationshipToPartner":"none",
    "AllowDelegatedAccess":null,
    "UserCredentials":null,
    "CustomDomains":null,
    "AssociatedPartnerId":null,
    "Attributes":{
        "ObjectType":"Customer"
    }
}
```
