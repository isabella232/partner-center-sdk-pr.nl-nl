---
title: Een abonnement voor commerciële Marketplace-producten maken
description: Ontwikkel aars kunnen een abonnement voor commerciële Marketplace-producten maken en beheren met behulp van partner Center-Api's.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: df2a3707e00ba36a11c404b102304c08d105244e
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767198"
---
# <a name="create-a-subscription-for-commercial-marketplace-products"></a>Een abonnement voor commerciële Marketplace-producten maken

**Van toepassing op:**

* Partnercentrum

U kunt een abonnement voor commerciële Marketplace-producten maken met behulp van partner Center-Api's. U moet [een lijst met aanbiedingen voor een markt verkrijgen](#get-a-list-of-offers-for-a-market), een bestelling voor een abonnement op commerciële Marketplace [maken en verzenden en](#create-and-submit-an-order) vervolgens [een activerings koppeling ophalen](#get-activation-link).

U kunt ook [levenscyclus beheer uitvoeren](#lifecycle-management) en [facturen](#invoice-and-reconciliation) voor deze abonnementen beheren.

## <a name="prerequisites"></a>Vereisten

* Verificatie referenties voor het [partner centrum](partner-center-authentication.md) . Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.
* De klant-id. Als u geen klant-id hebt, volgt u de stappen in [een lijst met klanten ophalen](get-a-list-of-customers.md). U kunt zich ook aanmelden bij het partner centrum, de klant kiezen uit de lijst met klanten, **account** selecteren en vervolgens hun **micro soft-id** opslaan.

## <a name="get-a-list-of-offers-for-a-market"></a>Een lijst met aanbiedingen voor een markt ophalen

U kunt de beschik bare aanbiedingen voor een markt controleren met behulp van de volgende partner Center API-modellen:

* **[Product](product-resources.md#product)**: een groeperings constructie voor tevens goederen of-services. Een product zelf is geen tevens-item.
* **[SKU](product-resources.md#sku)**: een SKU (Stock Keeping Unit) onder een product. Deze vertegenwoordigen de verschillende vormen van het product.
* **[Beschik baarheid](product-resources.md#availability)**: een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land-, valuta-of sector segment).

Voordat u een Azure-reserve ring aanschaft, voert u de volgende stappen uit:

1. Identificeer en haal het product en de SKU op die u wilt kopen. Als u de product-ID en SKU-ID al kent, selecteert u deze.

    * [Een lijst met producten ophalen](get-a-list-of-products.md)
    * [Een product ophalen met de product-ID](get-a-product-by-id.md)
    * [Een lijst met Sku's voor een product ophalen](get-a-list-of-skus-for-a-product.md)
    * [Een SKU ophalen met behulp van de SKU-ID](get-a-sku-by-id.md)

    > [!NOTE]
    > U kunt producten voor commerciële Marketplace identificeren met hun **product type** -eigenschap van **Azure** en hun **subtype** -eigenschap van **SaaS**.

2. Als de Sku's zijn gelabeld met een **InventoryCheck** -vereiste, [controleert u de inventaris van een SKU](check-inventory.md).

    > [!NOTE]
    > Op dit moment zijn er geen commerciële Marketplace-producten die inventaris controle ondersteunen of die zijn gelabeld met een **InventoryCheck** -vereiste.

3. De beschik baarheid voor de SKU ophalen. U hebt de **CatalogItemId** van de beschik baarheid nodig bij het plaatsen van de order, die u via de volgende api's kunt ophalen:

    * [Een lijst met Beschik baarheid voor een SKU ophalen](get-a-list-of-availabilities-for-a-sku.md)
    * [Krijg een Beschik baarheid met behulp van de beschikbaarheids-ID](get-an-availability-by-id.md)

## <a name="create-and-submit-an-order"></a>Een order maken en verzenden

Voer de volgende stappen uit om uw Azure-reserverings order in te dienen:

1. [Maak een mandje](create-a-cart.md) om de verzameling catalogus items te bewaren die u wilt kopen. Wanneer u een [winkel wagen](cart-resources.md#cart)maakt, worden de [Winkelwagen regel items](cart-resources.md#cartlineitem) automatisch gegroepeerd op basis van wat er in dezelfde [volg orde](order-resources.md#order)kan worden aangeschaft. (U kunt ook [een winkel wagen bijwerken](update-a-cart.md).)
2. [Bekijk de winkel wagen](checkout-a-cart.md), wat resulteert in het maken van een [order](order-resources.md#order).

### <a name="get-order-details"></a>Bestellingsgegevens ophalen

U kunt [de details van een afzonderlijke order ophalen met behulp van de order-id](get-an-order-by-id.md). U kunt ook [een lijst met alle orders voor een specifieke klant ophalen](get-all-of-a-customer-s-orders.md).

> [!NOTE]
> Nadat een order is verzonden, is er een vertraging van Maxi maal 15 minuten voordat de order wordt weer gegeven in de order lijst van die klant.

## <a name="get-activation-link"></a>Activerings koppeling ophalen

De partner of klant moet abonnementen activeren voor Azure Marketplace-producten. U kunt [een activerings koppeling verkrijgen per order regel item](get-activation-link-by-order-line-item.md). U kunt ook [een abonnement op id ophalen](get-a-subscription-by-id.md)en vervolgens de eigenschap **links** ervan opsommen om een activerings koppeling te maken.

## <a name="lifecycle-management"></a>Levenscyclus beheer

U kunt de levens cyclus van uw abonnementen op commerciële Marketplace-Producten beheren met de volgende methoden:

* [Een abonnement op de commerciële marketplace annuleren](cancel-an-azure-marketplace-subscription.md)
* [Autoverlengen voor een abonnement op commerciële Marketplace in-of uitschakelen](update-autorenew-for-an-azure-marketplace-subscription.md)

## <a name="quantity-management"></a>Hoeveelheids beheer

De hoeveelheid van een abonnement op commerciële Marketplace moet binnen de grenzen vallen die door de bijbehorende [SKU](product-resources.md#sku) zijn gedefinieerd (Zie de kenmerken **minimumQuantity** en **maximumQuantity** ). Als u de hoeveelheid van een abonnement op commerciële Marketplace wilt bijwerken, gebruikt u de volgende methode:

* [De hoeveelheid van een abonnement wijzigen](change-the-quantity-of-a-subscription.md)

## <a name="invoice-and-reconciliation"></a>Factuur en reconciliatie

U kunt de volgende methoden gebruiken om klant [facturen](invoice-resources.md) (inclusief kosten voor abonnementen op commerciële Marketplace-Producten) te beheren:

* [Gefactureerde commerciële Marketplace voor factuur gebruik ophalen regel items](get-invoice-billed-consumption-lineitems.md)
* [Koppelingen voor factuurramingen ophalen](get-invoice-estimate-links.md)
* [Factuur niet-gefactureerde commerciële Marketplace verbruik regel items ophalen](get-invoice-unbilled-consumption-lineitems.md)
* [Regel items voor niet-gefactureerde reconciliatie van factuur ophalen](get-invoice-unbilled-recon-lineitems.md)

## <a name="test-using-integration-sandbox-account"></a>Testen met behulp van een sandbox-account voor integratie

Nadat u in productie een abonnement hebt gemaakt op een commerciële Marketplace SaaS-producten, moet u een persoonlijke activerings koppeling ophalen van het partner centrum en de site van de uitgever bezoeken om het installatie proces te volt ooien. De facturering van het abonnement wordt pas gestart nadat de installatie is voltooid.

In de CSP-sandbox-omgeving is er geen integratie met Isv's. Als u probeert een activerings koppeling op te halen van het partner centrum, wordt een dummy-koppeling geretourneerd. U kunt deze dummy koppeling niet gebruiken om het installatie proces te volt ooien op de site van de uitgever. Gebruik de volgende methode om het abonnement te activeren als u het sandbox-account voor integratie wilt gebruiken om de facturering te testen voor abonnementen op de SaaS-producten van de commerciële markt plaats. De facturering van het abonnement wordt gestart nadat de activering is voltooid:

* [Een sandbox-abonnement voor commerciële Marketplace-producten activeren](activate-sandbox-subscription-azure-marketplace-products.md)

