---
title: Een eenmalige aankoop doen
description: Een eenmalige aankoop van software-en reserverings producten, zoals software-abonnementen, permanente software en Azure reserved virtual machine-exemplaren (VM), met behulp van de Partner Center-API.
ms.date: 10/09/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 17a5f5c1e845ba36a94d7ce909df30e0146ba448
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767228"
---
# <a name="make-a-one-time-purchase"></a>Een eenmalige aankoop doen

**Van toepassing op**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud for US Government

Een eenmalige aankoop van software-en reserverings producten, zoals software-abonnementen, permanente software en Azure reserved virtual machine-exemplaren (VM), met behulp van de Partner Center-API.

> [!NOTE]
> Software-abonnementen zijn niet beschikbaar op de volgende markten:
>
> | Niet-beschik bare markten            | Niet-beschik bare markten (voortgezet...) | Niet-beschik bare markten (voortgezet...)      |
> |--------------------------------|-----------------------------------|------------------------------------------|
> | Åland-eilanden                  | Groenland                         | Papoea-Nieuw-Guinea                         |
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
> | Brits Territorium in de Indische Oceaan | Jersey                            | Sao Tomé en principe                    |
> | Britse Maagdeneilanden         | Kiribati                          | Seychellen                               |
> | Burkina Faso                   | Kosovo                            | Sierra Leone                             |
> | Burundi                        | Laos                              | Sint Eustatius                           |
> | Cambodja                       | Lesotho                           | Sint Maarten                             |
> | Centraal-Afrikaanse Republiek       | Liberia                           | Salomonseilanden                          |
> | Tsjaad                           | Madagaskar                        | Somalië                                  |
> | China                          | Malawi                            | Zuid-Georgië en de Zuidelijke Sandwicheilanden |
> | Christmaseiland               | Maldiven                          | Zuid-Soedan                              |
> | Cocoseilanden        | Mali                              | Sint-Helena, Ascension en Tristan da Cunha   |
> | Comoren                        | Marshalleilanden                  | Suriname                                 |
> | Congo                          | Martinique                        | Svalbard                                 |
> | Congo (DRC)                    | Mauritanië                        | Swaziland                                |
> | Cookeilanden                   | Mayotte                           | Timor-Leste                              |
> | Djibouti                       | Micronesia                        | Togo                                     |
> | Dominica                       | Montserrat                        | Tokelau                                  |
> | Equatoriaal-Guinea              | Mozambique                        | Tonga                                    |
> | Eritrea                        | Myanmar                           | Turks- en Caicos-eilanden                 |
> | Falklandeilanden               | Nauru                             | Tuvalu                                   |
> | Frans-Guyana                  | Nieuw-Caledonië                     | Amerikaanse ondergeschikte afgelegen eilanden                    |
> | Frans-Polynesië               | Niger                             | Vanuatu                                  |
> | Franse Gebieden in de zuidelijke Indische Oceaan    | Niue                              | Vaticaanstad                             |
> | Gabon                          | Norfolk                    | Wallis en Futuna                        |
> | Gambia                         | Noordelijke Marianen          | Jemen                                    |
> | Gibraltar                      | Palau                             | &nbsp;                                   |
>
&nbsp;
> [!NOTE]
> Als u permanente software wilt kopen, moet u al eerder gekwalificeerd zijn. Neem contact op met de ondersteuning voor meer informatie.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="making-a-one-time-purchase"></a>Een eenmalige aankoop doen

Als u een eenmalige aankoop wilt uitvoeren, voert u de volgende stappen uit:

