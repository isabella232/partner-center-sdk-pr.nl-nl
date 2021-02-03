---
title: Azure-reserveringen kopen
description: U kunt Azure-reserve ringen kopen voor een klant met behulp van de Partner Center API via uw bestaande Microsoft Azure-abonnement (MS-AZR-0145P) of Azure-plan.
ms.date: 11/01/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4c09f65ae5105a74be41a7ec45824e3889217a1c
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767255"
---
# <a name="purchase-azure-reservations"></a>Azure-reserveringen kopen

**Van toepassing op:**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud for US Government

Als u een Azure-reserve ring voor een klant wilt kopen met behulp van de Partner Center API, moet u een bestaand Microsoft Azure (**MS-AZR-0145P**) of een Azure-abonnement hebben.

> [!NOTE]
> Azure-reserve ringen zijn niet beschikbaar op de volgende markten:
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

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Een abonnements-ID voor een actief CSP Azure-abonnement of een Azure-plan.

## <a name="how-to-purchase-microsoft-azure-reservations"></a>Microsoft Azure reserve ringen aanschaffen

Wanneer u het actieve CSP Azure-abonnement hebt geïdentificeerd waaraan u een Azure-reserve ring wilt toevoegen, gebruikt u de volgende stappen om het te kopen:

1. [Activering](#enablement) : Registreer een actief CSP Azure-abonnement om het in te scha kelen voor het aanschaffen van Azure-reserve ringen.

2. [Detectie](#discovery) : Zoek en selecteer de Azure reservation-producten en sku's die u wilt kopen en controleer de beschik baarheid.

3. [Order inzending](#order-submission) : Maak een winkel wagen met de items in uw bestelling en verzend deze.

4. Bestellingsgegevens [ophalen](#get-order-details) : Bekijk de details van een order, alle orders voor een klant of geef orders per facturerings cyclus type weer.

Nadat u Azure-reserve ringen hebt aangeschaft, kunt u in de volgende scenario's zien hoe u hun levens cyclus beheert door informatie over uw Azure-reserve ringen te verkrijgen en saldo overzichten, facturen en factuur overzichten op te halen.

- [Levenscyclus beheer](#lifecycle-management)
- [Factuur en reconciliatie](#invoice-and-reconciliation)

## <a name="enablement"></a>Activering

Activering betekent dat u een bestaand Microsoft Azure-abonnement (**MS-AZR-0145P**) koppelt aan een gereserveerde VM-instantie van Azure door het abonnement te registreren zodat Azure-reserve ringen worden ingeschakeld. Registratie is een vereiste voor het aanschaffen van Azure Reserved VM Instances.

Er is een abonnement vereist vanwege het volgende:

1. Om te controleren of de klant in aanmerking komt voor het implementeren van resources en daarom het aanschaffen van Azure Reserved VM Instances in een regio of niet.

2. Om capaciteits prioriteit te bieden voor implementaties op een abonnement. Dit is alleen van toepassing op de Azure Reserved VM Instances voor een enkele scope waarvoor de optie **capaciteits prioriteit** is geselecteerd.

Zodra u het actieve abonnement hebt geïdentificeerd waaraan u de Azure-reserve ring wilt toevoegen, moet u het abonnement registreren zodat Azure-reserve ringen worden ingeschakeld. Als u een bestaande [abonnements](subscription-resources.md) resource wilt registreren, zodat deze geschikt is voor het best Ellen van Azure-reserve ringen, raadpleegt u [een abonnement registreren](register-a-subscription.md).

Nadat u uw abonnement hebt geregistreerd, moet u controleren of het registratie proces is voltooid door de registratie status te controleren. Zie de [registratie status van het abonnement ophalen](get-subscription-registration-status.md)voor meer informatie.

> [!NOTE]
> Wanneer u Microsoft Azure reserve ring voor een klant met een Azure-abonnement aanschaft, moet u eerst het Azure-abonnement registreren. Net als bij een Microsoft Azure (**MS-AZR-0145P**) wordt een Azure-abonnement vertegenwoordigd door de resource van een partner Center- [abonnement](subscription-resources.md) . Daarom kunt u dezelfde methode voor het [registreren van](register-a-subscription.md) een Azure-abonnement gebruiken.

## <a name="discovery"></a>Detectie

Zodra het abonnement is ingeschakeld voor het aanschaffen van Azure-reserve ringen, bent u klaar om producten en Sku's te selecteren en de beschik baarheid te controleren met de volgende partner Center API-modellen:

- [Product](product-resources.md#product) : een groeperings constructie voor tevens-goederen of-services. Een product zelf is geen tevens-item.

- [SKU](product-resources.md#sku) : een SKU (tevens Stock Keeping Unit) onder een product. Deze vertegenwoordigen de verschillende vormen van het product.

- [Beschik baarheid](product-resources.md#availability) : een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land-, valuta-en sector segment).

Voordat u een Azure-reserve ring aanschaft, voert u de volgende stappen uit:

1. Identificeer en haal het product en de SKU op die u wilt kopen. U kunt dit doen door eerst de producten en Sku's te vermelden, of als u de Id's van het product en de SKU al kent, selecteert u deze.

   - [Een lijst met producten ophalen (per land)](get-a-list-of-products.md)
   - [Een product ophalen met de product-ID](get-a-product-by-id.md)
   - [Een lijst met SKU’s voor een product ophalen (per land)](get-a-list-of-skus-for-a-product.md)
   - [Een SKU ophalen met behulp van de SKU-ID](get-a-sku-by-id.md)

2. Controleer de inventarisatie van een SKU. Deze stap is alleen nodig voor Sku's die zijn gelabeld met een **InventoryCheck** -vereiste.

   - [Voorraad controleren](check-inventory.md)

3. De [Beschik baarheid](product-resources.md#availability) voor de [SKU](product-resources.md#sku)ophalen. U hebt de **CatalogItemId** van de beschik baarheid nodig wanneer u de order plaatst. Gebruik een van de volgende Api's om deze waarde op te halen:

   - [Een lijst met beschikbaarheid voor een SKU ophalen (per land)](get-a-list-of-availabilities-for-a-sku.md)
   - [Krijg een Beschik baarheid met behulp van de beschikbaarheids-ID](get-an-availability-by-id.md)

> [!IMPORTANT]
> Elk Microsoft Azure reserverings product heeft een ander Beschik baarheid voor Microsoft Azure (**MS-AZR-0145P**)-abonnement en het Azure-plan. Als u [een lijst met producten wilt ophalen (per land)](get-a-list-of-products.md)of als u een lijst wilt ophalen [van de sku's voor een product (per](get-a-list-of-skus-for-a-product.md)land) of als u een lijst wilt ophalen met Beschik baarheid [voor een SKU (per land)](get-a-list-of-availabilities-for-a-sku.md) die alleen van toepassing is op het Azure-abonnement, geeft u de para meter ' reservationScope = AzurePlan ' op.

## <a name="order-submission"></a>Verzen ding best Ellen

Ga als volgt te werk om uw Azure reserverings order in te dienen:

1. Maak een mandje om de verzameling catalogus items te bewaren die u wilt kopen. Wanneer u een [winkel wagen](cart-resources.md)maakt, worden de [Winkelwagen regel items](cart-resources.md#cartlineitem) automatisch gegroepeerd op basis van wat er in dezelfde [volg orde](order-resources.md)kan worden aangeschaft.

   - [Een winkel wagen maken](create-a-cart.md)
   - [Een winkel wagen bijwerken](update-a-cart.md)

2. Bekijk de winkel wagen. Het uitchecken van een winkel wagen resulteert in het maken van een [order](order-resources.md).

   - [De winkel wagen afhandelen](checkout-a-cart.md)

## <a name="get-order-details"></a>Bestellingsgegevens ophalen

Nadat u uw Azure-reserverings order hebt gemaakt, kunt u de details van een afzonderlijke order ophalen met behulp van de order-ID of een lijst met orders voor een klant ophalen. Er is een vertraging van Maxi maal 15 minuten tussen de tijd dat een bestelling wordt verzonden en wanneer deze wordt weer gegeven in een lijst met de orders van een klant.

- Om de details van een afzonderlijke order op te halen met behulp van de order-ID. Zie [een order op basis van id ophalen](get-an-order-by-id.md).

- Een lijst met orders voor een klant ophalen met behulp van de klant-ID. Zie [alle bestellingen van een klant ophalen](get-all-of-a-customer-s-orders.md).

- Als u een lijst met orders voor een klant per [facturerings cyclus type](product-resources.md#billingcycletype) wilt ophalen, kunt u Azure-reserverings orders (eenmalige kosten) en jaarlijks of maandelijks gefactureerde orders afzonderlijk weer geven. Zie [een lijst met orders ophalen op basis van het type van de klant en de facturerings cyclus](get-a-list-of-orders-by-customer-and-billing-cycle-type.md).

## <a name="lifecycle-management"></a>Levenscyclus beheer

Als onderdeel van het beheer van de levens cyclus van uw Azure-reserve ringen in het partner centrum, kunt u informatie ophalen over uw Azure-reserve ring [rechten](entitlement-resources.md)en de reserverings Details ophalen met behulp van de reserverings order-id. Zie [rechten ophalen](get-a-collection-of-entitlements.md)voor voor beelden van hoe u dit doet.   

## <a name="invoice-and-reconciliation"></a>Factuur en reconciliatie

In de volgende scenario's ziet u hoe u de [facturen](invoice-resources.md)van uw klant programmatisch kunt bekijken en hoe u uw account saldi en samen vattingen kunt ophalen die eenmalige kosten voor Azure-reserve ringen bevatten.

### <a name="balance-and-payment"></a>Saldo en betaling

Als u het huidige account saldo wilt ophalen in het standaard valuta type dat een saldo van de kosten voor periodiek en eenmalig (Azure reserve ring) is, raadpleegt [u uw huidige account saldo ophalen](get-the-reseller-s-current-account-balance.md)

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
