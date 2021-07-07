---
title: Een Azure-plan maken
description: Ontwikkelaars kunnen Azure-abonnementen programmatisch kopen, maken en beheren met behulp Partner Center API's.
ms.date: 01/02/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: mowrim
ms.author: mowrim
ms.openlocfilehash: f329b6a3f9a61522a9fad1f0ead021563c393118
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973403"
---
# <a name="create-an-azure-plan"></a>Een Azure-plan maken

U kunt een Azure-abonnement kopen, maken en beheren met behulp van Partner Center API's. Het proces is vergelijkbaar met het maken van een Microsoft Azure (MS-AZR-0145P). U moet [het catalogusitem voor het Azure-plan downloaden](#get-the-catalog-item-for-azure-plan)en [vervolgens een order maken en verzenden.](#create-and-submit-an-order)

## <a name="prerequisites"></a>Vereisten

* [Partner Center](partner-center-authentication.md) verificatiereferenties. Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.
* De klant-id. Als u geen klant-id hebt, volgt u de stappen in [Een lijst met klanten op halen.](get-a-list-of-customers.md) U kunt zich ook aanmelden bij Partner Center, de klant kiezen in de lijst met klanten, **Account** selecteren en vervolgens hun **Microsoft-id opslaan.**
* [Bevestiging van de acceptatie van de Microsoft-klantovereenkomst](/partner-center/confirm-customer-agreement).

## <a name="get-the-catalog-item-for-azure-plan"></a>Het catalogusitem voor het Azure-plan downloaden

Voordat u een Azure-plan voor een klant kunt maken, moet u het bijbehorende catalogusitem ophalen. U kunt het catalogusitem ophalen met behulp van de bestaande Partner Center catalogus-API's met de volgende resourcemodellen.

