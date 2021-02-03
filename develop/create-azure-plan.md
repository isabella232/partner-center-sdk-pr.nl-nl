---
title: Een Azure-abonnement maken
description: Ontwikkel aars kunnen Azure-abonnementen via de partner centrum-Api's kopen, maken en beheren.
ms.date: 01/02/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: mowrim
ms.author: mowrim
ms.openlocfilehash: 372b94ac7217899ca560cf943bf11a7e8906872d
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767366"
---
# <a name="create-an-azure-plan"></a>Een Azure-abonnement maken

**Van toepassing op:**

* Partnercentrum

U kunt een Azure-abonnement kopen, maken en beheren met de Api's van het partner centrum. Het proces is vergelijkbaar met het maken van een Microsoft Azure-abonnement (MS-AZR-0145P). U moet [het catalogus item voor het Azure-abonnement ophalen](#get-the-catalog-item-for-azure-plan) [en vervolgens een bestelling maken en verzenden](#create-and-submit-an-order).

## <a name="prerequisites"></a>Vereisten

* Verificatie referenties voor het [partner centrum](partner-center-authentication.md) . Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.
* De klant-id. Als u geen klant-id hebt, volgt u de stappen in [een lijst met klanten ophalen](get-a-list-of-customers.md). U kunt zich ook aanmelden bij het partner centrum, de klant kiezen uit de lijst met klanten, **account** selecteren en vervolgens hun **micro soft-id** opslaan.
* [Bevestiging van de acceptatie van de micro soft-klant overeenkomst door de klant](/partner-center/confirm-customer-agreement).

## <a name="get-the-catalog-item-for-azure-plan"></a>Het catalogus item voor Azure-abonnement ophalen

Voordat u een Azure-abonnement voor een klant kunt maken, moet u het bijbehorende catalogus item ophalen. U kunt het catalogus item ophalen met behulp van de bestaande partner centrum-catalogus-Api's met de volgende bron modellen.