1. [Activering](#enablement) : (alleen voor Azure gereserveerde VM-instantie) Registreer een actief CSP Azure-abonnement om het in te scha kelen voor het aanschaffen van een reserverings product.

2. [Detectie](#discovery) : Zoek en selecteer de producten en sku's die u wilt kopen en controleer de beschik baarheid.

3. [Order inzending](#order-submission) : Maak een winkel wagen met de items in uw bestelling en verzend deze.

4. Bestellingsgegevens [ophalen](#get-order-details) : Bekijk de details van een order, alle orders voor een klant of geef orders per facturerings cyclus type weer.

Nadat u uw eenmalige aankoop hebt gedaan, kunt u in de volgende scenario's zien hoe u de levens cyclus van uw producten beheert door informatie over uw rechten op te halen en saldo overzichten, facturen en factuur overzichten te verkrijgen.

- [Levenscyclus beheer](#lifecycle-management)

- [Factuur en reconciliatie](#invoice-and-reconciliation)

## <a name="enablement"></a>Activering

Zodra u het actieve abonnement dat u wilt toevoegen aan de Azure gereserveerde VM-instantie hebt geïdentificeerd, moet u het abonnement registreren zodat het is ingeschakeld. Als u een bestaande [abonnements](subscription-resources.md) resource wilt registreren om deze in te scha kelen, raadpleegt u [een abonnement registreren](register-a-subscription.md).

Nadat u uw abonnement hebt geregistreerd, moet u controleren of het registratie proces is voltooid door de registratie status te controleren. Zie de registratie status van het [abonnement ophalen](get-subscription-registration-status.md)voor het uitvoeren van deze stap.

## <a name="discovery"></a>Detectie

Zodra het abonnement is ingeschakeld, kunt u producten en Sku's selecteren en de beschik baarheid controleren met behulp van de volgende partner Center API-modellen:

- [Product](product-resources.md#product) : een groeperings constructie voor tevens-goederen of-services. Een product zelf is geen tevens-item.

- [SKU](product-resources.md#sku) : een SKU (tevens Stock Keeping Unit) onder een product. Sku's vertegenwoordigen de verschillende vormen van het product.

- [Beschik baarheid](product-resources.md#availability) : een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land-, valuta-en sector segment).

Voer de volgende stappen uit voordat u een eenmalige aankoop doet:

1. Identificeer en haal het product en de SKU op die u wilt kopen. U kunt deze stap uitvoeren door eerst de producten en Sku's te vermelden of als u de Id's van het product en de SKU al kent, selecteert u deze.

   - [Een lijst met producten ophalen](get-a-list-of-products.md)
   - [Een product ophalen met de product-ID](get-a-product-by-id.md)
   - [Een lijst met Sku's voor een product ophalen](get-a-list-of-skus-for-a-product.md)
   - [Een SKU ophalen met behulp van de SKU-ID](get-a-sku-by-id.md)

2. Controleer de inventarisatie van een SKU. Deze stap is alleen nodig voor Sku's die zijn gelabeld met een **InventoryCheck** -vereiste.

   - [Voorraad controleren](check-inventory.md)

3. De [Beschik baarheid](product-resources.md#availability) voor de [SKU](product-resources.md#sku)ophalen. U hebt de **CatalogItemId** van de beschik baarheid nodig wanneer u de order plaatst. Gebruik een van de volgende Api's om deze waarde op te halen:

   - [Een lijst met Beschik baarheid voor een SKU ophalen](get-a-list-of-availabilities-for-a-sku.md)
   - [Krijg een Beschik baarheid met behulp van de beschikbaarheids-ID](get-an-availability-by-id.md)

## <a name="order-submission"></a>Verzen ding best Ellen

Voer de volgende stappen uit om uw bestelling te verzenden:

1. Maak een mandje om de verzameling catalogus items te bewaren die u wilt kopen. Wanneer u een [winkel wagen](cart-resources.md)maakt, worden de [Winkelwagen regel items](cart-resources.md#cartlineitem) automatisch gegroepeerd op basis van wat er in dezelfde [volg orde](order-resources.md)kan worden aangeschaft.

   - [Een winkel wagen maken](create-a-cart.md)
   - [Een winkel wagen bijwerken](update-a-cart.md)

2. Bekijk de winkel wagen. Het uitchecken van een winkel wagen resulteert in het maken van een [order](order-resources.md).

   - [De winkel wagen afhandelen](checkout-a-cart.md)

## <a name="get-order-details"></a>Bestellingsgegevens ophalen

Wanneer u uw bestelling hebt gemaakt, kunt u de details van een afzonderlijke order ophalen met de order-ID of een lijst met orders voor een klant ophalen. Er is een vertraging van Maxi maal 15 minuten tussen de tijd dat een bestelling wordt verzonden en wanneer deze wordt weer gegeven in een lijst met de orders van een klant.

- Om de details van een afzonderlijke order op te halen met behulp van de order-ID. Zie [een order op basis van id ophalen](get-an-order-by-id.md).

- Een lijst met orders voor een klant ophalen met behulp van de klant-ID. Zie [alle bestellingen van een klant ophalen](get-all-of-a-customer-s-orders.md).

- Als u een lijst met orders voor een klant per [facturerings cyclus type](product-resources.md#billingcycletype) wilt ophalen, kunt u orders (eenmalige kosten) en jaarlijks of maandelijks gefactureerde orders afzonderlijk weer geven. Zie [een lijst met orders ophalen op basis van het type van de klant en de facturerings cyclus](get-a-list-of-orders-by-customer-and-billing-cycle-type.md).

## <a name="lifecycle-management"></a>Levenscyclus beheer

Als onderdeel van het beheer van de levens cyclus van uw eenmalige aankopen in het partner centrum, kunt u informatie over uw [rechten](entitlement-resources.md)ophalen en reserverings Details ophalen met behulp van de reserverings order-id. Zie [rechten ophalen](get-a-collection-of-entitlements.md)voor voor beelden van hoe u dit doet.

## <a name="invoice-and-reconciliation"></a>Factuur en reconciliatie

In de volgende scenario's ziet u hoe u de [facturen](invoice-resources.md)van uw klant programmatisch kunt bekijken en hoe u uw account saldi en samen vattingen kunt ophalen die eenmalige kosten bevatten.

### <a name="balance-and-payment"></a>Saldo en betaling

Als u het huidige account saldo wilt ophalen in uw standaard valuta type dat een saldo van zowel terugkerende als eenmalige kosten is, raadpleegt [u uw huidige account saldo ophalen](get-the-reseller-s-current-account-balance.md)

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
