---
title: Een abonnement maken voor commerciële marketplace-producten
description: Ontwikkelaars kunnen een abonnement voor commerciële marketplace-producten maken en beheren met behulp Partner Center API's.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7e7a4b96f509ae99cd4933963c04b0f660d7d76410ee86c31256c62b290f122f
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991375"
---
# <a name="create-a-subscription-for-commercial-marketplace-products"></a>Een abonnement maken voor commerciële marketplace-producten

U kunt een abonnement maken voor commerciële marketplace-producten met behulp Partner Center API's. U moet [een lijst met aanbiedingen voor een](#get-a-list-of-offers-for-a-market)markt ophalen, een order maken en verzenden voor een commerciële marketplace-abonnement en vervolgens een [](#create-and-submit-an-order) [activeringskoppeling ophalen.](#get-activation-link)

U kunt ook [levenscyclusbeheer uitvoeren en](#lifecycle-management) [facturen voor](#invoice-and-reconciliation) deze abonnementen beheren.

## <a name="prerequisites"></a>Vereisten

* [Partner Center](partner-center-authentication.md) verificatiereferenties. Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.
* De klant-id. Als u geen klant-id hebt, volgt u de stappen in [Een lijst met klanten op halen.](get-a-list-of-customers.md) U kunt zich ook aanmelden bij Partner Center, de klant kiezen in de lijst met klanten, **Account** selecteren en vervolgens hun **Microsoft-id opslaan.**

## <a name="get-a-list-of-offers-for-a-market"></a>Een lijst met aanbiedingen voor een markt ophalen

U kunt de beschikbare aanbiedingen voor een markt controleren met behulp van de Partner Center API-modellen:

* **[Product:](product-resources.md#product)** een groeperingsconsistente voor opschatbare goederen of services. Een product zelf is geen opschatbaar item.
* **[SKU:](product-resources.md#sku)** een opschatbare Stock Keeping Unit (SKU) onder een product. Deze vertegenwoordigen de verschillende vormen van het product.
* **[Beschikbaarheid:](product-resources.md#availability)** een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land, valuta of branchesegment).

Voordat u een Azure-reservering aanschaft, moet u de volgende stappen uitvoeren:

1. Identificeer en haal het product en de SKU op die u wilt kopen. Als u de product-id en SKU-id al kent, selecteert u deze.

    * [Een lijst met producten op halen](get-a-list-of-products.md)
    * [Een product op halen met behulp van de product-id](get-a-product-by-id.md)
    * [Een lijst met SKU's voor een product op halen](get-a-list-of-skus-for-a-product.md)
    * [Een SKU krijgen met behulp van de SKU-id](get-a-sku-by-id.md)

    > [!NOTE]
    > U kunt commerciële marketplace-producten identificeren op basis van hun **ProductType-eigenschap** **'Azure'** en hun **SubType-eigenschap** **van 'SaaS'.**

2. Als de SKU's zijn gelabeld met een **inventoryCheck-vereiste,** [controleert u de inventaris voor een SKU](check-inventory.md).

    > [!NOTE]
    > Op dit moment zijn er geen commerciële marketplace-producten die ondersteuning bieden voor voorraadcontrole of die zijn gelabeld met een **InventoryCheck-vereiste.**

3. Haal de beschikbaarheid voor de SKU op. U hebt de **CatalogItemId** van de beschikbaarheid nodig bij het plaatsen van de order, die u kunt ophalen via de volgende API's:

    * [Een lijst met beschikbaarheid voor een SKU op halen](get-a-list-of-availabilities-for-a-sku.md)
    * [Een beschikbaarheid krijgen met behulp van de beschikbaarheids-id](get-an-availability-by-id.md)

## <a name="create-and-submit-an-order"></a>Een order maken en verzenden

Volg deze stappen om uw Azure-reserveringsorder in te dienen:

1. [Maak een winkelwagen](create-a-cart.md) voor de verzameling catalogusitems die u wilt kopen. Wanneer u een [winkelwagen maakt,](cart-resources.md#cart)worden de winkelwagenregelitems automatisch gegroepeerd op basis van wat samen in dezelfde order kan worden [](cart-resources.md#cartlineitem) [gekocht.](order-resources.md#order) (U kunt ook [een winkelwagen bijwerken.)](update-a-cart.md)
2. [Bekijk de winkelwagen](checkout-a-cart.md), wat resulteert in het maken van een [order](order-resources.md#order).

### <a name="get-order-details"></a>Ordergegevens op halen

U kunt [de details van een afzonderlijke order ophalen met behulp van de order-id](get-an-order-by-id.md). U kunt ook [een lijst met alle orders voor een specifieke klant ophalen.](get-all-of-a-customer-s-orders.md)

> [!NOTE]
> Nadat een order is verzonden, is er een vertraging van maximaal 15 minuten voordat de order wordt weergegeven in de orderlijst van die klant.

## <a name="get-activation-link"></a>Activeringskoppeling krijgen

De partner of klant moet abonnementen activeren voor Azure Marketplace producten. U kunt [een activeringskoppeling krijgen via orderregelitem](get-activation-link-by-order-line-item.md). U kunt ook [een abonnement op id krijgen](get-a-subscription-by-id.md)en vervolgens de eigenschap **Koppelingen** opsnoemen om een activeringskoppeling te maken.

## <a name="lifecycle-management"></a>Levenscyclusbeheer

U kunt de levenscyclus van uw abonnementen op commerciële marketplace-producten beheren met behulp van de volgende methoden:

* [Een abonnement op de commerciële marketplace annuleren](cancel-an-azure-marketplace-subscription.md)
* [Automatisch verlengen in- of uitschakelen voor een abonnement op de commerciële marketplace](update-autorenew-for-an-azure-marketplace-subscription.md)

## <a name="quantity-management"></a>Hoeveelheidsbeheer

De hoeveelheid van een abonnement op de commerciële marketplace moet binnen de limieten liggen die zijn gedefinieerd door de bijbehorende [SKU](product-resources.md#sku) (zie de kenmerken **minimumQuantity** en **maximumQuantity).** Gebruik de volgende methode om de hoeveelheid van een abonnement op de commerciële marketplace bij te werken:

* [De hoeveelheid van een abonnement wijzigen](change-the-quantity-of-a-subscription.md)

## <a name="invoice-and-reconciliation"></a>Factuur en afstemming

U kunt klantfacturen [(inclusief](invoice-resources.md) kosten voor abonnementen op commerciële marketplace-producten) beheren met behulp van de volgende methoden:

* [Gefactureerde verbruiksregelitems voor de commerciële marketplace ontvangen](get-invoice-billed-consumption-lineitems.md)
* [Koppelingen voor factuurramingen ophalen](get-invoice-estimate-links.md)
* [Niet-gefactureerde verbruiksregelitems voor de commerciële marketplace op basis van facturen ontvangen](get-invoice-unbilled-consumption-lineitems.md)
* [Niet-gefactureerde afstemmingsregelitems voor facturen ontvangen](get-invoice-unbilled-recon-lineitems.md)

## <a name="test-using-integration-sandbox-account"></a>Testen met behulp van een sandbox-account voor integratie

Nadat u in productie een abonnement op SaaS-producten op de commerciële marketplace hebt gemaakt, moet u een gepersonaliseerde activeringskoppeling ophalen van Partner Center en naar de site van de uitgever gaan om het installatieproces te voltooien. Abonnementsfacturering begint pas nadat de installatie is voltooid.

In de CSP-sandboxomgeving is er geen integratie met ISV's. Als u een activeringskoppeling probeert op te halen Partner Center, wordt er een dummykoppeling geretourneerd. U kunt deze dummykoppeling niet gebruiken om het installatieproces op de site van de uitgever te voltooien. Als u het sandbox-account voor integratie wilt gebruiken om de facturering voor abonnementen op SaaS-producten op de commerciële marketplace te testen, gebruikt u in plaats daarvan de volgende methode om het abonnement te activeren. Abonnementsfacturering begint na een geslaagde activering:

* [Een sandbox-abonnement activeren voor commerciële marketplace-producten](activate-sandbox-subscription-azure-marketplace-products.md)

