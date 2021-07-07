---
title: Catalogusitems kopen
description: Catalogusitems kopen met behulp van Partner Center API.
ms.date: 07/12/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d3e0deedff194b1c836d9266c2201a2b3a52cc1b
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445354"
---
# <a name="purchase-catalog-items"></a>Catalogusitems kopen

In het volgende scenario wordt het algemene proces gedemonstreerd voor het kopen van items uit de catalogus met behulp van Partner Center API.

## <a name="discovery"></a>Detectie

Selecteer producten en SKU's (Stock Keeping Units) en controleer de beschikbaarheid ervan met behulp van de Partner Center API-modellen:

- [Product:](product-resources.md#product) een groeperingsconsistente voor opschatbare goederen of services. Een product op zichzelf is geen opschatbaar item.
- [SKU:](product-resources.md#sku) een opschatbare SKU onder een product. Deze vertegenwoordigen de verschillende vormen van het product.
- [Beschikbaarheid:](product-resources.md#availability) een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land, valuta en branchesegment).

Als u een item uit de catalogus wilt kopen, moet u de volgende stappen voltooien:

1. Identificeer en haal het product en de SKU op die u wilt kopen.

   - [Een lijst met producten op halen](get-a-list-of-products.md)
   - [Een product op halen met behulp van de product-id](get-a-product-by-id.md)
   - [Een lijst met SKU's voor een product op halen](get-a-list-of-skus-for-a-product.md)
   - [Een SKU op halen met behulp van de SKU-id](get-a-sku-by-id.md)

2. Controleer de inventaris voor een SKU. Deze stap is alleen nodig voor SKU's die zijn gelabeld met de waarde **InventoryCheck** in de eigenschap [purchasePrerequisites.](product-resources.md#sku)

   - [Voorraad controleren](check-inventory.md)

3. Haal de [beschikbaarheid voor](product-resources.md#availability) de [SKU op.](product-resources.md#sku) U hebt de **CatalogItemId van de** beschikbaarheid nodig bij het plaatsen van de order. Gebruik een van de volgende API's om deze waarde op te halen:

   - [Een lijst met beschikbaarheid voor een SKU op halen](get-a-list-of-availabilities-for-a-sku.md)
   - [Een beschikbaarheid krijgen met behulp van de beschikbaarheids-id](get-an-availability-by-id.md)

## <a name="order-submission"></a>Verzending van order

Ga als volgt te werk om uw catalogusitemvolgorde in te dienen:

1. Maak een [winkelwagen](cart-resources.md) voor de verzameling catalogusitems die u wilt kopen. Wanneer u een winkelwagen maakt, worden de [regelitems](cart-resources.md#cartlineitem) van de winkelwagen automatisch gegroepeerd op basis van wat samen in dezelfde order kan worden [gekocht.](order-resources.md)

   - [Een winkelwagen maken](create-a-cart.md)
   - [Een winkelwagen bijwerken](update-a-cart.md)

2. Bekijk de winkelwagen. Als u een winkelwagen bekijkt, wordt er een order [gemaakt.](order-resources.md)

   - [De winkelwagen uitchecken](checkout-a-cart.md)

## <a name="get-order-details"></a>Orderdetails op halen

U kunt de details van een afzonderlijke order ophalen met behulp van de order-id of een lijst met orders voor een klant ophalen. Er is een vertraging van maximaal 15 minuten tussen het moment waarop een order wordt verzonden en wanneer deze wordt weergegeven in een lijst met orders van een klant.

- Zie [Een order op id krijgen](get-an-order-by-id.md) om de details van een afzonderlijke order op te halen met behulp van de order-id's.

- Zie [Get all of a customer's orders (Alle orders van een klant op halen)](get-all-of-a-customer-s-orders.md) voor een lijst met orders voor een klant met behulp van de klant-id.

- Zie Get [a list of orders by customer](get-a-list-of-orders-by-customer-and-billing-cycle-type.md) and billing cycle [](product-resources.md#billingcycletype) type (Een lijst met orders per klant en type factureringscyclus) voor een lijst met orders voor een klant per type factureringscyclus, zodat u catalogusitemorders (een keer kosten) en jaarlijkse of maandelijks gefactureerde orders afzonderlijk kunt bekijken.

## <a name="lifecycle-management"></a>Levenscyclusbeheer

Als onderdeel van het beheren van de levenscyclus van uw catalogusitems in Partner Center, kunt u informatie ophalen over uw catalogusitem Rechten en [reserveringsgegevens](entitlement-resources.md)ophalen met behulp van de reserveringsorder-id. Zie Rechten krijgen voor voorbeelden van [hoe u dit doet.](get-a-collection-of-entitlements.md)   

## <a name="invoice-and-reconciliation"></a>Factuur en afstemming

In de volgende scenario's ziet u hoe [](invoice-resources.md)u de facturen van uw klant programmatisch kunt weergeven en de saldo's en samenvattingen van uw account kunt opmaken die een een time-kosten voor catalogusitems bevatten.

### <a name="balance-and-payment"></a>Saldo en betaling

Zie Uw huidige rekeningsaldo opmaken om het huidige rekeningsaldo op te halen in uw standaardvalutatype dat een saldo is van zowel terugkerende als eenmalige kosten [(catalogusitem).](get-the-reseller-s-current-account-balance.md)

### <a name="multi-currency-balance-and-payment"></a>Saldo en betaling met meerdere valuta

Zie [Factuuroverzichten](get-invoice-summaries.md)ophalen voor het saldo van uw huidige rekening en een verzameling factuuroverzichten met zowel terugkerende als eenmalige kosten voor elk van de valutatypen van uw klant.

### <a name="invoices"></a>Facturen

Zie Een verzameling facturen ophalen voor een verzameling facturen met zowel terugkerende als eenmalige [kosten.](get-a-collection-of-invoices.md) 

### <a name="single-invoice"></a>Eén factuur

Zie Een factuur ophalen op id als u een specifieke factuur wilt ophalen met behulp van de [factuur-id.](get-invoice-by-id.md)  

### <a name="reconciliation"></a>Verzoening

Zie Factuurregelitems ophalen voor een verzameling factuurregelitems (afstemmingsregelitems) voor een specifieke [factuur-id.](get-invoiceline-items.md)  

### <a name="download-an-invoice-as-a-pdf"></a>Een factuur downloaden als PDF

Zie Een factuuroverzicht ophalen als u een factuuroverzicht in PDF-vorm wilt ophalen met behulp van een [factuur-id.](get-invoice-statement.md)
