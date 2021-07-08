---
title: Azure-reserveringen kopen
description: U kunt Azure-reserveringen voor een klant kopen met behulp van de Partner Center-API via uw bestaande Microsoft Azure-abonnement (MS-AZR-0145P) of uw Azure-abonnement.
ms.date: 11/01/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0b9ce4a808ac12c32bd67888fc92808baeb0e575
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547764"
---
# <a name="purchase-azure-reservations"></a>Azure-reserveringen kopen

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud for US Government

Als u een Azure-reservering voor een klant wilt kopen met behulp van de Partner Center-API, moet u een bestaand abonnement op Microsoft Azure **(MS-AZR-0145P)** of een Azure-abonnement voor deze klant hebben.

> [!NOTE]
> Azure-reserveringen zijn niet beschikbaar in de volgende markten:
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

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een abonnements-id voor een actief CSP Azure-abonnement of een Azure-abonnement.

## <a name="how-to-purchase-microsoft-azure-reservations"></a>Reserveringen voor Microsoft Azure aanschaffen

Nadat u het actieve CSP Azure-abonnement hebt geïdentificeerd aan wie u een Azure-reservering wilt toevoegen, gebruikt u de volgende stappen om het aan te schaffen:

1. [Inschakelen:](#enablement) registreer een actief CSP Azure-abonnement om dit in te stellen voor het kopen van Azure-reserveringen.

2. [Detectie:](#discovery) zoek en selecteer de Azure-reserveringsproducten en Stock Keeping Units (SKU's) die u wilt kopen en controleer de beschikbaarheid ervan.

3. [Verzending van bestelling:](#order-submission) maak een winkelwagen met de items in uw bestelling en verzend deze.

4. [Ordergegevens op halen:](#get-order-details) bekijk de details van een order, alle orders voor een klant of bekijk orders per type factureringscyclus.

Nadat u Azure-reserveringen hebt aangeschaft, laten de volgende scenario's zien hoe u hun levenscyclus kunt beheren door informatie op te halen over uw Azure-reserveringsrechten en hoe u saldo-instructies, facturen en factuursommen kunt ophalen.

- [Levenscyclusbeheer](#lifecycle-management)
- [Factuur en afstemming](#invoice-and-reconciliation)

## <a name="enablement"></a>Activering

Inschakelen betekent dat u een bestaand Microsoft Azure **(MS-AZR-0145P)** abonnement aan een gereserveerde VM-instantie van Azure moet koppelen door het abonnement te registreren zodat het wordt ingeschakeld voor Azure-reserveringen. Registratie is een vereiste om een Azure Reserved VM Instances.

Een abonnement is vereist voor de ondersteuning van de volgende taken:

1. Om te controleren of de klant in aanmerking komt voor het implementeren van resources en Azure Reserved VM Instances kopen in een regio of niet.

2. Om capaciteitsprioriteit te bieden voor implementaties in een abonnement. Dit is alleen van toepassing op één bereik Azure Reserved VM Instances de optie **capaciteitsprioriteit** is geselecteerd.

Nadat u het actieve abonnement hebt geïdentificeerd waar u de Azure-reservering aan wilt toevoegen, moet u het abonnement registreren zodat het is ingeschakeld voor Azure-reserveringen. Zie Een abonnement [registreren](subscription-resources.md) als u een bestaande abonnementsresource wilt registreren zodat deze is ingeschakeld voor het bestellen van Azure-reserveringen. [](register-a-subscription.md)

Nadat u uw abonnement hebt geregistreerd, moet u bevestigen dat het registratieproces is voltooid door de registratiestatus te controleren. Zie Registratiestatus van abonnement [krijgen om dit te doen.](get-subscription-registration-status.md)

> [!NOTE]
> Wanneer u Microsoft Azure reservering voor een klant met een Azure-abonnement aanschaft, moet u het Azure-plan eerst registreren. Net als bij een Microsoft Azure (**MS-AZR-0145P)** wordt een Azure-plan vertegenwoordigd door een resource Partner Center [Subscription.](subscription-resources.md) Daarom kunt u dezelfde methode Een abonnement registreren [gebruiken](register-a-subscription.md) om een Azure-plan te registreren.

## <a name="discovery"></a>Detectie

Zodra het abonnement is ingeschakeld voor het kopen van Azure-reserveringen, kunt u producten en SKU's selecteren en de beschikbaarheid ervan controleren met behulp van de volgende API Partner Center-modellen:

- [Product:](product-resources.md#product) een groeperingsconsistente voor opschatbare goederen of services. Een product op zichzelf is geen opschatbaar item.

- [SKU:](product-resources.md#sku) een opschatbare SKU onder een product. Deze vertegenwoordigen de verschillende vormen van het product.

- [Beschikbaarheid:](product-resources.md#availability) een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land, valuta en branchesegment).

Voltooi de volgende stappen voordat u een Azure-reservering aanschaft:

1. Identificeer en haal het product en de SKU op die u wilt kopen. U kunt dit doen door eerst de producten en SKU's weer te geven, of Als u de ID's van het product en de SKU al kent, selecteert u deze.

   - [Een lijst met producten ophalen (per land)](get-a-list-of-products.md)
   - [Een product op halen met behulp van de product-id](get-a-product-by-id.md)
   - [Een lijst met SKU’s voor een product ophalen (per land/regio)](get-a-list-of-skus-for-a-product.md)
   - [Een SKU krijgen met behulp van de SKU-id](get-a-sku-by-id.md)

2. Controleer de inventaris voor een SKU. Deze stap is alleen nodig voor SKU's die zijn getagd met een **inventoryCheck-vereiste.**

   - [Voorraad controleren](check-inventory.md)

3. Haal de [beschikbaarheid voor](product-resources.md#availability) de [SKU op.](product-resources.md#sku) U hebt de **CatalogItemId van de** beschikbaarheid nodig bij het plaatsen van de order. Gebruik een van de volgende API's om deze waarde op te halen:

   - [Een lijst met beschikbaarheid voor een SKU ophalen (per land)](get-a-list-of-availabilities-for-a-sku.md)
   - [Een beschikbaarheid krijgen met behulp van de beschikbaarheids-id](get-an-availability-by-id.md)

> [!IMPORTANT]
> Elk Microsoft Azure reserveringsproduct heeft verschillende beschikbaarheid voor Microsoft Azure abonnement **(MS-AZR-0145P)** en een Azure-abonnement. Geef de parameter reservationScope=AzurePlan op om een lijst met producten (per [land)](get-a-list-of-products.md)of Een lijst met SKU's voor een [product (per land)](get-a-list-of-skus-for-a-product.md)op te halen of Een lijst met beschikbaarheid voor een [SKU (per land)](get-a-list-of-availabilities-for-a-sku.md) op te halen die alleen van toepassing zijn op het Azure-abonnement.

## <a name="order-submission"></a>Verzending van order

Ga als volgt te werk om uw Azure-reserveringsorder te verzenden:

1. Maak een winkelwagen voor de verzameling catalogusitems die u wilt kopen. Wanneer u een [winkelwagen maakt,](cart-resources.md)worden de winkelwagenregelitems automatisch gegroepeerd op basis van wat samen kan worden gekocht in dezelfde [](cart-resources.md#cartlineitem) [order](order-resources.md).

   - [Een winkelwagen maken](create-a-cart.md)
   - [Een winkelwagen bijwerken](update-a-cart.md)

2. Bekijk de winkelwagen. Als u een winkelwagen bekijkt, wordt er een order [gemaakt.](order-resources.md)

   - [De winkelwagen uitchecken](checkout-a-cart.md)

## <a name="get-order-details"></a>Ordergegevens op halen

Nadat u uw Azure-reserveringsorder hebt gemaakt, kunt u de details van een afzonderlijke order ophalen met behulp van de order-id of een lijst met orders voor een klant ophalen. Er is een vertraging van maximaal 15 minuten tussen het moment waarop een order wordt verzonden en wanneer deze wordt weergegeven in een lijst met orders van een klant.

- Om de details van een afzonderlijke order op te halen met behulp van de order-id. Zie [Get an order by ID (Een bestelling op id krijgen).](get-an-order-by-id.md)

- Een lijst met orders voor een klant op te halen met behulp van de klant-id. Zie [Alle orders van een klant op te halen.](get-all-of-a-customer-s-orders.md)

- Als u een lijst met [](product-resources.md#billingcycletype) orders voor een klant wilt op halen op type factureringscyclus, kunt u afzonderlijke Azure-reserveringsorders (een time-charges) en jaarlijkse of maandelijkse gefactureerde orders opneren. Zie Get [a list of orders by customer and billing cycle type (Een lijst met orders per klant en type factureringscyclus) bekijken.](get-a-list-of-orders-by-customer-and-billing-cycle-type.md)

## <a name="lifecycle-management"></a>Levenscyclusbeheer

Als onderdeel van het beheren van de levenscyclus van uw Azure-reserveringen in Partner Center, kunt u informatie over uw Azure-reserveringsrechten ophalen en [reserveringsgegevens](entitlement-resources.md)ophalen met behulp van de reserveringsorder-id. Zie Rechten krijgen voor voorbeelden van [hoe u dit doet.](get-a-collection-of-entitlements.md)   

## <a name="invoice-and-reconciliation"></a>Factuur en afstemming

In de volgende scenario's ziet u hoe [](invoice-resources.md)u programmatisch de facturen van uw klant kunt weergeven en de saldo's en samenvattingen van uw account kunt opsommen die een time-kosten voor Azure-reserveringen bevatten.

### <a name="balance-and-payment"></a>Saldo en betaling

Zie Uw huidige rekeningsaldo opmaken als u het huidige rekeningsaldo wilt opmaken in uw standaardvalutatype dat een saldo is van zowel terugkerende als eenmalige kosten [(Azure-reservering)](get-the-reseller-s-current-account-balance.md)

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
