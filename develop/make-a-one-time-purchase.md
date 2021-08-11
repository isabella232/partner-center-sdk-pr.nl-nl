---
title: Een eenmalige aankoop doen
description: Een een time-aankoop doen van software- en reserveringsproducten, zoals softwareabonnementen, permanente software en Azure Reserved Virtual Machine-instanties (VM-instanties), met behulp van de Partner Center-API.
ms.date: 10/09/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: baf0b5d4aaa8957874ab019359aca2662a76194387e0cd06999b0bb329076c80
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994435"
---
# <a name="make-a-one-time-purchase"></a>Een eenmalige aankoop doen

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud for US Government

Een een time-aankoop doen van software- en reserveringsproducten, zoals softwareabonnementen, permanente software en Azure Reserved Virtual Machine-instanties (VM-instanties), met behulp van de Partner Center-API.

> [!NOTE]
> Softwareabonnementen zijn niet beschikbaar in de volgende markten:
>
> | Niet-beschikbare markten            | Niet-beschikbare markten (vervolg...) | Niet-beschikbare markten (vervolg...)      |
> |--------------------------------|-----------------------------------|------------------------------------------|
> | Ålandeilanden                  | Groenland                         | Papoea-Nieuw-Guinea                         |
> | Amerikaans-Samoa                 | Grenada                           | Pitcairneilanden                         |
> | Andorra                        | Guadeloupe                        | Réunion                                  |
> | Anguilla                       | Guam                              | Russische Federatie                       |
> | Antarctica                     | Guernsey                          | Saba                                     |
> | Antigua en Barbuda            | Guinee                            | Saint Barthélemy                         |
> | Aruba                          | Guinee-Bissau                     | Saint Lucia                              |
> | Benin                          | Guyana                            | Saint-Martin                             |
> | Bhutan                         | Haïti                             | Saint-Pierre en Miquelon                |
> | Bonaire                        | Heard- en McDonald-eilanden | Saint Vincent en de Grenadines         |
> | Bouveteiland                  | Isle of Man                       | Samoa                                    |
> | Brazilië                         | Jan Mayen                         | San Marino                               |
> | Brits Territorium in de Indische Oceaan | Jersey                            | Sño Toñ en Prñncipe                    |
> | Britse Maagdeneilanden         | Kiribati                          | Seychellen                               |
> | Burkina Faso                   | Kosovo                            | Sierra Leone                             |
> | Burundi                        | Laos                              | Sint Eustatius                           |
> | Cambodja                       | Lesotho                           | Sint Maarten                             |
> | Centraal-Afrikaanse Republiek       | Liberia                           | Salomonseilanden                          |
> | Tsjaad                           | Madagaskar                        | Somalië                                  |
> | China                          | Malawi                            | Zuid-Georgië en de Zuidelijke Sandwicheilanden |
> | Christmaseiland               | Maldiven                          | Zuid-Soedan                              |
> | Cocoseilanden        | Mali                              | St Helena, Ascension, Tristan da Cunha   |
> | Comoren                        | Marshalleilanden                  | Suriname                                 |
> | Congo                          | Martinique                        | Svalbard                                 |
> | Congo (DRC)                    | Mauritanië                        | Swaziland                                |
> | Cookeilanden                   | Mayotte                           | Timor-Leste                              |
> | Djibouti                       | Micronesia                        | Togo                                     |
> | Dominica                       | Montserrat                        | Tokelau                                  |
> | Equatoriaal-Guinea              | Mozambique                        | Tonga                                    |
> | Eritrea                        | Myanmar                           | Turks- en Caicos-eilanden                 |
> | Falklandeilanden               | Nauru                             | Tuvalu                                   |
> | Frans-Guyana                  | Nieuw-Caledonië                     | Amerikaanse outlyingeilanden                    |
> | Frans-Polynesië               | Niger                             | Vanuatu                                  |
> | Franse Gebieden in de zuidelijke Indische Oceaan    | Niue                              | Vaticaanstad                             |
> | Gabon                          | Norfolk                    | Wallis en Walluna                        |
> | Gambia                         | Noordelijke Marianen          | Jemen                                    |
> | Gibraltar                      | Palau                             | &nbsp;                                   |
>
&nbsp;
> [!NOTE]
> Als u doorlopende software wilt kopen, moet u eerder zijn gekwalificeerd. Neem contact op met de ondersteuning voor meer informatie.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="making-a-one-time-purchase"></a>Een een time-time aankoop doen