* **[Product](product-resources.md#product)**: een groeperings constructie voor tevens goederen of-services. Een product zelf is geen tevens-item.
* **[SKU](product-resources.md#sku)**: een SKU (Stock Keeping Unit) onder een product. Sku's vertegenwoordigen de verschillende vormen van het product.
* **[Beschik baarheid](product-resources.md#availability)**: een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land-, valuta-of sector segment).

Voer de volgende stappen uit om het catalogus item voor een Azure-abonnement te verkrijgen:

1. Identificeer en haal de *product* -id voor het Azure-abonnement op. Volg de stappen in [een lijst met producten ophalen](get-a-list-of-products.md) en geef de **TargetView** op als **MicrosoftAzure**. (Als u al bekend bent met de *product* -id voor het Azure-abonnement, kunt u de stappen in [een product ophalen met behulp van de product-id](get-a-product-by-id.md) in plaats daarvan volgen.)

2. Haal de **SKU** op uit het product voor het Azure-abonnement. Volg de stappen in [een lijst met sku's voor een product ophalen](get-a-list-of-skus-for-a-product.md). Als u de SKU-id voor het Azure-abonnement al kent, kunt u de stappen in [een SKU ophalen met behulp van de SKU-id](get-a-sku-by-id.md) in plaats daarvan volgen.

3. De **Beschik baarheid** ophalen uit de SKU voor het Azure-abonnement. Volg de stappen in [een lijst met Beschik baarheid voor een SKU ophalen](get-a-list-of-availabilities-for-a-sku.md). Als u al bekend bent met de id voor de beschik baarheid die u nodig hebt, kunt u de stappen volgen in een Beschik baarheid [ophalen met behulp van de beschikbaarheids-id](get-an-availability-by-id.md) . *Noteer de waarde van de eigenschap **CatalogItemId** van de beschik baarheid van het Azure-abonnement. U hebt deze waarde nodig om een order te maken.*

## <a name="create-and-submit-an-order"></a>Een order maken en verzenden

Voer de volgende stappen uit om uw bestelling voor een Azure-abonnement in te dienen:

1. [Maak een mandje](create-a-cart.md) om de verzameling catalogus items te bewaren die u wilt kopen. Wanneer u een [winkel wagen](cart-resources.md#cart)maakt, worden de [Winkelwagen regel items](cart-resources.md#cartlineitem) automatisch gegroepeerd op basis van wat er in dezelfde [volg orde](order-resources.md#order)kan worden aangeschaft. (U kunt ook [een winkel wagen bijwerken](update-a-cart.md).)

2. [Bekijk de winkel wagen](checkout-a-cart.md), wat resulteert in het maken van een [order](order-resources.md#order).

## <a name="get-order-details"></a>Bestellingsgegevens ophalen

U kunt [de details van een afzonderlijke order ophalen met behulp van de order-id](get-an-order-by-id.md). U kunt ook [een lijst met alle orders voor een specifieke klant ophalen](get-all-of-a-customer-s-orders.md).

>[!NOTE]
>Nadat een order is verzonden, is er een vertraging van Maxi maal 15 minuten voordat de order wordt weer gegeven in de order lijst van die klant.

## <a name="manage-azure-plans"></a>Azure-abonnementen beheren

Nadat de bestelling is verwerkt, wordt er een resource voor het **abonnement** op partner centrum voor het Azure-plan gemaakt. U kunt de volgende methoden gebruiken voor het beheren van het Azure-abonnement voor het beheren van de **abonnements** resources van uw partner centrum:

* [De abonnementen van een klant ophalen](get-all-of-a-customer-s-subscriptions.md)
* [Een lijst met abonnementen op basis van bestelling ophalen](get-a-list-of-subscriptions-by-order.md)

Wanneer een Azure-abonnement wordt gemaakt in Partner Center, wordt er ook een bijbehorend Azure Usage-abonnement in azure gemaakt. U kunt ook extra Azure-gebruiks abonnementen maken onder hetzelfde Azure-abonnement met behulp van Azure Portal en Azure Api's. U kunt de id's ophalen van alle Azure-gebruiks abonnementen die aan een Azure-abonnement zijn gekoppeld met behulp van de stappen in [een lijst met Azure-rechten voor het Partner Center-abonnement ophalen](get-a-list-of-azure-entitlements-for-subscription.md)

## <a name="lifecycle-management"></a>Levenscyclus beheer

U kunt een bestaand Azure-abonnement opschorten door de stappen in [een abonnement opschorten](suspend-a-subscription.md)te volgen.

*U kunt een bestaand Azure-abonnement alleen onderbreken als er geen actieve verbruiks activa meer aan zijn gekoppeld, met inbegrip van Azure-gebruiks abonnementen en Azure-reserve ringen.*

Zie voor meer informatie over het uitschakelen van Azure-gebruiks abonnementen [Azure API voor het beheer van de levens cyclus van abonnementen](/rest/api/resources/subscriptions).

Als u bestaande Azure-reserve ringen wilt verwijderen, moet u [de reserve ringen annuleren](/partner-center/azure-reservations-manage#cancel-or-exchange-a-reservation).
Nadat u een Azure-abonnement hebt opgeschort, kunt u het opnieuw activeren.

Zie [een opgeschort abonnement opnieuw activeren](reactivate-a-suspended-a-subscription.md) voor meer informatie over hoe u een Azure-abonnement opnieuw activeert.

## <a name="transition-existing-csp-offers-to-azure-plan"></a>Bestaande CSP-aanbiedingen overzetten naar Azure-plan 

U kunt geen Azure-plan maken voor een bestaande klant met een Microsoft Azure-abonnement (MS-AZR-0145P). U kunt [een klant echter vanuit hun bestaande CSP Azure-oplossingen overzetten naar Azure-services onder het Azure-plan](/partner-center/azure-plan-transition) in de nieuwe commerce-ervaring in het CSP-programma vanuit het partnercentrum. Als u een bestaande klant wilt overzetten, gebruikt u de productupgrade-API's om de volgende stappen uit te voeren:

* [Controleren of de klant in aanmerking komt voor een overgang naar Azure-plan](get-eligibility-for-product-upgrade.md)
* [Een productupgrade initiëren voor de klant](create-product-upgrade-entity.md)
* [De status van de productupgrade controleren](get-product-upgrade-status.md)

## <a name="azure-spending"></a>Uitgaven voor Azure

Met de volgende methoden kunt u [Azure-uitgaven](azure-spending.md) bijhouden door query's uit te zoeken voor gebruiks samenvatting en gedetailleerde gebruiks records:

* [Gebruiksoverzicht van partner ophalen](get-a-partner-usage-summary.md)
* [Alle klantgebruiksrecords voor een partner ophalen](get-a-customer-s-usage-records.md)
* [Gebruiksoverzicht van klant ophalen](get-a-customer-usage-summary.md)
* [Alle gebruiksrecords voor abonnementen voor een klant ophalen](get-a-customer-subscription-s-usage-records.md)
* [Samenvatting van gebruik van abonnement ophalen](get-a-customer-subscription-usage-summary.md)
* [Gebruiksgegevens voor het abonnement per bron ophalen](get-a-customer-subscription-resource-usage-records.md)
* [Gebruiksgegevens voor het abonnement per meter ophalen](get-a-customer-subscription-meter-usage-records.md)
* [Bronnen voor metergebruiksrecords ophalen](meter-usage-resources.md)
* [Bronnen voor brongebruiksrecords ophalen](resource-usage-resources.md)

U kunt ook het klant gebruiks budget instellen en beheren met behulp van de volgende methoden:

* [Klantgebruiksbudget ophalen](get-a-customer-s-usage-spending-budget.md)
* [Klantgebruiksbudget bijwerken](update-a-customer-s-usage-spending-budget.md)

## <a name="invoice-and-reconciliation"></a>Factuur en reconciliatie

U kunt met behulp van de volgende methoden facturen en reconciliatie gegevens beheren:

* [Een verzameling facturen ophalen](get-a-collection-of-invoices.md)
* [Koppelingen voor factuurramingen ophalen](get-invoice-estimate-links.md)
* [Factuur op ID ophalen](get-invoice-by-id.md)
* [Factuur ophalen](get-invoice-statement.md)
* [Factuuroverzichten ophalen](get-invoice-summaries.md)
* [Regelitems gefactureerd verbruik ophalen](get-invoice-billed-consumption-lineitems.md)
* [Regelitems ongefactureerd verbruik ophalen](get-invoice-unbilled-consumption-lineitems.md)
* [Factuur afstemmings regel items factureren ophalen](get-invoiceline-items.md)
* [Regelitems ongefactureerde reconciliatie ophalen](get-invoice-unbilled-recon-lineitems.md)
