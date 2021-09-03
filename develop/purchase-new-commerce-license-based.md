---
title: Nieuwe commerce-services op basis van licenties kopen
description: Ontwikkelaars kunnen nieuwe op licenties gebaseerde commerceservices kopen, maken en beheren met behulp van Partner Center API's.
ms.date: 02/24/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: dd3aebdb0a670449d3a39f67fc2ad6c7ef8df8e5
ms.sourcegitcommit: e1db965e8c7b4fe3aaa0ecd6cefea61973ca2232
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/03/2021
ms.locfileid: "123457302"
---
# <a name="purchasing-new-commerce-license-based-services"></a>Nieuwe commerce-services op basis van licenties kopen

**Van toepassing op:**

* Partnercentrum

> [!Note] 
> Nieuwe commercewijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de technical preview van de nieuwe commerce-ervaring M365/D365.

U kunt op licenties gebaseerde nieuwe commerce-ervaringsservices kopen, maken en beheren met behulp van de Partner Center API's. Het proces is vergelijkbaar met zoals Azure-plan en Marketplace-aanbiedingen.

## <a name="prerequisites"></a>Vereisten

* [Partner Center](partner-center-authentication.md) verificatiereferenties. De nieuwe commerce-ervaring ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.
* De klant-id. Als u geen klant-id hebt, volgt u de stappen in [Een lijst met klanten op halen.](get-a-list-of-customers.md) U kunt zich ook aanmelden bij Partner Center, de klant kiezen in de lijst met klanten, **Account** selecteren en vervolgens hun **Microsoft-id opslaan.**
* [Bevestiging van de acceptatie van de Microsoft-klantovereenkomst.](/partner-center/confirm-customer-agreement)

## <a name="get-the-catalog-item-for-new-commerce-license-based-services"></a>Het catalogusitem voor nieuwe op licenties gebaseerde commerceservices downloaden

U moet nieuwe catalogusitems voor commercelicentieservices ophalen. Haal catalogusitems op met de bestaande Partner Center catalogus-API's met de volgende resourcemodellen:

* **[Product:](product-resources.md#product)** een groeperingsconsistente voor opschatbare goederen of services. Een product zelf is geen opschatbaar item.
* **[SKU:](product-resources.md#sku)** een op te halen Stock Keeping Unit (SKU) onder een product. SKU's vertegenwoordigen de verschillende vormen van het product.
* **[Beschikbaarheid:](product-resources.md#availability)** een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land, valuta of branchesegment).

De catalogusitems voor nieuwe aanbiedingen op basis van licentieservices voor commerce verkrijgen:

1. Volg de stappen in [Een lijst met producten voor producten op](get-a-list-of-products.md) halen en geef **targetView** op als **OnlineServices.** (Als u al bekend bent met de product-id voor de aanbieding die u wilt kopen, kunt u in plaats daarvan de stappen in Een product kopen met de [product-id](get-a-product-by-id.md) volgen.)

2. Haal de **SKU op** uit het product voor de aanbieding die u zoekt. Volg de stappen in [Een lijst met SKU's voor een product op halen.](get-a-list-of-skus-for-a-product.md) (Als u al bekend bent met de SKU-id voor de wante aanbieding, kunt u in plaats daarvan de stappen in Een SKU kopen met de [SKU-id](get-a-sku-by-id.md) volgen.)

3. Haal de **beschikbaarheid op** uit de SKU voor de aanbieding. Verschillende aanbiedingen ondersteunen specifieke voorwaarden. Sommige SKU's hebben meer dan één beschikbaarheid. Volg de stappen in [Een lijst met beschikbaarheid voor een SKU op halen.](get-a-list-of-availabilities-for-a-sku.md) (Als u al bekend bent met de id voor de beschikbaarheid die u nodig hebt, kunt u in plaats daarvan de stappen in Een beschikbaarheid krijgen met behulp van de [beschikbaarheids-id](get-an-availability-by-id.md) volgen.) *Noteer de waarde van de eigenschap **CatalogItemId** van de beschikbaarheid voor de aanbieding. U hebt deze waarde nodig om een bestelling te maken.*

## <a name="create-and-submit-an-order"></a>Een order maken en verzenden

Volg deze stappen om uw bestelling voor een Azure-plan (inclusief nieuwe handelsorders) in te dienen:

1. [Maak een winkelwagen](create-a-cart.md) voor de verzameling catalogusitems die u wilt kopen. Wanneer u een [winkelwagen maakt,](cart-resources.md#cart)worden de [regelitems](cart-resources.md#cartlineitem) van de winkelwagen automatisch gegroepeerd op basis van wat samen in dezelfde volgorde kan worden [gekocht.](order-resources.md#order) (U kunt ook [een winkelwagen bijwerken.)](update-a-cart.md)

2. [Bekijk de winkelwagen](checkout-a-cart.md), wat resulteert in het maken van een [order](order-resources.md#order).

## <a name="get-order-details"></a>Orderdetails op halen

U kunt [de details van een afzonderlijke order ophalen met behulp van de order-id](get-an-order-by-id.md). U kunt ook [een lijst met alle orders voor een specifieke klant ophalen.](get-all-of-a-customer-s-orders.md)

>[!NOTE]
>Nadat u een order hebt verzenden, is er een vertraging van maximaal 15 minuten voordat de order wordt weergegeven in de orderlijst van die klant. Momenteel kunnen EU-partners alleen nieuwe commerceaanbiedingen aanschaffen voor: 1. Nieuwe klanten 2. Bestaande klanten die geen al bestaand Azure-abonnement, Marketplace, softwareabonnementen of permanente software hebben in een andere valuta dan de landvaluta van de partner.

## <a name="manage-new-commerce-subscriptions"></a>Nieuwe commerce-abonnementen beheren

Nadat de order is verwerkt, wordt er Partner Center **abonnementsresource** gemaakt voor het Azure-plan. U kunt de volgende methoden gebruiken voor het beheren Partner Center **abonnementsbronnen** om het Azure-plan te beheren:

* [De abonnementen van een klant ophalen](get-all-of-a-customer-s-subscriptions.md)
* [Een lijst met abonnementen op basis van bestelling ophalen](get-a-list-of-subscriptions-by-order.md)

Er zijn verschillen en nieuwe mogelijkheden die specifiek zijn voor nieuwe handel.

## <a name="invoice-and-reconciliation"></a>Factuur en afstemming

U kunt facturen en afstemmingsgegevens beheren met behulp van de volgende methoden:

* [Een verzameling facturen ophalen](get-a-collection-of-invoices.md)
* [Koppelingen voor factuurramingen ophalen](get-invoice-estimate-links.md)
* [Factuur op id ontvangen](get-invoice-by-id.md)
* [Factuur ophalen](get-invoice-statement.md)
* [Factuuroverzichten ophalen](get-invoice-summaries.md)
* [Regelitems gefactureerd verbruik ophalen](get-invoice-billed-consumption-lineitems.md)
* [Regelitems ongefactureerd verbruik ophalen](get-invoice-unbilled-consumption-lineitems.md)
* [Gefactureerde recon line-items voor facturen ontvangen](get-invoiceline-items.md)
* [Regelitems ongefactureerde reconciliatie ophalen](get-invoice-unbilled-recon-lineitems.md)
