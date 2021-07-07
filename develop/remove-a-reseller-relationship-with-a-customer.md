---
title: Een relatie als reseller met een klant verwijderen
description: Het verwijderen van een resellerrelatie met een klant met wie u geen transacties meer hebt.
ms.date: 01/12/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 45eca3564c3b9078e04d1f8155d08849a589d52f
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446595"
---
# <a name="remove-a-reseller-relationship-with-a-customer"></a>Een relatie als reseller met een klant verwijderen

Verwijder een resellerrelatie met een klant met wie u geen transacties meer hebt.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Alle orders voor gereserveerde VM-instanties van Azure moeten worden geannuleerd voordat een resellerrelatie wordt verwijderd. Roep ondersteuning voor Azure voor het annuleren van openstaande orders voor gereserveerde Azure-VM-instanties.

## <a name="c"></a>C\#

Als u de resellerrelatie voor een klant wilt verwijderen, moet u er eerst voor zorgen dat alle actieve Azure Reserved VM Instances voor die klant worden geannuleerd. Controleer vervolgens of alle actieve abonnementen voor die klant zijn opgeschort. Om dit te doen, bepaalt u de id van de klant voor wie u de resellerrelatie wilt verwijderen. In het volgende codevoorbeeld wordt de gebruiker gevraagd de klant-id op te geven.

Om te bepalen of een Azure Reserved VM Instances voor de klant moet worden geannuleerd, haalt u de verzameling rechten op door de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met behulp van de klant-id om de klant op te geven en de eigenschap [**Entitlements**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) om een interface voor rechtenverzamelingsbewerkingen op te halen. Roep de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) om de rechtenverzameling op te halen. Filter de verzameling op rechten met de waarde [**EntitlementType.VirtualMachineReservedInstance**](entitlement-resources.md#entitlementtype) en annuleer deze door ondersteuning aan te roepen voordat u doorgaat. [](entitlement-resources.md#entitlementtype)

Haal vervolgens een verzameling van de abonnementen van de klant op door de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met behulp van de klant-id om de klant op te geven en de eigenschap Abonnementen om een interface op te halen voor bewerkingen voor het verzamelen van abonnementen. [](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) Roep ten slotte de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) om de verzameling abonnementen van de klant op te halen. Doorkruis de abonnementsverzameling en zorg ervoor dat geen van de abonnementen de [**eigenschapswaarde Subscriptions.Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) van [**SubscriptionStatus.Active heeft.**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus) Als een abonnement nog steeds actief is, zie [Abonnement opschorten voor](suspend-a-subscription.md) informatie over het opschorten van het abonnement.

Nadat u hebt bevestigd dat alle actieve Azure Reserved VM Instances voor die klant zijn geannuleerd en alle actieve abonnementen zijn opgeschort, kunt u de resellerrelatie voor de klant verwijderen. Maak eerst een nieuw object [Customer/dotnet/api/microsoft.store.partnercenter.models.customers.customer) met de eigenschap [Customer.RelationshipToPartner/dotnet/api/microsoft.store.partnercenter.models.customers.customer.relationshiptopartner) ingesteld op [**CustomerPartnerRelationship.None.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerpartnerrelationship) Roep vervolgens de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met behulp van de klant-id om de klant op te geven en roep de **patchmethode** aan, waarbij het nieuwe klantobject wordt doorgeven.

Als u de relatie opnieuw tot stand wilt brengen, herhaalt u het proces van [een resellerrelatie aanvragen/partnercentrum/develop/request-reseller-relationship).

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

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project:** PartnerSDK.FeatureSample-klasse: DeletePartnerCustomerRelationship.cs 

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode     | Aanvraag-URI                                                                                                                           |
|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| **Patch**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/ HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Deze tabel bevat de vereiste queryparameters voor het verwijderen van een resellerrelatie.

| Naam                   | Type     | Vereist | Beschrijving                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| **customer-tenant-id** | **guid** | J        | De waarde is een in GUID **opgemaakte klant-tenant-id** die de klant identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Een **klantresource** is vereist in de aanvraag body. Zorg ervoor **dat de eigenschap RelationshipToPartner** is ingesteld op geen.

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

Als dit lukt, wordt met deze methode een resellerrelatie voor de opgegeven klant verwijderd.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

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