* **[Product:](product-resources.md#product)** een groeperingsconsistente voor opschatbare goederen of services. Een product zelf is geen opschatbaar item.
* **[SKU:](product-resources.md#sku)** een opschatbare Stock Keeping Unit (SKU) onder een product. SKU's vertegenwoordigen de verschillende vormen van het product.
* **[Beschikbaarheid:](product-resources.md#availability)** een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land, valuta of branchesegment).

Voltooi de volgende stappen om het catalogusitem voor een Azure-plan op te halen:

1. De product-id *voor het* Azure-plan identificeren en ophalen. Volg de stappen in [Een lijst met producten op halen en](get-a-list-of-products.md) geef **targetView** op **als MicrosoftAzure**. (Als u de *product-id* voor het Azure-abonnement al kent, kunt u in plaats daarvan de stappen in Een product kopen met behulp van de [product-id](get-a-product-by-id.md) volgen.)

2. Haal de **SKU op** uit het product voor het Azure-plan. Volg de stappen in [Een lijst met SKU's voor een product op halen.](get-a-list-of-skus-for-a-product.md) Als u de SKU-id voor het Azure-plan al kent, kunt u in plaats daarvan de stappen in Een SKU kopen met behulp van [de SKU-id](get-a-sku-by-id.md) volgen.

3. Haal de **beschikbaarheid op** uit de SKU voor het Azure-plan. Volg de stappen in [Een lijst met beschikbaarheid voor een SKU op te halen.](get-a-list-of-availabilities-for-a-sku.md) Als u de id voor de beschikbaarheid die u nodig hebt al kent, kunt u de stappen in Een beschikbaarheid krijgen volgen met behulp van de [beschikbaarheids-id.](get-an-availability-by-id.md) *Noteer de waarde van de eigenschap **CatalogItemId** van de beschikbaarheid voor het Azure-plan. U hebt deze waarde nodig om een order te maken.*

## <a name="create-and-submit-an-order"></a>Een order maken en verzenden

Volg deze stappen om uw bestelling voor een Azure-plan in te dienen:

1. [Maak een winkelwagen](create-a-cart.md) voor de verzameling catalogusitems die u wilt kopen. Wanneer u een [winkelwagen maakt,](cart-resources.md#cart)worden de [winkelwagenregelitems](cart-resources.md#cartlineitem) automatisch gegroepeerd op basis van wat samen in dezelfde order kan worden [gekocht.](order-resources.md#order) (U kunt ook [een winkelwagen bijwerken.)](update-a-cart.md)

2. [Bekijk de winkelwagen](checkout-a-cart.md), wat resulteert in het maken van een [order](order-resources.md#order).

## <a name="get-order-details"></a>Ordergegevens op halen

U kunt [de details van een afzonderlijke order ophalen met behulp van de order-id](get-an-order-by-id.md). U kunt ook [een lijst met alle orders voor een specifieke klant ophalen.](get-all-of-a-customer-s-orders.md)

>[!NOTE]
>Nadat een order is verzonden, is er een vertraging van maximaal 15 minuten voordat de order wordt weergegeven in de orderlijst van die klant.

## <a name="manage-azure-plans"></a>Azure-abonnementen beheren

Nadat de order is verwerkt, wordt er Partner Center **abonnementsresource** gemaakt voor het Azure-plan. U kunt de volgende methoden gebruiken voor het beheren Partner Center **abonnementsbronnen** om het Azure-plan te beheren:

* [De abonnementen van een klant ophalen](get-all-of-a-customer-s-subscriptions.md)
* [Een lijst met abonnementen op basis van bestelling ophalen](get-a-list-of-subscriptions-by-order.md)

Wanneer een Azure-plan wordt gemaakt in Partner Center, wordt er ook een bijbehorend Azure-gebruiksabonnement gemaakt in Azure. U kunt ook extra Azure-gebruiksabonnementen maken onder hetzelfde Azure-plan met behulp Azure Portal en Azure-API's. U kunt de id's van alle Azure-gebruiksabonnementen die zijn gekoppeld aan een Azure-plan, verkrijgen door de stappen te volgen in Een lijst met Azure-rechten voor uw [Partner Center verkrijgen](get-a-list-of-azure-entitlements-for-subscription.md)

## <a name="lifecycle-management"></a>Levenscyclusbeheer

U kunt een bestaand Azure-plan opschorten door de stappen in [Abonnement opschorten te volgen.](suspend-a-subscription.md)

*U kunt een bestaand Azure-plan alleen opschorten als er geen actieve gebruiksactiva meer aan zijn gekoppeld, waaronder Azure-gebruiksabonnementen en Azure-reserveringen.*

Zie Azure API voor levenscyclusbeheer van abonnementen voor meer informatie over het uitschakelen van [Azure-gebruiksabonnementen.](/rest/api/resources/subscriptions)

Als u bestaande Azure-reserveringen wilt verwijderen, moet [u de reserveringen annuleren.](/partner-center/azure-reservations-manage#cancel-or-exchange-a-reservation)
Nadat u een Azure-plan hebt opgeschort, kunt u het opnieuw activeren.

Zie Een tijdelijk abonnement opnieuw activeren voor meer informatie over het opnieuw activeren [van een Azure-abonnement](reactivate-a-suspended-a-subscription.md)

## <a name="transition-existing-csp-offers-to-azure-plan"></a>Bestaande CSP-aanbiedingen overzetten naar Azure-plan 

U kunt geen Azure-plan maken voor een bestaande klant met een Microsoft Azure-abonnement (MS-AZR-0145P). U kunt [een klant echter vanuit hun bestaande CSP Azure-oplossingen overzetten naar Azure-services onder het Azure-plan](/partner-center/azure-plan-transition) in de nieuwe commerce-ervaring in het CSP-programma vanuit het partnercentrum. Als u een bestaande klant wilt overzetten, gebruikt u de productupgrade-API's om de volgende stappen uit te voeren:

* [Controleren of de klant in aanmerking komt voor een overgang naar Azure-plan](get-eligibility-for-product-upgrade.md)
* [Een productupgrade initiëren voor de klant](create-product-upgrade-entity.md)
* [De status van de productupgrade controleren](get-product-upgrade-status.md)

## <a name="azure-spending"></a>Uitgaven voor Azure

U kunt uw [Azure-uitgaven bijhouden door](azure-spending.md) een query uit te voeren voor gebruiksoverzicht en gedetailleerde gebruiksrecords met behulp van de volgende methoden:

* [Gebruiksoverzicht van partner ophalen](get-a-partner-usage-summary.md)
* [Alle klantgebruiksrecords voor een partner ophalen](get-a-customer-s-usage-records.md)
* [Gebruiksoverzicht van klant ophalen](get-a-customer-usage-summary.md)
* [Alle gebruiksrecords voor abonnementen voor een klant ophalen](get-a-customer-subscription-s-usage-records.md)
* [Samenvatting van gebruik van abonnement ophalen](get-a-customer-subscription-usage-summary.md)
* [Gebruiksgegevens voor het abonnement per bron ophalen](get-a-customer-subscription-resource-usage-records.md)
* [Gebruiksgegevens voor het abonnement per meter ophalen](get-a-customer-subscription-meter-usage-records.md)
* [Bronnen voor metergebruiksrecords ophalen](meter-usage-resources.md)
* [Bronnen voor brongebruiksrecords ophalen](resource-usage-resources.md)

U kunt ook het budget voor klantgebruik instellen en beheren met behulp van de volgende methoden:

* [Klantgebruiksbudget ophalen](get-a-customer-s-usage-spending-budget.md)
* [Klantgebruiksbudget bijwerken](update-a-customer-s-usage-spending-budget.md)

## <a name="invoice-and-reconciliation"></a>Factuur en afstemming

U kunt facturen en afstemmingsgegevens beheren met de volgende methoden:

* [Een verzameling facturen ophalen](get-a-collection-of-invoices.md)
* [Koppelingen voor factuurramingen ophalen](get-invoice-estimate-links.md)
* [Factuur op id ontvangen](get-invoice-by-id.md)
* [Factuur ophalen](get-invoice-statement.md)
* [Factuuroverzichten ophalen](get-invoice-summaries.md)
* [Regelitems gefactureerd verbruik ophalen](get-invoice-billed-consumption-lineitems.md)
* [Regelitems ongefactureerd verbruik ophalen](get-invoice-unbilled-consumption-lineitems.md)
* [Gefactureerde recon line-items op factuur ontvangen](get-invoiceline-items.md)
* [Regelitems ongefactureerde reconciliatie ophalen](get-invoice-unbilled-recon-lineitems.md)
