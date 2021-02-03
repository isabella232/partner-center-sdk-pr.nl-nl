---
title: Catalogusitems kopen
description: Catalogus items aanschaffen met de API van partner Center.
ms.date: 07/12/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f2b3a34cdb6b29cb7eaaf5d977e4588f538fff09
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767222"
---
# <a name="purchase-catalog-items"></a>Catalogusitems kopen

**Van toepassing op**

- Partnercentrum

In het volgende scenario wordt het algemene proces voor het kopen van items uit de catalogus gedemonstreerd met behulp van de Partner Center-API.

## <a name="discovery"></a>Detectie

Selecteer producten en Sku's en controleer hun Beschik baarheid met behulp van de volgende partner Center API-modellen:

- [Product](product-resources.md#product) : een groeperings constructie voor tevens-goederen of-services. Een product zelf is geen tevens-item.
- [SKU](product-resources.md#sku) : een SKU (tevens Stock Keeping Unit) onder een product. Deze vertegenwoordigen de verschillende vormen van het product.
- [Beschik baarheid](product-resources.md#availability) : een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land-, valuta-en sector segment).

Voer de volgende stappen uit om een item te kopen vanuit de catalogus:

1. Identificeer en haal het product en de SKU op die u wilt kopen.

   - [Een lijst met producten ophalen](get-a-list-of-products.md)
   - [Een product ophalen met de product-ID](get-a-product-by-id.md)
   - [Een lijst met Sku's voor een product ophalen](get-a-list-of-skus-for-a-product.md)
   - [Een SKU ophalen met behulp van de SKU-ID](get-a-sku-by-id.md)

2. Controleer de inventarisatie van een SKU. Deze stap is alleen nodig voor Sku's die zijn gelabeld met een **InventoryCheck** -waarde in de eigenschap [purchasePrerequisites](product-resources.md#sku) .

   - [Voorraad controleren](check-inventory.md)

3. De [Beschik baarheid](product-resources.md#availability) voor de [SKU](product-resources.md#sku)ophalen. U hebt de **CatalogItemId** van de beschik baarheid nodig wanneer u de order plaatst. Gebruik een van de volgende Api's om deze waarde op te halen:

   - [Een lijst met Beschik baarheid voor een SKU ophalen](get-a-list-of-availabilities-for-a-sku.md)
   - [Krijg een Beschik baarheid met behulp van de beschikbaarheids-ID](get-an-availability-by-id.md)

## <a name="order-submission"></a>Verzen ding best Ellen

Ga als volgt te werk om de volg orde van uw catalogus items te verzenden:

1. Maak een [mandje](cart-resources.md) om de verzameling catalogus items te bewaren die u wilt kopen. Wanneer u een winkel wagen maakt, worden de [Winkelwagen regel items](cart-resources.md#cartlineitem) automatisch gegroepeerd op basis van wat er in dezelfde [volg orde](order-resources.md)kan worden aangeschaft.

   - [Een winkel wagen maken](create-a-cart.md)
   - [Een winkel wagen bijwerken](update-a-cart.md)

2. Bekijk de winkel wagen. Het uitchecken van een winkel wagen resulteert in het maken van een [order](order-resources.md).

   - [De winkel wagen afhandelen](checkout-a-cart.md)

## <a name="get-order-details"></a>Bestellingsgegevens ophalen

U kunt de details van een afzonderlijke order ophalen met behulp van de order-ID of een lijst met orders voor een klant ophalen. Er is een vertraging van Maxi maal 15 minuten tussen de tijd dat een bestelling wordt verzonden en wanneer deze wordt weer gegeven in een lijst met de orders van een klant.

- Zie [een order op basis van id ophalen](get-an-order-by-id.md) om de details van een afzonderlijke order op te halen met behulp van de order-id's.

- Zie [alle orders van een klant ophalen](get-all-of-a-customer-s-orders.md) voor een lijst met orders voor een klant met behulp van de klant-id.

- Zie [een lijst met orders ophalen per klant en facturerings cyclus type](get-a-list-of-orders-by-customer-and-billing-cycle-type.md) voor een lijst met orders voor een klant per [facturerings cyclus type](product-resources.md#billingcycletype) , zodat u orders voor catalogus items (eenmalige kosten) en jaarlijks of maandelijks gefactureerde orders afzonderlijk kunt weer geven.

## <a name="lifecycle-management"></a>Levenscyclus beheer

Als onderdeel van het beheer van de levens cyclus van uw catalogus items in het partner centrum, kunt u informatie ophalen over de [rechten](entitlement-resources.md)van uw catalogus item en reserverings Details ophalen met behulp van de reserverings order-id. Zie [rechten ophalen](get-a-collection-of-entitlements.md)voor voor beelden van hoe u dit doet.   

## <a name="invoice-and-reconciliation"></a>Factuur en reconciliatie

In de volgende scenario's ziet u hoe u de [facturen](invoice-resources.md)van uw klant programmatisch kunt bekijken en hoe u uw account saldi en samen vattingen kunt ophalen die eenmalige kosten voor catalogus items bevatten.

### <a name="balance-and-payment"></a>Saldo en betaling

Als u het huidige account saldo wilt ophalen in het standaard valuta type dat een saldo van de kosten voor terugkerend en eenmalig (catalogus item) is, raadpleegt u [uw huidige account saldo ophalen](get-the-reseller-s-current-account-balance.md).

### <a name="multi-currency-balance-and-payment"></a>Saldo en betaling in meerdere valuta

Zie [factuur overzichten ophalen](get-invoice-summaries.md)voor een overzicht van uw huidige account saldo en een verzameling van factuur overzichten met een factuur samenvatting met zowel periodieke als eenmalige kosten voor elk van de valuta typen van uw klant.

### <a name="invoices"></a>Facturen

Zie [een verzameling facturen ophalen](get-a-collection-of-invoices.md)voor een verzameling facturen waarin zowel terugkerende als eenmalige kosten worden weer gegeven. 

### <a name="single-invoice"></a>Eén factuur

Als u een specifieke factuur wilt ophalen met behulp van de factuur-ID, raadpleegt u [een factuur op id ophalen](get-invoice-by-id.md).  

### <a name="reconciliation"></a>Afstemming

Zie [factuur regel items ophalen](get-invoiceline-items.md)voor een verzameling van gegevens over het factuur regel item (reconciliatie regel items) voor een specifieke factuur-ID.  

### <a name="download-an-invoice-as-a-pdf"></a>Een factuur als PDF-bestand downloaden

Zie [een factuur overzicht ophalen](get-invoice-statement.md)als u een factuur overzicht wilt ophalen in een PDF-formulier met een factuur-ID.