Gebruik de volgende stappen om een een time-aankoop te doen:

1. [Inschakelen:](#enablement) (alleen gereserveerde VM-instantie van Azure) Registreer een actief CSP Azure-abonnement om het in te stellen voor het kopen van een reserveringsproduct.

2. [Detectie:](#discovery) zoek en selecteer de producten en SKU's die u wilt kopen en controleer de beschikbaarheid ervan.

3. [Verzending van bestelling:](#order-submission) maak een winkelwagen met de items in uw bestelling en verzend deze.

4. [Ordergegevens op halen:](#get-order-details) bekijk de details van een order, alle orders voor een klant of bekijk orders per type factureringscyclus.

Nadat u een een time-aankoop hebt gedaan, laten de volgende scenario's zien hoe u de levenscyclus van uw producten beheert door informatie over uw rechten op te halen en om saldo-instructies, facturen en factuursommen op te halen.

- [Levenscyclusbeheer](#lifecycle-management)

- [Factuur en afstemming](#invoice-and-reconciliation)

## <a name="enablement"></a>Activering

Zodra u het actieve abonnement hebt geïdentificeerd waar u de gereserveerde VM-instantie voor Azure aan wilt toevoegen, moet u het abonnement registreren zodat het is ingeschakeld. Zie Een abonnement [registreren](subscription-resources.md) als u een bestaande abonnementsresource wilt registreren zodat deze is [ingeschakeld.](register-a-subscription.md)

Nadat u uw abonnement hebt geregistreerd, moet u bevestigen dat het registratieproces is voltooid door de registratiestatus te controleren. Zie Registratiestatus van abonnement krijgen voor [deze stap.](get-subscription-registration-status.md)

## <a name="discovery"></a>Detectie

Zodra het abonnement is ingeschakeld, kunt u producten en SKU's selecteren en de beschikbaarheid ervan controleren met behulp van de Partner Center API-modellen:

- [Product:](product-resources.md#product) een groeperingsconsistente voor opschatbare goederen of services. Een product op zichzelf is geen opschatbaar item.

- [SKU:](product-resources.md#sku) een purchasable Stock Keeping Unit (SKU) onder een product. SKU's vertegenwoordigen de verschillende vormen van het product.

- [Beschikbaarheid:](product-resources.md#availability) een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land, valuta en branchesegment).

Voltooi de volgende stappen voordat u een een time-aankoop gaat doen:

1. Identificeer en haal het product en de SKU op die u wilt kopen. U kunt deze stap doen door eerst de producten en SKU's weer te geven, of als u de ID's van het product en de SKU al kent en deze selecteert.

   - [Een lijst met producten op halen](get-a-list-of-products.md)
   - [Een product op halen met behulp van de product-id](get-a-product-by-id.md)
   - [Een lijst met SKU's voor een product op halen](get-a-list-of-skus-for-a-product.md)
   - [Een SKU krijgen met behulp van de SKU-id](get-a-sku-by-id.md)

2. Controleer de inventaris voor een SKU. Deze stap is alleen nodig voor SKU's die zijn getagd met een **inventoryCheck-vereiste.**

   - [Voorraad controleren](check-inventory.md)

3. Haal de [beschikbaarheid voor](product-resources.md#availability) de [SKU op.](product-resources.md#sku) U hebt de **CatalogItemId van de** beschikbaarheid nodig bij het plaatsen van de order. Gebruik een van de volgende API's om deze waarde op te halen:

   - [Een lijst met beschikbaarheid voor een SKU op halen](get-a-list-of-availabilities-for-a-sku.md)
   - [Een beschikbaarheid krijgen met behulp van de beschikbaarheids-id](get-an-availability-by-id.md)

## <a name="order-submission"></a>Verzending van order

Volg deze stappen om uw bestelling te verzenden:

1. Maak een winkelwagen voor de verzameling catalogusitems die u wilt kopen. Wanneer u een [winkelwagen maakt,](cart-resources.md)worden de winkelwagenregelitems automatisch gegroepeerd op basis van wat samen kan worden gekocht in dezelfde [](cart-resources.md#cartlineitem) [order](order-resources.md).

   - [Een winkelwagen maken](create-a-cart.md)
   - [Een winkelwagen bijwerken](update-a-cart.md)

2. Bekijk de winkelwagen. Als u een winkelwagen bekijkt, wordt er een order [gemaakt.](order-resources.md)

   - [De winkelwagen uitchecken](checkout-a-cart.md)

## <a name="get-order-details"></a>Ordergegevens op halen

Zodra u uw order hebt gemaakt, kunt u de details van een afzonderlijke order ophalen met behulp van de order-id of een lijst met orders voor een klant ophalen. Er is een vertraging van maximaal 15 minuten tussen het moment waarop een order wordt verzonden en wanneer deze wordt weergegeven in een lijst met orders van een klant.

- Om de details van een afzonderlijke order op te halen met behulp van de order-id. Zie Get [an order by ID (Een bestelling op id krijgen).](get-an-order-by-id.md)

- Om een lijst met orders voor een klant op te halen met behulp van de klant-id. Zie [Alle orders van een klant op te halen.](get-all-of-a-customer-s-orders.md)

- Als u een lijst met [](product-resources.md#billingcycletype) orders voor een klant wilt op halen op type factureringscyclus, kunt u afzonderlijke orders (een time-charges) en jaarlijkse of maandelijks gefactureerde orders op een lijst plaatsen. Zie Get [a list of orders by customer and billing cycle type (Een lijst met orders per klant en type factureringscyclus) bekijken.](get-a-list-of-orders-by-customer-and-billing-cycle-type.md)

## <a name="lifecycle-management"></a>Levenscyclusbeheer

Als onderdeel van het beheren van de levenscyclus van uw een time-aankopen in Partner Center, kunt u informatie over uw rechten ophalen en [reserveringsgegevens](entitlement-resources.md)ophalen met behulp van de reserveringsorder-id. Zie Rechten krijgen voor voorbeelden van [hoe u dit doet.](get-a-collection-of-entitlements.md)

## <a name="invoice-and-reconciliation"></a>Factuur en afstemming

In de volgende scenario's ziet u hoe [](invoice-resources.md)u programmatisch de facturen van uw klant kunt weergeven en hoe u de saldo's en samenvattingen van uw account kunt opsommen die een time-kosten bevatten.

### <a name="balance-and-payment"></a>Saldo en betaling

Zie Uw huidige rekeningsaldo opmaken als u het huidige saldo in uw standaardvalutatype wilt [opmaken](get-the-reseller-s-current-account-balance.md) dat een saldo is van zowel terugkerende als eenmalige kosten

### <a name="multi-currency-balance-and-payment"></a>Saldo en betaling met meerdere valuta

Zie [Factuuroverzichten](get-invoice-summaries.md)ophalen voor het saldo van uw huidige account en een verzameling factuuroverzichten met zowel terugkerende als eenmalige kosten voor elk van de valutatypen van uw klant.

### <a name="invoices"></a>Facturen

Zie Een verzameling facturen ophalen voor een verzameling facturen met zowel terugkerende als eenmalige [kosten.](get-a-collection-of-invoices.md)

### <a name="single-invoice"></a>Enkele factuur

Zie Een factuur ophalen op id voor het ophalen van een specifieke factuur met behulp van de [factuur-id.](get-invoice-by-id.md)

### <a name="reconciliation"></a>Verzoening

Zie Factuurregelitems ophalen voor een verzameling factuurregelitems (afstemmingsregelitems) voor een specifieke [factuur-id.](get-invoiceline-items.md)

### <a name="download-an-invoice-as-a-pdf"></a>Een factuur downloaden als PDF

Zie Een factuuroverzicht ophalen als u een factuuroverzicht in PDF-vorm wilt ophalen met behulp [van een factuur-id.](get-invoice-statement.md)
